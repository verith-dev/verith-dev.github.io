---
title: Content Freshness — security and data handling
permalink: /content-freshness/security/
---

# Security and data handling

**Vendor:** `Verith` · **Contact:** [`support@verith.dev`](mailto:support@verith.dev)
· [Privacy policy](/content-freshness/privacy-policy/) · [Support](/content-freshness/)

This page answers, in one place, the questions an IT or security team asks before installing
an app. It is written to be checkable against the app's own manifest rather than to reassure.

## Where the code runs

Content Freshness is an **Atlassian Forge** app. All of its code runs on Atlassian's own
infrastructure, inside Atlassian's tenancy model; all of its data lives in Forge app storage.
The vendor operates **no server, no database and no analytics** of its own, and has no
mechanism to read a customer's content.

The one vendor-visible channel is the app's diagnostic log output, which Atlassian's developer
console exposes to the app's publisher. That is why the app logs identifiers rather than
content — see **Personal data** below.

## Permissions the app requests, and why

| Permission | Why it is needed |
|---|---|
| `read:page:confluence` | Read page metadata (id, last-edit date) for the label and the scan |
| `read:space:confluence` | Resolve a space id to its key, for per-space thresholds and exclusions |
| `read:confluence-content.summary` | List pages during the weekly scan |
| `read:confluence-content.all` | Read the page's version date, which the summary API does not carry |
| `read:confluence-user` | Show the last author's name on the dashboard, and read the viewer's own language setting |
| `storage:app` | Store confirmations, scan results, per-space configuration |
| `report:personal-data` | Report stored account identifiers to Atlassian weekly, as the Marketplace requires |
| `external:fetch:backend` | Send the scan summary to the webhook URL an administrator configures |

**There is no write permission of any kind.** The app cannot create, edit, move or delete a
page, a comment, or anything else in Confluence — not by policy, but because the permission
was never granted to it. Every Confluence call it makes is a `GET`.

That is verifiable without trusting this page: the app's requested permissions are shown on
the installation screen and in the Marketplace listing, and any write scope would appear
there.

## Outbound network access

The app makes **no request to any destination outside Atlassian** unless an administrator
enters a webhook URL on the admin dashboard. (Inside Atlassian it calls the Confluence REST
API, read-only, and Atlassian's personal-data reporting endpoint.)

If a webhook is set, each scan posts its **full result** as JSON to that address and nowhere
else. Assess it as a data transfer, not as a notification: besides the counts it carries, for
every page in the stale list, the page identifier, **its title**, its age, its space key and
name, and the **account identifier and display name of that page's last author**, together
with the site's address.

The manifest permits egress to any address because the destination is chosen by the customer
at runtime and cannot be known when the app is built. Removing the URL stops the sending
immediately. If your organisation does not want this, simply never configure it: the field is
empty by default.

## Personal data

The app stores the **account identifier** and **display name** of the last author of each
page the weekly scan classified as stale, so the dashboard can show who to ask. It collects no
other personal data.

- Stored identifiers are reported to Atlassian weekly via Atlassian's personal-data API.
- Accounts Atlassian reports as **closed** are erased from the stored scan result; the page
  stays in the list, without the person.
- Application logs record **identifiers, not content** — no page titles, no space names, no
  display names, no account identifiers.
- If a webhook is configured, the author's identifier and display name are included in what
  is posted to it. See **Outbound network access** above.

Details in the [privacy policy](/content-freshness/privacy-policy/).

## What an unlicensed instance can still do

If a subscription lapses, the app degrades **read-only**: labels, the freshness panel,
marking a page as up to date, per-page exclusion and all existing scan results continue to
work. Starting new scans and changing configuration stop. No customer data is deleted as a
result of a lapse.

## Reporting a vulnerability

Email [`support@verith.dev`](mailto:support@verith.dev) with the subject line **SECURITY**. Please
include enough detail to reproduce the issue and do not disclose it publicly until it is
fixed. Acknowledgement within **two business days**; a fix or a remediation plan within
**30 days**, communicated to you directly. Reports may also be submitted through Atlassian's
Marketplace security channel, which reaches the vendor as well.
