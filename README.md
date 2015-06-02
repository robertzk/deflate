# Deflate R objects

The naive method of serializing R objects uses the built-in `saveRDS`. However,
this method has a major problem! Since R function objects carry information
about parent environments (that is, closures usually contain more information
than is needed), it is possible to get bloated R objects when serializing,
especially when these include function, formula, or environment objects.

The deflate package will take an R object and inspect it, pruning away
unnecessary pieces so that the final object may be serialized without
additional space bloat. In some cases, this has reduce 5GB+ objects
to several megabytes.

