---
layout: post
title: mix10-ndash-windows-7-series-phone-architecture
---
Rearchitected from the ground up

Hardware Architecture

Capacitive touch – 4 or more contact points

Sensors

-   GPS
-   Accelerometers
-   Compass
-   Light
-   Proxmity

Camera

Multimedia

Memory

GPU

CPU

Only 2 resolutions

Software Architecture

Built on WinCE

MS is writing almost all of the device drivers instead of OEM

App updating, Licensing built in

New UI model

-   Shell frame
-   Direct3D

XBox LIVE, Bing, Location, Push notifications

Apps all built on CLR (no unmanaged code)

Silverlight, XNA, HTMl/JavaScript

Frameworks built for you to access all phone features

App Model

What is an app?

-   Uniquely identifiable and servicable product packaged as XAP

Application deployment

-   Windows phone marketplace

Application license

-   Crypto-verifable object issued to grant rights to the applications

Phone only installs .xap pakcages signed by marketplace

phone handles all aspects of .xap installation based on manifest

-   you cannot make arbitrary changes to the phone during install

Users control install, update and uninstall, while the marketplace
controls revocation

Phone only runs apps that have a valid marketplace license

Apps are sandboxed into separate security accounts while installed and
at runtime

Resource allocation policy keeps the foreground app responsive

Resource management policy ensures the user can always use Start to run
an app.

App hosting

-   Each app executes inside an isolated, least-privileged host process
-   all app code is transparent and CLS-verifiable
-   Frameworks enable app code to interact with app model, UI model,
    phone functionality

Frameworks

-   CLR
-   Silverlight
-   Device & phone
-   Cloud

UI Model

Concepts

-   Application – UI and logic for functionality exposed through pages
-   Page  a single screen of user interaction elements
-   Session – An ordered workflow of user interactions spanning
    applications

UI metaphor – Web

Sessions can be paged out when inactive.

Page State – Contains data that describes an instance of a page,
analogous to browser cookie

-   Allows the phone to discard all UI info when app is inactive
-   Rehydrates page ui based on Page State info

Graphics composition

-   Each page gets it’s own layer on top of the Direct3D  surface

Cloud Integration Services

built-in user experiences and APIs

Familar APIs for interactingwith existing web 2.0 services

Rich support for incorporating custom web services

Location Service

-   support for consuming GPS, AGPS and Wi-Fi based location
-   reverse geo-coding

Push notification service

-   Managed APIs for notification-driven interaction
-   When battery is low the service may shut down
-   This is not guaranteed message delivery.
-   Based on the state of the phone, message could be delayed, batched,
    or dropped.

Gamer Services APIs
