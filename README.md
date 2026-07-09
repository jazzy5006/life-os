
/
/
ADDITION TO BUILD SPEC — Move Tab: PT Ramp-Up Engine
Paste this section into the Cowork overhaul prompt alongside the existing Move tab spec. It replaces the current "show everything for today" PT checklist behavior with a phased, gradually-unlocking system. All existing PT exercise data (names, doses, day assignments) is reused as-is.
Purpose
The user is restarting PT after a long gap and cannot resume the full daily/weekly load at once. The Move tab must support a graduated ramp-up: exercises unlock progressively, completion is scored only against what's currently active, and nothing that isn't unlocked yet is ever shown as incomplete or missed. The system must never create a sense of failure — no streaks, no red states, no auto-demotion.
Data model (synced to GitHub Gist, same pattern as other app state)

ptRamp: {
  phase: 1,                    // 1, 2, or 3
  unlocked: ["nerve-glides", "standing-clam", "single-leg-stance"],  // exercise ids
  snoozeUntil: null,           // ISO date — readiness suggestions hidden until this date
  completions: [               // one entry per exercise completion
    { id: "nerve-glides", date: "2026-07-03", time: "10:42", fatigue: 2 }
  ]                            // fatigue: 1 = easy, 2 = ok, 3 = rough, null = skipped rating
}
Give every exercise in the existing PT dataset a stable id (kebab-case of name).
Phase system

Phase 1: Daily Essentials + Movement Snacks groups only
Phase 2: adds Group A — Floor (M/W/F)
Phase 3: adds Group B — Standing (T/Th/Sat)
Groups outside the current phase are completely hidden from the daily checklist — not greyed out, not shown as locked rows with padlocks everywhere. A single quiet line at the bottom of the tab may say "Phase 2 adds Group A when you're ready 🌱". The weekly consistency chart and any completion percentages are calculated only against unlocked exercises active on that day. Historical days are scored against what was unlocked on that day (store the denominator with each day's log, or derive from completion records).
Unlock engine (within-phase ramp)
Each phase starts with a small subset unlocked at full prescribed dose (no modified reps/sets — the ramp is in exercise count, not dosage). Remaining exercises unlock one at a time in a fixed, pre-defined order:
Phase 1 — starts with: Nerve Glides, Standing Clam, Single Leg Stance Phase 1 unlock order: Iso Hip Abd (Wall) → Anti-Rotation Press → 4-Way Band Walk → Around the World → Side Plank (Knees) → Plank (Standard)
Phase 2 — starts with: Supine Bridge, Clamshell Phase 2 unlock order: Inner & Outer Thigh → Active Leg Raise → Lower Trunk Rotation → Open Book → Ham/Glute Ball Set
Phase 3 — starts with: Wall Squat (Ball), Prone Hip Extension Phase 3 unlock order: Lateral Step-Ups → 3-Way Reach (Band) → Slider Lunge (Rev) → Single-Leg RDL
Entering a new phase keeps all previously unlocked exercises active and adds the new phase's starting subset.
Readiness suggestions (app suggests, user confirms — never automatic)
Compute over the trailing 7 days:

completion rate = completions ÷ (active exercises scheduled on each of those days)
average fatigue across rated completions
When completion ≥ 75% AND average fatigue ≤ 2.0 ("ok" or better):

If exercises remain in the current phase's unlock order → show a gentle card: "Ready to unlock [next exercise name]? 🌱" with buttons Yes, add it / Not yet
If the current phase is fully unlocked → same card suggests advancing to the next phase: "Ready to start Phase [n]? It adds [group name]."
"Not yet" sets snoozeUntil to 3 days out. No penalty, no tracking of declines, no escalating language. The card simply reappears after the snooze if criteria still hold.
If average fatigue runs ≥ 2.5 over the trailing 7 days, show a soft (dismissible) note: "This week's been heavy — it's okay to hold here, or step back a phase if you want." Include an optional Step back button. The app never steps back automatically.
Serve Me One (snack-sized interface)
A prominent button at the top of the Move tab: "🎲 Serve me one" (or similar kawaii framing). Tapping it:

Picks the next undone unlocked exercise scheduled for today (in list order)
Shows it as a single large card: exercise name, dose (e.g., "3×10"), and one big Done ✓ button
On Done: logs the completion, then slides in the fatigue strip (below), then offers "Another? 🎲" or close
This is the primary interface for the spread-through-the-day pattern — one exercise per Pomodoro break. The full checklist view remains available below/behind it for people who want to batch.
Deep link: support a URL parameter (e.g., ?serve=1) that opens the app directly into Serve Me One mode, for NFC tag use. Follows the existing NFC pattern in the overhaul spec (every NFC action has a manual UI fallback — the button itself is the fallback).
If everything for today is done, Serve Me One shows a small celebration state ("All done for today 🌸") — calm, not confetti-explosion.
Fatigue check-in (after each mini-session)
Immediately after tapping Done on any exercise (via Serve Me One or the checklist), a three-emoji strip slides in:
😌 easy · 😐 ok · 😮‍💨 rough

One tap records it and dismisses
Auto-dismisses after ~5 seconds if ignored (fatigue = null, no nag, no "you forgot to rate")
Per-exercise fatigue is what feeds the readiness engine and allows distinguishing one hard exercise from general fatigue
Google Sheets logging
Extend the existing midnight/on-demand Sheets logging with:

Per-day: phase, count of active exercises, count completed, completion %, average fatigue
Per-completion (optional detail sheet or columns): exercise id, time, fatigue rating
Tone and framing rules (apply throughout)

Never show locked/future exercises as incomplete, missed, or overdue
No streak counters, no broken-streak messaging
Consistency chart shows percentages of active exercises only
All ramp-up language is invitational ("when you're ready", "want to add…?"), never evaluative ("you failed to", "you missed")
Stepping back a phase is presented as a neutral, valid option — same visual weight as advancing Visual style Matches the app's existing 2D Soft UI / Minimalist Sanrio aesthetic — pastel, neumorphic cards, rounded everything. The Serve Me One card is a good candidate for a slightly more playful treatment (it's the highest-frequency touchpoint of the feature).
Show more

Ran 2 commands, found files, read a file
Ran 2 commands, found files, read a file

Ran 15 commands, updated tasks, read 2 memories
Ran 15 commands, updated tasks, read 2 memories
Now writing the patch script (Python string-replacement with asserts, per the safety rules):


Created a file, ran a command
Created a file, ran a command
All 14 edits applied cleanly. Running the mandatory 4-block syntax check:


Updated tasks, ran a command
Updated tasks, ran a command
All blocks pass. Quick logic smoke-test of the ramp engine in isolation:


Ran a command
Ran a command
Test harness typo (window-scoped function), not an app bug — fixing the test line and rerunning:


Ran 2 commands
Ran 2 commands
All logic tests pass (chart correctly shows Mon–Thu 100%, future days neutral). Now updating README per the sync rules:


Edited 3 files, read a file
Edited 3 files, read a file
Final integrity check, then updating my memory notes:


Edited 2 files, read 2 files, ran a command
Edited 2 files, read 2 files, ran a command
The PT Ramp-Up Engine is built, all 4 script blocks pass node --check, logic unit-tested, and README updated.

You start today at Phase 1 with Nerve Glides, Standing Clam, and Single Leg Stance unlocked — everything else is invisible until the readiness card offers it. The 🎲 Serve Me One button sits at the top of the Move tab, fatigue emoji strip slides in after each Done, and ramp state syncs through your Gist like everything else. Write ?serve=1 to an NFC tag to jump straight into serve mode.

Three things worth knowing:

Google Sheets logging was skipped — it doesn't exist in the current build (it's part of the unbuilt overhaul spec), so there was nothing to extend. It'll slot in when we do the full overhaul.
Hip Flex into Ball wasn't in the spec's Phase 3 unlock order — I appended it last (after Single-Leg RDL). Say the word if you want it elsewhere.
Fixed a pre-existing bug: window.onload was calling two functions that don't exist (handleNFCHash, initMidnightReset), which silently killed the last init steps including agenda restore. They're guarded now — agenda persistence should be more reliable as a side effect.

C:\Users\jmaya\OneDrive\Documents\Claude\Projects\Jasmine OS\index.html
Code 

C:\Users\jmaya\OneDrive\Documents\Claude\Projects\Jasmine OS\README.md
Document 


Fable 5 is the most capable model and draws down usage much faster than Opus 4.8




Claude is AI and can make mistakes. Please double-check responses. Give us feedback


Readme · MD
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
### 🌿 Move — PT Ramp-Up Engine
A phased, gradually-unlocking PT system built for restarting after a gap — no streaks, no red states, no auto-demotion.
- **Three phases**: Phase 1 = Daily Essentials + Movement Snacks · Phase 2 adds Group A — Floor (M/W/F) · Phase 3 adds Group B — Standing (T/Th/Sat). Groups outside the current phase are completely hidden, never shown as missed.
- **Unlock engine** — each phase starts with a small subset at full dose; remaining exercises unlock one at a time in a fixed order, only when the app suggests it AND you confirm. Never automatic.
- **Readiness suggestions** — when trailing 7-day completion ≥ 75% and average fatigue ≤ 2.0, a gentle card offers the next unlock (or next phase). "Not yet" snoozes it 3 days, no penalty. If fatigue runs heavy (≥ 2.5), a soft note offers holding or stepping back — same visual weight as advancing.
- **🎲 Serve Me One** — one-tap snack-sized interface: serves the next undone exercise as a single card with a big Done ✓ button. Deep link `?serve=1` opens straight into it (for NFC tags).
- **Fatigue check-in** — after each Done, a three-emoji strip (😌 easy · 😐 ok · 😮‍💨 rough) slides in; auto-dismisses after ~5s if ignored. Feeds the readiness engine.
- **Weekly consistency chart** — scored only against exercises active on each day (denominator snapshotted daily).
- Arm PT reference guide + RLT protocol: Face 10m → Hips 20m → Rotating 10m.
### 📊 Stats — Streaks & Progress
- 7-day completion heatmap, morning streak counter, Timber walk minutes this week.
### 📅 Calendar — Google Calendar (iCal)
- Paste your secret iCal URL(s) — your personal calendar plus an optional shared/partner calendar. Both are fetched and merged into one combined view of the next 7 days, grouped by day.
### 🏠 Sitter — Pet Care Guide
- Full sitter instructions accessible via tab or `#sitter` URL hash.
- **Standalone shareable file**: `Timber Care Guide.html` — a self-contained copy of the sitter guide (general care reference, not date-specific) that can be sent directly to a sitter without exposing the rest of the OS. Re-generate manually by copying the Sitter tab content if it's updated.
### 🎓 Train — Timber's Training Reference
**28 cues** across Foundation, Technique, Conditioning, and Enrichment categories.
 
Puppy class content through Week 5:
- *Weeks 1–2 (original):* Sit, Down, Name, Recall, Leave It, Touch, Paw, Magnetic Hand, Loose Leash Walking, Eye Contact, Alone Time, Fetch (2-toy), Grooming Tolerance, Snuffle Mat, Crate Happy Place
- *Week 3:* Find It, Up/Down Pattern Game, Mat Work (settling — no verbal cue yet), Engage/Disengage
- *Week 4:* Ping Pong Pattern Game, Mat Work with Duration (puppy pushups), Follow Me, Cookie Two Step, Choose to Heel
- *Week 5:* Collar Grabs, Back-Step Recall, Get It and Come, Counting Game (calm greetings / keep-away management)
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
| `?serve=1` (URL param) | Opens Move tab directly in Serve Me One mode |
 
---
 
## ☁️ Cloud Sync
 
### Personal Gist (Jasmine's phone ↔ laptop)
Auto-pushes on every save. Auto-pulls on app open + every 3 minutes.
 
| Data | Syncs |
|---|---|
| Timber memories | ✅ Merged by ID |
| PT daily progress | ✅ |
| PT ramp state (phase, unlocks, completions, fatigue) | ✅ |
| Battery / energy log | ✅ |
| Connection log (Nathan/Mom/Sister) | ✅ |
| Brain dump + items | ✅ |
| Daily checklist state | ✅ |
| Timber walks / trains / feeds / potty | ✅ |
| Training skill statuses | ✅ |
| GitHub token | ❌ Per-device |
| Google Calendar iCal URL(s) | ❌ Per-device |
 
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
- **allorigins.win** — CORS proxy for your iCal URL(s)
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
| iCal URL(s) (personal + shared) | localStorage | ❌ Per device |
 
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
 
