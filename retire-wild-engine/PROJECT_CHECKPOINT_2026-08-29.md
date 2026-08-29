# Retire Wild Engine — Project Checkpoint

**Date:** August 29, 2026  
**Status:** Shelved for today / ready to resume  
**Repository plan:** Separate GitHub repository under the existing GitHub account

---

## Project Purpose

Build a standalone retirement sequencing and decision-support engine for the Retire Wild, Retire Free plan.

The system should answer not only:

> Can we retire?

but more importantly:

> In what order should we use wages, cash, pretax accounts, Roth assets, HSA funds, HELOC capacity, and Social Security while controlling taxes, healthcare eligibility, benefit cliffs, and long-term portfolio risk?

The engine should optimize for lifetime usable spending and flexibility rather than simply maximizing the ending portfolio.

---

## Core Architecture Decision

Use the same GitHub login/account as the AI Factory, but keep the retirement project in a separate repository and separate file tree.

Recommended layout:

```text
D:\codex-projects\
├── ai-tools\
│   └── AI Factory
│
└── retire-wild-engine\
    └── Retirement sequencing project
```

Recommended GitHub repository:

```text
retire-wild-engine
```

The Factory can be used as a reference for persistent state, reports, tests, scheduling, health checks, and approval gates, but the retirement project should not depend directly on live Factory folders.

---

## Governing Planning Principle

The system must keep these two concepts separate every year:

1. Household spending / cash needed to live.
2. Taxable or benefit-countable income recognized during that year.

Annual sequencing order:

1. Determine required household spending.
2. Establish healthcare / MAGI constraints for that year.
3. Account for unavoidable income.
4. Choose the source of remaining spending.
5. Decide whether a Roth conversion is beneficial.
6. Deliberately use remaining tax/MAGI room before year-end.

---

## Planned Funding Sources

The sequencing engine will eventually evaluate combinations of:

- wages / side income
- cash
- taxable brokerage
- pretax retirement withdrawals
- Roth IRA contribution basis
- Roth conversion basis by conversion year
- Roth earnings
- HSA reimbursements
- HELOC draws and repayments
- Kellie Social Security
- Jason Social Security

---

## Rules Engine

The future rules layer should model:

- Federal income tax
- Michigan income tax
- MAGI
- ACA premium tax credits
- Michigan Medicaid / Healthy Michigan Plan
- SNAP interactions where applicable
- Rule of 55
- Age 59½ retirement-account rules
- Roth IRA ordering and conversion five-year rules
- HSA qualified reimbursements
- Medicare
- IRMAA two-year lookback
- Social Security claiming
- RMDs

PolicyEngine is a leading candidate for the tax/benefit rules layer, with Tax-Calculator available as a validation source.

---

## Optimization Objective

The optimizer should balance:

- lifestyle spending
- taxes
- healthcare costs
- benefit cliffs
- HELOC interest
- penalties
- account longevity
- sequence-of-returns risk
- Social Security timing
- survivor outcomes
- future RMD exposure
- adequate cash reserves

It should not automatically choose the strategy with the largest ending portfolio.

---

## Planned Retirement Phases

```text
Current work years
↓
Runway preparation
↓
Possible Rule-of-55 window
↓
First retirement bridge year
↓
Age 59½
↓
Kellie Social Security / Medicare transitions
↓
Jason Social Security / Medicare transitions
↓
Roth conversion and tax-management years
↓
RMD years
↓
Late retirement / survivor planning
```

Jason and Kellie must be modeled separately because their ages and Social Security / Medicare transitions occur at different times.

---

## Current Starter Project

A standalone starter project has already been created.

Current structure includes:

```text
retire-wild-engine/
├── README.md
├── docs/
│   ├── BLUEPRINT.md
│   └── BUILD_PLAN.md
├── engine/
├── data/
├── tests/
├── .gitignore
└── .env.example
```

A primitive one-year sequencing prototype exists.

It can already compare simplified combinations of:

- cash
- pretax withdrawals
- Roth withdrawals
- HSA reimbursements
- HELOC draws

It also contains basic strategy scoring and automated tests.

The current calculations are infrastructure scaffolding only and must not yet be treated as retirement recommendations.

---

## Important Modeling Requirements

### Rule of 55

Track:

- employer
- plan
- separation year
- age in separation year
- whether assets remain in the qualifying employer plan
- whether prior plans were rolled into the qualifying plan
- plan-specific withdrawal rules

### Roth

Track Roth money by source:

```text
Roth IRA
├── contribution basis
├── conversion basis — year 1
├── conversion basis — year 2
├── conversion basis — year 3
└── earnings
```

Do not model all Roth dollars identically.

### HSA

Create an unreimbursed qualified-medical-expense ledger so old qualified expenses can potentially become a future tax-free reimbursement reserve.

### HELOC

Treat HELOC use as a financing variable, not a tax loophole.

The engine should compare:

- interest cost
- tax timing
- healthcare/MAGI effect
- lender/freeze risk
- future repayment source

Using a retirement distribution to repay a HELOC does not change the distribution's tax treatment.

---

## Planned Strategy Competitors

The optimizer should eventually compare strategies such as:

1. MAGI Protection
2. Pretax Burn
3. Roth Conversion Window
4. Roth-Heavy Bridge
5. HSA-Assisted Bridge
6. HELOC Smoothing
7. Social Security Delay Bridge
8. Adaptive Optimizer

Each strategy should be evaluated on lifetime outcomes rather than one-year tax savings alone.

---

## Monte Carlo Plan

Monte Carlo should be added only after deterministic sequencing works correctly.

Each sequence should later be stress-tested against:

- poor first five years
- immediate bear market
- elevated inflation
- average markets
- strong markets
- healthcare shock
- major home repair
- early death of one spouse
- long life to age 95–100

---

## Future Command Center

The eventual dashboard should surface a simple annual operating plan:

```text
RETIRE WILD

Plan Status
Current Portfolio
Freedom Date
Annual Spending
MAGI Target
Projected MAGI
Healthcare Strategy

This Year's Funding:
Cash
Pretax
Roth
HSA
HELOC

Roth Conversion
Social Security Status
Federal Tax
Michigan Tax
Healthcare Cost
Ending Portfolio
Success Probability

NEXT BEST ACTION
WHY
```

The complexity should remain behind the interface.

---

## Automation Vision

Future automated workflow:

| Timing | Process |
|---|---|
| Monthly | Refresh balances, spending, and debt |
| Quarterly | Re-run lifetime sequence |
| September | Tax and MAGI forecast |
| October | Roth-conversion analysis |
| November | Healthcare comparison |
| December | Final withdrawal/conversion recommendation |
| January | Generate annual retirement operating plan |
| Annually | Refresh tax, Social Security, Medicare, Medicaid, SNAP, and ACA rules |

Automation should generate recommendations and reports only. It should not automatically execute financial transactions.

---

## Next Development Milestone

### Bridge-Year Engine v0.2

Resume here.

Goal:

> Given the household state at January 1 of a selected retirement year, automatically determine and compare ways to fund the next 12 months.

Minimum strategies to compare:

- Roth-heavy
- pretax-heavy
- HSA-assisted
- HELOC-assisted
- MAGI-protected
- optimizer-selected

Required output:

```text
Household spending
Unavoidable income
Target MAGI
Projected MAGI

Funding:
- wages
- cash
- taxable
- pretax
- Roth
- HSA
- HELOC

Federal tax
Michigan tax
Healthcare impact
HELOC interest
Ending account balances
Strategy score

Recommended sequence
Alternatives
Plain-English explanation of why the winner won
```

After this single-year engine is trustworthy, connect consecutive years into the lifetime sequencing model.

---

## Resume Instruction

When restarting this project, begin with:

> Open the Retire Wild Engine project checkpoint and continue with Bridge-Year Engine v0.2.

Do not restart architecture design unless a new constraint requires it.
