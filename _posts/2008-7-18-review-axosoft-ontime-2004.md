---
layout: post
title: review-axosoft-ontime-2004
---
[This is an honest to goodness opinion of software that I use daily.  I
was not paid, nor will I accept payment for exposing my views on
developer tools]

Defect Tracking, Bug Tracking, Feature Request Tracking, whatever you
call it, it is something that all developers need to use.  I've used
plenty of different systems over the past few years (mostly homebrew) to
track, categorize, and assign defects to developers but not one has been
the "perfect fit".  So far [Axosoft OnTime
2004](http://www.axosoft.com/default.aspx) comes the closest.

First let me state that I'm a "platform bigot".  Any tools that I use
must run on the platform that I write software for.  I don't know why,
but I just prefer things that way.  So when I started looking at Defect
Tracking tools, I wanted on that was written in .NET and had some sort
of SDK that I could hook into (again, preferably .NET).  OnTime 2004 was
one of the few that I found that was .NET based, but the only one that I
found that had an SDK (If anybody knows otherwise, let me know).  The
[OnTime 2004 Web
Services](http://www.axosoft.com/products/ontime_sdk.aspx) SDK is all
around solid, allowing you access to all of the functionality of the
OnTime product itself.  One glaring problem is that it truncates white
space in text fields when editing, but that could be a setup/environment
problem on my part.

Second, I need to point out that I like my tools to be "pretty".  I know
that seems like a weird requirement, but I think that it is really easy
nowadays to make software look good, and if you can't put in that little
bit of work it takes to make something look good then I question the
overall quality of your product even before using it.  Also, if you
expect me to spend all day in your app, then I better like looking at
it. :)  OnTime 2004 hits the nail on the head when it comes to designing
a "pretty UI".  I like the way it looks, it's laid out nicely, and
everything is where I expect it to be.

Anyway, I'll break this down into the pros and cons as I see them:

**Pros:**

    -.NET Application (See my platform bigotry statement above)

    -SDK

    -Visual Studio .NET plug-in: This thing is pretty sweet.  I haven't
seen another tool do it.  A small little plug-in that sits in Visual
Studio that gives you 95% of the functionality of the Win client.

    -Windows Authentication: It is so sweet to not have to remember
another freakin' login.

    -Role based security:  You can create unlimited roles, and assign
permissions to those roles and limit the projects a role can see.

    -Custom fields:  No matter what Joel on Software says, you need to
have custom fields.

    -Free one user license:  Taking a trick from
[SourceGear](http://www.sourcegear.com/) and their VCS product
[Vault](http://www.sourcegear.com/vault/index.asp), Axosoft provides a
free one user license.

**Cons:**

    -Modal Windows: C'mon guys, just because I am in the detail view of
a defect, doesn't mean I don't want to go back to the main window, or if
I have a detail view open that doesn't mean when I bring focus to that
window that I want the parent window to pop up too.  This is especially
a problem with the VS.NET plug-in.  Let me get to my code!

    -Misspellings:  There are some misspellings in some of the field
types.  These are very easily editable, so it isn't something worth
freaking out about, but it is annoying to see in a commercial app.

    -Needs direct access to SQL Server:  Get with the times guys.  If I
have to open more than port 80 on a firewall to connect to the data
store, I'm working too hard and putting my network at risk.  You have a
web services SDK, why not take it a little further and use web services
to talk to the database?

Overall, OnTime is quite a cool product and I'm in the process of
purchasing it for use at work.  With the Win client, web client, VS
Plug-in and the SDK I haven't found any defect tracking tool that comes
close.  I give Axosoft OnTime 2004 4 out of 5 pieces of Halloween candy
