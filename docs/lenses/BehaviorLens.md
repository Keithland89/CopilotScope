# BehaviorLens (WIP)

*Employee work-behaviour patterns mapped to the AI-activity taxonomy — the manual-vs-AI baseline.*

> **Status: Work in progress.** Actively being built; content and measures are still changing.

## What it answers

- What **work-behaviour patterns** exist across Exchange / SharePoint / OneDrive / Teams?
- How do those manual behaviours map onto the **AI-activity taxonomy** — where is work still done by hand?
- Where is the **manual-vs-AI baseline** widest, i.e. where could Copilot take the most off people's plates?

## Source tables

| Table | Role | Required? |
|---|---|---|
| M365 work behaviour (Purview UAL) | Manual work signals | **Required — optional source** |
| Audit log | AI-side activity for comparison | Core |

## Key measures

- **Behaviour taxonomy** — manual behaviours classified into activity types.
- **Manual-vs-AI baseline per behaviour** — the headroom for Copilot per behaviour.

## Where it lives (pages)

- *Behaviour pages added as the lens is built.*

## Setup

BehaviorLens is **optional** and depends on **Purview UAL / M365 work-behaviour** data, which may not be
accessible in every tenant. The lens greys out when the source is absent. See
[`../PREREQUISITES.md`](../PREREQUISITES.md).

## Screenshot

_Added in M6 (anonymised demo assets)._
