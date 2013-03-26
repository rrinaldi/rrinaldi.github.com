You ever need to perform some function in Javascript (like submitting a
form?) that afterword, if the user were to hit the back button, it would
cause big problems?  A lot of times this can be solved by just throwing
a little more Javascript on the page.  Perticularly this little snippet:

That should do ya.  It really doesn't disable the back button, but if
you put that on the top of your page the page will stop processing and
send the user back to where they came from (only when the back button is
clicked, since there is no forward history the first time you come to
the page).
