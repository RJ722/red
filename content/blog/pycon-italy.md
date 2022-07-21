---
title: "PyCon Italy 2022"
date: 2022-07-06T16:59:17+05:30
draft: false
tags: ["python", "conference", "talk"]
---

I've been giving a talk on [Vulture] at many Python Conferences for almost half
a decade now. Each time, it's a new challenge for me since I don't reuse my
slides and it always comes out quite differently, takes me new places and
teaches me new things, which I like.

This time, rather than focussing on Vulture specifically, I wanted to
spend more time on automated code analysis in general.

I also wanted to have a nice ice-breaker to loosen up the awkwardness which is
generally present in technical conferences. And since we were in Italy, why not
Football? I started off with some old shots of Baggio _head faking_:

{{< figure src="https://i.imgur.com/E5bIFYt.gif" title="A head fake is when you kick the ball in the direction opposite to what your body pretended to kick" >}}

The term "head fake" was used by [Randy Pausch](lastlec). He used it to
attribute hidden learning from other activities, e.g. when children play
football, rather than just learning how to kick a ball, they also learn
team-building skills, leadership, communication, etc.

[lastlec]: https://www.youtube.com/watch?v=ji5_MqicxSo

Limited by how little I actually know about football, I promptly segued back to
code analysis.

As they say, if you want someone to do something, convince them _why_. There's a
better option though: Tell them what happens if they don't. That's how we start.

37 seconds into descent in June 1996, the Ariane5 rocket flipped by 90 degrees
and tore itself apart. Reason, it turned out, was a floating point error in the
IMU. Trying to stuff a 64bit value into a 16bit variable. The thing which made
it even more unfortunate was that this value wasn't even being utilized in the
guidance system. That's right: writing invalid data to an unused variable ended
up obliterating a $500mn rocket.

This is what code analysis tools excel at. To tell you things like whether or
not you follow the best practices, or if the function you're using is prone to
certain attack vectors or whether you comply with the style guide or not, or if
you're doing strange things like leaving old dead code or unused imports behind.
They are the voice of the collective wisdom of the community.

> "The voice of the people has been likened to the voice of God."

<cite>Niccolo Machiavelli</cite>

During the later half, I gave a brief demo of Vulture -- how to run it, tweak
all its knobs and joints to optimize it on your codebase, etc.

The last part was the most exciting one, where I drew out _how_ Vulture worked
under the hood with Abstract Syntax Trees.

{{< figure src="images/pycon_italy/ast.png" title="How Vulture parses an AST">}}

## Conclusion

This talk was a head fake of sort: "_Let's learn about Vulture_" to "_Let's take
charge of our code quality!_"

Here's the deal: how Vulture works is irrelevant for most, if not all of its
users. But knowing that there's a way you can just parse the AST yourself and
write a method to do _that_ is incredibly powerful. 

P.S. The video isn't out yet. I'll make sure to add a link here as soon as it's out.

[vulture]: https://github.com/jendrikseipp/vulture
