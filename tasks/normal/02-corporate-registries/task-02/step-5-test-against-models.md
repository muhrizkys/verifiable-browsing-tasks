# Step 5 — Test against models

Three models attempt the final prompt, each in two modes: browsing (open web) and closed-book (from memory / sample search). **All three models must fail both modes** before the task can be submitted.

| Model | Browsing run | Closed-book run | Failure checked for false positive? |
|---|---|---|---|
| <model 1> | Fail | Fail | Yes — reasoning read, no false positive |
| <model 2> | Fail | Fail | Yes |
| <model 3> | Fail | Fail | Yes |

Run logs are kept in `evidence/`. A "browsing: client harness" response counts as a fail.

## Redesign loop

If any model passes either mode, the prompt goes back for redesign (narrow the window, add a condition, change the data source) and is re-tested. Record every round:

| Round | What changed | Result |
|---|---|---|
| 1 | <...> | <...> |

Workarounds are attempted while a fix is still possible. Hours spent do not rescue a preseed.

## Disposition

- **Golden** — all models failed both modes after the final design. The task proceeds to submission for QA review.
- **Preseed rejected by evaluator** — a model kept solving it in either mode and no redesign fixed it. The evaluator declares the preseed unfit, with the passing run and the attempted redesigns recorded above as the evidence. This verdict is on the preseed. It is not a QA rejection of the evaluator's work; QA review happens after submission and is a separate gate.
