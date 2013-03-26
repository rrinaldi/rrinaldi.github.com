---
layout: post
title: ams352-best-practices-and-technques-for-migrating-asp-net-1-x-applications-to-asp-net-2-0
---
I was able to find a spot close to the wall for this session so I was
able to find some quality electric to keep MojoDojo running for this
session.

* * * * *

 
Migration Options
- Run 1.x and 2.0 web apps side by side
- RUn 2.0 in backward compatibility mode
- Convert your web app to 2.0
     - Use new 2.0 features
 
Changes since beta 2
- Excluded files
- file based assembly references
- CodeFileBaseClass attribute?
- XHTML validation
 
Partial Classes
- Allow a class to span more than one file
 
Excluding Files
- VS03: files and folders can be excluded from both build and source
control
- VS05 Added post beta 2: Allows files to be exluded from build but not
source control
- VS05 team system allows files to be excluded from source control
 
ASP.NET compilation model
- Compile using the asp.net compilier
- web app defined by files in a folder
- Multiple assembiles
 
Compilation model benefits
- improved performance at design time
- team develpment enabled
-project open is faster
- more deployment options
 - server side compilation
 - precompile and publish
 
I need to look into this Abstract base class generation.  Seems to use
some redirection to load the actual class at runtime.  The presenter
kinda blew right past that.  He just showed a code example, and I'm not
really sure why it's needed.
 
Before Migration:
- Get it running in VS03 and IIS first
- Set up sub-web apps (if any)
- Make a backup
- In a location other than your web app folder
- Open using the solution file if possible
- Review the web site architecture for possible VS05 conflicts
     - Multiple project files
     - Multple pages referring to the same code-behind file
     - Excluded files (include for conversation, exclude later)
     - Other projects referencing the web project (find them and make
note)
 
Things to look out for:
- References between user controls
- Mismatched tags are going to be a problem
- Extra classes in code behind files
- Resource access has changed, so be aware of using resource manager
- Changing the visibility on auto-generated code.
 
After Migration:
- Open using solutin file
- Turn batch compiling off
- Exlude files if needed
- Refactor your code for reserved word conflicts
 
The first paragraph in the migration tool is wrong.  It mentions that it
will check out all the code to perform the migration, while in reality
it will not.  You need to check out and check in the code when the
migration is completed. (How did wrong information get into the RTM? 
That is really a WTF)
 
The converstion report looks pretty slick.  Similiar to the SQL Server
2005 report, but the SS2005 one is a lot slicker.
 
Something that is labeled as an error is known to make the project
un-compileable (is that a word, cause he just used it).
 
Anything that is set to build action = none seems to confuse the heck
out of the conversion wizard.
 
He just mentioned that the conversion wizard was added late in the beta
2 cycle.  That doesn't make me feel very secure.  I'm sure it will be
fine, but I imagine there will be a lot of work to migrate any
non-trival app.
 
Batch mode compilation can sometimes hide some errors because you get
lucky. :) Since it is non-deterministic, you can sometimes have it work
on some machines but not on others.  Make sure to turn it off when
testing your app on 2.0.
 

* * * * *

 
I gave this session 45 minutes, but I heard anything that I haven't
heard before so I'm going to be taking off from this one.
 
Technorati Tags :
[DevConnections](http://technorati.com/tag/DevConnections)
 
 
 
 
 
 
 
 
