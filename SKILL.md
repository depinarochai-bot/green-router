---
name: green-router
description: |
  Energy-aware model router with a per-task planetary-impact summary.
  EN triggers: "install skill", "install green-router", "choose the most efficient
  model", "route by energy", "minimize environmental impact".
  PT triggers: "instalar skill", "instalar green-router", "escolher o modelo mais
  eficiente", "rotear por energia", "minimizar impacto ambiental".
---

# GreenRouter — Energy-Aware Model Router / Roteador Energético-Consciente

## 🚨 INSTALLATION PROTOCOL

**Trigger commands:** `install skill`, `install green-router`, `instalar skill`,
`instalar green-router`.

When the user pastes this file and sends one of the trigger commands, respond
in the user's language (English if the trigger was English, Portuguese if
Portuguese) and execute:

### Step 1 — Explain (2–4 sentences)
GreenRouter is an energy-aware routing skill. Every task in this conversation
will be routed to the model with the **lowest environmental cost**
(energy × PUE × grid carbon intensity) that still meets the user's quality and
latency requirements. After every task, a **🌍 planetary contribution footer**
shows that task's impact, the running session average, and how much was saved
versus a baseline.

### Step 2 — Install
- **Claude Code:** write this file to `~/.claude/skills/green-router/SKILL.md`
  (ask for confirmation first). Confirm the skill loads on next restart.
- **Claude app / web:** activate for the current Project or conversation.
  Tell the user that to persist across conversations they should save it as a
  Project skill or copy `SKILL.md` to `~/.claude/skills/green-router/`.

### Step 3 — Confirm activation (see Activation message below).

### Step 4 — Initialize the session ledger
Create an in-conversation ledger with these fields, all starting at zero:
[
  {
    "name": "llama-3.1-8b",
    "wh_per_query": 0.443,
    "accuracy": { "text": 0.72, "code": 0.60 },
    "latency_s": 2.5
  },
  {
    "name": "gpt-4o-mini",
    "wh_per_query": 1.9,
    "accuracy": { "text": 0.84, "code": 0.78 },
    "latency_s": 1.8
  },
  {
    "name": "gemini-2.0-flash",
    "wh_per_query": 1.2,
    "accuracy": { "text": 0.82, "code": 0.75 },
    "latency_s": 2.0
  },
  {
    "name": "claude-3.5-haiku",
    "wh_per_query": 4.5,
    "accuracy": { "text": 0.86, "code": 0.82 },
    "latency_s": 2.2
  },
  {
    "name": "gpt-4o",
    "wh_per_query": 2.9,
    "accuracy": { "text": 0.90, "code": 0.88 },
    "latency_s": 2.8
  }
]# 🌱 GreenRouter

**An energy-aware routing skill for Claude.**

Every AI task is routed to the model with the **lowest environmental cost** (energy × PUE × grid carbon intensity) that still meets your quality & latency requirements — and every task ends with a 🌍 planetary-contribution summary.

## Why GreenRouter?

Not every task needs the biggest model. GreenRouter makes the **environmental cost** a first-class citizen in model selection:
- **Picks the greenest viable model** for each task.
- **Respects hard constraints** on quality and latency.
- **Accounts for datacenter cooling** (PUE) and **grid carbon intensity**.
- **Reports impact per task** and a **running session average**.

## 📦 Install

1. Open `SKILL.md` and copy its full content.
2. Paste it into a Claude conversation.
3. Send one of these commands:
   `install skill` (English) or `instalar skill` (Portuguese).
4. Claude explains what it is, installs it, and activates it.

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