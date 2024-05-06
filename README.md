---
license: llama3
---

# Llama 3 8B Self-Alignment Data Generation

This repository contains the various stages of the data generation and curation portion of the StarCoder2 Self-Alignment pipeline:

![](method.png)

## How this repository is laid out

Each revision (branch) of this repository contains one of the stages laid out in the [data generation pipeline](https://github.com/muellerzr/llama-3-8b-self-align/tree/main?tab=readme-ov-file#data-generation-pipeline) directions. 

Eventually a Docker image will be hosted on the Hub that will mimic the environment used to do so, I will post this soon.

**Stage to branchname**:
- Snippet to concepts generation: `snippet-to-concept`
- Concepts to instruction generation: `concept-to-instruction`
- Instruction to response (with self-validation code) generation: TODO
- Execution filter: TODO
- Data sanitization and selection: TODO

## How the data was generated

Each step followed the directions outlined in the original repository except:

1. The `dev` branch was used to allow for using vLLM directly, no need to host a server. Just pass in `--use_vllm_server False` when calling `self_ossinstruct.py` and increase `--num_batched_requests` to 200.
