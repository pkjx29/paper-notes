# Reading guide 04 — Not What You've Signed Up For: Compromising Real-World LLM-Integrated Applications with Indirect Prompt Injection

**Greshake, Abdelnabi, Mishra, Endres, Holz, Fritz** · 16th ACM Workshop on Artificial Intelligence and Security (AISec '23, co-located with CCS)
arXiv: <https://arxiv.org/abs/2302.12173> · DOI: [10.1145/3605764.3623985](https://doi.org/10.1145/3605764.3623985)
Type: recent attack paper (2023) · Length: 13 pages plus a long appendix · Suggested time: 3–4 hours

## Why read it
This paper named and organised *indirect* prompt injection: instructions planted in content
that an LLM application retrieves, rather than typed by the user. Project A attacks RAG systems,
and a planted document in a retrieval corpus is exactly this kind of entry point. For the
"LLMs, AI Agents, Privacy & Security" internship, the paper's taxonomy is common vocabulary.
Any platform that lets an AI agent read third-party data, as CDPG's data exchanges might, has
this attack surface.

## Background you need
- How an LLM-integrated application is built: system prompt, user turn, retrieved context,
  tool or plugin calls.
- The difference between a direct jailbreak and an indirect injection.
- The classic idea behind injection attacks: data and instructions share one channel (think of
  SQL injection).

Resource: OWASP Top 10 for LLM Applications, LLM01 Prompt Injection:
<https://genai.owasp.org/llmrisk/llm01-prompt-injection/>. Read it *after* the paper and
compare its framing with the paper's.

## Sections
| Read closely | Skim | Leave for a second pass |
|---|---|---|
| 1, 3.1, 3.2, 4.1, two or three demos of your choice in 4.2, 4.3, 5.2, 5.6 | 2, the other demos in 4.2, 5.3–5.5 | 5.1, Appendix A (use it as a reference for exact prompts) |

## Five questions to answer while reading
1. In indirect injection, what does the attacker control and what do they not control? How does
   this differ from a user jailbreaking a chatbot? Write it as a threat model.
2. Map each injection method in Section 3.1 onto a RAG pipeline. Which of them are still
   possible if the attacker can only add one document to the retrieval corpus?
3. Choose one threat category from Section 3.2 and trace one matching demo in Section 4.2 from
   start to finish: entry point, payload, what the model does, and the harm caused.
4. Which demonstrations ran against deployed products and which against the authors' own test
   applications? How does that affect how far the findings generalise (see 5.2)?
5. What mitigations do the authors discuss in 5.6, and why do they argue that filtering inputs
   is hard? Propose one defence you could measure in Project A, and the metric you would use.

## Pointer for Project A
Keep the paper's threat categories as the labels for the attacks you implement, so that your
results table uses vocabulary reviewers already know.
