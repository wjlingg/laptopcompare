# ASUS ML Laptop Guide

A single-page guide to choosing an ASUS laptop in Singapore for day-to-day machine learning on a budget.

Open `index.html` in any browser. No build step, no dependencies (it loads three Google Fonts and falls back to system fonts offline).

## What the page contains

1. **The pick**: a recommended laptop, three alternatives, and a price-freshness notice.
2. **Specs explained**: plain-language cards for GPU/VRAM, RAM, CPU, storage, NPU, display, ports, weight, warranty and model numbers, each with an "For ML" takeaway.
3. **Will my model fit?**: a rule-of-thumb calculator comparing model memory needs to GPU VRAM.
4. **Compare the laptops**: filter by price, RAM and NVIDIA GPU, sort, and tick up to four models for a side-by-side with best-in-row highlighting.

## Where the data comes from

| Data | Source | As of |
| --- | --- | --- |
| Prices, CPU, RAM, SSD, screen, stock | ASUS Singapore online store (`sg.store.asus.com`) | 12 Oct 2026 |
| Brochure-only model (Vivobook 16 `X1605VA`) and spec notes (ports, Wi-Fi, weights) | "ASUS Singapore specifications comparison" brochure PDF, Majulah Singapura Specials, 1-31 Aug 2026 | Aug 2026 |
| VRAM and CUDA core counts | NVIDIA public laptop GPU specs (not listed by the store) | n/a |

Prices change often. Re-check them before relying on the page. See `PROGRESS.md` for how to refresh.

## Files

- `index.html`: the whole page (HTML, CSS and JS inline).
- `CLAUDE.md`: working notes for Claude (or any contributor) editing the page.
- `PROGRESS.md`: what is done, how the data was gathered and how to refresh it, known gaps, and next ideas.
