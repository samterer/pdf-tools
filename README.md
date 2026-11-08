# PDF Workshop fonts

Optional fonts that the **PDF Workshop** Android app downloads on first use (instead of shipping them inside the app).

```
text/   fonts for the Text / Edit-text tools   (Nanum, Gothic A1, IBM Plex Sans KR, Roboto, Lato, Lora, …)
sig/    handwriting fonts for typed signatures (Nanum Pen Script, Nanum Brush Script, Gaegu)
manifest.json   file sizes + SHA-256 of every font (the app checks the size after downloading)
```

## Publishing (GitHub Pages)

1. Push this folder as the root of the public repository `samterer/pdf-tools`.
2. Repository → **Settings → Pages → Build and deployment → Deploy from a branch → `main` / `(root)`**.
3. The fonts are then served from `https://samterer.github.io/pdf-tools/text/Roboto.ttf`, etc.
4. Put that base URL (ending in `/`) in `www/js/fontstore.js` → `FONT_BASE_DEFAULT`.

GitHub Pages serves static files over HTTPS with CORS enabled and has no per-request limits that matter here
(site size soft limit 1 GB, 100 MB per file). Don't use `raw.githubusercontent.com` as a CDN.

## Updating

Fonts are addressed by file name and the app verifies each download against the size it was built with.
To change a font, add it under a **new file name** (and ship an app update that references it) rather than
replacing a file in place, so installed apps keep working.

Regenerate this folder and `manifest.json` from the app sources with `node scripts/prepare.mjs`.

## Licenses

All fonts here are free fonts under the **SIL Open Font License 1.1** (Nanum fonts by NAVER, the others from Google Fonts).
The OFL allows redistribution and use in documents and apps, but the fonts may not be sold on their own.
Each font remains the property of its authors; see each project's page for its copyright notice.
