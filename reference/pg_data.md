# Download data from Pangaea.

Grabs data as a dataframe or list of dataframes from a Pangaea data
repository URI; see: <https://www.pangaea.de/>

## Usage

``` r
pg_data(doi, overwrite = TRUE, mssgs = TRUE, ...)
```

## Arguments

- doi:

  DOI of Pangaeae single dataset, or of a collection of datasets.
  Expects either just a DOI of the form `10.1594/PANGAEA.746398`, or
  with the URL part in front, like
  <https://doi.pangaea.de/10.1594/PANGAEA.746398>

- overwrite:

  (logical) Ovewrite a file if one is found with the same name

- mssgs:

  (logical) print information messages. Default: `TRUE`

- ...:

  Curl options passed on to
  [crul::verb-GET](https://docs.ropensci.org/crul/reference/verb-GET.html)

## Value

One or more items of class pangaea, each with the doi, parent doi (if
many dois within a parent doi), url, citation, path, and data object.
Data object depends on what kind of file it is. For tabular data, we
print the first 10 columns or so; for a zip file we list the files in
the zip (but leave it up to the user to dig unzip and get files from the
zip file); for png files, we point the user to read the file in with
[`png::readPNG()`](https://rdrr.io/pkg/png/man/readPNG.html)

## Details

Data files are stored in an operating system appropriate location. Run
`pg_cache$cache_path_get()` to get the storage location on your machine.
See [pg_cache](https://docs.ropensci.org/pangaear/reference/pg_cache.md)
for more information, including how to set a different base path for
downloaded files.

Some files/datasets require the user to be logged in. For now we just
pass on these - that is, give back nothing other than metadata.

## References

<https://www.pangaea.de>

## Author

Naupaka Zimmerman, Scott Chamberlain

## Examples

``` r
if (FALSE) { # \dontrun{
# a single file
(res <- pg_data(doi='10.1594/PANGAEA.807580'))
res[[1]]$doi
res[[1]]$citation
res[[1]]$data
res[[1]]$metadata

# another single file
pg_data(doi='10.1594/PANGAEA.807584')

# Many files
(res <- pg_data(doi='10.1594/PANGAEA.761032'))
res[[1]]
res[[2]]

# Manipulating the cache
## list files in the cache
pg_cache$list()

## clear all data
# pg_cache$delete_all()
pg_cache$list()

## clear a single dataset by DOI
pg_data(doi='10.1594/PANGAEA.812093')
pg_cache$list()
path <- grep("PANGAEA.812093", pg_cache$list(), value = TRUE)
pg_cache$delete(path)
pg_cache$list()

# search for datasets, then pass in DOIs
(searchres <- pg_search(query = 'birds', count = 20))
pg_data(searchres$doi[1])

# png file
pg_data(doi = "10.1594/PANGAEA.825428")

# zip file
pg_data(doi = "10.1594/PANGAEA.860500")

# login required
## we skip file download
pg_data("10.1594/PANGAEA.788547")
} # }
```
