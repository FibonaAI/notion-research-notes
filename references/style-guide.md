# Close-Reading Style and Acceptance Examples

These examples illustrate the level of explanation, not paper facts to reuse. The numbers below come from a user-approved close reading of pages 1–14 of GEPA v2 and demonstrate how to explain results. For future material, recheck the sources; do not carry these numbers or conclusions over to other work.

## Three Representative Writing Patterns

### 1. Do Not Just Name the Algorithm: Make It Possible to Work Through It

GEPA, page 6: Explaining "preserving different strengths" requires more than saying "uses Pareto selection." First label the following table as an **invented teaching example**:

| Candidate | Question 1 | Question 2 | Question 3 |
|---|---:|---:|---:|
| A | 1 | 1 | 0 |
| B | 0 | 0 | 1 |
| C | 1 | 0 | 0 |

The per-question winners are A/C, A, and B. A is at least as good as C on every question and better on one, so C is excluded from this round's sampling pool. B has a lower total score but a unique strength on Question 3. A leads on two questions and B on one, giving sampling probabilities of 2/3 and 1/3. Then clarify: this filters the current round's pool, not the entire history. This particular algorithm is not equivalent to retaining every mathematically nondominated solution.

Reusable pattern: **small example → step-by-step operations → final result → the boundary readers are most likely to misunderstand**.

### 2. Show Both Wins and Losses in the Results

GEPA, page 8: With the same Qwen3 8B model, the aggregate over six tasks is 54.85 for GEPA and 48.91 for GRPO, a difference of 5.94. But on AIME-2025 the scores are 32.00 versus 38.00, a regression of 6 points. The merged variant scores 52.40 overall, below ordinary GEPA.

Do not simply write "GEPA beats RL across the board." Keep the tasks, baselines, methods, and differences in a table. Explain which tasks contribute to the aggregate and whether they use the same metric. Discuss regressions alongside overall gains. Explicitly flag disagreements between source captions and numerical results rather than repeating promotional summaries.

Reusable pattern: **comparison conditions → table → positive and negative results → scope of the conclusion**.

### 3. Unpack the Denominator Behind Efficiency Multipliers

GEPA, page 9: 24,000 ÷ 678 ≈ 35.4 uses "rollouts consumed by the time a good candidate was found"; 24,000 ÷ 3,593 ≈ 6.7 uses "the full optimization budget." These ratios do not contradict each other; they answer different questions.

Continue by explaining the separate costs of training feedback, candidate validation, and reflection calls. Rollout counts do not automatically equal total monetary cost or wall-clock time. Do not report an efficiency multiplier without its measurement basis.

Reusable pattern: **raw quantities → calculation → meaning of the denominator → excluded costs → limits of the conclusion**.

## Architecture Figures That Can Be Read Independently

For a request such as "mark the model architecture in detail," use numbered markers on the original figure with matching explanations. Explain operations, dependencies, training-only branches, and timing indices where relevant; highlighting only the caption does not complete the request. The [architecture annotation workflow](architecture-annotations.md) contains layout, evidence, export, and delivery checks, with Moshi as a worked reference. Its four figures and 36 notes illustrate coverage rather than prescribe a quota.

## Adaptable Article Outline

Select what the material needs; do not require every subsection to repeat the same labels:

```text
Article title (work name and reading scope)
One-sentence main idea
Original sources, version, date, and reading scope

Page N / Section: a concrete question
Why this part matters
Original figure or table, if present, and how to read it
Method steps, equation explanation, or key code
Paper example / explicitly labeled invented worked example
Experimental results, differences, failures, and limitations, if applicable
What to remember from this part

Central conclusions and applicability limits
Sources, supplementary material, and necessary editorial notes
```

## Checks Before and After Publishing

- **Establish the baseline first:** Locate the latest approved article and record its sections/pages, figures, tables, equations, worked examples, and key numbers. Do not summarize again from an earlier abridged version.
- **Check explanatory completeness:** Do more than compare headings and word counts. Check that "why," "how to calculate it," and "when it does not hold" remain intact. Original figures are not standalone decorations.
- **Check presentation:** Tables on the remote page must not collapse into garbled long lines; images must display in the correct order; code and equations must be legible; and sources must be accessible. Do not treat local paths as remote attachments.
- **Check scope and boundaries:** Organize blogs by section and papers by the requested page range. When there are no experiments, explain the evidence source instead of inventing experiments. For a concise version, remove repetition rather than essential conditions.
- **Check consistency:** Read back the actual Notion content and compare it with the canonical article. A successful write request alone is not acceptance. If media display remains unconfirmed, explicitly identify that verification item as incomplete when delivering the result.
