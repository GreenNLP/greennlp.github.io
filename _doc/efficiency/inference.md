---
title: Efficient inference
sections:
  - Dynamic loading
  - Job scheduling
  - Scaling the throughput
  - Reduced precision inference
  - Model compilation
---

To use the trained large language models, the models need to be deployed and served to the users. The user experience from the initial startup overhead and the usage latency are inherently combatting with computational resources. 

If the resources would be unlimited the collection of all available models could be kept in memory, but with limited server space and optimization for less energy usage, it is efficient to operate on a shared resource that runs other workloads while the demand for inference is low, and thus the idle power consumption of the system is reduced. 

### Dynamic loading
 
To avoid wasting computational resources, and assuming a shared cluster, the models should only be loaded when they are required. This could be implemented for example by signaling a backend when an user enters a website, or by implementing API calls for loading a model as a first step for starting inferencing. 

### Job scheduling

To improve utilization and thus being able to tune for efficiency, having multiple users operating through a same system and possibly on a single copy of a network is required. The users would be interacting via a job scheduling or queue system. This can be implemented 

### Scaling the throughput

TODO

### Reduced precision inference

TODO. The software stack is important and can make this one unfeasible if the reduced precision reduces accuracy but does not improve throughput. 

### Model compilation

To optimize models for inference, multiple optimized formats such as ONNX are available. 

TODO: evaluation
