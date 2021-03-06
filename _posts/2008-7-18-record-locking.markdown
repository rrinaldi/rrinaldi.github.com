---
layout: post
title: record-locking
---
On my most favoritest SQL Server mailing list, SSWUG, the question came
up if it was possible for SQL Server to maintain a lock on an accessed
record after a client disconnects from the server.  The question also
asked that if it wasn't possible currently, would it be possible in next
version of SQL Server (Yukon).  The quick answer is no, it's not
currently possible.  Although I cannot speak for the availability of
this “feature” in Yukon, I can't fathom why anybody would ever want it
in the first place.  Most developers I know already know that having SQL
server maintain a lock for a client (Pessimistic locking) is evil.  But
since this developer was looking for this functionality, I figure that
it's not as widely known as I thought (or hoped).  I figure I'll give a
little bit of an explanation as to it's evils here, in the hopes that
someone will stumble upon it.

Pessimistic Locking requires the a database server (or application code
in the database server) to make unavailable certain records of data when
they have been "checked out" for editing by an application.  This
application could be anything: a Windows application, a WebForm, a
console app, a Web Service.  When the application is done with it's
editing, it sends the data back to the server and the server unlocks the
now updated records.  This would seem like a wonderful solution to
concurrency issues, but it falls apart rather quickly.  What happens
when the application never connects back to the server?  Now we have
records locked in perpetuity.  Depending on the granularity of the lock,
and how vital that record is to the system, you could now have a
completely unresponsive application as it waits for a lock to be
released.

Your best bet is optimistic locking.  That is letting the data be
checked out by multiple parties, but validate that the data has not
changed since retrieval. 

Meaning:

1.) Get data

2.) Manipulate data

3.) Right before save, check to make sure data is the same as it was
when data was retrieved.

4.) Save data.

This can easily be done by using a timestamp or GUID on the row that
changes when any data is changed, or compare the data retrieved, column
by column, to the data that is currently stored.

Optimistic locking also allows an application to verify different data
for different situations.  Maybe you don't want a parent record to be
saved if the children have been updated?  With pessimistic locking, this
would involve locking multiple records in multiple tables.  With
optimistic locking, it just involves the retrieval of extra data and a
quick check right before a save.
