# Estimation Basics

#### Navigation
- [Scope](https://github.com/kakarotto67/KnowledgeBank/blob/master/Estimation/Basics.md#scope)
- [Definition and Basics](https://github.com/kakarotto67/KnowledgeBank/blob/master/Estimation/Basics.md#definition-and-basics)
- [Estimation Activities and Estimation Errors](https://github.com/kakarotto67/KnowledgeBank/blob/master/Estimation/Basics.md#estimation-activities-and-estimation-errors)
- [Estimation Size, Efforts and Schedule](https://github.com/kakarotto67/KnowledgeBank/blob/master/Estimation/Basics.md#estimation-size-efforts-and-schedule)
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
The following is list of typical **extra activities** that affect estimate:
- Unit Testing (~25%)
- Code Review (~10%)
- Defect Fixing (~15%)
- Manual Testing (~30%)

The following is list of typical **estimation errors**:
- Chaotic development process
- Inaccurate information about the project
- Omitted activities
- Unfamilliar business area
- Unfamilliar technology area
- Inexperienced personnel

#### Estimation Size, Efforts and Schedule
TBD

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
