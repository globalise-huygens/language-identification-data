# language-identification-data

### Pages with non-Latin script languages

Pages in the Globalise VOC corpus written (or printed) in scripts that Loghi can't process (in effect, nearly all non-Latin scripts) will be recorded here. Currently, this is being done by hand, via a Google Sheets page (contact @kintopp for access), periodically exported to this repository. The spreadsheet captures both the language ([ISO-639](https://en.wikipedia.org/wiki/ISO_639)) and script ([ISO-15924](https://en.wikipedia.org/wiki/ISO_15924)), together with the inventory number, page, URL ([Globalise Transcriptions Viewer](https://transcriptions.globalise.huygens.knaw.nl/)), and a comment field. The languages identified so far include Persian, Chinese, Singhalese, and Tamil as well as the special case of pages written in cipher, which is classified as a constructed, artificial language. 

Note that the language(s) identified are here based on what is written on the individual pages comprising a document. Thus, a two page spread in an inventory, with the left page in Chinese and right page in Dutch will be recorded here as being in Chinese only (since the page(s) of the Chinese document on the left, as a physical artefact, has no other language written on it. However, a single page document with Chinese and Dutch writing on it will be listed as being in both Chinese and Dutch. To aid future automatic language detection of non-western scripts, we also record in the comments field whether the digital facsimile of the page is oriented incorrectly with respect to the viewer (i.e. sideways or upside down). 

Instances of non-Latin scripts in the corpus are first made in Google sheets, then periodically uploaded here in TSV format, each upload overwriting the previous 'pages-nw-scripts.tsv' file so that the changes can be tracked and attributed in GitHub. This data is then converted to web annotations and periodically uploaded to the Globalise infrastructure.

[Link to the dataset](non-latin-script-pages)

### Pages with monolingual, non-Dutch, Latin script languages

These are whole pages written in a single, non-Dutch, Latin script. Currently, these correspond to the following languages: Danish, German, English, Spanish, Malay (transcribed in Latin script), Italian, Latin, and Portuguese. The initial identifications are made automatically, and then curated manually in Google sheets (contact @kintopp for access). Exports are periodically uploaded here in TSV format, each upload overwriting the previous 'monolingual-nd-pages.tsv' file so that the changes can be tracked and attributed in GitHub. Once all the identified pages have been curated, the respective language codes and page references are converted to web annotations and uploaded to the Globalise infrastructure.

### Pages with Latin script languages

These are pages whose `paragraph` layout regions contain text in Latin script corresponding to one or more of the following languages: Dutch, Danish, German, English, Spanish, Malay (transcribed in Latin script), Italian, Latin, and Portuguese. The  identifications are made entirely automatically, and initially recorded on a per layout region, per page basis. However, only the text in the `paragraph` region is considered when determining the overall language(s) of the page. This information is then converted to web annotations and uploaded to the Globalise infrastructure.

### Lines with Latin script languages

These are the automatically identified languages on a per line, per layout region, per page basis. Because this data is currently so noisy, it is not converted to web annotations. 
