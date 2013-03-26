---
layout: post
title: how-to-get-the-last-successful-build-from-tfs
---
Normally when I’m on a project I write up a little deployment console
app to make deploying builds a bit easier (and repeatable!).  The first
step in any sort of deployment app is getting the last successful build
from your build server.  Here is some code that gets the build
information from TFS:

var

server = TeamFoundationServerFactory.GetServer("TFS SERVER NAME");

var buildServer = (IBuildServer)server.GetService(typeof(IBuildServer));

var buildDef = buildServer.GetBuildDefinition("TFS PROJECT NAME", "BUILD
NAME");

IBuildDetail buildDetail =
buildServer.GetBuild(buildDef.LastGoodBuildUri);

string

dropLocation = buildDetail.DropLocation;

Now you can copy the build straight from the path in dropLocation.
![](http://ryanrinaldi.com/files/media/image/smile1.gif)

Technorati Tags: [tfs](http://technorati.com/tags/tfs)
