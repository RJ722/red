---
title: "\u0022isn't a title of this post\u0022 isn't a title of this post"
tags: ["programming", "mathematics"]
date: 2020-01-20T00:28:48+05:30
load_mathjax: true
---

In the early part of the last century, when David Hilbert was working on
stricter formalization of geometry than Euclid, Georg Cantor had worked out a
theory of different types of infinities, _the theory of sets_. This
theory would soon unveil a series of confusing paradoxes, leading to <a
href="https://en.wikipedia.org/wiki/Foundations_of_mathematics#Foundational_crisis">
a crisis in the Mathematics community </a> regarding the stability of the
foundational principles of the math of that time.

Central to these paradoxes was the _Russell's paradox_ (or more generally, as
we'd talk about later, the _Epimenides Paradox_). Let's see what it is.

In those simpler times, you were allowed to define a set if you could describe
it in English. And, owing to mathematicians’ predilection for self-reference,
sets could contain other sets.

Russell then, came up with this:

<p>
\(R\)&nbsp; is a set of all the sets which do not contain themselves.
</p>

<p>
The question was "Does \(R \) contain itself?" If it doesn’t, then according to
the second half of the definition it should. But if it does, then it no longer
meets the definition.
</p>

The same can symbolically be represented as:

<p style="text-align: center;">
  Let \(R = \{ x \mid x \not \in x \} \), then \(R \in R \iff R \not \in R \)
</p>

Cue mind exploding.

"Grelling's paradox" is a startling variant which uses adjectives instead of
sets. If adjectives are divided into two classes, autological
(self-descriptive) and heterological (non-self-descriptive), then, is
'heterological' heterological? Try it!

### Epimenides Paradox

Or, the so-called _Liar Paradox_ was another such paradox which shred apart
whatever concept of 'computability' was, at that time - the notion that things
could either be true or false.

Epimenides was a Cretan, who made one immortal statement:

{{< blockquote cite="Epimenides, a Cretan">}} 
All Cretans are liars.
{{< /blockquote >}} 

If all Cretans are liars, and Epimenides was a Cretan, then he was lying when
he said that "All Cretans are liars". But wait, if he was lying then, how can
we 'prove' that he wasn't lying about lying? Ein?

{{< figure src="https://i.imgur.com/Cdd6LpT.png" >}}

This is what makes it a _paradox_: A statement so rudely violating the assumed
dichotomy of statements into true and false, because if you tentatively think
it's true, it backfires on you and make you think that it is false. And a
similar backfire occurs if you assume that the statement is false. Go ahead,
try it!

If you look closely, there is one common culprit in all of these paradoxes,
namely 'self-reference'. Let's look at it more closely.

### Strange Loopiness

If self-reference, or what Douglas Hofstadter - whose prolific work on the
subject matter has inspired this blog post - calls 'Strange Loopiness' was the
source of all these paradoxes, it made perfect sense to just banish
self-reference, or anything which allowed it to occur. Russell and Whitehead,
two rebel mathematicians of the time, who subscribed to this point of view, set
forward and undertook the mammoth exercise, namely _"Principia Mathematica"_,
which we as we will see in a little while, was utterly demolished by Gödel's
findings.

The main thing which made it difficult to ban self-reference was that it was
hard to pin point where exactly did the self-reference occur. It may as well be
spread out over several steps, as in this 'expanded' version of Epimenides:

{{< blockquote >}}
The next statement is a lie.
The previous statement is true.
{{</ blockquote >}}

Russell and Whitehead, in _P.M._ then, came up with a multi-hierarchy set
theory to deal with this. The basic idea was that a set of the lowest 'type'
could only contain 'objects' as members (not sets). A set of the next type
could then only either contain objects, or sets of lower types. This,
implicitly banished self-reference.

Since, all sets must have a type, a set 'which contains all sets which are not
members of themselves' is not a set at all, and thus you can say that Russell's
paradox was dealt with.

Similarly, if an attempt is made towards applying the expanded Epimenides to
this theory, it must fail as well, for the first sentence to make a reference
to the second one, it has to be hierarchically above it - in which case, the
second one can't loop back to the first one.

Thirty one years after David Hilbert set before the academia to rigorously
demonstrate that the system defined in _Principia Mathematica_ was both
_consistent_ (contradiction-free) and _complete_ (i.e. every true statement
could be evaluated to true within the methods provided by _P.M._), Gödel
published his famous Incompleteness Theorem. By importing the Epimenides
Paradox right into the heart of _P.M._, he proved that not just the
axiomatic system developed by Russell and Whitehead, but none of the
axiomatic systems whatsoever were _complete_ without being _inconsistent_.

Clear enough, _P.M._ lost it's charm in the realm of academics.

Before Gödel's work too, _P.M._ wasn't particularly loved as well.

Why?

It isn't just limited to this blog post, but we humans, in general, have a diet
for self-reference - and this quirky theory severely limits our ability to
abstract away details - something which we love, not only as programmers, but
as linguists too - so much so, that the preceding paragraph, "It isn't ...
_this_ blog ... _we_ humans ..." would be doubly forbidden because the 'right'
to mention '_this blog post'_ is limited only to something which is
hierarchically above blog posts, '_metablog-posts_'. Secondly, me (presumably a
human) belonging to the class _'we'_ can't mention '_we_' either.

Since, we humans, love self-reference so much, let's discuss some ways in which
it can be expressed in written form.

One way of making such a strange loop, and perhaps the 'simplest' is using the
word 'this'. Here:

- This sentence is made up of eight words.
- This sentence refers to itself, and is therefore useless.
- This blog post is so good.
- This sentence conveys you the meaning of 'this'.
- This sentence is a lie. (Epimenides Paradox)

Another amusing trick for creating a self-reference without using the word
'this sentence' is to quote the sentence inside itself.

Someone may come up with:

{{< blockquote >}}
The sentence 'The sentence contains five words' contains five words.
{{< /blockquote >}}

But, such an attempt must fail, for to quote a finite sentence inside itself
would mean that the sentence is smaller than itself. However, infinite
sentences can be self-referenced this way.

```
The sentence
    "The sentence
        "The sentence
                                ...etc
                                ...etc
        is infinitely long"
    is infinitely long"
is infinitely long"
```

There's a third method as well, which you already saw in the title - the Quine
method. The term 'Quine' was coined by Douglas Hofstadter in his book "Gödel
Escher, Bach" (which heavily inspires this blog post). When using this, the
self-reference is 'generated' by describing a typographical entity, isomorphic
to the quine sentence itself. This description is carried in two parts - one is
a set of _'instructions'_ about how to 'build' the sentence, and the other, the
_'template'_ contains information about the construction materials required.

The Quine version of Epimenides would be:

{{< blockquote >}}
"yields falsehood when preceded by it's quotation" yields falsehood when preceded by it's quotation.
{{< /blockquote >}}

Before going on with 'quining', let's take a moment and realize how awfully
powerful our cognitive capacities are, and what goes in our head when a
cognitive payload full of self-references is delivered - in order to decipher
it, we not only need to know the language, but also need to work out the
referent of the phrase analogous to 'this sentence' in that language. This
parsing depends on our complex, yet totally assimilated ability to handle the
language.

The idea of referring to itself is quite mind-blowing, and we keep doing it all
the time &mdash; perhaps, why it feels so 'easy' for us to do so. But, we aren't born
that way, we grow that way. This could better be realized by telling someone
much younger "This sentence is wrong.". They'd probably be confused - What
sentence is wrong?. The reason why it's so simple for self-reference to occur,
and hence allow paradoxes, in our language, is well, our language. It allows
our brain to do the heavy lifting of what the author is trying to get through
us, without being verbose.

Back to Quines.

## Reproducing itself

Now, that we are aware of how 'quines' can manifest as self-reference, it would
be interesting to see how the same technique can be used by a computer program
to 'reproduce' itself.

To make it further interesting, we shall choose the language most apt for the
purpose - brainfuck:

```
>>>>+++++++++++++++++++++++++++++++++++++++++++>+++++++++++++++++++++++++++++++++++++++++++>+++++++++++++++++++++++++++++++++++++++++++>+++++++++++++++++++++++++++++++++++++++++++>+++++++++++++++++++++++++++++++++++++++++++>+++++++++++++++++++++++++++++++++++++++++++>+++++++++++++++++++++++++++++++++++++++++++>+++++++++++++++++++++++++++++++++++++++++++>+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++>+++++++++++++++++++++++++++++++++++++++++++++>++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++>+++++++++++++++++++++++++++++++++++++++++++>+++++++++++++++++++++++++++++++++++++++++++>+++++++++++++++++++++++++++++++++++++++++++>+++++++++++++++++++++++++++++++++++++++++++>+++++++++++++++++++++++++++++++++++++++++++>+++++++++++++++++++++++++++++++++++++++++++>+++++++++++++++++++++++++++++++++++++++++++>+++++++++++++++++++++++++++++++++++++++++++>++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++>+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++>++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++>+++++++++++++++++++++++++++++++++++++++++++++>+++++++++++++++++++++++++++++++++++++++++++++>++++++++++++++++++++++++++++++++++++++++++++++>++++++++++++++++++++++++++++++++++++++++++++++>++++++++++++++++++++++++++++++++++++++++++++++>++++++++++++++++++++++++++++++++++++++++++++++>+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++>+++++++++++++++++++++++++++++++++++++++++++++>+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++>++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++>++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++>+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++>++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++>+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++>++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++>++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++>+++++++++++++++++++++++++++++++++++++++++++>+++++++++++++++++++++++++++++++++++++++++++>+++++++++++++++++++++++++++++++++++++++++++>+++++++++++++++++++++++++++++++++++++++++++>+++++++++++++++++++++++++++++++++++++++++++>+++++++++++++++++++++++++++++++++++++++++++>+++++++++++++++++++++++++++++++++++++++++++>+++++++++++++++++++++++++++++++++++++++++++>+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++>+++++++++++++++++++++++++++++++++++++++++++++>++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++>+++++++++++++++++++++++++++++++++++++++++++>+++++++++++++++++++++++++++++++++++++++++++>+++++++++++++++++++++++++++++++++++++++++++>+++++++++++++++++++++++++++++++++++++++++++>+++++++++++++++++++++++++++++++++++++++++++>++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++>+++++++++++++++++++++++++++++++++++++++++++>+++++++++++++++++++++++++++++++++++++++++++>+++++++++++++++++++++++++++++++++++++++++++>+++++++++++++++++++++++++++++++++++++++++++>+++++++++++++++++++++++++++++++++++++++++++>+++++++++++++++++++++++++++++++++++++++++++>+++++++++++++++++++++++++++++++++++++++++++>+++++++++++++++++++++++++++++++++++++++++++>++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++>++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++>+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++>++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++>+++++++++++++++++++++++++++++++++++++++++++>+++++++++++++++++++++++++++++++++++++++++++>+++++++++++++++++++++++++++++++++++++++++++>++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++>+++++++++++++++++++++++++++++++++++++++++++++>+++++++++++++++++++++++++++++++++++++++++++++>++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++>+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++>+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++>+++++++++++++++++++++++++++++++++++++++++++++>++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++>++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++>++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++>+++++++++++++++++++++++++++++++++++++++++++>++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++>++++++++++++++++++++++++++++++++++++++++++++++>++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++>++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++>+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++>++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++>++++++++++++++++++++++++++++++++++++++++++++++>+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++>+++++++++++++++++++++++++++++++++++++++++++++>++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++>+++++++++++++++++++++++++++++++++++++++++++>++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++>+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++>++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++>+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++>+++++++++++++++++++++++++++++++++++++++++++++>++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++>+++++++++++++++++++++++++++++++++++++++++++>++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++>+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++>++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++>++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++>++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++>+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++>++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++>++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++>++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++>++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++>+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++>++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++>+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++>++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++>+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++>++++++++++++++++++++++++++++++++++++++++++++++>++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++>+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++>++++++++[->++++++++<]>--....[-]<<[<]<<++++++++[->+++++>++++++++<<]>+++>-->[[-<<<+>.>>]<.[->+<]<[->+<]>>>]<<<<[<]>[.>]

```

<!-- Here's an EasterEgg: https://www.youtube.com/watch?v=F5P6Q7vs_-Y -->

Running that program above produces itself as the output. I agree, it isn't the
most descriptive program in the world, so written in Python below, is the
nearest we can go to describe what's happening inside those horrible chains of
+'s and >'s:

```python
THREE_QUOTES = '"' * 3

def eniuq(template): print(
  f'{template}({THREE_QUOTES}{template}{THREE_QUOTES})')

eniuq("""THREE_QUOTES = '"' * 3

def eniuq(template): print(
  f'{template}({THREE_QUOTES}{template}{THREE_QUOTES})')

eniuq""")
```

The first line generates `"""` on the fly, which marks multiline strings in
Python.

Next two lines define the `eniuq` function, which prints the argument template
twice - once, plain and then surrounded with triple quotes.

The last 4 lines cleverly call this function so that the output of the program
is the source code itself.

Since we are printing in an order opposite of quining, the name of the function
is 'quine' reversed -> `eniuq` (name stolen from Hofstadter again)

Remember the discussion about how self-reference capitalizes on the processor?
What if ‘quining’ was a built-in feature of the language, providing what we in
programmer lingo call 'syntactic sugar'?

Let's assume that an asterisk, `*` in the brainfuck interpreter would copy the
instructions before executing them, what would then be the output of the
following program?

```
*
```

It'd be an asterisk again. You could make an argument that this is silly, and
should be counted as 'cheating'. But, it's the same as relying on the
processor, like using "this sentence" to refer to this sentence - you rely on
your brain to do the inference for you.

What if `eniuq` was a builtin keyword in Python? A perfect self-rep was then
just be a call away:

```python
eniuq('eniuq')
```

What if `quine` was a verb in the English language? We could reduce a lot of
explicit cognitive processes required for inference. The Epimenides paradox
would then be:

{{< blockquote >}}
"yields falsehood if quined" yields falsehood if quined
{{< /blockquote >}}

Now, that we are talking about self-rep, here's one last piece of entertainment
for you.

## The Tupper's self-referential formula

This formula is defined through an inequality:

<p align="center">
\({1 \over 2} < \left\lfloor \mathrm{mod}\left(\left\lfloor {y \over 17} \right\rfloor 2^{-17 \lfloor x \rfloor - \mathrm{mod}(\lfloor y\rfloor, 17)},2\right)\right\rfloor\)
</p>

<p>
If you take that absurd thing above, and move around in the cartesian plane for
the coordinates \(0 \le x \le 106, k \le y \le k + 17\), where \(k\) is a <a
href="https://gist.githubusercontent.com/RJ722/cad7deff9a11ed927e0979091d45b479/raw/dd3b18d6e6b693685724a148f6ce937e6347f587/544-1.txt">
544 digit integer </a> (just hold on with me here), color every pixel black for
True, and white otherwise, you'd get:
</p>

{{< figure src="https://i.imgur.com/aGouM3u.png" >}}

<p>

This doesn't end here. If \(k\) is now replaced with <a
href="https://gist.githubusercontent.com/RJ722/cad7deff9a11ed927e0979091d45b479/raw/4ab074d235de9e58f10b2d94fe4e9970cb03a6c7/291.txt">
another integer containing 291 digits</a>, we get yours truly:

</p>

{{< figure src="https://i.imgur.com/NvPlE33.png" >}}
