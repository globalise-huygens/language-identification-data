These are the main results from the [language detection](https://github.com/knaw-huc/globalise-tools/tree/main/pipelines/langdetect) pipeline:

* `pages.lang.tsv` - All language classification per page

Derived results with paragraph region text for inspection:

* `nondutchmono-pages.lang.tsv` - Pages that have been classified exclusively non-Dutch and are monolingual
* `mixed-pages.lang.tsv` - Pages that have been classified as a mixture of any two language (may or may not contain dutch as part of the mix)
* `unknown-pages.lang.tsv` - Pages classified as unknown (no automatic language classification possible)
