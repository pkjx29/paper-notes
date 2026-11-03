# Reading guide 05 — The Good and The Bad: Exploring Privacy Issues in Retrieval-Augmented Generation (RAG)

**Zeng, Zhang, He, Xing, Liu, Xu, Ren, Wang, Yin, Chang, Tang** · Findings of ACL 2024
arXiv: <https://arxiv.org/abs/2402.16893> · ACL Anthology: <https://aclanthology.org/2024.findings-acl.267/>
Code (listed on the arXiv page): <https://github.com/phycholosogy/RAG-privacy>
Type: recent attack and measurement paper (2024) · Suggested time: 3–4 hours

## Why read it
Guide 04 is about making a RAG system *do* something harmful. This paper is about making it
*leak* its private retrieval database. Together they cover the two halves of Project A. One of
the retrieval datasets is medical dialogue, which mirrors the risk for CDPG's health data
platforms if an LLM assistant is placed in front of them. The paper also asks whether retrieval
changes how much the model leaks its own training data, a privacy question that links to
Guides 01 and 02.

## Background you need
- The RAG pipeline: chunking, embedding models, vector store, top-k retrieval by distance.
- L2 and cosine distance between embeddings.
- Training-data extraction and memorisation in LLMs: Carlini et al., "Extracting Training Data
  from Large Language Models", USENIX Security 2021, <https://arxiv.org/abs/2012.07805>.
  Section 1 and the threat model are enough.
- How to read an ablation table.

## Sections
| Read closely | Skim | Leave for a second pass |
|---|---|---|
| 1, 3.1, 3.2, 4.1, 4.2, 4.3, 4.5, 7, A.2.1 | 2, 3.3, 4.4, 5 (5.1–5.4), A.1 | A.2.2, A.2.3, A.3–A.5 |

A.2.1 matters if you want to reproduce the attack in Project A.

## Five questions to answer while reading
1. What access does the attacker have: query access only, or knowledge of the retriever,
   embedding model or database? Fill in the template's threat-model bullets for this paper.
2. The attack prompt has separate parts. What job does each part do, and how does that differ
   between the targeted and untargeted attacks?
3. How is leakage measured? What exactly counts as a successful extraction, and are the metrics
   strict or lenient? Would you count a paraphrase of a patient record as a leak?
4. Which mitigations were tested in 4.5? Which ones reduce leakage, and at what cost to answer
   quality? Pick one to reimplement as a baseline in Project A.
5. For RQ2, what is the evidence that retrieval changes how much the LLM leaks its training data?
   Is the explanation causal or only correlational, and would you expect it to hold for a
   healthcare question-answering system?

## Pointer for Project A
Questions 3 and 4 decide your evaluation design. Write down the metric definitions you will use
before you run anything.
