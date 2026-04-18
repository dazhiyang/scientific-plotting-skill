# Scientific Publication Plotting Standard

## Context
Use this skill whenever the user asks to visualize, plot, or graph data intended for a scientific paper, manuscript, or academic publication. 

## Core Philosophy
Do not rely on hardcoded scripts. You must dynamically generate and execute the plotting code natively in the user's preferred language (e.g., Python/Matplotlib, R/ggplot2, Julia/Plots) based on their current workspace environment.

## Strict Formatting Constraints
When generating the plotting code, you MUST enforce the following journal typesetting rules:

1. **Figure Dimensions (Critical):**
   - Single-column figures MUST be exactly 85 mm wide.
   - Double-column figures MUST be exactly 180 mm wide.
   - Default to single-column (85 mm) unless the user explicitly requests double.
   - Calculate the height using the golden ratio (width / 1.618).

2. **Typography:**
   - Font Family: MUST be a Serif font, strictly "Times New Roman".
   - Base Font Size: 8 pt (unless the user specifies 7 pt or 9 pt).
   - Tick Labels: 1 pt smaller than the base font (e.g., 7 pt).

3. **Line Weights & Aesthetics:**
   - Data lines: 1.0 pt width.
   - Axes, grid lines, and error bars: 0.5 pt width.
   - Bounding box: Set to "tight" to eliminate excess whitespace.

4. **Vector-Only Output:**
   - NEVER rasterize the output. DO NOT save as `.png`, `.jpg`, or `.jpeg`.
   - Save the final figure exclusively as a vector format (default to `.pdf`).

## Execution
1. Analyze the user's data and request.
2. Write the optimal plotting code in the user's active language, baking in the strict constraints above.
3. Execute the code to generate the vector file in the current directory.
