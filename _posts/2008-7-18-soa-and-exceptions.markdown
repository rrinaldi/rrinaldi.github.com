---
layout: post
title: soa-and-exceptions
---
So [Ray](http://blogs.geekdojo.net/ray) and I were discussing SOA at the
office today and trying to figure out how to handle exceptions
gracefully.  When you get an exception from a webservice all you get is
a
[SoapException](http://msdn.microsoft.com/library/default.asp?url=/library/en-us/cpref/html/frlrfSystemWebServicesProtocolsSoapExceptionClassTopic.asp). 
That doesn't tell you much.  Take this example:

1.  Add new user to application
2.  Application calls AddUser service
3.  AddUser service attempts to add the user to the database
4.  Database throws a primary key violation
5.  AddUser throws a DuplicateUserException internally
6.  The webservice returns a SoapException that contains the text of the
    DuplicateUserException.

At this point I have a SoapException that I can't do anything with.  I
have no clue why it was thrown. The DuplicateUserException is completely
lost. [Well, almost lost.  It's in the Message property of the
SoapException.  Should I have to parse the string to find it? That seems
so totally wrong.]  What if I want to tell the user something other than
"It no worky, try again.  Maybe it worky now."

 

We worked around this problem by returning status codes, but that is SO
HRESULT-ish that it makes my skin crawl.  There has to be a better way
to make this work.  Did we miss something?  Is there something obvious
that I am overlooking? Can some of you SOA guys shed some light on this
for me?
