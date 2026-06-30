# 🎪 OCF Fair Map

An offline, installable pocket guide to the **Oregon Country Fair** (Veneta, OR · July 10–12, 2026). One self-contained web app: the real grounds map, a searchable event schedule, GPS navigation, custom pins, and favorites — all running on the phone with **no signal required**.

> Unofficial / fan-made. Built for finding your way (and your friends' camp) when the cell service drops out in the woods.

---

## ✨ Features

- **Full grounds map** — the north-up 2026 Peach Pit map with smooth pan / pinch-zoom.
- **150 mapped places** — every stage, neighborhood, service, family area and food booth pinned to its real grid cell (rows A–N, columns 1–9).
- **468-vendor craft & artisan directory** — searchable by name, category, and booth number.
- **Search & filter** across places and vendors.
- **GPS locate & voice navigation** — shows where you are and gives spoken walking directions (in a mellow "the Dude" narration voice), with a compass arrow and live distance. Optional 2-point GPS calibration for the hand-drawn map.
- **Custom pins** — drop and name your own spots (car, camp, meet-up) and navigate back to them.
- **Favorites** — star any place; favorites + your pins live in one **Saved** tab.
- **Event schedule** — all 317 acts across the three days, searchable, with **reminders** that alert you with enough lead time to walk there, plus a navigate-on-alert.
- **Themes** — Light / Dark / Psychedelic (with an animated map), full-screen mode, and a selectable narration voice.
- **Installable PWA** — Add to Home Screen for a full-screen, icon-on-the-home-screen app.
- **Fully offline & local** — pins, favorites, reminders and settings are saved on the device; no accounts, no servers, no tracking.

---

## 📁 What's in this repo

| File | Purpose |
|------|---------|
| `oregon-country-fair-map.html` | The entire app — map image, data, styles and code, all inline |
| `sw.js` | Service worker for guaranteed offline caching |
| `SETUP.md` | Hosting & install walkthrough with a test checklist |
| `README.md` | This file |

The HTML is self-contained (the base map and all schedule/vendor data are embedded), so the only moving parts are these two files. **Keep `sw.js` in the same folder as the HTML** — the page registers it from its own directory.

---

## 🚀 Host it

A service worker and GPS both require an `https://` link, so host the folder rather than opening the file directly.

**Option A — GitHub Pages (free, straight from this repo)**
1. Push these files to the repo.
2. Repo **Settings → Pages → Build and deployment → Deploy from a branch**, pick `main` / root.
3. Your app is live at `https://<username>.github.io/<repo>/oregon-country-fair-map.html`.
4. (Optional) rename the HTML to `index.html` so the URL is just the repo root.

**Option B — drag-and-drop**
- [Netlify Drop](https://app.netlify.com/drop) or [tiiny.host](https://tiiny.host) — drop **both** files in together and copy the link.

---

## 📱 Install on a phone

1. Open the hosted link **once with signal** so the service worker caches everything.
2. **Share → Add to Home Screen** (it installs as "OCF Map" with its own icon, full-screen).
3. After that it works in **airplane mode** at the fair — map, schedule, navigation, pins and favorites are all cached on-device.

---

## 🔒 Privacy & security

- No accounts, analytics, trackers, or third-party scripts. The only external resource is Google Fonts, which degrades gracefully offline.
- A strict **Content-Security-Policy** prevents the app from loading external code or sending data anywhere.
- Location is used only on the device for the map and navigation — it never leaves the phone.
- All saved data lives in the browser's local storage; clearing site data erases your pins, favorites and reminders.

---

## 🛠️ Tech notes

- Vanilla HTML / CSS / JavaScript — no build step, no framework, no dependencies to install.
- SVG map with pan/zoom; the base map is an embedded image stitched and rotated north-up from the official Peach Pit.
- Places are positioned by the Peach Pit's printed grid; the craft directory is listed by booth number (find the booth on the base map).
- GPS → map placement uses a similarity transform refined by optional 2-point calibration, since the map is illustrated rather than to-scale.
- To edit, open `oregon-country-fair-map.html` in any editor — everything is inline.

---

## ⚠️ Disclaimer

This is an unofficial guide. Always confirm showtimes and locations against the official **2026 Peach Pit**. The "you are here" dot is approximate on a hand-drawn map — use the calibration tool for best accuracy.

---

## 📜 Credits & license

**Application development by Josh Hughes** — [jhughesgraphics@gmail.com](mailto:jhughesgraphics@gmail.com)

Base map & schedule data © their respective owners: cartography by **McKenzie Maps & PittsWebb / OCF Cartography Crew**, sourced from the **2026 Oregon Country Fair Peach Pit**. Map and fair data are used here for a personal, non-commercial fan project and are **not** licensed for redistribution.

The application code is © Josh Hughes. If you want others to reuse the code, add a `LICENSE` file (e.g. MIT) — but note the embedded map/data are not yours to relicense.

*Oregon Country Fair is a trademark of its respective owner. This project is not affiliated with or endorsed by the Oregon Country Fair.*
