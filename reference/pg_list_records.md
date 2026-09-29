# List records from Pangaea

List records from Pangaea

## Usage

``` r
pg_list_records(
  prefix = "oai_dc",
  from = NULL,
  until = NULL,
  set = NULL,
  token = NULL,
  as = "df",
  ...
)
```

## Arguments

- prefix:

  A character string to specify the metadata format in OAI-PMH requests
  issued to the repository. The default (`oai_dc`) corresponds to the
  mandatory OAI unqualified Dublin Core metadata schema.

- from:

  Character string giving datestamp to be used as lower bound for
  datestamp-based selective harvesting (i.e., only harvest records with
  datestamps in the given range). Dates and times must be encoded using
  ISO 8601. The trailing Z must be used when including time. OAI-PMH
  implies UTC for data/time specifications.

- until:

  Character string giving a datestamp to be used as an upper bound, for
  datestamp-based selective harvesting (i.e., only harvest records with
  datestamps in the given range).

- set:

  A character string giving a set to be used for selective harvesting
  (i.e., only harvest records in the given set).

- token:

  (character) a token previously provided by the server to resume a
  request where it last left off. 50 is max number of records returned.
  We will loop for you internally to get all the records you asked for.

- as:

  (character) What to return. One of "df" (for data.frame; default),
  "list", or "raw" (raw text)

- ...:

  Curl debugging options passed on to
  [`oai::list_records()`](https://docs.ropensci.org/oai/reference/list_records.html)

## Value

XML character string, data.frame, or list, depending on what requested
witht the `as` parameter

## References

[OAI-PMH documentation](https://www.openarchives.org/pmh/)

## See also

wraps
[`oai::list_records()`](https://docs.ropensci.org/oai/reference/list_records.html)

Other oai methods:
[`pg_get_record()`](https://docs.ropensci.org/pangaear/reference/pg_get_record.md),
[`pg_identify()`](https://docs.ropensci.org/pangaear/reference/pg_identify.md),
[`pg_list_identifiers()`](https://docs.ropensci.org/pangaear/reference/pg_list_identifiers.md),
[`pg_list_metadata_formats()`](https://docs.ropensci.org/pangaear/reference/pg_list_metadata_formats.md),
[`pg_list_sets()`](https://docs.ropensci.org/pangaear/reference/pg_list_sets.md)

## Examples

``` r
if (FALSE) { # \dontrun{
pg_list_records(set='citable', from=Sys.Date()-1, until=Sys.Date())

# When no results found > "'noRecordsMatch'"
# pg_list_records(set='geomound', from='2015-01-01', until='2015-01-01')

pg_list_records(prefix="iso19139", set='citable', from=Sys.Date()-1,
  until=Sys.Date())

## FIXME - below are broken
# pg_list_records(prefix="dif", set='citable', from=Sys.Date()-4,
#   until=Sys.Date())
# pg_list_records(prefix="dif", set='project4094', from=Sys.Date()-4,
#   until=Sys.Date())
} # }
```
