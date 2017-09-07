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
  - [MS Security Development Lifecycle](https://github.com/kakarotto67/KnowledgeBank/blob/master/SDLC/Basics.md#ms-security-development-lifecycle)
  - [Evaluating Application Performance](https://github.com/kakarotto67/KnowledgeBank/blob/master/SDLC/Basics.md#evaluating-application-performance)
  - [Evaluating Team Performance](https://github.com/kakarotto67/KnowledgeBank/blob/master/SDLC/Basics.md#evaluating-team-performance)
- [SCRUM Process](https://github.com/kakarotto67/KnowledgeBank/blob/master/SDLC/Basics.md#scrum-process)
  - [Scrum Essentials](https://github.com/kakarotto67/KnowledgeBank/blob/master/SDLC/Basics.md#scrum-essentials)
  - [Scrum vs Kanban](https://github.com/kakarotto67/KnowledgeBank/blob/master/SDLC/Basics.md#scrum-vs-kanban)
  - [Scaled Agile Framework](https://github.com/kakarotto67/KnowledgeBank/blob/master/SDLC/Basics.md#scaled-agile-framework)

#### SDLC Essentials
- Typical Phases
  - Simplified:
    - Planning >> Analysis >> Design >> Implementation >> Maintenance
  - Extended:
    - Initiation >> System Concept Development >> Planning >> Requirements Analysis >> Design >> Integration & Tests >> Implementation >> Operations & Maintenance >> Disposition
- Typical Waterfall flow
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
- Kanban
  - Start with existing process, board with queue of tasks, capacity of each team member
- Lean Software Development (LSD)
  - Remove unnecessary stuff, learning is important, decide as late as possible, develir fast, responsible team, see the whole
  - Scrum and Kanban are examples of LSD
- Feature-driven Development (FDD) - iterative and incremental process which is base on development by feature
  - Feature1 >> Feature2 >> ... >> FeatureN
- Use-Case-driven Process
  - Attributes are the Actor and the Use Case
- Other SDLC models
  - Software prototyping
  - Joint application development
  - Object-oriented development
  - Open source development
  - End user development

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
  - Coding standards & conventions
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
  - Manual & automation testing
  - Unit testing
    - Clear
    - Independent
    - Runs quickly
    - Only one thing is tested
    - Isolated
    - Mocks/stubs/fakes are used
    - Assertions are used
    - Code is covered as fully as possible
  - Integration testing (Top-Down, Bottom-Up, Umbrella Testing)
    - Create test plan
    - Execute use cases
    - Execute load testing
    - Execute stress testing
    - Execute globalization testing
    - Execute security testing
  - Stress testing
    - Identify key scenarios
    - Identify workload
    - Identify metrics
    - Create test cases
    - Simulate the load
    - Analyze results
  - Performance/load testing
    - Prepare baseline
    - Collect data
    - Analyze results
    - Reconfiguration
    - Testing and measurement
  - Manual testing
  - UI testing
  - Other types of testing
    - Regression testing
    - User acceptance testing
    - Security testing
    - Whitebox testing
    - Bblackbox testing
    - Web/Desktop/Mobile testing (by app type)
  - Good Test Framework
    - Test case
    - Test suite
    - Test fixture
  - What have to be tested
    - Public methods
    - Protected methods
    - Private methods
  - Environment Simulation
    - Hardware and software have to be similar to production
    - Clear logs after each test's run

Correlation between product levels and testing types

| Product Level | Type of Testing |
| --- | --- |
| Code | Compile |
| Design | Unit Tests |
| Architecture | Integration Tests |
| Requirements | User Acceptance Tests |

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
    - File System Editor, UI Editor, Registry Editor, File Types, Custom Actions, Launch Conditions
  - Click-Once deployment (desktop apps deployment)
  - MS Deploy (web apps deployment)
  - VS Publish Website (for web project)
  - VS Copy Website (for web site)
  - Other tools (WiX Toolset, Setup Factory, Install Shield, InnoSetup, XCopy, etc.)
- Possible types of app environments
  - Development environment
  - Common build environment
  - Integration testing environment
  - User acceptance testing environment
  - Production environment
#### MS Security Development Lifecycle
I. Training Phase
  - Core Security Training

II. Requirements Phase
  - Establish Security and Privacy Requirements
  - Create Quality Gates/Bug Bars
  - Perform Security and Privacy Risks Assessments

III. Design Phase
  - Establish Design Requirements
  - Attack Surface Analysis/Reduction
  - Use Threat Modeling

IV. Implementation Phase
  - Use Approved Tools
  - Deprecate Unsafe Functions
  - Perform Static Analysis

V. Verification Phase
  - Perform Dynamic Analysis
  - Fuzz Testing
  - Attack Surface Review

VI. Release Phase
  - Create an Incident Response Plan
  - Conduct Final Security Review
  - Certify Release and Archive

VII. Response Phase
  - Execute Incident Response Plan
#### Evaluating Application Performance
- Performance Modeling
  - Key usage scenarios identification
  - User & transaction workload
  - Performance objectives identification
  - Budget constraints
  - Identify processing steps
  - Allocate budget
  - Evaluate & validate your model
- Identify application performance spikes
- Analyze application performance trends
#### Evaluating Team Performance
- Team Velocity - the number of User Stories that team can develop per one Sprint. Typically defined as an average based on first 3-4 iterations. Calibration helps identify valid Team Velocity
- Factors that affect Team Velocity:
  - Team changes
  - New tools
  - Vendor defects
  - Responsibilities outside the project
  - Personal issues
  - Stakeholders
  - Unclear requirements
  - Changing requirements
  - Relocations

## SCRUM Process
#### Scrum Essentials
- Scrum in hierarchy of methodologies: Incremental Development -> Agile -> Scrum
- Forms of Scrum:
  - Scrum and ...
  - Scrum but ...
  - Scrum not ...
- 3 main principles of Scrum:
  - Transparency (daily meeting)
  - Inspection (planning, demo)
  - Adaptation (retrospective)
- Scrum Meetings/Ceremonies:
  - Sprint Planning (grooming, pre-planning, planning, tasks breakdown)
  - Daily Scrum (daily meeting, stand-up)
  - Reporting (demo)
  - Sprint Review (retrospective)
- Scrum Artifacts:
  - Backlog
    - Product Backlog
    - Sprint Backlog
  - Sprint Burndown Chart
  - Feature Burnup Chart
  - Scrum Board
  - Sprint
  - Feature/Epic, Story, Task
  - Definition of Done
- Tasks Decomposition hierarchy
  - Product >>
  - Feature/Epic >>
  - Story >>
    - Task
    - Bug
    - Technical Debt (did something in the fastest way and left to refactor later, didn't know how to do something in the right way, had knowledge but didn't have a time for right implementation, didn't have knowledge of the right implementation)
- Charts & Metrics
  - Story Points
  - Team Velocity
  - Sprint Burndown Chart
  - Feature Burnup Chart
  - Using charts you can see scope changes and track real progress
- Efforts estimation
  - Story Points types
    - S, M, L
    - Powers of 2 (1, 2, 4, 8, ...)
    - Fibonacci numbers (1, 2, 3, 5, 8, ...)
    - No Estimates approach (small vs need-to-be-split stories)
- The Sprint
  - Release planning (features estimation & prioritization)
  - Sprint planning
    - Planning poker
    - Affinity estimation
  - Daily scrum
  - Sprint demo
  - Retrospective
    - Story points triangulation
- Scrum Roles
  - Product Owner (BA, customer, main stakeholder)
  - Scrum Master (responsible for Scrum rules and processes on the project)
  - Development Team (developers, testers, designers etc.)
- Scrum issues
  - Maladaptive code
  - Untestability
  - Metrics (Code Coverage, LOC, Depth of Inheritance, Cyclomatic Complexity, etc.)
- Other
  - Scrum calendar - when to perform any meeting, etc.
  - Scrum scaling - Scrum with multiple teams involved

#### Scrum vs Kanban
- Similarities with Kanban
  - Lean & Agile
  - Work in progress
  - Transparency
  - Focus on delivering
  - Self-organized teams
  - Plan is optimized continuously
- Differences in Kanban
  - Specialized team
  - No backlog
  - New items can be added at any time
  - No roles
  - No charts

**Applicability**

| Scrum | Kanban |
| --- | --- |
| Cross functional team  | Team is specialized (devops team, support team, database team, etc.) |
| Product backlog | No product backlog |
| Typically for one big project | Typically for one small project or a set of small projects (e.g., support projects) |
| Extended process have to be setup | No process setup needed or lightweight process is needed |
| Stakeholders are ok with Scrum | No experience in Scrum |

#### Scaled Agile Framework
- Scaled Agile Framework (SAFe) - is a programming knowledge base that allows large organizations to move tword a more agile way of working
- SAFe has some similarities with Rational Unified Process (RUP)
- Release Train - team of teams (typically 50-150 persons)
- Release Planning consists of 2 days:
  - 1st day - Product Vision, Architecture Vision, Planning, Draft Plan, Management Review
  - 2nd day - Planning Adjustments, Final Plan Review, Risk Management, Plan Rework & Retrospective
- Risk Management
  - *Risk = Probability * Impact*
  - Risk can be
    - Mitigated
    - Transfered
    - Avoided/Eliminated
    - Shared (positive risk/opportunity)

**SAFe in one table**
TBD
