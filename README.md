# CC Progression App

A mobile-first Progressive Web App for Convict Conditioning-style progression tracking.

> "What should I do today, and am I ready to progress?"

---

## Features

- **Today** — Log sets, track pain per exercise, finish workflow
- **Progress** — Phase readiness dashboard with progress bars + trend charts
- **Phases** — Visual roadmap with exit criteria checklist
- **Body** — Daily pain check-in with 3-day warning logic
- **Progression Engine** — Auto-suggests level advancement when criteria are met
- **Offline capable** — Works after first load via service worker
- **PWA installable** — Add to iPhone Home Screen via Safari

---

## Run Locally

No build step required. Just serve the files:

```bash
# Option 1: Python
cd cc-app
python3 -m http.server 8080
# Open http://localhost:8080

# Option 2: Node
npx serve .

# Option 3: VS Code Live Server
# Open folder in VS Code, click "Go Live"
```

---

## Deploy to GitHub Pages

### Step 1 — Create a GitHub repo

```bash
git init
git add .
git commit -m "Initial commit: CC Progression App"
```

### Step 2 — Push to GitHub

```bash
# Create a new repo on github.com, then:
git remote add origin https://github.com/YOUR_USERNAME/cc-app.git
git branch -M main
git push -u origin main
```

### Step 3 — Enable GitHub Pages

1. Go to your repo on GitHub
2. Settings → Pages
3. Source: **Deploy from a branch**
4. Branch: **main**, folder: **/ (root)**
5. Click Save

Your app will be live at:
`https://YOUR_USERNAME.github.io/cc-app/`

> **Note:** GitHub Pages serves from a subdirectory. The app uses relative paths (`./`) which work correctly in subdirectory deployments.

---

## Install on iPhone (iOS 17+)

1. Open Safari on your iPhone
2. Navigate to your GitHub Pages URL
3. Tap the **Share** button (box with arrow)
4. Scroll down → tap **"Add to Home Screen"**
5. Name it **CC PRO** → tap **Add**

The app will open in full-screen standalone mode (no browser UI).

---

## Data Storage

All data is stored in `localStorage` — no server, no account required.
- Sessions, pain history, progress metrics all persist on your device
- Export feature not included in v1 (browser dev tools → Application → Local Storage to backup manually)

---

## Progression Logic

### Push Level Advancement
- Total reps ≥ 45 across sets
- Last set ≥ 75% of first set
- Session shoulder pain ≤ 2
→ App suggests lowering rings (advancing level)

### Phase 1 → Phase 2
- Push level ≥ 5 (Near Floor)
- Pullups ≥ 8
- Hollow Hold ≥ 30s
- Ring Support Hold ≥ 45s  
- Pistols/leg ≥ 5
- Avg shoulder pain ≤ 2
- Avg low back pain ≤ 2

---

## Future Improvements (v2+)

- **Ring Height Visual Ladder** — graphic showing ring position
- **Auto Day Scheduling** — rest day detection, A/B rotation warnings
- **Session Streaks** — weekly consistency dots
- **Export/Import** — JSON backup of localStorage data
- **Apple Watch Integration** — rest timer + quick set logging
- **Form Cue Videos** — embedded short clips per exercise level
- **Warmup Protocol** — pre-workout checklist screen
- **Body Weight Tracking** — optional, for relative strength ratio

---

## Tech Stack

- Vanilla JS (no framework, no build step)
- CSS custom properties for theming
- localStorage for persistence
- Service Worker for offline/PWA
- Google Fonts: Barlow Condensed + JetBrains Mono
