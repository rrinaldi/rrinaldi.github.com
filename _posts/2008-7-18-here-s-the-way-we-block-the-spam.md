block the spam, block the spam early in the morning....

So the past couple weeks I've been kinda busy with work, but I managed
to find some spare time to add a few spam blocking measures to the ol'
dojo here.

I blacklisted a few hundred IPs that are known spammers.  I got the list
from [CommentSpam.org](http://www.commentspam.org/), run by [Robert
McLaws](http://weblogs.asp.net/rmclaws/).  Be careful though, as the
list from Robert isn't straight up compatible with the HttpModule I used
to do the IP blocking, written by [Scott
Hanselman](http://www.hanselman.com/blog/).  Robert is taking the IPs
from the [.Text](http://www.scottwater.com/dottext) comments, which
sometimes contains a comma delimited list of IPs which kills the
HttpModule.  I'm think I'm going to try to work something out so the 2
function together "out-of-the-box", but I'll probably never get around
to it. :(

I added the [Clearscreen SharpHIP
HIP-CAPTCHA](http://blogs.clearscreen.com/migs/archive/2004/11/10/575.aspx)
control to all of the blogs on this site, as a means to stop automated
spambots.  Yeah, it's a pain to type in crap that is hard to read, and
it is a little flakey since it is added without modifying the source. 
But it's better than the alternative of deleting 200+ spams.

So, if you get past the blacklist and the CAPTCHA, I assume you are
non-spamming human.  If you are a non-spamming human, feel free to post
a comment.  If your comment happens to contain various "spammy"
keywords, it will probably get picked up by my spam sweeper in the
evening.  I assume that since none of the content here is related to
poker or pharmaceuticals of any kind the spam sweeper is a pretty safe
bet.

Was all of this a pain?  Yeah, but what you going to do?  Add some sort
of tag to links that will lower the relevancy of those links in search
results?  Like that would ever work.... ;)
