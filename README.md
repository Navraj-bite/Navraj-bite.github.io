# the portfolio is the model

**Navraj Singh Gill** — CS @ Waterloo. An ML portfolio that ranks its own projects against *your* job description, using a real sentence-transformer running entirely in your browser.

🔗 **Live:** [navraj-bite.github.io](https://navraj-bite.github.io)

## What it does

Paste a job description and the page embeds it with [`Xenova/all-MiniLM-L6-v2`](https://huggingface.co/Xenova/all-MiniLM-L6-v2) via [transformers.js](https://github.com/xenova/transformers.js), then re-ranks the portfolio's projects by cosine similarity to what you're hiring for. The ranking is real — the model runs client-side, in-browser, with a tag-based fallback if the CDN or model fetch is unavailable.

## Tech

- **Single static file.** Everything lives in [`index.html`](index.html) — no build step, no framework, no bundler.
- **In-browser inference.** `@xenova/transformers@2.17.2` (ESM) loaded from a CDN; sentence embeddings computed locally, nothing sent to a server.
- **Type:** Space Grotesk / Inter / IBM Plex Mono.
- Must be served over `http(s)://` — the ESM imports and model fetch don't run from `file://`.

## Run locally

```bash
# any static server works; here's one with Python
python3 -m http.server 8000
# then open http://localhost:8000
```

## Deploy

Hosted on **GitHub Pages** from the `main` branch. Because the repo is named `Navraj-bite.github.io`, GitHub serves it at the root user domain automatically. Push to `main` and it's live.

## Contact

- **Email:** [ns8gill@uwaterloo.ca](mailto:ns8gill@uwaterloo.ca)
- **GitHub:** [@Navraj-bite](https://github.com/Navraj-bite)
- **LinkedIn:** [navrajsgill](https://www.linkedin.com/in/navrajsgill)
