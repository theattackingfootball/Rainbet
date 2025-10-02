[README.md](https://github.com/user-attachments/files/22665889/README.md)
# Rainbet Exposed — Timeline, Evidence & Right-of-Reply

This repository documents Attacking Football’s reporting on Rainbet, the aftermath on our platforms, and our attempts to obtain an on-the-record response. It includes a dated timeline, copies of our outreach, platform/host notices, and technical indicators observed during an ongoing DDoS/inauthentic-engagement campaign.

> **Last updated:** 02 Oct 2025  
> **Maintainer:** Paddy Keogh — Attacking Football (paddy@attackingfootball.com)

---

## Contents
- [Summary](#summary)
- [Timeline of Events](#timeline-of-events)
- [What We Published](#what-we-published)
- [Pre-Publication Outreach](#pre-publication-outreach)
- [Social Platform Signals (Botting)](#social-platform-signals-botting)
- [Third-Party Notices (Hosting/CDN)](#third-party-notices-hostingcdn)
- [Technical Indicators (DDoS)](#technical-indicators-ddos)
- [Mitigations Taken](#mitigations-taken)
- [Open Questions for Rainbet](#open-questions-for-rainbet)
- [Evidence Pack](#evidence-pack)
- [How Others Can Verify](#how-others-can-verify)
- [UPDATES](#updates)
- [Legal / Editorial Notes](#legal--editorial-notes)
- [Changelog](#changelog)
- [Maintainer Contact](#maintainer-contact)

---

## Summary
- **Article published:** *Rainbet Exposed: The Most Dangerous Bookie On Football Twitter* (26 Sept 2025).  
- **Before publication:** On 13 Sept 2025 we sent a detailed media enquiry to Rainbet. **No response** by the requested 18 Sept deadline.  
- **After publication:** Our site and social channels experienced a spike in suspicious activity (bot-like follows/likes; HTTP-flood attacks).  
- **Notices:** Namecheap applied HAProxy blocking, then **null-routed** our domain during the wave; Cloudflare auto-mitigated requests flagged as **“HTTP requests from known botnet (signature #5)”** peaking ~**180 rps**.  
- **Right of reply:** Multiple emails sent (28 Sept, 29 Sept, 01 Oct). **No response** received as of this update.

---

## Timeline of Events

| Date & Time | Event | Evidence / Notes |
|---|---|---|
| **Sat, 13 Sept 2025, 00:39** | **Media enquiry** to `marketing@rainbet.com` (licensing, consumer protection, marketing, payments, leadership). **No reply** by 18 Sept deadline. | `evidence/outreach/2025-09-13-media-enquiry.png`, `evidence/outreach/2025-09-13-media-enquiry.txt` |
| **Fri, 26 Sept 2025 ~09:41** | Article promo on X/Twitter. | `evidence/social/tweets/rainbet-exposed-tweet.png` |
| **Fri, 26 Sept 2025** | **Article published:** *Rainbet Exposed: The Most Dangerous Bookie On Football Twitter*. | `evidence/article/` |
| **27–28 Sept 2025** | Abrupt spike in bot-like follows/likes; raised on Rainbet live chat (agent **“Abby”**). | `evidence/social/engagement-anomalies/`, `evidence/support/live-chat-notes.txt` |
| **Sun, 28 Sept 2025, 23:39** | **Right of reply #1** sent to `manager@rainbet.com`. | `evidence/outreach/2025-09-28-right-of-reply.txt` |
| **Mon, 29 Sept 2025, 20:49** | **Namecheap**: active DDoS; site blocked via **HAProxy**. | `evidence/notices/namecheap-2025-09-29-2049.txt` |
| **Mon, 29 Sept 2025, 21:12** | **Follow-up** email to Rainbet noting DDoS impact. | `evidence/outreach/2025-09-29-follow-up.txt` |
| **Mon, 29 Sept 2025, 22:05** | **Namecheap follow-up**: persistent wave; domain **null-routed**. | `evidence/notices/namecheap-2025-09-29-2205.txt`, `evidence/notices/namecheap-followup-screenshot.png` |
| **Wed, 01 Oct 2025, 06:35 UTC** | Cloudflare alert: **HTTP flood** (ongoing). | `evidence/cf/2025-10-01-0635UTC-http-flood.png` |
| **Wed, 01 Oct 2025, 09:03** | **Final request for response** sent to Rainbet (48-hour window; escalation path). | `evidence/outreach/2025-10-01-final-request.txt` |
| **Thu, 02 Oct 2025, 16:11:55 UTC** | Cloudflare **auto-mitigation**: *HTTP requests from known botnet (signature #5)* — action **block**, peak **180 rps**. | `evidence/cf/2025-10-02-rule5-email.png` |
| **Thu, 02 Oct 2025 (evening)** | Tweet noting **Rainbet removed “Meet the Team” page** post-publication. | `evidence/social/tweets/meet-the-team-removed.png` |
| **As of 02 Oct 2025** | No response from Rainbet; attacks intermittent. | Status noted here. |

---

## What We Published
- **Article (26 Sept 2025):** *Rainbet Exposed: The Most Dangerous Bookie On Football Twitter.*  
  Focus: licensing posture (incl. Anjouan/Comoros screenshot), influencer/bet-slip promos, consumer-protection risks, payment transparency.  
  - Licence screenshot: `evidence/licenses/anjouan-rbgaming-nv.png`

---

## Pre-Publication Outreach
**13 Sept 2025 (00:39)** — Media enquiry to `marketing@rainbet.com` with 14 questions covering:  
- **Licensing & Consumer Protection:** Anjouan choice; player-fund safeguarding; restricted-jurisdiction access.  
- **Responsible Gambling & Self-Exclusion:** liability language; handling of self-excluded relapses; available RG tools.  
- **Marketing Practices:** undisclosed paid “bet slip” posts; influencer reliance; safeguards for minors/vulnerable users.  
- **Payments & Transparency:** crypto/gift-card reliance; AML controls; beneficial ownership of **RBGaming N.V.**  
- **Leadership & Accountability:** verification of named executives, industry track record.  
**Outcome:** No reply by 18 Sept; right of reply remained open post-publication.  
Evidence: `evidence/outreach/2025-09-13-media-enquiry.png` and `.txt`.

---

## Social Platform Signals (Botting)
Indicators of **inauthentic engagement** starting after publication and overlapping with DDoS windows:

- **Follower spikes** well above baseline on **27–29 Sept**.  
  → `evidence/social/twitter/new-follows-7d.png`
- **Demographics anomaly:** **“Not specified” = 91.3%** in Gender chart — typical of bulk/low-quality accounts.  
  → `evidence/social/twitter/gender-not-specified.png`
- **Engagement mismatch:** posts with **likes ≫ replies/RTs**; add examples under `evidence/social/tweets/examples-likes-gt-follows-*.png`.

*Why it matters:* Mass low-quality liking/following is a known tactic to trip platform integrity heuristics, risking rate limits, reduced distribution, or shadow-bans for the target account.

---

## Third-Party Notices (Hosting/CDN)
- **Namecheap Legal & Abuse (29 Sept, 20:49):** active DDoS; HAProxy block.  
- **Namecheap follow-up (29 Sept, 22:05):** ongoing wave; domain **null-routed** to protect infra.  
- **Cloudflare (01 Oct, 06:35 UTC & 02 Oct, 16:11:55 UTC):** HTTP flood; **known-botnet signature #5** event auto-mitigated (peak ~180 rps).  
Artefacts under `evidence/notices/` and `evidence/cf/`.

---

## Technical Indicators (DDoS)
- **Layer-7 HTTP flood** with randomized query strings to bust cache (e.g., `GET /?abc123`).  
  → raw origin excerpt **29 Sept 2025**: `evidence/server-logs/DDoS_Log_attavmph_Sep-29-2025.txt`  
- **Cloudflare analytics (7-day window):** ~**921M** total requests; **95.66%** cached; **~2 TB** served.  
  → `evidence/cf/cloudflare-analytics-7d.png`
- **Signature event:** Cloudflare rule *“HTTP requests from known botnet (signature #5)”*, **Rule ID** displayed in alert; action **block**.  
  → `evidence/cf/2025-10-02-rule5-email.png`

---

## Mitigations Taken
- Cloudflare **Under Attack** mode during peaks; tightened WAF & rate-limits on `wp-json`, login/API, and high-risk paths.  
- Coordination with host during HAProxy block and null-route; staged re-enable based on status.  
- Centralised log retention (Cloudflare events + origin logs).  
- Public repo redacts sensitive indicators (full IPs, cookies, WAF thresholds) to avoid evasion.

---

## Open Questions for Rainbet
1. Any involvement in, knowledge of, or benefit from inauthentic engagement and/or DDoS targeting AttackingFootball.com since 26 Sept 2025?  
2. Clarify current licences, corporate entities, and controls around influencer/bet-slip promotions (including any use of fabricated slips).  
3. Commit to preserve and, if requested by competent authorities, provide relevant campaign/affiliate records for **24 Sept 2025 → present**.

---

## Evidence Pack

```
/evidence
  /article/
    2025-09-26-rainbet-exposed-summary.txt
  /outreach/
    2025-09-13-media-enquiry.png
    2025-09-13-media-enquiry.txt
    2025-09-28-right-of-reply.txt
    2025-09-29-follow-up.txt
    2025-10-01-final-request.txt
  /notices/
    namecheap-2025-09-29-2049.txt
    namecheap-2025-09-29-2205.txt
    namecheap-followup-screenshot.png
  /cf/
    2025-10-01-0635UTC-http-flood.png
    2025-10-02-rule5-email.png
    cloudflare-analytics-7d.png
  /social/
    /twitter/
      new-follows-7d.png
      gender-not-specified.png
    /tweets/
      rainbet-exposed-tweet.png
      meet-the-team-removed.png
      examples-likes-gt-follows-1.png
    /engagement-anomalies/
  /licenses/
    anjouan-rbgaming-nv.png
  /server-logs/
    DDoS_Log_attavmph_Sep-29-2025.txt
    README-REDACTIONS.md
  /support/
    live-chat-notes.txt
```

---

## How Others Can Verify
- **Hash artefacts** (simple integrity check):
  ```bash
  shasum -a 256 evidence/**/*.png evidence/**/*.txt 2>/dev/null | tee EVIDENCE_HASHES.txt
  ```
- **Archive public URLs** (article, tweets) via independent web-archiving services for third-party timestamps.

---

## UPDATES
> Add dated statements/responses here. If Rainbet (or an authorized spokesperson) provides an on-the-record reply, include it verbatim or as an attributed statement with timestamp.

- **[Placeholder]** *No response received from Rainbet as of 02 Oct 2025.*

---

## Legal / Editorial Notes
- All statements reflect **our records and observations**. Allegations remain **alleged** pending formal adjudication.  
- Third-party personal data may be redacted to protect privacy/security.  
- Evidence is shared in the public interest on consumer protection, platform integrity, and responsible gambling marketing.  
- **Right of Reply remains open**; verifiable, attributable statements will be added in **UPDATES**.

---

## Changelog
- **02 Oct 2025:** Initial public README with timeline, outreach log, DDoS indicators, platform/host notices, and social-botting signals.

---

## Maintainer Contact
**Paddy Keogh** — Attacking Football  
Email: paddy@attackingfootball.com  
Site: https://www.attackingfootball.com
