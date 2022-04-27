---
title: "Statistics for Software Use"
linkTitle: "Software Use Statistics"
type: book
description: >
  "How to get statistics on the number of downloads for software projects
---

It can be helpful to know how frequently your software is being downloaded to assess it's use and report on its impact. Below are instructions for how to do this for different languages. Keep in mind that downloads can be influenced by automated testing systems if they install the software from the central repository.

## R

These instructions get downloads from the cloud CRAN mirror. This is a minimum estimate of total downloads.

* Install the [`cranlogs` package](https://github.com/r-hub/cranlogs) `install.packages("cranlogs")`
* Run the `cran_downloads` function with your package name and date ranges if desired

```r
downloads = cranlogs::cran_downloads(packages = c("portalr"), from = "2020-02-26", to = "2020-08-16")
total_downloads = sum(downloads$count)
```

## Python

Python packages are often distributed using both PyPI and conda so you might need to get download statistics for both.

### PyPI

* Setup a Google BigQuery account
* Run a version of this query where with additional modifications as necessary

```Python
SELECT COUNT(*) downloads
FROM `the-psf.pypi.downloads2020*`
WHERE file.project='retriever'
```

### Conda

* Install the [`condastats` package](https://www.anaconda.com/blog/get-python-package-download-statistics-with-condastats) `conda install -c conda-forge condastats`
* From the command line run a version of the following command

```bash
condastats overall retriever --start_month 2020-01 --end_month 2020-08
```
