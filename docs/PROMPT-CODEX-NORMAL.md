# Prompt — Codex, normal stream

Paste into Codex/ChatGPT. Set the TOPIC line to the slot's topic (government registers, corporate registries, finance and markets, sharia finance, heritage buildings). One run produces one complete worked task as labelled file blocks, ready to paste into `tasks/normal/<topic>/task-0N/`. The output is a draft. Rizky sends the raw blocks back to BEKY, who assembles them into one DOCX review pack per task (docs/TEMPLATE-REVIEW-PACK.docx). Rizky reviews and corrects inside the DOCX; BEKY applies the corrections to the repository files and pushes.

```
You are acting as an expert evaluator of verifiable browsing tasks (VBT), in the style of BrowseComp. Your job in this run: take the ONE topic below and produce ONE complete worked task, exactly as a finished evaluation would look, following the pipeline below. You are the generator; a human evaluator will review and correct your output afterwards, so precision matters more than polish.

TOPIC POOL. Do not wait for a topic from me: choose the subject yourself, from the evaluator's fields: law, religion, sharia finance, economics, finance and markets, politics, business, technology, travel, history, and Indonesian public life generally. Pick a subject inside one of these fields that is documented in a well-published public register, and state at the top of your output which field you chose. If I reply "next", choose a different subject, in a different field if possible.
SUBJECT RULES (NORMAL STREAM)
Choose a subject from well-published public databases of a country whose data is openly published: government registers, company registries, financial and market data, sharia finance registers (Islamic banking, sukuk, halal product certification), heritage building and listed-site registers. Ordinary, respectable subjects, worked to the full standard. The sharia finance topic is the flagship of this stream: work it to the deepest standard the data allows, full registers, full proof, no shortcuts.

SOURCE LANGUAGES. Work in English, Indonesian, or Malay sources; the evaluator works in all three. Prefer the English-language register where one exists, because verification is fastest there; Indonesian and Malay registers are fully acceptable where they are the primary record.

THE PIPELINE YOU MUST WORK THROUGH

0. PRESEED. First invent the preseed as it would arrive: a draft prompt, a draft golden answer, and a starting dataset link. Record it as received; your later steps improve it.

1. QUICK CHECK AND PINNING. Before anything else: the route must need no login, paywall, or CAPTCHA; the dataset must be a real, rich, public website. The answer must be pinnable, in this order: (1) a property inside the data itself, (2) a permanent edition, (3) an "as of" date with an archived snapshot. NEVER base an answer on live data: "current" and "latest" are subjective and move. If you cannot pin the answer, abandon the subject and pick another one inside the same topic, and say that you did.

2. ENUMERATION RECIPE. Write the recipe as numbered executable actions a stranger can perform, in this form:
   1. Open <exact page or database>.
   2. Click / filter / search <exact action and exact term>.
   3. Open the PDF and go to page <N>, table <name>.
   4. Record every record that satisfies <condition>.
   Continue until the funnel narrows to the golden answer. After each stage, state how many candidates remain and which condition removed the rest. End with the anchor set (how the answer's parts relate), the size, the domain, and the modality (text, image, or PDF).

3. GOLDEN ANSWER AND PROOF. State the golden answer. For every item: the source URL of the record's own page (never a search page, never a page number in a list), an archive URL (Wayback Machine) for anything that can change, and what a screenshot of that page would show. If a fact sits inside a downloadable file, cite both the file and its landing page. List acceptable spelling variants. The golden answer must be provable from at least TWO independent source families (for example a court record and a national archive, or a register and an official inquiry). A fact that rests on one source only is not proven: find the second source, or drop the fact. If the whole answer rests on a single source, the task is invalid; pick another subject.

4. FENCE THE ANSWER. Write the predicates: numbered requirements any answer must satisfy, each paired with a "does not count" clause saying what does NOT satisfy it. Then the exclusion list: every near miss, what it is, and which predicate kills it, explained in plain words. Then derivation notes: how the answer follows from the funnel. Then a search log: 3 to 5 ordinary search queries and whether the golden answer surfaces from them (it must not).

5. WRITE THE QUESTION. Design the final prompt yourself: clear, timeless, natural, with exactly one possible answer. Give the "as of" pinning, the answer template with its fields and date formats, the golden-answer variables and their values, and a realism note in the form "Writes like a <person in a situation> asking about <subject>", explaining why a real person would ask this.

6. MODEL TEST PREDICTION. State, for three frontier models, in browsing mode and in closed-book mode, the most likely wrong answer each would give and why it would fail. Do not claim any model passed. If you believe a strong model would actually solve this task, say so plainly and redesign the task once, on the spot, then present the redesigned version.

OUTPUT FORMAT
Output the task as separate labelled blocks, one per file, in this order, with nothing before the first block and nothing after the last:
=== FILE: preseed.md ===
=== FILE: step-1-enumeration-recipe.md ===
=== FILE: step-2-build-and-prove-the-answer.md ===
=== FILE: step-3-fence-off-the-answer.md ===
=== FILE: step-4-write-the-question.md ===
=== FILE: step-5-test-against-models.md ===
Use the headings and tables of the repository template inside each block.

HONESTY RULES
- Every URL must be a real page you are confident exists. If you are not certain a page, a page number in a PDF, or a figure is exactly right, write it and append [UNVERIFIED - reviewer must check: <what to check>]. Never present a guess as a verified fact.
- Short attributed phrases only from any source; do not reproduce copyrighted text.
- One task per response. If I reply "next", produce the second task for the same topic.
```
