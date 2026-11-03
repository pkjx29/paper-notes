# Reading guide 06 — Slalom: Fast, Verifiable and Private Execution of Neural Networks in Trusted Hardware

**Tramèr, Boneh** · ICLR 2019 (oral)
arXiv: <https://arxiv.org/abs/1806.03287>
Type: foundational systems/crypto paper · Length: 10 pages plus appendix · Suggested time: 4 hours

## Why read it
Differential privacy limits what a model's *output* reveals. Confidential computing protects
data *while it is being processed*, using trusted execution environments (TEEs). A data exchange
that lets analysts or AI models compute on sensitive records without seeing them (CDPG describes
"federated AI without raw data exposure") can draw on both, and interviewers may ask how the two
differ. Slalom is a clear, short entry point: it states exactly what is trusted and what is not,
and it shows how cryptographic tricks can split ML work between a slow trusted enclave and a fast
untrusted GPU.

## Background you need
- What a TEE is: enclave, remote attestation, encrypted memory, and the fact that side-channel
  attacks exist. Intel SGX is the example used.
- Why matrix multiplications dominate the cost of a DNN forward pass.
- Freivalds' algorithm: a randomised check that A·B = C, cheaper than recomputing the product.
- Arithmetic in a finite field (modulo a prime) and one-time-pad-style additive blinding.

## Sections
| Read closely | Skim | Leave for a second pass |
|---|---|---|
| 1, 2.1, 2.2, 2.3, 3, 3.1, 3.2, 3.3, 4.3, 5 | 4.1, 4.2, Appendix A | Appendices B–H |

## Five questions to answer while reading
1. Who is trusted and who is not: the enclave, the GPU, the host operating system, the cloud
   provider? For each one, what does Slalom guarantee (integrity, privacy, or both), and for
   which phase, inference or training?
2. Why must the model's values be quantised into a finite field before verification and
   blinding can work?
3. Explain Freivalds' check in two lines. Why is it cheaper than recomputing the product, what is
   its error probability, and how can that probability be reduced?
4. How is input privacy achieved, and what has to be precomputed for it? Where does that
   precomputed material live, and what does it cost?
5. Using Section 5, explain why training is harder than inference for this approach. Modern data-
   centre GPUs now offer their own confidential-computing modes; which parts of Slalom's
   motivation still hold?

## Optional follow-up (recent)
For the current GPU-based picture, see "Confidential Computing on NVIDIA Hopper GPUs: A
Performance Benchmark Study" (2024), <https://arxiv.org/abs/2409.03992>. Only skim it after
finishing this guide.
