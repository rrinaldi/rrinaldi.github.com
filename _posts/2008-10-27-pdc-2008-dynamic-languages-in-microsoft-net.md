(Battery died during Anders' talk.  Now I'm sitting all alone in the
back of the Dynamic Lanaguages talk by the water cooler stealing some
electricity. :))

 

Dynamic versus Static: WAR! Not really, but people think so.

They (They being MS) is working to bring the two together with the DLR. 
On top of the DLR you have IronPython and IronRuby and now the dynamic
features of C\# and VB.NET (There is talk of an IronScheme).

Things the DLR will give us: Expression Trees, Shared notion of Dynamic
Dispatch and Call Site Caching

DLR is open source

-   OSI Approved
-   DLR is on CodePlex
-   DLR will be in .NET 4.0 and VS2010 (AWESOME!)
-   Future stuff will be on CodePlex, maybe making it into product at
    some time

IronPython 1.0 is faster than Python 2.5 (Python 2.5 is written in C)

Extending Python is super easy in C\#

Python to C and C to Python is pain.  2 different object models

Python to C\# is easy. 1 object model, 1 garbage collector

When to use IronPython

-   Rapid prototyping
-   Python has a lot of libraries
-   Personal tools
-   Test suites
-   build and deployment scripts

The meaning of Iron

-   True Language Implementation
-   True to the community
-   True to the experience
-   Excellent performance
-   Great integration with .NET
-   **I**mplemention **R**unning **O**n .**N**ET

Things coming up

-   Script Hosting
-   Compiler as a Service

Dynamic Dispatch

Multiple language dynamic dispatch

x.Foo turns into GetMember Name = Foo, IgnoreCase = false that the DLR
uses in an object binder

Easy to write your own binder

Common Actions

-   GetMember
-   SetMember
-   DeleteMember
-   UnaryOperators
-   BinaryOperators
-   Convert
-   InvokeMember
-   Invoke
-   CreateInstance
-   GetIndex
-   SetIndex
-   DeleteIndex

Implement System.Dynamic.DynamicObject (I'm totally going to abuse this)

-   easiest way to play in the dynamic pool

Demo of writing a dynamic dispatch object in C\# and calling it from
IronPython

-   Now showing how to add a method to a dynamic object (So cool.)
-   Loading the C\# assembly into Python and newing up the Bag object
    and calling methods and setting properties on it.

System.Linq.Expressions v2

Start with LINQ Expression Trees

-   Not really, had their own implementation but almost done getting it
    converted to LINQ

Add assignment

Add dynamic nodes

All the languages can be mapped to the new and improved LINQ expression
trees

Different Semantics

x \* 2

-   Assume x = 2 billion
-   In Dynamic Languages that is 4 billion
-   in C\# it's -294 million and something
-   We all know why.

Trees

-   Analyzable, transformable and composable
-   Shared tree form with language semantics
-   Optimized machine code
-   Code is collectable
-   Great way to deal with generated code at runtime

Callsites

Old Idea: Polymorphic Inline Cache (What?!?!)

-   Implemented with delegates and generics
-   No changes to CLR

Major addition: multiple lanagages on CLR

-   Interop for sharing objects
-   Customizable

CallSite\<T\>

-   I'm kinda lost here.  Must learn more about CallSites

This makes dynamic dispatch fast in .NET

Binders work with MetaObjects

Static Objects = fast

DynamicObject uses strings. :(

So build a MetaObject for your objects/language.

-   You generate the trees
-   It's hard
-   It's error prone

Implement IDynamicObject instead of DynamicObject

Must implement a handful of methods on MetaObject
