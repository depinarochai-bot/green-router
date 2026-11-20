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
