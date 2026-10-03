# open.hallspeak.app

The redirect page behind `https://open.hallspeak.app?url=<listener-url>`.

A listener page on any Hallspeak domain offers "Open in the app" with a link to this
domain. That single link does two jobs:

- **App installed** — the domain is registered as a universal / app link, so the OS hands
  the URL to the Hallspeak app, which opens the channel. This page never loads.
- **App not installed** — the browser loads this page. It detects the platform from the
  user agent, shows "Opening the App Store…" or "Opening Google Play…" for about a second,
  then redirects to the store listing. If the platform cannot be determined it shows
  "Download the mobile app" with both official store badges instead.

## Store and signing identifiers

- `index.html` — `APP_STORE_URL` is the App Store listing (Apple ID `6816664866`) and
  `PLAY_STORE_URL` the Play listing (`app.hallspeak.mobile`). Until an app is public, its
  listing is visible only to its testers.
- `.well-known/apple-app-site-association` — Apple Developer Team ID `DB4BLJB7ZB`.
- `.well-known/assetlinks.json` — two fingerprints: the Play app signing key (Play Console →
  Protect with Play → Play app signing), which signs every install from Play, and the
  upload key held by EAS, which signs builds installed outside Play.

The fingerprints belong to the signing keys, not to a build: they stay the same across
releases. Add a new fingerprint alongside the old one only if a key is rotated or builds
start shipping signed with a different key.
