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

## Before the apps are published

The site currently ships with placeholders. Replace them once the apps are in the stores:

- [ ] `index.html` — `APP_STORE_URL` and `PLAY_STORE_URL` point at unrelated apps; set them to
      the Hallspeak listings.
- [ ] `.well-known/apple-app-site-association` — replace `APPLE_TEAM_ID` with the Apple
      Developer Team ID (developer.apple.com → Membership).
- [ ] `.well-known/assetlinks.json` — replace `PLAY_APP_SIGNING_SHA256` with the app signing
      key certificate fingerprint (Play Console → Test and release → App integrity), and
      `UPLOAD_KEY_SHA256` with the upload/EAS key fingerprint (`eas credentials -p android`),
      or remove it if builds are only distributed through Play.

Until then universal / app links do not verify, so every link loads this page.

The fingerprints belong to the signing keys, not to a build: they stay the same across
releases. Add a new fingerprint alongside the old one only if a key is rotated or builds
start shipping signed with a different key.
