# ✿ Life OS — The Capacity Engine

A custom-built, single-file responsive web dashboard designed to reduce cognitive overhead for people managing ADHD and hypermobility. The philosophy is simple: by handling the mechanics of remembering health protocols, puppy care, and daily routines, the app frees up mental bandwidth for the people and things that matter most.

---

## ✨ Core Features

### 🏠 Home — Daily Dashboard
The landing tab. Everything you need to start and pace your day, at a glance.
- **Live clock and date** widget — always oriented.
- **Timber needs mini-checklist** — quick-glance view of what Timber still needs today.
- **Calendar widget** — today's and tomorrow's events pulled from Google Calendar.
- **💜 Connection card** — Nathan / Mom / Sister orbits. Tap any person to log a moment together. Shows days since last connection.
- **✨ Build My Day button** — opens the Day Builder modal.
- **💭 Brain Dump** — zero-friction thought capture with "+ Day" queuing. Resets at midnight.
- **Daily soft checklist** — time-aware, section-collapsing checklist:
  - 🌅 **Morning** — Timber outside, Glucosamine, Iron, Vitamins, Vyvanse, Brush Teeth, Log breakfast.
  - ☀️ **Midday** — Iron nudge (only shows if morning Iron was skipped).
  - 🌙 **Evening** — Birth Control, Zoloft, Timber last out, Log dinner.
  - 🌿 **Wellness** — Red Light Therapy, Exercise/PT.
  - Auto-expand by time of day, section streaks, confetti on completion, midnight reset.

### 🐾 Timber — Puppy Care
Needs-based daily care tab built around Timber's age and development.
- **Age-aware exercise banner** — `5 min × age_months × 2` target. Calculates from Timber's birthday (December 30, 2025).
- **Activity log buttons** — four tap-to-log buttons with combined timeline:
  - 🦮 **Walk** — live timer + manual entry. Persistent floating 🐾 indicator appears on all tabs during a walk.
  - 🎓 **Train** — log a training session.
  - 🍽️ **Fed** — log a feeding with optional note.
  - 🚽 **Outside / Potty** — log a potty trip with last-trip timestamp.
- **Combined activity timeline** — all four activities logged today, newest first, with ✕ delete buttons.
- **🔗 Partner button** — generate and manage Nathan's partner view.
- **Training daily rotation card** — today's focus cues at a glance.
- **Memories log** — milestone tracking categorised by Social, Home Life, Health, Training.

### 🌿 Move — PT & Wellness
- Arm PT reference guide + weekly M/W/F consistency chart.
- RLT protocol: Face 10m → Hips 20m → Rotating 10m.

### 📊 Stats — Streaks & Progress
- 7-day completion heatmap, morning streak counter, Timber walk minutes this week.

### 📅 Calendar — Google Calendar (iCal)
- Paste your secret iCal URL once. Shows next 7 days grouped by day.

### 🏠 Sitter — Pet Care Guide
- Full sitter instructions accessible via tab or `#sitter` URL hash.

### 🎓 Train — Timber's Training Reference
**24 cues** across Foundation, Technique, Conditioning, and Enrichment categories.

Puppy class content through Week 4:
- *Weeks 1–2 (original):* Sit, Down, Name, Recall, Leave It, Touch, Paw, Magnetic Hand, Loose Leash Walking, Eye Contact, Alone Time, Fetch (2-toy), Grooming Tolerance, Snuffle Mat, Crate Happy Place
- *Week 3:* Find It, Up/Down Pattern Game, Mat Work (settling — no verbal cue yet), Engage/Disengage
- *Week 4:* Ping Pong Pattern Game, Mat Work with Duration (puppy pushups), Follow Me, Cookie Two Step, Choose to Heel

Status badges — tap to cycle: 🌱 New → 🔄 Practicing → ⭐ Mastered. Daily rotation, category filters, progress bar.

---

## 🔗 Partner View (Nathan)

Jasmine generates a standalone HTML file for Nathan via the **🔗 Partner** button on the Timber tab. It bakes in Gist credentials and has two tabs:

**Today tab:**
- Log buttons: 🦮 Walk · 🍽️ Feeding · 🎓 Training Session · 🚽 Outside/Potty
- Nathan's logs appear in Jasmine's app automatically
- Combined timeline — Nathan can delete his own entries with ✕
- Stats row: Walks / Walk mins / Meals / Potty trips
- Timber's Memories — Nathan can add memories; they merge into Jasmine's app on next pull

**Training tab:**
- **Today's Focus** — the same daily rotation Jasmine sees, with full cue + how-to
- **All Skills** — filterable by All / Class / New / Practicing / Mastered
- Training data updates automatically from the Gist — **no new link needed when skills are added**

A new link is only needed when the partner HTML structure itself changes (new buttons, new tab).

---

## ✨ Day Builder

Open via **Build My Day** on the Home tab. Saved task library + freeform add + Brain Dump → Day queue. Generates a time-blocked agenda on the Home dashboard.

---

## 📡 NFC Shortcuts

| NFC Tag | Action |
|---|---|
| `#nfc=teeth` | Silently checks Brush Teeth ✓ |
| `#nfc=meds-morning` | Opens modal: Glucosamine, Iron, Vitamins, Vyvanse |
| `#nfc=meds-evening` | Opens modal: Birth Control, Zoloft |
| `#nfc=walk` | Smart toggle — starts/stops walk timer and logs |
| `#nfc=cronometer` | Checks "logged meal" + opens Cronometer deep link |

---

## ☁️ Cloud Sync

### Personal Gist (Jasmine's phone ↔ laptop)
Auto-pushes on every save. Auto-pulls on app open + every 3 minutes.

| Data | Syncs |
|---|---|
| Timber memories | ✅ Merged by ID |
| PT daily progress | ✅ |
| Battery / energy log | ✅ |
| Connection log (Nathan/Mom/Sister) | ✅ |
| Brain dump + items | ✅ |
| Daily checklist state | ✅ |
| Timber walks / trains / feeds / potty | ✅ |
| Training skill statuses | ✅ |
| GitHub token | ❌ Per-device |
| Google Calendar iCal URL | ❌ Per-device |

### Partner Gist (Jasmine ↔ Nathan)

| Flow | How |
|---|---|
| Jasmine → Nathan | Pushed on every activity log and every memory save |
| Nathan → Jasmine | Nathan logs → partner Gist → Jasmine's app pulls + merges on next activity pull |
| Nathan's memories → Jasmine | Merged by ID, no duplicates |
| Training data | Always current via Gist, no new link needed |

**Setup:**
1. [github.com/settings/tokens/new](https://github.com/settings/tokens/new) → name it, select **gist** scope only
2. Tap the **Sync** dot in the header → paste token → Connect
3. For partner view: Timber tab → 🔗 Partner → Generate → send HTML to Nathan

---

## 🛠️ Technical Stack

| Component | Technology |
|---|---|
| Structure | HTML5 — single file (~8,628 lines, 488KB) |
| Styling | CSS3 (custom properties, grid, flexbox, safe-area-insets) |
| Logic | Vanilla JavaScript (ES6+), 4 script blocks |
| Charts | Chart.js |
| Typography | Google Fonts (Nunito) |
| Sync | GitHub Gist API (personal + partner Gist) |

---

## 🚀 Getting Started

1. Open `index.html` in Chrome or Safari
2. Add to home screen for full-screen app experience
3. Connect cloud sync via the Sync dot in the header (strongly recommended)
4. Connect Google Calendar via Cal tab → paste your secret iCal URL

---

## 📱 Device Support

Optimised for: Android phone (Chrome, primary) · Tablet · Windows laptop / Surface Pro

---

## 🛡️ Privacy

No data leaves your device except to:
- **GitHub Gist API** — your memories and logs, using your own token
- **allorigins.win** — CORS proxy for your iCal URL

---

<details>
<summary><b>🛠️ Maintenance & AI Collaboration Guide</b></summary>

## How to Make Changes

Your OS is a single HTML file. To update it:
1. Open Cowork and start a new session
2. Describe what you want — Claude has persistent memory of your OS structure and Timber's history
3. Changes are applied directly to your workspace folder

Your data is safe — it lives in localStorage and your Gist, not in the HTML file itself.

---

## What Lives Where

| Data | Location | Syncs |
|---|---|---|
| Timber memories | localStorage + personal Gist | ✅ Cross-device + partner |
| PT progress | localStorage + personal Gist | ✅ Cross-device |
| Battery log | localStorage + personal Gist | ✅ Cross-device |
| Connection log | localStorage + personal Gist | ✅ Cross-device |
| Checklist state | localStorage + personal Gist | ✅ Cross-device |
| Timber walks/feeds/trains/potty | localStorage + personal Gist | ✅ Cross-device + partner |
| Training skill statuses | localStorage + personal Gist | ✅ Cross-device |
| GitHub token | localStorage | ❌ Per device |
| iCal URL | localStorage | ❌ Per device |

---

## Troubleshooting

| Problem | Fix |
|---|---|
| White screen / blank app | JavaScript error — describe to Claude in Cowork |
| Partner page stuck on "loading" | Re-generate partner link — HTML structure may be outdated |
| Sync dot is red | Token expired — tap dot → renew at github.com/settings/tokens/new |
| Memories disappeared | If Gist connected: tap Sync dot to pull. If not: localStorage only. |
| Calendar not loading | Check iCal URL in Cal tab — may need to regenerate in Google Calendar settings |
| Walk timer stops on screen lock | Expected in browser — use phone native alarms for time-critical items |
| Checklist not resetting | Reset happens at midnight. Force-clear: `localStorage.removeItem('jlos_checklist_v2')` |
| Partner not seeing my logs | Tap any activity button to trigger a push, or use the Partner modal |

---

## Re-orienting Claude Mid-Session

> *"Quick context: this is Jasmine's single-file HTML Life OS (index.html, ~8,628 lines, 488KB). Timber is a miniature poodle born December 30, 2025. Tab bar: Home · Timber · Move · Stats · Cal · Sitter (Train also accessible). Home has soft checklist (Morning/Midday/Evening/Wellness), brain dump, Day Builder, calendar widget, connection orbits (Nathan/Mom/Sister). Timber tab has age-aware exercise banner (5min × age_months × 2), four activity buttons (Walk/Train/Fed/Potty) with combined timeline + ✕ delete buttons, memories log, partner button. Partner view is a standalone HTML with Today tab (log + timeline + memories) and Training tab (daily focus + all 24 skills). Sync: personal Gist for cross-device (checklist, walks, feeds, trains, potty, memories, connections, training statuses, brain dump); partner Gist for Nathan ↔ Jasmine. 24 TRAIN_CUES including weeks 3–4 puppy class content. NFC: #nfc=teeth/meds-morning/meds-evening/walk/cronometer. Design: kawaii pastel, lilac+matcha day, deep-plum+sage night. No Gemini. No template literals inside generatePartnerViewHtml. Always run node --check on all 4 script blocks after edits."*

</details>
