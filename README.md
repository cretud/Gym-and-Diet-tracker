# Health Tracker

A personal, local-first health dashboard for tracking workouts, nutrition, sleep, and daily activity — built as my own space to stay consistent on my journey to better health.

> **Local only.** Runs on your laptop. Your data stays yours.

---

## What It Does

Reset Tracker brings together workout data from **Hevy** with a simple manual journal for food, steps, sleep, and how you feel day-to-day — all in one clean dashboard.

### Core Features

| Module | What it tracks |
|---|---|
| Food Journal | Simple daily log — meals, rough protein notes, how you felt |
| Workout Log | Import recent workouts from Hevy CSV exports |
| Daily Health Log | Manually enter steps, sleep, energy, and notes for the day |
| Dashboard | Weekly overview — workouts hit, step averages, journal streak |

---

## Tech Stack

| Layer | Choice | Why |
|---|---|---|
| Frontend | React + Vite | Fast dev, component-driven |
| Styling | Tailwind CSS | Utility-first, easy to iterate |
| Backend | Python (FastAPI) | Lightweight local API |
| Database | SQLite | Zero config, single file, perfect for local use |
| Data Import | CSV parsing (Hevy export format) | |

---

## Project Structure

```
reset-tracker/
├── backend/
│   ├── main.py              # FastAPI app entry point
│   ├── database.py          # SQLite setup & connection
│   ├── models/              # DB models (workouts, food, health)
│   ├── routers/             # API routes per module
│   └── importers/           # CSV parser for Hevy
│
├── frontend/
│   ├── src/
│   │   ├── pages/           # Dashboard, Journal, Workouts, Health
│   │   ├── components/      # Shared UI components
│   │   └── api/             # Frontend API client
│   └── public/
│
├── data/
│   └── reset_tracker.db     # SQLite database (auto-created)
│
├── imports/                 # Drop your Hevy export CSV here
│   └── hevy/
│
└── README.md
```

---

## Getting Started

> Prerequisites: **Node.js 18+** and **Python 3.10+**

### 1. Clone the repo

```bash
git clone https://github.com/yourusername/reset-tracker.git
cd reset-tracker
```

### 2. Start the backend

```bash
cd backend
python -m venv venv
source venv/bin/activate        # Windows: venv\Scripts\activate
pip install -r requirements.txt
uvicorn main:app --reload
```

The API will run at `http://localhost:8000`.

### 3. Start the frontend

```bash
cd frontend
npm install
npm run dev
```

Open `http://localhost:5173` in your browser.

---

## Importing Your Data

### From Hevy

Hevy exports your full workout history as a single CSV. Rather than importing everything at once, the app lets you **choose how many recent workouts to import** — for example, the last 2 weeks or the last 10 sessions. This keeps the database clean and relevant.

1. Open Hevy → Profile → Export Workouts → **CSV**
2. Drop the file into `imports/hevy/`
3. Go to **Settings → Import** in the app
4. Select how far back you want to import (e.g. last 7 days, last 30 days, or a custom date range)
5. Click **Import** — already-imported workouts are skipped automatically

### Daily Health Log (Manual)

Steps and sleep are logged manually — just a quick daily check-in. No app integration needed.

Each day you can log:
- Steps
- Sleep (hours + quality)
- Energy level (1–5)
- Any notes

It takes under a minute and keeps things simple.

---

## Data & Privacy

- Everything runs locally on your machine
- The SQLite database lives in `/data/reset_tracker.db`
- Nothing is sent to any server
- To back up your data: just copy that `.db` file anywhere

---

## Roadmap

- [x] Project setup & database schema
- [ ] Food journal (add/edit/delete meals)
- [ ] Hevy CSV importer with selective date range
- [ ] Daily health log (steps, sleep, energy)
- [ ] Dashboard with weekly summary
- [ ] Workout history & basic progress charts
- [ ] Step & sleep trend views
- [ ] Dark/light mode toggle

---


