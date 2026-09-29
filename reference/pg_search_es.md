# Search the Pangaea database with Elasticsearch

Search the Pangaea database with Elasticsearch

## Usage

``` r
pg_search_es(
  query = NULL,
  size = 10,
  from = NULL,
  source = NULL,
  df = NULL,
  analyzer = NULL,
  default_operator = NULL,
  explain = NULL,
  sort = NULL,
  track_scores = NULL,
  timeout = NULL,
  terminate_after = NULL,
  search_type = NULL,
  lowercase_expanded_terms = NULL,
  analyze_wildcard = NULL,
  version = FALSE,
  ...
)
```

## Arguments

- query:

  (character) Query terms..

- size:

  (character) The number of hits to return. Pass in as a character
  string to avoid problems with large number conversion to scientific
  notation. Default: 10. The default maximum is 10,000 - however, you
  can change this default maximum by changing the
  `index.max_result_window` index level parameter.

- from:

  (character) The starting from index of the hits to return. Pass in as
  a character string to avoid problems with large number conversion to
  scientific notation. Default: 0

- source:

  (character) character vector of fields to return

- df:

  (character) The default field to use when no field prefix is defined
  within the query.

- analyzer:

  (character) The analyzer name to be used when analyzing the query
  string.

- default_operator:

  (character) The default operator to be used, can be `AND` or `OR`.
  Default: `OR`

- explain:

  (logical) For each hit, contain an explanation of how scoring of the
  hits was computed. Default: `FALSE`

- sort:

  (character) Sorting to perform. Can either be in the form of
  fieldName, or `fieldName:asc`/`fieldName:desc`. The fieldName can
  either be an actual field within the document, or the special `_score`
  name to indicate sorting based on scores. There can be several sort
  parameters (order is important).

- track_scores:

  (logical) When sorting, set to `TRUE` in order to still track scores
  and return them as part of each hit.

- timeout:

  (numeric) A search timeout, bounding the search request to be executed
  within the specified time value and bail with the hits accumulated up
  to that point when expired. Default: no timeout.

- terminate_after:

  (numeric) The maximum number of documents to collect for each shard,
  upon reaching which the query execution will terminate early. If set,
  the response will have a boolean field terminated_early to indicate
  whether the query execution has actually terminated_early. Default: no
  terminate_after

- search_type:

  (character) The type of the search operation to perform. Can be
  `query_then_fetch` (default) or `dfs_query_then_fetch`. Types `scan`
  and `count` are deprecated.

- lowercase_expanded_terms:

  (logical) Should terms be automatically lowercased or not. Default:
  `TRUE`.

- analyze_wildcard:

  (logical) Should wildcard and prefix queries be analyzed or not.
  Default: `FALSE`

- version:

  (logical) Print the document version with each document.

- ...:

  Curl options passed on to
  [crul::verb-GET](https://docs.ropensci.org/crul/reference/verb-GET.html)

## Value

tibble/data.frame, empty if no results

## Details

An interface to Pangaea's Elasticsearch query interface. You can also
just use [elastic](https://github.com/ropensci/elastic) package to
interact with it. The base URL is
https://ws.pangaea.de/es/pangaea/panmd/\_search

## See also

[`pg_search()`](https://docs.ropensci.org/pangaear/reference/pg_search.md)

## Examples

``` r
if (FALSE) { # \dontrun{
(res <- pg_search_es())
attributes(res)
attr(res, "total")
attr(res, "max_score")

pg_search_es(query = 'water', source = c('parentURI', 'minElevation'))
pg_search_es(query = 'water', size = 3)
pg_search_es(query = 'water', size = 3, from = 10)

pg_search_es(query = 'water sky', default_operator = "OR")
pg_search_es(query = 'water sky', default_operator = "AND")

pg_search_es(query = 'water', sort = "minElevation")
pg_search_es(query = 'water', sort = "minElevation:desc")
} # }
```
