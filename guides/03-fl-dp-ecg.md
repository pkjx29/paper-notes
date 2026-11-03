# Reading guide 03 — Federated Learning and Differential Privacy Techniques on Multi-hospital Population-scale Electrocardiogram Data

**Agrawal, Kalmady, Malipeddi, Manthena, Sun, Islam, Hindle, Kaul, Greiner** · ICMHI 2024 (arXiv comment: "Accepted for ICMHI 2024")
arXiv: <https://arxiv.org/abs/2405.00725> · Code: <https://github.com/vikhyatt/Hospital-FL-DP>
Type: recent applied paper (2024) · Suggested time: 3 hours, plus 1 hour in the code

## Why read it
This is the paper closest to Project B: DP-SGD, through Opacus, applied to 12-lead ECG
classification across several hospitals, with public code. The setting is similar to CDPG's
health data platforms: several data holders that cannot pool raw patient data but want a shared
model. It is also a short applied paper whose privacy details are thin. That makes it good
practice for critical reading: much of your summary's value will be in noting what is
*missing*.

## Background you need
- Guide 02 (DP-SGD) first.
- Federated averaging (FedAvg): McMahan et al., AISTATS 2017,
  <https://arxiv.org/abs/1602.05629>. Algorithm 1 and Section 2 are enough.
- Multi-label classification and macro-averaged AUROC.
- Rényi DP accounting at the level of "Opacus tracks ε for you; know what inputs it needs".
- 12-lead ECG basics, which you already have from your ECG work.

## Sections
| Read closely | Skim | Leave for a second pass |
|---|---|---|
| 1.2, 1.3, 3.1, 3.4 (especially 3.4.2), 3.5, 4.3 and its figure, 5 | 2, 3.2, 3.3, 4.1, 4.2 | Appendix A |

In the repo, find where the privacy engine is set up and which parameters it is given.

## Five questions to answer while reading
1. Where exactly is noise added, and whose data is protected from whom: the other hospitals, the
   central server, or anyone who gets the final model? The paper's threat model is mostly
   implicit, so write the one it implies.
2. What is the unit of privacy, an ECG or a patient? Using the cohort numbers in Section 3.1,
   explain what happens to the guarantee when one patient contributes many ECGs.
3. Which ε values, δ, clipping bound, noise multiplier and number of rounds were used? For each
   one, note whether it is stated in the paper, recoverable from the code, or missing.
4. How does the cost of DP differ between larger and smaller hospitals in their results, and why
   would the size of a site's dataset change that cost?
5. FedAvg runs for many rounds. Is the reported ε per site per round, per site for the whole of
   training, or something else? What would you need to know to state an end-to-end guarantee?

## Pointer for Project B
Your answers to questions 2, 3 and 5 are a checklist for what your own Project B README must
state clearly. If you want a second DP-ECG paper later, a 2026 candidate is Santos, Brito &
Machado, "Differentially Private ECG Heartbeat Classification", SBBD 2026,
DOI [10.5753/sbbd.2026.249231](https://doi.org/10.5753/sbbd.2026.249231).
