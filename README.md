lme4: Mixed-effects models in R. 
====

[![Build Status](https://travis-ci.org/lme4/lme4.svg?branch=master)](https://travis-ci.org/lme4/lme4)

## Recent/release notes

* The major user-visible change in release 1.1-7 is that most of the recent rash of false convergence warnings have been cleared up.  As far as we know, any convergence warnings you get with `lme4` >= 1.1-7 are actually cause for concern and should be handled in the usual ways (e.g. try alternative optimizers within `lme4` or alternative R packages/software to cross-check the results; explore data for outliers or complete separation; center and scale continuous predictors).
* Otherwise, see the `NEWS` file (or  `news(Version=="1.1.7",package="lme4")`).

## Features

* Efficient for large data sets, using algorithms from the 
[Eigen](http://eigen.tuxfamily.org/index.php?title=Main_Page)
linear algebra package via the [RcppEigen](http://cran.r-project.org/web/packages/RcppEigen/index.html)
interface layer.
* Allows arbitrarily many nested and crossed random effects.
* Fits generalized linear mixed models (GLMMs) and nonlinear mixed models (NLMMs) via Laplace approximation
or adaptive Gauss-Hermite quadrature; GLMMs allow user-defined families and link functions.
* Incorporates likelihood profiling and parametric bootstrapping.

## Installation

### On current R (>= 3.0.0)

* From CRAN (stable release 1.0.+)
* Development version from Github:
```
library("devtools"); install_github("lme4",user="lme4")
```
(These commands install the "master" (development) branch.)
The `install_github()` approach requires that you build from source, i.e. `make` and compilers must be installed on your system -- see the R FAQ for your operating system; you may also need to install dependencies manually. You may need to specify `build_vignettes=FALSE` if your system is missing some of the `LaTeX/texi2dvi` tools.
* Usually up-to-date development binaries from `lme4` r-forge repository:
```
install.packages("lme4",
   repos=c("http://lme4.r-forge.r-project.org/repos",
          getOption("repos")[["CRAN"]]))
```
(these source and binary versions are updated manually, so may be out of date; if you believe they are, please contact the maintainers).

### On old R (pre-3.0.0)

It is possible to install (but not easily to check) `lme4` at least as recently as 1.1-7.

* make sure you have *exactly* these package versions: `Rcpp` 0.10.5, `RcppEigen` 3.2.0.2
* for installation, use `--no-inst`; this is necessary in order to prevent R from getting hung up by the `knitr`-based vignettes
* running `R CMD check` is difficult, but possible if you hand-copy the contents of the `inst` directory into the installed package directory ...

### Of `lme4.0`

* `lme4.0` is a maintained version of lme4 back compatible to CRAN versions of lme4 0.99xy,
  mainly for the purpose of  *reproducible research and data analysis* which was done with 0.99xy versions of lme4.
* Notably, `lme4.0` features  `getME(<mod>, "..")` which is compatible (as much as sensibly possible) with the current `lme4`'s version of `getME()`.
* You can use the `convert_old_lme4()` function to take a fitted object created with `lme4` <1.0 and convert it for use with `lme4.0`.
* It currently resides on R-forge, and you should be able to install it with
```
install.packages("lme4.0", 
                 repos=c("http://lme4.r-forge.r-project.org/repos",
                         getOption("repos")[["CRAN"]]))
```
(if the binary versions are out of date or unavailable for your system, please contact the maintainers).
