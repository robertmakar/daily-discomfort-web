# Daily Discomfort website — local draft

Standalone HTML/CSS project for GitHub Pages and dailydiscomfort.app. No JavaScript, package installation, backend, analytics, external fonts, or embeds. No repository has been initialized and nothing has been deployed. Never publish this draft without approval.

## Preview

From this folder run:

```sh
python3 -m http.server 8765 --bind 127.0.0.1
```

Open http://127.0.0.1:8765, /privacy/ and /support/. Stop with Ctrl-C. Root-relative links target the intended custom-domain root; a GitHub repository-subpath preview is not supported without its custom domain. /privacy and /support redirect to their trailing-slash directory pages.

## Contents and brand

- index.html: concise homepage and non-clickable Coming to the App Store status.
- privacy/index.html: 11-section privacy-policy draft; no effective date assigned.
- support/index.html: native HTML FAQ disclosures, troubleshooting and unverified contact status.
- styles.css: responsive layout; app colors #F5F2ED, #111111, #FF5C35; local system fonts.
- assets/peak.png: byte-for-byte copy of the approved mobile asset assets/images/daily-discomfort-peak-mark.png. No redraw or animation port.
- CNAME: requested custom domain; its presence alone does not configure DNS.
- .nojekyll: serve the static files directly.

## Confirmed readiness

Design, operator Robert Ashraf (operating as Daily Discomfort), and intended audience 16+ are approved. Both addresses use Spaceship forwarding into Gmail. The owner confirmed delivery/reply testing and the same up-to-12-month retention for support and privacy requests, with legitimate support/legal/security exceptions. These email confirmations are owner-reported, not tests performed by this agent. The destination mailbox address does not need to be published.

## Remaining publication gates

- Confirm an operational deletion process covering received/sent mail, attachments, Trash, downloaded copies and any backups. Gmail normally retains deleted messages in Trash for up to 30 days; archiving is not deletion. Decide how to meet the stated period and document justified exceptions. No mailbox settings or deletions have been performed.
- Confirm GitHub account/organization owner. Suggested new repository name: daily-discomfort-web (not yet created or checked for availability).
- Approve final privacy policy and authorize publication separately. Keep all local-preview strips, policy draft title/metadata/label and noindex/nofollow until then.
- Effective date: unset intentionally. At the authorized release, use the calendar date when the policy is first made public. Do not use this review date or a planned date. If release is delayed into another day, update before release; record the successful public release date. Replace the draft badge with “Effective date: [actual day month year]” and the Changes paragraph with “We will update this page when our privacy practices change and show the effective date of the updated policy.” Do not publish the bracketed instruction.
- Once retention is confirmed, remove its policy notice. At release remove preview strips, remove draft references from privacy title/description, update hosting wording to present tense, and remove noindex/nofollow if public indexing is intended. Keep the approved styling, artwork and App Store coming-soon status.

## Exact deployment sequence — NOT AUTHORIZED YET

Publishing starts when files are uploaded to a public repository or Pages is enabled, not only when DNS changes. Complete the content gates first. Do not execute any step below without publication/DNS authorization.

1. In Spaceship open Launchpad → Domain Manager → dailydiscomfort.app → Advanced DNS. Save a complete copy/screenshots of existing records and confirm Spaceship is authoritative. Keep nameservers unchanged. Preserve every MX, SPF/TXT, DKIM TXT/CNAME, DMARC TXT, forwarding, mail-host and service-verification record. Gmail is only the forwarding destination: DO NOT replace Spaceship MX with Google MX.
2. GitHub profile Settings → Pages → Add a domain → dailydiscomfort.app (use the owning organization's Pages settings if applicable). Copy its exact verification TXT host/value into Spaceship Advanced DNS as an additional record. A typical host begins _github-pages-challenge-, but use the generated values, never a guessed token. If Spaceship appends the domain automatically enter only the host portion. Verify on GitHub and retain the TXT record permanently.
3. GitHub → New repository. Owner: the confirmed account/organization. Name: daily-discomfort-web (proposed). Visibility: Public for GitHub Free Pages. Create a separate repository; do not use or expose the mobile app. Add only these release files at the root of main: index.html, styles.css, privacy/index.html, support/index.html, assets/peak.png, CNAME and .nojekyll. Do not nest them inside an extra daily-discomfort-web folder. Keep internal README/VALIDATION, screenshots and recovery copies out of the served release. Public repository upload/commit is a publication step requiring approval.
4. Repository Settings → Pages → Build and deployment → Source: Deploy from a branch → Branch: main → Folder: /(root) → Save. Set Custom domain to dailydiscomfort.app and Save BEFORE changing web DNS. CNAME must contain exactly dailydiscomfort.app and a newline (already correct); .nojekyll is present. The file is not a DNS CNAME record. No build command, dependencies, Actions workflow or secrets are needed.
5. In Spaceship Advanced DNS, add the four apex A records below. Use TTL 3600 seconds if offered, otherwise the default. Replace only confirmed conflicting apex web/parking A records; inspect apex AAAA/ALIAS records for old hosting destinations and remove/replace only those web conflicts. Do not delete the whole zone or a mixed email/service connection. Do not add an apex DNS CNAME, which would conflict with apex mail records. No wildcard DNS.

| Type | Host | Value | TTL |
| --- | --- | --- | --- |
| A | @ | 185.199.108.153 | 3600/default |
| A | @ | 185.199.109.153 | 3600/default |
| A | @ | 185.199.110.153 | 3600/default |
| A | @ | 185.199.111.153 | 3600/default |

A-only is sufficient. If IPv6 is intentionally enabled, use all four official AAAA destinations: 2606:50c0:8000::153, 2606:50c0:8001::153, 2606:50c0:8002::153, 2606:50c0:8003::153. Do not leave old apex IPv6 routing active.

Optional www (recommended by GitHub): CNAME host www → CONFIRMED-OWNER.github.io, without https or repository path; replace CONFIRMED-OWNER with the actual GitHub owner. With apex configured as the Pages custom domain, GitHub redirects www to apex. This is an optional additional DNS change, not performed or required for the requested apex URLs.

6. Wait for the GitHub Pages deployment and DNS check. Certificate issuance/Enforce HTTPS availability may take up to 24 hours. Enable Enforce HTTPS. If existing CAA records block issuance, investigate against GitHub's current documentation; do not remove or weaken them blindly. Never bypass certificate warnings. Keep Spaceship email records intact.
7. Verify from a signed-out browser and another network/device: https://dailydiscomfort.app/, https://dailydiscomfort.app/privacy and https://dailydiscomfort.app/support, including slash redirects, CSS/image loading, policy effective date, absence of draft notices, navigation, keyboard use and both mailto targets. HTTP should redirect to HTTPS. Verify www only if configured. Root-relative assets require the domain root; the default project-subpath URL is not the intended preview.
8. Compare mail-related DNS to the saved copy and re-test incoming delivery/replies for both addresses. Record the actual public release date. A mobile Settings link is a separate, later approval; do not modify the mobile app here.

## Read-only checks after approved deployment

```sh
dig +short dailydiscomfort.app A
dig +short dailydiscomfort.app AAAA
dig +short dailydiscomfort.app MX
curl -I https://dailydiscomfort.app/
curl -IL https://dailydiscomfort.app/privacy
curl -IL https://dailydiscomfort.app/support
curl -I http://dailydiscomfort.app/
```

Expected A answers are the four listed addresses; AAAA must be empty or the intended GitHub addresses. MX must remain the original Spaceship forwarding records. Check the generated verification TXT separately. Compare all email TXT/CNAME records too; MX alone does not prove mail configuration is preserved.

GitHub logs and stores visitor IP addresses for security. The website therefore does not claim that no visitor data is processed. No cookie banner is added because our code introduces no cookies or tracking; reassess if services change.

## Official references

- https://docs.github.com/en/pages/getting-started-with-github-pages/what-is-github-pages#data-collection
- https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/verifying-your-custom-domain-for-github-pages
- https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site
- https://docs.github.com/en/pages/getting-started-with-github-pages/securing-your-github-pages-site-with-https

Website previews do not verify DNS, TLS issuance, email delivery, the final App Store privacy label, or device-level application behavior.

- https://www.spaceship.com/knowledgebase/dns-records-types/
- https://support.google.com/mail/answer/7401
- https://policies.google.com/privacy
