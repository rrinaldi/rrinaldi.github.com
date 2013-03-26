---
layout: post
title: pdc-2008-the-future-of-c
---
(Battery dying, this might be incomplete)

December is the 10th anniversary of the inception of C\#

Some history:

1.0: Managed Code

2.0 Generics

3.0 Language Integrated Query

 

Trends that shaped the thinking of C\#:

Dynamic

Declarative

Concurrent

 

Languages now borrow from each other, nothing is purely dynamic or
functional or OO, etc anymore.

 

Declarative Programming: More that What less of the How.  When you state
the "What" the framework can take care of the how.

Dynamic Languages: You want attributes of both static and dynamic. 
Dynamic languages can be faster to write, simpler to understand.

Concurrency: Moore's Law let us stick our heads in the sand.  Time to
worry about going parallel.  There will be no "/concurrent" switch that
can do it.  It's hard and you have to think about it.

 

Anders mentioned the Parallel Extensions Framework for .NET.  Need to
look into this.

 

VB versus C\#: Co-Evolution. When features are introduced into one
language they will work to introduce that into the other.  There are no
guarantee but they will make sure that the feature isn't "impossible".

 

C\# 4.0:

Dynamic: Dynamically Typed Objects, Optional and Named Parameters,
Improved COM interop, Co and Contra variance. (Yay!)

C\# and VB will both get support to use the DLR (Dynamic Language
Runtime)

Binders: Object, Javascript, Python, Ruby and COM. Binders enable C\# to
talk to Dynamic Languages.

 

Dynamically Typed Objects: "Statically typed to be dynamic" (LOL)

Anders: Things should be able to be "dotted into"

New psuedo keyword: "dynamic" dynamic i = 42;

When operands aare dynamic: Member selection deferred to run-time, at
run time actual type(s) substituted for dynamic.
