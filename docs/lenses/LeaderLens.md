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

LeaderLens **extends** the existing value/adoption measures (`AI Tasks`, `Estimated Hours Saved`,
`AI Assisted Value`, …) — it does not duplicate them — and layers on gamification:

- **Points** — a single configurable score (`LeaderLens Points`) driven by a **`Leader Metric`
  toggle**: *Reclaimed Hours* (default), *AI Tasks*, or *AI Value (£)*.
- **Rankings** — user / team / org `RANKX` rankings that respect slicers (`ALLSELECTED`), plus a
  percentile rank.
- **Leagues (climb / relegate)** — five divisions by percentile —
  **⚪ Starter → 🥉 Bronze → 🥈 Silver → 🥇 Gold → 💎 Diamond** — with month-over-month
  **▲ Promoted / ▬ Held / ▼ Relegated** movement.
- **Streaks** — consecutive **active weeks** (a week with ≥ 1 AI task): current streak + longest
  streak.
- **Badges** — emoji threshold flags: 🔥 On Fire (4-wk streak), 💎 Consistent (8-wk best run),
  🏅 Top Decile, 🚀 Fast Riser (promoted), 🤖 Agent Adopter, ⏱️ Time Saver, 🌐 Explorer — rolled
  into a badge strip + count.
- **Team roll-ups** — adoption aggregated up the manager chain (direct-manager tier works today;
  full org-chain tiers use the M2/PAX `Level*_Name` columns, with a `manager_*` / `PATH()` fallback).

> **Full DAX & bindings:** see **[`LeaderLens-measures.md`](./LeaderLens-measures.md)** — the reviewable
> measure catalogue (points, ranks, leagues, streaks, badges, de-identify) bound to the verified model.
> Measures/pages are applied in an **in-Desktop build pass** (open → add → refresh → save); the
> `.pbit` binaries are not edited blind.

## Privacy — names by default

LeaderLens shows **real names by default** so leaders can recognise their teams. A **de-identify toggle**
is provided as an **opt-in** for scenarios that require anonymised leaderboards.

> Public / demo assets (M6) always use **synthetic** names regardless of this default.

## Where it lives (pages)

Grouped under the **`Leader · …`** page-tab prefix:

- **Leader · Leaderboards** — individual + team leaderboards (name, points, rank; manager → team →
  individual drill).
- **Leader · Leagues** — division standings with promotion / relegation arrows.
- **Leader · Streaks & Badges** — streak leaders + the badge wall.

Each page carries the **`Leader Metric`** and **`Leader Privacy`** slicers, so the whole lens is
re-scored / anonymised from one place.

## Setup

LeaderLens needs the **org / manager hierarchy** for roll-ups. On the **SharePoint (PAX)** path this is
produced today; on **Fabric** the hierarchy is added in milestone M2. See
[`../PREREQUISITES.md`](../PREREQUISITES.md).

## Screenshot

_Added in M6 (anonymised demo assets)._
