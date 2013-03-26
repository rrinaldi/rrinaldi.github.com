---
layout: post
title: using-web-application-projects-with-team-build
---
Are you using Web Application Projects with Team Build?

Did you upgrade from WAP RC1 to 1.0?

Can you not find your Web Application Project under the
**\_PublishedWebsites** directory in your drop location?

I couldn’t, and after much googling I found the solution here:
[http://forums.asp.net/thread/1275619.aspx](http://forums.asp.net/thread/1275619.aspx)

Problem is any WAPs that were created prior to 1.0 don’t support Team
Build so you need to tweak the WAP project file by hand.  Just in case
that link stops working someday, I’m reprinting the directions below:

*“If you're using Team System with Team Build  or building via the
command line build with MSBuild you'll want to make one change to your
existing WAP projects.  We've added a MSBuild targets file to support
these build scenarios.  This targets files will be included in all new
Web App Projects and any newly migrated projects.  However you'll need
to manually add it to existing Web App Project files.*

*To do this\<right\>\<click\> on the project node and select "Unload
Project", then \<right\>\<click\> again and select "Edit Project".  Add
the line highlighted below right after the existing targets entry. *

*  \<Import
Project=**"\$(MSBuildBinPath)\\Microsoft.CSharp.targets"**/\>\
**  \<Import
Project="\$(MSBuildExtensionsPath)\\Microsoft\\VisualStudio\\v8.0\\WebApplications\\Microsoft.WebApplication.targets"
/\>*

**

*Adding the import for Microsoft.WebApplication.targets will ensure that
your Web App Project will build correctly when building with Team Build
or via the command line using MSBuild.”*

**Now playing:** Red Hot Chili Peppers - Naked in the Rain
