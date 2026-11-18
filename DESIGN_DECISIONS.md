# Design decisions

This portal is deliberately a route through several repositories, not a fourth course.
The decisions below explain how the route keeps the material learnable without hiding
where the code, fixtures, and claims actually live.

The format follows the
[decision-reasoning template](https://github.com/julie-elkins/agent-systems-design-guide/blob/main/DESIGN_DECISION_TEMPLATE.md).

## 1. Keep the portal as navigation, not a duplicate implementation

- **Problem:** A fourth repository could make the learning path easier to find while
  creating a second source of truth for every lesson and command.
- **Decision:** Keep the portal responsible for sequence, learner checkpoints, and
  repository boundaries; keep each linked repository authoritative for its own material.
- **Instead of:** Copying lessons, fixtures, or analysis into this README.
- **Why:** Duplicated teaching material drifts. A learner should know which file to edit,
  verify, and cite when the underlying implementation changes.
- **Implementation:** The README links to canonical lessons, labs, reports, and
  checklists in the three connected projects.
- **Verification:** Every stage names its repository, objective, start command, expected
  result, checkpoint, and limitation.
- **Costs if wrong:** A learner may follow a stale command or believe the portal's
  summary is the implementation.
- **What this does not prove:** Links being present does not prove that the destination
  content is current; each repository owns its own verification.

## 2. Order the path by dependency, not by feature popularity

- **Problem:** Production agent failures often cross systems, data, model, tool, and
  operational boundaries. Starting with a framework feature hides those dependencies.
- **Decision:** Teach foundations, build, production operation, workflow evidence,
  measurement validity, and security in that order.
- **Instead of:** Organizing the path around vendors, frameworks, or a list of popular
  agent features.
- **Why:** A learner needs a mental model of the system before evaluating its output or
  securing its tools.
- **Implementation:** The portal flowchart and five stages make the dependency order
  explicit.
- **Verification:** Each stage states the prerequisite understanding and the checkpoint
  that must be explainable before continuing.
- **Costs if wrong:** A learner may produce a convincing demo without understanding
  authorization, recovery, evidence, or measurement.
- **What this does not prove:** Completing the path does not grant a certification or
  predict production readiness.

## 3. Make the required route offline or synthetic

- **Problem:** Credentials, network access, and provider spend make a learning path
  difficult to reproduce and unsafe to run casually.
- **Decision:** Keep the required exercises offline or synthetic; make live provider work
  optional and explicitly bounded.
- **Instead of:** Making a live model call the first gate for every learner.
- **Why:** The core lesson is reasoning about system boundaries, not access to a
  particular account or model.
- **Implementation:** The portal marks the optional judge stage and points to synthetic
  labs with bounded retry, cost, latency, evidence, and approval behaviour.
- **Verification:** The linked repositories document their commands and expected
  outputs; the required route does not require API credentials.
- **Costs if wrong:** Learners may confuse provider access with engineering skill or
  incur spend before understanding the control being tested.
- **What this does not prove:** Synthetic controls do not establish live model quality,
  production observability, or business impact.

## 4. Put production operation between build and evaluation

- **Problem:** A workflow can be technically correct in a local run and still lack
  ownership, recovery, observability, or change control.
- **Decision:** Add a production bridge before the learner studies workflow and
  measurement evidence in detail.
- **Instead of:** Treating deployment as the final paragraph after the code is built.
- **Why:** The meaning of “success” changes when a system can affect external state,
  spend money, or require incident recovery.
- **Implementation:** The bridge lab covers data contracts, access checks, semantic
  outcomes, evidence, authorization, containment, and recovery staging.
- **Verification:** The lab reports the guarded outcome and its bounded evidence; the
  readiness checklist exposes missing or refused controls.
- **Costs if wrong:** Learners may optimize a benchmark while leaving the delivery path
  unable to explain, contain, or recover a failure.
- **What this does not prove:** A completed lab is not a production approval.

## 5. Teach claims with evidence and boundaries

- **Problem:** “The test passed” is not enough to explain what the test checked or what
  the result permits someone to claim.
- **Decision:** Every stage has an expected result, learner checkpoint, and limitation.
- **Instead of:** Treating a passing command as the end of the lesson.
- **Why:** Evidence is only useful when its scope is explicit. A limitation tells the
  learner where the next review must begin.
- **Implementation:** The README pairs runnable work with plain-language questions and
  explicit non-proofs.
- **Verification:** Each linked repository keeps its own tests and reports; this portal
  checks the route and learner-facing framing.
- **Costs if wrong:** A learner may carry a synthetic result into a production decision
  as if it were a live guarantee.
- **What this does not prove:** A well-described checkpoint still needs independent
  review for a real deployment.

## 6. Make design reasoning part of the capstone

- **Problem:** New engineers can reproduce commands without learning how to choose
  between defensible designs.
- **Decision:** Require the learner to explain at least one design choice, rejected
  alternative, verification method, and production boundary at each stage.
- **Instead of:** Measuring completion only by whether the commands ran.
- **Why:** The transferable skill is making a decision that another engineer can inspect
  and challenge.
- **Implementation:** The checkpoints now point to decision maps in the linked repos and
  the canonical decision template.
- **Verification:** A reviewer can trace each decision from this portal to the owning
  repository's implementation and test.
- **Costs if wrong:** The path can look complete while teaching cargo-cult execution.
- **What this does not prove:** Explaining a design is not evidence that the design is
  correct for every workload.

## 7. Keep adjacent research optional and claim-bounded

- **Problem:** Current research on self-improving agents introduces important topics
  such as verifier validity, generated-task quality, resource tradeoffs, and continual
  learning, but adding all of them to the required route would make the learner path
  broader than its current labs and evidence support.
- **Decision:** Link the Stanford CS329A Part 9 lecture and related research surfaces as
  optional continuation material. Keep the required route focused on foundations,
  production controls, evidence, measurement validity, and security.
- **Instead of:** Expanding the current paper, synthetic labs, or required course
  checkpoints to claim coverage of every adjacent research direction.
- **Why:** Learners need a stable path through the concepts they can run and verify
  today, while advanced readers need a visible route into the next research questions.
  Separating those layers prevents optional reading from being mistaken for completed
  evidence.
- **Implementation:** The portal links the lecture; the design guide and Agent Assurance
  Harness record the adjacent checks; the response-quality study records its narrower
  frozen construct and results.
- **Verification:** Each linked artifact states whether it is a required exercise,
  executable companion, future-work surface, or research result. The current provider
  results remain unchanged.
- **Costs if wrong:** The optional section may be overlooked by learners who would
  benefit from it, or the route may appear more fragmented because the deeper material
  remains in its owning repository.
- **What this does not prove:** Reading the adjacent research does not establish that
  the current labs measure verifier validity, curriculum quality, or production
  efficiency across all environments.

## 8. Build one learner route from the missing projects

- **Problem:** Statistics, judge calibration, retrieval analysis, and recovery evidence
  are useful as separate repositories but difficult for a new learner to sequence.
- **Decision:** Add one public evaluation-engineer learning path that links the canonical
  implementations and ends with a bounded decision report.
- **Instead of:** Creating a fourth repository that copies the existing labs.
- **Why:** The learner needs a route and checkpoints, while each implementation repository
  needs to remain the authoritative source for its own code, fixtures, and claims.
- **Implementation:** `EVAL_ENGINEER_LEARNING_PATH.md` links `llm-eval-validity`,
  `claude-evaluation-lab`, and `esac-bench` by dependency order.
- **Verification:** Each stage has a runnable or inspectable artifact, an interview
  question, a limitation, and a capstone handoff.
- **Costs if wrong:** A learner may complete commands without understanding how
  uncertainty, evaluator validity, retrieval failure, or recovery changes the decision.
- **What this does not prove:** Completing the route does not certify production
  readiness or learner competence.

## 9. Make the capstone an integrated decision contract

- **Problem:** A learner can complete statistics, judge, retrieval, and recovery
  exercises independently without demonstrating how those evidence types interact
  in one release decision.
- **Decision:** Add one synthetic capstone scenario with a report contract,
  evidence map, negative-control requirement, and reviewer rubric.
- **Instead of:** Building another evaluator or copying the implementation and
  fixtures from the canonical repositories into this portal.
- **Why:** The transferable skill is deciding what the evidence supports and
  stating what it does not prove. Keeping the implementations in their owning
  repositories avoids source drift while giving the learner one coherent case.
- **Implementation:** `CAPSTONE.md` defines the Atlas scenario, required report
  sections, evidence boundaries, and feedback prompts. The learning path links to it
  as Stage 6.
- **Verification:** A reviewer can check that the report separates task outcome,
  execution reliability, evidence completeness, claim support, uncertainty, judge
  validity, retrieval failure, and recovery evidence.
- **Costs if wrong:** The capstone could become a score-collection exercise or
  imply that synthetic evidence is production approval.
- **What this does not prove:** Completing the capstone does not certify a learner,
  validate a live provider, or authorize a production release.

## 10. Include a completed synthetic report

- **Problem:** A report contract can still feel abstract to a learner who has
  never seen uncertainty, evaluator validity, retrieval failure, and recovery
  evidence combined in one decision.
- **Decision:** Include one completed synthetic Atlas report that demonstrates a
  bounded hold decision.
- **Instead of:** Publishing real provider results, copying private study data, or
  presenting a worked example as a universal answer key.
- **Why:** A concrete report makes the reasoning visible while explicit synthetic
  labeling prevents the example from being mistaken for benchmark evidence.
- **Implementation:** `examples/atlas-capstone-sample.md` covers the same sections
  required by `CAPSTONE.md`, including negative controls, relative cost units,
  judge suitability, recovery evidence, limitations, and the final recommendation.
- **Verification:** The sample states its synthetic boundary at the top and in
  its final claim; every conclusion is tied to a declared evidence dimension.
- **Costs if wrong:** Learners may copy the sample's numbers or recommendation
  instead of learning to inspect their own evidence.
- **What this does not prove:** The sample does not validate Atlas, a model,
  a provider, a production workflow, or a learner's competence.

## 11. Add a public-evidence capstone without creating a composite score

- **Problem:** The synthetic Atlas example teaches report structure, but learners
  also need to see how to use real published evidence without overclaiming or
  merging incompatible denominators.
- **Decision:** Add one claim-bounded capstone that cites the public Harbor study
  and LLM Eval Validity results, while treating ESAC-Bench and the RAG lab as
  synthetic controls rather than live scores.
- **Instead of:** Presenting a portfolio result as a universal model ranking,
  copying raw provider artifacts, or collapsing task outcome, execution
  reliability, evidence completeness, judge validity, and recovery safety into
  one number.
- **Why:** A senior evaluation engineer must be able to connect evidence across
  repositories while preserving each study's unit of analysis, denominator,
  protocol, and limitation.
- **Implementation:** `examples/public-evidence-capstone.md` reports the
  matched Harbor cohorts, sample-size and judge-calibration limits, RAG
  negative controls, ESAC-Bench recovery controls, and a hold recommendation.
- **Verification:** Every real result links to its canonical public source; every
  synthetic result is labeled; unsupported dimensions are marked not established;
  no raw trajectory, credential, prompt, provider response, or private content
  is added.
- **Costs if wrong:** A learner may mistake a well-connected portfolio for a
  single benchmark, repeat an unsupported leaderboard claim, or treat synthetic
  controls as production evidence.
- **What this does not prove:** The report does not establish production
  readiness, provider superiority, long-horizon reliability, or learner
  competence.
