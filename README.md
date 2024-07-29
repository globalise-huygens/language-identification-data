# language-identification-data

Data on languages and language scripts identified in the Globalise VOC corpus. Please [contact the Globalise Project](https://globalise.huygens.knaw.nl/contact-us/) if you would like to contribute a new language identification or offer a correction to an existing identification.

To date, we have identified pages written (in part or in whole) in the following languages: Dutch, French, Latin, English, Portuguese, Spanish, German, Italian, Malay (in Latin-script), and Danish. In addition, we have manually identified pages written (in part or in whole) in several non-Latin script languages including Malay (in Arabic script), Chinese, Persian, Tamil, and Sinhalese.

- [nondutch-pages.lang.tsv](https://github.com/globalise-huygens/language-identification-data/blob/main/latin-script-pages/nondutch-pages.lang.tsv) - automatically identified pages with a single, non-Dutch, Latin-script language (e.g. French); includes the relevant paragraph region texts
- [mixed-pages.lang.tsv](https://github.com/globalise-huygens/language-identification-data/blob/main/latin-script-pages/mixed-pages.lang.tsv) - automatically identified pages with a mix of Dutch and one or more non-Dutch, Latin-script languages (e.g. Dutch + English); includes the relevant paragraph region texts
- [pages.lang.tsv](https://github.com/globalise-huygens/language-identification-data/blob/main/latin-script-pages/pages.lang.tsv) - all pages, including those only in Dutch, with all automatically identified Latin-script languages; does not include any text
- [non-latin.scripts.tsv](https://github.com/globalise-huygens/language-identification-data/blob/main/non-latin-script-pages/non-latin.scripts.tsv) - manually curated list of pages including text in one or more non-Latin scripts and languages (e.g. Chinese); does not include any text 
- [unknown-pages.lang.tsv](https://github.com/globalise-huygens/language-identification-data/blob/main/latin-script-pages/unknown-pages.lang.tsv) - pages whose languages could not be automatically identified (e.g. blank pages, pages consisting of numerical tables); includes the relevant paragraph region texts
- [corrected-pages.tsv](https://github.com/globalise-huygens/language-identification-data/tree/main/corrections) - manually curated list of corrections from all the above categories; does not include any text

Please see below for more details on the methodology used to define and create these datasets.

### Methodology

The starting point for the automatic language identifications is a list of all lines of text in the transcribed Globalise corpus, their content in plaintext, and their layout region (e.g. paragraph, marginalia..). In brief, each character on each line is first examined using a [character based language recognition model](https://github.com/pemistahl/lingua-rs/) for the presence of one or more instances of a pre-selected group of languages known to be present in the corpus (Dutch, French, Latin, English, Portuguese, Spanish, German, Italian, Malay, and Danish). Note that the HTR transcription platform used by Globalise can only recognize and output text written in Latin-script. This is then checked, on the word level, with a series of [language-specific lexical models](https://github.com/knaw-huc/globalise-tools/tree/main/pipelines/langdetect). To improve its accuracy (for example, to better account for the presence of foreign loan words in e.g. French or Latin) the Dutch lexical model was derived from the historical, ground truth transcriptions of the Globalise VOC corpus. The predictions of the character and word based models are then reconciled, and a set of heuristics are applied to assign one set of per-page language classifications from the individual, per-line classifications. Because on most pages only the paragraph layout region will contain significant amount of text, for the purpose of assigning the per-page language identifications, we have opted to set aside any text found in the remaining layout regions (marginalia, signatures, catch-word, page numbers etc.). The resulting language identifications of all text in the paragraph regions of all pages in the corpus can be found on [pages.lang.tsv](https://github.com/globalise-huygens/language-identification-data/blob/main/latin-script-pages/pages.lang.tsv).  

We suspect, however, that researchers using the Globalise VOC corpus will want to distinguish between instances of Dutch pages with additional language content (e.g. parallel columns of Dutch and English text) and documents written entirely in a single, non-Dutch language such as French or Malay (i.e. Malay transcribed in Latin-script). Additionally, we would like to make it easy as possible for researchers to review for themselves the language identifications made by the automatic process described above. For this reason we have split the identifications colleced in pages.lang.tsv into two derivative datasets, [nondutch-pages.lang.tsv](https://github.com/globalise-huygens/language-identification-data/blob/main/latin-script-pages/nondutch-pages.lang.tsv) and [mixed-pages.lang.tsv](https://github.com/globalise-huygens/language-identification-data/blob/main/latin-script-pages/mixed-pages.lang.tsv), including the text found in their paragraph regions. A third dataset, [unknown-pages.lang.tsv](https://github.com/globalise-huygens/language-identification-data/blob/main/latin-script-pages/unknown-pages.lang.tsv) lists all pages and paragraph region texts which we were not able to automatically identify. This could be for several reasons. By far the most common is insufficient text on the page (for example, in the case of entirely blank pages which were inserted between individual documents in an inventory). Other typical reasons include tabular pages with predominantly numerical content or pages that were inserted upside-down or sideways into an inventory.

Naturally, we are also very interested in identifying those pages that contain or consist entirely of text in non-Latin scripts and languages, such as Chinese, Persian, or Tamil. Currently, we have not yet attempted to recognize these pages automatically, and are instead manually reviewing selections from [unknown-pages.lang.tsv](https://github.com/globalise-huygens/language-identification-data/blob/main/latin-script-pages/unknown-pages.lang.tsv) for erroneous HTR output that might suggest the presence of an e.g. South Asian language. The pages and documents we have found containing non-Latin scripts and languages are recorded in [non-latin.scripts.tsv](https://github.com/globalise-huygens/language-identification-data/blob/main/non-latin-script-pages/non-latin.scripts.tsv). We very much welcome further contributions to this list.

Finally, [corrected-pages.tsv](https://github.com/globalise-huygens/language-identification-data/tree/main/corrections) consists of a running list of corrections and amendments to the above datasets. Each time we publish a new release of the identified language datasets we incorporate the corrections on this list into it and reset the list to zero.

### Resources

- [langdetect](https://github.com/knaw-huc/globalise-tools/tree/main/pipelines/langdetect) - Pipeline for language detection on the Globalise HTR output
- [lingua-cli](https://github.com/proycon/lingua-cli) - A command-line tool for language detection, it is a simple wrapper around the [lingua-rs](https://github.com/pemistahl/lingua-rs/) library for Rust

### Credits

- Bram Buitendijk, HuC Digital Infrastructure Department
- Maarten van Gompel, HuC Digital Infrastructure Department
- Arno Bosse, HuC Digital Infrastructure Department; Globalise Project
