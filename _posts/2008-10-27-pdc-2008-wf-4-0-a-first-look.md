---
layout: post
title: pdc-2008-wf-4-0-a-first-look
---
(Ray and Richard are in the ultra-hip Ruby session. I'm taking this one
for the team.  I am not a fan of the current version of WF but I'm
hoping they made some changes that will make it more applicable to the
stuff we are trying to do.)

(They call it Dub-F and Dub-CF. WOW)

-   WF Basics
    -   3 parts
        -   Activities
            -   Arbitrarily Composable
            -   Top most Activity is the workflow
            -   Activities are structured data (written in XAML)

        -   Runtime
            -   Lightweight managed runtime for activities
            -   Services
                -   Persistance
                -   Tracking

            -   Tooling
                -   VS Designer
                -   VS Debugger
                -   Rehosted Designer (is this new???)

    -   Data flows into and out of Activities as Arguments
    -   Data can be stored across Activity boundries as "Variables"
    -   Activities can bind to any variables in scope
    -   Variables define the active state
    -   OOB Library of Activities
        -   Flowchart
        -   sequential
        -   state machine
        -   rules
        -   Base Activity Library
            -   BPEL
            -   Utilities
            -   Expressions
            -   Error Hanlding
            -   Database
            -   WCF messaging

        -   Custom Activities
            -   Sharepoint
            -   Dynamics
            -   Systems Center
            -   HPC
            -   TFS (I think this is in Team Build, they didn't mention
                that but I read that before)
            -   YOUR CODE HERE

-   Why Else use workflow
    -   Coordinate Work
    -   Write Persistable Applications
    -   Gain Visibility into your application
    -   Customizable Vocabulary and design experience

-   State.Get and State.Set to manage state
-   WF Can coordinate work
    -   You create the logic
    -   You orchestrate it with WF

-   Persistable Applicaions
    -   Workflows are persistence-enabled for free
    -   if you need control it's available
        -   Persistence Provider
        -   Typically handled by the host
        -   Explicit persistence points
        -   Support for no-persist zones
        -   Host Extensions can participle in persistence

    -   WF adapts to mid-stream process changes

-   You can make changes to apps that are already persisted.  Pretty
    cool.
    -   As long as the workflow activity you are changing isn't the
        active activity in any persisted app

-   Visibility into your app
    -   Rich debugging  for running instances
    -   Can schematize persisted state

-   Authoring is simpler
-   Fully declarative
-   Alignment across Expressions, Rules and Activities
-   Runtime is 10-100x faster
-   Flow-in Transactions (???)
-   Integrates with WCF, WPF, ASP.NET
-   Rehosting improvements
-   Designer Performance
-   Unified Debugging experience
-   WF was rewritten from the ground-up
    -   The stuff they wanted to do for 4.0 wasn't possible on 3.0
    -   3.0/3.5 workflows continue to work
    -   Can use 3.0 Activities within 4.0 workflow
    -   Guidance on how to prepare 3.0/3.5 code

-   No more CodeActivities or Code Besides
-   80x reduction of code
    -   Less management of activities
    -   system handles all the complex stuff

-   You need an interop activity to use 3.0/3.5 code. 
    -   Not an issue for us. We don't use it! :)

-   Trident Scientific Workflow from MSR WF 4

