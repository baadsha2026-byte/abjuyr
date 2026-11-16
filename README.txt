# shad0w.x7 PWA

This folder contains the PWA-converted version of your original dashboard.

## Included
- `index.html` — original dashboard with PWA metadata and install control
- `manifest.webmanifest` — app name, icon, standalone display and launch settings
- `service-worker.js` — offline app-shell caching
- `icons/` — generated PNG sizes from your supplied icon

## Publish / enable installation
A PWA must be served from **HTTPS** (or localhost for testing). It will not install as a PWA by opening `index.html` directly from a file manager.

1. Upload the contents of this folder to the root of an HTTPS website/static host.
2. Open the HTTPS site in Chrome or Safari while online once, so the service worker can cache the app shell.
3. Android/Chrome: use the page's **INSTALL APP** button when offered, or browser menu → Install app / Add to Home screen.
4. iPhone/iPad: open the site in Safari → Share → Add to Home Screen.

## Offline and saved data
The service worker caches the app shell and icon files for offline launch after the first successful online visit. Existing dashboard data remains in browser `localStorage`; it is not uploaded or migrated by this PWA conversion. Browser storage can still be cleared by the device/browser, so keep regular backups if the dashboard contains important records.

## Notes
- The installed app opens in standalone mode without normal browser chrome.
- True fullscreen behavior is controlled by the operating system/browser; the manifest requests standalone with fullscreen as a display override.
- Updates are served from the same HTTPS origin. The service worker activates a new cache version when its cache name changes.
