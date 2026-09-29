# Identify information about the Pangaea repository

Identify information about the Pangaea repository

## Usage

``` r
pg_identify(...)
```

## Arguments

- ...:

  Curl debugging options passed on to
  [`oai::id()`](https://docs.ropensci.org/oai/reference/id.html)

## Value

list

## References

[OAI-PMH documentation](https://www.openarchives.org/pmh/)

## See also

wraps [`oai::id()`](https://docs.ropensci.org/oai/reference/id.html)

Other oai methods:
[`pg_get_record()`](https://docs.ropensci.org/pangaear/reference/pg_get_record.md),
[`pg_list_identifiers()`](https://docs.ropensci.org/pangaear/reference/pg_list_identifiers.md),
[`pg_list_metadata_formats()`](https://docs.ropensci.org/pangaear/reference/pg_list_metadata_formats.md),
[`pg_list_records()`](https://docs.ropensci.org/pangaear/reference/pg_list_records.md),
[`pg_list_sets()`](https://docs.ropensci.org/pangaear/reference/pg_list_sets.md)

## Examples

``` r
if (FALSE) { # \dontrun{
pg_identify()
} # }
```
