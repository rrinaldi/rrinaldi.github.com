---
layout: post
title: want-to-rename-the-junk-e-mail-folder-in-outlook-2003
---
Well you can't.

I just upgraded to Office 2003 today and so far I like it.  Outlook 2k3
is fan-freakin'-tastic.  Almost a lickable interface. (The shnozberries
taste like shnozberry.)

Since I use
[SpamBayes](http://blogs.geekdojo.net/ryan/posts/219.aspx) for Spam
filtering I had a folder named Junk Suspects and another named Junk
E-mail.  After upgrading to 2k3 I now had another named Junk E-mail1
that Outlook was going to use to store Spam.  This was not acceptable. 
I figured I would just delete that folder and tell Outlook to use the
existing Junk E-mail folder.  Well, you can't customize where Outlook
stores it's Spam.

Since I couldn't change that setting I changed SpamBayes to point to the
new Junk E-Mail1 folder and I deleted the Junk E-Mail folder.  I assumed
that I would be able to rename the Junk E-Mail1 folder.  When you rename
or move folders in Outlook, Rules and plug-ins that use those folders
automagically point to the new folder, so I didn't think there would be
any problems renaming it.  Well Outlook won't let you rename it.

After searching for awhile, I came across [this KB
article](http://support.microsoft.com/default.aspx?scid=kb;en-us;296192)
describing the Outlook commandline switches.  It seems that the switch
/ResetFolderNames will rename all the special folders back to their
default names.  For me that's all I needed.  Running Outlook with that
switch renamed Junk E-Mail1 back to Junk E-Mail and allowed be to be
sane again.

If you want to change the name to anything else, you seem to be SOL for
now.  Probably one of the dumbest decisions I have seen.  Why *wouldn't*
you let someone rename that folder?  Maybe they wanted to name the
folder “Spam” or “Evil mail go here” or “BAD”?  Whatever the reason
Outlook should allow it.

So, if you are upgrading Outlook 2000 to 2003 and you use SpamBayes
you'll need to do the following so you can only have one Spam folder:

-   Delete the folder “Junk E-Mail“
-   Point SpamBayes to the “Junk E-Mail1“ folder
-   Close Outlook
-   Run Outlook with the /ResetFolderNames switch.

The command line that you run should look something like this:

"c:\\Program Files\\Microsoft Office\\OFFICE11\\OUTLOOK.EXE"
/ResetFolderNames

After that everything should be fine.
