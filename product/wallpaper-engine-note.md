# Wallpaper Engine Compatibility — Go/No-Go Note

**Sprint Zero, Task #6 · Owner: Product & Engineering Agent · 2026-09-14**

---

## Verdict: ✅ GO (conditional)

The Wong Ngap Station scene is technically compatible with Wallpaper Engine's web-wallpaper format today, with **one required code change** (wallpaper display mode) and **one outstanding real-hardware performance check** before Workshop publication.

---

## 1. What Wallpaper Engine supports (verified facts)

- Wallpaper Engine officially supports **web wallpapers** (HTML/CSS/JS). Import is done by dragging the main `.html` file into the editor's "Create Wallpaper" button; all sibling files are copied into `wallpaper_engine\projects\myprojects\`, and a `project.json` is generated. Publication to the Steam Workshop happens from the same editor. Source: [Wallpaper Engine designer docs — Creating a Web Wallpaper](https://docs.wallpaperengine.io/en/web/first/gettingstarted.html), retrieved 2026-09-14.
- The official docs require that wallpapers **bundle all assets locally** (no runtime dependency on our server) and **scale across resolutions/aspect ratios** (incl. 21:9 ultrawide). Source: same docs page, retrieved 2026-09-14.
- By default, Wallpaper Engine **pauses wallpaper playback while the user is in-game / running a fullscreen app** (configurable in its Performance tab, incl. "Stop (free memory)"). Source: [help.wallpaperengine.io — Performance issues / low FPS](https://help.wallpaperengine.io/en/performance/game.html), retrieved 2026-09-14.
- Channel size (why we care): Wallpaper Engine averaged **~75k concurrent users over the last 30 days** (peak 117,596) per [SteamCharts](https://steamcharts.com/app/431960), retrieved 2026-09-14; Steam's own stats page showed 81,274 concurrent / 97,656 daily peak on 2026-09-13; owner estimates sit at **20–50M** per [SteamSpy](https://steamspy.com/app/431960). This confirms vision.md's "sleeping giant channel" claim (directionally; vision's "75k avg concurrent" matches current data).

## 2. Our build vs. those requirements

| Requirement | Status | Evidence |
|---|---|---|
| Self-contained local bundle | ✅ Pass | `npm run build` produces a fully static `dist/` (index.html + 1 JS + 1 CSS, ~220 kB gzip JS). Three.js is bundled; no runtime network calls. The Plausible tag is dormant until a domain is configured and fails silently regardless. |
| Runs as a web page wallpaper | ✅ Pass (mechanism) | Standard WebGL canvas + rAF loop; no dependencies on browser chrome. Verified rendering correctly in Chromium at 1920×1080 and 960×540 (screenshots on file with Product agent). |
| Scales across resolutions / aspect ratios | ✅ Pass | Renderer resizes via `ResizeObserver`; grid layout is CSS `grid-cols-2/rows-3` on narrow, `grid-cols-3/rows-2` on wide. Ultrawide (21:9) keeps 3×2 grid — acceptable letterboxing of feed frames. |
| Audio behavior | ✅ Pass | `AudioContext` is only created on an explicit user click of the sound toggle; default state is **silent**. In Wallpaper Engine there is no user gesture, so the wallpaper stays mute by construction — no violation of WE audio norms. |
| Pauses when user is gaming | ✅ Pass (by platform) | rAF stops firing when WE pauses the page (default behavior, see §1). No code needed. |

## 3. Performance data (measured 2026-09-14, this codebase)

Measured against the production build via `renderer.info` and engine internals:

| Metric | Value | Assessment |
|---|---|---|
| Draw calls per camera view | 284 | — |
| Draw calls per frame (grid mode, 6 views) | **~1,704** | Main perf lever; high but tolerable given trivial geometry |
| Triangles per camera view | 10,608 | Tiny; ~64k tris/frame total — negligible for any real GPU |
| Shader programs | 8 | Trivial |
| Textures | 11 | Trivial VRAM footprint |
| Shadow maps | **none** (not enabled anywhere) | Good — no shadow-pass cost |
| pixelRatio cap | 2 | Reasonable; could expose a quality setting later |
| Steady-state duck population | 24 (`TARGET_DUCKS` in `sim.ts`; seeds 16) | **Note: the "30+ ducks @ 60fps" budget from my ROLE.md is not currently exercised** — population caps at ~24 plus train-alighting bursts |

**Honest caveat (verified fact vs. estimate):** this sandbox only has a *software* GL rasterizer (0.5 FPS there is meaningless). The 60 FPS-on-2021-MacBook-Air budget therefore remains an **estimate: high confidence of passing**, based on ~64k triangles/frame and 8 programs — workloads two orders of magnitude below what Apple-Silicon integrated GPUs sustain in WebGL. Cheapest way to raise confidence to "verified": CEO opens the deployed URL on the actual MacBook Air (and one Windows iGPU machine) and checks the frame rate — 5 minutes, no tooling. A built-in FPS counter (`?debug=1`) would make this trivial and is a 30-minute task.

**Identified optimization (not blocking):** merging static station geometry would cut draw calls ~5–10×. Effort S–M. Recommend deferring until real-hardware numbers exist — premature otherwise.

## 4. Required change before Workshop release: wallpaper display mode

The current UI is an *interactive observatory*: header bar, subscribe button, hint footer, duck profile cards, feed frames, scanline/vignette overlays. As a desktop wallpaper this chrome is wrong — users want the pure scene. Proposal (effort **S**, rollback = delete the query-param branch):

- Add a `?wallpaper=1` (or `#/wallpaper`) mode that hides all interactive UI (header/footer/buttons/cards), keeps the 6-camera grid + scanlines, and locks out pointer handling.
- Ship the Workshop item as the static `dist/` opened with that parameter baked into a tiny wrapper `index.html`.

**Risk: low.** No engine changes; display-only branch.

## 5. Packaging checklist (when CEO approves Phase 2 parallel freebie)

1. Implement wallpaper mode (§4) → rebuild → verify in browser at 16:9 and 21:9.
2. Real-hardware FPS check (§3).
3. Create WE project: drag `index.html` into WE editor → confirm `project.json` → preview at 1920×1080 + 3440×1440.
4. Workshop metadata: title 「黃鴨站 · Wong Ngap Station — CCTV Ducks」, type `web`, tags: relaxing / pixel-free 3D / ambient; description links to the Steam coming-soon page (funnel!) and the web toy URL.
5. Publish → log the Workshop ID in `company/metrics.md` as a tracked funnel source.

---

## Assumptions made

- Wallpaper Engine's web-wallpaper format and default pause behavior are as documented on the official docs/help sites retrieved 2026-09-14; no breaking change since.
- The wallpaper use-case is non-interactive by definition, so removing pointer handling is acceptable.
- TARGET_DUCKS = 24 is the intended population for now; the 30+ duck performance budget applies to a later, denser build.

## Open questions for the CEO

1. Approve the `?wallpaper=1` display-mode task (effort S) for the Sprint Zero backlog, or defer to Phase 2?
2. Wallpaper release timing: parallel-with-web-toy (extra discovery surface now) or hold until the Steam coming-soon page exists so the Workshop description has a wishlist link to point at? *Product recommendation: hold — the funnel value is the whole point.*
3. Can you run the 5-minute real-hardware FPS check once the MVP is public (§3)?

## Suggested next task

**TASK: Add `?debug=1` FPS/duck-count overlay + `?wallpaper=1` display mode** (one PR, effort S). Both are prerequisites for the Workshop release and for completing the performance budget verification.
