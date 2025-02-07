# Chapter 4 - Architecture Characteristics

The hate on `nonfunctional requirements`: It's hard to care about something if it's not functional. Or `quality attributes` since it implies after-the-fact assessments rather than original design

Hence `Architecture Characteristics`

Architecture Characteristics influence design by:

- Specific a non domain design consideration (eg: performance): Implicit vs explicit considerations. Implicit usually not mentioned in design but should be understood by the architect.
- Influence some structural aspects of the design: sometimes the architect needs to design something special
- Identify the critical characteristics: supporting all characteristic increases system complexity, so architect needs to identify the most critical ones only (it's harder)

## Characteristics

- Operational
- Structural
- Cross-cutting

### Operational

- Availability: how long the system needs to be available (24/7, 99.999% uptime?)
- Continuity: recover from disaster
- Performance: stress testing, peak analysis, capacity required, etc. (performance is broad)
- Recoverability: how fast system can recover (backup, duplicated hardware, etc.)
- Reliability/safety: does the system needs to be fail-safe, or it's mission critical. If it fails will it cost a lot of money?
- Robustness: handling error and boundary conditions (offline, power outage)
- Scalability: dealing with increased loads, how many users/requests the system can handle

This heavily overlaps with Ops and DevOps concern

### Structural

Concerning with code

- Configurability: ability for end users to easily change software configuration
- Extensibility: is it important to plug in new pieces of functionalities
- Installability: the ease of installing this on different platform
- Leverageability/reusablility: ability to use common components
- Localization: support for languages, currency, multibyte characters, etc.
- Maintainability: how easy it is to apply changes & enhance the system
- Portability: does the system needs to run with different platform (eg: replacing databases)
- Upgradeability: update from previous version to new version on servers & clients


### Cross-cutting

- Accessibility: supporting for different users requirements (disabilities, hearing loss, etc.)
- Archivability: does data needs to be archived, deleted?
- Authentication: security requirements to ensure users who they said they are
- Authorization: security requirements to allow users to access only what they can
- Legal: legislative concern (GDPR, data protection act, etc.)
- Privacy: hide transactions from internal operators
- Security: does data needs to be encrypted
- Supportability: what level of technical support is needed for the application
- Usability/achievability: level of training required for users to achieve their goals with the application

A list like this is never exhaustive, there will be things that is unique needs to the organization, some terms are also overlapping in some cases but not in other cases

A common frustration is there's no clear definitions of these characteristics industry-wide. The solution is to follow domain-driven design: to establish common terms among teams/domain to reach the same understanding

## Trade-offs and Least Worst Architecture

It's not possible to satisfy all of the characteristic above. Due to:

- Complexity added in supporting too many characteristics
- Conflicting trait between characteristics. Eg: security (adding encryption) will degrade performance

So an architect should aim for Least Worst Architecture, not the Best Architecture, and focus on iterative ability (make it easier for the architecture to adapt to changes), rather than trying to get it right the first time.

Generic solutions that tries to solve for every business problems rarely work
