# Module 4: Evaluation

This folder contains my work and exercises completed as part of LLM Zoomcamp 2026 – Module 4.

This module focuses on **evaluation**: how do we know whether a RAG pipeline, a search index, or an agent is actually any good? Rather than trusting intuition, this module builds a ground-truth dataset and uses it to score retrieval quality, generated answers, and full agent trajectories.

Monitoring (tracking system behavior over time in production) is intentionally out of scope for now — this module covers evaluation only.

---

## Learning Objectives

By completing this module, I learned how to:

* Generate a synthetic ground-truth dataset for evaluation using an LLM
* Evaluate search/retrieval quality using Hit Rate and Mean Reciprocal Rank (MRR)
* Tune search boosting parameters against an evaluation metric instead of guessing
* Evaluate RAG-generated answers using an LLM-as-a-judge approach
* Evaluate a tool-calling agent on both its final answer and its tool-use trajectory
* Track token usage and cost across large batches of LLM evaluation calls

---

## Topics Covered

### Ground Truth Generation (`data-gen.ipynb`)

Since no labeled evaluation set exists for the course FAQ data, one is generated synthetically:

* An LLM (`gpt-5.4-mini`) is prompted to act as a student and generate 5 plausible questions per FAQ record, using structured outputs (Pydantic models via `responses.parse`).
* This is run across the full `llm-zoomcamp` FAQ corpus in parallel using a thread pool.
* The result — a `(question, document_id)` pair for every generated question — is saved to `data/ground_truth-new.csv` and used as the ground truth for every evaluation step below.

### Search Evaluation (`search-eval.ipynb`)

Retrieval quality is scored using two standard metrics:

* **Hit Rate** – the percentage of queries where the correct document appears anywhere in the top-k results.
* **Mean Reciprocal Rank (MRR)** – rewards the correct document appearing *higher* in the ranking, not just present.

The notebook grid-searches boosting weights across `question`, `answer`, and `section` fields to find the combination that maximizes MRR, rather than tuning boosts by hand.

### RAG Evaluation (`rag-eval.ipynb`)

Once retrieval is scored, the full RAG pipeline (search + LLM answer generation) is evaluated:

* `RAGWithUsage` (in `evaluation_utils.py`) wraps the base RAG assistant and tracks token usage/cost per call.
* Answers are generated for every ground-truth question and saved to `data/rag-answers-new.csv`.
* An **LLM-as-a-judge** then compares each generated answer against the original FAQ answer and scores it `good` / `bad` with reasoning, saved to `data/rag-evaluations-new.csv`.

### Agent Evaluation (`agent-eval.ipynb`)

The same evaluation approach is extended to a tool-calling agent (built with `toyaikit`):

* The agent is given a `search` tool over the FAQ index and instructed to search before answering.
* For each ground-truth question, the agent's final answer, full tool-call trajectory, and cost are captured (`data/agent-answers.csv`).
* A judge model scores both **answer quality** and **trajectory quality** (did the agent use the tool sensibly?), saved to `data/agent-evaluations.csv`.

### Shared Evaluation Utilities (`evaluation_utils.py`)

* `llm_structured` / `llm_structured_retry` – structured-output LLM calls with retry/backoff
* `calc_price` / `calc_total_price` – token-usage-based cost calculation
* `map_progress` – parallel execution over a list with a progress bar
* `RAGWithUsage` – RAG assistant subclass that tracks per-call token usage

---

## Project Structure

```text
module-4/
│
├── data-gen.ipynb
├── search-eval.ipynb
├── rag-eval.ipynb
├── agent-eval.ipynb
├── evaluation_utils.py
├── rag_helper.py
├── ingest.py
├── data/
│   ├── ground_truth-new.csv
│   ├── rag-answers-new.csv
│   ├── rag-evaluations-new.csv
│   ├── agent-answers.csv
│   └── agent-evaluations.csv
└── README.md
```

### File Descriptions

| File                     | Purpose                                                                |
| ------------------------ | ----------------------------------------------------------------------- |
| `data-gen.ipynb`         | Generates the synthetic ground-truth question set                      |
| `search-eval.ipynb`      | Evaluates and tunes retrieval quality (Hit Rate, MRR, boosting)        |
| `rag-eval.ipynb`         | Generates and judges full RAG answers                                  |
| `agent-eval.ipynb`       | Generates and judges tool-calling agent answers and trajectories       |
| `evaluation_utils.py`    | Shared helpers: structured LLM calls, cost tracking, parallel mapping  |
| `rag_helper.py`          | Base RAG implementation (search → prompt → answer)                     |
| `ingest.py`              | Loads and indexes the course FAQ dataset                               |
| `data/`                  | Generated ground truth, answers, and evaluation results (CSV)          |

---

## Setup Instructions

### Clone the Repository

```bash
git clone https://github.com/RudranshKadiveti/llm-zoomcamp-2026.git
cd llm-zoomcamp-2026
```

### Create Virtual Environment

Using uv:

```bash
uv venv
source .venv/bin/activate
```

### Install Dependencies

```bash
uv sync
```

---

## Environment Variables

Create a `.env` file in the project root:

```env
OPENAI_API_KEY=your_api_key_here
```

---

## Running the Evaluation Pipeline

The notebooks are designed to be run in order, since each stage depends on the CSV output of the previous one:

```text
1. data-gen.ipynb      → data/ground_truth-new.csv
2. search-eval.ipynb   → retrieval metrics (Hit Rate, MRR)
3. rag-eval.ipynb      → data/rag-answers-new.csv, data/rag-evaluations-new.csv
4. agent-eval.ipynb    → data/agent-answers.csv, data/agent-evaluations.csv
```

From `module-4/`:

```bash
jupyter notebook
```

Open and run each notebook in the order above.

---

## Key Takeaways

* You can't evaluate what you haven't measured — a ground-truth set is the foundation for every downstream evaluation.
* Hit Rate and MRR give complementary views of retrieval quality: presence vs. ranking.
* Grid-searching boost weights against MRR beats hand-tuning them.
* LLM-as-a-judge is a practical way to score open-ended generated answers at scale, provided the judge prompt is precise about what "correct" means.
* Evaluating an agent requires looking at both the final answer *and* its tool-use trajectory — a correct answer reached the wrong way is still a problem worth catching.
* Token usage and cost should be tracked from day one; evaluation runs (especially with a judge model) can add up quickly.

---

## Next Steps

This module covered evaluation of search, RAG, and agent behavior — but only as one-off, manually triggered runs.

Planned follow-ups:

* Wire these evaluation notebooks into the Kestra workflows from Module 3, so evaluation runs automatically after ingestion/index changes.
* Extend from evaluation into **monitoring**: tracking answer quality, cost, and latency over time in a running system rather than in a single offline batch.

## References

* LLM Zoomcamp 2026 – Module 4
* OpenAI Structured Outputs Documentation
* [toyaikit](https://pypi.org/project/toyaikit/)

## Course

This project is part of the LLM Zoomcamp learning program and serves as a record of concepts, experiments, and implementations completed during Module 4.
