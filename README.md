# SmartMemo

> **SmartMemo is a generic, technology-neutral, on-device Android
> automation, accessibility, and note-taking utility.**
>
> It is not a chat-recorder, not an anti-recall tool, not a vendor
> hack, and not a cloud service. It is a blank notebook with
> well-engineered blank pages.
>
> **Author / Maintainer: `hannanlsa`**
> **License: [GPL-3.0](./LICENSE)**

---

## What is SmartMemo?

SmartMemo is an Android application that:

1. Listens to **Android Accessibility events** from apps you have
   explicitly associated with the service, and stores the text
   content locally.
2. Listens to **microphone audio** (and, where the user has
   authorised it, accessibility media streams) on the device, and
   stores the audio locally.
3. Runs **on-device speech-to-text inference** (a Whisper-class
   model bundled with the app) to produce a text transcript
   locally.
4. Aligns the captured text and the transcript on a single local
   timeline.
5. Lets you search, export, and delete everything — locally, with
   no network involvement.

The shipped product is **completely generic**: it does not know
about, hard-code, or specifically interact with any named third-party
application. You, the user, decide which apps (if any) to associate.

## Why does this exist?

Many people have legitimate, everyday reasons to want a private,
on-device note-taking helper that:

- Captures spoken words from a phone call they're on, in a
  jurisdiction that allows it
- Transcribes a meeting they're attending, for their own
  reference
- Records a personal voice memo
- Helps them remember a sequence of tasks across multiple apps

SmartMemo is built for those use cases. It is built with the
deliberate constraint that **it cannot be used to attack a specific
third-party product**, because the design of the product is to
not know about any specific third-party product.

## What makes it safe (for you, the user)?

- **No `INTERNET` permission.** The app cannot send data anywhere.
  A packet capture will record zero outbound bytes.
- **No analytics, no crash reporter, no telemetry.**
- **No donation, no payment, no premium tier.** There is no
  financial infrastructure to abuse, no commercial signal, and
  no entity with a financial interest in the data.
- **Auditable source code** under GPL-3.0. Anyone can read it.
- **Local-first storage.** All data lives in the app's private
  sandbox. Uninstall = erase.

## What makes it safe (for us, the maintainer)?

We follow a strict "technology-neutrality" policy:

- The shipped code contains **no hard-coded reference** to any
  named third-party application.
- We **reject** any pull request that would re-introduce such
  a reference.
- We **reject** any pull request that would add network egress,
  telemetry, or remote configuration.
- We **reject** any pull request that adds payment, donation, or
  premium-tier infrastructure.
- We **reject** any pull request that contains reverse-engineered
  code from a third-party proprietary product.

See [`LEGAL.md`](./LEGAL.md) and [`THREAT_MODEL.md`](./THREAT_MODEL.md)
for the full reasoning.

## Status

**Early development.** The repository is being prepared with the
governance, licensing, and contributor-policy documents first. The
actual implementation will follow after the legal posture is
stable.

A public roadmap will be added here once the first source code is
merged.

## Project layout

```
SmartMemo/
├── LICENSE                  # GPL-3.0
├── NOTICE                   # Third-party attributions, no-trademark-licence
├── README.md                # This file
├── DISCLAIMER.md            # No warranty, end-user responsibility
├── LEGAL.md                 # Legal posture, responsibility allocation
├── CLA.md                   # Individual contributor licence agreement
├── CONTRIBUTING.md          # How to contribute, what is / is not accepted
├── CODE_OF_CONDUCT.md       # Community standards
├── SECURITY.md              # Vulnerability disclosure
├── THREAT_MODEL.md          # Threats the design resists / does not resist
└── .github/
    ├── ISSUE_TEMPLATE/      # Bug, feature, question, legal-notice
    └── PULL_REQUEST_TEMPLATE.md
```

## Reading order for newcomers

1. `README.md` (this file)
2. `DISCLAIMER.md`
3. `LEGAL.md`
4. `THREAT_MODEL.md`
5. `CONTRIBUTING.md` + `CLA.md`
6. `CODE_OF_CONDUCT.md`
7. `SECURITY.md`

## License

This project is licensed under the **GNU General Public License
v3.0** (GPL-3.0). See [`LICENSE`](./LICENSE) for the full text.

The governance documents (`DISCLAIMER.md`, `LEGAL.md`,
`THREAT_MODEL.md`, `CODE_OF_CONDUCT.md`) are made available under
GPL-3.0 as well, for consistency with the rest of the repository.

---

*Project: SmartMemo. Maintainer: `hannanlsa`.*
*Last updated: 2026-06-18.*
