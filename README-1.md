# ClaudeFit

A personal fitness tracker built with React. Tracks workouts, body composition, nutrition, cycling power, and mesocycle periodisation — all in a single-page app running on GitHub Pages with zero backend.

**Three apps, one ecosystem:**

- **ClaudeFit** (this app) — daily tracking, gym logging, charts, AI food processing
- **Z2 CTRL** — Zone 2 roller sessions with live Bluetooth power and heart rate → [Open Z2 CTRL](https://richardmcdowall-glitch.github.io/Zone2/)
- **EatingWithClaude** — standalone meal builder with more food options → double-tap the 🍽️ icon in ClaudeFit, or [open directly](https://richardmcdowall-glitch.github.io/EatingWithClaude/)

All three share data via localStorage on the same domain.

---

## Getting Started

### 1. Clear old data (if updating)

Go to **⚙️ Settings → Profile** and tap **Clear All Data** at the bottom.

### 2. Set up your profile

On the same Profile page, fill in:

| Field | What it does |
|-------|-------------|
| **Name** | Shown in your morning greeting |
| **Weight target** | Reference line on your weight chart |
| **Cal floor / ceiling** | Colour-codes your calorie charts (green = in range) |
| **W/kg goals** | Reference lines on the power-to-weight chart |
| **FTP** | Your threshold power in watts |
| **Z2 target** | Weekly Zone 2 minutes goal |

Tap **Save**.

### 3. Get an API key for AI food processing

Go to [console.anthropic.com/settings/keys](https://console.anthropic.com/settings/keys) and create a key. Paste it into the **Claude API Key** field in Profile and Save.

This lets you type food notes ("2 eggs on toast, coffee with milk") and tap **Process** to get automatic calorie and macro estimates.

### 4. Set up EatingWithClaude (optional)

If you double-tap the 🍽️ food icon, it opens EatingWithClaude in a new tab. Go to its Settings and paste the same API key there.

---

## App Layout

**Bottom navigation:** 🏠 Home → 🏋️ Gym → 📈 Progress → 🍽️ Food → ⚙️ Settings

**Side panels:** Swipe from the left edge for a date sidebar. Swipe from the right edge for a quick calendar strip showing your week at a glance.

**Header:** The 🚴 Z2 button opens the Z2 CTRL cycling app. The 💾 button creates a full backup.

---

## Screen by Screen

### 🏠 Home

Your morning check-in. Enter today's weight, set mood and readiness (1–5 sliders), and optionally log Zone 2 minutes (for commutes or untracked rides). Tap Save.

Below the check-in: weight/target/W/kg stat cards, a 30-day consistency ring, and the body map showing which muscles you've trained in the last 10 days. Tap any muscle for detail.

### 🏋️ Gym

A scrolling day list. Tap any day to expand and log your session. Exercises come from your active training plan.

- **⭕** marks a set done and starts a rest timer
- **⇊** copies set 1's weight and reps to all sets
- **Feel indicators** per exercise (tap to cycle: more → growth → ok → twinge → pain → less)
- **💬** note bubble per exercise
- **🧘 Mobility** button logs a standard mobility session
- **📅 Move** relocates a session to another date
- **Plans** link in the header jumps to plan management

The coloured **meso banner** shows your current periodisation phase. Tap to change phase or cycle number.

### 📈 Progress

Charts and trends. Use the 7d/14d/30d/All selector to zoom.

- **Body weight trend** with target line and 7-day rolling average
- **Calorie intake** colour-coded against your floor/ceiling
- **W/kg weekly averages** with FTP and goal reference lines
- **EF trend** (Efficiency Factor = watts ÷ HR) for Z2 rides and spinning
- **Zone 2 weekly** totals vs your target

### 🍽️ Food

Four tabs: **Notes** (default), **History**, **Search**, **Import**.

- **Notes:** Type what you ate, tap **Process** for AI macro estimation, or **📷** for photo-based estimation. Requires API key in Profile.
- **Quick Add:** Fast entry with name, calories, protein, and date picker.
- **Favourites:** Tap ★ on any meal in History to save it. One-tap logging from favourites.
- **History:** Browse by day, colour-coded by calorie range. Expand any day to see individual meals.
- **Import:** Paste MEAL lines (from chat or other apps). Preview before saving.

### ⚙️ Settings

Tabs: Manual, Dev Notes, Exercises, Plans, + New Plan, Profile, Export, Mobility.

- **Profile:** All your targets, FTP, API key, and Clear All Data
- **Plans:** View, edit, clone, or reactivate training plans
- **Exercises:** Auto-built registry with muscle group overrides
- **Export:** Generate copyable text dumps of gym, food, plan, or full JSON data
- **Manual:** In-app help for every feature

---

## Backup & Restore

Tap **💾** in the header to create a JSON backup of everything. Copy it somewhere safe. To restore: tap Restore (also in the header) and either load a file or paste the JSON.

Backups include: health log, gym sessions, training plans, food data, favourites, exercise registry, profile settings, and all preferences.

---

## Tips

- The **rest timer** floats in the corner after marking a set done. Tap to dismiss.
- **Sideswipe left** for the date navigation sidebar. **Sideswipe right** for the quick calendar strip.
- Z2 ride data flows from Z2 CTRL → ClaudeFit via a copy-paste field on each day.
- EF below 1.0 flags fatigue 🚨 — useful for spotting overtraining or illness.
- All data stays in your browser's localStorage. Nothing is sent to any server except AI food calls (which go directly to Anthropic's API using your key).
