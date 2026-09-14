# open.linguacast.app

The redirect page behind `https://open.linguacast.app?url=<listener-url>`.

A listener page on any LinguaCast domain offers "Open in the app" with a link to this
domain. That single link does two jobs:

- **App installed** — the domain is registered as a universal / app link, so the OS hands
  the URL to the LinguaCast app, which opens the channel. This page never loads.
- **App not installed** — the browser loads this page. It detects the platform from the
  user agent, shows "Opening the App Store…" or "Opening Google Play…" for about a second,
  then redirects to the store listing. If the platform cannot be determined it shows
  "Download the mobile app" with both official store badges instead.
