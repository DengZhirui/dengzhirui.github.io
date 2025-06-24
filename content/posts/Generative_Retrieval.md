---
title: "Introduction of Generative retrieval"
date: 2025.6.24
description: "Introduction of papers about PRM"
tags: ["GR"]
categories: ["survey"]
---

## Related Works about GR
1. [Transformer Memory as a Differentiable Search Index](https://arxiv.org/pdf/2202.06991)
- Introducing generative retrieval framework and index building and training strategies, especially **Semantic Structured Identifiers** for representing doc_ids.
- Semantic structured identifiers ensure:
  - the docid should capture some information about the semantics of its associated document.
  - the docid should be structured in a way that the search space is effectively reduced after each decoding step.
  - Kmeans for clustering and assign each document clustering an id, then continue this way for each cluster.
- Training pipeline: first learn document2id, then learn query2docid_list

   <img src="https://raw.githubusercontent.com/DengZhirui/dengzhirui.github.io/main/images/DSI.png" width="500"/>

