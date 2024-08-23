# language-identification-data

Data on languages and language scripts identified in the [Globalise VOC corpus](https://www.nationaalarchief.nl/onderzoeken/archief/1.04.02). Please [contact](https://globalise.huygens.knaw.nl/contact-us/) the Globalise Project if you would like to contribute a new language identification or offer a correction to an existing identification.

To date, we have identified c. 12,200 non-Dutch language pages written (in part or in whole) in French, Latin, English, Portuguese, Spanish, German, Italian, Danish, and Malay (in Latin-script). In addition, we have manually identified a further c. 180 pages written (in part or in whole) in several non-Latin script languages including Malay (in Arabic script), Chinese, Persian, Tamil, and Sinhalese as well as pages written in cipher. 

- [pages.lang.tsv](https://github.com/globalise-huygens/language-identification-data/blob/main/latin-script-pages/pages.lang.tsv) - a concise listing of all automatically identified Latin-script language(s) used on each page in the corpus, including pages only in Dutch, as well as all manually identified non-Latin script pages.
- [nondutch-pages.lang.tsv](https://github.com/globalise-huygens/language-identification-data/blob/main/latin-script-pages/nondutch-pages.lang.tsv) - all automatically identified pages with at least one non-Dutch language; also includes the relevant paragraph region texts and page URLs.
- [unknown-pages.lang.tsv](https://github.com/globalise-huygens/language-identification-data/blob/main/latin-script-pages/unknown-pages.lang.tsv) - all pages whose language(s) could not be automatically identified (e.g. blank pages, pages consisting of numerical tables, upside-down pages); also includes the relevant paragraph region texts and page URLs.
-
[non-latin.scripts.tsv](https://github.com/globalise-huygens/language-identification-data/blob/main/non-latin-script-pages/non-latin.scripts.tsv) - a manually curated list of pages with text in one or more non-Latin (e.g. Arabic) scripts and languages (e.g. Persian), as well as pages in cipher; includes the page URLs but not the paragraph region text.
- [corrections.lang.tsv](https://github.com/globalise-huygens/language-identification-data/blob/main/corrections/corrections.lang.tsv) - a manually curated list of corrections to the four lists named above. 

In these datasets, the languages and language scripts are identified by their three-letter [ISO-639-3](https://en.wikipedia.org/wiki/List_of_ISO_639_language_codes) and [ISO-15924](https://en.wikipedia.org/wiki/ISO_15924) codes.

### Methodology

The starting point for the automatic language identifications is a list of all lines of text in the transcribed Globalise corpus, their content in plaintext, and their layout region (e.g. paragraph, marginalia..). Each character on each line is first examined using a [character based language recognition model](https://github.com/pemistahl/lingua-rs/) for the presence of one or more instances of a pre-selected group of languages known to be present in the corpus (Dutch, French, Latin, English, Portuguese, Spanish, German, Italian, Malay, and Danish). This is then checked, on the word level, with a series of [language-specific lexical models](https://github.com/knaw-huc/globalise-tools/tree/main/pipelines/langdetect/lexicons). To improve the accuracy on Dutch text (for example, to better account for the widespread presence of foreign loan words in French and Latin) the Dutch lexical model was derived from the historical ground truth transcriptions of the Globalise VOC corpus. 

The predictions of the character and word based models are then [reconciled](https://github.com/knaw-huc/globalise-tools/blob/main/scripts/gt_classify_language.py), and a set of [heuristics](https://github.com/knaw-huc/globalise-tools/blob/main/scripts/gt_classify_language.py) are applied to assign one set of per-page language classifications from the individual, per-line classifications. Specifically, a non-Dutch language needs to have been identified on at least three lines or occur (this also applies to Dutch) on at least 25% of the total lines of text in the relevant layout region. These rules were applied to filter out, on the one hand, very short, non-Dutch phrases, but on the other hand be able to accomodate pages that are evenly split between Dutch and non-Dutch in parallel columns. Because on most pages only the paragraph layout region will contain significant amount of text, for the purpose of assigning the per-page language identifications, we have opted to set aside any text found in the remaining layout regions (marginalia, signatures, catch-word, page numbers etc.). The resulting language identifications of all text in the paragraph regions of all pages in the corpus can be found on [pages.lang.tsv](https://github.com/globalise-huygens/language-identification-data/blob/main/latin-script-pages/pages.lang.tsv).  

We expect that researchers will want to review for themselves whether language identifications made by the automatic process described above are sufficiently accurate. For this reason we have collected all the automatic identifications in [pages.lang.tsv](https://github.com/globalise-huygens/language-identification-data/blob/main/latin-script-pages/pages.lang.tsv) and included in this file the text found in their paragraph regions and their page URLs. A second dataset, [unknown-pages.lang.tsv](https://github.com/globalise-huygens/language-identification-data/blob/main/latin-script-pages/unknown-pages.lang.tsv) lists the pages we were not able to automatically identify. This could be for several reasons. In the vast majority of cases this is due to insufficient text on the page – for example blank pages inserted between individual documents. Other potential reasons for an 'unknown' classification include tabular pages with numerical content or pages that were inserted upside-down or sideways into an inventory. Here too, to make it easier for researchers to review the results (and possibly offer their own language identifications) we have included the paragraph region texts and page URLs. 

Naturally, we are also very interested in identifying pages with texts written in non-Latin scripts such as Chinese, Persian, or Tamil and texts written in a secret cipher. These pages are recorded in [non-latin.scripts.tsv](https://github.com/globalise-huygens/language-identification-data/blob/main/non-latin-script-pages/non-latin.scripts.tsv) and we very much welcome further contributions to this list.

Finally, [corrections.lang.tsv](https://github.com/globalise-huygens/language-identification-data/tree/main/corrections/corrections.lang.tsv) consists of a running list of corrections and amendments to our automatic and manual language identifications.
### Caveats

Based on our (thus far, only qualitative) tests, the automatic language identification pipeline has excellent precision (i.e. there are very few cases of Dutch language texts classified as non-Dutch, and the identified non-Dutch texts are almost all correctly assigned to their respective languages) and good recall (i.e. there are still some instances of non-Dutch languages being misidentified as Dutch or unknown). For example, a series of pages in a document are correctly classified as French, but some pages in the French document are 'left out' and misidentified as Dutch. At the same time, in the case of mixed use, deciding how to assign a language(s) to a page is itself subjective. For example, when is there enough English text on a page (alongside some Dutch) for that page to be 'in English'? When it constitutes more than 50% of the total? Or rather, 90%? It is precisely to give researchers the opportunity to apply their own criteria to such questions that we have provided additional datasets non-Dutch and unknown classifications, together with the relevant text extracts and their page URLs for easy reference.     

### Resources

- [langdetect](https://github.com/knaw-huc/globalise-tools/tree/main/pipelines/langdetect) - Pipeline for language detection on the Globalise HTR output
- [lingua-cli](https://github.com/proycon/lingua-cli) - A command-line tool for language detection, it is a simple wrapper around the [lingua-rs](https://github.com/pemistahl/lingua-rs/) library for Rust

### Credits

- Bram Buitendijk, HuC Digital Infrastructure Department
- Maarten van Gompel, HuC Digital Infrastructure Department
- Arno Bosse, HuC Digital Infrastructure Department; Globalise Project
