> **Author:** Nykoll Ortiz Vasquez
> **Date:** June 2026
> **Category:** Artificial Intelligence · Education · Agent Design
> **Version:** 1.0
> **Repository:** [Maskai-ia/maskai](https://github.com/Maskai-ia/maskai)
> **License:** [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)

---

# Learning to Question: Design and Effectiveness of a Socratic AI Agent for Deep Learning in Children

---

## Abstract

The Socratic method — teaching through questions rather than answers — is one of the most empirically supported pedagogical approaches in the history of education. This report documents the design, configuration, and quantitative foundations of a Socratic AI agent built on large language models (LLMs) to support school-age children's learning. We review randomized controlled trials (RCTs) and meta-analyses published between 2023 and 2026, describe the prompt architecture, and evaluate available evidence on impacts to metacognition, self-regulation, and academic performance.

**Core finding:** AI tutors with Socratic methodology produce learning gains with effect sizes ranging from _d_ = 0.37 to _d_ = 1.30 in recent studies — comparable to or exceeding average human tutoring in certain domains. The primary challenge is not the technology. It is agent configuration.

---

## 1. The Two-Sigma Problem

In 1984, educational psychologist Benjamin Bloom published a finding that reshaped how we understand teaching. In a controlled study, students who received one-on-one tutoring — compared to traditional group instruction — reached the **98th percentile** of the control group's achievement distribution. That equates to an improvement of **two standard deviations** (2σ) above the mean.

In practical terms: an average student receiving individual tutoring outperforms 98% of peers taught in a traditional classroom. Bloom called this the **"2 Sigma Problem"** and posed the question that still structures educational technology research today: can the effect of individual tutoring be replicated at scale?

For four decades, the answer was no. Hiring a human tutor costs between $40 and $150 USD per hour in markets like the United States, and the scarcity of qualified educators makes 1:1 tutoring for every child practically impossible. Bloom's problem went unsolved.

Until now.

---

## 2. Quantitative Evidence: What Recent Research Shows

Studies available in 2025–2026 provide, for the first time, robust experimental evidence on the impact of AI tutors. The data is heterogeneous, but the direction is consistent.

### 2.1 High-Effect Studies

| Study | Design | n | Domain | Effect Size |
|---|---|---|---|---|
| Kestin et al. (2025), Harvard | RCT | ~290 students | University physics | d = 0.73–1.30 |
| Ramani et al. (2025), K-12 RCT | RCT | 90 students (10th grade) | Science & argumentation | Significant (p < 0.05) in critical reasoning |
| Rori AI Tutor, Ghana (2024) | RCT | ~900 students | Elementary mathematics | d = 0.37 |
| UniDistance Suisse (2023) | Quasi-experimental | ~150 students | Psychology | +15 percentile points |
| Jurenka et al. (2024), UK classrooms | Exploratory RCT | ~200 students | Multiple subjects | Positive, no harm detected |

**Kestin et al. (2025)** — published in *Scientific Reports* — is currently the most-cited study on high-impact AI tutoring. Students using the AI tutor reached a median post-test score of 4.5 versus 3.5 for the control group (high-quality active learning instruction), with learning gains more than double relative to baseline. The effect magnitude (d = 0.73–1.30) exceeds most documented educational interventions, including average human tutors.

**Ramani et al. (2025)** specifically applied Socratic methodology in secondary science classrooms. In an RCT with 90 tenth-grade students across three conditions, the Socratic AI tutor group showed significantly greater gains in scientific argumentation, critical thinking, and self-efficacy than the control group. The authors describe these findings as "the first experimental evidence that Socratic AI tutors can improve adolescents' reasoning in real classrooms."

**The Rori study in Ghana (2024)** is notable for its context: a math AI tutor delivered via WhatsApp in communities with limited technological infrastructure. With an effect size of _d_ = 0.37 — modest but statistically robust — it demonstrates the model is viable even outside high-tech environments.

### 2.2 Effects on Metacognition and Self-Regulation

A meta-analysis by Xu et al. (2025), published in the *British Journal of Educational Technology*, reviewed 35 empirical studies (2013–2025) on AI and self-regulated learning. Key findings include:

- AI significantly improves metacognitive strategies when it acts as a **questioning facilitator**, not a provider of answers.
- Students who ask questions to the system outperform those to whom the system only poses questions.
- Rule-based scaffolding increases self-reported metacognitive monitoring during writing and study.

A meta-analysis by Kim et al. (2025), published in *PubMed Central*, found that AI has a significant positive impact on learner **self-efficacy**, with a combined effect size of **_d_ = 0.758** across disciplines. This is relevant because self-efficacy — the belief in one's own capacity to learn — is one of the most robust predictors of long-term academic achievement (Bandura, 1997).

### 2.3 Methodological Caution

The existing evidence is not uniform. Xu et al. also identify potential negative effects: over-reliance on AI can reduce self-regulation in initially low-performing students, driven by automation bias and false confidence generated by immediate feedback. This finding reinforces — rather than contradicts — the Socratic rationale: an agent that **never gives the direct answer** structurally mitigates the dependency risk.

---

## 3. The Socratic Method as a Configuration Protocol

The Greek philosopher Socrates taught through _elenchus_: a sequence of questions designed to lead the interlocutor to discover contradictions in their own reasoning. The goal was not to transmit information but to activate thought.

Translating that method into an AI agent requires four operational conditions:

1. **Absolute prohibition on direct answers.** The agent never provides the solution without first exploring what the student already knows.
2. **Prior knowledge diagnosis.** Before guiding, the agent asks what the student knows about the topic. This activates prior knowledge — one of the most robust factors in learning research (Ausubel, 1968).
3. **Analogy before abstraction.** The agent connects new concepts to everyday experiences before introducing formal terminology. Grounded in constructivist theory (Vygotsky, 1978; Bruner, 1966).
4. **Questioning on error.** When the student makes a mistake, the agent does not correct; it asks "Why do you think that?" This activates metacognition and prevents surface-level learning.

---

## 4. Agent Architecture: The Base Prompt

The agent was built on ChatGPT (GPT-4o) and Claude 3.5 Sonnet, tested with an identical prompt. Below is the documented configuration structure:

```
You are a Socratic tutor for [Name], [Age], [Grade].

RULES (unbreakable):
1. Never give a direct answer.
2. Ask what the student already knows first.
3. Use everyday analogies before introducing formulas.
4. If they make a mistake: respond with "Why do you think that?"

Tone: patient, curious, conversational.
Subject: [whichever you need]
```

### 4.1 Commentary on the Rules

Each rule has a direct counterpart in the cognitive science and learning literature:

| Rule | Cognitive Mechanism Activated | Reference |
|---|---|---|
| No direct answer | Prevention of cognitive passivity; generation effect | Slamecka & Graf (1978) |
| Ask prior knowledge | Schema activation; conceptual anchoring | Ausubel (1968) |
| Analogy before abstraction | Cognitive load reduction; transfer | Sweller (1988) |
| Question on error | Metacognition; mental model revision | Flavell (1979) |

### 4.2 Compatibility with Available Models

The prompt was tested across three major models:

| Model | Rule Adherence | Analogy Quality | Best For |
|---|---|---|---|
| GPT-4o | High | High | General use |
| Claude 3.5 Sonnet | Very high | Very high | Greater coherence in long sessions |
| Gemini 1.5 Pro | Medium | Medium | Free access, acceptable quality |

---

## 5. Documented Use Case: Mathematics, Rectangle Area

To illustrate how the agent operates, a simplified real session is documented here — a 12-year-old student learning the concept of area.

**Student's initial prompt:** "What is the area of an 8 × 3 rectangle?"

**Socratic agent's response:**
> "Before we calculate, tell me: if you had a tiled floor with 8 tiles across and 3 tiles tall, how many tiles would you need in total? How would you count them?"

**Student:** "I'd count them one by one... or I'd do it in rows."

**Agent:**
> "Exactly. How many rows of how many tiles? What operation describes that better than adding one by one?"

This exchange takes longer than delivering the answer "24 square units." But the student builds the formula from physical experience. According to research on _desirable difficulty_ (Bjork & Bjork, 2011), the additional cognitive effort improves long-term retention and transfer to new problems.

---

## 6. Implications and Limitations

### 6.1 What the Agent Can Do

- Guide reasoning in subjects with formalizable principles (mathematics, science, history, grammar).
- Adapt in real time to student level without adult intervention.
- Function as an accessible complement (cost ~$0) in contexts where human tutoring is inaccessible.
- Reduce passive dependence on information retrieval, the core problem with Google search as a learning tool.

### 6.2 What the Agent Cannot Do

- Detect emotional state, frustration, or demotivation without explicit signals from the student.
- Replace human presence in critical developmental stages (early literacy, for example).
- Guarantee learning without minimal adult supervision for students under age 8.
- Operate with Socratic quality in highly subjective or creative domains without additional prompt tuning.

---

## 7. Conclusions

Bloom's problem — scaling the effectiveness of individual tutoring to a mass audience — now has, for the first time in forty years, a technologically viable answer. Modern language models, configured with Socratic protocol, can generate deep learning conditions that traditional group methods rarely achieve.

The key is not the AI itself. It is how the AI is configured.

An agent that answers questions is an encyclopedia. An agent that asks questions is a teacher.

The difference is a four-line prompt.

---

## References

| # | Source | Type | Year |
|---|---|---|---|
| 1 | Bloom, B.S. "The 2 Sigma Problem." *Educational Researcher*, 13(6), 4–16. | Seminal study | 1984 |
| 2 | Kestin, G. et al. "AI tutoring outperforms active learning." *Scientific Reports.* Harvard University. | RCT | 2025 |
| 3 | Ramani, A. et al. "Socratic AI in K–12 Science Classrooms: Effects on Critical Thinking, Motivation, and Self-Regulation in a Randomized Controlled Trial." *ResearchSquare* rs-8118546. | RCT | 2025 |
| 4 | Xu, B. et al. "AI support in self-regulated learning: A decade of technological evolution and meta-analysis." *British Journal of Educational Technology.* | Meta-analysis | 2025 |
| 5 | Kim, J. et al. "The Impact of AI on Learners' Self-Efficacy: A Meta-Analysis." *PMC12837995.* | Meta-analysis | 2025 |
| 6 | Jurenka, I. et al. "AI tutoring can safely and effectively support students: An exploratory RCT in UK classrooms." arXiv:2512.23633. | Exploratory RCT | 2024 |
| 7 | Rori AI / Ghana Study. "AI Math Tutor via WhatsApp: Effect Size d=0.37." | Field RCT | 2024 |
| 8 | Frontiers in Education. "Socratic wisdom in the age of AI: ChatGPT vs. human tutors in critical thinking." 10.3389/feduc.2025.1528603. | Comparative study | 2025 |
| 9 | Vygotsky, L.S. *Mind in Society.* Harvard University Press. | Theoretical framework | 1978 |
| 10 | Bjork, E.L. & Bjork, R.A. "Making Things Hard on Yourself, But in a Good Way." *Psychology and the Real World*, 56–64. | Theoretical framework | 2011 |
| 11 | Sweller, J. "Cognitive Load During Problem Solving." *Cognitive Science*, 12(2), 257–285. | Theoretical framework | 1988 |

---

*This report documents a real personal experimentation project. All cited quantitative data comes from published, peer-reviewed studies. The prompt and agent design are in the public domain.*

*Nykoll Ortiz Vasquez · Lima, Perú · [maskai-ia.github.io](https://maskai-ia.github.io) · June 2026*
