# blaze-swarm

blaze-swarm explores how agent swarms can help systematically optimize LLM inference engines such as vLLM, SGLang, NVIDIA Dynamo, and custom inference runtimes.

**The goal**: Move inference optimization from manual trial and error to systematic, hardware-aware experimentation.

**Status**: Early exploration / Experimental

Contributions, research papers, optimization techniques, and ideas are welcome.


## The Problem

Getting the best performance out of an inference engine is difficult. Performance depends on several interacting factors. 

What works for one workload may perform poorly for another.  The key challenge is to define a common target that works for everyone. Is it even possible or do we have CAP version (theorom from distributed systems) for inference perf here in play here

## Core Idea

Combine two approaches:

**Hardware-aware performance modelling**

Understand what the hardware can theoretically deliver and identify the gap between theoretical and actual inference performance.

Roofline analysis provides an initial model for understanding compute and memory bandwidth limitations. Additional models can account for real inference workloads and serving behaviour.

**Agent-driven experimentation**

Use specialized agents to analyse performance, propose optimization hypotheses, run controlled experiments, and evaluate results.

The objective is to continuously reduce the gap between actual performance and achievable performance under real-world workload and latency constraints.

## Architecture

The initial architecture has three primary components:

**1. Planning Agent (Python)**

**2. Experiment Agents (Python initially)**

**3. Evaluation Agent (Python)**

## Technology Choices

## Technology Choices

| Component | Technology |
|---|---|
| Planning and reasoning agents | Python |
| Experiment execution | Python |
| Performance analysis | NumPy, Pandas |
| GPU profiling | NVIDIA Nsight, Perfetto |
| Inference metrics | Prometheus, vLLM/SGLang metrics |
| Orchestration | Go (planned) |
| Cluster integration | Kubernetes (planned) |
| Inference engines | vLLM, SGLang, NVIDIA Dynamo |
| LLM integration | Model-agnostic API |

Python will be used initially for planning, reasoning, and experimentation. Go may be introduced for distributed orchestration, resource management, and long-running workers as the project evolves.

