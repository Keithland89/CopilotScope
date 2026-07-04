# CopilotScope — Engineering & Design Brief

**Owner:** Keith McGrane · **Audience:** GHCP / VS Code implementers · **Status:** Draft for build
**Related repos:** `Keithland89/AI-Business-Value-Dashboard` (the current dashboard → to become CopilotScope;
**interim-retitled "ValueLens"** by Keith) ·
`Keithland89/StudioLens-for-Copilot-Studio` (shipped standalone; formerly AgentLens)

> **✅ Naming resolution (Option A, confirmed):** the current dashboard was *interim-retitled* **ValueLens**,
> but in CopilotScope **ValueLens is one lens** (cost/value/ROI). Per Keith's decision, the **repo/product
> becomes `CopilotScope`** (the umbrella) and **ValueLens narrows to just the value/ROI lens**
> inside it. Apply this at M1 — do not leave the umbrella and a single lens sharing the name.

---

## 1. Vision & metaphor

Rebrand and reorganise the "AI Business Value Dashboard" family into the **CopilotScope** —
a scope of focused, well-named Power BI **lenses** for measuring Microsoft 365 Copilot **value,
adoption, readiness, maturity, behaviour, agents, and leadership impact**. Modelled on the
**Copilot Studio Kit** (one umbrella brand; several named modules that each do one job well).

**The metaphor — a microscope with swappable lenses.**
The **CopilotScope is the microscope**: you set up the *stage* (your data) **once**. Then you **swap in lenses**
to examine different things — value, adoption, behaviour, agents, leadership. The stage doesn't change;
the lens does. This is the core UX promise: **one setup, every lens.**

**One-liner:** *CopilotScope — one setup, many lenses. Measure the value, adoption, maturity,
behaviour, and impact of Microsoft 365 Copilot.*

Positioning language to weave into copy (grounded in current MS framing): *value realization*,
*adoption maturity* (Initial → Efficient), *the capacity gap*, *human-agent teams / Frontier Firm*.

---

## 2. Goals & non-goals

**Goals**
- A coherent, memorable **suite brand** (CopilotScope) with **swappable named lenses**.
- Make it unmistakable that **one data setup powers all lenses** — no per-lens reinstall.
- Preserve "everything in one place" — a leader can still see the whole picture.
- Add **LeaderLens** (managers/gamification), **ReadinessLens** (pre-adoption), **BehaviorLens** (M365).
- Keep **StudioLens** available standalone (its own repo) *and* as a lens inside CopilotScope.

**Non-goals (v1)**
- Not rebuilding the pipeline/measures from scratch — reorganise + extend.
- Not shipping separate data models per lens (see architecture decision).

---

## 3. Naming & taxonomy (the lenses)

Naming rules: PascalCase, no space, always suffixed `Lens` (e.g. `ValueLens`). Umbrella = **CopilotScope**.

| Lens | Audience | Job (one line) | Primary source |
|---|---|---|---|
| **ValueLens** | Exec / FinOps | Cost vs value, ROI, time & tasks saved | audit + credit/cost |
| **AdoptionLens** | Adoption / CoE | Post-adoption: usage, reach, activation | audit |
| **ReadinessLens** | CoE / IT | Pre-adoption: who's **licensed/enabled/ready**, provisioning, reclamation | licensed users / org |
| **MaturityLens** | Strategy / CoE | Proficiency curve (Initial→Efficient); "Maturity Meter" gauge | audit |
| **LeaderLens** | Managers / leaders | Team & function roll-up + **gamified leagues/streaks/badges** | audit + **org hierarchy** |
| **BehaviorLens** | CoE / workplace analytics | Employee **work-behaviour patterns** (Exchange/SharePoint/OneDrive/Teams) mapped to the AI-activity taxonomy — the **manual-vs-AI baseline** | **Purview UAL / M365 work-behaviour** |
| **StudioLens** *(= renamed AgentLens)* | Makers / CoE | Deep **Copilot Studio** agent evaluation (quality, topics, transcripts, errors, feedback, credits) | Dataverse transcripts (+ PPAC credits) |
| **GovernanceLens** *(optional)* | Admins / governance | Agent health, governance, feedback | agent tables + feedback |

**StudioLens dual availability:**
- **In CopilotScope** — the Studio page-group inside the Fabric build (lights up when transcripts are loaded).
- **Standalone** — the existing repo (rename `AgentLens-for-Copilot-Studio` → **`StudioLens-for-Copilot-Studio`**)
  for Studio-only / **Dataverse-Direct** users who don't want all of CopilotScope. Cross-linked both ways.

---

## 4. Product architecture — DECISION

**Option A — modular branding, one product per platform path.** Lenses are **named page-groups +
measure display-folders** inside a single dashboard per platform (one Fabric PBIT, one SharePoint PBIT),
fronted by a **"Scope Home" landing/nav page**. One data model, one refresh. *(This is the "microscope"
— one stage, swappable lenses.)*

**Why A over B (separate PBITs per lens):** preserves "everything in one place"; one semantic model =
no duplicated core tables or N× refresh setup; a measure fix lands once; still delivers CopilotScope's
modular identity (named lenses, per-lens nav + docs). **Option B rejected for v1.**

> ✅ Confirmed: umbrella **CopilotScope**, **Option A**, microscope framing.

---

## 5. "One setup, many lenses" — the core design

The single most important UX principle. Communicated three ways:

### 5a. Setup → Lens matrix (hero artifact on Scope Home)
Users see that **most lenses come free from the same core setup**; you only *add a source to swap in a
specialised lens*.

| Data source (set up once) | Lenses it unlocks |
|---|---|
| **Audit log** (core) | ValueLens · AdoptionLens · MaturityLens · LeaderLens |
| **Org data + manager hierarchy** | LeaderLens roll-ups · org slicing across all lenses |
| **Licensed users** | ReadinessLens |
| **Credit / cost (PPAC / MAC)** | ValueLens (cost pages) |
| **Copilot Studio transcripts (Dataverse)** | StudioLens |
| **M365 work behaviour (Purview UAL)** | BehaviorLens |
| **Product feedback / Agent 365** | GovernanceLens |

### 5b. Live lens status on Scope Home
Scope Home shows each lens tile as **active** (source loaded) or **greyed with "add <source> to unlock"** —
driven by the existing `Enable_*` toggles / presence of tables. The user literally sees which lenses
their current setup powers.

### 5c. "Set up once" docs (not per-lens)
A single **Set up once** section in the README (ingesters/PAX + parameters), then the matrix, then
optional per-lens deep-dive docs. No per-lens setup instructions.

**Combining lenses** is automatic in Option A — they share one model/report, so a user just navigates
between them; cross-filters and slicers are consistent across lenses.

---

## 6. Repository structure (target)

**Where:** build on **personal repos (`Keithland89/*`)** for now. Create CopilotScope as a **new** repo
`Keithland89/CopilotScope` (seeded from the current `AI-Business-Value-Dashboard`). Leave the
existing `AI-Business-Value-Dashboard` repo and its `microsoft/` mirror **untouched** until CopilotScope is
complete and tested, then move/mirror to `microsoft/` via OSPO.

```
CopilotScope/
├─ README.md                       ← Scope Home: microscope intro, Setup→Lens matrix, lens tiles, choose your path
├─ 1. Fabric/
│   ├─ CopilotScope - Fabric.pbit
│   ├─ notebooks/ (core/ + optional/)
│   └─ README.md                   ← "Set up once" (Fabric)
├─ 2. SharePoint/
│   ├─ CopilotScope - SharePoint.pbit
│   ├─ scripts/ (PAX wrappers)
│   └─ README.md                   ← "Set up once" (SharePoint/PAX)
├─ docs/
│   ├─ lenses/ ValueLens.md, AdoptionLens.md, ReadinessLens.md, MaturityLens.md, LeaderLens.md, BehaviorLens.md, StudioLens.md, GovernanceLens.md
│   ├─ DATA-DICTIONARY.md
│   └─ OPTIONAL-SOURCES.md
└─ assets/                          ← GIFs / screenshots per lens + Scope Home
```

**StudioLens** stays a standalone repo too (`StudioLens-for-Copilot-Studio`, renamed from AgentLens),
cross-linked from Scope Home as "the standalone Copilot Studio deep-dive (incl. Dataverse-Direct)".

---

## 7. Data model & sources (per lens)

Reuse the existing model. Each lens = a **display-folder grouping** of measures + a page group.
Keep the **optional-source pattern** (EmptyTable + `try…otherwise` + `Enable_*` toggles).

| Lens | Key tables | Key measures |
|---|---|---|
| ValueLens | audit, Human Time Estimates, credit/cost | Human Equivalent Hours, Estimated Hours Saved, PPUPM, billable/total credits |
| AdoptionLens | audit | active/enabled users, % active, activation, reach |
| ReadinessLens | licensed users, org | license status, readiness, reclamation candidates |
| MaturityLens | audit (User_Stage / _Maturity) | maturity-stage measures; **NEW** Initial→Efficient mapping + Maturity Meter |
| LeaderLens | audit + **org/manager hierarchy** | **NEW** team roll-ups, per-manager rankings, streaks, badges, league tables |
| BehaviorLens | **M365 work-behaviour (UAL)** + audit | **NEW/existing** behaviour taxonomy, manual-vs-AI baseline per behaviour |
| StudioLens | agent tables (transcripts) | quality/perf, topics, errors, feedback, credits |
| GovernanceLens | agent tables, feedback | governance/health, sentiment |

---

## 8. Design / UX

- **Scope Home** (mirrors Studio Kit home): microscope intro + Setup→Lens matrix + a **tile per lens**
  (icon, name, one-line job, active/greyed status, button → that lens's first page). "Data status" strip.
- **Per-lens sections**: contiguous page group, consistent header band with lens name + "back to Scope
  Home". Page tabs prefixed by lens (e.g. `Value · ROI`, `Adoption · Reach`, `Leader · Leagues`).
- **Single theme** (`theme.json`): palette, fonts, spacing, iconography — one visual language across lenses.
- **LeaderLens gamification**: leagues/divisions (climb/relegate), per-team & per-manager leaderboards
  rolled up the hierarchy, streaks & badges, manager→team→individual drill. **De-identified toggle**
  (default ON for the public template; real names only when the customer opts in). Tone = motivating team
  progress & reclaimed capacity, **not** individual surveillance.

---

## 9. Phased plan

- **M0 — Sign-off (blocking):** umbrella (**CopilotScope** ✅), Option A ✅, lens set, StudioLens
  rename, `microsoft/` mirror strategy.
- **M1 — Rebrand + restructure (docs/branding, low risk):** rename repo → `CopilotScope`;
  Scope Home README with **Setup→Lens matrix**; regroup page tabs into lens groups; add Scope Home nav page
  (Desktop-validate); add `docs/lenses/*.md`.
- **M1b — StudioLens rename:** rename `AgentLens-for-Copilot-Studio` → `StudioLens-for-Copilot-Studio`;
  update its README/hero/badges/GIF alt-text; cross-link from Scope Home.
- **M2 — Fabric org-hierarchy port (unblocks LeaderLens on Fabric):** port PAX's manager-hierarchy logic
  into `Copilot_Org_Data_Direct_Ingester.ipynb` — parent chain, level, management chain, direct/total
  report counts — **identical output shape to PAX** so the model binds unchanged.
- **M3 — LeaderLens:** new page group; league/streak/badge measures; hierarchy roll-up; de-identified
  toggle. SharePoint first (PAX hierarchy exists), Fabric after M2.
- **M4 — ReadinessLens + BehaviorLens:** split Readiness from Adoption; wire BehaviorLens to the M365
  work-behaviour source (optional; only lights up when supplied).
- **M5 — MaturityLens expansion:** map to Initial→Efficient; add the **Maturity Meter** gauge.
- **M6 — Polish + demo assets:** per-lens GIF/screenshots (anonymised), Scope Home GIF, publish.

Dependencies: M3(Fabric)→M2. M1/M1b/M4/M5 independent.

---

## 10. Concrete build tasks (ticket-ready)

1. **Repo rename + Scope Home README** — `CopilotScope`; microscope intro; **Setup→Lens matrix**;
   lens tiles; choose-your-path. *(docs)*
2. **StudioLens rename** — rename AgentLens repo → StudioLens; update README/badges/GIF; cross-link. *(docs)*
3. **Page-group reorg + Scope Home nav page** — lens-prefixed tabs; nav buttons/bookmarks; live lens status. *(PBIT, Desktop-validate)*
4. **Measure display-folders** — group measures under `ValueLens\`, `AdoptionLens\`, … *(TMDL)*
5. **Fabric org-hierarchy port** — manager chain in the Fabric org ingester; columns match PAX. *(notebook)*
6. **LeaderLens pages + measures** — leagues, leaderboards, streaks, badges, hierarchy drill, de-id toggle. *(PBIT + DAX)*
7. **ReadinessLens** — split from Adoption (licensing/readiness/reclamation). *(PBIT)*
8. **BehaviorLens** — M365 work-behaviour pages + manual-vs-AI baseline; optional-source gated. *(PBIT + ingester)*
9. **MaturityLens + Maturity Meter** — Initial→Efficient mapping + gauge. *(PBIT + DAX)*
10. **`docs/lenses/*.md`, `theme.json`, demo assets.** *(docs/assets)*

---

## 11. Conventions & guardrails (MUST follow)

- **No customer names/data anywhere** in public repos — code, comments, commits, PR text, sample data,
  screenshots. Scrub demo data (synthetic UPNs like `user000@example.com`, no tenant domains, no
  SharePoint URLs). Blur identifiers in any image.
- **`.pbit` are binaries** — never edit two branches touching the same `.pbit` in parallel; every `.pbit`
  change must be **opened + refreshed + saved in Power BI Desktop** to validate before merge.
- Prefer **in-Desktop edits** over blind binary/JSON surgery; validate a Desktop open after any
  pages.json / bookmarks / TMDL edit.
- **One focused PR per task**; conventional commits; include the Copilot co-author trailer.
- Keep the **optional-source pattern** and **contract column names** intact so measures keep binding.

---

## 12. Open decisions (need Keith's sign-off)

1. **StudioLens rename** — **DONE:** `AgentLens-for-Copilot-Studio` renamed →
   `StudioLens-for-Copilot-Studio` (PR #6). Cross-link Scope Home to it.
2. **`microsoft/` mirror** — **DECIDED:** build all of CopilotScope on **personal repos (`Keithland89/*`) first**;
   move/mirror to the `microsoft/` org (via OSPO) only **after it's complete and tested**. Do **not**
   touch the microsoft/ mirror until then.
3. **GovernanceLens** — first-class lens in v1, or fold into AdoptionLens/StudioLens?
4. **BehaviorLens data** — confirm it stays **optional** (Purview UAL may not be customer-accessible).
5. **LeaderLens privacy** — de-identified by default in the shipped template? (Recommended.)

---

## 13. Acceptance criteria (per milestone)
- **M1:** repo renamed; Scope Home renders with the Setup→Lens matrix + a tile per lens (active/greyed);
  all links resolve; no customer names; PBIT opens clean.
- **M1b:** StudioLens repo renamed; links/badges/GIF updated; cross-links resolve both ways.
- **M2:** Fabric org table exposes the same hierarchy columns as PAX; test-Lakehouse refresh yields a
  valid manager chain; no page breakage.
- **M3:** LeaderLens populates from the hierarchy on both paths; league/streak/badge measures validated;
  de-identified toggle works end-to-end.
- **M4:** ReadinessLens split clean; BehaviorLens lights up only when the M365 source is present.
- **M5:** maturity levels map to Initial→Efficient; Maturity Meter reads correctly.
- **M6:** per-lens + Scope Home demo assets published; all anonymised.

---

## Appendix — current-state facts implementers should know
- Deployment paths today: `1. Fabric` (notebooks/core + optional; Lakehouse; thin PBIT over SQL endpoint),
  `2. SharePoint` (PAX extract → rollup CSVs → PBIT).
- Core Fabric ingesters: audit log, licensed users, org data. Optional: transcript parser, credit, cost
  (Cowork/WorkIQ), product feedback, Agent 365.
- **Manager hierarchy** currently built only by **PAX `-UserInfoFile`** (SharePoint). The Fabric org
  ingester does **not** build it yet → task #5 / M2.
- Existing pages to regroup into lenses: Activation, Adoption & Reach, Activity & Value, Usage Maturity,
  Leaderboards, Agent Governance, User Feedback, License Readiness, Heatmap Trend, Credit/Cost Consumption
  (+ Studio pages → StudioLens).
- Behaviour taxonomy: `Behavior_Enriched` → `Value_Outcome`; value model via `Human Time Estimates` + PPUPM.
- **StudioLens** = the shipped `AgentLens-for-Copilot-Studio` repo (two paths: `1. Dataverse (Direct)`,
  `2. Fabric`); demo GIF already on its README.
