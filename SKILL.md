---
name: scientific-publication-plotter
description: Use for scientific-paper figures in **R (ggplot2)** or **Python (plotnine)**. Default **85 mm** single column, **180 mm** double-column when needed; flat aspect; light PDFs (scattermore / low-res maps); Wong ≤8; viridis + quantile color; parameter block.
---

# Scientific Publication Plotting Standard

## When to use
Manuscript-quality figures: **vector** output, readable typography, a **single top-of-file parameter block** the user can edit without searching the script, and the **color rules** below whenever color encodes data.

## Stack
**R → ggplot2 only; Python → plotnine only.**

## Script layout
1. Imports / setup.  
2. **Parameter block** — all tunable sizes, figure dimensions, the **Wong hex list** when discrete **≤8** colors apply, and **always** include **auto quantile** settings for continuous color: **viridis-family** map name + rule that color follows **equal-count quantile** breaks derived from the data (no fixed bin-count knob required—see **Color**).  
3. Optional **base path** variable if the user manages data/output in a fixed tree; otherwise use the working directory.  
4. Data preparation → build figure → **save** using only values from the parameter block.

## Color

### Discrete qualitative data (Wong, colorblind-safe)
Use this when color distinguishes **categories or series** (lines, bars, points, map classes)—**not** for continuous magnitude.

- If the plot needs **eight or fewer** distinct data colors, use **Bang Wong’s** colorblind-safe palette in the **exact order below** (position 1 → first category after **stable** factor / legend ordering, position 2 → second, …). **Do not reorder** colors for taste; if you must drop series, drop from the end of the **category list**, not by reshuffling colors.
- Define the hex values **once** in the parameter block (e.g. a vector/list) and reference them from scales—no one-off hex literals scattered through geoms.

| Order | Name | Hex |
|------:|------|-----|
| 1 | orange | `#E69F00` |
| 2 | sky blue | `#56B4E9` |
| 3 | blue green | `#009E73` |
| 4 | pale violet | `#CC79A7` |
| 5 | vermillion | `#D55E00` |
| 6 | yellow | `#F0E442` |
| 7 | blue | `#0072B2` |
| 8 | black | `#000000` |

- If **more than eight** discrete colors would be needed, **do not** invent extra saturated colors: merge categories, split across facets, and/or encode class with **linetype**, **marker shape**, or **fill pattern**, or ask the user how to regroup.

### Continuous data (viridis family + quantile splits)
Use this when color encodes a **numeric field** (heatmaps, choropleth, filled contours, color-mapped scatter).

- **Colormap:** use **only** maps from the **viridis family**—**viridis**, **plasma**, **inferno**, **magma**, or **cividis** (same design system). **Default: viridis.** Do **not** use jet, rainbow, turbo, HSV rainbows, or any colormap outside this family unless the user explicitly overrides in writing.
- **Auto quantile (default on):** the parameter block **always** sets the **viridis-family** map and documents that continuous color uses **equal-count quantile** breaks computed from the data (finite values only), then maps those bands through the **full** viridis ramp—**not** a naive linear stretch of raw values (avoids one hue dominating skewed distributions). Choose break count or quantile grid **inside the plotting code** from the data shape (e.g. deciles)—not as a fixed tunable in the parameter block. If nothing uses continuous color, leave those settings unused. **Rasters:** same idea on valid cells, or percentile-transform before a linear colormap API.

## Visual conventions
- **Typography:** serif text aligned with **Times** / **Times New Roman** in the exported PDF; one **base font size (pt)** for titles, axis labels, ticks, and legend text unless the design needs a smaller secondary size (derive it from the base, e.g. a fixed ratio—keep that ratio in the parameter block).
- **Canvas:** prefer a **white** panel, **light major grid**, **no minor grid** (or visually negligible), and **transparent** figure background where the API allows—so TeX can place the PDF on any page color.
- **Lines & points:** line widths and marker sizes come from the parameter block; use a thinner width for axes, grids, and error bars than for main data if the library distinguishes them.
- **Dense scatter (PDF size):** very large point counts **bloat vector PDFs**—use **smaller** markers, **alpha**, subsampling, or **hex / 2d density** when appropriate. **R:** prefer **`scattermore`** with `geom_scattermore()` for big scatterplots instead of millions of `geom_point()` glyphs. **Python:** thin the data, use **`geom_hex`** / 2d bins, or smaller `size` + alpha—avoid shipping huge raw-point layers in the PDF.
- **Maps / boundaries:** always draw **low-resolution** / **simplified** outlines (generalized polygons, coarse shape layers). Do not embed **high-res** coastlines or admin boundaries unless the user explicitly needs that detail.
- **Axis math:** proper mathematical typography (Unicode math, LaTeX, expression-style calls, etc.—whatever the stack supports)—not ASCII hacks for units, powers, or Greek letters.
- **Column width:** default **`width_mm` = 85** (single column). Use **`width_mm` = 180** only for **double-column** figures when the user or venue asks. Prefer **single column** whenever possible and **vertically stacked** facets (`ncol = 1` / one column of panels) instead of a wide strip—reserve 180 mm only when content truly needs full page width.
- **Flat aspect:** prefer a **flatter** canvas (**width_mm** clearly larger than **height_mm**) so the figure reads easily in print—**unless** **x** and **y** are the **same quantity** (same units and a **1:1** relationship matters: parity lines, isotropic space, Q–Q plots, etc.), in which case use **equal** aspect / a square layout as appropriate.
- **Multi-panel:** align stacked or composed panels cleanly; one **`width_mm` / `height_mm`** for the saved figure, driven by the rules above.

## Parameter block (mandatory)
Define at least these **roles** (idiomatic names in R or Python):

| Role | Typical starting values | Purpose |
|------|-------------------------|---------|
| Base font | ~8 pt | Axis, ticks, legend, facet strip text |
| Line width (data) | one small default in stroke units | Main lines (comment the unit) |
| Point / marker size | small; **smaller still** for dense scatter | Scatter / markers; shrink for many points (see **Visual conventions**) |
| Legend scale | optional second knob | Legend glyphs only, if needed |
| Smaller text | e.g. base × 5/14 | Captions or secondary labels |
| **`width_mm`**, **`height_mm`** | **`width_mm`:** **85** (default single column) or **180** (double column when required); **`height_mm`:** flat unless x/y same-quantity | Journal-style widths; see **Visual conventions** |
| **Wong palette** | fixed `#E69F00`, `#56B4E9`, … | Discrete **≤8** series only; see **Color** |
| **Continuous color** | viridis-family name + quantile-color note | Always present; see **Color** |

No duplicate numeric literals for the same aesthetic elsewhere in the file.

## Export
Vector **PDF** (or EPS) at **`width_mm` × `height_mm`** via ggplot2/plotnine; optional raster preview only.

## Execution
1. **Parameter block → plot → save** (ggplot2 or plotnine per task); viridis + auto quantile always in the block; Wong / quantile rules in **Color**; for big scatter use **scattermore** (R) or density-friendly geoms (Python); maps use **low-res** shapes.  
2. Run and confirm the vector file exists.
