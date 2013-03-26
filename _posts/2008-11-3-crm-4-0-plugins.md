(Lisle to Union is going to be a recurring series.  I'm going to
**attempt**to write daily my thoughts on what I'm currently working on. 
As to the name "Lisle to Union"?  That's the train I take to get into
work every morning. :))

 

In my current project we are consuming data out of MS CRM.  Accounts and
contacts to be precise. Pulling data out to display it is relatively
easy using their web service apis and we are quite happy with the
result.  Having one silo-ed system that is in charge of a very specific
domain and requesting data from that domain from very well defined end
points jives with my line of thinking.

But, there is one problem with not having control over the domain.  The
problem is how do you find out about changes to data that you are
interested in?  Account name changes, contact name changes, merging of
entities, etc?  Luckily MS CRM has a rich plug-in model that allows you
to receive messages when "interesting" things happen in the MS CRM
pipeline.  I say "interesting" things because you can hook into every
event that you need.

When I first started looking into the MS CRM Plug-in model I first
thought "This so extensible that it is useless". The amount of
configuration and registration that is required is quite frightening. 
The awesome part is that the CRM 4 sdk has tools in it to make it super
easy.  They have a plugin registration tool that makes it a snap to
register a plug-in for the events you are interested in and a developer
tool that makes it easy to re-register any changes to your plug-in
during development. 

When you get a message from MS CRM you are passed a Context object that
contains the entity that changed (which was the entity you said you
wanted in the plug-in registration) and (here is the interesting part)
the **actual message that MS CRM processed**.  You don't get a "here is
the before and after" message (which is what I was expecting).  Since
all of the APIs MS CRM uses are all passed on the Command Pattern, the
easiest thing for them to do is pass you the command that it used.  In
all honesty I find this pretty slick. (and I'm happy that we are using
the Command Pattern in my current app (not through-out but in places
where we didn't want to play the game of "What has changed on my data
model?".  That is not a fun game to play.)

Unfortunately, for my first plug-in it seems I have tried to tackle one
of the hardest problems in MS CRM.  Entity Merging.  There aren't a lot
of examples out there for MS CRM and I can't find a single one for
entity merging.  As soon as I get it figured out I'll post more in depth
on it.
