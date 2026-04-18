# 📊 Scientific Publication Plotter (AI Skill)

[![License: MIT](https://img.shields.io/badge/License-MIT-22c55e?style=for-the-badge)](https://github.com/dazhiyang/scientific-plotting-skill/blob/main/LICENSE)
[![Single file](https://img.shields.io/badge/skill-single--file-8b5cf6?style=for-the-badge)](SKILL.md)
[![No dependencies](https://img.shields.io/badge/deps-none-64748b?style=for-the-badge)]()

A drop-in AI skill that **forces** large language models (LLMs) to format plots for **scientific journals**: exact sizing, strict typography, and **vector-only** export—no bundled scripts and no extra dependencies.

> 🧩 **One file.** The model reads [`SKILL.md`](SKILL.md), then writes plotting code in **your** stack (Python, R, Julia, MATLAB) with strict journal-style math and layout rules.

---

## ✨ Features

| | |
| :--- | :--- |
| 📏 **Exact sizing** | Single-column **85 mm** or double-column **180 mm** widths—computed explicitly, not guessed. |
| 🔤 **Strict fonts** | Serif (**Times New Roman**), **8 pt** body, **7 pt** ticks (unless you override). |
| 📄 **Vector-only** | No `.png` / `.jpg`; defaults to **`.pdf`** (or `.eps` when appropriate). |
| 🌐 **Language-agnostic** | Matches your repo: e.g. **Matplotlib**, **ggplot2**, **Plots.jl**, etc. |

---

## 🚀 How to use

### 🖱️ Cursor

1. 📋 Copy **`SKILL.md`** into your **`.cursor/rules/`** folder.  
2. ✏️ Rename it to **`SKILL.mdc`**.  
3. 💬 Ask the AI: *“Plot my data for the manuscript.”*

### 🤖 Claude Code, Copilot, and other agents

1. 📁 Drop **`SKILL.md`** at the **root** of your project.  
2. 💬 Ask: *“Read `SKILL.md` and plot the attached data.”*

---

## 📜 License

MIT — see [`LICENSE`](LICENSE).
