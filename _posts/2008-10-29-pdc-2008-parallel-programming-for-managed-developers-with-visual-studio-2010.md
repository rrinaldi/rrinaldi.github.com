(Holy long session name Batman!)

Tools shipping in 2010

-   PLINQ
-   Task Parallel Library
-   Concurrency Runtime Threadpool
-   Parallel Debugger tool windows

Demo of a Ray tracer running in Serial versus Parallel

Hardware manufactures are talking about 80 to 100 cores on the desktop

-   Now is the time to go parallel

Threding/Concurrency versus Parallel

-   Concurrency versus Exploitable concurrency
-   To actual improve performance you need to go multi-core

Yay! This is a "mostly-code" demo

Fine Grained Parallelism Demo: From thread based to Task Based

Creating a tree with 1003 nodes

Processing takes 15 seconds or so

If you create threads each thread requires 1 meg of memory

Parallel framework handles creating threads (1 per core)

-   Now the program takes 3 seconds

User mode scheduler for tasks

Each thread has a local queue so if a thread creates a task it stays on
it's thread

-   If a thread has nothing to do, it steals work from other threads
    queues but always from the back of the queue

Task has some helper methods that helps manage tasks and waiting for
task completion

Tasks are lightweight.

Tasks.ContinueWith takes a lamda and calls it when the task is
complete.  Can be used for chaining

When a task creates tasks it has a parent child relationship, Task A
cannot complete until it's child tasks do. Unless you specify that the
child tasks are Detached

Tasks support Cancellation

Task objects also supports methods that return data

Tasks that return values are called Futures

-   Only in the CTP, in RTM it will be called Task\<T\>

System.Threading.Tasks

-   Has all the Parallel framework stuff

Demo of the Parallel Debugger Tool Windows

If you look at the Threads window you have to check the callstack of all
the threads window

Introduced the Parallel Tasks Window

-   Fully integrated

Also have a Parellel Stacks Window

-   This is super awesome.
-   Like really. Over the top, super cool Thread and Task visualization

Battery is dying, so I'm out.  Hopefully I'll find power at my next
session.
