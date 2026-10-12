# CLAUDE.md

Project: a single-file HTML guide and comparison tool for choosing an ASUS laptop (Singapore) for machine learning on a budget. Read `PROGRESS.md` before changing data or the recommendation.

## Ground rules

- **One file.** Everything lives in `asus-ml-laptop-guide.html` (inline CSS and JS). Keep it self-contained. No framework or build step.
- **Audience.** A beginner who wants to understand laptop specs and pick a cost-efficient machine for decent, non-heavy ML. Write plain, direct sentences. No jargon without a one-line explanation.
- **Currency and region.** S$, GST included, ASUS Singapore store.
- **Never invent specs.** If the source does not state a value, use `null` / "not stated" / "Not stated". VRAM and CUDA cores come from NVIDIA public specs and must stay flagged as such in the page copy.
- **Keep the recommendation consistent with the data.** The pick card, the "alts" cards, the lede and the `pick:1` flag in the data must agree. When prices change, re-derive the pick (rule below), then update all four.

## Recommendation rule (how the pick was chosen)

1. Must have an NVIDIA GPU (CUDA). Other GPUs and NPUs do not help training.
2. Prefer 8GB VRAM or more (RTX 5050 and up). 4-6GB cards (3050/4050) are listed as the "cheaper, with a catch" option.
3. Prefer 1TB SSD and upgradeable RAM (SO-DIMM) at the lowest price. Currently: TUF A16 `FA608UHI-TU147W`.
4. Show the "stretch" option as the best S$ per 1,000 CUDA cores among 8GB models (cores are comparable only within one GPU generation).

## Data model (inside the `<script>`)

- `GPU` table: per-GPU `vram`, `cuda` (cores), `gen`, optional `vramText`.
- `g(id, name, model, price, up, cpu, cores, boost, gpu, ram, ramType, slot, ssd, size, w, h, panel, hz, extra)`: builds an NVIDIA-GPU laptop. `up` = usual price, `ssd` in GB, `w`/`h` = resolution.
- Non-GPU models are plain object literals at the top of `L`.
- Flags: `pick:1` (best value chip), `oos:1` (out of stock), `src:'b'` (price from the brochure, not the store), `fit` = `cuda | light | arm | mem`.
- Persisted UI state: `localStorage` key `asus-ml-sel2` (selected compare ids). Bump the key if ids change.
- Add a model: append to `L` (use `g()` for NVIDIA), keep ids unique, and update counts in the page copy ("35 current models").

## Checks after editing

- Open the file in a browser; the console must be clean.
- The list count reads "(N of N shown)" with N equal to the number of entries in `L`.
- No `NaN` or `undefined` in the page text. Light and dark themes both stay readable (tokens are defined on `:root`, then redefined for dark).
- The page body never scrolls sideways at phone width; only tables scroll inside their containers.

## Gotchas

- `WebFetch` gets HTTP 403 from `sg.store.asus.com`. Use a real browser (the built-in browser pane works).
- The source PDF is scanned images with no text layer. Render pages to images to read them.
- Store list pages hide spec text for non-gaming models until "See more" is opened; fetch each product page for the full spec line.
