# Changelog

## pangaear 1.1.0

CRAN release: 2021-05-14

### MINOR IMPROVEMENTS

- add markdown pkg to Suggests for vignette

## pangaear 1.0.0

CRAN release: 2020-01-22

### MINOR IMPROVEMENTS

- vcr caching for pg_data tests, local only as files are too big
  ([\#74](https://github.com/ropensci/pangaear/issues/74))
- vignette title fix
  ([\#73](https://github.com/ropensci/pangaear/issues/73))
- `pg_search` fix for searching with a bounding box that crosses
  180/-180 longitude: not a fix in this package, but the remote data
  source fixed a problem reported from a user of this package
  ([\#71](https://github.com/ropensci/pangaear/issues/71))

## pangaear 0.8.2

CRAN release: 2019-09-12

### BUG FIXES

- detected from cran checks, only failing on debian clang r-devel:
  change `pg_search` tests to use `preserve_exact_body_bytes = TRUE` in
  the
  [`vcr::use_cassette()`](https://docs.ropensci.org/vcr/reference/use_cassette.html)
  call so `yaml` package doesn’t fail on loading it
  ([\#72](https://github.com/ropensci/pangaear/issues/72))

## pangaear 0.8.0

CRAN release: 2019-08-19

### NEW FEATURES

- now using package `hoardr` for managing caching, replacing package
  `rappdirs`; new object `pg_cache`, an R6 class, with methods for
  managing where you cache files, deleting them, listing them, etc.
  Importantly, you can set the full cache path now, not just the folder
  within a set directory
  ([\#66](https://github.com/ropensci/pangaear/issues/66))
  ([\#69](https://github.com/ropensci/pangaear/issues/69))

### MINOR IMPROVEMENTS

- most tests using `vcr` now for http reqeust caching
  ([\#70](https://github.com/ropensci/pangaear/issues/70))
- output of
  [`pg_data()`](https://docs.ropensci.org/pangaear/reference/pg_data.md)
  now includes a `metadata` slot with parsed metadata from text files
  (only included when the file is a txt file); `parameters` slot that’s
  part of the metadata is partially parsed into an unnamed list
  ([\#67](https://github.com/ropensci/pangaear/issues/67))

### BUG FIXES

- fix in
  [`pg_data()`](https://docs.ropensci.org/pangaear/reference/pg_data.md):
  Pangaea changed how links are organized for datasets, fixed now
  ([\#65](https://github.com/ropensci/pangaear/issues/65))
- fix in
  [`pg_data()`](https://docs.ropensci.org/pangaear/reference/pg_data.md):
  response content type header changed - a space was added, breaking the
  content type check; now not sensitive to the space
  ([\#68](https://github.com/ropensci/pangaear/issues/68))

## pangaear 0.6.0

CRAN release: 2018-01-03

### MINOR IMPROVEMENTS

- Added a vignette
  ([\#62](https://github.com/ropensci/pangaear/issues/62))
- replaced `httr` pkg with `crul` for HTTP requests
  ([\#55](https://github.com/ropensci/pangaear/issues/55))
- Some datasets require login on the Pangaea platform - we now detect
  this in `pg_data` and skip the file download with a message saying so.
  Eventually we hope to fix this to allow uesrs to input credentials to
  get the file(s)
  ([\#59](https://github.com/ropensci/pangaear/issues/59))

## pangaear 0.3.0

CRAN release: 2017-03-08

### NEW FEATURES

- New function `pg_search_es` - an interface to Pangaea’s Elasticsearch
  query interface.

### MINOR IMPROVEMENTS

- added more tests
  ([\#57](https://github.com/ropensci/pangaear/issues/57))
- now using markdown in docs
- tidy code to 80 line width

### BUG FIXES

- fixed bug in oai functions due to changed base url for the Pangaea OAI
  server ([\#53](https://github.com/ropensci/pangaear/issues/53))
- Fix to `pg_search` as search portal now has offset param - so if more
  than 500 results need to page through them with the `offset` parameter
  ([\#56](https://github.com/ropensci/pangaear/issues/56))

## pangaear 0.2.4

CRAN release: 2016-10-07

### MINOR IMPROVEMENTS

- Improved examples in the OAI methods to make sure they work regardless
  of when the user runs them

### BUG FIXES

- Fixes to
  [`pg_search()`](https://docs.ropensci.org/pangaear/reference/pg_search.md)
  needed due to changes in the Pangaea website. Nearly identical
  functionality, but one parameter switch (`env` param is now `topic`).
  More parameters may be added in the future. New fields are added to
  output, added to docs for the function. Now importing `jsonlite` as a
  result of these changes
  ([\#50](https://github.com/ropensci/pangaear/issues/50))
- Fixes to
  [`pg_data()`](https://docs.ropensci.org/pangaear/reference/pg_data.md)
  needed due to changes in the Pangaea website. Nothing should be
  different for the user.
  ([\#51](https://github.com/ropensci/pangaear/issues/51))

## pangaear 0.2.0

CRAN release: 2016-05-07

### MINOR IMPROVEMENTS

- Dropped `XML`, using `xml2` now
  ([\#42](https://github.com/ropensci/pangaear/issues/42))
- Using `rappdirs` package now for determing caching path on user’s
  machine ([\#46](https://github.com/ropensci/pangaear/issues/46))
- using `tibble` now for compact data.frame representations
  ([\#47](https://github.com/ropensci/pangaear/issues/47))
- Dropped `methods` dependency
  ([\#48](https://github.com/ropensci/pangaear/issues/48))
- Added test suite
  ([\#45](https://github.com/ropensci/pangaear/issues/45))

### BUG FIXES

- Fixes to
  [`pg_search()`](https://docs.ropensci.org/pangaear/reference/pg_search.md) -
  introduced due to changes in Pangaea website
  ([\#44](https://github.com/ropensci/pangaear/issues/44))

## pangaear 0.1.0

CRAN release: 2015-11-24

- Released to CRAN.
