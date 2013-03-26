---
layout: post
title: pdc-2008-building-textual-dsls-with-the-quot-oslo-quot-modeling-language
---
(This is going to be cool. I'm totally geeked out about Oslo and I want
me some Textual DSL goodness)

((Also, I have approx 51 mins of battery left so I might have to leave
early.)

MGrammar is actually a DSL over MGraph the lowest level of M

We will be implmenting a grammar to parse: "Contact: giodl - 555-1212"

Inside of IntelliPad there will be 3 panes

-   Left is the input
-   Center is the Grammar
-   Right is Output
-   Errors are listed on the bottom

Module is the top level Container for MGrammar

Language is the top level structure "Think void main"

token == word

syntax == sentence

Range expressions is ".."

How to model whitespace?

-   Explicitly model wherever we want it
-   OR "interleave"

You can use single or double quotes

Step 1 in creating a DSL is tokenizing

Step 2 is parsing

Step 3 is shaping

FYI, this is mostly a demo based presentation so it's hard to make good
notes.  Go watch this online. 
