After [Ray](http://blogs.geekdojo.net/jez) stole my thunder with his
[Concatination with
COALESCE](http://blogs.geekdojo.net/jez/posts/146.aspx), I guess I'll
have to post a different SQL script that I find handy.

Many times I see people that need to find how many times a string is
located in another instance of a string.  Normally the person figures
they will just loop through the string character by character and
increment a counter every time they find a match.  Not only is this
prone to error, in SQL it requires the use of cursor which is
“DoublyBadUnGood”^TM^.  Here is a quick little script that will get
around this:

DECLARE  @string varchar(100),\
         @temp   varchar(100),\
         @searchstring varchar(2)

SET @string = 'Ryan Rinaldi'\
SET @searchstring = 'R'\
SELECT @temp = REPLACE(@string, @searchstring, '')

SELECT (LEN(@string) - LEN(@temp)) / LEN(@searchstring)

This will come back with 2.  I know this might seem simplistic, but Hey!
It works! so this isn't much more that you really need.  @searchstring
can be any size, and this function would be quite easy to wrap in a User
Defined Function or similar.
