---
layout: post
title: system-net-mail-doc-error
---
**UPDATE:** So I'm slow.  There is a static method on AlternateView
called CreateAltenateViewFromString() that will take a string and a
ContentType and return an AlternateView instance for you.  Next time I
will read the rest of the docs (as long as they are correct!).

In .NET 2.0, MS added System.Net.Mail (SNM) in favor of
System.Web.Mail.  Being the nice developer I am, I always try to send
emails in HTML and plain text and let your mail client decided which one
to show you. (Having a crackberry, I understand what a pain it is to get
an email that is html only and not be able to read one line of the email
because all you see is angle brackets.)  To accomplish this in SNM, you
need to set add an AlternateView to the AlternateViews collection.  The
code to do this is not as straight forward as one would think.  Here is
the documentation from MSDN:

    // Create a message and set up the recipients.\
    MailMessage message = new MailMessage(\
        "jane@contoso.com",\
        recipients,\
        "This e-mail message has multiple views.",\
        "This is some plain text.");\
\
    // Construct the alternate body as HTML.\
    string body = "\<!DOCTYPE HTML PUBLIC \\"-//W3C//DTD HTML 4.0 Transitional//EN\\"\>";\
    body += "\<HTML\>\<HEAD\>\<META http-equiv=Content-Type content=\\"text/html; charset=iso-8859-1\\"\>";\
    body += "\</HEAD\>\<BODY\>\<DIV\>\<FONT face=Arial color=\#ff0000 size=2\>this is some HTML text";\
    body += "\</FONT\>\</DIV\>\</BODY\>\</HTML\>";\
\
    // Add the alternate body to the message.\
    AlternateView alternate = new AlternateView(body, MediaTypeNames.Text.Html);\
    message.AlternateViews.Add(alternate);\
\
    // Send the message.\
    SmtpClient client = new SmtpClient(server);\
    client.Credentials = CredentialCache.DefaultNetworkCredentials;\
    client.Send(message);\

The problem being that the AlternateView constructor overload that takes
a string assumes that the string is a file location.  Whoops!  Way to go
documentation team!  I say that jokingly, because if I wrote the docs
you would be lucky if there was a single line that said more than
"You're on your own dude."

Back to setting up that alternate view:  Since the AlternateView
constructor that takes a string is for filenames, I started looking at
the other ones I could use.  All of them are file related, some taking a
string and some taking a Stream.  But I had a string of content, not a
Stream.  So time to go converting...

To go from a string to a Stream, one needs to remember our friend
MemoryStream.  Since MemoryStream doesn't need any backing file or IO
system, this is what we need.  So what does a MemoryStream need to be
"newed" up?  A byte array.  So, how do we go from a string to a byte
array?  System.Text.Encoding can get us there!  We need to grab the
Unicode Encoding object and ask it to convert our string to a byte array
for us.  Pass the byte array to the MemoryStream constructor and pass
that to the AlternateView constructor.  So after updating the code above
to take into account all of our new code you get:

// Create a message and set up the recipients.\
    MailMessage message = new MailMessage(\
        "jane@contoso.com",\
        recipients,\
        "This e-mail message has multiple views.",\
        "This is some plain text.");\
\
    // Construct the alternate body as HTML.\
    string body = "\<!DOCTYPE HTML PUBLIC \\"-//W3C//DTD HTML 4.0 Transitional//EN\\"\>";\
    body += "\<HTML\>\<HEAD\>\<META http-equiv=Content-Type content=\\"text/html; charset=iso-8859-1\\"\>";\
    body += "\</HEAD\>\<BODY\>\<DIV\>\<FONT face=Arial color=\#ff0000 size=2\>this is some HTML text";\
    body += "\</FONT\>\</DIV\>\</BODY\>\</HTML\>";\
\
    // Add the alternate body to the message.\
    AlternateView alternate = new AlternateView(new MemoryStream(Encoding.Unicode.GetBytes(body)), MediaTypeNames.Text.Html));\
    message.AlternateViews.Add(alternate);\
\
    // Send the message.\
    SmtpClient client = new SmtpClient(server);\
    client.Credentials = CredentialCache.DefaultNetworkCredentials;\
    client.Send(message);\

Easy?  Kinda.  Straight forward?  Nope.  Is there an easier way? 
Probably, but this works.  If I missed something, let me know.
