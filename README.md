# Velvosoft Website

Static snapshot and archive of [velvosoft.biz](https://velvosoft.biz/) — the website for **Velvosoft**, a Bangalore-based hygiene product manufacturer specializing in tissue products and hygiene cleaning solutions.

## About the live site

- **Platform:** WordPress + Elementor (page builder)
- **Hosting:** LiteSpeed / PHP
- **Live edits** are made through the WordPress admin (`/wp-admin`) and the Elementor visual editor. This repository is a **backup and portfolio copy**, not the live editing surface.

## Contents

| Path | Description |
|------|-------------|
| `snapshot/` | Self-contained static mirror of the public site (HTML, CSS, JS, images, fonts). Renders offline. |

## Viewing the snapshot locally

Open `snapshot/index.html` in a browser, or serve it:

```bash
cd snapshot
python3 -m http.server 8080
# then visit http://localhost:8080
```

## Notes

- The snapshot captures the public-facing pages as rendered. Dynamic features (checkout, forms, cart) require the live WordPress/WooCommerce backend and will not function in the static copy.
- Secrets (`wp-config.php`, `.env`, database dumps) are excluded via `.gitignore` and must never be committed to a public repository.

## Maintained by

Mohammed Touseef — owner, Velvosoft
