# 🌱 GreenRouter

**An energy-aware routing skill for Claude.**

Every AI task is routed to the model with the **lowest environmental cost** (energy × PUE × grid carbon intensity) that still meets your quality & latency requirements — and every task ends with a 🌍 planetary-contribution summary.

## Why GreenRouter?

Not every task needs the biggest model. Running everything on the heaviest model wastes energy, money, and grid capacity. GreenRouter makes the **environmental cost** a first-class citizen in model selection:

- **Picks the greenest viable model** for each task — not the cheapest, not the most powerful.
- **Respects hard constraints** on quality (min accuracy) and latency (max seconds).
- **Accounts for datacenter cooling** via PUE and **grid carbon intensity**.
- **Reports impact per task** and a **running session average** — you see exactly what you saved.

> Typical savings: **30–60 % fewer gCO₂e per task** vs always using the largest model.

## ✨ Features

| | |
|---|---|
| 🌱 **Energy-aware routing** | Picks the lowest-cost model that meets your constraints |
| 🌍 **Planetary footer** | Per-task emissions, session average, total, and savings vs baseline |
| ⚖️ **Tunable weights** | Prioritize energy, quality, or balance them |
| 📊 **Session ledger** | `show ledger` / `reset ledger` commands |
| 🌐 **Bilingual** | Full English and Portuguese support |

## 📦 Install

1. Open [`SKILL.md`](SKILL.md) and copy its full content.
2. Paste it into a Claude conversation (app, web, or Claude Code).
3. Send one of these commands:
   `install skill` (English) or `instalar skill` (Portuguese).
4. Claude explains what GreenRouter is, installs it, and activates it.

## 🗣️ Commands

| Command (EN / PT) | Effect |
|---|---|
| `install skill` / `instalar skill` | Install GreenRouter |
| `prioritize energy` / `prioritizar energia` | Prioritize energy savings |
| `prioritize quality` / `prioritizar qualidade` | Prioritize accuracy |
| `show ledger` / `mostrar ledger` | Full session summary |
| `reset ledger` / `reiniciar ledger` | Zero the ledger |

## 📜 License

MIT — See the LICENSE file.