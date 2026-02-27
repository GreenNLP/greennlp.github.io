---
title: Getting the most out of LLMs
sections:
  - Introduction
  - Tools of the trade
---

### Getting the most out of LLMs

There are tons of LLMs out there. Some, such as OpenAI's models are only available via API. Their models are good and fast, but can get costly to run, if you need to make lots of API calls or have to process large amounts of data.

Luckily, there are open-weight models that you can run on your own computer or supercomputer cluster. This can be a lot cheaper, but requires some expertise. With a little effort, you can optimize the performance of the models, saving you time, money and electricity!

This page contains advice for how to run LLMs efficiently locally and links to other useful recourses.


### Tools of the trade

Probably the simplest way to start running LLMs is by using [Ollama](https://ollama.com/). The free tier lets you run models locally and even gives access to some limited cloud computing. Another popular library for high-performance LLM inference is called [SGLang](www.sglang.io).

However, in this short tutorial, we will focus on vLLM as it comes preinstalled on the CSC pytorch module and LUMI AI factory containers. For the latest and most comprehensive documentation, you should refer to the [vLLM documation](https://docs.vllm.ai/en/latest/) but here is a simple Python script to run offline inference.

```python
import torch
from vllm import LLM, SamplingParams

model = LLM(model="openai/gpt-oss-120b",
            download_dir=/scratch/project_<your_proj_num>/cache, # Set cache to /scratch as it will else fill you /home directory
            dtype="bfloat16",
            tensor_parallel_size=torch.cuda.device_count(), # use all available GPUs
            enforce_eager=False,
            gpu_memory_utilization=0.8, # adjust if your getting OOMs
            )

# Instruction fine-tuned models expect their input to follow the models "chat template"
# Here, we can use vLLM's model.chat() to automatically apply the correct chat template to our input
# Before calling model.chat(), we need to format our input as a list of dictionaries.
# The first dictionary contains the system prompt and the second dictionary contains the user prompt. 
input = [
    {"role": "system", "content": "You are a helpfull assistant"},
    {"role": "user", "content": "Write me an essay about LLMs."}
]

# Set sampling parameters to tune model output
sampling_params = SamplingParams(
    temperature=0.2, # Set temperature. Often the model card has a recommended default temperature. Set to 0 for deterministic output.
    top_p: 0.5,
    repetition_penalty=1,  # 1 = no penalty, >1 penalty for repeating tokens
    max_tokens=5000  # max tokens to generate
)

# Generate response
output = model.chat(input, sampling_params=sampling_params)
```

Often for large scale data analysis, you probably want to ensure that the model output follows a predetermined structure, such as JSON. For this, you want to use Structured Outputs like this:
```python

# More to come...

```

To use the newest models available on the HuggingFace hub, you also need a recent version of vLLM. Therefore it is recommended to use a recent container built by the LUMI AI factory. The instructions below are modifier from the original [CSC docs](https://docs.lumi-supercomputer.eu/laif/software/ai-environment/).

To launch your script on a single node using a LUMI AI factory container, you SLURM launch script should look something like this:
```bash
#!/bin/bash
#SBATCH --job-name=vllm
#SBATCH --account=project_<your_proj_num>
#SBATCH --partition=standard-g
#SBATCH --time=12:00:00
#SBATCH --nodes=1
#SBATCH --ntasks-per-node=1
#SBATCH --cpus-per-task=16
#SBATCH --mem=80G
#SBATCH --gpus-per-node=8  # vLLM will automatically split the model to all available GPUs 
#SBATCH -o %j.out
#SBATCH -e %j.err


module purge
module use /appl/local/laifs/modules
module load lumi-aif-singularity-bindings

# Choose the latest container for most up-to-date packages. It might make sense to `cp` this into you project `scratch`. 
export SIF=/appl/local/laifs/containers/lumi-multitorch-u24r64f21m43t29-20260124_092648/lumi-multitorch-full-u24r64f21m43t29-20260124_092648.sif

srun singularity run --rocm --bind /scratch/project_<your_proj_num> \
    $SIF bash -c "python vllm_inference.py"
```

If you run into errors, here are some debugging tips:
- If you see `RuntimeError: Please use HIP_VISIBLE_DEVICES instead of ROCR_VISIBLE_DEVICES`, try setting `export HIP_VISIBLE_DEVICES=$ROCR_VISIBLE_DEVICES`.
- You can also try `export TORCH_COMPILE_DISABLE=1` if your code still crashes.
- If you are getting HIP out-of-memory errors, try `PYTORCH_HIP_ALLOC_CONF=expandable_segments:True,garbage_collection_threshold:0.8`. A single node can handle models up to ~120 billion parameters. If you want to use models much bigger thatn this, you might want to consider running on multiple nodes.



