---
layout: post
title: system-diagnostics-debug-writeline-not-doing-anything-for-you
---
Just found out that if you add a new project to a solution using the
“New Project In Existing Folder” option of Visual Studio.NET 2003 the
project doesn’t define the DEBUG (or TRACE for that matter) compile
directive, which is required for System.Diagnostics.Debug to do it’s
thing.

Don’t get burned like I did.  Cost me 15 minutes of head scratching.
