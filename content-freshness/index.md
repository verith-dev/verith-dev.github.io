---
title: Content Freshness — support and documentation
permalink: /content-freshness/
---

# Content Freshness

Content Freshness adds a freshness label to every Confluence Cloud page: **Up to date**,
**Getting old** or **Possibly outdated**, based on how long ago the page was last edited or
last confirmed as current. A weekly scan collects everything that has gone stale so an
administrator can see it in one place.

> **Vendor:** `Verith` · **Support:** [`support@verith.dev`](mailto:support@verith.dev)
> · [Privacy policy](/content-freshness/privacy-policy/) · [Security and data handling](/content-freshness/security/)
> · [Release notes](/content-freshness/changelog/)

---

## Getting started

1. Install the app from the Atlassian Marketplace. **No configuration is required.** The
   label appears on every page immediately, using the global defaults: *Getting old* after
   **120 days**, *Possibly outdated* after **180 days**.
2. Open any page. Next to the page title, in the byline, you will see a coloured indicator
   and the current status. Click it to open the freshness panel with the exact age in days.
3. If the page is still correct despite its age, click **Mark as up to date** in that panel.
   From that moment the page counts as fresh — no edit, no new version, no notification to
   anyone watching the page.

A page's age is the **more recent** of its last edit and its last confirmation, so
confirming an old page makes it fresh, and editing a confirmed page keeps it fresh.

## Changing the thresholds for a space

**Space settings → Content Freshness.** Set *Aging threshold (days)* and *Stale threshold
(days)* for that space; the aging value must be smaller than the stale one. Spaces that set
nothing keep the global defaults. The same page shows a freshness summary for the space.

Individual pages can be excluded from monitoring from the freshness panel on the page
itself, and whole spaces from the admin dashboard.

## The administrator dashboard

**Confluence → Apps → Content Freshness — Admin.** Four tabs:

| Tab | What it shows |
|---|---|
| **Stale pages** | Everything the last scan classified as stale, with a page-health breakdown (fresh / aging / stale / excluded). Filter by space and by author, copy the list as CSV, or mark the whole list — as currently filtered — as current in one action |
| **History** | The last ten scans — pages scanned, stale and aging counts, and whether the trend is improving |
| **Excluded spaces** | Spaces the scan skips entirely, added by space key |
| **Webhook URL** | An optional URL that receives the scan result as JSON after each scan — including stale page titles and author names, so treat it as a data transfer |

The scan runs **once a week**, automatically, at a time Atlassian schedules. It processes
large instances in batches, so it may take a few minutes to finish; results appear when it
completes. An admin can also start a scan on demand from this dashboard.

The stale list shows at most the **500 oldest** stale pages. If your instance has more, the
dashboard says so — exclude spaces you do not track to bring the rest into view.

## Languages

The interface follows each viewer's own Atlassian language setting, in **English, Polish,
German, French, Spanish, Portuguese and Japanese**. Confluence caches the byline briefly, so
after changing your language the label may need one extra page reload.

## Support

Email [`support@verith.dev`](mailto:support@verith.dev). Please include:

- your Confluence site URL,
- what you expected and what happened instead,
- the approximate time, with time zone — the app's logs are timestamped and contain
  identifiers rather than page titles, so a time narrows an investigation down far faster
  than a description does.

Expected first response: **two business days**.

## Frequently asked

**Does the app change our content?**
No. It holds no write permission of any kind. Every call it makes to Confluence is a read;
everything it records lives in the app's own storage. Marking a page as up to date does not
edit the page.

**Does anything leave our Atlassian site?**
Only if an administrator sets a webhook URL — there is no vendor server to send anything to.
What goes to that URL is the whole scan result, which includes the titles of stale pages and
the names of their last authors, so choose the destination with that in mind. See the
[privacy policy](/content-freshness/privacy-policy/).

**Why is a page still listed as stale after I edited it?**
The dashboard shows the result of the **last scan**, which runs weekly. The label on the
page itself is always live. Run a scan from the dashboard if you need the list refreshed
now.

**Can we be notified when a page goes stale?**
Through the webhook and through the dashboard. The app sends no email of its own and never
posts to a page, so nobody is notified without an administrator setting that up
deliberately.

**What happens when our subscription lapses?**
Reading keeps working — the label, the freshness panel, **Mark as up to date**, per-page
exclusion and every scan result you already have. What stops is starting new scans and
changing configuration.
