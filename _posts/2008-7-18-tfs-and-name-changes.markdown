---
layout: post
title: tfs-and-name-changes
---
One of my fellow developers on my team just had her name change.  We
figured there would be a few issues when her login name changed and TFS
pretty much puked on it.  It seems that TFS stores some workspace
mapping info locally and part of that information is the owner name. 
When it connects to the server it gets all sorts of conflicts because
the workspace on the server has the same mappings as the workspace on
the client but they are owned by different logins.  After a bit of
digging, I found the solution.

If this happens to you go to “C:\\Documents and Settings\\{login}\\Local
Settings\\Application Data\\Microsoft\\Team Foundation\\1.0\\Cache\\”
and open the VersionControl.config file and delete all of the
WorkspaceInfo nodes.  Don’t worry, they will be recreated once you
connect to the server again.  There you have it!  And next time, try to
convince your coworkers to leave their names alone!
