# Threat Model

> **This document describes the threats SmartMemo is designed to resist,
> the threats it explicitly does not try to resist, and the design
> decisions that draw the boundary between the two.**
>
> **Project: SmartMemo. Maintainer: `hannanlsa`. Last updated:
> 2026-06-18.**

This is a public document on purpose: it makes SmartMemo's defensive
posture auditable by anyone, including third-party vendors who may
have questions about what the project does and does not do.

---

## 1. What SmartMemo Protects Against

SmartMemo is designed to resist the following threats, **in its
default distribution**:

### 1.1 Threats against end-users

| Threat | Defence |
|--------|---------|
| Cloud-side data exfiltration | The shipped app has no `INTERNET` permission. There is no cloud to exfiltrate to. |
| Hidden telemetry | No analytics SDK, no crash reporter, no remote config. The code is open-source and auditable. |
| Credential capture | The accessibility framework is configured to ignore input fields, password fields, OTP fields, and any field marked as `isCredential`. |
| DRM bypass | SmartMemo does not interact with any DRM-protected content stream. It only captures accessibility text and microphone audio, both of which are already available to the user. |
| Auto-update that flips the design | The shipped APK is signed; any side-loaded APK with a different signature is, by definition, not SmartMemo. Auto-update is not part of the shipped design. |
| Silent "phone home" | The shipped app has no network capability. A packet capture will record zero outbound bytes from the SmartMemo process. |

### 1.2 Threats against the project (defensive posture)

| Threat | Defence |
|--------|---------|
| Closed-source fork for commercial abuse | GPL-3.0: any derivative work must also be GPL-3.0 with full source disclosure. |
| Targeted weaponisation against a specific vendor | Hard-reject policy on PRs that hard-code a specific package name (`CONTRIBUTING.md` §4.1). |
| IP laundering through the project | CLA: every contributor affirms originality and non-infringement (`CLA.md` §3). |
| Lawful "cease-and-desist" used to suppress the project | Technology-neutrality documentation: the shipped code does not target any specific product, so most C&Ds can be rebutted as inapplicable. |
| Loss of maintainer availability | GPL-3.0 + public repository: anyone can fork. The project's legal posture is documented in `LEGAL.md` and travels with the code. |

### 1.3 Threats against the maintainer personally

| Threat | Defence |
|--------|---------|
| Implicated by a third-party-specific build distributed by a fork operator | GPL-3.0, `LEGAL.md` §4.4, `NOTICE` file: forks are responsible for their own distribution. |
| Liable for a misuse that the maintainer did not author or sanction | `DISCLAIMER.md` §1 and §5: no warranty, end-user responsibility clause. |
| Personally identified through payment infrastructure | No donation, no ad, no payment infrastructure. The project has no commercial signal. |
| Personally identified through telemetry | No telemetry, no IP leakage, no DNS leakage. |

---

## 2. What SmartMemo Does Not Try to Protect Against

The following are **explicitly out of scope** for SmartMemo's design:

### 2.1 Threats the user takes on themselves

- **Recording a conversation in a two-party-consent jurisdiction without
  consent.** The user is responsible for knowing the consent rules of
  their jurisdiction and obtaining consent.
- **Recording employer-issued communications without employer
  authorisation.** The user is responsible for their employment
  contract and any notice requirements.
- **Recording minors.** The user is responsible for parental consent
  and child-protection law.
- **Using captured content for blackmail, defamation, or other
  unlawful purpose.** The user is solely responsible.

### 2.2 Threats the platform (Android) takes on

- **OS-level privilege escalation.** SmartMemo is a regular Android
  app; it does not (and cannot) defend against an OS-level compromise
  of the device.
- **Supply chain attacks on Google Play Services, the device
  manufacturer, or the SoC vendor.** Out of scope.
- **Side-channel leakage of accessibility events to other
  accessibility services.** This is an Android platform design
  property, not a SmartMemo property.

### 2.3 Threats the user takes on through misconfiguration

- **Configuring SmartMemo to monitor an app the user is not legally
  entitled to monitor.** The user is responsible for this
  configuration.
- **Sharing the local SmartMemo data store with a third party.** The
  user is responsible for this distribution.
- **Exporting notes that include copyrighted, personal, or otherwise
  protected content.** The user is responsible.

---

## 3. The "Line in the Sand"

There is exactly one bright line in SmartMemo's design:

> **The shipped code must not contain any hard-coded reference to a
> specific third-party commercial application.**

If a change crosses that line, it is rejected, regardless of how
clever, useful, or well-intentioned it is.

The reason for this line is simple: the strongest legal defence
available to a generic tool is **technology neutrality**, and the
single fastest way to destroy that defence is to ship code that
identifies a specific target by name.

---

## 4. Adversary Scenarios Considered

The following are representative scenarios the design has been
considered against:

### 4.1 "Vendor X notices SmartMemo exists and sends a C&D"

- `LEGAL.md` and `THREAT_MODEL.md` (this file) make the
  technology-neutrality argument on the record.
- The shipped code has no Vendor-X-specific content, so the
  "specific targeting" prong of most anti-competition claims is
  unsatisfied.
- The maintainer can offer to publish a written statement clarifying
  that SmartMemo is a generic tool and that any Vendor-X-specific use
  is an end-user's independent choice.

### 4.2 "A fork author ships a Vendor-X-specific build"

- The fork is a derivative work under GPL-3.0, so the source must be
  disclosed.
- The maintainer is not the author, distributor, or maintainer of
  that fork.
- `LEGAL.md` §4.4 and the `NOTICE` file put the responsibility on
  the fork author.

### 4.3 "A black-hat forks SmartMemo, strips the CLA, and ships a
closed-source product with Vendor-X-specific hacks"

- This is a GPL-3.0 violation. The maintainer is a potential
  co-plaintiff (with the FSF and the original contributors), not a
  defendant.
- The black-hat has, by violating the licence, **separated their
  build from the SmartMemo project**. The maintainer's
  documentation makes this separation easy to demonstrate.

### 4.4 "A user uses SmartMemo to record a conversation in a
two-party-consent jurisdiction without consent"

- This is the user's violation, not the maintainer's.
- `DISCLAIMER.md` §5 makes this allocation explicit.
- The maintainer is not involved in the user's specific
  configuration, capture, storage, or distribution of the content.

### 4.5 "A jurisdiction passes a law banning accessibility-based
monitoring apps"

- SmartMemo is shipped with an empty configuration, so the law
  would, by its terms, target the *end-user's* configuration
  decision, not the *shipped product's* default state.
- The maintainer would, in good faith, update the project to
  document the law and any necessary changes to the default
  behaviour.

---

## 5. Open Questions

The maintainer is honest about the limits of this design. The
following are open questions that the project does not yet have a
fully formed answer to:

- **Federated / peer-to-peer sync:** would it be acceptable to add
  end-to-end-encrypted peer-to-peer sync as a user-enabled feature?
  (Currently: no, because it reintroduces network capability. A
  future design may consider a fully local, USB / SD-card-based
  sync as a non-network alternative.)
- **Accessibility-service competition:** what happens when another
  malicious accessibility service runs concurrently with SmartMemo?
  (Currently: the user's device is already in a state of
  "any-accessibility-service-can-do-anything"; SmartMemo's
  behaviour is not worse than the platform default. The user is
  responsible for their accessibility-service allowlist.)
- **On-device model poisoning:** if a future release allows
  user-provided model files, a malicious model could behave
  unexpectedly. (Currently: only the bundled model is loaded.
  User-provided models are explicitly out of scope for the
  initial release.)

---

*Project: SmartMemo. Maintainer: `hannanlsa`. License: GPL-3.0
for the source code, CC BY-SA 4.0 for this document.*
