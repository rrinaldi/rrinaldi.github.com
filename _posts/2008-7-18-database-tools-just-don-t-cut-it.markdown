---
layout: post
title: database-tools-just-don-t-cut-it
---
I don't like databases any more.  I'm tired of them.  They just don't do
it for me any more.

In my opinion (which means you should probably ignore it), database
tools just don't make sense in enterprise development today.

"Blasphemy!", you shout.

Hear me out for a second.  I'm not saying you shouldn't use them, or
that there is some other magical solution for storing data that is
better.  I'm saying that the way we work with them doesn't match the way
you work with all of the other tools that you use.

Lets say you are given a new feature request to work on.  One of the
first things you do is create a new branch in source control.  You start
hacking away at your code, until you realize that there is a need to add
a new field to the database.  Right away there is a problem.  Do you add
the field to a shared development database?  Well, if you do you have no
control over the state of the server.  It could be up, it could be
down.  That's no good.  So you add the field to your own personal
development database.  That works pretty well.  You have control over
the state of the server, you know that when a query doesn't return right
away it's because you screwed up and not another developer.  All in all
it seems like a good solution.

So you go hacking away at the code, adding new fields to the database,
add a couple new procedures, change some other ones and add a few
views.  Some time passes and now it's time to promote your new feature
to QA.  So you merge your code back in, and up pops a window so you can
manually merge in some changes that are conflicting but for the most
part all of your changes were automatically merged in.  Now comes the
time to update that QA database.  What changed from your version to the
one in QA?  How many new fields have been added?  How many procedures
have been changed?  Have fun finding out, since it's mostly a manual
process.  It's error prone and, quite frankly, scary.  I know I hate it.

What I want is to see a system that can branch and merge database schema
integrated directly into the tools that come with SQL Server (whether
that is Enterprise Manager or SQL Workbench (whatever it is called in
2005)).  Is that asking a lot?  Yeah, but I think it's about time.

Maybe I'm a dreamer, but I know I'm not the only one. :P
