# United Nations DESA Zotero Style

This CSL style is for United Nations publications and related references in author-date format. It was created to match the UN style guide as closely as possible for Zotero output.

UN style guide: https://www.un.org/dgacm/en/content/editorial-manual

Main style file:
- `united-nations-desa.csl`

Upstream CSL PR:
- https://github.com/citation-style-language/styles/pull/6523

Special use cases:
- If a UN sales number is available for a source, enter it in `Loc. in Archive` in Zotero. The style will print it as `Sales No. ...` in the reference.

## Testing

Test files:
- `tests/un-style-test.rdf` (fixture dataset to import into Zotero)
- `tests/un-style-guide-reference.pdf` (combined UN style-guide reference pages)

How to run a style check:
1. In Zotero, import `tests/un-style-test.rdf` (`File` -> `Import`).
2. Ensure the style `united-nations-desa.csl` is installed in Zotero.
3. Select the imported test items and create a bibliography with the style `United Nations - DESA`.
4. Export or print the generated bibliography to PDF.
5. Compare the generated bibliography against `tests/un-style-guide-reference.pdf` and confirm formatting and ordering behavior.

## Pending Issues

| Issue | Why Not Addressed Yet |
| --- | --- |
| Author-publisher deduplication for organization names | CSL does not provide a reliable, low-risk way to suppress publisher text only when it duplicates institutional author strings across varied metadata patterns. |
| Initial-article normalization in sorting (for example ignoring leading "The") | Zotero/CSL sorting does not provide a robust style-level mechanism to normalize leading articles without side effects. |
| Conditional URL omission for easily discoverable web sources | The UN guide treats this as editorial judgment; CSL has no context signal for "easily located through search." |
| Some `document` records with `Type` stored only in `Extra` may not print URL/access text | In Zotero RDF, `Type: ...` in `Extra` is not always mapped to CSL `genre`/type fields consistently, so one edge-case document can bypass expected `Available at ...` rendering. |
| Automatic inference of the phrase "United Nations publication" | Reliable detection cannot be derived deterministically from author/publisher metadata alone, so this remains a manual/data-driven decision. |
| Masthead document symbol/date ordering | UN masthead examples place date before symbol (for example `... 12 December. S/...`), but applying that reliably only to masthead-like reports is not deterministic with current CSL/Zotero metadata signals. |
