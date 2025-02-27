---
title: "LLM Reinforcement Learning Optimization with PRM"
date: 2025.2.28
description: "Introduce papers about PRM"
tags: ["blog"]
categories: ["survey"]
---

Read deepseek-R1, although PRM can facilitates the optimization of LLMs in RL progress, they face:

1. Obtaining the training data for PRM is time- and money-consuming.
2. It is hard for people to accurately annotate the process reward.
3. Accurate ORM is more useful that rough PRM.

:round_pushpin:How to accurately annotate the PRM without human intensive?
This problem is more important for Multi-hop QA / Web Search.


- [Demystifying Multilingual Chain-of-Thought in Process Reward Modeling](https://arxiv.org/pdf/2502.12663): Translate PRM800K and Math-Shepherd from English to **six** additional languages and train a PRM model with best-of-N and three setups:
**PRM-MONO**: train and evaluate on a single language.
**PRM-CROSS**: train on one laguage but evaluate on all test languages.
**PRM-MULTI**: train on seven languages and evaluate on all test languages (best performance).

QWEN2.5-MATH-7B-INSTRUCT as verifier (PRM) and METAMATHMISTRAL-7B / LLAMA-3.18B-MATH (fine-tuned with the MetaMath dataset) / DEEPSEEKMATH-7BINSTRUCT as generator.

Shortcome: Still rely on the large amount of human labeled data to train the PRM.

![Framework of PRM](https://dengzhirui.github.io/images/PRM-MULTI.png)


