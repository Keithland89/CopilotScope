# ValueLens

*The FinOps view of Copilot — cost vs value, ROI, and time & tasks saved.*

## What it answers

- How much **time** and how many **tasks** has Copilot saved, and what is that worth in **money**?
- What is the **ROI** of Copilot once we factor in licence and consumption **cost**?
- How does realised value trend over time, and where is it concentrated?

## Source tables

| Table | Role | Required? |
|---|---|---|
| Audit log | Copilot activity that drives value | **Core** |
| Human Time Estimates | Minutes-saved assumptions per behaviour | Core (shipped) |
| Credit / cost (PPAC / MAC) | Message-credit and licence cost | Optional — unlocks the cost pages |

## Key measures

- **Human Equivalent Hours** — activity converted to hours of manual effort.
- **Estimated Hours Saved** — time returned to the business.
- **PPUPM** — price per user per month (licence cost basis).
- **Billable / total credits** — consumption reconciled against value (when credit/cost is loaded).

## Where it lives (pages)

- **Activity & Value**
- **Credit / Cost Consumption** *(appears when the credit/cost source is loaded)*

## Setup

ValueLens works from the **core audit log** out of the box. Load the **credit / cost** source to unlock
the cost/ROI pages. See [`../PREREQUISITES.md`](../PREREQUISITES.md).

## Screenshot

_Added in M6 (anonymised demo assets)._
