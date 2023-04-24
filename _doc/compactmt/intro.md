---
title: Introduction
sections:
  - Energy consumption of machine translation
  - Reducing model size
---

### Energy consumption of machine translation

Modern machine translation relies on a specific type of neural network, called transformer. Training a transformer model usually consumes significant amounts of energy: 
in [Strubell et al. (2019)](https://aclanthology.org/P19-1355/), the energy consumption for training a normal-sized _transformer-base_ model was estimated as 27 kWh, and training a larger _transformer-big_ model as 201 kWh. While the amount of energy required to train a single transformer model is not huge, machine translation development usually involves training and testing many variants of models, which multiplies the energy consumption of training. Generating translations with transformer models also requires energy. As with training, bigger models require more energy to generate translations than smaller models.

### Reducing model size

The best way to reduce the energy consumption of transformer models is to reduce their size, since smaller models use less energy when being trained and when generating translations. However, size reduction is only useful, if the quality of the translations that the smaller model produces remains competitive.

In the GreenNLP project, we will explore different methods which reduce translation model size without compromising quality. The most common way of creating machine translation models that are small but perform well, is to use knowledge distillation, which means compacting the knowledge embedded in a large model into a smaller model (you can see the effect of knowledge distillation on model sizes in the table below). In addition to knowledge distillation, we will explore retrieval-augmented translation models, which utilize external information sources in generating translations. 

<div class="table-responsive">

{: .table .table-striped .}
| Model type | Model size | Time to translate 48,000 words
|-
| big | 891 MB       |
| base | 294 MB      | 46.36s
| small | 226 MB      | 24.07s
| tiny11 | 96 MB      | 10.98s
| tiny | 89 MB     | 6.22

{: .center }
**Table 1.** The effect of knowledge distillation on model size and translation speed ([Tiedemann et al., 2023](https://arxiv.org/abs/2212.01936))

</div>
