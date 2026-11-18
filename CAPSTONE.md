# Evaluation Engineer Capstone: Make the Release Decision

The capstone is the final integrated exercise in this learning path. You will
combine the statistics, judge-calibration, retrieval, and recovery work into one
bounded decision report.

This is a teaching exercise, not a live-provider benchmark. It uses synthetic
evidence and links to the canonical repositories instead of copying their
implementations.

## The scenario

You are reviewing **Atlas**, a synthetic agent that:

1. retrieves product documentation;
2. answers a support question with citations;
3. proposes a bounded configuration change; and
4. resumes after an interruption or handoff.

The team wants to move Atlas from an internal experiment to a limited pilot.
Your job is to decide whether the evidence supports that move.

The cost of a wrong release decision is not only an incorrect answer. Atlas
could cite the wrong document, report completion without a recoverable record,
or pass a judge that is not calibrated well enough to support release.

## Your decision

Write one of these recommendations:

- **release** — the declared evidence supports the limited pilot;
- **hold** — important evidence is missing or a negative control failed;
- **revise and rerun** — the design or evidence contract needs a bounded change;
- **rollback** — an already-approved condition is no longer supported; or
- **escalate** — the evidence is ambiguous and requires human adjudication.

Do not choose a recommendation from the overall score alone. A passing task
result cannot compensate for missing evidence, an unsafe recovery path, or a
judge that is only suitable for screening.

## Evidence map

Use the canonical implementation in each repository. Do not copy its source
code or replace its results with an unmarked learner estimate.

| Question | Canonical source | Evidence to bring into the report |
| --- | --- | --- |
| How uncertain is the comparison? | [Eval Statistics Interview Lab](https://github.com/julie-elkins/llm-eval-validity/blob/main/docs/eval-statistics-interview-lab.md) | Unit of analysis, dependence assumption, interval, paired or clustered comparison, and cost interpretation |
| Can the judge support the decision? | [Human-Grounded Judge Calibration Study](https://github.com/julie-elkins/llm-eval-validity/blob/main/research/response-quality/CALIBRATION_STUDY.md) | Human-human ceiling, judge-human agreement, repeatability, bias probes, abstention, and screening/release suitability |
| Where does retrieval fail? | [RAG Failure-Decomposition Lab](https://github.com/julie-elkins/claude-evaluation-lab/tree/main/labs/optional-rag-failure-decomposition) | Retrieval, context, generation, citation, stale-source, wrong-document, and unanswerable-case results |
| What survives interruption? | [ESAC-Bench Recovery Track](https://github.com/julie-elkins/esac-bench/blob/main/docs/benchmark-spec.md#recovery-track) | Task outcome, recovery safety, evidence completeness, claim support, and the artifact that supports completion |
| What does the assurance layer block? | [Agent Assurance Harness](https://github.com/julie-elkins/agent-assurance-harness) | Required evidence, negative controls, refusal or hold conditions, and the boundary of the claim |

## Required report

Create a report with these sections. The headings are a contract: keeping them
separate prevents one attractive number from hiding a different failure.

### 1. Decision and failure cost

State:

- the decision Atlas must support;
- who is allowed to make the decision;
- what failure would cost;
- the population and task unit; and
- the recommendation you are making.

### 2. Contracts

Write the task contract and evidence contract in plain language.

- The **task contract** says what counts as a successful answer or action.
- The **evidence contract** says what must be observable before the completion
  claim can be accepted.

Include at least one negative control: a case designed to produce a known
failure so the evaluator has to demonstrate that it can catch a false pass.

### 3. Comparison and uncertainty

Report the baseline and candidate results, but also explain:

- whether cases are paired, independent, or clustered;
- what interval or test supports the comparison;
- whether the sample is large enough for the decision;
- whether multiple comparisons were corrected;
- the difference between pass@k and pass^k; and
- cost per solved task, including when that quantity is undefined.

If you cannot justify a statistic, mark it **not established** instead of
substituting a more familiar metric.

### 4. Judge calibration

State whether the judge is suitable for:

- screening only;
- screening and release; or
- neither.

Show the human-human ceiling, judge-human agreement, repeatability,
position or verbosity bias probes, rubric redundancy review, and abstention
handling. If the required human reference does not exist, say so explicitly.

### 5. Retrieval and answer failure decomposition

Separate:

1. failure to retrieve the needed source;
2. failure to assemble the right context;
3. failure to use available evidence;
4. citation that does not support the claim;
5. grounding in a stale or wrong document; and
6. an answer forced for an unanswerable question.

Explain whether the proposed fix belongs in retrieval, context assembly,
generation, citation validation, or the task contract.

### 6. Recovery and evidence

Describe what happens after interruption, retry, or handoff.

- What state is retained?
- What state is intentionally discarded?
- Can the system distinguish “task completed” from “transport finished”?
- Is the trajectory or equivalent evidence present?
- Can a reviewer reconstruct why the completion claim was accepted?
- What happens if the evidence artifact is missing?

### 7. Limits and operational controls

Record:

- runtime, retry, and spend ceilings;
- data and credential boundaries;
- what was synthetic or offline;
- what was not tested;
- what would require human approval; and
- what would trigger a rerun or rollback.

### 8. Final recommendation

Write a short decision memo:

> I recommend **[release / hold / revise and rerun / rollback / escalate]**
> because **[strongest evidence]**. This does not establish **[explicit
> limitation]**. The next review is **[specific check or owner]**.

## Reviewer rubric

A reviewer should be able to answer “yes” to each item:

- Is the decision stated before the results?
- Is the failure cost concrete?
- Are task outcome, execution reliability, evidence completeness, and claim
  support separate?
- Are dependence assumptions and uncertainty visible?
- Is the judge compared with independent human reference labels?
- Are retrieval and generation failures separated?
- Does the recovery section test interruption, retry, or handoff?
- Is there a negative control that the evaluator catches?
- Are missing, skipped, refused, and failed states distinguishable?
- Does the recommendation stay within the evidence boundary?

An incomplete answer is useful feedback. This rubric is not a certification or
a prediction of production readiness.

## Learner feedback

After completing the capstone, record:

- which stage was hardest and why;
- which term or decision boundary was unclear;
- which command or link failed;
- which evidence you wanted but could not observe; and
- one change that would make the path easier for the next learner.

Do not include credentials, private prompts, raw provider payloads, unpublished
exam content, reviewer identities, or private learner data.
