# Wong Ngap Station — Product Vision One-Pager

**Version 0.1 · 2026-09-14 · Owner: CEO (human) · Drafted by: Chief of Staff (Kimi)**

---

## 1. The Product

**Wong Ngap Station (黃鴨站)** is a cozy real-time observation simulator: a fictional Hong Kong MTR station populated by costumed ducks, watched through a bank of CCTV cameras. Ducks tap through turnstiles, wait on the platform, board trains, and leave — a living diorama the player observes, follows, and (in later versions) plays with.

**One-line pitch:** *A CCTV control room, but every commuter is a duck.*

**Current state:** Playable web MVP (Three.js, 6-camera CCTV wall, follow-cam, duck profiles, train cycle, procedural audio). Already validates the core fantasy.

---

## 2. Why Now — Market Evidence

- **Cozy is the clearest growth trend on Steam.** Games self-describing as "cozy" among titles grossing >$100k lifetime went from 0.4% (2022) to 3.1% (2025) — a ~675% rise in three years. 543 cozy-tagged games launched on Steam in 2025 alone, vs. 698 in all prior years combined (SteamDB via Destructoid / GameDiscoverCo / PC Gamer).
- **The "game you watch, not play" category is proven.** *Rusty's Retirement* (idle desktop-overlay game, solo dev) sold 100k copies in week one and 550k by mid-2025 at $7 (~$5 net/unit), with an 11% attach-rate $4 Supporter Pack DLC. *Placid Plastic Duck Simulator* proved ducks + idleness is a viable Steam category in itself.
- **Asia over-indexes for this genre.** Rusty's country split: 26% China, 10% Japan, 6% Korea, 4% Taiwan. A Hong Kong-themed cozy game is culturally native to the genre's biggest growth markets while remaining exotic-charming to the West.
- **Wallpaper Engine is a sleeping giant channel.** ~75k average concurrent users, 100k+ daily peaks, 20M+ owners, and it can run web pages as wallpapers — our Three.js scene is natively compatible.

---

## 3. Form-Factor Decision (the analysis you asked for)

| Option | Time-to-launch | Revenue potential | Risk | Verdict |
|---|---|---|---|---|
| **A. Web toy (free)** | ~2 weeks (MVP exists) | None directly; builds audience & email list | Low | ✅ **Phase 1 — launch first** |
| **B. Steam desktop cozy idle game** | ~3–4 months | High (proven comps at $5–8) | Medium | ✅ **Phase 2 — the business** |
| **C. Wallpaper Engine workshop** | ~1 week (scene is web-native) | Low-direct, strong funnel to B | Very low | ✅ **Phase 2 parallel freebie** |
| **D. Mobile app** | 4+ months | Uncertain; high CAC, store friction | High | ❌ Deferred indefinitely |

**Recommended sequence:**

**Phase 1 — "The Viral Toy" (Weeks 1–6).** Polish the web MVP, deploy at a memorable domain, ship to itch.io, post CCTV duck clips to TikTok/Reels/Shorts, submit to Product Hunt and relevant subreddits. Single CTA everywhere: **wishlist the Steam version / join the email list.** Cost: near zero. Purpose: validate the hook and build the launch list.

**Phase 2 — "The Steam Game" (Weeks 6–20).** Desktop ambient game (windowed + desktop-overlay mode à la Rusty's Retirement), $6.99, with a $3.99 Supporter Pack (golden duck outfit + exclusive station). Port via Tauri/Electron keeping the Three.js core, or Godot rewrite if performance demands. Launch aligned with a themed Steam festival. Simultaneously release the station scene as a **free Wallpaper Engine wallpaper** as a discovery funnel.

**Phase 3 — "The Franchise" (post-launch).** New stations (each an MTR-inspired diorama), duck collection/album mechanics, seasonal events. Mobile reconsidered only if Steam revenue > $50k.

---

## 4. Positioning & Audience

- **Primary:** Cozy/idle game players on Steam (Townscaper, Rusty's Retirement, Spirit City audience), global EN-first with zh-HK soul.
- **Secondary:** Hong Kong nostalgia diaspora + MTR/transit-enthusiast communities (unusually passionate, meme-literate).
- **Tertiary:** "Satisfying ambience" TikTok/YouTube audience — the CCTV format is clip-native.
- **Tone:** English UI, Hong Kong heart. Station names, duck names, and signage stay Cantonese-flavored (黃鴨站, 蛋撻, 叉燒) — this is the differentiator, not a localization afterthought.

---

## 5. Business Model

- Web toy: free, forever (audience asset).
- Steam: **$6.99** base + **$3.99 Supporter Pack** (cosmetic duck outfits — the accessory system already exists in code).
- Wallpaper Engine: free (marketing channel).
- Year-1 scenario bands (Steam gross, after Phase 1 validation): conservative 3k units (~$15k), base 15k units (~$75k), upside 60k+ units (~$300k, Rusty's-tier requires festival feature + streamer pickup).

---

## 6. Success Metrics (what the swarm reports on)

| Phase | North star | Supporting KPIs |
|---|---|---|
| 1 | 5,000 email/wishlist signups | Web sessions, TikTok clip views, Reddit upvote ratios |
| 2 pre-launch | 15,000 Steam wishlists | Wishlist weekly growth, festival featuring |
| 2 launch | 10,000 units in 30 days | Review score ≥ 90%, refund rate < 8% |

---

## 7. Operating Principles

1. **AI-native by default.** Every artifact (research, code, copy, sprites, schedules) is agent-produced; the human CEO decides, approves, and steers.
2. **Small swarm, real cadence.** 5 agents, weekly sprint rhythm, written decision log.
3. **Ship in public.** Devlog clips from week 1; the build process itself is marketing content ("I run a game studio where every employee is an AI").
4. **The HK flavor is sacred.** No genericizing the station names or duck personalities for "global appeal."

---

*Next document: `Wong-Ngap-Station_Agent-Swarm-Setup.md` — the org design and operating protocol that executes this vision.*
