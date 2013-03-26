---
layout: post
title: distro-replacement-for-registerclientscriptblock
---
[From Youngpup](http://www.youngpup.net/), the guru of all things DOM
and JavaScript related, comes a [replacement server control/API
library](http://www.youngpup.net/2004/distro) for
RegisterClientScriptBlock().

 

He aims to solve a few shortcomings of RegisterClientScriptBlock(), such
as:

-   API requires mixing of .NET and JavaScript code in the code-behind.
-   JavaScript code is compiled into the code-behind, which means
    constant recompilation during development, debug, and QA.
-   JavaScript in code-behind breaks separation of style and logic - the
    JavaScript should be in the ASPX or ASCX with the rest of the HTML.
-   No way to control the order in which the scripts execute in.
-   No good way to link a JavaScript function to the client-side events
    of an ASP.Net Server Control.

Make sure to cruise around the site.  He has some sweet JavaScript
libraries up there.

 
