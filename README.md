# 🧠 MindGuard – Your Screen Buddy

> A smart, AI-powered screen time manager designed to help children and teens build healthier digital habits — with parental controls powered by face recognition.

---

## 📸 Overview

**MindGuard** is a single-file web application (no backend required) that runs entirely in the browser. It helps families manage screen time with gamification, mental wellness tools, and a biometric lock system — all in a beautiful dark-themed UI.

---

## ✨ Features

### 📊 Dashboard
- Real-time screen time tracking with daily limit progress bar
- XP-based reward system and avatar mood indicator
- Quick stats: session time, locks triggered, focus score, streak days

### 📱 Apps Monitor
- Track opens and time spent per app (Instagram, YouTube, TikTok, etc.)
- Simulated app interface with mindful usage prompts

### 📈 Analytics
- Daily usage bar charts across apps
- Focus score ring chart
- Weekly summary stats

### 🧘 Mental Health Tools
- Guided breathing exercise (animated bubble)
- Mood check-in with emoji selector
- Quick-access wellness cards: Anxiety Help, Sleep Tips, Focus Boost

### 👨‍👩‍👧 Parental / Guardian Controls
- **Face Registration** – Register a parent face using the webcam via face-api.js
- **Face Unlock** – Screen locks and can only be unlocked by the registered face
- **PIN Fallback** – Optional 4-digit PIN as backup unlock method
- **Lock Stats** – Track lock count, unlock attempts, and current status
- **Alert History** – Live log of all app events and lock triggers

### 🔔 Notifications
- Browser push notifications at 50%, 80%, and 100% of daily limit
- Beep alerts on lock/unlock events

---

## 🛠️ Tech Stack

| Technology | Purpose |
|---|---|
| HTML5 / CSS3 / Vanilla JS | Core app — no frameworks needed |
| [face-api.js](https://github.com/justadudewhohacks/face-api.js) | AI face detection & recognition |
| Google Fonts (Nunito, Space Grotesk, Space Mono) | Typography |
| Font Awesome 6 | Icons |
| localStorage | Persistent state (settings, face descriptor, usage data) |
| Web Notifications API | Browser push alerts |
| Web Audio API | Beep sounds on lock events |
| MediaDevices API | Webcam access for face registration/verification |

---

## 🚀 Getting Started

### Option 1 — Open Locally (Simplest)

```bash
# Just open the file in your browser
open index.html
```

> ⚠️ Face recognition requires webcam access. Use Chrome or Edge for best results.

---

### Option 2 — Deploy on GitHub Pages (Free Hosting)

1. **Create a GitHub account** at [github.com](https://github.com)
2. **Create a new public repository** (e.g., `mindguard`)
3. **Upload `index.html`** via the GitHub UI (Add file → Upload files)
4. Go to **Settings → Pages → Source: main branch / root**
5. Your app goes live at:

```
https://your-username.github.io/mindguard/
```

---

### Option 3 — Serve Locally with a Dev Server

```bash
# Using Python
python -m http.server 8080

# Using Node.js (npx)
npx serve .

# Then open
http://localhost:8080
```

---

## 📁 Project Structure

```
mindguard/
│
├── index.html          # Entire app in a single file (HTML + CSS + JS)
└── README.md           # This file
```

> The entire app is self-contained in `index.html`. No build step, no dependencies to install.

---

## ⚙️ Configuration

All settings are saved in the browser's `localStorage` automatically. No server or database needed.

| Setting | Default | Description |
|---|---|---|
| Daily Screen Limit | 60 min | Adjustable via slider on dashboard |
| Parent PIN | None | Set in Guardian Controls tab |
| Face Descriptor | None | Registered via webcam in Guardian Controls |
| XP / Streak | 0 | Auto-tracked from usage |

---

## 🔒 How the Face Lock Works

```
1. Parent registers their face via webcam (Guardian tab)
   └─ Face descriptor saved to localStorage (encrypted Float32Array)

2. When screen time limit is hit → Lock overlay appears

3. Child cannot dismiss the overlay

4. Parent scans their face via webcam to unlock
   └─ face-api.js compares live face to stored descriptor
   └─ Distance threshold < 0.55 = match → unlocked ✅

5. Fallback: PIN entry if face scan fails
```

---

## 🌐 Browser Compatibility

| Browser | Support |
|---|---|
| Chrome 90+ | ✅ Full support |
| Edge 90+ | ✅ Full support |
| Firefox | ⚠️ Camera may need permission |
| Safari | ⚠️ Limited Web Audio / Notification support |
| Mobile Chrome | ✅ Supported (responsive layout) |

---

## ⚠️ Known Limitations

- Face recognition requires an active internet connection to load AI model weights from CDN
- This is a **frontend-only prototype** — no real app blocking capability on the OS level
- All data is stored locally in the browser; clearing browser data resets the app
- Face AI models (`TinyFaceDetector`) load from `justadudewhohacks.github.io` CDN

---

## 🤝 Contributing

Pull requests are welcome! For major changes, please open an issue first.

```bash
git clone https://github.com/your-username/mindguard.git
cd mindguard
# Make your changes to index.html
git add .
git commit -m "feat: your feature description"
git push origin main
```

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

---

## 💡 Inspiration

MindGuard was built to address the growing concern of excessive screen time among children and teenagers, combining AI biometrics with gamification to make digital wellness engaging rather than restrictive.

---
