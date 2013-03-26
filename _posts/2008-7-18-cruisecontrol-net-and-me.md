---
layout: post
title: cruisecontrol-net-and-me
---
The last couple of days at work I've been setting up a continuous
integration server using
[CruiseControl.NET](http://confluence.public.thoughtworks.org/display/CCNET). 
I've found the process to be relatively painless, except for some
incidents where reading the docs was the WRONG thing to do.

As an FYI to those out there that, like me, just wanted
[CCNET](http://confluence.public.thoughtworks.org/display/CCNET) to
build their solution using Visual Studio you will run into a bug in the
documentation that might make you bang your head against a wall.  The
docs will tell you that to setup a Visual Studio Builder in the config
file you need to add the following:

"commandLineBuilder"\>\
     src\\MyProject.sln\
     Debug\

Actually, commandLineBuilder is the type you need to pass in if you are
using 'make' files.  What you really want to put in there is "devenv". 
This will tell
[CruiseControl.NET](http://confluence.public.thoughtworks.org/display/CCNET)
to use Visual Studio.
