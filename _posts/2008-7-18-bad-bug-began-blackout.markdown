---
layout: post
title: bad-bug-began-blackout
---
According to [this SercurityFocus
article](http://www.securityfocus.com/news/8016) a wee-tiny little flaw
in the energy management system (created my non-other than General
Electric) caused the great catastrophe that was the August 14th
blackout.

I apologize.  It was me.  I got a little sloppy that day, and forgot to
catch a OutOfPowerException.  If I handled that correctly and maybe
backed the system off a little bit everything would have been fine.

Oh well. Live and learn. :)
