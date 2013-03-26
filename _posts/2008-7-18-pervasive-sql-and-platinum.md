For the past couple days I’ve been working on an integration project
with [Platinum for Windows](http://www.bestsoftware.com/pfw/).  Platinum
uses a file based database engine called
[Pervasive](http://www.pervasive.com/).  Before this project I’ve never
really heard of it before, except in passing.  Having never worked with
a file based database before, I’ve found a few things quite interesting:

1.) Each table in the database corresponds directly to a file in a
directory.  In the documentation the terms table and file are used
interchangeably which can sometimes get quite confusing.

2.) Since each file is a table, the documentation explains exactly how
the data is laid out in files.  I believe the expectation is that you
will be modifying files directly at some point.

Pervasive apparently has a limitation on the number of letters in a file
name, which leads to table/file names like “ARLIN” and “ARTRAN”.  ARLIN
is a “Accounts Receivable Line Item” and ARTRAN is “Accounts Receivable
Current Transaction”.  Sometimes an H is appended to the end of the file
name.  This could mean that it is a Historical table/file or if contains
Header information for another table.

Another problem is that Pervasive’s SQL is quite limited.  I was trying
to do a few ad-hoc queries to get an idea of the data we have, and
things like adding and subtracting numbers and converting between data
types are completely foreign concepts to Pervasive.

For the most part though, it looks to be an interesting project.  I’ve
already learned more about Accounting than I ever really planned on
knowing. ![](http://blogs.geekdojo.net/ryan/images/smile1.gif)

 
