# Public Evidence Capstone: Should This Agent Evaluation Support a Release?

> **Portfolio study using published evidence.** This report is a worked example
> of evidence-backed reasoning across Julie Elkins' public evaluation projects.
> It is not a new benchmark score, provider leaderboard result, production
> approval, or claim that the repositories measure the same construct.

## 1. Decision and failure cost

**Decision:** Does the public evidence support treating the evaluated agent
workflow as reliable enough for a broader release or leaderboard-style claim?

**Recommendation:** **Hold the broader claim; continue with bounded diagnostics
and a pre-specified replication plan.**

The evidence supports narrower claims about specific configurations and failure
paths. It does not support a universal model ranking, a production-readiness
claim, or a single composite reliability score.

The failure cost is asymmetric. A benchmark failure is visible and usually
stops a task claim. An execution failure can prevent a score from being
observed. Missing evidence can make a passing task impossible to audit. A
provider refusal or setup timeout is therefore not silently converted into a
benchmark failure, and a benchmark pass is not treated as proof that the
execution evidence is complete.

The unit of analysis for the Harbor comparison is one agent attempt on one
public Terminal-Bench 2.0 task. The unit of analysis for ESAC-Bench is one
synthetic task or recovery case under a declared contract. The unit of analysis
for the validity study is a graded turn or declared behavioral case. These units
must not be pooled into one score.

## 2. Contracts

### Task contract

For the Harbor study, the task contract is: run the selected public coding task
under the pinned benchmark, task-set, runner, and environment configuration;
record whether Harbor completed cleanly; and report the native verifier result
when a trustworthy observation exists.

For ESAC-Bench, the task contract is more explicit: the deterministic verifier
must accept the outcome, the expected effects must be correct, and the declared
evidence identifiers must be present. Outcome, recovery safety, evidence
completeness, and claim support are reported separately.

### Evidence contract

A public completion claim requires bounded metadata that lets a reviewer
distinguish at least:

- clean execution from provider, setup, timeout, or transport failure;
- benchmark pass, benchmark failure, and no trustworthy observation;
- presence or absence of the expected trajectory or equivalent metadata;
- the pinned task, benchmark, runner, and configuration identity; and
- the limitation that remains when the evidence is incomplete.

The Agent Assurance Harness is a secondary assurance check, not a replacement
for the benchmark verifier. Its evidence boundary checks whether the recorded
metadata is sufficient to support the bounded claim without publishing raw
prompts, tool arguments, provider responses, credentials, or trajectories.

### Negative controls

The public portfolio includes negative controls that are designed to look
successful until the evaluator checks the right dimension:

- a benchmark can pass while the expected trajectory artifact is absent;
- ESAC-Bench mutations remove evidence, duplicate effects, create stale state,
  or leave an unsupported completion claim;
- the RAG lab uses a wrong document, stale source, unsupported citation, and
  forced answer for an unanswerable question; and
- the validity study separates a perfect observed policy record from the
  larger error bound that the sample can actually support.

If a control is not detected, the evaluator is not ready to support the claim.

## 3. Comparison and uncertainty

### Harbor matched cohorts

The original matched cohort used the same ten public Terminal-Bench 2.0 tasks,
one attempt per task, the same task-set revision, and the same Finch
compatibility path.

| Runner and cohort | Attempted | Clean executions | Benchmark observations | Passes | Execution completion | Pass rate / attempted | Conditional pass rate |
| --- | ---: | ---: | ---: | ---: | ---: | ---: | ---: |
| Codex, original matched cohort | 10 | 10 | 10 | 7 | 100% | 70% | 70% |
| mini-swe-agent, original matched cohort | 10 | 9 | 9 | 6 | 90% | 60% | 66.7% |
| mini-swe-agent, post-bridge follow-up | 10 | 10 | 10 | 9 | 100% | 90% | 90% |
| mini-swe-agent, replication diagnostic | 10 | 9 | 9 | 7 | 90% | 70% | 77.8% |

The original mini-swe-agent `qemu-startup` task failed during setup and did
not produce a trustworthy benchmark observation. The follow-up cohort is a
new execution, not a replacement for the original cohort and not causal proof
that the credential or evidence bridge caused the improvement. The replication
diagnostic was not clean because `qemu-startup` timed out during agent
execution, so it remains outside a leaderboard denominator.

The public report therefore supports these bounded statements:

1. Codex completed all ten original executions and passed seven.
2. mini-swe-agent completed nine of the ten original executions and passed six.
3. A separate post-bridge mini-swe-agent follow-up completed ten executions and
   passed nine under the recorded configuration.
4. Those cohorts should not be combined into one score or used to claim that
   one provider or agent is universally better.

The comparison is paired at the task level because the agents saw the same task
set, but the original study has only one attempt per task. A paired difference
is therefore descriptive evidence, not a high-powered estimate of general
agent capability. A future replication should pre-register the cohort,
attempt count, exclusion rules, and analysis before running.

### Statistical validity evidence

The separate LLM Eval Validity study demonstrates why a point estimate is not
enough for a release decision:

- the policy family recorded 79 correct answered turns out of 79, but the
  95% upper error bound is 4.6%, above a declared 2.0% tolerance;
- demonstrating a 2.0% error tolerance with zero observed errors requires
  roughly 189 clean answered observations under the study's planning method;
- the behavior family recorded 3 restricted-action violations in 19 scored
  turns, with a lower bound of 5.5% against a 5.0% tolerance; and
- pooling the families hides the fact that they have different failure costs
  and different standards.

The study's statistics lab explains paired bootstrap, McNemar's test, cluster
bootstrap, multiple-comparison correction, confidence intervals, pass@k,
pass^k, and cost per solved task. Those tools are available for a future
pre-registered cohort, but they do not manufacture uncertainty estimates for
the one-attempt Harbor runs.

`pass@k` means at least one of `k` attempts succeeds. `pass^k` means all `k`
attempts succeed. A recovery or evidence contract often needs the stricter
interpretation, while a capability search may use the first. They answer
different questions and must not be substituted for one another.

Observed Harbor cost is a recorded run observation, not a provider billing
guarantee. Cost per solved task is not a valid comparison when a cohort has no
trustworthy benchmark observations or when the cost accounting boundary is
different.

## 4. Judge calibration

The judge-calibration work is useful evidence, but it does not establish that a
judge can approve a release.

The response-quality study compared two model judges and a regex grader with one
human auditor over 192 policy turns. Headline agreement with that auditor was:

| Rater | Raw agreement | Kappa |
| --- | ---: | ---: |
| Sonnet judge | 93.8% | 0.872 |
| Haiku judge | 95.3% | 0.904 |
| Regex grader | 88.0% | 0.772 |

Repeated judge passes showed run-to-run variation, and the judge validation
identified order sensitivity and corpus cues. The study also found that the
judge could be useful as a screen that routes cases to a human reviewer.

The required human-human ceiling is **not established** because the published
study used one independent human auditor. That means judge-human agreement
cannot yet be interpreted as agreement with a stable human reference
population. An additional independent rater on a frozen, stratified subset,
followed by adjudication, is required before considering release-gate use.

**Decision:** the judge is suitable for bounded screening and error discovery,
not for autonomous release approval. Repeatability is a different property
from validity: a judge can be consistently wrong or consistently agree with
one auditor's labels.

## 5. Retrieval and answer failure decomposition

The RAG Failure-Decomposition Lab is an offline synthetic control, not a live
retrieval benchmark. It evaluates BM25-style lexical retrieval, a transparent
semantic retriever, hybrid retrieval, ranking, context assembly, grounding,
citations, stale sources, wrong documents, and unanswerable questions.

Its deterministic output shows that the answer layer must not hide the retrieval
layer:

| Failure layer | Public control | Correct interpretation |
| --- | --- | --- |
| Retrieval | The needed source may be absent from top-k | Improve retrieval or ranking |
| Context assembly | A stale or conflicting source may remain in context | Add revision-aware selection |
| Generation | The answer may ignore evidence that was retrieved | Add grounded-answer checks |
| Citation | A cited identifier may not support the claim | Validate citation support |
| Answerability | An unanswerable question may be forced into an answer | Require abstention or escalation |

The lab's candidate release decision is `block` because its negative controls
are intentionally present. That is evaluator-control evidence, not evidence
that a production retriever or model should be blocked.

## 6. Recovery and evidence

ESAC-Bench is the canonical source for the recovery contract. Its offline
reference run uses six core synthetic task contracts and a separate seven-case
Recovery Track. The guarded profile passes all four recovery dimensions across
all seven cases:

- final-state restoration;
- side-effect integrity;
- recovery-evidence completeness; and
- bounded recovery.

The naive profile is intentionally not safe: it fails claim support in all
seven recovery cases, fails evidence completeness in all seven, and exposes
state or side-effect failures in selected cases. The mutation suite also
detects missing evidence, duplicate effects, stale state, and unsupported
success.

These are strong evaluator controls, not production recovery proof. They show
that the contract can catch planted failures before a live adapter is trusted.

The Harbor study adds a real evidence-pipeline finding: a controlled Claude
Code task passed, but Harbor did not produce the expected ATIF trajectory
artifact. The adapter refused to label the run ATIF-verified and recorded the
available fallback metadata path instead. This is why benchmark correctness and
evidence completeness remain separate dimensions.

For a real release decision, the reviewer must be able to answer:

- what state was retained after interruption;
- whether retry or handoff could duplicate an effect;
- whether transport completion was confused with semantic task completion;
- whether the trajectory or equivalent record is present; and
- what the system does when the evidence artifact is missing.

## 7. Limits and operational controls

- The Harbor comparison is a small, one-attempt, ten-task study.
- The post-bridge and replication cohorts are separate evidence sets.
- The Harbor task results are calibration evidence for ESAC-Bench, not native
  ESAC-Bench scores.
- ESAC-Bench and the RAG lab are synthetic and offline.
- The judge study has one human auditor and no human-human ceiling.
- The current work does not establish long-horizon reliability, user outcomes,
  production safety, multilingual quality, or provider-general rankings.
- Provider, setup, timeout, transport, and missing-evidence outcomes must remain
  visible rather than being converted into benchmark failures.
- Credentials, raw trajectories, prompts, tool arguments, provider responses,
  and private learner or assessment content remain outside the public repos.
- Runtime, retry, output, and spend ceilings must be declared before any live
  rerun.
- A human owner must approve any release decision, and a failed negative
  control triggers hold or revise-and-rerun.

## 8. Final recommendation

I recommend **hold the broader release or leaderboard claim** because the
published evidence demonstrates useful task-level and evidence-pipeline
findings, but the matched cohorts are small, the judge lacks an independent
human-human ceiling, and the synthetic controls do not establish production
behavior. This does not establish that Codex, mini-swe-agent, Claude Code, or
any provider is universally better. The next review is a pre-registered,
bounded replication with independent human calibration, explicit recovery
evidence, and separate reporting of execution completion, benchmark
correctness, evidence completeness, and claim support.

## Canonical sources

- [Harbor Assurance Adapter study summary](https://github.com/julie-elkins/harbor-assurance-adapter/blob/main/docs/study-summary.md)
- [Harbor comparison metrics](https://github.com/julie-elkins/harbor-assurance-adapter/blob/main/docs/metrics.md)
- [ESAC-Bench specification](https://github.com/julie-elkins/esac-bench/blob/main/docs/benchmark-spec.md)
- [ESAC-Bench calibration policy](https://github.com/julie-elkins/esac-bench/blob/main/docs/calibration-policy.md)
- [Eval Statistics Interview Lab](https://github.com/julie-elkins/llm-eval-validity/blob/main/docs/eval-statistics-interview-lab.md)
- [Human-Grounded Judge Calibration Study](https://github.com/julie-elkins/llm-eval-validity/blob/main/research/response-quality/CALIBRATION_STUDY.md)
- [LLM Eval Validity decision summary](https://github.com/julie-elkins/llm-eval-validity/blob/main/docs/executive-summary.md)
- [RAG Failure-Decomposition Lab](https://github.com/julie-elkins/claude-evaluation-lab/tree/main/labs/optional-rag-failure-decomposition)
- [Agent Assurance Harness](https://github.com/julie-elkins/agent-assurance-harness)
