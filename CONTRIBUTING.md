# Contributing to SmartMemo

> **First-time contributor? Start by reading `LEGAL.md`, `CLA.md`, and
> `THREAT_MODEL.md` in full. They are short, and they explain what kind of
> contributions are welcome and which are not.**

Thank you for your interest in improving SmartMemo. This project depends
on community contributions to grow, but it operates in a sensitive
legal area, so contribution rules are stricter than for a typical
open-source project.

## 1. The Cardinal Rule: Technology Neutrality

SmartMemo must remain a **generic Android automation, accessibility,
and on-device AI utility**. It must not, in its default distribution,
target any specific third-party commercial application.

Before submitting a pull request, ask yourself:

> *Would this change still make sense if every Android user replaced
> the third-party app I am thinking of with a different one?*

If the answer is **no**, the change is probably not appropriate for
the default codebase.

## 2. Contribution License Agreement (CLA)

By opening a pull request, you agree to the terms in `CLA.md`. The
key points are:

- You are the original author of the contribution (or have the right
  to submit it).
- The contribution does not infringe any third-party IP.
- The contribution does not contain reverse-engineered code from any
  third-party proprietary product.
- The contribution does not specifically target any named commercial
  application.

No paper signature is required; the act of opening a PR is the
acceptance mechanism.

## 3. What We Will Accept

We welcome contributions that:

- Improve the on-device AI inference (Whisper-class models,
  alternative ASR backends, quantisation, NPU/GPU acceleration on
  supported SoCs)
- Improve the accessibility framework's general text-capture logic
  (e.g. better OCR, better noise reduction, better timestamp alignment)
- Improve the audio capture pipeline (e.g. better AEC, better VAD,
  better microphone routing)
- Improve the local data model (search, export, encryption at rest)
- Improve build, test, and CI infrastructure
- Improve documentation, translations (of **non-targeting** content),
  and code comments
- Improve energy efficiency and battery life
- Add platform support (e.g. newer Android API levels, foldables,
  tablets, large screens)
- Add accessibility features for users with disabilities (e.g. screen
  reader support, high-contrast mode, large fonts)

## 4. What We Will Reject

We will reject pull requests that:

### 4.1 Hard-coded third-party targeting

- Adding a hard-coded package name for any commercial product
- Adding a default configuration that ships with a specific
  third-party app pre-associated
- Adding a sample, demo, screenshot, or tutorial that features a
  specific third-party product
- Adding an in-app "starter preset" that targets a specific product
- Adding any "compatibility list" that names specific products

### 4.2 Invasive or "hack" functionality

- Hooking, patching, or modifying any third-party application's
  process, in-memory state, or on-disk files
- Decompiling, disassembling, or otherwise reverse-engineering any
  third-party application
- Reading or copying any third-party application's private storage,
  database, or sandbox
- Circumventing any access control, DRM, or anti-tamper mechanism
  of any third-party application
- Bypassing `allowAudioPlaybackCapture=false` or any similar
  per-app media-capture opt-out

### 4.3 Network and telemetry

- Adding the `INTERNET` permission
- Adding any HTTP client, gRPC client, WebSocket client, or other
  network egress
- Adding any analytics SDK, crash reporter, or telemetry endpoint
- Adding any remote configuration mechanism
- Adding any "phone home" beacon, even for the purpose of counting
  users

### 4.4 Commercial or donation infrastructure

- Adding donation buttons, crypto addresses, payment links, ad SDKs,
  sponsorship sections, or any other financial infrastructure to
  the codebase
- Adding premium tiers, in-app purchases, or subscription logic
- Adding referral codes, affiliate links, or any form of revenue
  sharing

### 4.5 IP / copyright / licence violations

- Submitting code copied from a third-party proprietary product
  (even with modifications)
- Submitting code copied from another open-source project under an
  incompatible licence
- Submitting code without proper SPDX headers where required
- Submitting assets (images, audio, fonts) without a compatible
  licence declaration

### 4.6 Code quality red flags

- Submitting code that intentionally hides its behaviour
  (obfuscation, dynamic code loading, etc.) without a strong and
  documented reason
- Submitting code that requires unsafe, undocumented, or
  manufacturer-specific APIs without a clear fallback for unsupported
  devices
- Submitting code that fails to build on the project's standard
  build matrix

## 5. Review Process

1. **Open an issue first** for non-trivial changes. Describe the
   problem, the proposed solution, and (if applicable) the affected
   files. Wait for a maintainer acknowledgement before writing code.
2. **Open a pull request** with a clear title and description.
3. **CI must pass** (build, lint, unit tests).
4. **Maintainer review** will check the cardinal rule (technology
   neutrality) in addition to code quality.
5. **One approval** from a maintainer with write access is required.
6. **Squash-merge** is the default to keep a clean history.

A rejected PR is not a personal judgement. It is usually a
technology-neutrality or legal-posture decision, and the maintainer
will explain the reason in the PR thread.

## 6. Coding Style

- **Kotlin first** for new code. Java is acceptable for legacy
  reasons but should be migrated when touched.
- **No external runtime dependencies** that are not licence-clean
  (Apache-2.0, MIT, BSD-2/3, MPL-2.0, GPL-3.0 compatible) without
  maintainer approval.
- **Tests required** for non-trivial logic. Use the project's
  standard test harness.
- **Comments in English** by default. Code is a global artefact.
- **No "TODO" comments** that target a specific third-party app.
  TODOs are allowed for refactoring or for genuine unknowns.

## 7. Commit Message Convention

We follow the **Conventional Commits** style:

```
<type>(<scope>): <short summary>

<longer description if needed>

Refs: <issue number>
```

Types: `feat`, `fix`, `docs`, `refactor`, `perf`, `test`, `build`,
`ci`, `chore`, `revert`.

## 8. Issue Labels

We use the following labels to triage issues:

- `good first issue` — small, well-scoped, newcomer-friendly
- `help wanted` — maintainer would like outside help
- `discussion` — open for community input
- `legal-review` — requires maintainer legal review
- `wontfix` — design decision, not a defect
- `not-a-bug` — working as intended
- `needs-info` — needs more information from the reporter
- `duplicate` — already reported

## 9. Reporting a Legal Concern

If you believe a contribution or a behaviour of the project is in
violation of any law or third-party right, do **not** raise it in a
public issue. Instead, follow the responsible-disclosure process in
`SECURITY.md`.

---

*Thank you for helping keep SmartMemo a clean, neutral, community
project.*

*— `hannanlsa`*
