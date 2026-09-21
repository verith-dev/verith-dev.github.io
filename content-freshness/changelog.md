---
title: Content Freshness — release notes
permalink: /content-freshness/changelog/
---

# Release notes

[Support](/content-freshness/) · [Privacy policy](/content-freshness/privacy-policy/) · [Security](/content-freshness/security/)

Newest first. Marketplace version numbers are assigned by Atlassian when a version is
published; the dates below are publication dates.

## 1.0 — `<RELEASE DATE>` — first public release

Everything the app does at launch:

- **Freshness label in the page byline** — *Up to date*, *Getting old* or *Possibly outdated*,
  on every page; the outdated label carries the page's age in days.
- **Freshness panel** — click the byline label for the full status and the exact age in days,
  to confirm the page is still current, or to exclude that page from monitoring.
- **Mark as up to date** — confirms a page without editing it, creating a version, or
  notifying its watchers.
- **Per-space thresholds** — each space can override the global defaults (120 days aging,
  180 days stale) in *Space settings → Content Freshness*.
- **Weekly scan** — runs automatically, processes large instances in batches, and can also be
  started on demand by an administrator.
- **Admin dashboard** — stale pages with a health breakdown, filters by space and author, CSV
  copy, bulk confirmation, scan history for the last ten runs, and space exclusions.
- **Webhook** — optional; posts each scan's result as JSON to an address the administrator
  chooses. It contains stale page titles and author names, so it is a data transfer the
  administrator sets up deliberately.
- **Seven languages** — English, Polish, German, French, Spanish, Portuguese, Japanese,
  following each viewer's own Atlassian language setting.

Two design decisions worth stating at launch, because they are visible in what the app does
*not* do:

- **No write permission.** The app cannot change anything in Confluence; every call it makes
  is a read. Confirmations and configuration live in the app's own storage.
- **No email and no comments.** Stale pages surface on the dashboard and, if an administrator
  configures one, through the webhook — channels the customer sets up on purpose. Nothing is
  ever posted to a page and nobody is emailed by the app.
