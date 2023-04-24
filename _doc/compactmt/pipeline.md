---
title: Machine translation training pipeline
sections:
  - firefox-translations-training pipeline
  - Example of a pipeline job
---

### _firefox-translations-training_ pipeline

Reducing the energy consumption of machine translation models first of all requires that there is a system in place for consistently tracking the energy consumption of MT training and generation. GreenNLP project uses a modified version of the [firefox-translations-pipeline](https://github.com/GreenNLP/firefox-translations-training), originally developed as part of the [Bergamot project](https://browser.mt/), to record detailed information about the energy consumption data during different training steps.  

_firefox-translations-pipeline_ also includes out-of-the-box support for knowledge distillation, which is used as a foundation for knowledge distillation experiments within the GreenNLP project. An important addition to the pipeline is the possibility to use machine translation models trained in the [OPUS-MT](https://github.com/Helsinki-NLP/Opus-MT) and [Tatoeba-Challenge](https://github.com/Helsinki-NLP/Tatoeba-Challenge) project as sources of knowledge for knowledge distillation.

### Example of a pipeline job

The training pipeline can run jobs with different configurations. Below is a diagram of one possible job configuration, where pretrained OPUS-MT models are used (click to zoom).

<div class="screenshot-holder">
   <a href="assets/images/DAG.png" data-title="Pipeline" data-toggle="lightbox"><img class="img-responsive" src="assets/images/DAG.png" width="50%" heigh="50%" alt="screenshot" margin-left="0" /></a>
   <a class="mask" href="assets/images/DAG.png" data-title="Pipeline" data-toggle="lightbox"><i class="icon fa fa-search-plus"></i></a>
  </div>
