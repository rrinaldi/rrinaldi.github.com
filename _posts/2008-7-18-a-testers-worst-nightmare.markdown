---
layout: post
title: a-testers-worst-nightmare
---
I'm sitting at home this saturday evening doing some laundry and going
through my laptop cleaning off unused programs.  I noticed that I had VS
2003 installed, and now that our team is moving to Team Foundation
Server I figured it was high time to install VS 2005 Team System on this
baby.

This is where I start to make software testers cry.

I fire up my VPN over my wireless connection on the laptop, map a drive
to a share on our corporate LAN, load up Microsoft's Virtual CD-ROM tool
and point it to an ISO that is on the newly mapped drive.  I then
navigate on over to the virtual drive and fire up the VS 2005 install.

So I'm running on a wireless network over a virtual network to create a
mapped drive (which, when you think about it is merely a virtual pointer
to a UNC share) so I can load another virtual drive to actually run my
install.

You think that edge case was tested? :)
