# Chapter 2 - Architectural Thinking

## 4 aspects of architectural thinking

- Difference btw architecture and design & knowing how to collab with dev team to make the architecture work
- Having a breath of understanding while still maintaining the depth required to see solutions & possibilities others might have missed
- Understanding, analyzing, reconciling trade-offs between different solutions & technologies
- Understanding the importance of business driver & how they translate to the architecture

## Architecture vs design

- Architect vs development team needs to be in sync, with bi-directional communication

But why?
- Both are on the same team
- The physical barrier is broken down
- To deal with the ever increasing changes in software requirements

## Breadth of knowledge

The pyramid of knowledge

        Stuff you know
    Stuff you know you don't know
Stuff you don't know you don't know


Stuff you know: is language, framework you usually work with as developer. The more you horn your skill in this (esplly earlier career), the more you will expands the Stuff you know you don't know.

And this is where the strength of an architect is drawn from.

Having a wide depth of knowledge is more helpful, eg: knowning 10 different caching strategies is better than being an expertise in only one.

Stuff you know gradually become Stuff you have to maintain, this is where you'll be faced with the choice of which to keep digging into, which can be usefully atrophied

The difference between architect and developer: developer spent their time horning their expertise, and transitioning into an architect role means a shift in that mindset. This will lead to 2 other problems:
    - Try to maintain expertise in many aspect, which is not possible & will usually lead to failure
    - Stales expertise: the mistaken sensation that what you know is still cutting edge. This leads to Frozen Caveman Anti-pattern

An architect should focus on technical breadth to have a larger pool to draw from

## Trade off

*"It depends"*

Thinking like an architect means to understand different pros/cons of the solutions, and decide which is more important for current & future problems


## Understanding business drivers

Working with business stakeholders and satisfying the *lities* characteristic of the architecture is not simple

# Balance between architect role & writing code

An architect definitely should write code

Don't be the bottleneck to your team:

- Don't singularly own the implementation, or don't write the first implementation
- Delegate to the team the critical path, only implement a peace of the business logic

The benefits:

- Gain hands on experience in production code
- Distribute knowledge to the team
- (most important) better to identify with the same development pain the team has


Other avenues:

- POCs with production-level quality code as much as you can
- Tackle tech debt
- Code review
