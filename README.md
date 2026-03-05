# ✿ Life OS — The Capacity Engine

A custom-built, single-file responsive web dashboard designed to reduce cognitive overhead for people managing ADHD and hypermobility. The philosophy is simple: by handling the mechanics of remembering health protocols, puppy care schedules, and daily routines, the app frees up mental bandwidth for the people and things that matter most.

---

## ✨ Core Features

### 🐾 Flow — Daily Schedule (ADHD Safety Net)
A dynamic timeline that grounds you in the present without overwhelming you.
- **Timber-integrated schedule:** Every potty trip, crate nap, training session, and tethering window is built into the timeline alongside your work blocks, meals, and wellness routines.
- **Consistent alarm reference:** Each block reflects the exact alarm you have set on your phone — the app is the visual map, your phone is the trigger.
- **"Where Am I?" Anchor:** Tap any schedule block to set your current position. The app calculates how far ahead or behind schedule you are and lets you shift the remaining day forward.
- **Today's Shape — Override Mode:** A collapsible card at the top of Flow. Auto-pulls today's calendar events, accepts a freetext context note, and uses Gemini to suggest which blocks to compress, skip, or move. Suggestions appear with one-tap Apply buttons.
- **Per-block overrides:** Tap any block → bottom sheet → ⏩ Compress · ✗ Skip · ↕ Move later · ↺ Clear. Colour-coded badges show on each block. Resets automatically at midnight.
- **48-Hour Horizon:** Collapsible Tomorrow preview at the top of Flow.
- **Contextual Filtering:** Toggle between All / 🐾 Timber / 💻 Work / 🌿 Wellness.
- **🎯 Now Button + ↑ Top Button:** Floating buttons to jump to your current moment or back to the top.
- **AI Replan:** 🚀 Replan with Gemini and 🤖 Ask Claude, both in the bottom sheet.
- **Day-specific blocks:** Wednesday and Thursday pre-meeting potty trips only appear on the correct days automatically.

### 💭 Brain Dump
A zero-friction thought capture area on the Flow tab.
- Type anything — how you're feeling, Timber moments, things to remember, random thoughts.
- Tap **✨ Sort this** and Gemini categorises your notes into chips with suggested actions.
- Clears automatically at midnight.

### 🐶 Timber — Puppy Care
- **Schedule:** Crate nap cycles, potty trips, training sessions, and tethering windows are woven into the Flow timeline and visible in the Timber filter.
- **Memories log:** Milestone and memory tracking categorised by Social, Home Life, Health, Training. Quick-add preset buttons, editable timestamps.
- **PT tracker:** Daily exercise completion tracker with a weekly consistency chart.
- All Timber data syncs to GitHub Gist for cross-device access.

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
- **Arm PT Reference:** Exercise guide and weekly consistency chart.
- **Germany Countdown → Timber Schedule Reminder:** Three-state module:
  - **Pre-trip:** Live countdown to March 28 departure with rotating German phrases and Wanderlog link.
  - **In Germany (March 28 – April 11):** Shows days until you're back. Timber is with the sitter.
  - **Home (April 11+):** Flips into a 🐾 reminder to rebuild Timber's schedule — he'll be 14–15 weeks old and ready for an updated routine.

### 🧹 Sweepy — Daily Clean
A daily 10-minute Sweepy task is built into the 9:00 AM block right after Timber's first crate nap begins. Keeps accident spots managed at the start of every work day.

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

**Setup:**
1. Go to [github.com/settings/tokens/new](https://github.com/settings/tokens/new)
2. Name it anything, select **gist** scope only — nothing else
3. Tap the **Sync** dot in the header, paste your token, tap Connect

**On a new device:** open the HTML file → tap Sync dot → paste token → Connect. Everything pulls automatically.

**Token expiry:** The app warns you 14 days before a 90-day token expires. Your data is never lost — just reconnect with a new token.

---

## ⏰ Timers & Alarms

Timers inside the app use absolute end timestamps so they survive screen lock better than simple countdowns. However, **for Timber's potty and crate alarms, use your phone's native alarm app** — native alarms fire reliably with sound even when the screen is off and the browser is closed. The OS is the visual map; your phone is the trigger.

**Timber's daily alarm schedule (set once, repeat daily):**

| Time | Alarm |
|---|---|
| 4:00 AM | 🐾 Timber potty → back to crate |
| 8:00 AM | 🐾 Timber wake + potty #1 |
| 8:15 AM | 🐾 Timber breakfast training session |
| 8:50 AM | 🐾 Timber potty #2 → crate nap |
| 9:00 AM | 🧹 Sweepy daily clean |
| 10:30 AM | 🐾 Timber wake + potty #3 |
| 11:00 AM | 🐾 Timber potty #4 |
| 12:00 PM | 🐾 Timber potty #5 → crate nap · Lunch · Iron |
| 1:30 PM | 🐾 Timber wake + potty #6 |
| 2:00 PM | 🐾 Timber potty #7 |
| 3:00 PM | 🐾 Timber potty #8 → crate nap |
| 4:30 PM | 🐾 Timber wake + potty #9 |
| 5:00 PM | 🐾 Timber potty #10 |
| 5:30 PM | 🐾 Timber dinner training session |
| 5:50 PM | 🐾 Timber potty #11 → crate nap |
| 7:30 PM | 🐾 Timber wake + potty #12 |
| 9:00 PM | 🐾 Timber potty #13 → crate nap · Your shower |
| 9:20 PM | 🔴 RLT session |
| 10:00 PM | 💜 Lotion + oils → office |
| 11:00 PM | 🐾 Timber wake + potty #14 |
| 11:30 PM | 🐾 Timber potty #15 → crate for night · Your bed |
| 1:00 AM | 🐾 Timber potty — **partner's alarm, set on his phone** |

*This schedule will reduce significantly as Timber matures. The 1:00 AM trip drops first, then the 4:00 AM, then daytime gaps widen. Reassess fully on April 11 when you return from Germany.*

---

## 🛠️ Technical Stack

| Component | Technology |
|---|---|
| Structure | HTML5 |
| Styling | CSS3 (custom properties, grid, flexbox, safe-area-insets) |
| Logic | Vanilla JavaScript (ES6+) |
| Charts | Chart.js |
| Typography | Google Fonts (Nunito) |
| AI (Gemini) | @google/generative-ai via esm.run |
| Calendar | iCal feed via allorigins.win CORS proxy |
| Storage | Browser localStorage + GitHub Gist |

Single-file architecture. No build step, no dependencies to install, no server required.

---

## 🚀 Getting Started

1. **Open** `jasmines-life-os.html` in Chrome or Safari
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

1. **Start a new Claude chat** at claude.ai
2. **Upload your current `jasmines-life-os.html`** file
3. **Describe what you want** in plain language
4. **Download the returned file** and replace your old one

Your data is safe — it lives in localStorage and your Gist, not in the HTML file itself.

**When you return from Germany on April 11:** The app will remind you automatically. The instruction is: open a new Claude chat, upload your OS file, and say: *"It's time to rebuild Timber's schedule — he is now 15 weeks old."*

---

## What Lives Where

| Data | Location | Syncs |
|---|---|---|
| Timber memories | localStorage + GitHub Gist | ✅ Cross-device |
| PT progress | localStorage + GitHub Gist | ✅ Cross-device |
| Battery log | localStorage + GitHub Gist | ✅ Cross-device |
| Connection log | localStorage + GitHub Gist | ✅ Cross-device |
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
| White screen / blank app | JavaScript error. Give the file to Claude: *"This file has a syntax error — fix it and return the working file."* |
| Gemini error | Invalid key → re-enter in Stats ⚙️. Rate limit (429) → check aistudio.google.com. |
| Sync dot is red | Token expired or offline. Tap dot → renew at github.com/settings/tokens/new. |
| Memories disappeared | If Gist connected: tap Sync to pull. If not: they were localStorage only. |
| Calendar not loading | Check your iCal URL in the Cal tab. May need to regenerate in Google Calendar settings. |
| Today's Shape missing calendar | Open the Cal tab first to let it load, then return to Flow. |
| Notifications not firing | Allow notifications in browser settings. Use phone native alarms for Timber's schedule. |
| Timers stop when screen locks | Expected behaviour in browser. Use phone native alarms for anything time-critical. |
| Wrong day in PT | Use the Day selector in the Move tab. |
| Override badges cleared | Overrides reset at midnight — this is intentional. Fresh start every day. |
| Sync not working on new device | Open file → tap Sync dot → paste your GitHub token → Connect. iCal URL and Gemini key must be re-entered per device. |

---

## Re-orienting Claude Mid-Session

If Claude loses context, paste this:

> *"Quick context: this is a single-file HTML personal Life OS. It includes a Timber puppy schedule (9-week-old miniature poodle, crate training, Learn to Earn, Sophia Yin protocol), a daily schedule with AI replan and per-block override mode, PT tracker, battery/connection tracking, Google Calendar iCal integration, and Gemini + Claude AI integration. The design is minimalist kawaii pastel. The goal is reducing cognitive overhead, not productivity. Please keep changes minimal and targeted."*

</details>
