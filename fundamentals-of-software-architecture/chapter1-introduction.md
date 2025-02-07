# What does Software Architect do?

- Industry doesn't have good definition of what an Architect does
- The scope of an Architect role always expand
- Software Architect is dealing with constantly moving target, not solved once then ignored kind of issues
- Materials around software architects are historical



The 4 pillars (corner) of software architecture

- Structure: Microservices, monolith
- Architecture characteristics: the *lities*. Eg: availability, reliability, testability, performance
- Architecture decisions: defining the rules (constraint) for how a system should be constructed. Eg: only the business and services layers can communicate with database, the presentation layers can't.
- Design decisions: a guideline rather than rules. Eg: communication between services should be async for the sake of performance, but service and developers can choose either gRPC or REST to facilitate this communication


## The expectations of an Architect

The book aligns 8 core expectations

- Make architecture decisions: to *guide* or sometimes *make* the decisions within team, across teams
- Continually analyze the architectures: to keep the application relevant to business changes after original design
- Keep up with industry trends: to prepare for the future and make the correct decisions
- Ensure compliance with decisions
- Diverse exposure and experience: focus on technical breath rather than technical depth
- Have business domain knowledge: communication with the business & build reliability
- Possess interpersonal skills: Leadership skills are at least half of what it takes to become an effective software architect, architect is expected to lead the team through out (multiple) implementations
- Understand & navigate politics: almost every decision an architect makes will be challenged.


## Evolutionary architecture using fitness function

An architecture has to survive implementations and future changes.

One way to achieve it is to build out fitness function as a measurement tools on the characteristic of the architecture.

Eg: if load time of a webpage is an important metrics, identify it, build a measurement tool & include it in CI to avoid degradation in the future

## The law of software architecture

- Architecture decisions is all about trade-offs
- The Why is more important than the How
