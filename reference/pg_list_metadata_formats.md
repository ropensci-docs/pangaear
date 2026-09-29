# Get metadata formats from the Pangaea repository

Get metadata formats from the Pangaea repository

## Usage

``` r
pg_list_metadata_formats(...)
```

## Arguments

- ...:

  Curl debugging options passed on to
  [`oai::list_metadataformats()`](https://docs.ropensci.org/oai/reference/list_metadataformats.html)

## Value

data.frame

## References

[OAI-PMH documentation](https://www.openarchives.org/pmh/)

## See also

wraps
[`oai::list_metadataformats()`](https://docs.ropensci.org/oai/reference/list_metadataformats.html)

Other oai methods:
[`pg_get_record()`](https://docs.ropensci.org/pangaear/reference/pg_get_record.md),
[`pg_identify()`](https://docs.ropensci.org/pangaear/reference/pg_identify.md),
[`pg_list_identifiers()`](https://docs.ropensci.org/pangaear/reference/pg_list_identifiers.md),
[`pg_list_records()`](https://docs.ropensci.org/pangaear/reference/pg_list_records.md),
[`pg_list_sets()`](https://docs.ropensci.org/pangaear/reference/pg_list_sets.md)

## Examples

``` r
if (FALSE) { # \dontrun{
pg_list_metadata_formats()
} # }
```
