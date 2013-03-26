---
layout: post
title: dialogs-windows-events-oh-my
---
Anytime you give a user a list of items to choose from there is always
going to be the problem of what to do when the item the user wants is
not in that list (dropdown, select box, what-have-you).  You normally
have two options that you can implement. 1.) Have the user leave the
page and enter the item they want in the item creation page.  2.) Allow
the user to open up a dialog and create the item right there.  Both of
these options leave little to be desired.  For instance take the first
option, have the user navigate to the item creation page and enter the
data there.  That’s all fine and dandy, except all the work the user has
done on the page up to that point is now lost.  Not a very good user
experience there, now is it?  Now take the second option, let the user
pop open a dialog screen to enter the data.  At first glance, that ’s
great since now the user hasn’t lost any work, and the item has been
created.  But now how do you update the original page with the newly
created item?  If you have the dialog simply call a
opener.location.reload(); when it’s done with its work you run into the
same problem of the first option.  All the work that the user has done
up to that point is now gone.  You can’t have the dialog window just
close, because then the information that the user is looking at hasn’t
been updated.  What you (and I) need is some sort of event that we can
capture that tells us the dialog is done with its work and we can reload
the item list.  Well, today I created just that. 

First let’s create some method that we can call when the dialog is done
doing its dirty work.

protected virtual void PageComplete(string args)\
  {\
   if( Request.QueryString["targetMethod"] != null)\
   {\
    string script = @"window.opener." +
Request.QueryString["targetMethod"] + "(window, " + args + ");";\
    Page.RegisterStartupScript("\_clientEventHandler", "\<script\>" +
script + "\</script\>");\
   }\
  }

The method is pretty simple.  Check to see if a targetMethod is present
in the request collection.  If targetMethod exists, lets output some
JavaScript that will call that method on the dialog window opener.

The second thing we need to know is how to call the dialog so that we
will get a callback from the window when it’s done.  This is SO simple,
but I figure I’ll give an example just in case someone out there needs
it.

http://..../dialogWindow.aspx?targetMethod=dialogEventHandler

So now that the dialog window is going to call a method on the opener
window, we need to write one.

function dialogEventHandler(sender, args) \
{ \
    var target = document.getElementById("\<%= buttonToClick.ClientID
%\>"); \
    target.click(); \
    if( sender != null) \
    { \
        sender.close(); \
    } \
}

As you can see, this function takes in 2 arguments very similar to an
event handler in .NET.  The first argument is a reference to the window
that called the function (the dialog window), and the second argument is
going to be populated with any arguments that you might want to pass
from the dialog window to the function (in our case, it was obvious that
we wanted to get the newly created items ID so we could select it
automagically for the user). 

The last thing you’ll need to setup is something that you can trigger
client side that will cause an event to be fired server side.  My
preferred method is to create a button on the page and then hide it
using styles.

\<INPUT id=buttonToClick style="DISPLAY: none" type=button\>

I find this a pretty easy, yet powerful way to manage dialog windows. 

If you find this useful in any way, let me know!\

