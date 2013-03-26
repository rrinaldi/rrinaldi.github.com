Morning on the third and "final" day of the conference.  Final being in
quotes because there are three post conference sessions on Friday. I'm
going to a C\# 2.0 and Visual Studio 2005.

* * * * *

(My blog editor decided to enabling double spacing on this entry for
me.  I didn't ask it to, and I don't have time to figure out how to
change it.)

Never used MSVSTO 2003, but according to the presenter (Ken Getz (sp)),
it was a good start but missed the boat quite a bit.

VSTO 2005:

- Microsoft stategic tool for devloping Office solutions:

      - Excel 2003

      - Word 2003

      - InfoPath 2003

      - Outlook 2003 add-in support

- Targetd at the professional developer

 

Develper Productivitiy

- Integrated desing-time experience

-"It allows you to react to events from office in managed code"

 

VB.NET is still the perferred language for office interop thanks to
optional parameter support.  Apparently VB still has a use. ( :) Hi
Eric! )

In VS 2005 when you create an Excel project it loads Excel inside a tab
of the VS. Even going as far as merging the menus. (At least they are a
sub-menu, but it looks really, really cluttered.)

For every object in the spreadsheet, VS creates a code file that acts as
sort of a code behind for that object (an object being a sheet or the
workbook itself)

VSTO creates a class called Globals that contains instances of all the
"code-behinds" that VS creates

 The link between the assemblies that interop with excel and excel
itself is stored in custom properties of the document.  These custom
properties can be deleted by anybody who has permissions to change
custom properties.

VSTO 2005 has two databinding controls (NamedRange, and ListObject) so
you don't need to loop through columns and rows to do your binding. 
Looks pretty sweet, and un-excelly which makes me happy. (Un-excelly
meaning it doesn't feel like I'm writing VBA code in .NET)

Writing UserControls to run in the task pane looks cool.  The document
is manipulated like and XmlDocument.  Tags are inserted into a document
and the usercontrol finds and replaces the tags with data. (Yum. Token
parsing, .NET style).

 

Host Items and Host Controls

- Host Items

     - Visual representation of a class

     - Provide a means for displaying data

- Host Items can contain Host controls

     - Excel: NamedRange and List Object

     - Word: Bookmark and XmlNode

- Native objects mapped into managed code

 

You don't need to even drag the NamedRange control onto the
spreadsheet.  Any named range on the site automagically becomes an
object.

Ken got bit by code access security during the presentation.  That is
probably going to be a problem for most developers.  I don't understand
Code Access Security very well, and I'm sure most other developers don't
understand it and so I think you are going to be seeing a lot of people
granting full trust to everything.  Not good.  MS needs to get on the
ball and figure out a way to teach CAS without putting people to sleep.

The VSTO com wrapper appears to hit COM way to soon for my taste.  When
you want to change fonts, it doesn't use the standard .NET Font
classes.  An Excel cell has a Value and a Value2 object, because that is
what the COM object has.

Bookmarks in Word: Apparently the normal bookmarks disappear after you
jack text into them.  The new, improved BookMark .NET object doesn't die
when you set the text.

What do host controls get you

-Promote items of interest into your programming model

- Office development feels more like .NET windows forms development

- Can handle events at control level, rather than at document level

- Can modify properties at design time

- All view controls support binding

      - ListObject supports complex data binding

- added "correct" functionality (like the bookmark example above)

      - but no existing code broken

There is no patch required to Office 2003 to run VSTO 2005 (Which means
that VSTO 2005 is a hack that sits above all of the COM entry points. 
So nothing was really "fixed", they just put in some extra code that
most people would have written anyway. IMHO)

Ken is going to show us how to show, edit and save data from a database
in Word.  Why, oh why would you write a word doc to edit data?

Binding seems very similiar to binding in other apps.

VSTO just blew up on Ken. :( Poor Ken.  His machine has been doing lots
of funky things during the presentation, so I'm choosing to blame him
and his machine for the problems and not Microsoft or VSTO. :) (See, I'm
being a good little MS fanboy!)

Demo gods are angry at Ken.  Ken is turning a rather flattering shade of
red.

Still working on that binding demo.  Ken abandoned the binding in Word
demo because he just can seem to get it to work.  Either VS crashes on
him or Word locks up. :(

All of this is very, very cool.  Maybe if somebody had to, no matter
what, work in Excel I would do some VSTO stuff for Excel.  I was really
hoping to see some Outlook stuff.  The outlook add-in / task pane is
where I see being able to add the most value.  I'm thinking like showing
a sales guy some customer information when he reads an email from that
customer.  Showing him/her things like: open support tickets, last
activity with the customer, products the customer has, and trials the
customer is partcipating in, etc.

Looks like I won't get to see any Outlook stuff. :( Ken is going to
start showing us some taskpane stuff, so maybe I can extrapolate that
into some stuff for Outlook.

(quick aside.  If you have VBA code and .NET code that both handle
similiar events (workbook loading for example) the order that the code
will run is non-deterministic)

All managed controls that are on a sheet are wrapped in an ActiveX
wrapper.

Why embed n ActiveX

- Secruity

- Registration

     - Rather use one wrapper instead of creating a shim for each
control

Whoops, everything that I've been calling a task pane is really called
an action pane.  So do a mental search and replace.

Action Panes host WinForm UserControls.  To add a user control to an
action pane, just add the control to the Controls collection.

We are running out of time, and I have to venture off to find my next
session.  I guess thats as much as I am going to learn about Action
Panes.

Technorati Tags :
[DevConnections](http://technorati.com/tag/DevConnections),
[VSTO](http://technorati.com/tag/VSTO)
