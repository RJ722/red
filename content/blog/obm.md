---
title: "Operation Blue Moon"
date: 2019-07-12T00:28:48+05:30
tags: ["productivity"]
---

It's been a couple of years since I read ["i want 2 do project tell me wat 2
do"][book], which then landed me on the home page of [Operation Blue Moon
(OBM)][obm], a project run single-handedly by the author of the book - [Shakthi
Kannan (mbuf)][mbuf]. It is aimed towards time management and getting things
done.

The project not only borrows it's name, but also the spirit of discipline, from
our miliary counterparts. The practices here, built upon Shakthi's years of
experience of dealing with people trying, and failing, and learning from their
mistakes, regarding time management.

OBM, at it's core, provides one with a framework (the ability to define WHY, WHAT,
WHEN and HOW) to align their thoughts, expectations and action practically,
along with the ability to monitor your success. How does it do so? Read on.

{{< blockquote >}}
It's difficult. It's this difficulty that creates the scarcity and you, the winner.
{{< /blockquote >}}

Every participant of OBM has a `plan`[^1] (an emacs org file), which enlists
their goals - long term, short term, secondary, etc. - all goals - The WHAT.

[^1]: every plan is inside a particular track (theme), eg. data scientist,
devops, etc. - this serves as WHY

Then, under each subsequent heading, define what tasks do you need to do in
order to achieve that goal - The HOW. The tasks have the following properties:

```
*** TODO Write one blog post
    :PROPERTIES:
    :ESTIMATED: 3
    :ACTUAL:
    :OWNER: RJ722
    :ID: WRITE.1562247371
    :TASKID: WRITE.1562247371
    :END:
```

`ESTIMATED` - The time you estimate you would take for completing the task.

`ACTUAL` - The actual amount it takes for you to complete it.

`OWNER`, `ID` and `TASKID` are there for better visualizations. (more on this
later)

I've the following function (courtesy of [mbuf][mbuf]) in my
[spacemacs][spacemacs] config to help me generate these tasks:

```lisp
(define-skeleton insert-org-entry
  "Prompt for task, estimate and category"
  nil
  '(setq task  (skeleton-read "Task: "))
  '(setq estimate  (skeleton-read "Estimate: "))
  '(setq category (skeleton-read "Category: "))
  '(setq timestamp (format-time-string "%s"))
  "*** TODO " task \n
  ":PROPERTIES:" \n
  ":ESTIMATED: " estimate \n
  ":ACTUAL:" \n
  ":OWNER: RJ722" \n
  ":ID: " category "." timestamp \n
  ":TASKID: " category "." timestamp \n
  ":END:")
```

The more important question is WHEN. Here's where the 'sprints' chime-in. If
you're participating in OBM, you're always sprinting (which makes perfect sense,
since ideally you wouldn't want yourself 'unmanaging' your time). A sprint,
generally lasts for around 14-18 days. Before the sprint starts, move the tasks
you want to get done in that sprint, under it's 'tab' (which exists in the plan
file, [an example here][plan]). You also need to enter an average amount
of time you can dedicate on a per day basis for this sprint.

Shakthi would then move such tasks from all participants to a file dedicated to
that sprint. The participants can now clock their tasks (track the amount of
time they have spend doing each of these tasks) - in emacs' org mode
(`org-clock-in`, `org-clock-out`).

If you have done everything until now correctly, you should have a holistic view
of how well your performance was for the last sprint. And, *this* is the most
important step. Introspection - See what you did you wrong, what factor did you
forget to take into account - how much was the difference between the actual and
expected time of completion. Were you not able to complete all the tasks - why?
what could you do to improve your estimates?

You don't even have to do this formally (although, it helps). Just doing the
work, clocking it, and sending it over is enough to spark an introspective
impulse. Just stick with the plan long enough and you'd see improvements. You'd
see major improvements. I want to attribute the reason for OBM's success to
it's simplicity, but it really is the discipline, showing up everyday and doing
the work.

If you currently find yourself in a position, where it feels like you're stuck -
you know what you want to do, but there's this 'something' stopping you, and it
feels forever since you've been wanting to do this thing, but there's been no
tangible progress so far. Well, then OBM is exactly the right thing for you.
With this framework, you're forced to formalize things, diagnose the 'something'
stopping you, make changes to your current schedule and to see the different
between the direction you aim to go towards and the one where you're heading
(with your current planning).

Lastly, I want to thank [Shakthi][mbuf] for all the energy and
motivation he's been pumping into the project himself. Thank you so much
Shakthi!

Have fun experiencing OBM!

[obm]: https://gitlab.com/shakthimaan/operation-blue-moon/
[mbuf]: http://shakthimaan.com/
[book]: http://www.shakthimaan.com/what-to-do.html
[plan]: https://gitlab.com/shakthimaan/operation-blue-moon/blob/master/plan/data-scientist/RJ722.org
[spacemacs]: http://spacemacs.org/
