---
title: Efficient training
sections:
  - GPU utilization and profiling
  - Mixed precision training
---

### GPU utilization and profiling

From the resource utilization point-of-view, a common first thing to
check is the GPU utilization. The GPU utilization should ideally be
close to 100%. If your utilization is consistently low (for example
under 50%) it might be a sign of a bottle-neck in the processing
pipeline. For example:

- There might not be enough CPU cores reserved for data loading
- File I/O is too slow (e.g., an overloaded shared file system in a
  Supercomputer)
  
Having a GPU load of 100% is not a guarantee that the job is actually
doing something useful on the GPU. Having a good reported GPU load can
be considered as a neccessary, but not sufficient condition for an
efficient job.

The next step would be to check with a profiler, such as the [PyTorch
profiler](https://pytorch.org/tutorials/intermediate/tensorboard_profiler_tutorial.html)
what operations are being performed. CSC's Machine learning guide has
a [short tutorial on how to use the PyTorch
profiler](https://docs.csc.fi/apps/pytorch/#pytorch-profiler).


### Mixed precision training

A simple way to speed up training is to enable mixed precision
training, and for many software packages this is already the
default. In mixed precision training, some floating points values are
stored with reduced 16-bit precision in cases where the loss of
precision is not critical. A simple way to do this is to [enable
Automatic Mixed Precision
(amp)](https://pytorch.org/docs/stable/amp.html#module-torch.amp) in
PyTorch.


