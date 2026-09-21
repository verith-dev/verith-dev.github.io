# verith.dev — public site

The published vendor site for Verith, served by GitHub Pages at <https://verith.dev>.

This repository is **public by design** and contains nothing but published documents. App
source code lives in separate, private repositories.

| Path | Published at |
|---|---|
| `index.md` | `https://verith.dev/` |
| `content-freshness/index.md` | `https://verith.dev/content-freshness/` |
| `content-freshness/privacy-policy.md` | `https://verith.dev/content-freshness/privacy-policy/` |
| `content-freshness/security.md` | `https://verith.dev/content-freshness/security/` |
| `content-freshness/changelog.md` | `https://verith.dev/content-freshness/changelog/` |

Each page's URL is set by its own `permalink:` front matter, so a file can be renamed
without breaking a URL that the Atlassian Marketplace listing points at. **Those four
Content Freshness URLs are referenced from the Marketplace listing — treat them as fixed.**

Links between pages are written as absolute site paths (`/content-freshness/security/`)
rather than as `.md` filenames, so they resolve identically on the published site.

The documents are maintained in the Content Freshness app repository under `docs/` and
copied here when they change; edit them there first, so the source that describes the app
sits next to the app.
