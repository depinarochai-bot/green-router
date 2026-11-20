<div align="center">

# 🌱 GreenRouter

**An energy-aware routing skill for Claude.**

Every AI task is routed to the model with the **lowest environmental cost** (energy × PUE × grid carbon intensity) that still meets your quality & latency requirements — and every task ends with a 🌍 planetary-contribution summary.

[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Claude Skill](https://img.shields.io/badge/Claude-Skill-blueviolet)](https://docs.claude.com)
[![Languages](https://img.shields.io/badge/lang-EN%20%7C%20PT--PT-blue)](#-português)
[![Status](https://img.shields.io/badge/status-stable-success)](CHANGELOG.md)

[Install](#-install) · [How it works](docs/HOW-IT-WORKS.md) · [Examples](examples/) · [Tuning](docs/TUNING.md) · [Contributing](CONTRIBUTING.md)

</div>

---

## Why GreenRouter?

Not every task needs the biggest model. A summarization task doesn't require the same compute as a code-refactoring task, and running everything on the heaviest model wastes energy, money, and grid capacity. GreenRouter makes the **environmental cost** a first-class citizen in model selection:

- **Picks the greenest viable model** for each task — not the cheapest, not the most powerful.
- **Respects hard constraints** on quality (min accuracy) and latency (max seconds).
- **Accounts for datacenter cooling** via PUE and **grid carbon intensity** via Electricity Maps.
- **Reports impact per task** and a **running session average** — you see exactly what you saved versus always using the heaviest model.

> Typical savings: **30–60 % fewer gCO₂e per task** vs always using the largest model, with no measurable quality loss on standard tasks.

---

## ✨ Features

| | |
|---|---|
| 🌱 **Energy-aware routing** | Picks the lowest-cost model that meets your accuracy/latency constraints |
| 🌍 **Planetary footer** | Per-task emissions, session average, total, and savings vs baseline |
| ⚖️ **Tunable weights** | Prioritize energy, quality, or balance them |
| 🔌 **Electricity Maps ready** | Optional real-time grid carbon intensity |
| 📊 **Session ledger** | `show ledger` / `reset ledger` commands |
| 🌐 **Bilingual** | Full English and Portuguese support |
| 🧩 **Zero-dependency** | Pure markdown skill — no runtime, no install scripts |

---

## 📦 Install

### Option A — Copy-paste (fastest)

1. Open [`SKILL.md`](SKILL.md) and copy its full content.
2. Paste it into a Claude conversation (app, web, or Claude Code).
3. Send one of these commands:

   ```
   install skill
   instalar skill
   ```

4. Claude explains what GreenRouter is, installs it for the current Project, and activates it.
5. To persist across conversations, save it as a **Project skill** (app/web) or copy the file to `~/.claude/skills/green-router/SKILL.md` (Claude Code).

### Option B — Git clone (Claude Code)

```bash
git clone https://github.com/<your-user>/green-router.git
mkdir -p ~/.claude/skills/green-router
cp green-router/SKILL.md green-router/model_catalog.json ~/.claude/skills/green-router/
```

Restart Claude Code. The skill will appear as `green-router` and load automatically.

### Option C — Plugin marketplace (if enabled)

```bash
/plugin marketplace add <your-user>/green-router
```

### Option D — One-liner (copy directly into skill folder)

```bash
mkdir -p ~/.claude/skills/green-router && \
curl -sSL https://raw.githubusercontent.com/<your-user>/green-router/main/SKILL.md \
  -o ~/.claude/skills/green-router/SKILL.md
```

---

## 🎬 Demo

Ask Claude:

> "Summarize this report. Pick the most energy-efficient model with accuracy ≥ 0.80."

You get:

```
🌱 GreenRouter decision
Model: gemini-2.0-flash
Energy: 1.85 Wh  (PUE 1.54)
Emissions: 0.554 gCO₂e  (CI 300 gCO₂e/kWh)
Accuracy: 0.82  |  Latency: 2.0 s
Reason: lowest environmental cost among models meeting accuracy ≥ 0.80
```

…then the answer, then:

```
🌍 Planetary contribution — task #1
This task:     1.85 Wh | 0.554 gCO₂e
Session total: 1.85 Wh | 0.554 gCO₂e across 1 task
vs baseline:   saved 1.161 gCO₂e (67.7%) compared to always using claude-3.5-haiku
```

See full [examples](examples/).

---

## 🧠 How it works

1. **Classify** the task (`text` / `code` / `multimodal`).
2. **Filter** models that violate your constraints (accuracy, latency, energy cap).
3. **Compute** environmental cost:

   ```
   gCO₂e = energy_Wh × PUE × CI / 1000
   ```

4. **Score** the survivors:

   ```
   score = w_q × accuracy − w_e × (energy_Wh/10) − w_l × (latency/max_latency)
   ```

5. **Pick** the highest-scoring model.
6. **Report** the decision (🌱) and, after the task, the planetary footer (🌍).

Full methodology: [`docs/HOW-IT-WORKS.md`](docs/HOW-IT-WORKS.md).

---

## 🗣️ Commands

| Command (EN / PT) | Effect |
|---|---|
| `install skill` / `instalar skill` | Install GreenRouter |
| `prioritize energy` / `prioritizar energia` | `w_energy = 3` |
| `prioritize quality` / `prioritizar qualidade` | `w_quality = 3` |
| `show ledger` / `mostrar ledger` | Full session summary |
| `reset ledger` / `reiniciar ledger` | Zero the ledger |
| `set PUE to X` / `definir PUE para X` | Override PUE |
| `use Electricity Maps, zone XX` | Real-time carbon intensity |

---

## 📊 Model catalog

The default catalog lives in [`model_catalog.json`](model_catalog.json). You can override it with your own benchmarks:

```json
[
  { "name": "llama-3.1-8b", "wh_per_query": 0.443,
    "accuracy": {"text": 0.72, "code": 0.60}, "latency_s": 2.5 }
]
```

See [`docs/TUNING.md`](docs/TUNING.md) for guidance.

---

## 🌐 Português

**GreenRouter** é um *skill* de roteamento energético-consciente para o Claude. Cada tarefa é encaminhada para o modelo com o **menor custo ambiental** (energia × PUE × intensidade de carbono da rede) que ainda cumpra os requisitos de qualidade e latência — e cada tarefa termina com um resumo 🌍 de contribuição planetária.

### Instalação (PT)

1. Copia o conteúdo de [`SKILL.md`](SKILL.md).
2. Cola numa conversa com o Claude.
3. Envia: `instalar skill`.
4. O Claude explica, instala e ativa.
5. Persistência: guarda como *Project skill* (app/web) ou copia para `~/.claude/skills/green-router/SKILL.md` (Claude Code).

### Comandos (PT)

- `prioritizar energia` · `prioritizar qualidade`
- `mostrar ledger` · `reiniciar ledger`
- `definir PUE para 1.15` · `usar Electricity Maps, zona PT`

---

## 🤝 Contributing

Pull requests welcome. See [`CONTRIBUTING.md`](CONTRIBUTING.md) and [`CHANGELOG.md`](CHANGELOG.md).

Ideas welcome as issues:
- New model entries in the catalog
- Alternative scoring functions (e.g. Pareto)
- Water-usage metrics (WUE)
- Integration with the Claude plugin marketplace

---

## 📜 License

MIT — see [`LICENSE`](LICENSE).

## 🙏 Acknowledgements

Inspired by research on **carbon-aware computing** and **energy-efficient LLM routing** (PEARL, Electricity Maps, Uptime Institute PUE reports).

> Built with the belief that every prompt deserves a conscious choice.