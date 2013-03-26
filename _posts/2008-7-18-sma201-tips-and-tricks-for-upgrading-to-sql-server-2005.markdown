---
layout: post
title: sma201-tips-and-tricks-for-upgrading-to-sql-server-2005
---
Two types of upgrades: Migration and in-place
In-place upgrades an existing instance
Migration creates a new instance
 
Pre-upgrade work:
Check minimum hardware and software reqs
Check the differences in 2000 and 2005 skus - features are different
Run upgrade advisor
Examine any issues reported by the upgrade advisor
Fix or work around backward compatibility issues
 
Make sure to check backward compatibility list:
Discontinued features
Some features being deprecated
Catalog security changes
 
Upgrade advisor tool:
Improves sql server 20005 upgrade
Analyzes SQL Server 2000 and 7.0
Preforms readonly operations
analyzes objects
Provides reports for detected issues
Shows guidance on detected issues
Available in RTM or download from web
 
Continue running upgrade advisor until all it gives you the go ahead for
the upgrade. 
 
The upgrade advisor tool can check script files also
 
Upgrade advisor reports give line items that you can drill down into for
more info.  Each detail contains a link to a help file providing more
information on the issue.
 
CYA:
-Verify the backup before upgrading to 2005
-Create a back out plan
 
Pros of Migration:
-Migration provides more granular control over the upgrade process
-Having new and old instances side-by-side
-Legacy instance remains online during migration
 
Cons of Migration
-May require new or additional hardware resources
-Applications need to be directed to new instance
 
Pros of Upgrade:
- Easier, faster for small systems
-Requires no additional hardware
-Applications remain pointing to old instance
 
Cons of Upgrade:
- less ganular control over upgrade
 
Several migration techniques for Database engine:
- Detach/Attach
- Backup/Restore
- Copy Database Wizard, DTS
- Manual scripts, BCP
 
2000 and 2005 can co-exist on the same box
 
Management studio can live side by side with enterprise manager (yay!)
 
--------------------
 
My battery is dying so that is all we get for this one.  Hopefully I'll
find a spot near the wall for the next seminar.
 
Technorati Tags :
[DevConnections](http://technorati.com/tag/DevConnections)
 
