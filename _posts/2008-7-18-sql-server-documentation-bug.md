---
layout: post
title: sql-server-documentation-bug
---
At work I needed to find a way to store an obscene amount of text in our
database.  Either I could use a varchar(7000+) datatype or I could shoot
performance in the head and use the text datatype.  The problem was that
most of the time there wouldn't be more than, say, 500 characters.  I
didn't want to use text for that.  Seemed way overkill.  But I did need
to store an unlimited amount of text.  It was in the specs and as we
all know, the specs are never wrong. 

I did some digging and came upon the "text in row" table option.  After
reading about it, I remembered hearing something about it when I was a
regular on the SSWUG mailing lists.  Looking even deeper, it seems
perfect.  Store the data in the row until you run out of room, then when
need be (you run out of room in the row) bounce over to using a pointer
and out of row storage.  All automagically! Sweet!  What is even cooler
is that you don't need to worry about that WRITETEXT, UPDATETEXT, get a
pointer to my data bullcrap.  Just pretend it's a varchar field (that's
what the first doc I read said).  That makes my life easy.  And I like
easy. 

Then I notice that another doc completely contradicts the first doc I
read.  Well that isn't good.  That makes my life hard, and I don't like
hard. Here are the two contradictory statements:

When you look up the stored procedure "sp\_tableoption" (which you use
to turn on "text in row") it states:

"**text in row** supports the **TEXTPTR**, **WRITETEXT**,
**UPDATETEXT**, and **READTEXT** functions. Users can read parts of a
BLOB with the SUBSTRING() function, but must keep in mind that in-row
text pointers have different duration and number limits than other text
pointers."

When you look up "Text in Row Data" it states:

"After you have turned on the **text in row** option, you cannot use the
READTEXT, UPDATETEXT or WRITETEXT statements, to read or modify parts of
any **text**, **ntext**, or **image** value stored in the table. In
SELECT statements you can read an entire **text**, **ntext**, or
**image** string, or use the SUBSTRING function to read parts of the
string. All INSERT or UPDATE statements referencing the table must
specify complete strings and cannot modify only a part of a **text**,
**ntext**, or **image** string."

hmmmm.

Which one is right?  I guess that depends on your definition of the word
"right".  If by right you mean "correct" then the second one.  If by
"right" you mean "completely and horribly wrong" then the first one is
the one you want. 

After some testing, it seems that you cannot use any of the text only
statements on a text datatype after "text in row" has been set.  Here is
the script I used to try it out:

CREATE TABLE [TextFieldTest1] (\
  [TextField] [text] NOT NULL\
 ) ON [PRIMARY] TEXTIMAGE\_ON [PRIMARY]\
 GO

CREATE TABLE [TextFieldTest2] (\
  [TextField] [text] NOT NULL\
 ) ON [PRIMARY] TEXTIMAGE\_ON [PRIMARY]\
 GO

SELECT TextField AS Test1 FROM TextFieldTest1

SELECT TextField AS Test2 FROM TextFieldTest2

INSERT INTO TextFieldTest1 VALUES ('Insert Test 1')

INSERT INTO TextFieldTest2 VALUES ('Insert Test 1')

exec sp\_tableoption 'TextFieldTest2', 'text in row', 'ON'

INSERT INTO TextFieldTest1 VALUES ('Insert Test 2')

INSERT INTO TextFieldTest2 VALUES ('Insert Test 2')

DECLARE @ptrval1 binary(16)\
 SELECT @ptrval1 = TEXTPTR(TextField) FROM TextFieldTest1

\
 DECLARE @ptrval2 binary(16)\
 SELECT @ptrval2 = TEXTPTR(TextField) FROM TextFieldTest2

WRITETEXT TextFieldTest1.TextField @ptrval1 'WRITETEXT Test 1'

WRITETEXT TextFieldTest2.TextField @ptrval2 'WRITETEXT Test 1'

SELECT TextField AS Test1 FROM TextFieldTest1

SELECT TextField AS Test2 FROM TextFieldTest2

DROP TABLE TextFieldTest1

DROP TABLE TextFieldTest2

You'll see that it will throw an error when you try to get a TEXTPTR
from the TextFieldTest2 table.
