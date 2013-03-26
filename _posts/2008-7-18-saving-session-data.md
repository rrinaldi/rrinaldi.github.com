---
layout: post
title: saving-session-data
---
So, I'm cruising around the blogsphere today and I happen to come across
this this [post](http://neopoleon.com/blog/posts/1608.aspx) by Rory.
(Actually I didn't stumble across it, I subscribe to his RSS feed, but
don't tell him that.  He might get an ego or something. :) )  Rory makes
reference to a
[post](http://hyperthink.net/blog/PermaLink.aspx?guid=6d6c9a73-42a1-4fec-86a1-e0e58a410eb4)
written by Steve Maine.  Go read it, then come back.

Okay, here's the deal.  I like the fact that Steve's post removes
unnecessary string literals from code (string literals are Magic
Numbers' younger, less ugly sister), but I don't think that his methods
give as great of speed improvements as he is talking about.

Lets take his example:

> newOrder.CreditCard      =
> (CreditCardInfo)HttpContext.Current.Session[CREDITCARD\_KEY];\
> newOrder.BillingAddress  =
> (AddressInfo)HttpContext.Current.Session[BILLING\_KEY];\
> newOrder.ShippingAddress =
> (AddressInfo)HttpContext.Current.Session[SHIPPING\_KEY];

He wants the above changed to read something like the following:

> SessionDataContainer sessionState = HttpContext.Current.Session[
> CONTAINER KEY ];\
> \
> newOrder.CreditCard      = sessionState.CREDITCARD;\
> newOrder.BillingAddress  = sessionState.BILLING;\
> newOrder.ShippingAddress = sessionState.SHIPPING;

Comparing the two snippets of code, I definitely prefer the latter.  If
you ever ask anybody I have ever [worked](http://blogs.geekdojo.net/jez)
[with](http://blogs.geekdojo.net/richard), they will tell you how much I
hate magic numbers.  (Steve needs to run his code through FxCop though. 
Public member variables? All uppercase variable names?)

For code maintainability the above solution is great.  The problem I
have is that Steve is assuming in-process session management.  With
out-of-process session management instead of having 3 objects that you
can access randomly when you need them, you now have one larger object
that needs to be serialized and deserialized. Let's say that I only need
the shipping address.  Why should I need to deserialize the credit card
and billing address objects? That is a huge performance hit! 
Whatever gains in speed you had before you have just completely
annihilated by moving to out-of-process memory management.

If you are looking to solve some maintainability issues, Steve's post is
a brilliant way to make source code cleaner.  If your looking to speed
up your code, I don't think you will gain incredible amounts of speed by
adding a strongly typed container to your session lookups.
