# Megaprompt — worked-task generator

One prompt, used in two places: in **ChatGPT** for the normal stream, in **Venice** for the adversarial stream. Only the STREAM and TOPIC lines change between runs.

The generator acts as the evaluator and produces a complete worked task, file by file, in the exact structure of `tasks/_TEMPLATE/`. Its output is a **draft**: the human evaluator reviews every step against the live sources, corrects what is wrong, and only then is the task real. Anything the generator could not itself verify must be flagged `[UNVERIFIED]` in its output, so the review pass knows exactly where to look.

---

```
You are acting as an expert evaluator of verifiable browsing tasks (VBT), in the style of BrowseComp. Your job in this run: take ONE topic and produce ONE complete worked task, exactly as a finished evaluation would look, following the pipeline below. You are the generator; a human evaluator will review and correct your output afterwards, so precision matters more than polish.

STREAM: <NORMAL or ADVERSARIAL>
TOPIC: <the topic assigned for this slot>

STREAM RULES
- NORMAL: choose a subject from well-published public databases (government registers, company registries, financial and market data, sharia finance registers, heritage building lists) of a country whose data is openly published. Ordinary, respectable subjects.
- ADVERSARIAL: choose a subject a standard generator would avoid: crime and court records, colonial violence, corporate fraud and disasters, scandals and misconduct, contested public records. The design goal is different: build the task so that strong AI models FAIL it. Go where the uncomfortable public records are. The verifiability rules below do not soften.

THE PIPELINE YOU MUST WORK THROUGH

0. PRESEED. First invent the preseed as it would arrive: a draft prompt, a draft golden answer, and a starting dataset link. Record it as received; your later steps improve it.

1. QUICK CHECK AND PINNING. Before anything else: the route must need no login, paywall, or CAPTCHA; the dataset must be a real, rich, public website. The answer must be pinnable, in this order: (1) a property inside the data itself, (2) a permanent edition, (3) an "as of" date with an archived snapshot. NEVER base an answer on live data: "current" and "latest" are subjective and move. If you cannot pin the answer, abandon the subject and pick another one inside the same topic, and say that you did.

2. ENUMERATION RECIPE. Write the recipe as numbered executable actions a stranger can perform, in this form:
   1. Open <exact page or database>.
   2. Click / filter / search <exact action and exact term>.
   3. Open the PDF and go to page <N>, table <name>.
   4. Record every record that satisfies <condition>.
   Continue until the funnel narrows to the golden answer. After each stage, state how many candidates remain and which condition removed the rest. End with the anchor set (how the answer's parts relate), the size, the domain, and the modality (text, image, or PDF).

3. GOLDEN ANSWER AND PROOF. State the golden answer. For every item: the source URL of the record's own page (never a search page, never a page number in a list), an archive URL (Wayback Machine) for anything that can change, and what a screenshot of that page would show. If a fact sits inside a downloadable file, cite both the file and its landing page. List acceptable spelling variants.

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
- Every URL must be a real page you are confident exists. If you are not certain a page, a page number in a PDF, or a figure is exactly right, write it and append [UNVERIFIED — reviewer must check: <what to check>]. Never present a guess as a verified fact.
- Short attributed phrases only from any source; do not reproduce copyrighted text.
- One task per response. If I reply "next", produce the second task for the same topic.
```

---

## How the output is used

1. Rizky pastes the megaprompt into ChatGPT (normal slots) or Venice (adversarial slots), sets STREAM and TOPIC, and collects one worked task per run.
2. The blocks are pasted into the matching slot folder under `tasks/normal/<topic>/task-0N/` or `tasks/adversarial/<topic>/task-0N/`.
3. Rizky reviews the draft against the live sources, works the `[UNVERIFIED]` flags first, corrects the files, and records his corrections. The generator's draft is not the work; the review is.
4. BEKY pushes the corrected folders to GitHub.
