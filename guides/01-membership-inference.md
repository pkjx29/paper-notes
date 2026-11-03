# Reading guide 01 — Membership Inference Attacks Against Machine Learning Models

**Shokri, Stronati, Song, Shmatikov** · IEEE Symposium on Security and Privacy (S&P) 2017
arXiv: <https://arxiv.org/abs/1610.05820> · DOI: [10.1109/SP.2017.41](https://doi.org/10.1109/SP.2017.41)
Type: foundational attack paper · Length: 16 pages · Suggested time: 3–4 hours over two sittings

## Why read it first
This is the attack that differential privacy is meant to defend against. Before you can say
that your DP ECG classifier (Project B) "protects patients", you need a concrete attack to
measure protection against, and membership inference is the standard one. For CDPG, the
question "can someone tell whether a person's record was used to train a model?" applies
directly to its health data platforms.

## Background you need
- Supervised classification, softmax outputs read as confidence scores.
- Overfitting and the gap between training and test accuracy.
- Precision and recall for a binary decision.
- What "black-box access" to a model through an API means.
If you are new to security writing, read Section IV slowly: it is a model of how to state an
adversary's goal and knowledge.

## Sections
| Read closely | Skim | Leave for a second pass |
|---|---|---|
| I, IV, V (all of it), VI-A to VI-D, VI-G, VII, VIII | II, III, VI-E, VI-F | IX |

## Five questions to answer while reading
1. List exactly what the attacker can query and observe, and what they do *not* know about the
   target model or its training data. Use this list as your threat-model section.
2. The attack relies on shadow models. What assumption links a shadow model's behaviour to the
   target model's behaviour, and in what situation would that assumption break?
3. Why is the attack model trained separately for each output class rather than as one model?
4. One evaluation dataset comes from a health setting. Which one is it, and what would a
   successful membership inference reveal about a real person in that setting?
5. Sections VI-G and VII link attack success to overfitting. On their evidence, is overfitting
   necessary for the attack, sufficient, or neither? Which mitigations in Section VIII did they
   test, and does any of them come with a formal guarantee?

## Pointer for Project B
Write down which attack setup you would reuse to compare a non-private and a DP-SGD ECG
classifier. Later work argues that average accuracy hides the attack's real strength and that
you should report the true-positive rate at a low false-positive rate. See Carlini et al.,
"Membership Inference Attacks From First Principles", IEEE S&P 2022
(<https://arxiv.org/abs/2112.03570>). Optional follow-up; do not summarise it yet.
