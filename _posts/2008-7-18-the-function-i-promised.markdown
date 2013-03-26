---
layout: post
title: the-function-i-promised
---
Well, I really didn't promise it but I had some free time at work
waiting for Visual Studio .NET to repair itself. (Why does uninstalling
Visual Studio .NET 2002 kill the file associations for Visual Studio
.NET 2003?  Can someone explain that one?) Anyway, without further ado I
give you the function:

CREATE FUNCTION dbo.fnInStringCount(\
 @string varchar(1000),\
 @searchstring varchar(100)\
)\
RETURNS int\
AS\
BEGIN\
 DECLARE @temp varchar(1000)\
 SET @temp = REPLACE(@string, @searchstring, '')

 RETURN (LEN(@string) - LEN(@temp)) / LEN(@searchstring)\
END

SELECT dbo.fnInStringCount('Ryan Rinaldi', 'R')

I ask only one thing.  That if you find this useful, let me know.  :)
