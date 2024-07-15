# language-identification-data

_Please [contact the Globalise Project](https://globalise.huygens.knaw.nl/contact-us/) if you would like to contribute a language identification._

### Pages with non-Latin script languages

Pages in the Globalise VOC corpus written (or printed) in scripts that our [HTR tool](https://github.com/knaw-huc/loghi) can't process (in effect, nearly all languages written in non-Latin scripts). Currently, these are being discovered largely manually, recorded in a Google Sheets spreadsheet, and then periodically [exported to this repository](https://github.com/globalise-huygens/language-identification-data/blob/main/non-latin-script-pages). This data is then converted to web annotations and uploaded to the Globalise infrastructure. 

The spreadsheet captures both the language ([ISO-639-3](https://en.wikipedia.org/wiki/List_of_ISO_639_language_codes)) and script ([ISO-15924](https://en.wikipedia.org/wiki/ISO_15924)), together with the inventory number, page, URL ([Globalise Transcriptions Viewer](https://transcriptions.globalise.huygens.knaw.nl/)), and a comment field. The languages identified so far include Persian, Chinese, Sinhalese, and Tamil as well as the special case of pages written in cipher, which is classified as a constructed, artificial language. 

Note that the language(s) identified are here based on what is written on the individual pages comprising a document. Thus, a two page spread in an inventory, with the left page in Chinese and right page in Dutch will be recorded here as being in Chinese only (since the page(s) of the Chinese document on the left, as a physical artefact, has no other language written on it. However, a single page document with Chinese and Dutch writing on it will be listed as being in both Chinese and Dutch. To aid future automatic language detection of non-western scripts, we also record in the comments field whether the digital facsimile of the page is oriented incorrectly with respect to the viewer (i.e. sideways or upside down). In the case of a document (e.g. a grammar) where most but not all pages contain examples of non-Latin scripts, only those pages with non-Latin script will be recorded.

[Link to the dataset](non-latin-script-pages)

### Pages with monolingual, non-Dutch, Latin script languages

These are whole pages written in a single, non-Dutch, Latin script. Currently, these correspond to the following languages: Danish, German, English, Spanish, Malay (transcribed in Latin script), Italian, Latin, and Portuguese. The initial identifications are made automatically, and then curated manually in Google Sheets. Exports are periodically uploaded here in TSV format, each upload overwriting the previous 'monolingual-nd-pages.tsv' file so that the changes can be tracked and attributed in GitHub. Once all the identified pages have been curated, the respective language codes and page references are converted to web annotations and uploaded to the Globalise infrastructure. In the future, we will provide a means to allow visitors to our site to suggest corrections for misidentified languages.

### Pages with Latin script languages

These are pages whose `paragraph` layout regions contain text in a Latin script currently corresponding to one or more of the following languages: Dutch, Danish, German, English, Spanish, Malay (transcribed in Latin script), Italian, Latin, and Portuguese. The identifications are made entirely automatically. Only the combined blocks of text in the combined `paragraph` regions are considered when determining the overall language(s) of the page. This information is then converted to web annotations and uploaded to the Globalise infrastructure. Here too, we will later provide a means to allow visitors to our site to suggest corrections for misidentified languages on  pages.

### Lines with Latin script languages

These are the automatically identified languages on a per line, per layout region, per page basis. This data is not curated. Because the per line identifications still contain many errors, they are currently not being converted to web annotations for publication on our infrastructure. 
