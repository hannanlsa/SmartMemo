# DISCLAIMER

> **Read this carefully before using, contributing to, or redistributing SmartMemo.**

---

## 1. No Warranty

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.

IN NO EVENT SHALL THE AUTHOR (`hannanlsa`) OR COPYRIGHT HOLDER BE LIABLE
FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT,
TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE
OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

## 2. No Affiliation

SmartMemo is an independent, open-source project. It is **not affiliated with,
endorsed by, sponsored by, or in any way associated with** any third-party
software vendor, including but not limited to:

- WeChat / Weixin / Tencent
- DingTalk / Alibaba
- Lark / ByteDance / Feishu
- WhatsApp / Meta
- Telegram
- Signal
- Any other commercial or proprietary communication platform

All product names, trademarks, and registered trademarks referenced in this
repository (if any) are the property of their respective owners. Their use is
purely for descriptive and nominative purposes only and does not imply any
endorsement.

## 3. Universal Tool, User-Defined Scope

SmartMemo is a **generic, technology-neutral automation and accessibility
utility for Android**. It provides:

- An Android Accessibility Service framework (system-public API)
- A microphone-based audio capture pathway (system-public API)
- A Notification Listener Service pathway (system-public API)
- On-device AI inference (e.g. Whisper-class speech-to-text)
- A user-configurable application scope (the user manually enters which
  third-party app package names, if any, the user wishes to associate)

The author of SmartMemo has **no knowledge of, and exercises no control over,
which specific third-party applications any individual end-user chooses to
configure**. The configuration interface is, by design, an **empty whitelist**
that ships with no pre-populated package names from any commercial vendor.

The act of an end-user entering a package name, granting the corresponding
permissions, and using SmartMemo's general-purpose APIs in conjunction with
that user-selected application is **the end-user's sole and independent act**.
The author has neither authored, suggested, nor encouraged such configuration
in any specific case.

## 4. Zero Network Capability

SmartMemo is built to ship **without the `android.permission.INTERNET`
permission** in its default distribution. The application is **physically
incapable** of transmitting captured data off the user's device. This is a
deliberate architectural decision, not an oversight, and serves to:

- Eliminate any possibility of unauthorized data exfiltration
- Provide a categorical defence against claims of illegal data collection,
  transmission, or sale
- Make the application auditable as a fully offline, on-device tool

Any third-party build, fork, or derivative work that re-introduces network
capability is, by definition, no longer SmartMemo as distributed from this
repository, and is governed solely by the GPL-3.0 terms in the `LICENSE` file
and the laws of the contributor's jurisdiction.

## 5. Use at Your Own Risk

By installing, configuring, or otherwise using SmartMemo, **you affirm and
agree** that:

1. You are solely responsible for ensuring that your use of SmartMemo
   complies with the laws, regulations, terms of service, and end-user
   agreements applicable in your jurisdiction and with respect to any
   third-party application you choose to associate with SmartMemo.
2. You will not use SmartMemo to violate the privacy, intellectual property,
   contractual, or other legal rights of any third party.
3. You will not use SmartMemo to intercept, record, or process
   communications to which you are not a lawful party, or for which you do
   not have lawful consent from all participants.
4. The author (`hannanlsa`) shall not be a party to, and bears no
   responsibility for, any dispute arising from your use of SmartMemo.
5. You will indemnify and hold harmless the author (`hannanlsa`) and any
   contributor from any claim, demand, loss, or damage arising from your
   misuse of the software.

## 6. Jurisdictional Caveat

Laws regarding the recording, transcription, and storage of communications
vary significantly by country, region, and use case (e.g. two-party vs
one-party consent jurisdictions; employer/employee notice requirements;
cross-border data flow restrictions). It is **your** responsibility to
understand and comply with the law that applies to you.

## 7. No Legal Advice

Nothing in this repository, including this `DISCLAIMER.md`, the
`LEGAL.md`, the `README.md`, the `THREAT_MODEL.md`, or any source-code
comment, constitutes legal advice. For any question about the legality of
your specific use case, consult a qualified attorney licensed in your
jurisdiction.

---

*Last updated: 2026-06-18. Author: `hannanlsa`.*
*This document is part of the SmartMemo project and is licensed under
GPL-3.0, consistent with the rest of the repository.*
