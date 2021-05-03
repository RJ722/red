---
title: "GSoC Project Timeline"
date: 2017-05-28T00:28:48+05:30
tags: ["GSoC"]
---

Here is a description of how I plan to manage my schedule during GSoC period.

## Project Overview

Presently, we have coala - an automatic code linter and vulture - dead code
reporter. Amongst coala's fundamental `code checkers` known as `Bears`, there is
a `VultureBear` which runs vulture over the input batch of files and prepares a
patch for the respective files. The project proposal focuses on improving the
VultureBear and making vulture available as a library rather than as command
line tool.

Full project description can be found here: [GSoC Project I am working on this
summer](https://rj722.tech/gsoc_project)

## Milestones

The milestones are yet to be reviewed by my mentor
([@jendrikseipp](https://github.com/jendrikseipp)).

### Pre - Community Bonding Period ( Up Till  May 4)
- Initial investigation and discussion on what features to be added to API, and
  start implementing them on the go.
- Continue discussion with the community on ast and enhanced pyflakes ast - What
  are the underlying differences, and what can be possible implementations for
  source range acquisition.
- Diagnose possible cases which would render the code unreachable.
- Inculcate a habit of downloading the trending project of the day, running
  vulture on it, analyzing the results and adding anything suitable to whitelist
  file. This would help us in maintaining a rich whitelist file.
- Prioritize all the goals and targets

### Community Bonding (May 5 - 30)
- Finalize what should be implemented for source range acquisition on the basis
  of discussions during pre - community bonding period.

### Week 1 & 2 (May 31 - June 13)
- Implement API - At this point, we would have a fully functioning API, and we
  would be ready to incorporate these changes into the VultureBear.
- Refactor VultureBear to incorporate API - This would be relatively easy as the
  API would have had until now respected it’s usage in the VultureBear.

### Week 3 (June 14 - 20)
- Realize VultureBear completely - At this point, it should be able to execute
vulture, parse output, produce the patch file for removing the dead code what so
ever found. Review the tests written so far and add relevant test cases.
- Document Bear
- API documentation including, but not limited to possible use cases, example
  code snippets
- See that code is completely documented in place
- Buffer time to finish pending work.

### Week 4 (June 20 - 26)
- Develop an analysis report on what all constructs can we detect with complete
  surety, partial surety and the ones we cannot detect for the sake of
  implementing a confidence value with results. (A crude version is here in this
  thread).
- Discuss on the levels of certainty we would need to have (perhaps four for
  highly accurate (100%), accurate (>80%), medium (70 - 80%) and can’t say)

### Week 5 (June 27 - July 4)
- Create whitelist files for popular Python frameworks like Django
- Configure vulture in order to ensure that whitelist is taken into account by
  default.
- Updating docs and writing tests.

### Week 6 (July 4 - 15)
- Adapt to the strategy worked during community bonding period for obtaining
  source range.

### Week 7 & 8 (July 15 - 29)
- Diagnose the instances of unreachable code, our concern here would be to
  identify all such cases which would render the code unreachable, like the if
  False; if True: else; code after return statements, etc. - Adding this to the
  dead code classes, under a new category: get_unreachable

### Week 9 (August 1 - 7)
- Integrate these results with the VultureBear, which would primarily consist
  of:
- Transmitting source range, and unreachable code instances through API
- Yielding the results of Bear in the new format.

### Week 11 (August 8 - 17)
- Adding the suitable documentation for the new changes incorporated in the API,
  Bear and vulture itself.
- Code Review
- Taking feedback and making any improvements proposed.

### Week 12 (August 17 - 24)
- Buffer week to complete any pending work, evaluate and review tasks completed,
  review documentation and test cases.
