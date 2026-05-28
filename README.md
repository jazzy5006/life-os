# ✿ Life OS — The Capacity Engine

A custom-built, single-file responsive web dashboard designed to reduce cognitive overhead for people managing ADHD and hypermobility. The philosophy is simple: by handling the mechanics of remembering health protocols, puppy care, and daily routines, the app frees up mental bandwidth for the people and things that matter most.

---

## ✨ Core Features

### 🏠 Home — Daily Dashboard
The landing tab. Everything you need to start and pace your day, at a glance.
- **Live clock and date** widget — always oriented.
- **Timber needs mini-checklist** — quick-glance view of what Timber still needs today.
- **Calendar widget** — today's and tomorrow's events pulled from Google Calendar.
- **✨ Build My Day button** — opens the Day Builder modal.
- **💭 Brain Dump** — zero-friction thought capture. Type anything to get it out of your head, then decide whether to add it to your day. Items get a "+ Day" button to queue them in the Day Builder. Resets at midnight.
- **Daily soft checklist** — time-aware, section-collapsing checklist with four sections:
  - 🌅 **Morning** — Timber outside, Glucosamine, Iron (try w/ meal badge), Vitamins, Vyvanse (weekends default off with "taking it today" option), Brush Teeth, Log breakfast in Cronometer.
  - ☀️ **Midday** — Iron nudge (only shows if morning Iron was skipped; disappears once Iron is done).
  - 🌙 **Evening** — Birth Control, Zoloft, Timber last out, Log dinner.
  - 🌿 **Wellness** — Red Light Therapy, Exercise/PT.
  - Sections auto-expand by time of day. Section-level streaks. Confetti burst + banner on section completion. "Good enough" (80%+) midnight celebration before reset.

### 🐾 Timber — Puppy Care
Needs-based daily care tab, built around Timber's age and development.
- **Age-aware exercise banner** — calculates Timber's age from birthday (December 30, 2025), shows recommended daily exercise (5 min × age_months × 2). Walk over-exercise warning for pups under 6 months.
- **Daily needs checklist** — First outside (morning), Walk / active play (tap to log minutes), Training or enrichment, Last out before bed.
- **Walk timer** — tap to start/stop. A persistent 🐾 walk indicator appears on ALL tabs while a walk is in progress.
- **Walk log** — today's walks with duration.
- **Memories log** — milestone and memory tracking categorised by Social, Home Life, Health, Training. Quick-add preset buttons, editable timestamps.
- **Training daily rotation** — links to the Train tab's daily focus.

### 🌿 Move — PT & Wellness
Exercise reference and daily PT tracker.
- **Arm PT Reference:** Exercise guide and weekly consistency chart (M/W/F).
- **RLT Protocol:** Nightly sequence — Face 10m → Hips 20m → Rotating 10m.
- Day-specific exercises appear automatically on the correct days.

### 📊 Stats — Streaks & Progress
Celebratory, not analytical.
- **7-day completion heatmap** — visual history of checklist completions.
- **Morning streak counter** — consecutive days of full morning section completion.
- **Timber walk minutes this week** — total logged walk time.
- **Timber Reassessment Flags** — upcoming milestone reminders.

### 📅 Calendar — Google Calendar (iCal)
Read-only calendar integration.
- Paste your Google Calendar secret iCal URL once (Google Calendar → Settings → your calendar → "Secret address in iCal format").
- Shows the next 7 days grouped by day with event name, time, and duration.
- Today's and tomorrow's events also surface on the Home dashboard.

### 🏠 Sitter — Pet Care Guide
The full sitter guide for your pets — always accessible via this tab.
- Timber's care instructions, feeding schedule, emergency contacts.
- Also accessible directly via URL hash `#sitter`.

### 🎓 Train — Timber's Training Reference (preserved tab)
A dedicated training reference with Timber's full cue library.
- **Daily rotation** — which cues to focus on today.
- **Cue library** across four card types: 🎯 Cue · 🔧 Technique · 🌱 Conditioning · 🌿 Enrichment.
- **Status badges** — tap to cycle: 🌱 New → 🔄 Practicing → ⭐ Mastered.
- **Progress bar** and filters by category, status, source.

---

## ✨ Day Builder

Open via **Build My Day** on the Home tab.
- **Saved task library:** Deep Work 90m, Walk 30m, Training 15m, Meal 30m, Rest 60m, Admin 30m, PT 45m, Red Light 40m, Timber Time 20m.
- **Freeform add** — type any task name + duration.
- **Start time input** — generates a lightweight time-blocked agenda shown on the Home dashboard.
- Brain Dump items have a **+ Day** button to add them to the queue.

---

## 📡 NFC Shortcuts

Add NFC tags around your home to silently log actions. All have manual button equivalents.

| NFC Tag | Action |
|---|---|
| `#nfc=teeth` | Silently checks Brush Teeth ✓ |
| `#nfc=meds-morning` | Opens modal: Glucosamine, Iron, Vitamins, Vyvanse (with skip option) |
| `#nfc=meds-evening` | Opens modal: Birth Control, Zoloft |
| `#nfc=walk` | Smart toggle — starts walk timer if stopped, stops and logs if running |
| `#nfc=cronometer` | Checks "logged meal" + opens Cronometer deep link |

---

## 🤖 AI Features

| Feature | Where | Requires |
|---|---|---|
| 🤖 Ask Claude | Home → Day Builder / Flow bottom sheet | None (claude.ai proxy) |

---

## ☁️ Cloud Sync (GitHub Gist)

Timber memories, PT progress, battery logs, and connection logs sync to a private GitHub Gist.

**What syncs:** Timber memories · PT daily progress · Battery/energy logs · Connection logs

**What does NOT sync (per-device only):** GitHub token · Google Calendar iCal URL · Brain dump · Checklist state · Training cue statuses

**Setup:**
1. Go to [github.com/settings/tokens/new](https://github.com/settings/tokens/new)
2. Name it anything, select **gist** scope only
3. Tap the **Sync** dot in the header, paste your token, tap Connect

---

## 🛠️ Technical Stack

| Component | Technology |
|---|---|
| Structure | HTML5 |
| Styling | CSS3 (custom properties, grid, flexbox, safe-area-insets) |
| Logic | Vanilla JavaScript (ES6+) |
| Charts | Chart.js |
| Typography | Google Fonts (Nunito) |
| Calendar | iCal feed via allorigins.win CORS proxy |
| Storage | Browser localStorage + GitHub Gist |

Single-file architecture. No build step, no dependencies to install, no server required.

---

## 🚀 Getting Started

1. **Open** `index.html` in Chrome or Safari
2. **Add to home screen** for a full-screen app experience
3. **Connect cloud sync** via the Sync dot in the header (optional but recommended)
4. **Connect Google Calendar** via the Cal tab → paste your secret iCal URL

---

## 📱 Device Support

Optimised for: Android phone (Chrome, primary) · Tablet · Windows laptop / Surface Pro

---

## 🛡️ Privacy

- No data ever leaves your device except:
  - **GitHub Gist API** — your memories and logs, using your own token
  - **Anthropic (Claude)** — only when using Ask Claude inside claude.ai
  - **allorigins.win** — your iCal URL passes through this CORS proxy to fetch calendar data

---

<details>
<summary><b>🛠️ Maintenance & AI Collaboration Guide</b></summary>

## How to Make Changes

Your OS is a single HTML file. To update it:

1. **Open Cowork** and start a new session
2. **Describe what you want** in plain language — Claude has persistent memory of your OS structure and Timber's schedule history
3. Changes are applied directly to the file in your workspace folder

Your data is safe — it lives in localStorage and your Gist, not in the HTML file itself.

---

## What Lives Where

| Data | Location | Syncs |
|---|---|---|
| Timber memories | localStorage + GitHub Gist | ✅ Cross-device |
| PT progress | localStorage + GitHub Gist | ✅ Cross-device |
| Battery log | localStorage + GitHub Gist | ✅ Cross-device |
| Connection log | localStorage + GitHub Gist | ✅ Cross-device |
| Training cue statuses | localStorage | ❌ Per device |
| Brain dump notes | localStorage | ❌ Per device, midnight reset |
| Checklist state | localStorage | ❌ Per device, midnight reset |
| GitHub token | localStorage | ❌ Per device |
| iCal URL | localStorage | ❌ Per device |

---

## Troubleshooting

| Problem | Fix |
|---|---|
| White screen / blank app | JavaScript error. Describe the issue to Claude in Cowork. |
| Train tab shows 0 of 0 | Tap the Train tab to trigger a fresh render. |
| Sync dot is red | Token expired or offline. Tap dot → renew at github.com/settings/tokens/new. |
| Memories disappeared | If Gist connected: tap Sync to pull. If not: they were localStorage only. |
| Calendar not loading | Check your iCal URL in the Cal tab. May need to regenerate in Google Calendar settings. |
| Timers stop when screen locks | Expected behaviour in browser. Use phone native alarms for time-critical items. |
| Walk timer not showing | Tap the Timber tab and start a walk — the indicator appears on all tabs while active. |
| Checklist not resetting | Reset happens at midnight. Force-clear via browser console: `localStorage.removeItem('jlos_checklist_v2')` |

---

## Re-orienting Claude Mid-Session

If Claude loses context, paste this:

> *"Quick context: this is Jasmine's single-file HTML personal Life OS (index.html, ~7900 lines). Timber is a miniature poodle born December 30, 2025. The app has a top sticky tab bar: Home · Timber · Move · Stats · Cal · Sitter (the old Flow tab is commented out but preserved). Home tab has a soft daily checklist (Morning/Midday/Evening/Wellness), brain dump, Day Builder, calendar widget, and Timber mini-needs. Timber tab is needs-based (no rigid schedule): age-aware exercise banner using formula 5min × age_months × 2, walk timer with persistent walk indicator, memories log. NFC support via URL hash params (#nfc=teeth, meds-morning, meds-evening, walk, cronometer). Stats tab has 7-day heatmap and streak counter. Gemini has been removed. GitHub Gist sync retained. Google Calendar iCal retained. Design: minimalist kawaii pastel, lilac+matcha day theme, deep-plum+moonlit-sage night theme. Key CSS tokens: --la/--lm/--ll (lilac), --ma/--mm/--ml (sage), --pa/--pm/--pl (pink). Checklist data: const CHECKLIST=[...]. Training data: const TRAIN_CUES=[...]."*

</details>
