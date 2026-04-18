# 📊 Scientific Publication Plotter (AI Skill)

[![License: MIT](https://img.shields.io/badge/License-MIT-22c55e?style=for-the-badge)](https://github.com/dazhiyang/scientific-plotting-skill/blob/main/LICENSE)
[![Single file](https://img.shields.io/badge/skill-single--file-8b5cf6?style=for-the-badge)](SKILL.md)
[![No dependencies](https://img.shields.io/badge/deps-none-64748b?style=for-the-badge)]()

A drop-in AI skill that **forces** large language models (LLMs) to format plots for **scientific journals**: exact sizing, strict typography, and **vector-only** export—no bundled scripts and no extra dependencies.

> 🧩 **One file.** The model reads [`SKILL.md`](SKILL.md), then writes plotting code in **R (ggplot2)** or **Python (plotnine)** with strict journal-style math and layout rules.

---

## ✨ Features

| | |
| :--- | :--- |
| 📏 **Exact sizing** | Single-column **85 mm** or double-column **180 mm** widths—computed explicitly, not guessed. |
| 🔤 **Strict fonts** | One serif (**Times**), **one pt size** for all figure text; **no plot title** (caption in the paper). |
| 📄 **Vector-only** | No `.png` / `.jpg`; defaults to **`.pdf`** (or `.eps` when appropriate). |
| 🌐 **R & Python** | **ggplot2** (R) and **plotnine** (Python)—same grammar of graphics, no other primary plotting API unless you override. |

---

## 🚀 How to use

### 🖱️ Cursor

1. 📋 Copy **`SKILL.md`** into your **`.cursor/rules/`** folder.  
2. ✏️ Rename it to **`SKILL.mdc`**.  
3. 💬 Ask the AI: *“Plot my data for the manuscript.”*

### 🤖 Claude Code, Copilot, and other agents

1. 📁 Drop **`SKILL.md`** at the **root** of your project.  
2. 💬 Ask: *“Read `SKILL.md` and plot the attached data.”*

### 🛸 Google Antigravity

Antigravity loads **Agent Skills** from a folder that contains `SKILL.md` (see Google’s [Authoring Antigravity Skills](https://codelabs.developers.google.com/getting-started-with-antigravity-skills) codelab). This repo’s `SKILL.md` already includes YAML **frontmatter** (`name`, `description`) so the agent can match plotting requests.

**Project-only (recommended)** — skill applies to one workspace:

1. 📂 Create a skill directory under your repo, e.g. **`.agent/skills/scientific-publication-plotter/`**.  
2. 📋 Copy **`SKILL.md`** from this repo into that folder (path must end with **`SKILL.md`**).  
3. 💬 In Agent chat, ask for a manuscript-style figure (e.g. *“Plot … for the paper, vector PDF, single column”*). The agent should **activate** the skill when the task matches the description.

**All projects on this machine** — same layout under your user config:

1. 📂 Create **`~/.gemini/antigravity/skills/scientific-publication-plotter/`** (pick any folder name; keep **`SKILL.md`** inside).  
2. 📋 Copy **`SKILL.md`** there.

**Optional — rules UI:** You can also add always-on text rules via **Agent Manager → ⋮ → Additional options → Customizations** and edit **`GEMINI.md`** / **`AGENTS.md`** (see [Antigravity rules paths](https://antigravity.codes/blog/user-rules)); pasting the body of `SKILL.md` there works, but the **`.agent/skills/…`** layout keeps this skill **modular** and on-demand like other Antigravity skills.

---

## 📜 License

MIT — see [`LICENSE`](LICENSE).
