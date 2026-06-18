# Security Policy

> **Report security issues to `hannanlsa` via the GitHub Security
> "Advisory" tab on this repository. Do not file security issues as
> public bug reports.**

## 1. Supported Versions

The following table describes which versions of SmartMemo currently
receive security updates.

| Version | Supported          |
|---------|--------------------|
| Latest `main` | Yes                |
| Older tags / branches | No             |

The project is in early development. Once a stable release line is
established, this table will be updated to include it.

## 2. Reporting a Vulnerability

If you discover a security vulnerability in SmartMemo, please report
it privately:

- **Preferred channel:** GitHub Security Advisory at
  https://github.com/hannanlsa/SmartMemo/security/advisories/new
- **Backup channel:** Open a *privately* marked discussion, or
  contact the maintainer through their GitHub profile.

Please include:

- A clear description of the vulnerability
- A proof-of-concept (PoC) or reproduction steps, if available
- An estimate of the impact (data exposure, privilege escalation,
  remote code execution, etc.)
- Whether you intend to disclose the vulnerability publicly and on
  what timeline

The maintainer will acknowledge receipt within **7 days** and will
work with you on a coordinated disclosure timeline. As a non-commercial
project, we ask for your patience: the disclosure cycle may be slower
than what a corporate security team would offer.

## 3. Out-of-Scope: Legal / DMCA / "Cease-and-Desist"

The security channel is **not** the right venue for:

- DMCA takedown notices
- "Cease-and-desist" letters from commercial vendors
- Court orders or subpoenas
- Legal threats of any kind

For these, contact the maintainer through their GitHub profile. A
cease-and-desist or DMCA notice will be taken seriously and reviewed
by the maintainer; it will not, however, be processed through the
vulnerability-disclosure workflow.

If you are a commercial vendor and you believe SmartMemo infringes
your intellectual property, please state your claim factually and
proportionately. The maintainer is a single individual working in
good faith, and the project is explicitly designed to be
technology-neutral. Most legitimate IP claims are resolved by
clarifying that the dispute is with a **specific end-user's use** of
SmartMemo, not with the SmartMemo project itself; we are happy to
make this distinction clear in writing.

## 4. What Counts as a "Security" Issue for This Project

A security issue for SmartMemo includes:

- Any way for a malicious third-party application to read
  SmartMemo's local data store (SQLite, files in app sandbox)
  without the user's consent
- Any way for a malicious user to read another user's SmartMemo
  data store (e.g. on a shared / rooted device, or via a malicious
  accessibility service competing with SmartMemo)
- Any way for a malicious website / deeplink / intent to crash
  SmartMemo or gain code execution
- Any way to bypass the local-only design and cause SmartMemo to
  make network requests
- Any way to use SmartMemo as a privilege-escalation vector against
  the Android OS
- Any way for SmartMemo to be silently repackaged and redistributed
  in a way that escapes the GPL-3.0 terms (the maintainer wants to
  know about this, even though it is not a "security" issue in the
  traditional sense)

## 5. Out of Scope

- Vulnerabilities in third-party libraries (report them upstream)
- Issues requiring physical access to a locked, non-rooted device
- Issues requiring the user to install a malicious, sideloaded APK
  claiming to be SmartMemo (this is a social-engineering problem;
  the maintainer can only ship a signed APK on the official
  channel)
- Theoretical issues that cannot be reproduced
- Feature requests phrased as "security concerns"

## 6. Coordinated Disclosure

The maintainer favours **coordinated disclosure** with a 90-day
embargo by default, with the following extensions:

- Critical issues affecting end-user data: 30 days
- Issues requiring significant code refactor: 120 days, by mutual
  agreement
- Issues whose fix is trivial and immediately applicable: 7 days

The maintainer will credit the reporter in the fix commit (unless
the reporter requests anonymity).

## 7. Recognition

Security researchers who report valid issues will be credited in:

- The fix commit message
- A `SECURITY_ACKNOWLEDGEMENTS.md` file (if they consent)
- A public GitHub Security Advisory (if they consent)

---

*Project: SmartMemo. Maintainer: `hannanlsa`. Last updated: 2026-06-18.*
