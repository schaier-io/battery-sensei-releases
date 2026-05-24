<div align="center">

# Battery Sensei

**電池先生** · the quiet macOS menu-bar app that watches your MacBook battery

[**Download for macOS**](https://battery-sensei.app/download/latest) · [Website](https://battery-sensei.app) · [Report an issue](https://github.com/schaier-io/battery-sensei-releases/issues/new/choose) · [Email](mailto:sandro@schaier.io)

</div>

---

This repository hosts the **public, signed release artifacts** for Battery Sensei. The source lives in a separate, private repo; only the shipped binaries are open here, so Sparkle (the in-app updater) and people who prefer GitHub Releases have a stable, mirrorable home.

## Get the app

| You want | Go here |
| --- | --- |
| The latest stable build | [`battery-sensei.app/download/latest`](https://battery-sensei.app/download/latest) |
| A specific version | [`battery-sensei.app/download/1.2.3`](https://battery-sensei.app/download/1.2.3) |
| Browse the version history | [Releases tab](https://github.com/schaier-io/battery-sensei-releases/releases) |
| Verify the Sparkle feed | [`battery-sensei.app/appcast.xml`](https://battery-sensei.app/appcast.xml) |

Each release ships one asset: `Battery-Sensei.zip`. Apple-notarized. Hardened runtime. Universal binary (Apple Silicon + Intel). No installer, no helper daemon, no login.

> First time? You don't need this repo at all. Grab the app from [battery-sensei.app](https://battery-sensei.app) and the in-app updater handles every release after that.

## Issues, requests, and support

The product roadmap and bug triage happen **here**, in this repo, in public.

- 🐞 **Bug?** [Open a bug report.](https://github.com/schaier-io/battery-sensei-releases/issues/new?template=bug_report.yml) The template asks for the few specifics that almost always unblock a fix.
- 💡 **Feature idea?** [Open a feature request.](https://github.com/schaier-io/battery-sensei-releases/issues/new?template=feature_request.yml) Vote with a 👍 on existing ones to bump priority.
- 🔒 **Security?** Email <sandro@schaier.io> directly, do not open a public issue.
- 💌 **Billing, refunds, license keys, anything private?** [Contact form on the site](https://battery-sensei.app/#contact) or <sandro@schaier.io>.

Every public issue gets a first reply within ~48 hours on weekdays. If a fix is small, it tends to ship in the next point release within the week.

## Sparkle (auto-updates)

```
https://battery-sensei.app/appcast.xml
```

The feed is EdDSA-signed; the public key is embedded in the app bundle. The XML lives on the marketing site so it can be cached aggressively at the edge. The binaries it points to are served straight from this repo's Releases, which means free, unmetered bandwidth and a verifiable URL anyone can audit.

## What is *not* in this repo

A short list, in the spirit of saying it out loud:

- **The source code.** Battery Sensei is a paid product; the source stays private. This is intentional, not an oversight.
- **An installer script.** The `.zip` extracts to `Battery-Sensei.app`. Drag it to `/Applications`. That's the install.
- **Documentation.** Lives at [battery-sensei.app](https://battery-sensei.app) (overview, FAQ, pricing, comparison to AlDente).
- **Telemetry.** None. The app never phones home, including from this repo's binaries.

## Quick facts

- macOS 13 Ventura or later · Apple Silicon and Intel
- 5-day free trial · no card · no nag when it ends
- $3.99 USD once · lifetime license · every Mac you own
- 14-day refund, no questions
- English, German, Spanish, French, Japanese

## License

The binaries published here are © Sandro Schaier and distributed under Battery Sensei's end-user license (see [Pricing & EULA](https://battery-sensei.app/pricing.md)). Hosting them in a public GitHub repo grants no source-code rights. You may mirror the `.zip` for archival use; please do not redistribute it as your own.

---

<div align="center">

Made by a MacBook owner, for MacBook owners.

<sub>静かに、電池に寄り添う。</sub>

</div>
