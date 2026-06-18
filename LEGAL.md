# Legal Position & Responsibility Allocation

> **This document describes the legal posture of the SmartMemo project, the
> allocation of responsibility between the author, contributors, and end-users,
> and the technical and procedural safeguards in place to keep the project on
> the safe side of applicable law.**
>
> **Author / Maintainer: `hannanlsa`.**
> **Last updated: 2026-06-18.**

---

## 1. Project Identity

| Item | Value |
|------|-------|
| Project name | SmartMemo |
| Repository | https://github.com/hannanlsa/SmartMemo |
| Author / Maintainer | `hannanlsa` |
| License | GNU General Public License v3.0 (GPL-3.0) |
| Default distribution channel | Source code on GitHub Releases |
| Default build flag | `INTERNET` permission **not declared** |
| Default business model | None. No payment, no donation, no ad, no tracking. |

## 2. Statement of Intent

SmartMemo is built and distributed as a **generic Android automation,
accessibility, and on-device AI utility**. Its design goals are:

1. To help users organise their own notes and personal context using only
   publicly documented Android system APIs.
2. To remain completely technology-neutral with respect to any third-party
   application. The shipped product contains **no hard-coded reference** to
   any specific commercial software package.
3. To operate **100% on-device** with no network egress, in order to remove
   any technical possibility of unauthorised data collection, transmission,
   or sale.
4. To be auditable: the source code is published in full under a strong
   copyleft licence (GPL-3.0) so that any third party can verify the absence
   of hidden backdoors or surveillance logic.

The author has no intent to facilitate, encourage, or enable:

- Reverse engineering of any third-party proprietary application
- Bypassing of any access-control, copy-protection, or DRM mechanism of any
  third-party application
- Violation of any third party's terms of service, intellectual property
  rights, or privacy rights
- Any use that would be unlawful in the user's jurisdiction

## 3. What SmartMemo Is, and Is Not

### 3.1 What it is

A standalone Android application that:

- Reads accessibility events (text content, focus state) from apps the user
  has explicitly associated with the service
- Captures audio from the device microphone and/or from accessibility media
  streams that the user has explicitly authorised
- Runs on-device speech-to-text inference using bundled open-source models
- Stores the resulting notes in a local SQLite database inside the app's
  private sandbox
- Renders, searches, and exports these notes to the user

### 3.2 What it is **not**

- Not a "WeChat hack", "DingTalk spy", or any "anti-recall" tool for any
  specific product. No such behaviour is implemented, and no such behaviour
  will be merged from external contributions.
- Not a key-logger, screen scraper for theft, or password exfiltration tool.
  The accessibility framework is used only for text-content capture from
  user-authorised sources, and never for credential field capture.
- Not a cloud service. There is no backend, no telemetry endpoint, no
  authentication server, no analytics SDK.
- Not a malware dropper or loader. The codebase is fully open and auditable.

## 4. Allocation of Responsibility

### 4.1 The author (`hannanlsa`) is responsible for:

- The shipped source code in the default `main` branch
- Maintaining the technical-neutrality boundary in the shipped code
- Reviewing and rejecting any pull request that would re-introduce
  application-specific or invasive functionality
- Maintaining the GPL-3.0 licence on all distributed binaries
- The accuracy of the public documentation (this file, `DISCLAIMER.md`,
  `README.md`, `THREAT_MODEL.md`)

### 4.2 Contributors are responsible for:

- The contents of their own pull requests
- The originality of submitted code (no third-party copyrighted code
  without compatible licensing)
- The legal compatibility of any dependency they introduce
- Signing the project CLA (see `CONTRIBUTING.md`)

### 4.3 End-users are responsible for:

- Their choice of which third-party applications to associate with
  SmartMemo
- The legal basis on which they capture, store, and process any
  communication that they are party to
- Compliance with the laws of their jurisdiction, including (where
  applicable) one-party / two-party consent rules, employer notice
  requirements, and data-retention obligations
- The content of any export they produce from SmartMemo, and any further
  distribution of that content

### 4.4 Fork / downstream maintainers are responsible for:

- Any modification, build flag, dependency, packaging, or distribution
  decision they make to the codebase
- The legal posture of their own distribution channel (their own GitHub
  release, their own app store listing, their own website)
- Ensuring that the `LICENSE` and `NOTICE` files in any modified
  distribution remain visible and unmodified in their essential
  attribution content

## 5. The "Technology-Neutrality" Defence

SmartMemo's design deliberately preserves **technology neutrality** as a
legal defence, modelled on the well-established "generic tool" doctrine
in software law:

- A video player is not liable when a user uses it to play pirated content.
- An encryption library is not liable when a user uses it to hide a crime.
- A voice recorder is not liable when a user uses it to capture a private
  conversation without consent.

Similarly, SmartMemo is a generic Android accessibility + audio capture
framework. Its shipped configuration is empty of any application-specific
logic. The author has no involvement in, and bears no responsibility for,
any end-user's specific configuration choice.

The technology-neutrality posture is **preserved by code, not by promise**:

- No hard-coded third-party package name exists in the default codebase
- No third-party-specific UI flow exists in the default codebase
- No "load this specific app's content" demo or tutorial exists in the
  default codebase
- No automation script targeting a specific third-party app exists in the
  default codebase

## 6. The GPL-3.0 "Viral" Defence

By licensing SmartMemo under GPL-3.0, the author benefits from a strong
**copyleft** effect:

- Any derivative work that incorporates SmartMemo's source code must
  itself be distributed under GPL-3.0 with full source disclosure.
- This **deters commercial closed-source abuse** of the project: a
  commercial entity cannot quietly take SmartMemo's code, add a
  third-party-specific hack, and ship it as a proprietary product.
- If a downstream actor nevertheless does so, **the author of that
  derivative work is the infringer**, not the upstream author. The
  upstream author (`hannanlsa`) is a potential co-plaintiff (for
  GPL violation), not a co-defendant.

## 7. The "On-Device Only" Defence

By shipping without the `INTERNET` permission:

- No data can leave the device. The application is, at the kernel /
  network-stack level, a "black hole" with respect to outbound traffic.
- The application is, by construction, **incompatible with the
  business models** that the relevant anti-competition / privacy laws
  target (e.g. "data brokers", "ad networks", "user tracking firms").
- The application is **verifiable** by a network packet capture: any
  audit will record zero outbound traffic from the SmartMemo process.

## 8. The "PR Review" Defence

The author reserves the right to reject any pull request that, in the
author's reasonable judgement:

- Targets a specific third-party application by package name or other
  hard-coded identifier
- Implements a generic capability (e.g. accessibility, audio capture)
  in a way that is **only useful** against a specific third-party
  application
- Re-introduces any form of network egress, telemetry, or remote
  configuration
- Is submitted by a known troll, sock-puppet, or competitor of any
  third-party vendor
- Infringes the intellectual property of any third party

A refused pull request is **not** an indication of malice or misconduct
on the part of the contributor. It is a defence of the project's
technology-neutral posture, and is in the interest of all participants
(including the contributor, who would otherwise be exposed to the
same legal risk as the maintainer of a merged PR).

## 9. Community Behaviour and Lawful Use

To preserve the project as a non-commercial, technology-neutral,
community-supported utility, the following community standards apply
(see `CODE_OF_CONDUCT.md`):

- Discussion of how to use SmartMemo to attack, evade, reverse-engineer,
  or specifically target any named commercial product is **off-topic**
  and may be removed.
- Solicitation of paid services, paid support, paid consulting, or
  paid custom builds that target a specific third-party application
  is **prohibited** in the project's public channels.
- Donations, sponsorship, or commercial support of any kind that
  creates a financial link between the project and a third-party
  vendor are **prohibited**.

## 10. Limitation Period and Updates

The legal posture described in this document reflects the author's
understanding as of the date noted above. The author will, in good
faith, update this document when material legal or technical facts
change. However, no retroactive guarantee is made: a user of the
software is bound by the version of the document in effect at the
time of their use.

---

*This document is part of the SmartMemo project, copyright `hannanlsa`,
and is licensed under GPL-3.0, consistent with the rest of the
repository.*
