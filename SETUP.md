# OCF Fair Map — offline app (2 files)

Two files, kept **in the same folder**:
- `oregon-country-fair-map.html` — the app
- `sw.js` — the service worker that makes it work fully offline

Everything runs on the phone: no accounts, no server, no live data.

## Host it (required)
A service worker and GPS both need a real `https://` link, so host the folder (don't just open the file):
- **Netlify Drop** — https://app.netlify.com/drop → drag in BOTH files together
- **tiiny.host**, GitHub Pages, Cloudflare Pages, or Vercel also work

Keep both files at the same level (e.g. site root). The page registers `sw.js` from its own folder.

## Install on a phone
1. Open the link once **with signal** (so the service worker caches everything).
2. **Share → Add to Home Screen** — it installs as "OCF Map" with its own icon, full-screen.
3. After that first load it works in **airplane mode** at the fair: map, search, schedule, navigation, pins and favorites are all cached on-device.

## What's inside
- North-up Peach Pit map, 150 mapped places + 468-vendor directory, search
- **Locate** (GPS) + **voice navigation** (the Dude), optional 2-point GPS calibration in More
- **Custom pins** — drop & name your own (car, camp, meet-up); tap to navigate back
- **Favorites** — tap the star on any place; collected in the **Saved** tab with your pins
- Full **317-event schedule** with reminders/alerts (smart walk-time lead) + Preview
- Light / Dark / Psychedelic themes, full screen, selectable narration voice
- All data saved locally on the phone

## Security & efficiency notes
- A strict **Content-Security-Policy** is set: only the page's own inline code runs, the only external thing allowed is Google Fonts, and nothing can phone home.
- **no-referrer** policy; no third-party scripts, trackers, or network calls.
- No personal data leaves the device. Clearing the site/browser data erases saved pins, favorites and reminders.
- The service worker uses **stale-while-revalidate**: instant loads from cache, and when you re-upload an updated build it refreshes automatically on the next visit.

## Test checklist
- [ ] Open link, allow location → blue dot appears (tap **Locate**)
- [ ] Tap a place → **Navigate here** → you hear directions
- [ ] **More → Drop a pin** → tap the map → name it → shows on map and in **Saved**
- [ ] Open a place → **Save to favorites** → appears under **Saved → Favorites**
- [ ] **Events** → add a reminder → **Preview**
- [ ] Load once online, then **airplane mode + reload** → everything still works

## Calibrating GPS (recommended once, on-site)

The map is hand-drawn, so anchor it to reality: **More → Calibrate GPS**.

1. Tap **Locate** and let the dot settle for ~10 seconds.
2. Stand somewhere you can pinpoint (a stage, a gate, your booth) → **Add anchor at my location** → tap that exact spot on the map.
3. Repeat at a second spot **far from the first** — two anchors lock in scale and rotation. A third and fourth smooth out the map's hand-drawn distortion.

The panel shows fit quality (e.g. "±9 m across 3 anchors") and lets you delete any anchor. Anchors appear as numbered green dots. The app averages your recent GPS fixes (weighted by accuracy) when placing an anchor and refuses fixes worse than ~35 m, and your blue dot now shows a faint ring for current GPS accuracy.
