# Get record from the Pangaea repository

Get record from the Pangaea repository

## Usage

``` r
pg_get_record(identifier, prefix = "oai_dc", as = "df", ...)
```

## Arguments

- identifier:

  Dataset identifier. See Examples.

- prefix:

  A character string to specify the metadata format in OAI-PMH requests
  issued to the repository. The default (`oai_dc`) corresponds to the
  mandatory OAI unqualified Dublin Core metadata schema.

- as:

  (character) What to return. One of "df" (for data.frame; default),
  "list", or "raw" (raw text)

- ...:

  Curl debugging options passed on to
  [`oai::get_records()`](https://docs.ropensci.org/oai/reference/get_records.html)

## Value

XML character string, data.frame, or list, depending on what requested
with the `as` parameter

## References

[OAI-PMH documentation](https://www.openarchives.org/pmh/)

## See also

wraps
[`oai::get_records()`](https://docs.ropensci.org/oai/reference/get_records.html)

Other oai methods:
[`pg_identify()`](https://docs.ropensci.org/pangaear/reference/pg_identify.md),
[`pg_list_identifiers()`](https://docs.ropensci.org/pangaear/reference/pg_list_identifiers.md),
[`pg_list_metadata_formats()`](https://docs.ropensci.org/pangaear/reference/pg_list_metadata_formats.md),
[`pg_list_records()`](https://docs.ropensci.org/pangaear/reference/pg_list_records.md),
[`pg_list_sets()`](https://docs.ropensci.org/pangaear/reference/pg_list_sets.md)

## Examples

``` r
if (FALSE) { # \dontrun{
pg_get_record(identifier = "oai:pangaea.de:doi:10.1594/PANGAEA.788382")
pg_get_record(identifier = "oai:pangaea.de:doi:10.1594/PANGAEA.269656",
prefix="iso19139")
pg_get_record(identifier = "oai:pangaea.de:doi:10.1594/PANGAEA.269656",
prefix="dif")

# invalid record id
# pg_get_record(identifier = "oai:pangaea.de:doi:10.1594/PANGAEA.11111")
# pg_get_record(identifier = "oai:pangaea.de:doi:10.1594/PANGAEA.11111",
#   prefix="adfadf")
} # }
```
