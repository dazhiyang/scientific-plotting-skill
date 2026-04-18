# Scientific Publication Plotter (AI Skill)

A drop-in AI skill that forces large language models (LLMs) to format plots perfectly for scientific journals. 

It is just one file. No scripts, no dependencies, no bloat. The AI reads the rules and dynamically writes the plotting code in your preferred language (Python, R, Julia, MATLAB) while following strict typesetting math.

## Features
- **Exact Sizing:** Forces the AI to calculate exact dimensions (85mm single-column or 180mm double-column).
- **Strict Fonts:** Enforces Serif fonts (Times New Roman) and specific sizes (8pt base, 7pt ticks).
- **Vector-Only Output:** Prevents the AI from making `.png` files, forcing high-quality `.pdf` or `.eps` generation instead.
- **Language Agnostic:** Adapts to your workspace (e.g., uses `ggplot2` for R, or `matplotlib` for Python).

## How to Use

**For Cursor:**
1. Copy `SKILL.md` into your `.cursor/rules/` directory.
2. Rename it to `SKILL.mdc`.
3. Ask the AI: *"Plot my data for the manuscript."*

**For standard AI Agents (Claude Code, Copilot):**
1. Drop `SKILL.md` into the root of your project folder.
2. Ask the AI: *"Read SKILL.md and plot the attached data."*

## License
MIT
