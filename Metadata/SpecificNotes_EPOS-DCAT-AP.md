# About the details of EPOS-DCAT-AP

* Author: Tim Sonnemann
* Created: 2018-02-14

A general __issue__ is the inconsistent description in the EPOS-DCAT-AP vocabulary Excel file. See examples below

* `dct.language` is used in multiple classes, but only in `eposPerson` it is described to be only 2-char codes (e.g. 'en' for English)
    - At first it had no specification, GitHub issue #19 was raised because of that.
    - It was pointed out a '2char only rule' clashes with INSPIRE metadata which allow 5char, e.g. 'en-GB'
    - Apparently still open issue!
* identifier and its type not clearly defined, e.g. DOI, ISSN, UUID, checksum
    - a webservice can have DOI, a dataset or single file can have DOI
* not clear how to define `temporal extent`, see issue #31
    - Data(set) and webservice have this property
    - not clear how to express a time range here
    - `dct:temporal` is a link to class `dct:PeriodOfTime`, which has start/end times
    - Seen like that in webservice metadata XML for DynVolc, omits `schema:endDate`
    - maybe follow that example, can be used for data as well

 
