# 🌸 Jasmine’s Life OS: The Capacity Engine

Welcome to your digital cognitive prosthetic. This **Life OS** is a custom-built, responsive web dashboard designed to pay the "ADHD tax" automatically. It shifts the focus away from sheer productivity and instead protects your emotional bandwidth and physical capacity. 

By handling the mechanics of remembering the details of clinical trials, puppy training protocols, and hypermobility management, this system ensures you remain present and emotionally available for Nathan, Mom, Sister, and Timber.

## ✨ Core Features

### 💜 The Connection Heartbeat
A dedicated system to track the "soft goals" that matter most. 
* **Connection Orbits:** Visualizes recent touch-bases with Mom, Sister, and Nathan.
* **Gentle Nudges:** Low-friction reminders to reach out if too many days have passed, ensuring nobody falls off the radar.

### 🔋 Capacity Scaler & PT Engine
A high-performance health tracker that treats your energy as a finite, precious resource.
* **Smart PT Scheduling:** Automatically rotates hypermobility exercises (e.g., Floor exercises on M/W/F, Standing on T/Th/Sat).
* **The Battery Logger:** Tracks your daily internal battery and pain levels. 
* **Ruthless Compression:** If your battery is running on empty, the AI proactively suggests ways to compress or skip non-essential chores to protect your sleep and relationships.

### 📅 The ADHD Safety Net & Master Flow
A dynamic timeline that grounds you in the present while keeping an eye on the future.
* **48-Hour Horizon:** A minimalist "Tomorrow Peek" feature prevents time-blindness by showing upcoming "Big Rocks" without cluttering today's view.
* **Contextual Filtering:** Toggle between **Work**, **Timber**, and **Wellness** to eliminate overwhelming noise.
* **"Now" Pulse:** A real-time indicator that anchors your current task.

### 🧪 Lab Synthesis (Scratchpad)
A zero-friction brain dump area. Paste your messy thoughts, and the AI will automatically parse and categorize them into actionable *Work*, *Puppy*, *Health*, or *Connection* logs.

### 🌙 Adaptive Kawaii Aesthetic
* **Pastel Palette:** Features "Sophia Yin" lavender, "Timber" mint, and "Medical" peach.
* **Circadian Protection:** Automatically shifts to a deep, low-eye-strain night mode between **8:00 PM and 6:00 AM**.

---

## 🛠️ Technical Stack

| Component | Tech Used |
| --- | --- |
| **Structure** | HTML5 (Semantic & Accessible) |
| **Styling** | CSS3 (Variables, Grid, Flexbox, Safe-area-insets) |
| **Logic** | Vanilla JavaScript (ES6+) |
| **Charts** | Chart.js |
| **Typography**| Google Fonts (Nunito) |
| **Storage** | Browser LocalStorage + GitHub Gist Cloud Sync |

---

## 🚀 How to Use

1. **Launch:** Open the `jasmines-life-os.html` file in any modern browser (Chrome or Safari recommended for mobile).
2. **Reset Today:** Use the **☀️ Reset** button every morning to clear your PT checkboxes and start fresh.
3. **Save as App:** For the best experience, save the file as a "Web App" to your home screen to hide the browser UI.

---

## 🗺️ Future Roadmap

* [ ] **F1 Mexico City Tracker:** A countdown timer and logistics checklist for the October trip.
* [ ] **Hobonichi API:** (Conceptual) A way to sync "My 100" movies or habit logs.
* [ ] **Red Light Therapy Timer:** A dedicated 15/20-minute countdown with completion sounds.

---

<details>
<summary><b>🛠️ Click to view the Maintenance & AI Collaboration Guide</b></summary>

## ✿ Jasmine's Life OS System Manual
*Everything you need to update, extend, and maintain your OS.*

> **💜 Keep this document alongside your `jasmines-life-os.html` file. When you want to make changes, hand both this doc and the HTML file to any AI assistant and they will have everything they need.**

### 1. What Your Life OS Is
Your OS is a single HTML file that you open in any web browser. It has no server, no account, and no internet dependency (except for the AI features and GitHub sync). Everything runs locally on your device.

> **🗂 File location:** Save it somewhere you will always find it — iCloud Drive, Google Drive, or your Desktop. The file IS the app. If you lose the file, you lose the app (but not your data if Gist sync is connected).

**What is stored where:**
| Data | Stored in | Notes |
| :--- | :--- | :--- |
| **Timber memories** | localStorage + GitHub Gist | Syncs across devices via Gist |
| **PT progress** | localStorage | Per device, resets daily |
| **Today's scratch notes** | localStorage | Auto-clears next day |
| **Gemini API key** | localStorage | Per device, never shared |
| **GitHub Gist token** | localStorage | Per device, never shared |
| **Schedule & routine** | Inside the HTML file | Edit the file to change |

### 2. How to Ask an AI to Make Changes
When you want to update your OS, you will be giving the HTML file to an AI (Claude, Gemini, etc.) along with a description of what you want. 

**The 3-part prompt formula:**
1. **Give them the file:** Upload `jasmines-life-os.html`.
2. **Give them the context:** Explain the goal (e.g., "I need a new button for tracking water intake").
3. **Give them the constraint:** "DO NOT CHANGE THE CODE EVER AGAIN UNLESS I EXPLICITLY ASK YOU TO" applies to casual chats, but when you *do* want code, ask them to return the *entire* updated HTML file so you can simply copy and paste over your old one.

### 3. Troubleshooting
| Problem | Fix |
| :--- | :--- |
| **App is blank / white screen** | JavaScript syntax error. Give the file to an AI and say: *"This HTML file has a syntax error — fix it and return a working file."* |
| **Gemini returns an error** | Check the message in the blue panel. Invalid key → re-enter in Stats ⚙️. Rate limit (429) → visit aistudio.google.com and verify billing identity. |
| **Sync dot is red** | Token expired (if it's been 90 days) or internet issue. Tap Sync → follow the renewal steps. |
| **Memories disappeared** | If Gist sync is connected, tap Sync → the pull will restore them. If not connected, they were only in localStorage which may have been cleared. |
| **Notifications not firing** | You need to allow notifications in your browser. Tap the bell icon and accept the permission prompt. |
| **Timers not working** | Make sure you are tapping the peach launch buttons inside the block, not the block title itself. |
| **Wrong day showing in PT** | Use the Day selector dropdown in the Movement tab to set the correct day. |

*Made with love for Jasmine.*
</details>
