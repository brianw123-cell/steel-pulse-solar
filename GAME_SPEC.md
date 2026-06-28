# Steel Pulse Solar, Game Specification

*A business simulation game where you run a solar-install company. Built to be fun for a teenager and friends, and to quietly teach how a real contracting business actually makes (and loses) money.*

Status: v1 design spec. Numbers are starting values to tune. Brian knows the real market, so the economic model is meant to be corrected against reality.

---

## 1. The one-sentence pitch

Start with one truck, a credit line, and yourself. Bid on solar jobs, install them, get paid, survive payroll, hire a crew, buy equipment, and grow into a regional solar company without going bankrupt.

## 2. Who it's for and the vibe

- **Players:** Brian, friends, and a teenage son. Casual, pick-up-and-play.
- **Tone:** Light and snappy. Real business under the hood, but the surface is fun. Event text has a little humor. Numbers go up and it feels good.
- **Session length:** A full game runs 15 to 30 minutes. You can also play a fixed "challenge" length to compete with friends.
- **Not:** A twitch/action game. This is a dashboard-and-decisions game (think Lemonade Stand or RollerCoaster Tycoon's money side), which is exactly what mirrors a real company.

## 3. The teaching goal (why this mirrors the business)

Every mechanic maps to a real lesson:

| Game mechanic | Real-world lesson |
|---|---|
| Cash can hit zero even when you have signed jobs | **Cash flow timing** kills contractors, not lack of sales. You pay for materials and labor before the customer pays you. |
| Deposit now vs. paid-on-completion | Deposits fund the work. Terms matter. |
| Overhead is due every week no matter what | Fixed costs (payroll, trucks, insurance, rent) don't care if you sold a job this week. |
| Marketing spend buys leads with diminishing returns | **Customer acquisition cost (CAC)** is real and high in solar. |
| Reputation drives lead volume and pricing power | Reviews and referrals are the cheapest leads you'll ever get. |
| Hiring adds capacity but also fixed salary | Scaling too fast is how growing companies die. |
| Panel/material price swings and tax-credit changes | Supply chain and policy (the 30% federal ITC) move demand and margin. |
| Rushed or understaffed jobs cause callbacks | Quality is cheaper than warranty rework. |

If a player walks away understanding "revenue is not profit, and profit is not cash," the game did its job.

## 4. Core game loop (one turn = one week)

Each week you:

1. **See new leads.** Lead count depends on marketing spend + reputation. Each lead is a potential job.
2. **Bid / accept jobs.** Each job shows size (kW), roof difficulty, payout, deposit terms, and deadline.
3. **Assign crew** to jobs. Bigger jobs and tougher roofs take more crew-weeks.
4. **Buy materials** (panels, inverters, racking). Buy per-job or pre-stock in bulk for a discount if you have a warehouse.
5. **Advance the week.** Crews work, jobs progress, a random event may fire (weather, inspection, price spike, great review).
6. **Get paid** when a job finishes (final payment lands, minus any quality penalties).
7. **Pay overhead** automatically (salaries, truck payments, insurance, rent, loan interest).
8. **Repeat.** Keep cash above zero. Hit zero and you either take an emergency high-interest loan or go bankrupt (game over).

## 5. Game systems

### Money
- **Cash**, the number that ends your game if it hits zero.
- **Net worth**, cash + equipment value + a value for reputation. This is your **score**.
- **Credit line / loans**, borrow to cover gaps, but interest accrues every week.

### Jobs
- **Size:** 4 kW (small home) up to 20 kW+ (large home / small commercial).
- **Price to customer:** ~$2.50 to $3.50 per watt installed (tunable, region-dependent).
- **Material cost:** ~$0.70 to $1.10 per watt.
- **Labor:** measured in crew-weeks; scales with size and roof difficulty.
- **Difficulty modifiers:** steep pitch, old roof, tricky electrical, long drive.
- **Payment terms:** deposit (e.g., 50%) up front, remainder on completion. Some jobs are net-30 (paid a few weeks late) to teach cash-flow strain.

### Crew
- Start solo (you are 1 crew unit).
- **Hire installers** at a weekly salary. Each adds capacity.
- **Skill tiers:** rookie → journeyman → master. Higher skill = faster + better quality + fewer callbacks.
- **Trucks required:** roughly 1 truck per active crew.
- *(Optional depth)* morale/burnout if you overwork crews several weeks straight.

### Equipment
- **Trucks**, one per crew working in parallel.
- **Tools / equipment**, small upgrades to speed.
- **Warehouse**, unlock bulk panel buying at a discount, but adds rent.

### Reputation (0 to 100, shown as stars)
- Rises with on-time, quality installs. Falls with late, rushed, or failed-inspection jobs.
- Drives **how many leads** you get and **how much you can charge**.

### Marketing
- Spend per week to generate more leads. **Diminishing returns** (doubling spend does not double leads).
- *(Optional)* channels: door-knocking (cheap, slow), online ads (scalable, pricier), referrals (free, grows with reputation).

### Random events (the fun + the teaching)
A short list that fires occasionally:
- Rain delays an install a week.
- Failed inspection: rework costs money and time.
- Panel price spike / tariff: material cost jumps for a while.
- Big commercial contract appears (high payout, needs capacity).
- Glowing review: reputation boost.
- Truck breakdown: surprise repair bill.
- Tax-credit news: the 30% federal ITC changes, swinging customer demand up or down.
- An employee quits at the worst time.

## 6. Economic model (starting numbers, tune these against reality)

> Brian: these are placeholder figures so the game feels real. Correct them with your actual market numbers and the game becomes a genuinely useful teaching tool.

- **Sample 8 kW residential job:** 8,000 W × $3.00/W = **$24,000 revenue**.
- Materials at $0.90/W = $7,200. Labor + install, say $5,000. **Gross profit ≈ $11,800** before overhead.
- **Overhead per week** (solo start): truck $300, insurance $200, phone/misc $100 ≈ **$600/week** even with zero jobs.
- **Each installer hired:** ~$1,200/week salary (tune to your market).
- **Customer acquisition:** a few hundred to a few thousand dollars of marketing per closed job. CAC is deliberately painful, because it is in real life.
- **Starting cash:** ~$15,000 plus a $25,000 credit line (so you feel the squeeze early).
- **Win target (default):** grow net worth to **$1,000,000**, or survive and maximize net worth over a fixed run.

## 7. Progression and win conditions

**Company tiers** (cosmetic + capability milestones):
1. One-person operation
2. First hire, first dedicated truck
3. Multi-crew local company
4. Warehouse + office + a sales rep
5. Regional player taking commercial jobs

**Win conditions:**
- **Goal mode:** first to $1,000,000 net worth (or whatever target).
- **Challenge mode:** fixed length (e.g., a 2-year / 104-week run); highest net worth at the buzzer wins. This is the mode for competing with friends and your son.
- **Sandbox / endless:** no win, just see how big you can get.

**Difficulty:** Easy / Normal / Hard changes starting cash, overhead, and how brutal the events are.

## 8. Game modes

- **Career (default):** play to the $1M goal.
- **Challenge (multiplayer-friendly):** everyone plays the same fixed length and same difficulty, compares final net worth. v1 does this with a local high-score board (enter your name, score saves in the browser). A shared online leaderboard is a later add-on.
- **Sandbox:** endless.

## 9. Screens (UI)

1. **Main dashboard:** cash, net worth, week/date, reputation stars, active jobs with progress bars, crew status, and the big "Advance Week" button.
2. **Leads / Jobs board:** available leads to bid/accept; details on each.
3. **Crew & Equipment:** hire/fire, buy trucks, view skills.
4. **Marketing:** set weekly spend, pick channels.
5. **Event popups:** the random events, with a choice or an "OK."
6. **Game over / Victory:** final net worth, a one-line "grade," and the high-score entry.

Art does not need to be fancy. A clean dashboard with little house/job cards, progress bars, and dollar figures going up is plenty satisfying. We can add nicer art and sound in a polish pass.

## 10. Technical approach (recommended)

**Build it as a single self-contained HTML file** (`steel-pulse-solar.html`) using plain HTML, CSS, and JavaScript.

Why this is the right call for you:
- **No install, no build step, no server.** Double-click the file and it plays in any browser.
- **Easy to share:** email the file to friends, or drop it on a free host (Vercel) and send your son a link.
- **Saves progress** in the browser automatically (localStorage), no database needed.
- **Claude Code can build and update it fast,** and you can run it right here.

**The tradeoff:** a single HTML file is not a heavy game engine. For a numbers-and-dashboard tycoon game, that's a feature, not a limit. If you ever want animation-heavy 2D or 3D later, that's a different tool (Phaser or Godot). You don't need that here.

**Why not your usual Next.js + Supabase stack:** overkill for a game. More moving parts, needs a dev server running, and harder for a teenager to "just play." Save Supabase for if/when you want a shared online leaderboard across players.

## 11. Phased build plan

Playable at every step, not one giant black-box build.

- **Phase 1, Core loop (MVP):** cash, accept jobs, assign your solo crew, finish jobs, get paid, pay overhead, don't go bankrupt, win at the net-worth goal. Fully playable start to finish.
- **Phase 2, Growth:** hire crew, run multiple jobs in parallel, reputation, marketing for leads.
- **Phase 3, Depth:** random events, material price swings, equipment, warehouse, company tiers.
- **Phase 4, Polish + compete:** nicer art and a little sound, difficulty settings, high-score board, and the fixed-length Challenge mode for playing against friends and your son.

## 12. How to run and share it

1. Claude builds `steel-pulse-solar.html` in this project folder.
2. **Run it:** open the file in your browser (or Claude previews it here and sends a screenshot).
3. Play, tell Claude what's fun or boring, Claude iterates.
4. **Share with friends/son:** either send them the file, or host it free on Vercel and text them the link.

## 13. Open questions (your call before or during the build)

1. **Win target:** is $1M net worth the right goal, or do you prefer a fixed-length "2-year challenge" as the default?
2. **Realism dial:** lean more realistic (your real numbers, tighter margins) or more arcade (forgiving, faster growth) for the kids?
3. **Real numbers:** want to drop in your actual price-per-watt, material cost, and crew pay so it teaches your real economics?
4. **Naming:** "Steel Pulse Solar," "Roofing Tycoon," or a company-flavored name?
