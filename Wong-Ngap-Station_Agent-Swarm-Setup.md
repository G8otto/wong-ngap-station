# Wong Ngap Station — Agent Swarm Setup Guide (Kimi-Centric)

**Version 0.1 · 2026-09-14 · Companion to: Product Vision One-Pager**

---

## 1. Design Philosophy

An "AI-native company" in 2026 is not a single magical agent — it is **a small set of role-locked agents sharing one source of truth**, with a human CEO making decisions. Three primitives make it work:

1. **The Company Wiki** — one GitHub repo (`wong-ngap-station`) holding vision, strategy, roadmaps, and every agent's output. Agents don't talk to each other; they **read and write the wiki**. This kills coordination chaos.
2. **Role-locked agents** — each agent is a dedicated Kimi conversation (or Kimi Claw instance) with a pinned `ROLE.md`. It never drifts into another agent's job.
3. **A weekly cadence** — agents produce artifacts on a rhythm; the CEO reviews in one sitting. Autonomy inside the week, alignment at the week boundary.

**Budget envelope: $200+/month** → ~$120 Kimi membership/API headroom, ~$40 domain + analytics + tools, ~$40 reserve for paid experiments (Reddit/TikTok promotion tests).

---

## 2. Org Chart

```
                    ┌─────────────┐
                    │  CEO (You)  │  decisions, approvals, taste
                    └──────┬──────┘
                           │ weekly review
                    ┌──────┴──────┐
                    │ CHIEF OF     │  THIS conversation (Kimi)
                    │ STAFF        │  routing, wiki hygiene, standups
                    └──────┬──────┘
        ┌──────────┬───────┼───────────┬──────────┐
        ▼          ▼       ▼           ▼          ▼
   STRATEGY    PRODUCT   MARKETING   OPS &     (future:
   & RESEARCH  & ENG     & CONTENT   DATA      COMMUNITY
   agent       agent     agent       agent     agent)
```

| Agent | Runs on | Core mandate |
|---|---|---|
| **Chief of Staff** | This Kimi conversation (persistent) | Owns the wiki, breaks CEO goals into task cards, runs Monday planning / Friday review, quality-gates other agents' output |
| **Strategy & Research** | Kimi OK Computer sessions (spawned per research sprint) | Market scans, competitor teardowns, pricing analysis, festival calendar tracking |
| **Product & Engineering** | Kimi webapp-building sessions | Ships the web toy; later speccing the Steam port (Tauri/Godot decision) |
| **Marketing & Content** | Kimi sessions + **Kimi Claw** (always-on) | TikTok/Reels scripts, Reddit posts, devlog clips, press kit; Claw instance monitors mentions and drafts replies |
| **Ops & Data** | Kimi session + scheduled reminders | Weekly KPI report (analytics + Steamworks later), decision log, task board hygiene |

Why Kimi Claw for marketing: it is an always-online agent with long-term memory and configurable personas — the right substrate for "watch our mentions, keep a content calendar, nudge me when a clip overperforms." Research and building stay in on-demand sessions where context stays clean.

---

## 3. Repository Layout (the Company Wiki)

```
wong-ngap-station/
├── README.md                  # front door: vision + links
├── company/
│   ├── vision.md              # the One-Pager (v0.1 committed)
│   ├── decision-log.md        # every CEO decision, dated, with rationale
│   ├── roadmap.md             # phase plan, updated by Chief of Staff
│   └── metrics.md             # KPI table, updated weekly by Ops
├── agents/
│   ├── chief-of-staff.ROLE.md
│   ├── strategy.ROLE.md
│   ├── product.ROLE.md
│   ├── marketing.ROLE.md
│   └── ops.ROLE.md
├── tasks/
│   ├── backlog/               # task cards, one .md each
│   ├── in-progress/
│   └── done/
├── strategy/                  # research outputs
├── marketing/
│   ├── content-calendar.md
│   ├── clips/                 # scripts + shot lists
│   └── press-kit/
├── product/                   # links to code repo(s), specs
└── ops/
    └── weekly-reports/
```

**Task card format** (every unit of work):

```markdown
# TASK-001: Validate duck-clip hook on TikTok
- Owner: Marketing
- Sprint: 2026-W38
- Deliverable: 3 clip scripts + posting schedule → marketing/clips/
- Definition of done: CEO-approved scripts, calendar updated
- Status: backlog
```

---

## 4. ROLE.md Template (paste into each agent's first message / Kimi Claw persona)

```markdown
You are the {ROLE} of Wong Ngap Station, an AI-native indie game company.
Product: a cozy CCTV-observation simulator of a Hong Kong MTR station full of
costumed ducks. Phase 1 = free viral web toy; Phase 2 = $6.99 Steam idle game.

MANDATE: {one paragraph — what you own}
YOU DO NOT: {explicit scope boundaries}
SOURCE OF TRUTH: the company wiki (GitHub repo). Read vision.md and
roadmap.md before any task. Never contradict them; flag conflicts instead.
OUTPUT: always as markdown files matching the repo layout. Every deliverable
ends with: assumptions made, open questions for the CEO, suggested next task.
CADENCE: Monday planning input by 10:00, Friday artifact by 18:00 (HKT).
TONE: concise, evidence-cited, no hype. HK flavor is sacred.
```

**Concrete mandates:**

- **Strategy** — "Own the market map: competitor teardowns (Rusty's Retirement, Placid Plastic Duck Simulator, Spirit City, Townscaper), Steam festival calendar, pricing benchmarks, audience research. You do not write marketing copy or product specs."
- **Product** — "Own the playable artifact: web toy polish backlog, performance, the Steam-port technical decision. You do not set pricing or positioning; you flag technical risk to the CEO."
- **Marketing** — "Own attention: clip scripts, platform calendar, community drafts, press kit. You do not commit to launch dates; you propose, CEO approves."
- **Ops** — "Own the numbers and the paper trail: weekly KPI report, decision log upkeep, task board hygiene, budget tracking against the $200/mo envelope."

---

## 5. Weekly Operating Rhythm (HKT)

| When | Ritual | Who | Output |
|---|---|---|---|
| Mon 10:00 | Planning | Chief of Staff + CEO | 3–5 task cards moved to in-progress |
| Wed | Async check | Agents | Task card status updates in repo |
| Fri 18:00 | Artifacts due | All agents | Files committed to wiki |
| Fri 20:00 | **CEO review hour** | CEO | Decisions logged, next week steered |
| Sun | Ops digest | Ops agent | metrics.md + weekly report |

The Chief of Staff conversation should hold **memory instructions** (project facts, your preferences) so context survives across sessions; scheduled reminders (cron) fire the Monday/Friday rituals.

---

## 6. Sprint Zero — First Two Weeks (task package)

| # | Task | Owner | Deliverable |
|---|---|---|---|
| 1 | Register domain + deploy web MVP publicly | Product | Live URL |
| 2 | Competitor teardown: Rusty's Retirement launch timeline & festival strategy | Strategy | strategy/rustys-teardown.md |
| 3 | Record 5 CCTV duck clips from MVP; write 5 TikTok scripts | Marketing | marketing/clips/ + calendar |
| 4 | Set up analytics (Plausible) + email capture (Buttondown) | Product + Ops | Tracking live, signup form on site |
| 5 | Steamworks partner account + coming-soon page spec | Strategy + Product | Store page copy draft |
| 6 | Wallpaper Engine compatibility test (webpage wallpaper) | Product | Go/no-go note |
| 7 | Weekly report template + decision log initialized | Ops | ops/weekly-reports/000.md |

---

## 7. Rules of the Swarm (pin these)

1. **The wiki is the memory.** If it isn't in the repo, it didn't happen.
2. **Agents propose, CEO disposes.** No agent ships publicly, spends money, or changes pricing without a decision-log entry.
3. **One agent, one job.** Scope creep between agents is resolved by Chief of Staff, not by agents negotiating.
4. **Every artifact cites its evidence.** Numbers without sources get rejected at Friday review.
5. **Cost check monthly.** Ops reports API/tool spend vs. the $200 envelope; swarm shrinks before it overspends.
6. **Human taste is the moat.** Agents generate volume; the CEO's curation is the product.

---

*Setup checklist for the CEO: (1) create the GitHub repo and commit vision.md → (2) open the four agent conversations/Kimi Claw with their ROLE.md → (3) pin this document in each → (4) schedule Monday/Friday reminders → (5) kick off Sprint Zero task #1 tonight.*
