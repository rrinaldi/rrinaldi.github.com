Port knocking that is.

I'm not a network admin, but I found
[this](http://www.portknocking.org/) quite interesting.  A network
security system designed around a "secret handshake" of sorts.

An example:

I want to SSH into a server.

Port 22 is closed.

BUT, if I attempt connections to closed ports 1024, 88, 5632, and 9652
in succession port 22 will open and accept connections for the next 5
minutes.

It doesn't matter what port I want to connect to or what ports I attempt
a connection to in succession.  As long as the ports are part of
the secret handshake.

I don't think I explained that very well, but check out the site.  I'm
sure things will be crystal afterward.
