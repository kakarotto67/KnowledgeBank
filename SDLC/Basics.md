# SDLC General

#### Navigation
- [SDLC Essentials](https://github.com/kakarotto67/KnowledgeBank/blob/master/SDLC/Basics.md#sdlc-essentials)
- [RUP and AUP](https://github.com/kakarotto67/KnowledgeBank/blob/master/SDLC/Basics.md#rup-and-aup)
- [Waterfall vs Agile/Scrum vs Agile/Kanban](https://github.com/kakarotto67/KnowledgeBank/blob/master/SDLC/Basics.md#waterfall-vs-agilescrum-vs-agilekanban)
- [Extreme Programming](https://github.com/kakarotto67/KnowledgeBank/blob/master/SDLC/Basics.md#extreme-programming)
- [Engineering Process Planning](https://github.com/kakarotto67/KnowledgeBank/blob/master/SDLC/Basics.md#engineering-process-planning)
  - [Requirements Analysis & Evaluating Technical Feasibility](https://github.com/kakarotto67/KnowledgeBank/blob/master/SDLC/Basics.md#requirements-analysis--evaluating-technical-feasibility)
  - [Recommending Best Technologies](https://github.com/kakarotto67/KnowledgeBank/blob/master/SDLC/Basics.md#recommending-best-technologies)
  - [Defining Testing Process](https://github.com/kakarotto67/KnowledgeBank/blob/master/SDLC/Basics.md#defining-testing-process)
  - [Defining Code Review Process](https://github.com/kakarotto67/KnowledgeBank/blob/master/SDLC/Basics.md#defining-code-review-process)
  - [Defining Deployment Process](https://github.com/kakarotto67/KnowledgeBank/blob/master/SDLC/Basics.md#defining-deployment-process)
- [SCRUM Process](https://github.com/kakarotto67/KnowledgeBank/blob/master/SDLC/Basics.md#scrum-process)
  - [Scrum Essentials](https://github.com/kakarotto67/KnowledgeBank/blob/master/SDLC/Basics.md#scrum-essentials)

#### SDLC Essentials
- Typical Flow
  - Requirements >> Design >> Implementation >> Verification >> Maintenance
- Spiral Methodology
  - Determine objectives >> Identify & resolve risks >> Development & testing >> Plan next iteration ...
- Iterative Methodology
  - Waterfal1 >> Waterfal2 >> ... >> WaterfalN
- Incremental Development
  - Agile
    - Scrum
    - Kanban
    - Dynamic Systems Development Method (also related to RAD)
- Prototyping (development approach)
  - Prototype1 >> Prototype2 >> ... >> PrototypeN
- Rapid Application Development (RAD)
  - Iterative methodology + Prototyping
  - Minimun meetings, maximum development, only important features are developed, documentation is important
- Lean Software Development (LSD)
  - Remove unnecessary stuff, learning is important, decide as late as possible, develir fast, responsible team, see the whole
- Kanban
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

#### Waterfall vs Agile/Scrum vs Agile/Kanban
- Waterfall
  - Terms/artifacts/characteristics
    - Divided into stages
    - Difficult to implement the change request
    - Related to manufacturing industry
    - Isn't flexible
    - Flow: Requirements >> Design >> Implementation >> Verification >> Maintenance
  - Waterfall usage scenarios
    - Tremendous product development (e.g., space shuttle)
    - Well-defined requirements
    - No change requests
- Agile/Scrum
  - Terms/artifacts/characteristics
    - Scrum Team, Scrum Master and Product Owner
    - Product Backlog, Iteration Backlog, Burndown Chart
    - Transparency (daily meeting), Inspection (demo), Adaptation (retrospective)
  - Scrum usage scenarios
    - Long term project
    - No well-defined requirements at the initial stage, but you have a backlog and ready for iterative/incremental development
    - Change requests are expected
    - You have self-organized team of different specialities (developers, testers, designers, etc.)
- Agile/Kanban
  - Terms/artifacts/characteristics
    - Kanban board (typically has To Do/Active/Done stages)
    - Team member capacity
  - Kanban usage scenarios
    - You don't have a process defined and want to start from something lightweight
    - Your project is a support project
    - You don't have well-defined backlog
    - Your team is specialized on single area (e.g., you have team of DevOps)

#### Extreme Programming
- Extreme Programming (XP) principles (best practices):
  - Programming in pairs
  - Unit testing
  - Simple and clear code
  - Code review
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

## Engineering Process Planning
#### Requirements Analysis & Evaluating Technical Feasibility
  - Requirements development
    - Business requirements
    - User requirements
    - Functional requirements
    - Non-functional (quality) requirements
  - Evaluating the requirements
    - Perspective
    - Prioritization
    - Completeness
    - Feasibility
    - Correctness
#### Recommending Best Technologies
  - App type (desktop, web, mobile, service)
  - 3rd party frameworks, libraries, tools, controls, etc.
  - App server requirements
  - Data storage
  - Security, async messaging, remoting, etc.
#### Defining Testing Process
  - Code quality
    - Testing/TDD
    - Static Code Analysis
    - Code Review
  - Unit testing
    - Runs quickly
    - Only one thing is tested
    - Isolated
    - Mocks/stubs/fakes are used
    - Assertions are used
    - Code is covered as fully as possible
  - Integration testing
    - Create test plan
    - Execute use cases
    - Execute load testing
    - Execute stress testing
    - Execute globalization testing
    - Execute security testing
  - Performance/load testing
  - Manual testing
  - UI testing
  - Other types of testing: security testing, whibox testing, blackbox testing
#### Defining Code Review Process
  - Roles: Reviewer, Reviewee, Observer, Moderator, Reader
  - Advantages:
    - Better code
    - Better design
    - Better responsibility
    - Knowledge sharing
  - Areas to review:
    - Design (understandable, with no issues)
    - Maintainability (unit tests, code coverage)
    - Documentation (well-documented, commented)
    - Security (no vulnerabilities)
    - Performance (no leaks; specific to C#: dispose/using, string vs StringBuilder, exception handling, threading, boxing/unboxing, etc.)
#### Defining Deployment Process
- Define the following
  - Purpose of the app
  - All target environments
  - Resource requirements
  - Configuration requirements
  - Expected deployment scenarios 
  - Security & performance plan
  - Who will completed the deployment
  - Any pre-existing apps that must be also installed
- Tools
  - VS Setup project/VS Web setup
  - Click-Once deployment (desktop apps deployment)
  - MS Deploy (web apps deployment)
  - VS Publish Website (for web project)
  - VS Copy Website (for web site)
  - Other tools (WiX Toolset, Setup Factory, Install Shield, InnoSetup, XCopy, etc.)

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
