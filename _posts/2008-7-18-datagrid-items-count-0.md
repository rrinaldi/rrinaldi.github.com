---
layout: post
title: datagrid-items-count-0
---
Not if you bound it at least once.

I found this little bug the other day.  I don't know if I'm the first,
but I figured I would throw it out here so Google can reel it in for
someone else.

If you bind a DataGrid to a collection that has at least 1 (one) item in
it, the Items.Count property mirrors the count of the items in the
collection.  If you remove all the items from the collection and rebind,
the Items.Count property will be 1 (one) while the count of the items in
the collection will be 0 (zero).  You add one to the collection, rebind,
and the Items.Count will still be 1 (one).

Pretty silly huh?

I don't write bug free code (as evidence to that fact was the rollout I
did last week (by far my worst rollout ever!)) so I feel kind of weird
complaining about it but that seems like something that should have been
caught back in testing.
