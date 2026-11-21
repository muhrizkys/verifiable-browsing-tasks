# Provenance

## Why this repository exists

Professional browsing-task evaluation is normally performed under non-disclosure agreements, so the work itself cannot be shown to a prospective client or employer. This repository answers that problem with synthetic preseeds: newly generated tasks on public facts, worked through the same evaluation pipeline used in professional work (quick check, enumeration, proof, fencing, question writing, model testing, disposition), with nothing taken from any real project.

## Origin of each task

Every task folder begins with `preseed.md`: the pre-generated task, recorded verbatim as received. In this repository each preseed was generated for this repository, from a public topic, in the same form a preseed takes in professional work. Everything after the preseed (Steps 1–5 and the disposition) is the evaluator's own work and is labelled as such by the step files themselves.

| Task | Preseed origin | Disposition |
|---|---|---|
| — | No completed tasks yet | — |

## What is not in this repository

- No task, prompt, rubric, screenshot, or output from any platform or client project.
- No question or answer from the BrowseComp dataset or its paper.
- No model output that has been edited after the run. Outputs are kept raw in each task's `evidence/` folder; the run date and model version are stated beside each one.

## Verification

Every factual claim in a golden answer is tied to a named source in the task file. Any reader can re-run the verification: follow the Step 1 recipe, check the answer against its evidence, and check the exclusion list against its near-miss answers. Disagreements are welcome as issues on this repository.
