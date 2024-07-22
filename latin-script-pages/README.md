These are the main results from the [language detection](https://github.com/knaw-huc/globalise-tools/tree/main/pipelines/langdetect) pipeline:

* `pages.lang.tsv` - All language classification per page

Derived results with paragraph region text for inspection:

* `nondutch-pages.lang.tsv` - Pages that have been classified as exclusively non-Dutch
* `mixed-pages.lang.tsv` - Pages that have been classified as non-Dutch wholly or in part (may be mixed with Dutch)
* `unknown-pages.lang.tsv` - Pages classified as unknown (no automatic language classification possible)
