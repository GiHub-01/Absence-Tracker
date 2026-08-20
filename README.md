<div align="center">

# 🗓️ Absent

**A minimal attendance tracker that only tracks what actually matters — the days you missed.**

No total-classes math. No percentages to maintain. Just courses, dates, and how many you can't afford to lose.

</div>

<br/>

## Why

Most attendance apps make you log *every single class, every single day*. This one doesn't.
You only interact with it on the days you're **absent** — pick a course, pick a date, done.
Everything else is out of your way.

<br/>

## ✨ Features

| | |
|---|---|
| 📊 **Dashboard overview** | See every course and its absence count at a glance, in one compact list |
| 📅 **Date-based logging** | Mark any specific date absent — today, or a date you forgot to log earlier |
| 👁️ **Per-course details, on demand** | Each course's full dated history and an unmark control are tucked behind a "Show dates & unmark" toggle on that course's own page — not shown until you ask for it |
| 📚 **Multiple semesters** | Keep each semester's courses and absences separate |
| 🔍 **Search & sort** | Find a course instantly, or sort by who's racking up the most absences |
| 🌙 **Real dark mode** | A properly designed dark palette, not an inverted one |
| 📴 **Works offline** | Installs like a native app and keeps working without signal |
| 🔐 **100% private** | Everything lives in your browser's local storage — nothing is ever sent to a server |
| ⏪ **Undo everything** | Every change shows a toast with one-tap undo, right after the action |
| ⬇️ **Export / import** | Back up or move your data as a plain JSON file, any time |

<br/>

## 🚀 Getting started

This is a static site — no build step, no dependencies to install.

```bash
python3 -m http.server 8000
# then open http://localhost:8000
```

That's it. Opening `index.html` directly in a browser also works, with one
caveat: offline mode and "Add to Home Screen" both require the app to be
served over `http(s)`, not opened as a local file — that's a browser security
rule, not something this app can work around.

<br/>

## 📦 What's in here

```
.
├── index.html               the entire app — UI, logic, and styling
├── manifest.webmanifest     PWA metadata (name, icons, how it launches)
├── sw.js                    service worker, for offline support
├── icons/                   app icons
├── LICENSE                  MIT
└── README.md                this file
```

No `node_modules`, no bundler, no build artifacts. React and Tailwind load
from a CDN and compile in the browser at page load. It's meant to stay this
simple.

<br/>

## 🎨 Design

- **Type** — [Space Grotesk](https://fonts.google.com/specimen/Space+Grotesk) for headings, [Inter](https://fonts.google.com/specimen/Inter) for body text, [JetBrains Mono](https://fonts.google.com/specimen/JetBrains+Mono) for numbers
- **Color system** — every color is a CSS variable in `:root` / `html.dark` near the top of `index.html`, so retheming is a find-and-replace, not a rewrite
- **Motion** — short, purposeful transitions only; respects `prefers-reduced-motion`

<br/>

## 🔒 Data & privacy

Your data never leaves your device. It's stored in `localStorage` under a
single versioned key. Imported files are validated and sanitized before
they're accepted, so a corrupted or hand-edited JSON file can't crash the app.

<br/>

## 📱 Turning this into a real Android app (.apk / Play Store)

This app is already TWA-ready — a valid manifest and service worker (both
already present) are the prerequisites. To get an actual installable `.apk`
or a Play Store listing, without rewriting any code:

1. Host this project somewhere with a clean root domain (Netlify is the
   easiest free option for this).
2. Run the hosted URL through [pwabuilder.com](https://www.pwabuilder.com)
   and generate an **Android (Trusted Web Activity)** package.
3. Fill in `.well-known/assetlinks.json` in this project with the values
   PWABuilder gives you, and make sure that file is deployed at your domain's
   root — this is what lets Android drop the browser address bar entirely.
4. Download the signed `.apk` (to sideload and test immediately) or `.aab`
   (to upload to Google Play, which needs a one-time $25 developer account).

No Android Studio required — PWABuilder builds and signs the package in the
cloud.

<br/>

## 📄 License

MIT — see [LICENSE](./LICENSE). Do whatever you want with it.

<div align="center">
<sub>Built for students who'd rather spend two seconds logging an absence than two minutes filling out a register.</sub>
</div>
