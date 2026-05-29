<div align="center">

# Battery Sensei

**電池先生** · signed macOS release artifacts, served from GitHub

[**Download for macOS**](https://battery-sensei.app/download/latest) · [Website](https://battery-sensei.app) · [Report an issue](https://github.com/schaier-io/battery-sensei-releases/issues/new/choose) · [Email](mailto:sandro@schaier.io)

</div>

---

This repository holds the public, signed release artifacts for Battery Sensei. The source lives in a separate private repo; only the shipped binaries are open here. Two reasons. Sparkle (the in-app updater) gets a stable, mirrorable URL. And anyone can verify the exact bytes Apple notarized before installing.

> First time? You don't need this repo. Grab the app from [battery-sensei.app](https://battery-sensei.app) and Sparkle handles every release after that.

## Get the app

| You want | Go here |
| --- | --- |
| Latest stable build | [`battery-sensei.app/download/latest`](https://battery-sensei.app/download/latest) |
| A specific version | [`battery-sensei.app/download/1.2.3`](https://battery-sensei.app/download/1.2.3) |
| Browse version history | [Releases tab](https://github.com/schaier-io/battery-sensei-releases/releases) |
| Sparkle feed (signed XML) | [`battery-sensei.app/appcast.xml`](https://battery-sensei.app/appcast.xml) |
| Raw asset for a given tag | `github.com/schaier-io/battery-sensei-releases/releases/download/v1.2.3/Battery-Sensei.zip` |

Each release ships one asset: `Battery-Sensei.zip`. Apple notarized. Hardened runtime. Universal 2 binary (Apple Silicon and Intel). No installer, no helper daemon, no login item.

### Scriptable download

```sh
# Always-current stable build
curl -L -o Battery-Sensei.zip https://battery-sensei.app/download/latest

# Pin to a specific version
curl -L -o Battery-Sensei.zip https://battery-sensei.app/download/1.2.3
```

The `/download/...` URLs are stable; they 302-redirect to the matching GitHub release asset. Mirror or proxy them as you wish.

## Verify what you downloaded

Before installing anything from the internet, even from us, you can confirm the binary was signed by the same Developer ID that Apple notarized:

```sh
# 1. Unzip and move to /Applications (or wherever you want)
unzip Battery-Sensei.zip && mv "Battery Sensei.app" /Applications/

# 2. Confirm the code signature
codesign --verify --deep --strict --verbose=2 "/Applications/Battery Sensei.app"

# 3. Confirm Gatekeeper assessment (notarization ticket attached + accepted)
spctl --assess --type execute --verbose=2 "/Applications/Battery Sensei.app"

# 4. Read the Developer ID off the signature
codesign -dvv "/Applications/Battery Sensei.app" 2>&1 | grep "Authority="
```

Expected `Authority=` chain ends in `Developer ID Application: Sandro Schaier (...)`. Anything else and the bytes are not what we shipped, please file an issue.

## Sparkle (auto-updates)

```
https://battery-sensei.app/appcast.xml
```

The feed is EdDSA-signed; the public key is embedded in the app bundle (`SUPublicEDKey` in `Info.plist`). Each `<item>` carries the signature and length as Sparkle expects:

```xml
<item>
  <title>Battery Sensei 1.4.2</title>
  <sparkle:version>1.4.2</sparkle:version>
  <enclosure
    url="https://github.com/schaier-io/battery-sensei-releases/releases/download/v1.4.2/Battery-Sensei.zip"
    length="9437184"
    type="application/octet-stream"
    sparkle:edSignature="…" />
</item>
```

The XML lives on the marketing site so it can be cached aggressively at the edge. The binaries it points to are served from this repo's Releases, which means free, unmetered bandwidth and a URL anyone can audit.

If you fork the app, replace `SUPublicEDKey` with your own and point Sparkle at your own feed; ours will refuse to update something it didn't sign.

## Issues, requests, and support

The product roadmap and bug triage happen here, in this repo, in public.

- 🐞 **Bug?** [Open a bug report.](https://github.com/schaier-io/battery-sensei-releases/issues/new?template=bug_report.yml) The template asks for the few specifics that almost always unblock a fix (macOS version, chip family, what you tried, what you saw).
- 💡 **Feature idea?** [Open a feature request.](https://github.com/schaier-io/battery-sensei-releases/issues/new?template=feature_request.yml) Vote with a 👍 on existing ones to bump priority.
- 🔒 **Security?** Email <sandro@schaier.io> directly. Please don't open a public issue first.
- 💌 **Billing, refunds, license keys, anything private?** Use the [contact form](https://battery-sensei.app/#contact) or <sandro@schaier.io>.

Every public issue gets a first reply within about 48 hours on weekdays. Small fixes usually ship in the next point release within the week.

## What is *not* in this repo

- **The source code.** Battery Sensei is a paid product; the source stays private. This is intentional.
- **An installer script.** The `.zip` extracts to `Battery Sensei.app`. Drag it to `/Applications`. That's the install.
- **Documentation.** Lives at [battery-sensei.app](https://battery-sensei.app): overview, FAQ, pricing, comparison with AlDente.
- **Telemetry.** None. The app does not phone home, including from the binaries published here.
- **Helper daemons, kernel extensions, LaunchAgents.** None of those either.

## Build & runtime facts

- macOS 13 Ventura or later
- Apple Silicon and Intel (Universal 2)
- AppKit + SwiftUI, no Electron, no web wrappers
- 5-day free trial, no card, no nag when it ends
- $3.99 USD once for Lifetime (up to 3 Macs you own), or a Yearly Patron tier (up to 5 Macs while subscribed)
- 14-day refund, no questions
- English, Deutsch, Español, Français, 日本語

## License

The binaries published here are © Sandro Schaier and distributed under Battery Sensei's end-user license (see [Pricing & EULA](https://battery-sensei.app/pricing)). Hosting them in a public GitHub repo grants no source-code rights. You may mirror the `.zip` for archival use; please don't redistribute it as your own.

---

<div align="center">

Made by a MacBook owner, for MacBook owners.

<sub>静かに、電池に寄り添う。</sub>

</div>
