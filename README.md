# OpenRoad 🛣️

A CarPlay-like in-car experience delivered via Google Cast. Your phone casts to any Chromecast-compatible display, and the full car UI runs on the screen.

---

## Files

| File | Purpose |
|------|---------|
| `index.html` | **Sender** — loaded on your phone, has the Cast button |
| `receiver.html` | **Receiver** — loaded by the Chromecast on the car screen |

---

## Deployment (GitHub Pages)

1. Create a new GitHub repo (e.g. `openroad`)
2. Drop both files in the root
3. Go to **Settings → Pages → Source → main branch → / (root)** → Save
4. Your site will be at: `https://h-harder.github.io/openroad/`

The receiver URL you need to register is:
```
https://h-harder.github.io/openroad/receiver.html
```

---

## Google Cast App Registration ⚡

This is the most important step:

1. Go to: https://cast.google.com/publish
2. Sign in with your Google account
3. Click **Add New Application** → **Custom Receiver**
4. Set the **Receiver Application URL** to your `receiver.html` URL above
5. Your App ID should be **2A0E8A42** (already coded into both files)
6. Under **Devices**, add your Chromecast's serial number for testing (it needs to be registered while in development mode)

> ⚠️ New Cast apps go through a review/approval process. During development, you must register your Chromecast device in the developer console so it can load your unpublished receiver.

---

## How It Works

```
[Phone running index.html]
       │
       │  Cast SDK (App ID: 2A0E8A42)
       ▼
[Chromecast device on car screen]
       │
       │  Loads receiver.html from your GitHub Pages URL
       ▼
[Full OpenRoad UI on car display]
```

Once casting starts:
- The car screen shows the full OpenRoad UI
- Your phone screen can go to sleep — the session stays active
- The car touchscreen controls everything

---

## Features

- 🗺️ **Maps** — OpenStreetMap (free, no API key needed) with search. Can switch to Google Maps in Settings.
- 🎵 **Spotify** — Embedded Spotify Web Player (requires Spotify account)
- 🌐 **Browser** — Full iframe browser with address bar, back/forward, quick links
- 📞 **Phone** — Dialpad with `tel:` link support
- ▶️ **Media** — YouTube embed with search
- ⛅ **Weather** — Live weather via Open-Meteo API (free, no key needed)
- ⚙️ **Settings** — Dark mode, map provider, navigation voice toggle

---

## Notes

- The Cast SDK only works in **Chrome/Chromium** on the sender (phone). Safari/Firefox don't support it.
- `index.html` must be served over **HTTPS** for the Cast SDK to work. GitHub Pages serves HTTPS automatically.
- The receiver runs in a Chromecast browser (Chromium-based), so standard web features work.
