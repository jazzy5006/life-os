# ✿ Life OS — The Capacity Engine

A custom-built, single-file responsive web dashboard designed to reduce cognitive overhead for people managing ADHD and hypermobility. The philosophy is simple: by handling the mechanics of remembering health protocols, puppy care schedules, and daily routines, the app frees up mental bandwidth for the people and things that matter most.

---

## ✨ Core Features

### 🐾 Flow — Daily Schedule (ADHD Safety Net)
A dynamic timeline that grounds you in the present without overwhelming you.
- **Timber-integrated schedule:** Every potty trip, quiet time, training session, and walk is built into the timeline alongside your work blocks, meals, and wellness routines.
- **Consistent alarm reference:** Each block reflects the exact alarm you have set on your phone — the app is the visual map, your phone is the trigger.
- **"Where Am I?" Anchor:** Tap any schedule block to set your current position. The app calculates how far ahead or behind schedule you are and lets you shift the remaining day forward.
- **Today's Shape — Override Mode:** A collapsible card at the top of Flow. Auto-pulls today's calendar events, accepts a freetext context note, and uses Gemini to suggest which blocks to compress, skip, or move. Suggestions appear with one-tap Apply buttons.
- **Per-block overrides:** Tap any block → bottom sheet → ⏩ Compress · ✗ Skip · ↕ Move later · ↺ Clear. Colour-coded badges show on each block. Resets automatically at midnight.
- **48-Hour Horizon:** Collapsible Tomorrow preview at the top of Flow.
- **Contextual Filtering:** Toggle between All / 🐾 Timber / 💻 Work / 🌿 Wellness.
- **🎯 Now Button + ↑ Top Button:** Floating buttons to jump to your current moment or back to the top.
- **AI Replan:** 🚀 Replan with Gemini and 🤖 Ask Claude, both in the bottom sheet.
- **Day-specific blocks:** Arm PT (M/W/F) and other day-specific items appear automatically on the correct days.

### 💭 Brain Dump
A zero-friction thought capture area on the Flow tab.
- Type anything — how you're feeling, Timber moments, things to remember, random thoughts.
- Tap **✨ Sort this** and Gemini categorises your notes into chips with suggested actions.
- Clears automatically at midnight.

### 🐶 Timber — Puppy Care
- **Schedule:** Timber's quiet times, potty trips, training sessions, and walks are woven into the Flow timeline and visible in the Timber filter.
- **Quiet Time structure:** Two quiet-time windows per day (10:30 AM–12:30 PM and 2:15–4:15 PM). Each starts with a potty trip and a frozen treat (Kong, licki mat, or calming frozen mix) as the settle cue. Crate stays open — he chooses his dog bed, crate, or floor. Awake windows are ~1.5–2 hrs at this age.
- **Memories log:** Milestone and memory tracking categorised by Social, Home Life, Health, Training. Quick-add preset buttons, editable timestamps.
- **PT tracker:** Daily exercise completion tracker with a weekly consistency chart.
- **Timber Reassessment Flags:** Milestone reminders visible in the Stats tab.
- All Timber data syncs to GitHub Gist for cross-device access.

### 🎓 Train — Timber's Training Reference
A dedicated training reference tab with Timber's full cue library.
- **Daily rotation:** Shows which cues to focus on today based on a weekly schedule — no more forgetting what you've covered.
- **Cue library with 15 entries** across four distinct card types:
  - 🎯 **Cue** — explicit hand or word signals Timber responds to (Sit, Down, Recall, etc.)
  - 🔧 **Technique** — handler methods and protocol (Magnetic Hand, Loose Leash Walking)
  - 🌱 **Conditioning** — built through repeated exposure, no cue (Grooming Tolerance, Being Alone, Eye Contact)
  - 🌿 **Enrichment Tool** — mental/physical outlets (Snuffle Mat, Two-Toy Fetch)
- **Status badges:** Tap to cycle each cue through 🌱 New → 🔄 Practicing → ⭐ Mastered. Persists in localStorage.
- **Progress bar:** Shows how many cues are mastered at a glance.
- **Filters:** By category type, status, source (class vs. ZigZag), or status level.
- **Flow deep-link:** Breakfast and dinner training blocks in Flow have a 🎓 Train button that jumps straight to this tab.
- Session tips baked in: 5–10 min max, end on a win, mark the instant he gets it right.

### 📅 Calendar (Google Calendar — iCal)
Read-only calendar integration that pulls today's events directly into the app.
- Paste your Google Calendar secret iCal URL once in the Cal tab (Google Calendar → Settings → your calendar → "Secret address in iCal format").
- Shows the next 7 days grouped by day with event name, time, and duration.
- Today's events auto-populate into the **Today's Shape** card so Gemini can plan around them.

### 🔋 Energy & Capacity System
- **Battery Logger:** Five emoji levels logged daily, displayed as a 7-day arc.
- **Capacity Scaler:** When battery is low, a Gemini-powered button suggests what to compress or skip.
- **Today's Shape** uses your current battery level as context when generating override suggestions.

### 💜 Connection Heartbeat
- **Connection Orbits:** Visual rings showing how recently you've connected with your closest people. Rings shift warm green → cool blue → amber → soft red over time.
- **Gentle Nudges:** Quiet prompts when someone hasn't been reached in a while.
- **Connection Log:** One tap to log a call, text, or meaningful moment.

### 📊 Stats & Health Protocols
- **RLT (Red Light Therapy):** Weekly protocol reference with today's rotating zone. Nightly sequence: shower → Face 10m → Hips 20m → Rotating 10m → skincare/oils after.
- **Arm PT Reference:** Exercise guide and weekly consistency chart (M/W/F).
- **Timber Reassessment Flags:** Upcoming milestone reminders so schedule adjustments happen at the right time.

---

## 🤖 AI Features

| Feature | Where | Requires |
|---|---|---|
| 🚀 Replan with Gemini | Flow → tap block → bottom sheet | Gemini API key |
| ⚡ Capacity Scaler | Life tab → low battery | Gemini API key |
| ✨ Brain Dump Sort | Flow tab → Brain Dump card | Gemini API key |
| 🗂️ Today's Shape Suggest | Flow tab → Today's Shape card | Gemini API key |
| 🤖 Ask Claude | Flow → tap block → bottom sheet | None (claude.ai proxy) |

**Getting your Gemini key:** Go to [aistudio.google.com](https://aistudio.google.com) → Create API Key. Free tier is sufficient. Enter it in Stats → ⚙️.

---

## ☁️ Cloud Sync (GitHub Gist)

Timber memories, PT progress, battery logs, and connection logs sync to a private GitHub Gist — accessible from any device.

**What syncs:**
- Timber memories
- PT daily progress
- Battery/energy logs
- Connection logs

**What does NOT sync (per-device only):**
- Gemini API key
- GitHub token
- Google Calendar iCal URL
- Brain dump / scratch pad
- Today's Shape overrides
- Notification preferences
- Training cue statuses (localStorage only)

**Setup:**
1. Go to [github.com/settings/tokens/new](https://github.com/settings/tokens/new)
2. Name it anything, select **gist** scope only — nothing else
3. Tap the **Sync** dot in the header, paste your token, tap Connect

**On a new device:** open the HTML file → tap Sync dot → paste token → Connect. Everything pulls automatically.

**Token expiry:** The app warns you 14 days before a 90-day token expires. Your data is never lost — just reconnect with a new token.

---

## ⏰ Timers & Alarms

Timers inside the app use absolute end timestamps so they survive screen lock better than simple countdowns. However, **for Timber's potty and quiet-time alarms, use your phone's native alarm app** — native alarms fire reliably with sound even when the screen is off and the browser is closed. The OS is the visual map; your phone is the trigger.

**Timber's daily alarm schedule (set once, repeat daily) — 20-week revision:**

| Time | Alarm |
|---|---|
| 8:30 AM | 🐾 Timber wake + potty |
| 8:35 AM | 🎓 Vyvanse + breakfast training (downstairs) |
| 8:55 AM | 🦮 Morning walk |
| 10:05 AM | 🚽 Timber potty → frozen treat → Quiet Time #1 |
| 12:30 PM | 🐾 Timber Quiet Time #1 ends — wake + potty |
| 2:00 PM | 🚽 Timber potty → frozen treat → Quiet Time #2 |
| 4:15 PM | 🐾 Timber Quiet Time #2 ends — wake + potty |
| 5:00 PM | 🎓 Timber dinner training |
| 5:15 PM | 🦮 Afternoon walk — 30 min |
| 9:30 PM | 🚽 Timber evening potty (pick up water at 9:45) |
| 10:20 PM | 🌙 Timber bedtime potty → bedroom travel crate |
| 9:25 PM | 🔴 RLT session |
| 11:15 PM | 💊 Wind-down + meds |
| 11:30 PM | 🌙 Your bedtime |

*What changed at 20 weeks:* collapsed from 4 nap cycles to 2 quiet-time windows of 1.5–2 hrs each. Daytime crate naps replaced with free-roam quiet time in the gated office — frozen treat (Kong, licki mat, or calming mix) is the settle cue. Crate stays open all day; Timber self-selects his sleep spot (he prefers the fluffy dog bed). Overnight is 10:30 PM → 8:30 AM in the bedroom travel crate (~10 hrs). Office crate removed. Morning training happens downstairs before the walk, using his full breakfast as rewards.

**Upcoming milestones (Stats tab):**
- **June 30, 2026** — 6-month vet check + adolescence prep
- **September 1, 2026** — neuter assessment (toy breeds: 7–8 months)

---

## 🛠️ Technical Stack

| Component | Technology |
|---|---|
| Structure | HTML5 |
| Styling | CSS3 (custom properties, grid, flexbox, safe-area-insets) |
| Logic | Vanilla JavaScript (ES6+) |
| Charts | Chart.js |
| Typography | Google Fonts (Nunito) |
| AI (Gemini) | @google/genai via esm.run |
| Calendar | iCal feed via allorigins.win CORS proxy |
| Storage | Browser localStorage + GitHub Gist |

Single-file architecture. No build step, no dependencies to install, no server required.

---

## 🚀 Getting Started

1. **Open** `index.html` in Chrome or Safari
2. **Add to home screen** for a full-screen app experience (Share → Add to Home Screen on iOS; Install App on Chrome)
3. **Connect cloud sync** via the Sync dot in the header (optional but recommended)
4. **Add Gemini key** via Stats → ⚙️ (optional, unlocks AI features)
5. **Connect Google Calendar** via the Cal tab → paste your secret iCal URL

---

## 📱 Device Support

Tested and optimised for:
- Android phone (Chrome)
- Samsung tablet
- Windows laptop / Surface Pro (fullscreen desktop layout at ≥768px)
- iOS (Safari — Add to Home Screen for best experience)

---

## 🛡️ Privacy

- No data ever leaves your device except:
  - **GitHub Gist API** — your memories and logs, using your own token
  - **Google AI (Gemini API)** — your schedule context, using your own key
  - **Anthropic (Claude)** — only when using Ask Claude inside claude.ai
  - **allorigins.win** — your iCal URL passes through this CORS proxy to fetch calendar data. Your iCal URL contains a secret token — do not share it publicly.
- API keys are stored in `localStorage` only. Never in the HTML file, never synced.

---

<details>
<summary><b>🛠️ Maintenance & AI Collaboration Guide</b></summary>

## How to Make Changes

Your OS is a single HTML file. To update it:

1. **Open Cowork** and start a new session
2. **Describe what you want** in plain language — Claude has persistent memory of your OS structure and Timber's schedule history
3. Changes are applied directly to the file in your workspace folder

Your data is safe — it lives in localStorage and your Gist, not in the HTML file itself.

**Schedule reviews:** the app shows reassessment flags at the 6-month and neuter milestones. When prompted, say: *"It's time to reassess Timber's schedule — he is now N weeks old."*

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
| Today's Shape overrides | localStorage | ❌ Per device, midnight reset |
| Gemini API key | localStorage | ❌ Per device |
| GitHub token | localStorage | ❌ Per device |
| iCal URL | localStorage | ❌ Per device |
| Schedule & routine | Inside the HTML file | Edit the file to change |

---

## Troubleshooting

| Problem | Fix |
|---|---|
| White screen / blank app | JavaScript error. Describe the issue to Claude in Cowork. |
| Train tab shows 0 of 0 | Tap the Train tab to trigger a fresh render. |
| Gemini error | Invalid key → re-enter in Stats ⚙️. Rate limit (429) → check aistudio.google.com. |
| Sync dot is red | Token expired or offline. Tap dot → renew at github.com/settings/tokens/new. |
| Memories disappeared | If Gist connected: tap Sync to pull. If not: they were localStorage only. |
| Calendar not loading | Check your iCal URL in the Cal tab. May need to regenerate in Google Calendar settings. |
| Today's Shape missing calendar | Open the Cal tab first to let it load, then return to Flow. |
| Timers stop when screen locks | Expected behaviour in browser. Use phone native alarms for anything time-critical. |
| Wrong day in PT | Use the Day selector in the Move tab. |
| Override badges cleared | Overrides reset at midnight — this is intentional. Fresh start every day. |

---

## Re-orienting Claude Mid-Session

If Claude loses context, paste this:

> *"Quick context: this is a single-file HTML personal Life OS (index.html, ~6500+ lines). Timber is a miniature poodle born December 30, 2025 (currently ~20 weeks). Schedule: 2 quiet-time windows per day (10:30 AM–12:30 PM and 2:15–4:15 PM), each started with a frozen treat settle cue. Free-roam in gated office. Night crate is bedroom travel crate, 10:30 PM–8:30 AM. Morning training happens downstairs before the walk using breakfast kibble. There is a dedicated Train tab with 15 cues across 4 categories (cue / technique / conditioning / enrichment) with localStorage status persistence. Design is minimalist kawaii pastel: lilac+matcha day theme, deep-plum+moonlit-sage night theme, auto-switching by clock. Key CSS tokens: --la/--lm/--ll (lilac), --ma/--mm/--ml (sage), --pa/--pm/--pl (pink). Schedule data is const S=[...] array. Train data is const TRAIN_CUES=[...]. Features: Gemini AI replan, per-block override mode, Google Calendar iCal, GitHub Gist sync, RLT protocol tracker, PT tracker, battery/connection logging."*

</details>
