# WebsiteLibrary

Canonical Markdown content for
[MainWebsiteUI](https://github.com/VedavardhanaTheertha/MainWebsiteUI), checked out
there as the `library/` Git submodule.

Publish reviewed library commits before updating the website's submodule reference.
A website commit cannot include uncommitted files inside this repository. Generated
website files under `src/gen/` are disposable and must not be edited.

## Source ownership

| Location | Content |
|---|---|
| `general/` | Shared institutional, policy, and legal copy and site metadata |
| `announcement/` | Announcement popup/page content and metadata |
| `learn/` | Learning collection labels, subject order, suggested paths, and subjects |
| `parampara/` | Canonical guru text, portraits, and historical facts |
| `branches/`, `connect/` | Verified branch details and official channels |
| `sevas/` | Canonical offerings, guidelines, and booking data |
| `donations/pages/donation.md` | Canonical localized material-enquiry catalog and prices |
| `dasasahitya/` | Bhakti corpus with attribution and source metadata |
| `events/` | Event records and authored dates |
| Knowledge topic folders | Articles and validated topic-specific metadata |
| `pages/` | Metadata-only references to existing website pages |
| `hero/{dev,prod}/` | Original environment-specific hero groups |

Topic copy belongs in its owning folder, including nested `pages/` documents where
used. Do not create duplicate authorities in language JSON or settings. Short reusable
UI labels and retained media catalogs live in the website's `content/languages/`;
homepage copy and composition live in the settings repository.

## Structured copy and translations

Follow the existing schema for the same document kind. A structured page may use:

```yaml
---
kind: localized-copy
fields:
  pages.example.title:
    en: Example title
---
```

Dotted field names preserve the generated dictionary API. Do not repeat their prose
in an unused Markdown body. Other collections have language-keyed metadata/body
sections or translated sibling files; preserve that collection's format.

The website discovers its languages from JSON filenames and supplies the configured
default language. Missing optional translated content inherits defaults where
supported. Do not invent translations, facts, dates, enrollment links, or citations.
Unsafe paths, duplicate authorities, and invalid metadata fail generation.

Raw HTML is disabled and rendered Markdown is sanitized. Preserve citations,
attribution, verse layout, stable identifiers, and visible knowledge/review status.

## Collection conventions

- Learn's `index.md` has `kind: learning-collection`, ordered subject IDs, and localized
  collection fields. Subjects use `kind: learning-subject`, stable IDs, and a
  `translations` map. Optional metadata must reflect genuinely supplied facts.
- Numeric prefixes on guru filenames determine Parampara order. Translated siblings
  inherit missing optional facts; do not duplicate ordering in a JSON index.
- Project `_index.md` holds collection-wide copy and is not an article. Individual
  project Markdown owns its description and supplied status/year/progress facts.
- Sevas own offerings and their language-specific guidelines. The preserved material
  list and prices live only in `donations/pages/donation.md`; do not duplicate them.
- Official Connect records must be verified. Support email is
  `support@shiroormatha.org`; the WhatsApp destination is a broadcast channel, not
  a private-message inbox.
- Update the Yajna announcement's count and required
  `pages.local_copy.yajna_as_of_date` together (initial snapshot: **2026-07-01**).
  All translations share the same quoted ISO date; never stamp the build date.
  Preserve the temporary Panchanga test-data note, whose localized `panchanga_notice`
  belongs in topic Markdown.
- Preserve editorial article status on collection and related cards. Project
  collections show both editorial and operational project status; homepage remedy
  footnotes also use the authored article status.

## Homepage page references

Each `pages/*.md` record describes an existing website page; `home.md` represents
`/`. Use `kind: page-reference` with `title`, `description`, `image`, `page_type`,
`url`, and `footnote`. Text fields are language-keyed maps; `image` and `url` are
shared strings. Default-language values are required, missing translations inherit
them, and intentionally empty footnotes remain empty.

The homepage resolves four settings lists against these filenames: six top cards,
five icon cards, six bottom cards distinct from the top list, and three explore
cards. A record does not create a route. Keep destinations aligned with concrete
routes rather than query/hash states.

The generated `remidies_carousel` selects three distinct `remedies/` articles once
per generation and shares the result across languages/content variants. Maintain at
least four eligible articles. It uses article title, summary, image, and status plus
the collection's page-reference title; do not author a duplicate settings list.

For image-only edits preserve translated text and other metadata. Keep remote image
URLs consistent with settings image policy, verify availability, and record rights;
public availability alone does not establish permission.

## Review

Follow the website's content/language guidelines and record new asset provenance.
Have devotional, historical, and scholarly claims reviewed by an appropriate person.
Validate integration from the website checkout with `npm run content:validate` and
`npm run ci`, and disclose any incomplete review or validation.
