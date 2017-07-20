# Estimation Basics

#### Navigation
- [Scope](https://github.com/kakarotto67/KnowledgeBank/blob/master/Estimation/Basics.md#scope)
- [Definition and Basics](https://github.com/kakarotto67/KnowledgeBank/blob/master/Estimation/Basics.md#definition-and-basics)

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
  - Planning poker (Scrum)
  - Wall estimation
    - From small capacity/low priority to big capacity/high priority
  - Work Breakdown Structure (WBS)
  - Three-point estimation
    - Expected Estimate = (Best + 4 * Most Likely + Worst) / 6
  - Decomposition & Recomposition
    - Law of Large Numbers - the more grained items to estimate, the better estimate
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
