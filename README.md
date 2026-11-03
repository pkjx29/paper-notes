# paper-notes

One-page summaries of research papers in ML privacy and security, written as I read them.
They cover differential privacy, privacy attacks on ML models, attacks on LLM and RAG
applications, and confidential computing for ML.

Two of my ongoing projects draw on these papers: **Project A** (attacks on retrieval-augmented
generation systems) and **Project B** (a differentially private ECG classifier). Each summary
ends with how the paper affects that work.

Why these six papers were chosen: [PAPERS.md](PAPERS.md).

## Index

Status: ⬜ not started · ✏️ in progress · ✅ done

| # | Paper | Year | Topic | Reading guide | Summary | Status |
|---|---|---|---|---|---|---|
| 01 | Membership Inference Attacks Against ML Models (Shokri et al.) | 2017 | Privacy attack | [guide](guides/01-membership-inference.md) | — | ⬜ |
| 02 | Deep Learning with Differential Privacy (Abadi et al.) | 2016 | Differential privacy | [guide](guides/02-dp-sgd.md) | — | ⬜ |
| 03 | FL and DP on Multi-hospital ECG Data (Agrawal et al.) | 2024 | DP for ECG | [guide](guides/03-fl-dp-ecg.md) | — | ⬜ |
| 04 | Indirect Prompt Injection (Greshake et al.) | 2023 | LLM security | [guide](guides/04-indirect-prompt-injection.md) | — | ⬜ |
| 05 | Privacy Issues in RAG (Zeng et al.) | 2024 | LLM privacy | [guide](guides/05-rag-privacy.md) | — | ⬜ |
| 06 | Slalom: Private Execution of NNs in Trusted Hardware (Tramèr & Boneh) | 2019 | Confidential computing | [guide](guides/06-slalom-tee.md) | — | ⬜ |

When a summary is started, link it in the Summary column as `summaries/NN-short-name.md` and set
the status to ✏️. Change it to ✅ once it has been reviewed and revised.

Suggested reading order: 01 → 02 → 03 (privacy for Project B), then 04 → 05 (LLM security for
Project A), then 06.

## How these notes are written

- Every summary follows [TEMPLATE.md](TEMPLATE.md): problem, threat model, method, key result,
  limitations, connection to my projects, and open questions. Each fits on about one page.
- The summaries are my own words. Quotations are at most one sentence, in quotation marks, with a
  page number. Figures and tables are cited, not copied.
- Each number has a pointer to the table, figure or section it came from.
- The reading guides in `guides/` list the sections to focus on, the background each paper needs,
  and five questions to answer while reading. They are study aids, not summaries.
- A summary is marked ✅ only after a review pass for accuracy (does it match the paper?) and
  clarity (could a classmate follow it?), and after I have revised it.

## Layout

```
paper-notes/
├── README.md        index (this file)
├── PAPERS.md        paper list with links and why each one was chosen
├── TEMPLATE.md      one-page summary template
├── guides/          one reading guide per paper
└── summaries/       my summaries (added as I write them)
```
