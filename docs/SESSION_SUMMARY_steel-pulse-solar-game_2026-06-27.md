# Session Summary: Steel Pulse Solar game

**Date:** 2026-06-27
**Project:** Solar Tycoon business sim ("Steel Pulse Solar"), a single self-contained HTML file game for Brian, his friends, and his teenage son. Teaches how a real solar-install company makes (and loses) money.
**Live URL:** https://steel-pulse-solar.vercel.app
**Tech:** One file, plain HTML/CSS/JS, no build step. Saves to localStorage. Installable PWA. Hosted free on Vercel.

---

## What was built this session (by topic)

### 1. Core game (Phase 1)
Built the whole playable game from scratch: weekly turn loop, two modes (Realistic vs Arcade) chosen on a start screen, win at $1,000,000 net worth, bankruptcy on $0 cash + no credit. Leads → take jobs → crew installs → get paid → pay overhead. Marketing slider drives lead volume, reputation drives lead quality. Random events.

### 2. Branding
Renamed everything from "Solar Tycoon" / "Amy's Solar Co." to **Steel Pulse Solar**. File renamed `solar-tycoon.html` → `steel-pulse-solar.html`.

### 3. Phone app (PWA) + deploy
Made it installable: web manifest, service worker (network-first so updates always show + offline fallback), app icons (sun over panels), apple-touch meta tags. Deployed to Vercel project `steel-pulse-solar`. Add-to-home-screen works on iOS/Android.

### 4. Graphics / engagement
- **Roof fills with panels** as each install progresses (per active job), sun lights up at 100%.
- **Neighborhood map** (bottom): finished homes with panels + sun, trucks parked at in-progress jobs, empty lots ahead.
- **Animated crew yard**: trucks with crew figures that react to staffing — overworked (orange, sweat) when too few, bored (gray, "z z z") when too many, dialed-in when balanced.

### 5. Realism mechanics (all gated to Realistic mode; Arcade stays breezy)
- **Crew sizing:** ideal 3–4 installers per job (Brian's real-world numbers). Drives the "Crew load" metric, the yard mood, inspection pass rate, and work speed.
- **Weekly cash flow** stat + **Crew load** readout.
- **Wave 1 (job lifecycle + getting-paid-is-slow):** permit (1 wk) → install → installed-awaiting-payment (3 wk for inspection + utility sign-off) → paid. New **"Pending pay"** stat shows receivables. Per-job status shows the stage. Jobs can **cancel** during permit. **Hiring takes 2 weeks** (recruiting), **quit freezes hiring 1 week**, **truck breakdown sidelines a truck 1 week**, new truck **takes 1 week to arrive**.
- **Credit auto-repay:** spare cash above a ~2-week-overhead cushion sweeps against the credit line each week, so "Credit used" drops and you stop bleeding ~30%/yr interest.
- **Deposit lowered to 25%** in Realistic so signing a job costs cash up front (materials > deposit). Each lead shows a red "costs $X up front" tag.
- **Events show as a bold colored banner** in the top card (no more modal popup interrupting Advance week). Green = good, amber = warning, red = bad. Clears on a quiet week.
- **Wave 2 (electrician crew):** second licensed trade, ideal 2 per job, $1,600/wk each. Too few = half-speed installs + higher inspection failure. Yard shows electricians in blue vs installers in green. "Elec crew" readout.
- **Wave 3 (materials inventory):** pre-buy panel stock at a 10% bulk discount ("Panel stock" + "+ $5k" button in the crew card). Jobs draw materials from stock first (no cash needed when stocked), and stock hedges price-spike events. Leads show "stock covers materials" when applicable.

### 6. Layout (iterated several times to Brian's spec)
Frozen top card (company line + Goal bar + Marketing slider + Advance week, always visible). Compact stat cards. Crew & equipment as a **3-column card** (animation | hire/buy controls | readouts). New leads + Active jobs as a **2-column row, full width**. Neighborhood + Job log stacked full-width at the bottom. Menu button removed.

---

## Key decisions + rationale
- **Single HTML file** over a game engine or Next.js: zero install, double-click to play, trivial to share/host, perfect for a numbers/dashboard tycoon game.
- **Realism gated by mode flags** in `MODES`: Realistic gets the full simulation, Arcade stays forgiving and fun for the teen. Lets one codebase serve both.
- **Deposit 25% (Realistic):** real cash deals often have the deposit smaller than materials, so you front cash and wait — the classic contractor squeeze, sharpening the core lesson.
- **Auto-repay credit (not manual):** less clicking, and it's what a smart operator does (kill expensive debt first). Cash flow shown is operating (pre-paydown) so the number stays meaningful.
- **Events in a banner, not a modal:** modals interrupted the Advance-week rhythm.

---

## What changed and what to verify
All changes are in the single file unless noted. **The game is deployed and was verified via scripted evals + screenshots this session (no console errors).**

- **`steel-pulse-solar.html` (the whole game):** open https://steel-pulse-solar.vercel.app (or double-click the file). Start a **Realistic** game to see all the realism; start **Arcade** to confirm it stays simple.
- **Wave 2 electricians:** in Realistic, crew card shows an "Electricians" hire row and an "Elec crew" readout. With 0 electricians and an active job, installs run half speed and the readout is red "None on site"; hire 2 (for 1 job) → green "Full crew" and full speed. Confirm overhead jumps $1,600 per electrician. In Arcade, the electrician row is hidden.
- **Wave 3 inventory:** in Realistic, crew card (left column) shows "Panel stock $0" + "+ $5k" button. Click it → cash drops ~$4,500 for $5,000 stock (10% off), logged. Take a job whose materials ≤ stock → the lead shows green "stock covers materials" and signing pulls from stock instead of cash. In Arcade, the panel-stock row is hidden.
- **Deposit / upfront cost:** in Realistic, every lead shows a red "costs $X up front." Note cash, take a job, confirm cash drops by that amount. Arcade leads have no red tag (signing nets positive).
- **Credit auto-repay:** get "Credit used" above $0 (buy a truck early), then advance weeks with income; confirm Credit used ticks DOWN, and logs "Credit line paid off" at $0.
- **Event banner:** advance weeks until an event fires; it appears as a colored banner in the top card (no popup). Bad = red, good = green. Advance into a quiet week → banner clears.
- **Job lifecycle:** sign a job → "Permit pending ~1 wk" → "Installing %" → "Installed, payment in ~3 wk" with the amount in "Pending pay" → final payment lands.
- **Layout:** header is one compact frozen card with Advance week always visible; crew card is 3 columns; New leads sits left of Active jobs full-width; no Menu button.
- **Deploy:** Vercel project `steel-pulse-solar`. Redeploy after edits with `vercel --prod --yes` run from the game folder. Aliases to https://steel-pulse-solar.vercel.app. The `.vercelignore` keeps `GAME_SPEC.md`, `server.js`, `.claude/` off the public host (e.g. `/GAME_SPEC.md` returns 404 — that's intended).
- **Local preview:** `.claude/launch.json` runs `server.js` (a tiny Node static server) on port 8765; serves the game at `/`.

### Tuning reference (in the `MODES` object near the top of the JS)
Realistic: deposit 0.25, installerSalary 1200, elecSalary 1600, bulkDiscount 0.90, permitWeeks 1, payDelay 3, hireLeadWeeks 2, quitFreezeWeeks 1, truckDown/Delivery 1, cancelChance 0.05. Arcade: all realism off/forgiving.

---

## Files created or modified (absolute paths)
- `/Users/brianwest/Documents/Claude Code/Personal Projects/Games/Solar Installer game/steel-pulse-solar.html` — the game (main file, heavily edited all session)
- `/Users/brianwest/Documents/Claude Code/Personal Projects/Games/Solar Installer game/GAME_SPEC.md` — design doc
- `/Users/brianwest/Documents/Claude Code/Personal Projects/Games/Solar Installer game/manifest.webmanifest`, `sw.js`, `icon-180.png`, `icon-192.png`, `icon-512.png` — PWA
- `/Users/brianwest/Documents/Claude Code/Personal Projects/Games/Solar Installer game/vercel.json`, `.vercelignore` — deploy config
- `/Users/brianwest/Documents/Claude Code/Personal Projects/Games/Solar Installer game/server.js`, `.claude/launch.json` — local preview

## Deploys / side effects
- Vercel project `steel-pulse-solar` created under scope `brian-ws-projects-0191b468`, live at https://steel-pulse-solar.vercel.app. `.vercel/` dir was created in the project (git-ignored by Vercel).
- Redeployed many times this session; final deploy includes Wave 2 + Wave 3.

## Open questions / pending TODOs
- `coSub` (the "4-person crew" header subtitle) was NOT updated to show electrician count — minor cosmetic gap.
- No in-game restart now that Menu is removed (only on win/bankrupt, or reload to resume).
- Wave 2/3 balance is untuned by real play — electrician half-speed penalty and 10% bulk discount are first-pass values.
- Remaining realism ideas not built (from the earlier brainstorm): seasonality/weather, sales funnel + CAC, callbacks/warranty, safety + insurance, crew experience tiers.

## Pick up here (next 1–3 actions)
1. **Playtest a full Realistic game** end to end with Wave 2 + 3 live; tune electrician penalty / inventory discount / deposit if it feels off.
2. Optionally update `coSub` to show electrician count (quick polish).
3. If Brian wants more depth, pick from the remaining realism ideas (seasonality, sales funnel, callbacks, etc.).
