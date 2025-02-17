---
layout: doc
title:  "GreenNLP papers at NoDaLiDa/Baltic-HLT 2025"
date:   2025-01-24
categories: news
---
GreenNLP has a strong representation at the Joint 25th Nordic Conference on Computational Linguistics and 11th Baltic Conference on Human Language Technologies (NoDaLiDa/Baltic-HLT 2025).
GreenNLP researchers will present four papers showcasing the multifaceted research done within the project. 

The conference is held in Tallinn, Estonia on March 2–5. Read more about the conference here: https://www.nodalida-bhlt2025.eu/

If you meet us at the conference, come talk GreenNLP!

## GreenNLP papers presented at the conference

---

### FinerWeb-10BT: Refining Web Data with LLM-Based Line-Level Filtering
**Authors:** Erik Henriksson, Otto Tarkka, Filip Ginter

**Abstract:** Data quality is crucial for training Large Language Models (LLMs). Traditional heuristic filters often miss low-quality text or mistakenly remove valuable content. In this paper, we introduce an LLM-based line-level filtering method to enhance training data quality. We use GPT-4o mini to label a 20,000-document sample from FineWeb at the line level, allowing the model to create descriptive labels for low-quality lines. These labels are grouped into nine main categories, and we train a DeBERTa-v3 classifier to scale the filtering to a 10B-token subset of FineWeb. To test the impact of our filtering, we train GPT-2 models on both the original and the filtered datasets. The results show that models trained on the filtered data achieve higher accuracy on the HellaSwag benchmark and reach their performance targets faster, even with up to 25\% less data. This demonstrates that LLM-based line-level filtering can significantly improve data quality and training efficiency for LLMs. We release our quality-annotated dataset, FinerWeb-10BT, and the codebase to support further work in this area. 

**Paper:** https://arxiv.org/abs/2501.07314

---

### A Comparative Study of PEFT Methods for Python Code Generation
**Authors:** Johanna Mannistö, Joseph Attieh, Jörg Tiedemann

**Abstract:** Fine-tuning language models incurs high costs in training, inference and storage. Parameter-efficient fine-tuning (PEFT) methods have emerged as a more cost-effective alternative to full fine-tuning. However, limited work has compared different PEFT approaches for tasks like code generation. In this study, we examine the effect of various PEFT training methods on model performance in the task of Python code generation. We fine-tune four model families, ranging from 124M to 7B parameters, using three PEFT approaches alongside standard full fine-tuning. Our findings reveal that the effectiveness of each PEFT method varies with the model size and the corpus used.

---

### OpusDistillery: A Configurable End-to-End Pipeline for Systematic Multilingual Distillation of Open NMT Models
**Authors:** Ona De Gibert Bonet, Tommi Nieminen, Yves Scherrer, Jörg Tiedemann

**Abstract:** In this work, we introduce OpusDistillery, a novel framework to streamline the Knowledge Distillation (KD) process of multilingual NMT models. OpusDistillery's main features are the integration of openly available teacher models from OPUS-MT and Hugging Face, comprehensive multilingual support and robust GPU utilization tracking. We describe the tool in detail and discuss the individual contributions of its pipeline components, demonstrating its flexibility for different use cases. OpusDistillery is open-source and released under a permissive license, aiming to facilitate further research and development in the field of multilingual KD for any sequence-to-sequence task. Our code is available at https://github.com/Helsinki-NLP/OpusDistillery.

---

### Mind the Gap: Diverse NMT Models for Resource-Constrained Environments
**Authors:** Ona De Gibert Bonet, Dayyán O'Brien, Dušan Variš, Jörg Tiedemann

**Abstract:** We present fast Neural Machine Translation models for 17 diverse languages, developed using Sequence-level Knowledge Distillation. Our selected languages span multiple language families and scripts, including low-resource languages. The distilled models achieve comparable performance while being 10x times faster than transformer-base and 35x times faster than transformer-big architectures. Our experiments reveal that teacher model quality and capacity strongly influence the distillation success, as well as the language script. We also explore the effectiveness of multilingual students. We release publicly our code and models in our Github repository: https://github.com/hplt-project/bitextor-mt-models.

---
