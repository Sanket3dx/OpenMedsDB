# OpenMedsDB

A free, searchable reference for medicines available in India — composition,
uses, side effects, dosage, drug interactions, substitutes and safety advice.

**Live site:** https://openmedsdb.in

Compiled & maintained by **Sanket Patil**.

> Informational reference only — not medical advice. Always consult a doctor or pharmacist.

---

## About

The entire app is a **single static HTML file** (`index.html`) — no framework, no
build step, no backend. It loads data on demand from a public dataset over HTTPS:

- searching fetches only a small index shard for the letters you type
- opening a medicine fetches that one record
- the interaction checker compares the selected medicines in your browser

Routing is hash-based (`#/`, `#/m/<slug>`, `#/rx`), so it runs on any static host
with no server configuration.

## Deploy

### Cloudflare Pages (free, unlimited bandwidth)
1. Workers & Pages → Create → Pages → connect this repo.
2. Build command: *(none)*  ·  Build output directory: `/`

### GitHub Pages
Settings → Pages → Source: *Deploy from a branch* → `main` / `/ (root)`.

### Netlify
Connect the repo, publish directory `/`, no build command.

## Configuration

The data source is one line near the top of the `<script>` in `index.html`:

```js
const DATA_BASE = "https://huggingface.co/datasets/sanket3dx/medicine_db/resolve/main";
```

## License

Code: MIT (see [`LICENSE`](LICENSE)). The medicine data is provided for
informational purposes only, with no warranty of accuracy or completeness.
