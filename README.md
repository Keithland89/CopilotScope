<div align="center">

# 🔬 CopilotScope

#### by Microsoft Business Value Advisory (BVA)

### One scope, many lenses. Power BI lenses to measure the **value, adoption, maturity, behaviour, and impact** of Microsoft 365 Copilot.

[![Built by Microsoft BVA](https://img.shields.io/badge/BUILT_BY-MICROSOFT_BVA-4F73B8?style=for-the-badge&labelColor=1C2632)](https://github.com/Keithland89/CopilotScope)
[![Power BI Template](https://img.shields.io/badge/POWER_BI-TEMPLATE-F2C811?style=for-the-badge&logo=powerbi&logoColor=1C2632&labelColor=1C2632)](#the-lenses)
[![Status](https://img.shields.io/badge/STATUS-IN_BUILD-09B39D?style=for-the-badge&labelColor=1C2632)](#status)

**Set up your data once — then swap in lenses.** Like a microscope, CopilotScope keeps the *stage*
(your Copilot data) fixed and lets you **swap lenses** to examine value, adoption, readiness, maturity,
behaviour, leadership, and Copilot Studio agents.

</div>

> **🚧 Status:** early build. CopilotScope reorganises the existing *AI Business Value Dashboard* into a
> kit of named Power BI **lenses**. See the milestone plan in the engineering brief.

---

## One setup, many lenses

Most lenses come from the **same core setup**. You only add a data source to unlock a specialised lens:

| Data source (set up once) | Lenses it unlocks |
|---|---|
| **Audit log** (core) | ValueLens · AdoptionLens · MaturityLens · LeaderLens |
| **Org data + manager hierarchy** | LeaderLens roll-ups · org slicing everywhere |
| **Licensed users** | ReadinessLens |
| **Credit / cost (PPAC / MAC)** | ValueLens (cost pages) |
| **Copilot Studio transcripts (Dataverse)** | StudioLens |
| **M365 work behaviour (Purview UAL)** | BehaviorLens |
| **Product feedback / Agent 365** | GovernanceLens |

## The lenses

| Lens | What it measures |
|---|---|
| **ValueLens** | Cost vs value, ROI, time & tasks saved |
| **AdoptionLens** | Usage, reach, activation |
| **ReadinessLens** | Who's licensed / enabled / ready; provisioning & reclamation |
| **MaturityLens** | Adoption proficiency curve (Initial → Efficient) |
| **LeaderLens** | Team & function roll-up with gamified leagues, streaks & leaderboards |
| **BehaviorLens** | M365 work-behaviour patterns — the manual-vs-AI baseline *(optional source)* |
| **StudioLens** | Deep Copilot Studio agent evaluation — also available standalone: [StudioLens-for-Copilot-Studio](https://github.com/Keithland89/StudioLens-for-Copilot-Studio) |
| **GovernanceLens** *(optional)* | Agent health, governance, feedback |

---

## Deployment paths (planned)

| Path | Best for |
|---|---|
| **1 · Fabric** | scheduled Spark ingestion, larger volumes, PPAC message-credit pages |
| **2 · SharePoint** | flat-file / Power Automate (PAX) landing |

## Related

- **[StudioLens](https://github.com/Keithland89/StudioLens-for-Copilot-Studio)** — the standalone
  Copilot Studio agent deep-dive (also runs Dataverse-Direct, no Fabric).

## About

CopilotScope is created and maintained by the **Microsoft Business Value Advisory (BVA)** team.

## License

MIT — see [LICENSE](./LICENSE).
