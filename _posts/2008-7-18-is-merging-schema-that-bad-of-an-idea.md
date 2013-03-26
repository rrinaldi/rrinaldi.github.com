The other day, I posted about my ideal concept of [source control for
database
schema](http://blogs.geekdojo.net/ryan/archive/2005/05/17/8343.aspx) and
I got a few interesting comments. 

A lot of people recommended Red Gate Software’s [SQL
Compare](http://www.red-gate.com/SQL_Compare.htm) tool.  I have been a
customer of Red Gate for awhile and I’m quite happy with SQL Compare. 
It comes quite close to being the perfect tool for merging database
schema and objects.  Where it falls a little short is when updating
stored procedures and views.  It doesn’t actually merge the procedures
and views.  You have the choice of migrating your version of the object
or not.  What I would like to see is something that can merge objects as
easily as you can merge source code.  Also, as the name of tool states,
it’s a comparing tool not a *control*tool.  I would love to see an
application that gives me all of the features of a quality source
control management application.

[Frans Bouma](http://weblogs.asp.net/fbouma) said that I was running
into problems because I didn’t do proper design.  I can concede that the
database for our internal apps does not have the greatest design in the
world, but I fail to see how that has anything to do with differencing
and merging schema.  Even if I go and design the worlds greatest
database I think I would still benefit from a quality schema merging
tool.  (As an aside, he mentioned the use of stored procedures versus
dynamic sql.  Frans and I share a similar view on stored procs but that
is another conversation.)

I can think of a couple reasons why it’s a good idea, but I haven’t come
up with any that make it a downright bad idea.  But there are smart
people out there that can tell me why.
![](http://blogs.geekdojo.net/ryan/images/smile1.gif)
