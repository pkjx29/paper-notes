# Paper list and rationale

Six papers: three foundational (2016–2019) and three recent (2023–2024). Together they cover
the two research areas I am preparing for, differential privacy, and LLMs/AI agents with
privacy and security, plus confidential computing for ML. Each one feeds a project I am
building:

- **Project A:** attacks on retrieval-augmented generation (RAG) systems.
- **Project B:** a differentially private ECG classifier.

The context is the Centre of Data for Public Good (CDPG) at IISc. CDPG builds data exchanges
and data platforms for urban, agricultural and public-health data. Its site highlights consent,
controlled access, privacy-preserving AI, and federated AI without exposing raw data.

Each entry below was checked against its arXiv page and its publisher or venue record on
2026-10-21.

| # | Paper | Venue | Kind | Feeds |
|---|---|---|---|---|
| 01 | Shokri, Stronati, Song, Shmatikov. *Membership Inference Attacks Against Machine Learning Models.* [arXiv:1610.05820](https://arxiv.org/abs/1610.05820) · [DOI](https://doi.org/10.1109/SP.2017.41) | IEEE S&P 2017 | Foundational, attack | B |
| 02 | Abadi, Chu, Goodfellow, McMahan, Mironov, Talwar, Zhang. *Deep Learning with Differential Privacy.* [arXiv:1607.00133](https://arxiv.org/abs/1607.00133) · [DOI](https://doi.org/10.1145/2976749.2978318) | ACM CCS 2016 | Foundational, defence | B |
| 03 | Agrawal, Kalmady, Malipeddi, Manthena, Sun, Islam, Hindle, Kaul, Greiner. *Federated Learning and Differential Privacy Techniques on Multi-hospital Population-scale Electrocardiogram Data.* [arXiv:2405.00725](https://arxiv.org/abs/2405.00725) · [code](https://github.com/vikhyatt/Hospital-FL-DP) | ICMHI 2024 | Recent, applied DP | B |
| 04 | Greshake, Abdelnabi, Mishra, Endres, Holz, Fritz. *Not What You've Signed Up For: Compromising Real-World LLM-Integrated Applications with Indirect Prompt Injection.* [arXiv:2302.12173](https://arxiv.org/abs/2302.12173) · [DOI](https://doi.org/10.1145/3605764.3623985) | ACM AISec 2023 | Recent, attack | A |
| 05 | Zeng, Zhang, He, Xing, Liu, Xu, Ren, Wang, Yin, Chang, Tang. *The Good and The Bad: Exploring Privacy Issues in Retrieval-Augmented Generation (RAG).* [arXiv:2402.16893](https://arxiv.org/abs/2402.16893) · [ACL Anthology](https://aclanthology.org/2024.findings-acl.267/) | Findings of ACL 2024 | Recent, attack and measurement | A |
| 06 | Tramèr, Boneh. *Slalom: Fast, Verifiable and Private Execution of Neural Networks in Trusted Hardware.* [arXiv:1806.03287](https://arxiv.org/abs/1806.03287) | ICLR 2019 (oral) | Foundational, confidential computing | CDPG context |

## Why each matters for CDPG

**01 Membership inference.** The basic question for any model trained on shared records is
whether someone can tell that a particular person's record was used. For CDPG's health data
platforms, that alone can reveal a diagnosis. It is also the attack I will use to *measure*
whether Project B's DP training protects anyone.

**02 DP-SGD.** This is the standard algorithm for training models with a formal privacy
guarantee, and the basis of Opacus. If a data exchange offers model training on sensitive data,
DP-SGD is the most direct way to bound what the trained model reveals about any individual. It
is core material for the Differential Privacy role.

**03 FL + DP on ECG.** Several hospitals that cannot pool raw ECGs train one model, with DP added
at each site. This is close to the multi-party health data sharing CDPG supports, and close to
Project B's design. It is also a test of critical reading, because the privacy details are
under-specified.

**04 Indirect prompt injection.** Once an LLM assistant or agent reads data it did not write, as
it would when placed on top of a data exchange, anyone who can add data can try to steer it. This
paper set out the taxonomy the field still uses, and it frames the attacks in Project A.

**05 Privacy in RAG.** This paper shows that the private retrieval database behind a RAG system
can be extracted through ordinary queries, and it tests simple defences. One of its datasets is
medical dialogue. It is the closest published baseline for Project A's leakage experiments and
directly relevant to any LLM interface over sensitive records.

**06 Slalom (TEEs for ML).** Confidential computing protects data while models run on it, which
complements DP's protection of outputs. Slalom gives a precise trust model (enclave versus
untrusted GPU) and shows the performance trade-offs. That background helps with designing
"compute on data without seeing it" services such as data sandboxes.

## Candidates considered but not chosen (yet)
- Santos, Brito & Machado, *Differentially Private ECG Heartbeat Classification*, SBBD 2026,
  DOI [10.5753/sbbd.2026.249231](https://doi.org/10.5753/sbbd.2026.249231). Possible replacement
  or seventh paper for Project B once the full text is checked.
- *Confidential Computing on NVIDIA Hopper GPUs: A Performance Benchmark Study* (2024),
  [arXiv:2409.03992](https://arxiv.org/abs/2409.03992). A recent GPU-TEE follow-up to 06.
- Carlini et al., *Membership Inference Attacks From First Principles*, IEEE S&P 2022,
  [arXiv:2112.03570](https://arxiv.org/abs/2112.03570). The modern evaluation standard for MIAs;
  a follow-up to 01.
