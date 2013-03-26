A co-worker of mine asked me today if there was a way to compare 2
strings for equality in SQL Server but make the comparison case
sensitive.  Of course there is!  Some of you may know this little trick,
but since I see this post on mailing lists and now in my office I
figured I would post it here.  The secret is casting the values to
varbinary.  Run this little SQL Script below and see the magic in
action:

DECLARE @nameOne varchar(10)\
DECLARE @nameTwo varchar(10)

 

SET @nameOne = 'Ryan'\
 SET @nameTwo = 'RYAN'

 

IF @nameOne = @nameTwo\
 BEGIN\
 PRINT 'They are the same!'\
 END\
 ELSE\
 BEGIN\
  PRINT 'They are NOT the same!'\
END

 

IF CAST(@nameOne as varbinary) = CAST(@nameTwo as varbinary)\
 BEGIN\
 PRINT 'They are the same!'\
 END\
 ELSE\
 BEGIN\
  PRINT 'They are NOT the same!'\
END
