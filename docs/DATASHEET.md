# Datasheet

Format follows *Datasheets for Datasets* (Gebru et al., 2021), shortened for a small benchmark.

## Motivation

**For what purpose was the dataset created?**
As a public work sample of browsing-task evaluation: preseeded tasks reviewed, proven, fenced, redesigned, and tested against models, in the open.

**Who created it?**
One evaluator, Muhammad Rizky Syahfie, working in Batam, Indonesia. How each task originated is recorded in [PROVENANCE.md](PROVENANCE.md).

## Composition

**What do the instances represent?**
Each instance is one preseeded browsing task worked through the evaluation pipeline: the preseed as received, the enumeration recipe, the golden answer with its source evidence, the predicates and exclusion list, the final question, raw outputs from the models tested, rubric scores, a failure classification, and a final disposition.

**How many instances are there?**
The set grows one task at a time as preseeds clear the pipeline. The intended full set is 20 to 30 tasks.

**Is there a label or target associated with each instance?**
Yes: the golden (reference) answer, in the task's Step 2 file, with its final question form in Step 4.

**Does the dataset contain data that might be considered confidential?**
No. Every preseed is synthetic and newly generated for this repository. No task reproduces material from any platform, client, or private project. No question or answer from the BrowseComp dataset is reproduced; that dataset is encrypted by its authors and its published examples are not republished here, at the authors' request.

## Collection process

**How was the data acquired?**
By the pipeline described in [METHOD.md](METHOD.md). Preseeds are generated from public topics, then verified against published sources, which are cited in each task file. No answer in the set is based on live data; answers are pinned to properties inside the data, to permanent editions, or to archived snapshots, per the pinning hierarchy in METHOD.md.

**Over what timeframe?**
The set was started in November 2026 and grows incrementally.

## Preprocessing and labelling

Raw model outputs are kept unedited in each task's Step 5 file and `evidence/` folder, including errors. Scores and failure classifications were assigned by the evaluator. Model name, version, and run date are recorded per output, since both answers and difficulty expire as models change.

## Uses

**What tasks has the dataset been used for?**
Evaluating browsing agents, and demonstrating an evaluator's review, proof, fencing, redesign, and adjudication workflow.

**Is there anything about the composition or collection that might impact future uses?**
Yes, three things. First, one person is evaluator and scorer of these tasks, so the scores carry no independent verification beyond the published evidence and exclusion lists, which any reader can re-check. Second, the set is small, so results are reported as raw counts, not percentages. Third, topics reflect the author's region and interests, so the set is not a representative sample of browsing questions in general.

## Distribution

Published in this GitHub repository under CC BY 4.0 (task texts and documentation).

## Maintenance

The evaluator maintains this repository. Corrections are made in place, with the change recorded in the affected task file. A task found to have a second valid answer returns to redesign, or its preseed is rejected, with the reason kept on record.
