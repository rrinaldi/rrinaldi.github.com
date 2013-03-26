You might have noticed that if you ever use window.showModalDialog()
that the resulting window will always post back to another new window. 
Some people have worked around that by using an IFRAME inside of the
dialog window, but that just smacks of hackery. The real way to get it
to work is to use a old HTML tag called BASE. Just throw this tag on
your page: and your good to go.  No muss, no fuss.
