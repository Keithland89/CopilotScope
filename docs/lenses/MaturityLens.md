# MaturityLens

*The adoption proficiency curve — Initial → Efficient — with a Maturity Meter.*

## What it answers

- Where does the population sit on the **maturity curve** (Initial → Efficient)?
- How is maturity **progressing** over time?
- Which cohorts are advancing, and which are stuck at early stages?

## Source tables

| Table | Role | Required? |
|---|---|---|
| Audit log (`User_Stage` / `_Maturity`) | Maturity-stage classification | **Core** |

## Key measures

- **Maturity-stage measures** — population by stage.
- **Initial → Efficient mapping** — stage ordering along the proficiency curve.
- **Maturity Meter** — a gauge summarising overall maturity *(enhanced in milestone M5)*.

## Where it lives (pages)

- **Usage Maturity**

## Setup

MaturityLens runs from the **core audit log**. See [`../PREREQUISITES.md`](../PREREQUISITES.md).

## Screenshot

_Added in M6 (anonymised demo assets)._
