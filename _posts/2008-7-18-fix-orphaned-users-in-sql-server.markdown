---
layout: post
title: fix-orphaned-users-in-sql-server
---
Every time I restore a database, I forget how to fix the orphaned
users.  So I google, trying to find the magic words that will bring me
to that stored procedure that I know exists, but I just can't remember
the name of.  For those of you who don't know, sp\_change\_users\_login
has an 'Auto\_Fix' action that will map a user in a database to a login
of the same name. Since I'm going to forget all that again, I'm posting
this little snippet of Books Online.  Maybe Google will help me find it
next time!

sp\_change\_users\_login
========================

Changes the relationship between a Microsoft® SQL Server™ login and a
SQL Server user in the current database.

##### Syntax

**sp\_change\_users\_login** [ **@Action** **=** ] **'***action***'**\
     [ **,** [ **@UserNamePattern** **=** ] **'***user***'** ]\
     [ **,** [ **@LoginName** **=** ] **'***login***'** ]

##### Arguments

[**@Action** **=**] **'***action***'**

Describes the action to be performed by the procedure. *action* is
**varchar(10),** and can be one of these values.

Value

Description

**Auto\_Fix**

Links user entries in the **sysusers** table in the current database to
logins of the same name in **syslogins**. It is recommended that the
result from the **Auto\_Fix** statement be checked to confirm that the
links made are the intended outcome. Avoid using **Auto\_Fix** in
security-sensitive situations. **Auto\_Fix** makes best estimates on
links, possibly allowing a user more access permissions than intended.

*user* must be a valid user in the current database, and *login* must be
NULL, a zero-length string (''), or not specified.

**Report**

Lists the users, and their corresponding security identifiers (SID),
that are in the current database, not linked to any login.

*user* and *login* must be NULL, a zero-length string (''), or not
specified.

**Update\_One**

Links the specified *user* in the current database to *login. login*
must already exist. *user* and *login* must be specified.

\
 \
 \

[**@UserNamePattern** **=**] **'***user***'**

Is the name of a SQL Server user in the current database. *user* is
**sysname**, with a default of NULL. **sp\_change\_users\_login** can be
used only with the security accounts of SQL Server logins and users; it
cannot be used with Microsoft Windows NT® users.

[**@LoginName** **=**] **'***login***'**

Is the name of a SQL Server login. *login* is **sysname**, with a
default of NULL.

##### Return Code Values

0 (success) or 1 (failure)
