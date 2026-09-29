# Search the Pangaea database

Search the Pangaea database

## Usage

``` r
pg_search(
  query,
  count = 10,
  offset = 0,
  topic = NULL,
  bbox = NULL,
  mindate = NULL,
  maxdate = NULL,
  ...
)
```

## Arguments

- query:

  (character) Query terms. You can refine a search by prefixing the
  term(s) with a category, one of citation, reference, parameter, event,
  project, campaign, or basis. See examples.

- count:

  (integer) Number of items to return. Default: 10. Maximum: 500. Use
  `offset` parameter to page through results - see examples

- offset:

  (integer) Record number to start at. Default: 0

- topic:

  (character) topic area: one of NULL (all areas), "Agriculture",
  "Atomosphere", "Biological Classification", "Biospshere", "Chemistry",
  "Cryosphere", "Ecology", "Fisheries", "Geophysics", "Human
  Dimensions", "Lakes & Rivers", "Land Surface", "Lithosphere",
  "Oceans", "Paleontology"

- bbox:

  (numeric) A bounding box, of the form: minlon, minlat, maxlon, maxlat

- mindate, maxdate:

  (character) Dates to search for, of the form "2014-10-28"

- ...:

  Curl options passed on to
  [crul::verb-GET](https://docs.ropensci.org/crul/reference/verb-GET.html)

## Value

tibble/data.frame with the structure:

- score: match score, higher is a better match

- doi: the DOI for the data package

- size: size number

- size_measure: size measure, one of "data points" or "datasets"

- citation: citation for the data package

- supplement_to: citation for what the data package is a supplement to

## Details

This is a thin wrapper around the GUI search interface on the page
<https://www.pangaea.de>. Everything you can do there, you can do here.

## See also

[`pg_search_es()`](https://docs.ropensci.org/pangaear/reference/pg_search_es.md)

## Examples

``` r
if (FALSE) { # \dontrun{
pg_search(query='water')
pg_search(query='water', count=2)
pg_search(query='water', count=20)
pg_search(query='water', mindate="2013-06-01", maxdate="2013-07-01")
pg_search(query='water', bbox=c(-124.2, 41.8, -116.8, 46.1))
pg_search(query='reference:Archer')
pg_search(query='parameter:"carbon dioxide"')
pg_search(query='event:M2-track')
pg_search(query='event:TT011_2-CTD31')
pg_search(query='project:Joint Global Ocean Flux Study')
pg_search(query='campaign:M2')
pg_search(query='basis:Meteor')

# paging with count and offset
# max is 500 records per request - if you need > 500, use offset and count
res1 <- pg_search(query = "florisphaera", count = 500, offset = 0)
res2 <- pg_search(query = "florisphaera", count = 500, offset = 500)
res3 <- pg_search(query = "florisphaera", count = 500, offset = 1000)
do.call("rbind.data.frame", list(res1, res2, res3))

# get attributes: maxScore, totalCount, and offset
res <- pg_search(query='water', bbox=c(-124.2, 41.8, -116.8, 46.1))
attributes(res)
attr(res, "maxScore")
attr(res, "totalCount")
attr(res, "offset")

# curl options
pg_search(query='citation:Archer', verbose = TRUE)
} # }
```
