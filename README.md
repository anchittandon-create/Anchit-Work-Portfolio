# Anchit Tandon — Portfolio

Personal portfolio for **Anchit Tandon**, Senior Product Manager at Times Internet.
Ships as **web (any device + TV)**, **installable PWA**, and **native iOS + Android** via Capacitor.

**Live:** [anchits-work.vercel.app](https://anchits-work.vercel.app)

---

## What's in this repo

```
.
├── index.html              # The whole site — single-file static, no build step
├── manifest.json           # PWA manifest (installable on iOS/Android/desktop)
├── sw.js                   # Service worker — offline cache for the shell
├── icons/                  # PWA + favicon + apple-touch + iOS splash
├── capacitor.config.json   # Native app config (bundle id, splash, status bar)
├── package.json            # Capacitor dependencies + helper scripts
├── vercel.json             # Vercel static-host config (security headers)
├── DEPLOY.md               # Web + native deploy walkthroughs
└── README.md
```

No framework, no bundler. The site is a single `index.html` (~88 KB) with embedded CSS + JS.
Capacitor wraps that same `index.html` into native iOS and Android apps.

## Design system

- **Palette:** Cream (`#FBF5EC`) + electric coral (`#FF4D1F`) + mint (`#00B584`). Inky-black ink. Full dark mode (`#0F0D0A` background).
- **Type:** Fraunces (display, variable axes — uses `SOFT` + `WONK`), Inter (body), JetBrains Mono (labels).
- **Layout:** Top nav + scrolling ticker. Big serif hero. Section-paneled content. IntersectionObserver-driven scroll reveals.
- **Responsive:** Phone → tablet → laptop → 4K TV. Container scales up to 1920px on TV-class screens; type fluids via `clamp()`.

## Running locally

```bash
# 1. Install Capacitor deps (only needed for native builds)
npm install

# 2. Serve the site locally (any port)
npm run dev          # → http://localhost:5173
# or just open index.html in a browser
```

## Native apps — iOS + Android via Capacitor

> The container that generates this repo doesn't have Xcode or Android Studio.
> You'll do the final steps on your own machine (macOS for iOS, any OS for Android).

### One-time setup

```bash
# 1. Install dependencies (Node 18+)
npm install

# 2. Add native platforms (one-time per platform)
npx cap add ios          # generates the ios/ folder (needs macOS + Xcode)
npx cap add android      # generates the android/ folder (needs Android Studio)

# 3. Sync the web assets into the native projects
npx cap sync
```

### Every time you change web code

```bash
npx cap sync             # copies index.html + assets into iOS + Android projects
```

### iOS build & submit (App Store)

```bash
npx cap open ios         # opens Xcode
```

In Xcode:
1. Select the **App** target → Signing & Capabilities → set your **Team** (needs Apple Developer account, $99/yr)
2. Bundle ID is preset to `com.anchittandon.portfolio` — change in `capacitor.config.json` if needed
3. Bump version + build number under General → Identity
4. **Product → Archive** → upload to App Store Connect
5. Submit for review at [appstoreconnect.apple.com](https://appstoreconnect.apple.com)

**⚠️ Apple Review caveat:** Apple often rejects portfolio sites wrapped as apps under Guideline **4.2 — Minimum Functionality**. To strengthen the case:
- The PWA layer adds offline mode + share target + app shortcuts ✓
- Consider adding native features before submitting: push notifications, Siri shortcuts, share extensions, or a "contact me" haptic
- Write a clear App Review note explaining how it differs from the website (e.g. offline access, native share, home-screen presence)

### Android build & submit (Play Store)

```bash
npx cap open android     # opens Android Studio
```

In Android Studio:
1. Wait for Gradle sync
2. **Build → Generate Signed Bundle / APK** → create a keystore (save it safely — you need it for every future update)
3. Sign with your keystore → produces a `.aab` file
4. Upload to [play.google.com/console](https://play.google.com/console) (needs Google Play account, $25 one-time)
5. Fill out store listing → submit for review

Google's review is faster and more lenient than Apple's. PWA-style wrappers are generally fine.

### What you'll need

| Platform | Required | Cost |
|----------|----------|------|
| iOS | macOS + Xcode + Apple Developer | $99/yr |
| Android | Android Studio (any OS) + Google Play Console | $25 one-time |
| App icons | Already generated in `icons/` | — |
| Splash screen | `icons/splash-2048x2732.png` (regenerate at higher resolution if needed) | — |

## Web deploy (Vercel)

See [`DEPLOY.md`](./DEPLOY.md). TL;DR:

```bash
vercel
```

## Project links

- **MusicGenAI** — [github](https://github.com/anchittandon-create/MusicGenAI) · [live](https://music-gen-ai-blue.vercel.app/)
- **Hey Yaara** — [github](https://github.com/anchittandon-create/hey-yaara) · [live](https://hey-yaara.vercel.app/)
- **AI TeleSuite** — [github](https://github.com/anchittandon-create/AI-TeleSuite) · [live](https://ai-tele-suite.vercel.app/)
- **TH+ LifeEngine** — [github](https://github.com/anchittandon-create/TH-LifeEngine) · [live](https://th-life-engine.vercel.app/)

## Contact

- [anchit.tandon@gmail.com](mailto:anchit.tandon@gmail.com)
- [LinkedIn](https://linkedin.com/in/anchit-tandon)
- [GitHub](https://github.com/anchittandon-create)
