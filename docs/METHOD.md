# Method

This repository mirrors, in the open, the evaluation pipeline used for verifiable browsing tasks: preseeded tasks, reviewed and proven by an evaluator until they either become golden sets or are rejected as unfit. The steps below follow the structure of the Apricot VBT expert guidelines (enumeration, proof, fencing, question writing, model testing), restated here in general terms.

## Before Step 1: the quick check

Every preseed gets a viability check inside the first 30 minutes, before any deep work:

- All pages on the route load; no login, paywall, or CAPTCHA anywhere the work must go.
- The main dataset is a normal rich-text website, English as its primary language, with links to databases, lists, or archives, and not on the domain blocklist.
- All pre-filled fields are present and functional, and the predicates are aligned with the prompt.
- **Pinning is checked here, not at the end.** The answer must be pinnable (see Pinning below). If it cannot be pinned, the preseed is discarded at this point and the time is not spent.

## Step 1 — Find the hidden list

The enumeration section of the task. Six fields are checked and corrected: **anchor set** (how the answer's components relate), **size**, **domain**, **modality** (text, image, or PDF, according to where the critical evidence lives), **link** (the enumeration's starting point), and the **recipe**.

The recipe is a repeatable, ordered funnel from the starting link to the golden answer. The standard it must meet is the two-strangers test: two independent reviewers following the recipe derive exactly the same list.

## Step 2 — Build and prove the answer

The golden answer, item by item, each with its proof:

- The cited URL is the record's own page, the page that displays the fact. Never a search form, a filter page, or a position in a paginated list.
- Where a page reveals nothing until a term is typed, the citation carries the generic URL, the exact search term, and a screenshot of the filtered result.
- Where the answer lives in a downloadable file, both the file link and its landing page are cited; the landing page proves provenance, the file makes the recipe executable.
- Archived snapshots (Wayback Machine) are mandatory for any source that can change, captured at the time the answer is derived, and each archive link is opened and checked.
- Screenshots: at least one per website used, named for the task and answer they prove, showing the fact with enough context to relocate it. Where a screenshot cannot show why it proves the answer, a screenshot rationale states where the property is verified and how a reviewer reproduces the verification.
- Every attribute used in the answer or in a predicate must be supported by this evidence.
- Spelling variants and diacritic alternatives are recorded as acceptable variants.

## Step 3 — Fence off the answer

Three sections:

- **Predicates.** Rubric-like requirements any answer must adhere to, specifying what belongs in the answer and what does not. Each predicate carries a paired **"does not count"** clause.
- **Exclusions.** The near misses: data points that resemble the answer and were disqualified, each by a named predicate. This list corresponds to the final round of exclusions in the enumeration funnel, and may include points excluded at any funnel step.
- **Search log.** 3–5 ordinary search-engine queries, checked by hand, confirming the golden answer is unique and does not appear from plain searching.

Derivation notes sit with this step: how the golden answer was derived from the funnel, and where judgement was exercised.

## Step 4 — Write the question

The prompt is designed here, not inherited. It must be clear, timeless, natural (a request a real person would make, not a puzzle), and admit exactly one possible answer. This step also fixes:

- the **"as of"** pinning for the prompt,
- the **answer template**, including date formats and every required field,
- the **golden-answer variables** the template defines,
- the **realism note** ("reads like ..."), stating whose request this plausibly is and why.

Adding a requirement at this step sends the work back through Steps 1–3 for re-checking.

## Step 5 — Test against models

Three models attempt the prompt in two modes: a browsing run and a closed-book run. **All three must fail both.** Each failure is read for false positives; a model that produced the right string for the wrong reason is marked and explained, not silently counted.

If a model passes either mode, the prompt returns to Step 4 for redesign: narrow the window, add a condition, or change the data source. Workarounds are attempted while a redesign can still hold. If repeated redesigns still let a model through, the evaluator **rejects the preseed**: the preseed is declared unfit, with the passing runs and the attempted redesigns kept as the record. Time already spent on the preseed does not argue against rejecting it.

## Step 6 — Submit for review

A task that clears Step 5 is submitted for QA review. QA review is a separate gate with a separate meaning: a QA rejection states that the evaluator's work was wrong, and it is recorded as such. It is never the same event as the evaluator's rejection of a preseed in Step 5.

## Pinning

Answers must be time-invariant. The pinning hierarchy, in order:

1. A property inside the data itself.
2. A permanent edition.
3. An "as of" date, with an archived snapshot.

**No answer is based on live data.** A live page is what it happens to show today; "current" is a subjective claim, not a verifiable one. Leaderboards, rankings, statistics tables, and similar volatile sources are evidence only through their archived snapshots, and a prompt that can only be answered from a live page is redesigned or the preseed is rejected.

## The standing principle

Hard to answer, easy to verify. Difficulty must come from composition across sources, never from a single fact a model might simply know, and never from ambiguity: ambiguity produces second answers, and a second valid answer kills the task.
