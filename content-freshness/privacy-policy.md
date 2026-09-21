---
title: Content Freshness — privacy policy
permalink: /content-freshness/privacy-policy/
---

# Privacy policy — Content Freshness

**Vendor:** `Verith` · **Contact:** [`support@verith.dev`](mailto:support@verith.dev)
· **Last updated:** `2026-09-21`

This policy describes what the Content Freshness app for Atlassian Confluence Cloud stores,
where it stores it, and what leaves your site.

## Where the data lives

Content Freshness is an **Atlassian Forge** app. It runs on Atlassian's infrastructure and
stores everything in Forge app storage — Atlassian's own storage service, in a namespace
belonging to your installation. The vendor operates **no servers, no database and no
analytics** of its own, and cannot browse your content.

One thing the vendor *can* see is the app's own diagnostic log output, through Atlassian's
developer console. What those logs contain is stated under **Personal data** below.

## What the app stores

| Data | Why |
|---|---|
| Confluence page identifiers and the date a page was confirmed current | The core function — showing how long ago a page was last verified |
| The identifiers of pages, and the keys of spaces, excluded from monitoring | So the scan skips them |
| Space keys and their configured day thresholds | Per-space configuration |
| The result of the most recent scan: for each page it classified as stale, the page identifier, its **title**, its age in days, its space identifier, key and name, and the **account identifier and display name of its last author** | So the dashboard can list the stale pages and show who to ask about each one |
| The last ten scan summaries (counts only — no titles, no names, no identifiers) | The history tab |
| An optional webhook URL, if an administrator sets one | Outbound scan notifications |

The app does **not** store page bodies, comments, attachments or email addresses.

## Personal data

The personal data the app holds is the **Atlassian account identifier** and **display name**
of the last author of a page that the weekly scan classified as stale. It collects no other
personal data about anyone.

- Every stored account identifier is reported to Atlassian **weekly** through Atlassian's
  personal-data reporting API, as the Marketplace requires of any app that stores one.
- When Atlassian reports an account back as **closed**, the app erases that person's data:
  the account identifier and display name are removed from the stored scan summary. The
  page itself stays in the list — it is still stale; only the person is removed.
- Application logs record **identifiers, not content** — no page titles, no space names, no
  display names and no account identifiers.

## What leaves your Atlassian site

Nothing, unless an administrator configures a webhook URL.

If one is set, the app posts the **full result of each scan** to that address as JSON, and
that is more than counts. For every page in the stale list it carries the page identifier,
**the page title**, the age in days, the space key and space name, and **the account
identifier and display name of that page's last author** — plus your site's address.

A webhook therefore moves page titles and personal data out of Atlassian, to a destination
your own administrator chooses. That is what the feature is for, and it is the only way
anything leaves at all — but pick the destination accordingly, and record it as a transfer of
personal data if your organisation keeps such a record. The field is empty by default;
removing the URL stops the sending immediately, and the app has no other outbound
destination.

The app displays no advertising, contains no third-party trackers, and shares nothing with
any third party of the vendor's choosing.

## Retention and deletion

- A page's stored data is removed automatically once the page no longer exists, by a weekly
  sweep with a 30-day grace period (a page missing from one API response is not proof of
  deletion).
- An account reported back by Atlassian as **closed** is erased from the stored scan result
  automatically, without anyone asking.
- Uninstalling the app removes its data under **Atlassian's Forge storage lifecycle**, which
  the vendor neither controls nor can accelerate. Two details of that lifecycle are worth
  knowing, because "uninstall" does not mean "gone this second": Atlassian lets an
  administrator either keep the app until the end of the billing or trial period or remove it
  at once, forfeiting the remainder; and after removal the data is soft-deleted and held for
  Atlassian's retention period before permanent deletion, during which a reinstallation can,
  on request, be relinked to it.

### How to remove data yourself

Every lever is in your administrators' hands, and none of them requires the vendor:

| To remove | Do this |
|---|---|
| Everything the app stores | Uninstall the app; choose the immediate option rather than keeping it to the end of the period if you want the clock to start now. Atlassian then deletes the storage under the lifecycle described above |
| One space's pages and their authors from the stored results | Exclude the space on the admin dashboard, then run a scan. The stored result is **replaced**, not appended to — earlier results are not kept, and the scan history holds counts only, never a name or an account identifier |
| One page — and its author's name — from the stored results | Mark the page as up to date, or edit it, then run a scan: it is no longer stale, so neither it nor its author appears in the new result |

**The vendor cannot do any of this on your behalf** — not as policy, but because it holds no
copy of your data and has no access to your instance's app storage. What it *can* do is
explain exactly what is stored and where, and it will answer any such question within
**30 days**: [`support@verith.dev`](mailto:support@verith.dev).

## Your rights

Under GDPR terms, your organisation is the **data controller** and the vendor is a
**processor** with no access to the data. Access, correction, erasure and portability
requests are therefore satisfied by your own administrators, using the table above; a request
sent to the vendor will be answered with the same instructions rather than with an action,
because there is nothing on the vendor's side to act on.

## Changes

Material changes to this policy are published on this page with a new *Last updated* date
before they take effect.
