# Sample Atlas Capstone Report

> **Illustrative synthetic example — not a benchmark result, provider result,
> or production recommendation.** The numbers below demonstrate report shape
> and claim discipline. They must not be reused as evidence for a real system.

## 1. Decision and failure cost

**Decision:** Should Atlas enter a limited internal pilot for documentation
questions and bounded configuration proposals?

**Failure cost:** A wrong answer could send a user to an obsolete procedure.
A false completion claim could leave a configuration change without a
recoverable record. A judge that approves unsupported answers could turn either
failure into an accepted release result.

**Recommendation:** **Hold.**

The candidate shows a possible task-outcome improvement, but the evidence path
is incomplete and the judge is suitable for screening only.

## 2. Contracts

**Task contract:** Atlas must answer the selected documentation question using
the current source, cite the supporting document identifier, and produce the
requested bounded configuration proposal without inventing an answer when the
question is unanswerable.

**Evidence contract:** A completion claim requires the task result, source and
revision identifiers, citation-support status, recovery status when applicable,
and a present trajectory or equivalent metadata record. Missing evidence is not
treated as a pass.

**Negative controls:**

- a stale document is ranked above the current document;
- the answer cites a document that does not support the claim; and
- an unanswerable question is forced into an answer.

## 3. Comparison and uncertainty

The following values are synthetic teaching values for this report:

| Measure | Baseline | Candidate |
| --- | ---: | ---: |
| Matched tasks passed | 12/20 | 14/20 |
| Execution attempts completed | 20/20 | 20/20 |
| Paired candidate wins | — | 5 |
| Paired baseline wins | — | 3 |
| Relative cost units | 16 | 18 |
| Solved tasks | 12 | 14 |
| Relative cost per solved task | 1.33 | 1.29 |

The cases are paired because both systems saw the same synthetic tasks. A
paired bootstrap produced an illustrative 95% interval of **-0.05 to +0.20**
for the candidate-minus-baseline pass-rate difference. Because that interval
includes zero and the sample is small, the result does not establish a reliable
ranking.

The cost value is a relative teaching unit, not a dollar estimate. The report
does not claim live-provider pricing or production efficiency.

Pass@k and pass^k are not interchangeable here: pass@k would ask whether at
least one attempt succeeded, while pass^k would ask whether every attempt
succeeded. The recovery decision needs the second kind of reliability for the
required evidence path.

## 4. Judge calibration

| Calibration measure | Synthetic result | Interpretation |
| --- | ---: | --- |
| Human-human agreement | 0.90 | The reference ceiling is not perfect |
| Judge-human agreement | 0.75 | Some screening signal exists |
| Judge repeatability | 0.92 | The judge is internally consistent |
| Position-bias probe | detected | Candidate order changes some labels |
| Verbosity-bias probe | not detected | No change in this probe |
| Abstention handling | present | Abstentions remain visible |

The judge is **screening only**. Repeatability does not compensate for
insufficient agreement with the human reference or for detected position bias.
No release decision should rely on this judge alone.

## 5. Retrieval and answer failure decomposition

| Failure layer | Synthetic observation | Correct next action |
| --- | --- | --- |
| Retrieval | Current source appeared in top five for 18/20 cases | Improve ranking for the two misses |
| Context assembly | One stale source remained in the assembled context | Enforce revision-aware context selection |
| Generation | One answer ignored available current evidence | Add a grounded-answer check |
| Citation | 3/20 citations did not support the claim | Block unsupported citations |
| Wrong-document control | Detected | Keep this control in the suite |
| Unanswerable control | Candidate answered instead of abstaining | Strengthen the task contract and abstention check |

The main failure is not explained by a single overall answer score. Retrieval,
context assembly, generation, and citation validation each need their own
evidence.

## 6. Recovery and evidence

Five synthetic interruption, retry, or handoff trials produced:

- 5/5 task outcomes observed;
- 4/5 complete evidence records;
- 4/5 supported completion claims; and
- 1/5 missing trajectory artifacts.

The missing trajectory artifact is a blocking evidence failure. The task result
cannot be treated as proof of successful recovery when the record needed to
support the claim is absent.

Transport completion is separate from semantic task completion. A process that
returns successfully but leaves no recoverable evidence is not a clean pass.

## 7. Limits and operational controls

- The scenario and all values are synthetic and offline.
- No provider credentials, private prompts, or raw provider responses were used.
- Runtime, retry, and spend ceilings must be declared before any live study.
- The judge must not approve a release while position bias and weak
  judge-human agreement remain unresolved.
- The recovery lane must be rerun after the trajectory-recording defect is fixed.
- A human reviewer owns the final release decision.

## 8. Final recommendation

I recommend **hold** because the candidate's possible task-outcome improvement
is uncertain, the judge is suitable for screening but not release, and one of
five recovery trials lacks the evidence artifact required to support its
completion claim. This does not establish live model quality, production
reliability, or a provider ranking. The next review is a bounded rerun after
trajectory recording and abstention behavior are corrected.

## Reviewer notes

This is a strong capstone answer because it:

- states the decision before the score;
- keeps task outcome, execution reliability, evidence completeness, and claim
  support separate;
- treats the judge's repeatability as different from judge-human validity;
- identifies the failure layer instead of prescribing a generic model change;
- blocks on missing recovery evidence; and
- limits every claim to the synthetic configuration.
