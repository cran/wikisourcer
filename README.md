
# wikisourcer <img src="man/figures/logo.png" align="right" />

The **wikisourcer** R package helps you download public domain works
from the free library [Wikisource](https://wikisource.org/).

It includes two functions for downloading books and pages by url.

  - `wikisource_book()` to download a book
  - `wikisource_page()` to download a page

### Installation

``` r
install.packages("wikisourcer") # install release version from CRAN
devtools::install_github("lgnbhl/wikisourcer") # install development version from GitHub
```

### Minimal examples

Download Voltaire’s philosophical novel *Candide*.

``` r
library(wikisourcer)

wikisource_book("https://en.wikisource.org/wiki/Candide")
```

Download Voltaire’s *Candide* books in French, Spanish and Italian.

``` r
library(purrr)

fr <- "https://fr.wikisource.org/wiki/Candide,_ou_l%E2%80%99Optimisme/Garnier_1877"
es <- "https://es.wikisource.org/wiki/C%C3%A1ndido,_o_el_optimismo"
it <- "https://it.wikisource.org/wiki/Candido"

purrr::map_df(c(fr, es, it), wikisource_book)
```

Download *Sonnet 18* of William Shakespeare.

``` r
library(wikisourcer)

wikisource_page("https://en.wikisource.org/wiki/Sonnet_18_(Shakespeare)", "Sonnet 18")
```

Download 154 Sonnets of William Shakespeare.

``` r
library(purrr)

urls <- paste0("https://en.wikisource.org/wiki/Sonnet_", 1:154, "_(Shakespeare)") #154 urls

purrr::map2_df(urls, paste0("Sonnet ", 1:154), wikisource_page)
```

For more information on how to use **wikisourcer**, please read [the
vignette](https://lgnbhl.github.io/wikisourcer/articles/wikisourcer.html).
