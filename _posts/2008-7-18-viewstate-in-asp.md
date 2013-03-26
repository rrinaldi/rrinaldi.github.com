Having to do some work in Old Skewl ASP, I ran into a problem where I
wanted to throw my request collection in ViewState.  Well, since ASP
doesn't support ViewState I whipped up this little Sub that will take
everything in the Request.Form collection and output it to hidden form
fields.  Its not quite ViewState, but it might come in handy.

**Sub** CreateViewState()\
**dim** Item, intLoop\
 \
**if** Request.Form.Count \> 0 then\
     **for****each** Item in Request.Form\
          **for** intLoop = 1 **to** Request.Form(Item).Count\
               Response.Write("                              """
value=""" & Request.Form(Item)(intLoop) & """\>" & vbcrlf)\
          **next**\
     **next**\
 **end if**\
 \
**End sub**

© 2003 Ryan A. Rinaldi
