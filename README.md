# Stack Rush — PWA Game

## Files
- `index.html` — Full game (Home, Play, Shop, Leaderboard, Achievements)
- `manifest.json` — PWA manifest (display: fullscreen for Play Store)
- `sw.js` — Service Worker (offline play support)
- `icons/` — All required icon sizes (72→512px)

## Features
- ♾️ Infinite stacking gameplay
- 🏠 Home screen with stats tracking
- 🛒 Shop with 8 skins (coins earned in-game)
- 🏆 Local leaderboard
- ⭐ 8 Achievements system
- 🎨 Particle effects & combo system
- 📱 Fully responsive (mobile + desktop)
- ✈️ Offline play via Service Worker
- 🔑 One-tap/Space bar control
- ⏸ Pause menu
- 🎓 Skippable tutorial

## Publishing to Google Play Store (TWA Method)

### Step 1 — Host the game
Host on any HTTPS server (GitHub Pages is free):
1. Push folder to GitHub repo
2. Enable GitHub Pages → Settings → Pages → main branch

### Step 2 — Generate TWA with Bubblewrap
```bash
npm install -g @bubblewrap/cli
bubblewrap init --manifest https://YOUR_URL/manifest.json
bubblewrap build
```

### Step 3 — Sign & Upload
1. `bubblewrap build` generates `app-release-signed.apk`
2. Upload to Google Play Console → Create App → Internal Testing
3. Add `assetlinks.json` to your server (Bubblewrap generates this)

### Step 4 — Asset Links (required)
Create `/.well-known/assetlinks.json` on your HTTPS host:
```json
[{
  "relation": ["delegate_permission/common.handle_all_urls"],
  "target": {
    "namespace": "android_app",
    "package_name": "com.stackrush.game",
    "sha256_cert_fingerprints": ["YOUR_SIGNING_KEY_SHA256"]
  }
}]
```

## CrazyGames Compliance
- ✅ Tutorial is skippable
- ✅ Visual onboarding (no text walls)
- ✅ Consistent resolution & art style
- ✅ No Escape/Ctrl+W key conflicts
- ✅ Clear UI labels and goals
- ✅ Unique game name
- ✅ Responsive for all screen sizes
