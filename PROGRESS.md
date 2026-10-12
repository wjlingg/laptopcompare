# Progress

Last updated: 12 Oct 2026.

## Done

- [x] Read the ASUS Singapore brochure PDF (7 scanned pages, brochure pp.64-70: ProArt, Zenbook, Vivobook, Vivobook Go spec tables, plus the August 2026 promo flyer).
- [x] Built the single-page guide: pick, specs explained, VRAM fit calculator, interactive comparison.
- [x] Checked the brochure was only a slice of the range, then collected current data from the ASUS Singapore store (132 laptops listed).
- [x] Re-based the page on store prices and added 35 models. Replaced the original brochure pick (TUF F16 `FX608JHI-TU255W`, now S$2,199 and out of stock) with TUF A16 `FA608UHI-TU147W`, S$1,999.
- [x] Committed to GitHub: https://github.com/wjlingg/laptopcompare (`main`).

## Current recommendation (12 Oct 2026)

| Role | Model | Price (S$) |
| --- | --- | --- |
| Best value | TUF Gaming A16 `FA608UHI-TU147W` (RTX 5050 8GB, 16GB DDR5, 1TB) | 1,999 |
| Stretch | TUF Gaming A16 `FA608UP-QT115W` (RTX 5070 8GB, 2.5K 165Hz) | 2,599 |
| Spend less, no GPU | Vivobook 14 `X1404MA-EB176W` (use Colab/Kaggle) | 1,299 |
| Cheap NVIDIA, catch | TUF F16 `FX607VU-RL461W` (RTX 4050 6GB, 512GB) | 1,599 |

## How to refresh the data

The store blocks `WebFetch` (403), so use a browser session on `https://sg.store.asus.com`.

1. Category pages (add `?product_list_limit=36`):
   - TUF: `/laptop/gaming-laptops/tuf-gaming-laptop.html`
   - ROG: `/laptop/gaming-laptops/rog-gaming-laptop.html`
   - All laptops (132 results, pages via `&p=1..4`): `/laptop.html`
2. From inside a store tab, `fetch()` each category page, parse with `DOMParser`, and read `.product-item` text for name, part number, price (`Special Price` then regular price), CPU, GPU, RAM, SSD, and `Notify Me` (= out of stock).
3. For display, refresh rate and RAM slot type, `fetch()` each product page (links are `https://sg.store.asus.com/asus-...html`) and read the text between `Technical Specifications:` and `Model No.`.
4. Update `L` in the HTML, re-check the pick with the rule in `CLAUDE.md`, update the date in the eyebrow, notice, and the data comment, then run the checks in `CLAUDE.md`.

## Known gaps and caveats

- Store pages do not list VRAM, so VRAM and CUDA cores are NVIDIA's public figures: 3050 4-6GB / 2,048, 4050 6GB / 2,560, 5050 8GB / 2,560, 5060 8GB / 3,328, 5070 8GB / 4,608, 5070 Ti 12GB / 5,888, 5080 16GB / 7,680. Re-verify if ASUS changes GPU variants.
- The V16 `V3607VJ` RTX 3050 variant (4GB or 6GB) is not stated, so VRAM is shown as "4-6GB (not stated)".
- No weights or battery life for TUF/ROG on the store pages.
- About 85 non-GPU models (ExpertBook, other Vivobooks, Zenbooks) are not in the tool. Only the ones from the brochure are, because their full specs were already known.
- NVIDIA "RTX Spark" ProArt P14/P16 (S$4,999-11,099, all out of stock) were left out; not evaluated for ML.
- Vivobook 16 `X1605VA-MB2822W` is no longer on the store list; its price is the August brochure price (`src:'b'`).
- ProArt P16 display (3K OLED touch) and 1.85kg weight are from the brochure spec table.
- Other retailers (Challenger, Harvey Norman, Lazada, Shopee) are not checked and may price differently.
- No benchmarks. "Cost per 1,000 CUDA cores" is a rough guide only; real speed depends on power limit and cooling.
- Not published as a hosted page. GitHub Pages is off.

## Ideas for next time

- Add a "recommended for you" quiz (budget, portability, screen, how often you train).
- Add benchmark data (e.g., public PyTorch training throughput per laptop GPU) to replace cores as the value metric.
- Include the non-GPU Vivobooks and Zenbooks with full specs, and weight/battery for TUF/ROG from ASUS product pages.
- Track price history (date-stamped snapshots of `L`) so the page can show whether a price is a good deal.
- Add a short "set up PyTorch with CUDA on Windows (WSL2)" section.
- Enable GitHub Pages (rename to `index.html`) for a shareable link.
- Compare against other brands, or against renting cloud GPUs, for the same money.
