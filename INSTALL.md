# Škoda Dashboard — PWA Install Guide

## What you have
A Progressive Web App (PWA) version of your Škoda Monthly Performance Dashboard v12.4. Install it on your phone and it behaves like a native app — full screen, home screen icon, offline access.

## Files in this package
```
Skoda_PWA_v13/
├── index.html          Your full v12.4 dashboard (with PWA hooks injected)
├── manifest.json       App name, Škoda theme, icons
├── service-worker.js   Offline cache
├── icon-192.png        Home screen icon (Android)
├── icon-512.png        Splash screen icon
└── INSTALL.md          This file
```

## STEP 1 — Host the files
Upload the whole folder to any of these:

**Option A: SharePoint (Omnicom-friendly)**
1. Create a SharePoint site or use existing Skoda site
2. Upload the folder to Site Assets or Documents
3. Enable "Anyone with the link can view"
4. Copy the URL to `index.html`

**Option B: GitHub Pages (free, fastest)**
1. Create a new public repo, e.g. `skoda-dashboard`
2. Upload all files to root
3. Settings → Pages → Deploy from branch → main
4. Your URL: `https://<username>.github.io/skoda-dashboard/`

**Option C: Azure Static Web Apps** (enterprise)

## STEP 2 — Install on Android
1. Open the hosted URL in **Chrome**
2. Wait 5–10 seconds
3. Chrome bar shows **"Install app"** OR bottom banner appears: **📲 Install this dashboard as an app**
4. Tap **Install**
5. Icon appears on home screen

## STEP 3 — Install on iPhone
1. Open the hosted URL in **Safari** (not Chrome)
2. Bottom banner appears: **📲 Install: tap Share → Add to Home Screen**
3. Tap the **Share** icon (square with arrow up)
4. Scroll down → tap **Add to Home Screen**
5. Tap **Add**
6. Icon appears on home screen

## STEP 4 — Verify install
Open the app from the home screen icon. Check:
- ✅ No browser address bar visible
- ✅ Full-screen Škoda green theme
- ✅ Month toggle June/July works
- ✅ All filters work (State, Source, Sub Source, Ach%)
- ✅ Sticky State + City columns work
- ✅ Charts render
- ✅ Turn Airplane Mode ON → reopen → still loads (offline cache)

## Daily refresh (client-facing)
The client keeps the app installed forever. When you have new data:
1. Regenerate `index.html` with fresh numbers
2. Upload to the same hosting location (overwrite)
3. Client's app auto-updates within 24 hours (or immediately after a manual refresh)

## Requirements
- HTTPS (required for PWA install)
- Chrome 76+ on Android
- Safari 11+ on iOS
- Modern browsers on desktop for testing

## Troubleshooting
| Issue | Fix |
|---|---|
| "Install" not showing on Android | Wait 30 sec, ensure HTTPS, check `manifest.json` loads |
| iOS not showing "Add to Home Screen" | Must use Safari, not Chrome |
| Icon looks blurry | Icons are 192px + 512px, PNG — should be crisp |
| Offline doesn't work | Service worker only activates after first successful load |
| Chart doesn't render offline | Chart.js is CDN-cached; needs one online load first |

## Support
For dashboard corrections/discrepancies: **karan.patel@omc.com**
