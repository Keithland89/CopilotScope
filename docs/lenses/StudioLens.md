# StudioLens

*Deep Copilot Studio agent evaluation — quality, topics, transcripts, errors, feedback, and credits.*

> **Also available standalone.** StudioLens ships both as a page-group inside CopilotScope **and** as its
> own repo for Studio-only / Dataverse-Direct users:
> **[StudioLens-for-Copilot-Studio](https://github.com/Keithland89/StudioLens-for-Copilot-Studio)**.

## What it answers

- How are individual **Copilot Studio agents** performing — quality, resolution, errors?
- What **topics** are users bringing, and what do **transcripts** and **feedback** reveal?
- What are agents **costing** in PPAC credits?

## Source tables

| Table | Role | Required? |
|---|---|---|
| Agent tables (transcripts) | Studio agent activity | **Required for this lens** |
| PPAC credits | Agent consumption | Optional |

## Key measures

- **Quality / performance**, **topics**, **errors**, **feedback**, **credits**.

## Where it lives

- The **Studio** page-group inside CopilotScope (lights up when transcripts are loaded), **or**
- the standalone [StudioLens-for-Copilot-Studio](https://github.com/Keithland89/StudioLens-for-Copilot-Studio)
  repo (two paths: **Dataverse (Direct)** and **Fabric**).

## Setup

Inside CopilotScope, StudioLens lights up when **Copilot Studio transcripts (Dataverse)** are loaded. For
Studio-only analysis, use the standalone repo. See [`../PREREQUISITES.md`](../PREREQUISITES.md).

## Screenshot

See the demo on the standalone repo. CopilotScope-integrated screenshots added in M6.
