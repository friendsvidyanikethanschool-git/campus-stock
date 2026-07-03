# Campus Stock — deploying to GitHub Pages

## What's in this folder
- `index.html` — the app
- `manifest.json` — makes it installable as an app icon on phones
- `sw.js` — service worker, lets it work offline once loaded
- `icons/` — app icons

## Deploy steps
1. Create a new repository on GitHub (Settings → your name → New repository). Any name works, e.g. `campus-stock`.
2. Upload all the files in this folder into the repository, keeping the `icons/` folder structure intact (GitHub's web UI → **Add file → Upload files**, drag the whole folder in works fine, or use `git push` if you're comfortable with git).
3. In the repository, go to **Settings → Pages**.
4. Under **Build and deployment → Source**, choose **Deploy from a branch**, pick the `main` branch and `/ (root)` folder, then **Save**.
5. Wait a minute or two — GitHub will give you a URL like `https://yourusername.github.io/campus-stock/`.

That URL is a real HTTPS site, which is what makes camera scanning work (browsers only allow camera access on secure, non-embedded pages) and what makes "Add to Home Screen" available.

## Installing it like an app on a phone
- **Android (Chrome):** open the URL, tap the ⋮ menu → **Add to Home screen** / **Install app**.
- **iPhone (Safari):** open the URL, tap the Share icon → **Add to Home Screen**.

Once installed it opens full-screen with its own icon, no browser bar — it behaves like a native app, though it's technically a installed web app (a PWA), not something from the App/Play Store.

## About the data
Each device stores its own inventory in that browser (nothing is sent to a server). To move data between devices, use **Audit → Backup & restore**: download a `.json` backup on one device, then use "Restore from backup" on another. If you outgrow this later and want everyone to see the same live data automatically, that needs a small shared database (e.g. Firebase) added in — happy to help with that when you're ready.

## Updating the app later
Whenever you want to change something, edit `index.html` (or ask Claude to), re-upload the changed file(s) to the same GitHub repo, and it redeploys automatically within a minute or two.
