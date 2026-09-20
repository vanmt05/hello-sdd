## Prompts by phase

|Phase|Essential prompt|
|---|---|
|Constitution|"Propose the constitution of this project: N short, verifiable principles about stack, quality, tests and limits. Max. 15 lines. Wait for my approval."|
|Spec (interview)|"Do NOT write code. Ask me questions one at a time (max. 6) about edge cases, errors and scope, and then generate spec.md with numbered RFs in EARS, out of scope and completion criteria. Only the WHAT and the WHY."|
|Clarification|"Review the spec as a professional QA: ambiguities, contradictions, missing edge cases, conflicts with the constitution. Only detect, do not resolve."|
|Plan|"Read the constitution and spec. No code: generate plan.md with modules, data model, justified decisions (with the discarded alternative) and test strategy. State which RF each part covers."|
|Tasks|"Split the plan into tasks of <30 min, ordered by dependency, each one with its RFs and a verifiable 'Done when:' line. With checkboxes."|
|Implementation|"Implement ONLY task Tn. Tests first. Run the suite and show me the result. Mark Tn as done and STOP."|
|Validation|"Walk through the spec RF (Functional Requirement) by RF: which test covers each one and its result. Final verdict: is the spec fulfilled?"|
|Change|"New requirement: <X>. Do NOT touch code: update the spec first and show me the diff."|
