# Deploying Fair Finder — fresh branch to GitHub Pages

Build 2026.07.14 (shown at the bottom of More → About, so you can verify what's live).

## Files to commit
`index.html` · `sw.js` · `README.md` · `SETUP.md` · `LICENSE` · `.gitignore`
(`oregon-country-fair-map.html` is an identical named copy — optional.)
Keep `index.html` and `sw.js` side by side at the branch root.

## Fresh branch
```bash
cd your-repo
git checkout --orphan deploy-2026-07     # clean branch, no history
git rm -rf . 2>/dev/null
# copy the files above into the repo folder, then:
git add index.html sw.js README.md SETUP.md LICENSE .gitignore
git commit -m "Fair Finder build 2026.07.14"
git push -u origin deploy-2026-07
```

## Point Pages at it
Repo **Settings → Pages → Deploy from a branch** → branch `deploy-2026-07`, folder `/ (root)`.
Live at `https://<username>.github.io/<repo>/` in a minute or two.

## Verify the rollout
1. Open the URL → **More → About** → confirm "Build 2026.07.14".
2. If you see an older build: the service worker serves cache-first — close the tab, reopen (second load picks up the new version). The new `sw.js` cache name also purges all old caches automatically.
3. Smoke test: More → Simulation mode ON → Explore → any stage → Navigate here → the icon should ride the gold line around the Eight without leaving the paths.
