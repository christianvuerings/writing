---
ID: 5131
post_title: 'CSS: Expanding a div to take up the remaining space in a row'
author: James DiGioia
post_date: 2016-03-31 09:48:17
post_excerpt: ""
layout: post
permalink: >
  http://jamesdigioia.com/css-expanding-a-div-to-take-up-the-remaining-space-in-a-row/
published: true
---
I ran into a problem today. I had two elements next to each other on a row. I needed the first element to just be contained to the width of its child elements, while the second element needed to take up the rest of the space.

Here's some dummy markup to get the idea:

[embed]http://jamesdigioia.com/gistpens/expanding-a-div-to-take-up-the-space-in-a-row/original.html/[/embed]

The problem is, when I was using `float` left and right, I was setting the width of the second element manually using media queries, which worked at first but turned into a real bit of trouble when I attempted to make the containing element (a `column` wrapping the `row`) more responsive.

I couldn't keep adding breakpoints and reset the size. Or I could, but it would be really brittle and would need to be updated every time the breakpoints of the containing element changed. I floundered around a bit, trying to find a solution, until I settled on this one, which relies on the oft-maligned `table`.

Not a `<table>` per se, but `display: table`. I have not used this feature much, since my CSS knowledge is generally pretty minimal, but there are a lot of places, like this one, where it's going to be a lot more functional than the standard "float the div" method we're all used to for building responsive layouts. Here's how it works:

First, I needed to add an extra wrapper, so our HTML now looks like this:

[embed]http://jamesdigioia.com/gistpens/expanding-a-div-to-take-up-the-space-in-a-row/updated.html/[/embed]

And our CSS looks like this:

[embed]http://jamesdigioia.com/gistpens/expanding-a-div-to-take-up-the-space-in-a-row/styles.css/[/embed]

The nifty thing to notice is the `.contained` CSS. We set the width to be impossibly small, but tell the cell not wrap its contents. This has the effect of forcing the cell to expand to be the width of its contents, while allowing the `.expanded` div to take over the remaining space, achieving the effect I was looking for.

Do you know of any other uses for `display: table` that can't be solved with the standard "float the div" method? Let me know in the comments.