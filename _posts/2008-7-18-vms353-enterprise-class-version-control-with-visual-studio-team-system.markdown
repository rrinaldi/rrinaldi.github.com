---
layout: post
title: vms353-enterprise-class-version-control-with-visual-studio-team-system
---
Just finished lunch.  I'm currently chilling in the session room waiting
for the session to start up while watching my wireless connection go up
and down.  At least they provided a connection for us at the convention
center, in the hotel you need to pay 12 bucks a day for internet access.
\*sigh\*
 

* * * * *

 
Aside: MS seems to use the term "A deep dive look" a lot lately.  New
buzz word hmm?
 
Ajay is currently going over the features of Team System and Team
foundation server.  This is stuff I've already heard.  I'm hoping he
will be getting into the meat of the version control soon.....
 
 
Foundation Server's Guiding Principles:
- Productive
      - short learning curve
      - minimal administratvie overhead
- Integrated
     - Tools integrated tightly
     - automates common tasks
- Extensible
     - Customizable for your process
     - Integrates with 3rd party tools
 
Source Control:
- New version Control System
      - Build new
      - 3 tier ASP.NET web service
      - SQL Server 2005 data source
- New Features
      - Integrated checin
      - Shelving
      - Source Control Explorer
- Built for the enterprise
      - Support for distributed teams
      - Secure, Reliable, Scalable
      - Future tool for Microsoft
 
Able to view builds, see the work items related to a build, what
check-ins are in a build.
 
Shelving sounds cool.  Shelving allows you to place all of your code
back into the repository but not completely checked in so you can get
the latest code, do an emergency bug fix then get your shelve-set back
and merge the bug fix back into your local copy.
 
It's about time Microsoft dog-fooded a source control system!  The
eventual goal is for all of Microsoft to move to team system.
 
All check-ins are atomic.  Either all files that are part of a check-in
will be committed or none of them are
 
Work Item Integration: During check-ins you can choose which work items
are tied to that check-in
 
Check-in Policies: Team System will ship with a few check-in policies. 
This will allow you to create rules that govern all check-ins to the
code base.  Anything from code analysis to work item tracking.
 
Delta File Storage: Team System stores reverse deltas for all files.  
Meaning that TS keeps the lastest version and has the changes that would
take you all the way back to the first version ever checked in.
 
Email notification support: Sweetness. nuff said.
 
Non-Windows support: not a big deal for me, but could be useful for
some.  Almost all of the support is from 3rd party ISVs
 
Diff Tool extensibility: Uses Source Safe diff tool by default. Ewwww. 
Can be replaced through extensibility.
 
Shared Checkout: We use exclusive but I'm glad that Team System "Goes
both ways" so to speak.
 
VS 2003 integration: Wonderful!!!
 
Keyword expansion: Don't got it. :( Not a big deal.  There is ton of
auditing, so you can find that info in other places.
 
Pinning and Sharing: Don't got it.  :) 
 
Shadow Folders: Don't got it.  Never used it. Don't care about it.
 
Time for the demos!
 
Technorati Tags :
[DevConnections](http://technorati.com/tag/DevConnections)
 
 
 
 
 
 
 
 
 
