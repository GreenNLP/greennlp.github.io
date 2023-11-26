---
title: Data curation
sections:
  - Introduction
  - Monolingual data
  - Parallel data
---

### Introduction

Data curation is essential for good performance and the efforts needed to filter, clean and prepare training data is often under-estimated and not very much appreciated. However, without proper data curation it basically comes down to the "garbage in - garbage out" effect. Data size is important but data quality should not be neglected.


### Monolingual data

Various pipelines exist for monolingual data curation but no one-size-fits-all solution can be found. Depending on the purpose, source and language, various steps need to be taken into consideration. Many big data sets come from open web crawls leading to the big mess that can be expected from the unrestricted sources on the internet.

The [HPLT project](https://hplt-project.org/) extracts large quantities of monolingual texts from internet crawls and archives. [HPLT software](https://github.com/hplt-project) is released on Github for [extracting monolingual text](https://github.com/hplt-project/monotextor-slurm). It makes use of the [monotextor](https://github.com/bitextor/monotextor) pipelines.

Another pipeline for [data preparation](https://github.com/bigscience-workshop/data-preparation) has been developed by the BigScience project.

Yet another iniative is taken by the [OSCAR project](https://oscar-project.org/) with [Ungolian pipeline](https://github.com/oscar-project/ungoliant) for corpus creation from web crawls.


### Parallel data


[OPUS](https://github.com/Helsinki-NLP/OPUS) is a major hub of parallel texts collected from various sources. The repository provides a consistent interface for aligned trabslation data and the project curates parallel data for large-scale machine translation research and development.

The [Tatoeba translation challenge](https://github.com/Helsinki-NLP/Tatoeba-Challenge) is derived from OPUS and compiles the various resources into a consistent dataset with dedicated train, dev and test splits.

[Corset](https://corset.paracrawl.eu/) is a toolbox for tailoring parallel data to specific needs.


Other tools for parallel data curation are:

* [OpusCleaner](https://github.com/hplt-project/OpusCleaner) for parallel data cleaning
* [OpusFilter](https://github.com/Helsinki-NLP/OpusFilter) for filtering parellel data sets
* [bicleaner](https://github.com/bitextor/bicleaner) and [bicleaner-ai](https://github.com/bitextor/bicleaner-ai) for detection of noise in parallel data
* [biromer](https://github.com/bitextor/biroamer) for data anonymization