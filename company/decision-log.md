# Decision Log â€” Wong Ngap Station

**Purpose:** Every CEO decision, dated, with rationale. Rule #2 of the swarm: *nothing public ships without an entry here.* New entries append to the top of the log (below this header); never edit or delete past entries â€” supersede them with a new entry that references the old number.

**Entry format:**

```
### #NNN â€” {decision in one line}
- **Date:** YYYY-MM-DD
- **Decided by:** CEO
- **Context:** {what prompted the decision}
- **Decision:** {what was decided, specific enough to act on}
- **Rationale:** {why, with evidence links where applicable}
- **Supersedes / supersedes-by:** {entry numbers, if applicable}
- **Revisit trigger:** {what condition would reopen this}
```

---

## Log

### #003 â€” Sub-$20 spend pre-authorized for Ops (spend note, not full log entry)
- **Date:** 2026-09-14
- **Decided by:** CEO
- **Context:** Ops asked whether small promo/tool spends (e.g., a $20 TikTok test from the reserve bucket) require a full decision-log entry each time.
- **Decision:** Any single spend **under $20 USD** is pre-authorized; Ops records it as a lightweight spend note in the weekly report's budget table (item, cost, category, purpose). Spends of **$20 or more** still require a full decision-log entry before the money moves.
- **Rationale:** Keeps the $40/month paid-experiment reserve nimble â€” approval friction on a $10 test would cost more in delay than the test itself â€” while preserving the paper trail via the weekly budget table.
- **Supersedes / supersedes-by:** â€”
- **Revisit trigger:** Aggregate sub-$20 spends exceed $60 in any calendar month (i.e., the reserve envelope is being consumed in small slices without CEO visibility), or any sub-$20 spend is contested at Friday review.

### #002 â€” Kimi membership/API spend amortized weekly in budget reporting
- **Date:** 2026-09-14
- **Decided by:** CEO
- **Context:** Ops asked whether the ~$120/month Kimi membership/API line should hit the budget table as cash-out events or amortized.
- **Decision:** Amortize weekly at **~$28/week** ($120 Ã· 4.3 weeks) as a standing line item in the weekly report budget table; cash-out items (domain, tools, promo tests) reported as they occur on top of that.
- **Rationale:** "Envelope % used" becomes meaningful from week 1 instead of spiking in whichever week the subscription renews; week-over-week budget comparison stays apples-to-apples.
- **Supersedes / supersedes-by:** â€”
- **Revisit trigger:** Actual monthly API/membership spend deviates from the $120 planning figure by more than Â±20%.

### #001 â€” Adopted three-phase strategy (web toy â†’ Steam idle game â†’ franchise), $6.99 price point, $200/month budget envelope
- **Date:** 2026-09-14
- **Decided by:** CEO
- **Context:** Company founding; product vision one-pager v0.1 drafted from market evidence on cozy/idle Steam category growth and the Rusty's Retirement comparable.
- **Decision:** Three-phase strategy locked â€” Phase 1 (weeks 1â€“6): free viral web toy to build email/Steam-wishlist list â†’ Phase 2 (weeks 6â€“20): $6.99 Steam desktop idle game + $3.99 Supporter Pack (duck outfits) + free Wallpaper Engine release as funnel â†’ Phase 3: franchise (more stations, duck collection); mobile deferred indefinitely. Steam base price set at **$6.99**. Total company spend capped at **$200/month** (~$120 Kimi/API headroom, ~$40 domain+analytics+tools, ~$40 paid-experiment reserve).
- **Rationale:** Cozy-tagged games among >$100k-grossing Steam titles rose ~675% from 2022 to 2025; Rusty's Retirement validated the desktop-idle form factor at a near-identical price point ($7) with 550k units sold by mid-2025; web-first phase costs near zero and de-risks the Steam launch by building the wishlist list in advance. Sources: `company/vision.md` Â§2.
- **Supersedes / supersedes-by:** â€” (founding entry)
- **Revisit trigger:** Phase 1 misses its 5,000 email/wishlist signup target by >50% at week 6, or Steam festival slot for the Phase 2 window is unavailable.

---

## Assumptions made

- Entry #001 wording follows the pre-approved text from the Ops agent's Sprint Zero assignment, expanded into the full entry format so future entries have a complete exemplar.
- Newest-first ordering (append below header) chosen over chronological so the CEO sees the latest state of play first; the log will naturally invert if the team prefers chronological â€” one-line change, flag it and Ops will flip.
- "Revisit trigger" added beyond the minimum spec so decisions die by evidence, not by drifting memory.

## Open questions for the CEO

1. Do decisions need an explicit "informed by" field naming which agent's artifact prompted them (e.g., strategy/rustys-teardown.md), or is the context line enough?
2. Should marketing spend approvals (e.g., a $20 TikTok promo test from the reserve bucket) require a full decision-log entry, or a lighter-weight "spend note" section below the log?

## Suggested next task

**TASK-009:** Initialize `company/metrics.md` â€” the running cumulative KPI table that weekly reports append to, so week-over-week trends are visible in one file. Effort: S. Owner: Ops. Can start immediately; first data row lands when Task #4 (analytics) goes live.
