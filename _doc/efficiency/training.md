---
title: Efficient training
---

For getting started with efficient training of neural networks for
NLP, check CSC's machine learning guide, which has been expanded and
improved as part of the GreenNLP project.

Particularly relevant sections:

- [Getting started with machine learning at
  CSC](https://docs.csc.fi/support/tutorials/ml-starting/), for
  getting started with doing machine learning on supercomputers from
  scratch,
- [GPU-accelerated machine
    learning](https://docs.csc.fi/support/tutorials/gpu-ml/), which
    discusses GPU utlization and common bottle-necks than can cause
    low utilization,
- [Data storage for machine
  learning](https://docs.csc.fi/support/tutorials/ml-data/) which
  discusses data storage in the context of supercomputers,
- [Multi-GPU and multi-node machine
  learning](https://docs.csc.fi/support/tutorials/ml-multi/) with
  Slurm examples and short tutorials for PyTorch DDP, PyTorch
  Lightning, Accelerate and DeepSpeed.
- [Managing machine learning workflows on CSC's
  supercomputers](https://docs.csc.fi/support/tutorials/ml-workflows/)
  which covers using MLflow for tracking multiple runs and metrics,
- [Working with large language models on
  supercomputers](https://docs.csc.fi/support/tutorials/ml-llm/) which
  discussess how to do efficient fine-tuning of LLMs on supercomputers.

Also relevant is the [PyTorch module
documentation](https://docs.csc.fi/apps/pytorch/) which includes a
[short tutorial on how to use the PyTorch
profiler](https://docs.csc.fi/apps/pytorch/#pytorch-profiler).


In GreenNLP we have also collected other links with recipies and tips
for LLM training, in particular for LUMI:

- [TurkuNLP group's recipes for LUMI NLP training](https://github.com/TurkuNLP/lumi-nlp-recipes)
- [Megatron-LM fork for LUMI](https://github.com/LumiOpen/Megatron-LM-lumi)
- [LUMI NLP recipes and known problems collected by GreenNLP](https://siili.rahtiapp.fi/LUMI-NLP)
