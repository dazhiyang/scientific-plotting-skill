# 📊 Scientific Publication Plotter (AI Skill)

[![License: MIT](https://img.shields.io/badge/License-MIT-22c55e?style=for-the-badge)](https://github.com/dazhiyang/scientific-plotting-skill/blob/main/LICENSE)
[![Single file](https://img.shields.io/badge/skill-single--file-8b5cf6?style=for-the-badge)](SKILL.md)
[![No dependencies](https://img.shields.io/badge/deps-none-64748b?style=for-the-badge)]()
[![GitHub](https://img.shields.io/badge/repo-scientific--plotting--skill-181717?logo=github)](https://github.com/dazhiyang/scientific-plotting-skill)

## Overview

This repo ships **one** skill file, [`SKILL.md`](SKILL.md). Point your coding agent at it when you want **publication-style** figures: **ggplot2** in R or **plotnine** in Python, **vector PDF**, journal-friendly widths (**85 mm** / **180 mm**), **Wong** discrete colors, **viridis** with quantile splits for continuous color, and typography rules (single font size, **no plot title**—caption in the manuscript instead).

No bundled scripts: the agent generates code in your project from the rules in `SKILL.md`.

---

## Features

| | |
| :--- | :--- |
| 📏 **Sizing** | Default **85 mm** single column, **180 mm** when you need double column; prefer **flat** figures unless x and y are the same quantity. |
| 🔤 **Typography** | **Times** serif, **one** point size for **all** figure text; **no** plot title or subtitle on the canvas. |
| 📄 **Export** | **Vector PDF** (or EPS); raster only as an optional preview. |
| 🎨 **Color** | **Wong** order for discrete (≤8); **viridis** family + **equal-count quantiles** for continuous fields. |
| 🌐 **Stack** | **ggplot2** (R) and **plotnine** (Python) only for the figure code. |
| 🗺️ **Heavy plots** | Guidance for **dense scatter** (e.g. **scattermore** in R) and **low-resolution** map outlines so PDFs stay light. |

---

## Example prompts

Use wording close to your real task so the agent picks up the skill:

- *“Read `SKILL.md` and plot this CSV for my manuscript—single column PDF, ggplot2.”*
- *“Publication-style plotnine figure, Wong colors, vector output.”*
- *“Journal figure: 85 mm wide, no title, Times, save PDF.”*

---

## How to use

### 🖱️ Cursor

1. 📋 Copy **`SKILL.md`** into your **`.cursor/rules/`** folder.  
2. ✏️ Rename it to **`SKILL.mdc`**.  
3. 💬 Ask the AI to follow the skill (e.g. *“Plot my data for the manuscript.”*).

### 🤖 Claude Code, Copilot, and other agents

1. 📁 Add **`SKILL.md`** at the **root** of your project (or path your agent reads).  
2. 💬 Ask the model to use it (e.g. *“Read `SKILL.md` and plot the attached data.”*).

### 🛸 Google Antigravity

Antigravity loads **Agent Skills** from a folder that contains `SKILL.md` (see Google’s [Authoring Antigravity Skills](https://codelabs.developers.google.com/getting-started-with-antigravity-skills) codelab). This repo’s `SKILL.md` includes YAML **frontmatter** (`name`, `description`) so the agent can match plotting tasks.

**Project-only (recommended)**

1. 📂 Create e.g. **`.agent/skills/scientific-publication-plotter/`** in your repo.  
2. 📋 Copy **`SKILL.md`** there (path must end with **`SKILL.md`**).  
3. 💬 Ask for a manuscript-style figure in chat; the skill should load when the request matches the description.

**All projects on this machine**

1. 📂 Create **`~/.gemini/antigravity/skills/<your-skill-name>/`** and place **`SKILL.md`** inside.

**Optional — rules UI:** **Agent Manager → ⋮ → Additional options → Customizations** for **`GEMINI.md`** / **`AGENTS.md`** ([Antigravity rules](https://antigravity.codes/blog/user-rules)). Pasting the body of `SKILL.md` there is possible; **`.agent/skills/…`** keeps the skill **on-demand**.

---

## Make the repo easy to find (GitHub)

If you control [the GitHub repo](https://github.com/dazhiyang/scientific-plotting-skill):

1. **About** — add a one-line description (e.g. publication ggplot2/plotnine, vector PDF, Cursor/Antigravity skill).  
2. **Topics** — add tags such as: `ggplot2`, `plotnine`, `scientific-publishing`, `data-visualization`, `cursor-rules`, `pdf`, `latex`, `colorblind`, `reproducible-research`.  
3. **Share** — link from your profile, lab page, or a short post so others can star or fork it.

---

## License

MIT — see [`LICENSE`](LICENSE).
