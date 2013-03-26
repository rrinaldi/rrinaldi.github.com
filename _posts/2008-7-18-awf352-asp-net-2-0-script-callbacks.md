---
layout: post
title: awf352-asp-net-2-0-script-callbacks
---
So I can get an IP on the wireless network, but getting IP apparently
doesn't mean being able to route to web sites. ugh

* * * * *

Script callbacks are the official way to get data from the server to the
client in a remote scripting way in 2.0
 
Ajax.NET is the way to do it today (I'm aware of Ajax.NET, haven't had a
chance to play with it)
 
Script Callback
- Out of band calls to a remote server to downlad data to update the
current page.
     - Data marshaled from client to server and back
     - Client script code updates the page's DOM
     - No full page refresh
- Requires browsers with advanced capabilities
     - 90% of today's browsers have rquired capabilities
     - IE 5+, Safari 1.2+, Netscape 6+, Opera 7+
     - All implement a DOM and support W3C standards
 
90+ percent of all browsers support W3C standard DOM
 
Mechanics
- The client page makes a call to XmlHttpRequest to open a socket and
place a HTTP request behind the scenes
     - Something happens on the server
- Return values are passed to a Javascript function embedded in the page
     - Accesses the page's DOM and modifies the page
- The page contains a trigger - typically a client button with an
onclick Javascript handler
     - The onclick handler is bound to some ASP.NET generated script
code
     - This script code contains a call to XmlHttpRequest
- Out-of-band calls reaches the URL of the current page in a special
posback request
     - the target can be the page or a control in the page
     - must implement ICallbackEventHandler
 
 
Technorati Tags :
[DevConnections](http://technorati.com/tag/DevConnections),
[AJAX](http://technorati.com/tag/AJAX)
 
