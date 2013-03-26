---
layout: post
title: agn203-why-you-need-to-use-a-code-generator-in-asp-net
---
So tired.  So very very tired.  Using your brain all day then going out
at night really takes a toll on you.  And by the looks of most of the
people here, I'm not the only one.  The line for coffee has been getting
steadily longer every day. :)

* * * * *

Harold Chattaway is presenting and he says this session is going to
cover code generating everything from the data access to the UI. I've
always been interested in code-generation so it should be interesting to
see another persons ideas on how to approach it.
 
Why code-generators
- Large part of devlopersjob is repetive, assembly line coding
- Being consistent with naming conventions
- List view froms and edit moduls are perfect canditates
- conventional manufacturing has models that are made to create a
perfect product
- Templates serve the same purpose as these molds
 
(Harold has a nice pace to the session.  Makes it easy to take notes!)
 
What can code-generators be used for
- Everything! Aspx code behinds, aspx files, user controls
- Dal code
- CRUD sprocs
- in short anything that you do more than once could be a candidate for
a code generator
 
Tools available
- MyGeneration
([www.mygenerationsoftware.com](http://www.mygenerationsoftware.com)) :
Free
- CodeSmith ([www.codesmith.com](http://www.codesmith.com)) : \$299
- OlyMars
([http://www.microsoft.com/france/msnd/olymars/default.mspx](http://www.microsoft.com/france/msnd/olymars/default.mspx))
: Free
 
I've used OlyMars before and I haven't been impressed (and it's sql
server centric)
 
Harold recommends MyGeneration over CodeSmith. He says it has a better
dev environment.
 
Model first, tooling second!
-Develop the piece of code first, then convert to template
 
MyGeneration has a ASP like syntax. (I believe CodeSmith also does, but
it has been awhile since I've used it)
 
Up on the screen is MyGeneration right now, and we are getting a quick
tour of the app.  This thing is comp-li-cated.  Hopefully my shock will
wear off and I'll actually start to understand what he is talking about,
but currently my mind is reeling from the sight of all the dropdowns,
textboxes, checkboxes, and radio buttons on the screen.
 
MyGeneration supports running code generation files in a batch mode.
 
Everything Harold is going over right now I already know.  :(  I had my
fingers crossed hoping that he would go into some dynamic code
generation.  He seems to be a big fan of static generation, which is
great and can make life easy by allowing you to create a site during the
build process, but I've been looking at how to dynamically generate a UI
given an arbitrary object graph and I was hoping that he might go into
some depth there.
 
(It's really hard to write good notes when you are bored and tired. :( )
 
Technorati Tags :
[DevConnections](http://technorati.com/tag/DevConnections),
[CodeGeneration](http://technorati.com/tag/CodeGeneration)
 
