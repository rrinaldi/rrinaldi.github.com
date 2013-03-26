Maybe you like HttpHandlers.  Maybe you want to use them to intercept
calls to files end users will be downloading from your server.  You want
to log the file requests. 

"HttpHandlers would be perfect for this!", you smugly think.

Think again.

When deciding to use HttpHandlers, be very, very careful.

At my office, we were using HttpHandlers to track downloads of our
products from our customer portal.  So we thought we were being good
little developers and we mapped all .zip files in IIS to the ASP.NET
dll, setup the HttpHandler paths to only worry about the .zip files in
the product downloads section of our site and we went on our merry
little way.

A couple weeks go by, and we get an email from our support department.

"I can't download some log files from the customer portal."

Interesting.  The log files are just .zip files that customers upload to
the customer portal when they open up a support ticket.  So I ask our
support guy to forward me the email that has the link to the log files
in it, and I'll take a look.  Email comes in, I click on the link, then
BAM!

"**Server Unavailable**"

"HUH!?", I think to myself quite loudly.

That can't be right.  Must have been a quirk.  I'll click the link again
and everything will be alright.

\*Click\*

"**Server Unavailable**"

\*Gulp\*

At this point in time I start to panic a little. Every time that link is
clicked it restarts the ASP.NET worker process.  Kills all of the
sessions on the server.  Forcing all of our customers to re-login. Not
good.  Not good at all.

I take a look at the Event Viewer.  "ASP.NET worker process stopped
unexpectedly."  Thanks!  That explains it.  I'll just turn off the "Stop
Unexpectedly" flag in IIS!

So, I figure I'll open up perfmon and see what is going on.  Add a few
monitors there, a couple here, and presto.  I click the link in the
email and I watch the committed memory skyrocket, then plummet, then the
process restart.

"Interesting.  What could be causing that?", I wonder.

I look at the usual suspect: Norton Antivirus.  Norton has bit me a
couple times before, you see.  Before we were using the customer portal
to upload log files, customers would email them in.  That was all fine
and dandy until you realize that log files have lots and lots of
redundant data in them.  Very compressible.  So a 10 meg .zip file turns
into 600 megs of extracted text in memory that Norton Antivirus is
trying to scan.  Email server reboots, log file email vaporizes into
thin air.  Lots of fun all around. :)

Anyway, I turn off Norton and click the link in the email.

"**Server Unavailable**"

"<*@#!!@!@#$!@$!@#$!@#$!!!!!!!>", I scream loudly in my own skull.

I start to Google for magical potions and dances I can do that will let
people download files off of my server, when I remember the HttpHandlers
we have running.  Check web.config and see that the paths the Handlers
are handling for have nothing to do with the log file upload directory. 
So the handlers aren't running.  Check out IIS and see that .zip is
mapped to the ASP.NET dll.

"Ahhhhh!"

To make an incredible long and boring story a tad shorter, it seems that
when you map a file type in IIS to the ASP.NET dll, ASP.NET will read
the file into memory even if there isn't a HttpHandler that will handle
it.  When the file is incredible large, this can create problems.  Big
problems.

So my advice is to avoid HttpHandlers unless you are really sure they
are the solution to the specific problem that you are trying to solve.

 
