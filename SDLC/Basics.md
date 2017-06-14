# SDLC General

#### Navigation
- [SDLC Essentials](https://github.com/kakarotto67/KnowledgeBank/blob/master/SDLC/Basics.md#sdlc-essentials)
- [RUP and AUP](https://github.com/kakarotto67/KnowledgeBank/blob/master/SDLC/Basics.md#rup-and-aup)
- [Extreme Programming](https://github.com/kakarotto67/KnowledgeBank/blob/master/SDLC/Basics.md#extreme-programming)
- [Engineering Process Planning](https://github.com/kakarotto67/KnowledgeBank/blob/master/SDLC/Basics.md#engineering-process-planning)
- [SCRUM Process](https://github.com/kakarotto67/KnowledgeBank/blob/master/SDLC/Basics.md#scrum-process)
  - [Scrum Essentials](https://github.com/kakarotto67/KnowledgeBank/blob/master/SDLC/Basics.md#scrum-essentials)

#### SDLC Essentials
- Typical Stages
  - Requirements >> Design >> Implementation >> Verification >> Maintenance
- Spiral Methodology
  - Determine objectives >> Identify & resolve risks >> Development & testing >> Plan next iteration ...
- Iterative Methodology
  - Waterfal1 >> Waterfal2 >> ... >> WaterfalN
- Incremental/Agile Development
  - Kanban, Scrum, Dynamic System Development
- Prototyping (development approach)
  - Prototype1 >> Prototype2 >> ... >> PrototypeN
- Rapid Application Development (RAD)
  - Iterative methodology + Prototyping
  - Minimun meetings, maximum development, only important features are developed, documentation is important
- Lean Software Development (LSD)
  - Remove unnecessary stuff, learning is important, decide as late as possible, develir fast, responsible team
- Kanban (as type of LSD)
  - Start with existing process, board with queue of tasks, capacity of each team member
- Feature-driven Development (FDD) - iterative and incremental process which is base on development by feature
  - Feature1 >> Feature2 >> ... >> FeatureN
- Use-Case-driven Process
  - Attributes are the Actor and the Use Case

#### RUP and AUP
- Rational Unified Process (RUP) attributes:
  - Iterative development, requirements, components, modelling & visualization, testing & quality
- RUP Static structure:
  - Who? (Dev, QC, BA, etc.)
  - How? (Think >> Perform >> Review)
  - What? (Models, Sources, Documents, Executables, etc.)
  - When? (The plan)
- RUP Dynamic structure:
  - Sequential process (e.g., Waterfall)
  - Iterative lifecycle (Waterfall1 >> Waterfall2 >> ...)
  - Phases:
    1. Inception
    2. Elaboration
    3. Construction
    4. Transition
- Agile Unified Process (AUP) - derevied from RUP and describes different principles and rules of Agile methodology
  - The flow: Sprint Release 1 >> ... >> Sprint Release N >> Production Release 1 >> Sprint Release N+1 >> ...

#### Extreme Programming
- Extreme Programming (XP) principles (best practices):
  - Programming in pairs
  - Unit testing
  - Simple and clear code
  - Managing requirements
  - Frequent communication with Customer
  - Planning
  - Test-driven Development (TDD)
  - Coding standards
- XP Activities
  - Coding
  - Testing
  - Designing
  - Listeting

#### Engineering Process Planning
- **Evaluating Technical Feasibility**
  - Requirements development: Business requirements, User requirements, Functional requirements, Quality requirements
  - Evaluating the requirements
  - Recommending best technologies
- **Unit Testing**
  - Characteristics of unit test: runs quickly, only one thing is tested, isolated, mocks/stubs/fakes are used, code coverage, assertions
  - Integration testing
- **Code Review**
  - Roles: Reviewer, Reviewee, Observer, Moderator, Reader
  - Advantages:
    - Better code
    - Better design
    - Better responsibility
    - Knowledge sharing
  - Areas to look for:
    - Design
    - Maintainability
    - Documentation
    - Security
    - Performance (in C#: dispose/using, string vs StringBuilder, exception handling, threading, boxing/unboxing, etc.)

## SCRUM Process
#### Scrum Essentials
- Scrum in hierarchy of methodologies: Incremental Development -> Agile -> Scrum
- 3 main principles of Scrum:
  - Transparency
  - Inspection
  - Adaptation
- Typical Scrum meetings:
  - Daily meeting (Transparency)
  - Planning, Demo (Inspection)
  - Retrospective (Adaptation)
- Scrum flows/ceremonies:
  - Sprint Planning (grooming, pre-planning, planning, tasks breakdown)
  - Daily Scrum (daily meeting, stand-up)
  - Reporting (demo)
  - Sprint Review (retrospective)
- Scrum Rolew:
  - Product Owner (BA, customer, main stakeholder)
  - Scrum Master (responsible for Scrum rules and processes on the project)
  - Development Team (developers, testers, designers etc.)
- Scrum Artifacts:
  - Product Backlog
  - Sprint Backlog
  - Burndown Chart
- Scrum scaling - Scrum with multiple teams involved
