# List the set structure of the Pangaea repository

List the set structure of the Pangaea repository

## Usage

``` r
pg_list_sets(token = NULL, as = "df", ...)
```

## Arguments

- token:

  (character) a token previously provided by the server to resume a
  request where it last left off. 50 is max number of records returned.
  We will loop for you internally to get all the records you asked for.

- as:

  (character) What to return. One of "df" (for data.frame; default),
  "list", or "raw" (raw text)

- ...:

  Curl debugging options passed on to
  [`oai::list_sets()`](https://docs.ropensci.org/oai/reference/list_sets.html)

## Value

XML character string, data.frame, or list, depending on what requested
with the `as` parameter

## References

[OAI-PMH documentation](https://www.openarchives.org/pmh/)

## See also

wraps
[`oai::list_sets()`](https://docs.ropensci.org/oai/reference/list_sets.html)

Other oai methods:
[`pg_get_record()`](https://docs.ropensci.org/pangaear/reference/pg_get_record.md),
[`pg_identify()`](https://docs.ropensci.org/pangaear/reference/pg_identify.md),
[`pg_list_identifiers()`](https://docs.ropensci.org/pangaear/reference/pg_list_identifiers.md),
[`pg_list_metadata_formats()`](https://docs.ropensci.org/pangaear/reference/pg_list_metadata_formats.md),
[`pg_list_records()`](https://docs.ropensci.org/pangaear/reference/pg_list_records.md)

## Examples

``` r
if (FALSE) { # \dontrun{
pg_list_sets()
pg_list_sets(as = "list")
pg_list_sets(as = "raw")
} # }
```
