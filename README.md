# Verifiable Browsing Tasks

A public work sample of verifiable browsing task evaluation, in the style of BrowseComp: tasks that are hard to answer and easy to verify.

## How the work actually goes

Tasks in this line of work are not written from scratch. Each one arrives as a **preseed**: a pre-generated task, produced upstream and already screened closed-book, so any task a test model could answer from memory alone never arrives.

The evaluator's work starts where the preseed lands:

1. **Quick check.** Within the first 30 minutes: pages load, no login, paywall, or CAPTCHA on the route, the dataset is sound, and the answer's pinning holds. If the pinning fails here, the preseed is not viable and the work stops.
2. **Find the hidden list.** The enumeration recipe: anchor set, size, domain, modality, starting link, and the repeatable funnel that produces the golden answer.
3. **Build and prove the answer.** The golden answer, each item tied to the record's own page, an archived snapshot for anything that can change, screenshots, and a rationale for the evidence.
4. **Fence off the answer.** Predicates, each paired with a "does not count" clause; the exclusions those predicates generate, near miss by near miss; derivation notes; and a search log proving the answer does not surface from plain searching.
5. **Write the question.** The prompt is designed and rewritten against the fenced answer, with its "as of" pinning, its answer template and golden-answer variables, and a realism note on why it reads like a real person's request.
6. **Test against models.** Three models run the prompt with browsing and closed-book. All three must fail both modes.

If a model keeps passing, the prompt is redesigned and retested while a fix is possible. If no redesign holds, the evaluator **rejects the preseed** and records why. That rejection is a verdict on the preseed, delivered by the evaluator. It is a different event from a QA rejection of submitted work, which means the evaluator's own work was wrong; the two are never conflated here.

## Rules that hold across every task

- **No answer is based on live data.** "Current" and "latest" are subjective and move. Answers are pinned, in order of preference, to a property inside the data itself, to a permanent edition, or to an "as of" date with an archived snapshot. Never to a live page as it happens to stand today.
- **Easy to verify.** A stranger following the recipe reaches exactly the same list. Every claim in the answer is visible in the cited evidence.
- **Short attributed phrases only.** No copyrighted text is reproduced beyond them.
- **Synthetic preseeds only.** Every preseed in this repository was generated for this repository from public topics. No platform task, client material, or private project content appears here.

## Repository layout

| Path | Contents |
|---|---|
| `tasks/` | One folder per preseed, worked through the pipeline. Start from `tasks/_TEMPLATE/`, which defines the structure every task follows |
| `docs/METHOD.md` | The pipeline and its rules in full |
| `docs/SCORING.md` | How model runs are scored and how dispositions are assigned |
| `docs/DATASHEET.md` | Dataset documentation, in the Datasheets for Datasets format |
| `docs/PROVENANCE.md` | How each item in this repository is labelled by origin |
| `SCOREBOARD.md` | The task-by-model results matrix |

## Current set

No completed tasks yet. The template is final; worked tasks are added one at a time as they clear the pipeline, including any preseed the evaluator rejects, with its reasons.
