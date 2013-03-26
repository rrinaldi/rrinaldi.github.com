---
layout: post
title: pdc-2008-microsoft-visual-studio-customizing-and-extending-the-development-experience
---
Agenda

-   Extending Visual Studio
-   VS 2010 Extensibility

Extend your Development Experience

Find Tools

-   Visual Studio Gallery
-   VS 2010 download manager
-   CodePlex

Customize Tools

-   Existing Customizations
-   Start page

Build Tools

-   Add-ins
-   Packages
-   Designers
-   DSLs
-   Editor Components

Find extensions in the gallery

-   100s of Extensions
-   Demo of "Power Commands"

Creation of Custom Tool Window

-   Content is a XAML viewer
-   DTE Actions
-   Use SDK sample browser to initiate
-   Visual 2010 changes: WPF Shell

Side note: The SDK Samples look pretty complete.  Looking forward to
playing with that

Still a lot of work to hook Tool windows into VS.  Lots of hWnd magic,
wrapper to managed code stuff

-   Only in VS 2008!
-   All the VS2010 stuff will be all WPF

Currently there are a lot of MsVsShell attributes to wire packages into
VS.

-   Apparently there are lots of changes in VS 2010 to make this simpler

DTE

-   Development Tools Extensibility
-   High level apis
-   Used by macros and addins, but useful for packages as well

Isolated Shell

Visual Studio 10 Extensibility Offerings

Customizing the start page

-   The start page is just XAML

I think I might make a TFS start page explorer type thing.  It strikes
me as an interesting project

-   You can do whatever you want as far as DTE commands

New managed extensibility mechanism designed from the groupd up

All managed (NO COM!!!)

Used for emerging Visual Studio architecture

Appears first in the editor

Characterized by ease of construction and deployment

Self describing payloads, "xcopy" semantics

DILU (drop in, light up) deployment

\*Not\* focused on hot deploy in first release

-   Stop and restart is required (Not a big deal in my opinion.)

Things you can do

Rich text formatting

Rich reading experience

multiple fonts

Font styles and effects

Opacity

Higher performance

Composable

-   3rd party mixins
-   Per-line transforms

Adornments

Any WPF visual

-   Drawn on one of several planes

Two tracking modes

-   Associate with text
-   Associate with screen

Animation and behavior

-   If you can do it in WPF you can do it in the editor

Margin and scrollbar control

Replace or customize existing margins and scrollbar

define new margins

-   All four sides

Support for spatial mapping

Intellisense and Smart Tags

Any3rd party (not just language services)

-   Contribute to Completion
-   Override the presentation of Parameter Help or Quick Info
-   Add menu items to Smart Tags

Demo of a word tracking highlighting

-   Just need to use standard MEF attributes to wire up new components
-   Attribute ContentType constrains the providers to specific content
    types (text, csharp, vb)
-   There are services in place to simplify UI updating race conditions.
-   The WPF editor components are almost 100% production ready

Managing your extensions

-   What if you could dicover and search for extensions within the IDE
-   What if you could install, manage and update extensions there as
    well?
-   What if we could make publishing IDE extensions (of all flavors)
    easy, fast, and fun?

Side note: That would be cool if they could do that, but I don't think
there will be 100s of free hobbist addins

Extension manager

-   "In Situ" experience for extensions
-   Simplified packaging and deployment

