---
layout: post
title: backup-registered-sql-servers-from-em
---
Here's a little trick if you are building a new machine and you don't
want to manually re-register all of the servers you currently have in
Enterprise Manager on your new machine.  Backup the registry key

HKEY\_CURRENT\_USER\\Software\\Microsoft\\Microsoft SQL Server\\80
Tools\\SQLEW\\Registered Servers X

and restore it to your new machine.

Easy as pie.
