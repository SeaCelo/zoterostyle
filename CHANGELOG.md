# Changelog

All notable changes to this citation style should be documented in this file.

### Structural Changes
- Refactored bibliography/citation logic to better separate responsibilities across macros (`author`, `author-short`, `access`, `access-date`, `locators`, `article-date`, `report-date`).
- Added explicit citation sorting (author -> year -> title) and aligned bibliography tie-breaking on title for same-author/same-year items.
- Added a dedicated bibliography branch for `document` items and enhanced `speech` handling to include place/date metadata when present.
- Updated CSL metadata timestamp: `<updated>2026-02-11T00:00:00+00:00</updated>`.

### Core Style Behavior Updates
- Standardized no-date term to `n.d.`.
- Standardized access-date label to `accessed on`.
- Updated in-text et al punctuation behavior to avoid comma before `and others`.
- Set repeated-author substitute to a 10-underscore line (`__________`), per UN convention.
- Added `title-short` fallback in in-text citations when no author is present.
- Improved no-author bibliography fallback for web-like records (`webpage`, `software`, `dataset`, `document`) to be title-led.
- Updated web/database access formatting to `Available at ...` with conditional access-date output.
- Added page rendering to periodical references where pages are available.
- Updated periodical date rendering:
  - journal/magazine month/season in parentheses when issue is present
  - newspaper date handling by day and month
- Removed quotation marks from several title contexts to align with UN author-date examples (reports/chapters/speeches/fallback blocks).
- Updated chapter/conference item publication block to use place/publisher with colon separation.
- Refined report-number behavior:
  - numeric report numbers render with `No.`
  - symbolic UN-style report numbers (for example `A/CONF...`, `S/...`) are preserved without forced `No.`
- Added report-specific date output (`report-date`) and improved report punctuation order.

### UN-Specific Alignment Notes
- Kept `Sales No.` behavior tied to Zotero `Loc. in Archive` (`archive_location`) for UN publications that carry sales numbers.
- Confirmed symbolic UN document/report references are preserved when entered as report numbers.
- Removed automatic genre-driven `United Nations publication` phrase rendering from CSL output (project decision: conservative, data-neutral default).

### Test Coverage Expansion (Local Fixtures)
- Added/expanded fixtures for UN guide examples and edge cases, including:
  - UN publication and specialized-agency publication examples.
  - Conference report examples including corrigendum symbol chains.
  - Public statement and unpublished-paper patterns.
  - Same-author and co-author ordering/substitute-line tests.
  - Yearbook reference pattern.
  - Additional periodical, newspaper, and organization-author examples.

### Pending Issues
- Author-publisher deduplication for organization names is not implemented.
  - Reason: CSL has limited safe conditional logic for reliably suppressing publisher when it duplicates institutional author text across all data-entry variants.
- Initial-article normalization in sort order (for example ignoring leading "The") is not enforced.
  - Reason: Zotero/CSL sorting does not provide a robust, style-level mechanism to normalize leading articles consistently without introducing regressions.
- Conditional URL omission for easily discoverable web sources remains manual/editorial.
  - Reason: the UN guide treats this as a judgment call; CSL has no contextual signal for "easily located through search."
- Automatic inference of "United Nations publication" phrase is intentionally disabled.
  - Reason: reliable detection cannot be derived deterministically from author/publisher metadata alone; explicit metadata remains the safer approach.
