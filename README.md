# PitWall

A real-time telemetry HUD and session coaching overlay for **Assetto Corsa**, built as a native Python app using the AC SDK.

Two modes in one panel: a compact live dashboard while you drive, and a full session analysis view between laps.

---

## Features

### Live Mode (340×240)

| Display | Detail |
|---------|--------|
| Lap timer | Current lap time with millisecond precision |
| Delta | Real-time gap vs. personal best — green/red color-coded |
| Speed | Current speed vs. optimal reference with +/− indicator |
| Corner | Name, type (Hairpin / Slow / Medium / Fast), and phase (Entry / Apex / Exit) |
| Corner score | 0–10 rating vs. your best lap's apex speed, with color-coded bar |
| Pedals | Live throttle and brake bars |
| Tires | Temperature status: COLD / Warming / Optimal / HOT / F.Hot / R.Hot |
| Advice | Contextual tips — upcoming corner previews, speed corrections, tire warnings |

### Coach Mode (380×520)

| Section | Detail |
|---------|--------|
| Session summary | Lap count, best time, average time, consistency % |
| Corner analysis | Per-corner score table with visual bars (up to 8 corners) |
| Braking consistency | Brake point standard deviation per corner: Excellent / Good / Inconsistent |
| Improvements | Flags worst-scoring corners and inconsistent brake markers |
| Session report | Exports a full HTML report to `reports/` |

### Data Persistence

- Optimal lap telemetry (speed + normalized position) saved as JSON per car/track combo
- Auto-loaded on next session — delta math uses your actual recorded best, not an estimate
- Corner detection runs automatically from the speed profile of your first optimal lap — no per-track configuration needed

---

## Installation

PitWall runs as a Python app inside Assetto Corsa.

**1.** Create the app folder and copy the script:

```
...\SteamApps\common\assettocorsa\apps\python\PitWall\PitWall.py
```

**2.** Launch Assetto Corsa → **Options → General → UI Modules** → enable **PitWall**.

**3.** Start a session. The panel appears in the app tray on the right side of the screen.

---

## Usage

- The panel opens in **Live mode** by default.
- Click **📊 Coach** to switch to the full session analysis view.
- Click **🏎 Live** to switch back.
- In Coach mode, click **📄 Generate Report** to export an HTML session report.

The HUD automatically detects your car and track on session start and loads any existing PB data for that combination. Drive a full clean lap to populate baseline telemetry if none exists.

---

## Requirements

- Assetto Corsa (Steam)
- No external dependencies — uses only the AC SDK (`ac`, `acsys`) and Python standard library

---

## Compatibility

Built and tested on **PitWall v3.1**. Compatible with all cars and tracks in Assetto Corsa.

---

## License

MIT