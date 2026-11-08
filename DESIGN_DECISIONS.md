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
