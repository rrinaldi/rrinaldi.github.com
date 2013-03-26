---
layout: post
title: venture-into-viewstate
---
I was reading [Scott's little
rant](http://www.hanselman.com/blog/PermaLink.aspx?guid=e73efd87-2cae-49af-9674-7076a054f2ca)
about people that move ViewState to the Session object and I have to say
that I agree with him completely.  The reason I bring it up at all is
that he pointed out two really cool projects that I didn't know existed:

[Paul Wilson's ViewState
Decoder](http://www.wilsondotnet.com/Demos/ViewState.aspx "http://www.wilsondotnet.com/Demos/ViewState.aspx")

And

[Fritz Onion's Win-Form
ViewStateDecoder](http://staff.develop.com/onion/resources.htm)

 

Both are really, really, really cool and so simple enough to write that
I wish I did. :(

 

Also, I just want to add to Scott's post: WAY too many people are using
ViewState as a Caching mechanism.  First off: Don't.  It's not there for
that. Second: Read [Rory's](http://neopoleon.com/blog/) explanation on
[ASP.NET Caching](http://neopoleon.com/blog/posts/1976.aspx).  It will
be completely worth it.  If you don't get caching after reading it, at
least you will laugh. A lot.

 
