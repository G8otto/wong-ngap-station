# Analytics + Email Capture — CEO Setup Guide

**Sprint Zero, Task #4 · Owner: Product & Engineering Agent · 2026-09-14**

Code work is **done and verified in-browser**. Two one-time account steps remain that require the CEO's email address. Everything is paste-and-go.

---

## 1. Plausible (analytics) — CEO-approved at ~$9/mo

Budget note for Ops: ~$9/mo ≈ 4.5% of the $200 envelope. Plausible is cookieless/GDPR-friendly, matching the "privacy-friendly" mandate.

**Steps (≈10 min):**
1. Register at https://plausible.io → add a new site with the production domain (once registered; until then use the publish URL, e.g. `<name>.ok.kimi.link`).
2. In the codebase, open `index.html` and replace `YOUR-PLAUSIBLE-DOMAIN` in the `data-domain` attribute with the exact domain added in step 1. The script tag is already in place:
   ```html
   <script defer data-domain="YOUR-PLAUSIBLE-DOMAIN" src="https://plausible.io/js/script.js"></script>
   ```
3. Rebuild + republish. Verify in the Plausible dashboard's real-time view by opening the site.

**State until configured:** the tag is dormant — with the placeholder domain it collects nothing and throws no user-facing errors.

## 2. Buttondown (email capture) — free tier

**Steps (≈10 min):**
1. Register at https://buttondown.com (free up to 100 subscribers; paid tiers start at $9/mo — flag to Ops when we cross 100).
2. In the codebase, open `src/components/SubscribePanel.tsx` and set:
   ```ts
   const BUTTONDOWN_USERNAME = 'YOUR_BUTTONDOWN_USERNAME'
   ```
3. Rebuild + republish. Test by subscribing with a real email; confirm it appears in the Buttondown dashboard.

**What ships in the UI:** an amber 「訂閱通知」 button in the header opens a CCTV-styled dialog with the mandated copy *"Get notified when the Steam version wishlists open."* (+ zh-HK line), email input, and submit. The form posts directly to Buttondown's embed endpoint — no backend required.

## 3. KPI wiring for Ops

- Web sessions → Plausible dashboard.
- Email signups → Buttondown subscriber count.
- Phase 1 north star: 5,000 email/wishlist signups (vision.md §6). Ops should snapshot both numbers weekly into `company/metrics.md`.

---

## Assumptions made

- Plausible's ~$9/mo tier covers our Phase 1 traffic (<10k monthly pageviews band); revisit if a clip goes viral.
- Buttondown free tier (100 subscribers) is acceptable for Sprint Zero; overage is a good problem and triggers a budget check.
- Both tools are acceptable under our privacy-friendly positioning; no cookie banner needed for Plausible (cookieless).

## Open questions for the CEO

1. Which email address should own the Plausible and Buttondown accounts?
2. Approve Buttondown paid tier automatically at >100 subscribers, or require a decision-log entry first? *Recommendation: decision-log entry — it is a recurring spend.*

## Suggested next task

Once both IDs are configured: Ops agent adds Plausible + Buttondown to the weekly report template as data sources (ops/weekly-reports/000.md).
