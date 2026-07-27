# navraj-bite.github.io

**Navraj Singh Gill** — CS @ Waterloo. Portfolio site: the work up front, and an optional
view that re-ranks the whole page against a job description using a real
sentence-transformer running in your browser.

🔗 **Live:** [navraj-bite.github.io](https://navraj-bite.github.io) ·
📄 **CV:** [assets/navraj-gill-cv.pdf](assets/navraj-gill-cv.pdf)

## Layout

The default page is plain: hero → work → experience → skills → CV. No interaction is
required to read any of it, and the CV is a static PDF.

The **tailored view** is opt-in — a collapsed strip below the work. Open it, paste a job
description, and the page embeds it with
[`Xenova/all-MiniLM-L6-v2`](https://huggingface.co/Xenova/all-MiniLM-L6-v2) via
[transformers.js](https://github.com/xenova/transformers.js), then re-ranks every project
by cosine similarity. Runs entirely client-side — nothing is uploaded.

If the top cosine falls below `WEAK_FIT` (0.25) the page says there's no strong match
rather than reordering cards and hoping you don't check. MiniLM similarities compress
into roughly 0.2–0.6, so the ranking is the signal and the absolute number isn't.

## Tech

- **Single static file.** Everything lives in [`index.html`](index.html) — no build step,
  no framework, no bundler.
- **In-browser inference.** `@xenova/transformers@2.17.2` (ESM) from a CDN; embeddings
  computed locally, with a transparent tag-model fallback that announces itself on failure.
- **PCA from scratch.** The 2-D skill-space projection is power iteration with deflation.
- **Type:** Space Grotesk / Inter / IBM Plex Mono.
- Must be served over `http(s)://` — the ESM imports and model fetch don't run from `file://`.

## Run locally

```bash
python3 -m http.server 8000
# then open http://localhost:8000
```

## Deploy

Hosted on **GitHub Pages** from `main`. The repo is named `Navraj-bite.github.io`, so
GitHub serves it at the root user domain. Push to `main` and it's live.

## Contact

- **Email:** [ns8gill@uwaterloo.ca](mailto:ns8gill@uwaterloo.ca)
- **GitHub:** [@Navraj-bite](https://github.com/Navraj-bite)
- **LinkedIn:** [navrajsgill](https://www.linkedin.com/in/navrajsgill)
