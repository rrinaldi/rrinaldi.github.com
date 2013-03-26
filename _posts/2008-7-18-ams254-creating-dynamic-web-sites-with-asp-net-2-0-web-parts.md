---
layout: post
title: ams254-creating-dynamic-web-sites-with-asp-net-2-0-web-parts
---
Last session ran long so I'm walking into this one about 5 minutes in. 
No power can be found, but I do get a nice table to work on. :)

* * * * *

 
Webparts:
-Provide users with:
      - Flexible display options
      - Personalized content
 
-Provide developers with
      - Plenty of prewritten code
 
ASP.NET Webparts
- Provid ebuilding blocks for dynamic web sites
- Can be used in any kind of Web application
      - Portal, content management, intranet, internet
-Fully integrated into a ASP.NET control model
      - Every ASP.NET contrl can be used with Web Parts
      - Connections become easier, more powerful
- Full development flexibility and extensibility
- Leveage core ASP.NET services
- Great Visual Studio designer experience (yay! no more gray boxes!)
 
Compatibility
- SharePoint technology-based Web Parts
      - Will work in next release ofWindows SharePoint Services
      - SharePoint vNext WebPart == ASP.NET Web Part
- ASP.NET 2.0 Web Part controls
      - Willwork under ASP.NET 2.0
      - Willwork in the next release of Windows SharePoint Services
      - Are being evaluated working on ways to make them work iwht the
current release of Windows SharePoint Services (omg, so happy!!)
 
Dynamic Modular Web Sites
-Display Modes
      - Browse (Show the content)
      - Design (Allow the web parts to be moved around on the page (ala
SharePoint))
      - Edit (Change properties and attributes of the web parts (real
properties of the component))
      - Catalog (Showing a list of web parts can be shown on a page) 
      - Connection (Allow parts to share data between parts.  None of
the parts need to know about any other parts.)
 
Core Concepts:
- Non-Visual control: ASP web part manager.  Manages all the interaction
between web parts. "The brains behind web parts."
- Personalization: Persist control settings, configurable data store
(build in SQL Server support, extensible through providers, 7.0, 2000
and 2005 supported)
- Enabled by default (can be disabled via the web part manager)
- Zone: Zone == Layout
      - Manages layout for ASP.NET server controls
      - A page can contain one or more zones
      - A zone depends on the display mode of the page
      - a zone controls the look and feel of the parts that are shown in
that zone.
      - each mode requires a zone for that mode
- Types
      - Any ASP.NET server control or user control can be a web part
 
Only IE will have drag and drop support, but by using Layout zones you
can move parts into different zones. (Is drag and drop in other browsers
really that hard?!?!)
 
The demo is amazing.  I'm really excited to start using some web parts.
 
Building a web part
- As a user control
       - Create an ascx file
       - add it to a zone
       - at runtime the user control will be wrapped using a
GenericWebPart
- As a custom control
       - Inherit from System.Web.UI.WebControls.WebPart
      - Override ChildControlCreated/Render method
      - Add it to the zone
 
(I think I'll just be doing the user control method, thank you very
much)
 
Web Part Elements
- Title
- Verbs
       - UI Elements that enable users to perform actions
      - WebPartZone provides standard verbs
             - Close, minimize, restore, help, edit, connect, export
      - WebPart developer adds custom verbs
            - Really just a string that gets passed to an event handler
on the server
- Chrome
      - graphical aspect to the controls
- Content
      - the meat of the control
- TitleIcon
      - icon that represents the web part
 
Non-WebPart controls
- Opt-in model to fine tune the contrls behavior as a "Web Part"
      - IWebPart
            - Enable developer to define web part properties
      - IWebActionable (I might have wrote that down wrong)
 
WebPart class
- Proved programmitc control
       - Define how the user interacts with the web part UI
       - Add custom verbs
       - Define icon for the title and catalog
       - Define help mode and help url
- Container Control
       - WebPart is essentially a Panel
 
Editing
- End user can personalize web part properties using the Editor Zone
- Four types of Editor Part
- Set the appropriate attributes
      - Personalizable
      - WebBrowsable, WebDescription, WebDsiplayName
 
ASP.NET will reflect over the part at runtime and make them editable in
the editor parts.  The settings are saved in a database and when the
page is rendered the next time, the values will be pulled from the
database and injected into the part.
 
Adding controls to a page
- Developer or Admin could define approved controls in a catalog
 
WebPart connections
- Dynamic connections are invoked via the browser
- Static connections are defined by the page developer
- Most code intensive actions for web parts
 
People seem to dig the WebPart connections, they gave the presenter a
round of applause.
 
 
Technorati Tags :
[DevConnections](http://technorati.com/tag/DevConnections)
 
 
 
 
 
 
 
 
 
 
 
 
 
