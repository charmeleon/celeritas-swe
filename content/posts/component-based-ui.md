---
title: "Component Based UI"
date: 2023-01-28T12:12:51-06:00
draft: true
---
## Musings on component-based UI systems

After a decade of writing websites starting with the humble HTML page frontend development has
evolved to an almost steady state with component-based development. There's an almost natural
order to organizing UI repos with stateless components that are feature-rich, composable and
reusable.

Business logic, the lifeblood of many web applications, inevitably confuses the pursuit of the
most optimal way to organize the code. After many projects, I remain convinced business logic
must mix with UI logic as little as possible. This isn't always obvious to the growing number
of contributors on a codebase: the need to folllow a tutorial by a popular author or experiment
inevitably arises and gives way to unintended consequences the rest of us must live with. In
reality there's ways to approach frontend development in such a manner that it becomes 'boring':
standardized, isolated, unit-testable and succinct. This is possible, from my experience, both
using React and Angular and though I prefer React I must give credit to Angular for providing
a complete toolchain to go along with component development. In React you get choices but the
sad reality is that making the wrong choice leads to a painful maintenance cycle that the
people who make the choices almost never need to live with - and this is unlikely to happen
in an Angular codebase as batteries are included.

Another caveat when using React is the introduction of its Context system. Used correctly it
empowers developers to create powerful, highly reusable UI experiences. But it should not be
used for application state management except for trivial systems or UI state. The tried and
true redux should be used, if nothing else because both Angular and React developers will be
familiar with it. As for actual drawbacks, the fact that that the Context system notifies
each context subscriber individually after every update and the need to supplement its usage
with hooks for basic necessities such as memoization makes it unsuitable for the more
complicated tasks. In a user-driven web application, having _N_ context subscribers means
_N_ context updates need processing after each change. If your components need to respond
to constant streams of data such as mouse events you will notice problems quickly.

