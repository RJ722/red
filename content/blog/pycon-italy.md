---
title: "My talk at PyCon Italy"
date: 2022-07-06T16:59:17+05:30
draft: false
tags: ["python", "conference", "talk"]
---

I've been giving a talk on [Vulture] for almost half a decade now. It takes me
new places, and teaches me new things, and I quite like it. This time, it was
even more special -- it was in Italy. And rather than focussing on Vulture
specifically, I wanted to spend more time on automated code analysis in
general.

I also wanted to have a nice ice-breaker to loosen up the awkwardness which is
generally present in technical conferences. And since we were in Italy, why not
Football?

I started off with some old shots of Baggio _head faking_:

{{< figure src="https://i.imgur.com/E5bIFYt.gif" title="A head fake is when you kick the ball in the direction opposite to what your body pretended to kick" >}}

The phrase "head fake" was first used by [Randy Pausch](lastlec) to denote
_hidden_ indirect learnings from other activities, e.g. when children play
football, they don't just learn how to kick a ball, they also learn skills like
leadership, communication, comradery, etc.

[lastlec]: https://www.youtube.com/watch?v=ji5_MqicxSo

Limited by how little I actually know about football, I promptly segued back to
code analysis.

As they say, if you want someone to do something, convince them _why_. There's a
better option though: Tell them the cost of not doing it. That's how we start.

37 seconds into descent in June 1996, the Ariane5 rocket flipped by 90 degrees
and tore itself apart. Reason, it turned out, was a floating point error in the
IMU: trying to stuff a 64-bit value into a 16-bit variable. The thing which made
it even more unfortunate was that this value wasn't even being utilized in the
guidance system. That's right: writing invalid data to an unused variable ended
up obliterating a $500mn rocket.

Detecting these kinds of mistakes is what code analysis tools excel at. To tell
you whether or not your code follows best practices, or if the function you're
using is prone to attack vectors or whether you comply with the style guide or
not, or if you're doing strange things like leaving dead code or unused imports
behind. These tools, together, give voice to the collective wisdom of the
community.

> "The voice of the people has been likened to the voice of God."

<cite>Niccolo Machiavelli</cite>

During the later half, I gave a brief demo of Vulture -- how to run it, tweak
all its knobs and joints to optimize it for your codebase, etc.

The last part, however, was the most exciting: I drew out _how_ Vulture worked
under the hood with Abstract Syntax Trees.

{{< figure src="images/pycon_italy/ast.png" title="How Vulture parses an AST">}}

## Conclusion

This talk was a head fake of sort: "_Let's learn about Vulture_" to "_Let's take
charge of our code!_"

Here's the deal: how Vulture works is irrelevant for most, if not all, of its
users. But, knowing that there's a way you can just pluck the AST and mess with it.
It's incredibly powerful. 

~~P.S. The video isn't out yet. I'll make sure to add a link here as soon as it's out.~~

Here you go:

{{< youtube NraLRnN_cmA >}}

[vulture]: https://github.com/jendrikseipp/vulture
