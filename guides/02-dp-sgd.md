# Reading guide 02 — Deep Learning with Differential Privacy (DP-SGD)

**Abadi, Chu, Goodfellow, McMahan, Mironov, Talwar, Zhang** · ACM CCS 2016
arXiv: <https://arxiv.org/abs/1607.00133> · DOI: [10.1145/2976749.2978318](https://doi.org/10.1145/2976749.2978318)
Type: foundational defence paper · Length: 14 pages · Suggested time: 4–5 hours over two sittings

## Why read it
DP-SGD is the training algorithm behind Project B and behind libraries such as Opacus. The
Differential Privacy internship expects you to explain, without notes, what clipping, noise and
privacy accounting each do. CDPG says its data exchange stack supports AI on data without
exposing the raw records. DP-SGD is the standard way to limit what a trained model reveals
about any single record it was trained on.

## Background you need
- The definition of (ε, δ)-differential privacy and what "neighbouring datasets" means.
- Sensitivity and the Gaussian mechanism.
- Composition: why privacy loss adds up over repeated queries.
- Mini-batch SGD and the L2 norm of a gradient vector.

Free resources, in the order to use them:
- Near & Abuah, *Programming Differential Privacy*: <https://programming-dp.com/>. The chapters
  on the definition, sensitivity, composition and approximate DP are enough.
- Dwork & Roth, *The Algorithmic Foundations of Differential Privacy*:
  <https://www.cis.upenn.edu/~aaroth/Papers/privacybook.pdf>, chapters 2–3, for the formal version.
- Opacus tutorials: <https://opacus.ai/tutorials/>. Read these after the paper to map each part
  of the algorithm to code.

## Sections
| Read closely | Skim | Leave for a second pass |
|---|---|---|
| 2.1, 3 (intro), 3.1 including Algorithm 1, 5.1, 5.2 | 3.2 (follow the idea, skip the derivation), 3.3, 5.3, 6 | 4 (TensorFlow details are dated), Appendices A–D |

## Five questions to answer while reading
1. What is the unit of privacy here, that is, what differs between two neighbouring datasets?
   If an ECG dataset has several recordings per patient, does a per-example guarantee protect
   a recording or a patient? (Keep your answer; Project B needs it.)
2. Why are gradients clipped *per example* rather than per batch? What does the clipping bound
   trade off when it is set too small or too large?
3. In your own words, why does the moments accountant give a smaller ε than standard
   composition for the same training run? What role does the sampling ratio play?
4. Which hyperparameters mattered most for accuracy under DP, and how did the authors choose
   them? Does tuning hyperparameters on private data itself use up privacy budget?
5. Which (ε, δ) settings and accuracies do they report on MNIST and CIFAR-10, and how do they
   compare with non-private training? How is δ chosen relative to the dataset size, and why?

## Pointer for Project B
After reading, write a short note in your Project B repo recording your chosen unit of privacy,
clipping bound, noise multiplier, sampling rate, δ and accountant, each with a one-line reason.
