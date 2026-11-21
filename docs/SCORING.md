# Scoring

## Rubric

Each model output is scored on the Exact Answer only, then diagnosed on four dimensions.

| Dimension | Pass condition |
|---|---|
| Answer correctness | Exact Answer is semantically equivalent to the golden answer |
| Evidence quality | The explanation cites sources that actually support the answer |
| Constraint coverage | The explanation accounts for every constraint in the question, not only the easiest ones |
| Calibration | Stated confidence is in line with whether the answer is right |

Answer correctness decides pass or fail. The other three dimensions explain the result.

## Failure taxonomy

When an output fails, it is classified into exactly one primary type:

1. **No answer** — the model gives up, or produces no Exact Answer.
2. **Wrong entity** — the model settles on a near-miss answer, usually one listed in the task's exclusion list.
3. **Constraint drop** — the model satisfies most constraints and silently ignores the one that would have ruled its answer out.
4. **Fabricated evidence** — the model cites a source, date, or fact that does not exist or does not say what is claimed.
5. **Premature stop** — the model finds a plausible candidate early and stops searching before testing it against all constraints.
6. **Format failure** — the answer may be present in the explanation but is not committed to in the Exact Answer field.

## Disposition

Dispositions are assigned by the evaluator at Step 5, and they are verdicts on the preseed:

- **Golden** — all three models failed both the browsing and the closed-book runs on the final prompt, no false positives among the failures, and no second valid answer was found. The task proceeds to submission for QA review.
- **Redesign** — a model passed a run, a second valid answer surfaced, or a predicate proved ambiguous. The task returns to Step 4 (or earlier), the change and its reason are recorded in the redesign loop, and the task is re-tested.
- **Preseed rejected** — after redesign attempts, a model still passes, or the answer cannot be pinned or narrowed to one valid answer. The evaluator declares the preseed unfit and keeps it in the repository with its passing runs and attempted redesigns as the record.

A QA rejection after submission is a different event with a different meaning: it states the evaluator's submitted work was wrong. It is recorded as a QA outcome, never as a disposition above.
