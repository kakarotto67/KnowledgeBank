# Estimation Basics

#### Navigation
- [Scope](https://github.com/kakarotto67/KnowledgeBank/blob/master/Estimation/Basics.md#scope)
- [Definition and Basics](https://github.com/kakarotto67/KnowledgeBank/blob/master/Estimation/Basics.md#definition-and-basics)
- [Estimation Activities and Estimation Errors](https://github.com/kakarotto67/KnowledgeBank/blob/master/Estimation/Basics.md#estimation-activities-and-estimation-errors)
- [Estimation Size, Efforts and Schedule](https://github.com/kakarotto67/KnowledgeBank/blob/master/Estimation/Basics.md#estimation-size-efforts-and-schedule)
- [Documenting and Presenting Estimates](https://github.com/kakarotto67/KnowledgeBank/blob/master/Estimation/Basics.md#documenting-and-presenting-estimates)
- [Cone of Uncertainty and Diseconomies of Scale](https://github.com/kakarotto67/KnowledgeBank/blob/master/Estimation/Basics.md#cone-of-uncertainty-and-diseconomies-of-scale)
- [Work Breakdown Structure](https://github.com/kakarotto67/KnowledgeBank/blob/master/Estimation/Basics.md#work-breakdown-structure)
- [Delphi Method](https://github.com/kakarotto67/KnowledgeBank/blob/master/Estimation/Basics.md#delphi-method)
- [Pert Analysis](https://github.com/kakarotto67/KnowledgeBank/blob/master/Estimation/Basics.md#pert-analysis)

#### Scope
- Project Scope
  - It is a work performed to deliver a product with the specified features
    - Management, budget, scheduling, organization, work, etc.
  - Project is needed to create a product
  - PM is responsible for Project Scope
- Product Scope
  - Features & functions of a product
    - All about the product, its characteristics, techincal specifications, business rules, etc.
  - BA is responsible for Product Scope
- Scope Creep
  - Business scope creep
  - Features scope creep
- Story-based Scope
  - Scoping project
  - Making a *Big Plan*
  - Release planning
  - Events (Add Story, Change Story, etc.)
  - The *First Plan*
  - Release variation (short, long, small stories)

#### Definition and Basics
- Estimate - How many time is needed to develop a product/feature/task/etc.
  - Target date - when we have to produce
  - Commitment date - when we can produce
  - Main estimation rule - Overestimate is better than Underestimate (efforts & costs)
- Estimation Types
  - Story points (Scrum)
  - Story-based estimation (Scrum)
    - Write User Story (US)
    - Estimate User Story's size in story points
    - Order User Stories (consider business value, technical risk, negotiating between two)
  - Planning poker (Scrum)
  - Analogy-based estimation (use historical data to give an estimate)
  - Wall estimation
    - From small capacity/low priority to big capacity/high priority
  - Work Breakdown Structure (WBS)
  - Three-point estimation
    - Expected Estimate = (Best + 4 * Most Likely + Worst) / 6
  - Decomposition & Recomposition
    - Law of Large Numbers - the more grained items to estimate, the better estimate
  - *Three Techniques*
    - Count (count something similar, use calibration)
    - Computation (use historical data, analogy-based estimation, etc.)
    - Judgment (use experts' experience to create an estimate)

#### Estimation Activities and Estimation Errors
The following is list of typical *extra activities* that affect estimate:
- Unit Testing (~25%)
- Code Review (~10%)
- Defect Fixing (~15%)
- Manual Testing (~30%)

The following is list of typical *estimation errors*:
- Chaotic development process
- Inaccurate information about the project
- Omitted activities
- Unfamilliar business area
- Unfamilliar technology area
- Inexperienced personnel

#### Estimation Size, Efforts and Schedule
The following is list of three main *Estimation Stages*:
- Estimating Size
  - Size types: Lines of Code (LOC), Story Points, Use Cases, Function Points, GUI Elements, Web Pages, etc.
  - Techniques: Analogy-based, Decomposition, Group Reviews, Delphi method, etc.
- Estimating Efforts
  - 1 Staff/Month = 174 hours
  - Equation Example: Staff/Months = 0.157 * (Function Points)^0.591 * (Max Team Size)^0.810
- Estimating Schedule
  - Equation Example: Schedule in Months = 3.0 * (Staff/Months)^1/3
  - Instead of 1/3 different exponent is used depending on the application type

#### Documenting and Presenting Estimates
- Required features, not required features, how to develop features, dependencies, performance, unknown items, etc.
- Confidence-based expressing (probability of release, e.g., Jan - 20%, Aug - 50%, Nov - 90%)
- Case-based approach (best case - Jan, planned - Aug, current state - Sep, worst - Nov)
- Use big estimation sizes: years, quarters, months, weeks, ranges
- Avoid small estimation sizes: days, hours, etc.

#### Cone of Uncertainty and Diseconomies of Scale
*Cone of Uncertainty* shows how estimation accuracy varies on different project stages

| Project Stage | Estimation Accuracy (approximated) |
| --- | --- |
| Initial Scope | 0.25X - 4X |
| Approved Definition | 0.5X - 2X |
| UI Completed | 0.75X - 1.5X |
| Detailed Design | 0.9X - 1.1X |
| Project Completed | 1X |

*Diseconomies of Scale* means that  1 million LOC system is more than 10 times complex than 100 000 LOC system.
As for example this is because of communication paths:
- 2 people - 1 communication path
- 3 people - 3 communication paths
- 4 people - 6 communication paths
- 5 people - 10 communication paths

etc.

#### Work Breakdown Structure
- WBS main formulas
  - Expected = (Best + 4 * Most Likely + Worst) / 6
  - Standard Deviation = (Worst - Best) / 6
  - Variance = (Standard Deviation)^2
  - Standard Complex Deviation = Sqrt(Sum of Variances)
  - Final Estimate = Sum of Expected + 2 * Standard Complex Deviation
- Simplified WBS example

| Best | Worst | Most Likely | Expected | Standard Deviation | Variance |
| --- | --- | --- | --- | --- | --- |
| 1 | 5 | 4 | 3.6 | 0.66 | 0.44 |

#### Delphi Method
TBD

#### Pert Analysis
TBD
