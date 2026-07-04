# LeaderLens (Preview)

*Team & function roll-ups with gamified leagues, streaks, badges, and leaderboards.*

> **Status: Preview.** Built and usable; still stabilising as part of milestone M3.

## What it answers

- How does adoption **roll up** by team, function, and manager?
- Who are the **leaders** — top teams and individuals — and how do **streaks** and **badges** track
  sustained engagement?
- How do **league tables** compare cohorts to drive friendly competition?

## Source tables

| Table | Role | Required? |
|---|---|---|
| Audit log | Activity to rank and reward | **Core** |
| Org / manager hierarchy | Team & function roll-ups | **Required for roll-ups** |

## Key measures

- **Team roll-ups** — adoption aggregated up the manager chain.
- **Per-manager rankings**, **streaks**, **badges**, **league tables**.

## Privacy — names by default

LeaderLens shows **real names by default** so leaders can recognise their teams. A **de-identify toggle**
is provided as an **opt-in** for scenarios that require anonymised leaderboards.

> Public / demo assets (M6) always use **synthetic** names regardless of this default.

## Where it lives (pages)

- **Leaderboards** *(plus league / streak / badge views added in M3)*

## Setup

LeaderLens needs the **org / manager hierarchy** for roll-ups. On the **SharePoint (PAX)** path this is
produced today; on **Fabric** the hierarchy is added in milestone M2. See
[`../PREREQUISITES.md`](../PREREQUISITES.md).

## Screenshot

_Added in M6 (anonymised demo assets)._
