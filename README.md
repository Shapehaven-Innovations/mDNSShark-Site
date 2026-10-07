# mDNSShark site

Static landing page for [mDNSShark](https://github.com/Shapehaven-Innovations/mDNSShark), an open-source iPhone app for local network discovery, security assessment and packet capture.

Live: https://mdnsshark.shapehaveninnovations.com/

## Layout

| Path | Purpose |
| ---- | ------- |
| `index.html` | The whole page: markup, CSS and the screenshot-tab script, no build step |
| `assets/` | App icon (`icon.png`, rounded `icon-rounded.png` for the favicon), screenshots (`screen*.webp`), `hero.svg`, `og.png`, `qr.png` |
| `llms.txt` | Short summary and links for LLM crawlers |
| `llms-full.txt` | Full app documentation in one file, copied from the app README |
| `robots.txt`, `sitemap.xml` | Crawler config |
| `CNAME` | Custom domain for GitHub Pages |
| `docs/superpowers/` | Design spec and plan for the page |

## Run locally

```sh
python3 -m http.server 8000
```

Open http://127.0.0.1:8000/.

## Keeping content in sync

- `llms-full.txt` is a copy of the app repo README. Refresh it when that README changes:
  ```sh
  gh api repos/Shapehaven-Innovations/mDNSShark/readme -H "Accept: application/vnd.github.raw"
  ```
  and keep the header block at the top of the file.
- If price, trial length, minimum iOS version or the feature list changes, update `index.html`, `llms.txt` and the JSON-LD block in `index.html` together.
- Regenerate `assets/icon-rounded.png` from `assets/icon.png` if the app icon changes.
