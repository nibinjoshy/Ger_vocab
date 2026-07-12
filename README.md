# Verb-Kartei · Abfahrtstafel — Installable Web App

This folder turns your single HTML file into a full **Progressive Web App (PWA)**
that you can host for free on GitHub Pages and install on an Android phone
like a native app (home-screen icon, full-screen, works offline).

## What's in this folder

```
verb-kartei-app/
├── index.html          ← your app (with PWA tags added)
├── manifest.json        ← tells Android how to install the app
├── service-worker.js    ← caches the app so it works offline
└── icons/
    ├── icon-192.png
    ├── icon-512.png
    └── icon-maskable-512.png
```

## 1. Put it on GitHub Pages

1. Create a new GitHub repository (e.g. `verb-kartei`).
2. Upload **all files in this folder**, keeping the `icons/` folder structure intact.
   - Easiest way: on the repo page, click **Add file → Upload files**, then
     drag in `index.html`, `manifest.json`, `service-worker.js`, and the
     `icons` folder together.
3. Go to **Settings → Pages**.
4. Under **Build and deployment → Source**, choose **Deploy from a branch**.
5. Pick branch `main` and folder `/ (root)`, then click **Save**.
6. Wait about a minute, then GitHub will show your live URL, something like:
   ```
   https://YOUR-USERNAME.github.io/verb-kartei/
   ```

> **Important:** the app must be served over **https** (GitHub Pages does this
> automatically) — installable PWAs won't work over plain `http`.

## 2. Install it on your Android phone

1. Open the GitHub Pages URL above in **Chrome** on your Android phone.
2. Tap the **⋮** menu (top right).
3. Tap **Add to Home screen** (or you may see an **Install app** banner/prompt
   automatically — tap **Install**).
4. Confirm — the Verb-Kartei icon will appear on your home screen and app
   drawer, and will open full-screen like a native app, without the browser
   address bar.

Once installed, thanks to `service-worker.js`, the app will keep working even
without an internet connection (after the first load).

## Updating the app later

If you edit `index.html` and re-upload it to the repo, change the
`CACHE_NAME` value at the top of `service-worker.js` (e.g. `verb-kartei-v2`)
so phones pick up the new version instead of serving the old cached copy.

## Notes

- The icons are generated to match the app's black/amber theme. If you'd like
  a different icon design, just replace the three PNGs in `icons/` (keep the
  same filenames and sizes: 192×192 and 512×512).
- Google Fonts (Space Mono, Inter) are still loaded from the network the
  first time; after that they're cached by the browser as normal.
