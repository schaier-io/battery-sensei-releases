# Battery Sensei — Releases

Public release artifacts for **Battery Sensei**, a quiet macOS menu-bar
battery utility.

Source code lives in a private repo; this repo holds the signed `.zip`
artifacts that Sparkle (the in-app updater) downloads.

→ **[battery-sensei.app](https://battery-sensei.app)** — site, screenshots, FAQ, download.

## Get the app

- **Latest stable**: <https://battery-sensei.app/download/latest>
- **Specific version**: <https://battery-sensei.app/download/1.2.3>
- **Release history**: [Releases](https://github.com/schaier-io/battery-sensei-releases/releases)

Each release ships a single asset: `Battery-Sensei.zip` (notarized, hardened
runtime, Apple Silicon + Intel universal). Already-installed copies update
themselves through Sparkle; no need to re-download.

## Sparkle appcast

```text
https://battery-sensei.app/appcast.xml
```

EdDSA-signed; the public key ships inside the app bundle. The XML is hosted
by the marketing site (it's tiny); the binaries are served from this repo
(unmetered GitHub Releases bandwidth).

## What you won't find here

- Source code — private.
- Issue tracker — please use [battery-sensei.app](https://battery-sensei.app)
  contact links or email <sandro@schaier.io>.
- Documentation — see the site.

## License

The packaged binaries are © Sandro Schaier. Their inclusion in this repo
does not grant a source-code license. The site spells out the EULA + refund
policy in the FAQ.
