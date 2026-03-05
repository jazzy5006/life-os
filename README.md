# ✿ Life OS — The Capacity Engine

A custom-built, single-file responsive web dashboard designed to reduce cognitive overhead for people managing ADHD and hypermobility. The philosophy is simple: by handling the mechanics of remembering health protocols, care schedules, and daily routines, the app frees up mental bandwidth for the people and things that matter most.

---

## ✨ Core Features

### 💜 Connection Heartbeat
A relationship tracking system built around "soft goals."
- **Connection Orbits:** Visual rings showing how recently you've connected with the people closest to you. Rings shift from warm green → cool blue → amber → soft red as time passes.
- **Gentle Nudges:** Low-friction reminders when someone hasn't been reached out to in a while. No alarms — just a quiet prompt.
- **Connection Log:** One tap to log a call, text, quality time, or meaningful moment. Includes a note field and recent history.

### 🔋 Energy & Capacity System
Treats your daily energy as a finite, precious resource.
- **Battery Logger:** Tap one of five emoji levels each day to log how you're feeling. Displayed as a 7-day visual arc.
- **Capacity Scaler:** When battery is low (😔 or 🪫), a Gemini-powered suggestion button appears — tap it to get warm, specific suggestions for what to compress or skip to protect your emotional bandwidth.
- **Movement Engine:** PT exercise tracker with automatic day-based rotation (e.g. floor exercises M/W/F, standing T/Th/Sat). Tap to check off, auto-saves, resets daily.

### 📅 Flow — ADHD Safety Net
A dynamic timeline that grounds you in the present without overwhelming you.
- **"Where Am I?" Anchor:** Tap any schedule block to set your current position. The app calculates your offset and lets you shift the remaining schedule forward to match reality.
- **48-Hour Horizon:** A collapsible "Tomorrow" preview at the top of the Flow tab, showing tomorrow's key blocks without cluttering today.
- **Contextual Filtering:** Toggle between All / 🐾 Puppy / 💻 Work / 🌿 Wellness to reduce noise.
- **🎯 Now Button:** Floating button that scrolls to your current moment in the timeline.
- **AI Replan:** Two AI options in the bottom sheet — 🚀 Replan with Gemini (uses your Gemini API key) and 🤖 Ask Claude (uses built-in Claude proxy when running inside claude.ai).

### 💭 Brain Dump
A zero-friction thought capture area at the top of the Flow tab.
- Type anything — how you're feeling, things to remember, Timber moments, random thoughts.
- Tap **✨ Sort this** and Gemini automatically categorises your notes into Puppy / Health / Connection / Work chips with suggested actions.
- Clears automatically at midnight so it never accumulates.

### 🐶 Timber's Memories
A milestone and memory log for your puppy.
- Categorised entries: Social, Home Life, Health, Training.
- Quick-add preset buttons for common firsts (stroller trip, cat introduction, first sit, etc.).
- Editable timestamps — log past events accurately.
- Syncs to GitHub Gist for backup and cross-device access.

### 📊 Stats & Health Protocols
- **RLT (Red Light Therapy):** Weekly protocol reference with today's zone.
- **Iron Dosing:** Timing guide with buffer reminders.
- **Arm PT Reference:** Exercise guide and weekly consistency chart.
- **Germany Countdown:** Days/hours/minutes to trip departure with a rotating German phrase-of-the-day including pronunciation.

### 🇩🇪 Germany Trip Prep
- Live countdown to departure date.
- Daily rotating German phrases with phonetic pronunciation guide.
- Wanderlog itinerary link.

---

## 🤖 AI Features

| Feature | Where | Requires |
|---|---|---|
| 🚀 Replan with Gemini | Flow → tap block → bottom sheet | Gemini API key |
| ⚡ Capacity Scaler | Life tab → low battery | Gemini API key |
| ✨ Brain Dump Sort | Flow tab → Brain Dump card | Gemini API key |
| 🤖 Ask Claude | Flow → tap block → bottom sheet | None (claude.ai proxy) |

**Getting your Gemini key:** Go to [aistudio.google.com](https://aistudio.google.com) → Create API Key. Free tier is sufficient for daily use. Enter it in Stats → ⚙️.

---

## ☁️ Cloud Sync (GitHub Gist)

Timber memories, battery logs, and connection logs sync to a private GitHub Gist.

**Setup:**
1. Go to [github.com/settings/tokens/new](https://github.com/settings/tokens/new)
2. Name it anything, select **gist** scope only — nothing else
3. Tap the **Sync** dot in the header, paste your token, tap Connect

**Token expiry:** If you created a 90-day token, the app warns you 14 days before expiry with a toast and a red banner in the Sync modal. Your data is never lost when a token expires — just reconnect with a new one.

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
| Storage | Browser localStorage + GitHub Gist |

Single-file architecture. No build step, no dependencies to install, no server required.

---

## 🚀 Getting Started

1. **Open** `jasmines-life-os.html` in Chrome or Safari
2. **Add to home screen** for a full-screen app experience (Share → Add to Home Screen on iOS; Install App on Chrome)
3. **Connect cloud sync** via the Sync dot in the header (optional but recommended)
4. **Add Gemini key** via Stats → ⚙️ (optional, unlocks AI features)

---

## 📱 Device Support

Tested and optimised for:
- Android phone (Chrome)
- Samsung tablet
- Windows laptop / Surface Pro (fullscreen desktop layout at ≥768px)

---

## 🗺️ Roadmap

- [ ] Google Calendar integration (iCal feed or OAuth)
- [ ] F1 trip countdown and logistics tracker
- [ ] Red Light Therapy dedicated session timer with sound completion
- [ ] Hobonichi-style habit log

---

## 🛡️ Privacy

- No data ever leaves your device except:
  - **GitHub Gist API** — your memories/logs, using your own token
  - **Google AI (Gemini API)** — your schedule context, using your own key
  - **Anthropic (Claude)** — only when using Ask Claude inside claude.ai
- API keys are stored in `localStorage` only. They are never in the HTML file and never synced.

---

<details>
<summary><b>🛠️ Maintenance & AI Collaboration Guide</b></summary>

## How to Make Changes

Your OS is a single HTML file. To update it:

1. **Start a new Claude chat** at claude.ai
2. **Upload your current `jasmines-life-os.html`** file
3. **Describe what you want** using this format:

```
WHAT I WANT: [describe the change]
WHERE: [which tab — Flow, Move, Stats, Life, or Timber]
HOW IT SHOULD WORK: [describe the behaviour]
DESIGN: Keep the minimalist kawaii pastel aesthetic.
```

4. **Download the returned file** and replace your old one. Your data is safe — it lives in localStorage and your Gist, not in the HTML file.

---

## What Lives Where

| Data | Location | Notes |
|---|---|---|
| Timber memories | localStorage + GitHub Gist | Syncs across devices |
| PT progress | localStorage | Per device, resets daily |
| Brain dump notes | localStorage | Auto-clears at midnight |
| Gemini API key | localStorage | Per device, never synced |
| GitHub token | localStorage | Per device, never synced |
| Schedule & routine | Inside the HTML file | Edit the file to change |
| Connection log | localStorage + GitHub Gist | Syncs across devices |
| Battery log | localStorage + GitHub Gist | Syncs across devices |

---

## Troubleshooting

| Problem | Fix |
|---|---|
| White screen / blank app | JavaScript error. Give the file to Claude and say: *"This file has a syntax error — fix it and return the working file."* |
| Gemini error in panel | Invalid key → re-enter in Stats ⚙️. Rate limit (429) → visit aistudio.google.com and verify billing identity. |
| Sync dot is red | Token expired or internet issue. Tap dot → renew token at github.com/settings/tokens/new |
| Memories disappeared | If Gist connected: tap Sync to pull. If not: they were localStorage only (may have been cleared by browser). |
| Notifications not firing | Allow notifications in browser settings. Tap the 🔔 bell and accept the permission prompt. |
| Timers not appearing | Tap the specific timer button inside the block, not the block header. |
| Wrong day in PT | Use the Day selector dropdown in the Move tab. |
| Desktop sync/gear not visible | The header shows sync dot, 🔔 bell, and ⚙️ on all screen sizes. Hard refresh (Ctrl+Shift+R) if stale. |

---

## Re-orienting an AI Mid-Session

If Claude or Gemini loses context, paste this:

> *"Quick context: this is a single-file HTML personal Life OS. It includes a daily schedule with AI replan, PT tracker, Timber's puppy memories, battery/connection tracking, and Gemini + Claude AI integration. The design is minimalist kawaii pastel. The goal is reducing cognitive overhead, not productivity. Please keep changes minimal and targeted."*

</details>
