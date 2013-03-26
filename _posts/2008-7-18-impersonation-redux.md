So, [I've been](http://http://blogs.geekdojo.net/ryan/posts/387.aspx)
[trying](http://http://blogs.geekdojo.net/ryan/posts/384.aspx) to get my
stupid ASP.NET app to create a couple folders out on the network.  That
would sound easy enough, but apparently Microsoft decided that was a
security risk.  So I need to use Impersonation.  Okay, well I tried that
but apparently trying to impersonate a web user that logged in using NT
Authentication does not give that user network access (KB Article
describing this is
[here](http://support.microsoft.com/default.aspx?scid=kb;en-us;207671)). 

\<RANT\>

According to the KB article I linked to above, NT Authentication does
not give you access to network resources.  BUT Basic Authentication
does.

“So Ryan, what is the difference between the two?”, you ask.

Well, funny you should ask that.  You see NT Authentication passes a
token from your machine to the web server informing the web server as to
your identity.  The token contains no information that can actually be
used to log you onto the machine in the event that somebody was to
intercept it.  Now, Basic Authentication on the other hand passes your
username and password in clear text to the web server.

I'll let that sink in for a minute or two.

[Ryan hums “[The Spanish
Flea](http://www.columbia.edu/~sjt59/mr_nice.swf)“]

Oh sorry.  I'm back now.

If you didn't catch it, I said CLEAR TEXT.  Meaning anybody and their
half retarded chihuahua can sniff your web traffic and log onto the
machine as you.  And this abomination of security gives you greater
access to the domain's resources?

Huff.

Either I am completely wrong when it comes to NT Authentication versus
Basic Authentication or that needs some SERIOUS looking into.

\</RANT\>

Okay, so I'm done ranting now but that still doesn't solve my problem
about Impersonation.  [So I
tried](http://blogs.geekdojo.net/ryan/posts/384.aspx)the standard .NET
way of impersonating an user.  But as you can see, [that didn't
work](http://blogs.geekdojo.net/ryan/posts/387.aspx).  So I tried using
some interop and logging on as an [user with a known username and
password](http://www.mostlylucid.co.uk/posts/662.aspx). [Thank you
[Scott](http://www.mostlylucid.co.uk/) for the post.  It gave me a
glimmer of hope.]  That doesn't cut it either.  To make the LogonUser
API call, the security context that the process is running under needs
to have the “Act as part of the operating system.” flag set.  The ASPNET
worker process does not.

Huff.

So it looks like I will be using the CreateProcessWithLogonW call, which
allows me to spawn a new process under a new known logon, using that
logons security credentials. 

So, as soon as I get that taken care of I'll probably wrap it up with a
nice little bow and throw it out here for you.

Right now though, I'm going home.
