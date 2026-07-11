# LLM Zoomcamp 2026

Repository documenting my journey through **LLM Zoomcamp 2026**, where I explore the concepts, tools, and engineering practices required to build modern AI applications powered by Large Language Models (LLMs).

This repository contains hands-on exercises, experiments, notebooks, and projects completed throughout the course. The objective is not only to understand the theory behind LLMs and AI systems, but also to gain practical experience by building and experimenting with them.

---

## Objectives

Through this course, I aim to:

* Understand the fundamentals of Large Language Models (LLMs).
* Learn how Retrieval-Augmented Generation (RAG) systems are designed and implemented.
* Explore Agentic AI and tool-using systems.
* Build practical AI applications through hands-on projects.
* Develop AI Engineering skills and best practices.
* Create a public portfolio showcasing my learning journey and implementations.

---

## Course Progress

| Module   | Status      | Topics                                                         |
| -------- | ----------- | -------------------------------------------------------------- |
| Module 1 | ✅ Completed | RAG, Chunking, Persistent RAG, Agents, Agentic RAG, Frameworks |
| Module 2 | ✅ Completed | Embeddings, Semantic Search, Vector Search, SQLite, PGVector   |
| Module 3 | ✅ Completed   | Workflow Orchestration with Kestra                             |
| Module 4 | ✅ Completed   | Ground Truth Generation, Search / RAG / Agent Evaluation       |
| Module 5 | ⏳ In Progress   | Monitoring                                                   |

---

## Repository Structure

```text
llm-zoomcamp-2026/
│
├── README.md
│
├── module-1/
├── module-2/
├── module-3/
├── module-4/
└── module-5/
```

Each module folder contains:

* Notes and learning summaries
* Jupyter notebooks
* Experiments and implementations
* Supporting scripts, Docker/config files, and utilities
* Module-specific documentation

---

## Completed Work

### Module 1 – Retrieval-Augmented Generation (RAG)

Module 1 introduced the foundations of modern LLM-powered applications and focused on building systems capable of retrieving and utilizing external information.

#### Topics Covered

* Large Language Models (LLMs)
* Retrieval-Augmented Generation (RAG)
* Chunking Strategies
* Persistent RAG Systems
* Agents
* Agentic RAG
* Use of Frameworks and Orchestration

#### Key Learnings

* Learned how RAG improves LLM responses by providing relevant external context.
* Understood the importance of chunking and its impact on retrieval quality.
* Built persistent RAG workflows with separate ingestion and retrieval stages.
* Explored how agents can reason, make decisions, and use tools.
* Learned how Agentic RAG combines retrieval with autonomous agent workflows.
* Developed an understanding of AI frameworks such as LangChain, LangGraph, CrewAI, and AutoGen.

#### Most Valuable Insight

One of the most important takeaways from this module was understanding the purpose of AI frameworks.

> Frameworks do not provide intelligence. The LLM acts as the brain of the system, while frameworks act as orchestrators that coordinate agents, tools, memory, and workflows. For simple systems manual orchestration is possible, but frameworks become increasingly valuable as complexity grows.

📁 Detailed notes, notebooks, and implementations can be found in the `module-1` directory.

---

### Module 2 – Vector Search

Module 2 focused on the retrieval layer that powers modern Retrieval-Augmented Generation (RAG) systems. The emphasis was on understanding how textual information can be transformed into vector embeddings and efficiently retrieved using semantic similarity.

#### Topics Covered

* Embeddings
* Semantic Search
* Vector Similarity Search
* Minsearch
* SQLite-based Persistent Vector Search
* PostgreSQL + PGVector
* Chunking Strategies
* Production Retrieval Architectures

#### Key Learnings

- Learned how embedding models convert text into dense vector representations.
- Used the all-MiniLM-L6-v2 Sentence Transformer model to generate semantic embeddings.
- Built semantic search systems capable of retrieving information based on meaning rather than exact keyword matches.
- Compared in-memory vector search with persistent vector storage approaches.
- Implemented vector search using SQLite for persistence and experimentation.
- Explored PostgreSQL with PGVector as a production-oriented vector database solution.
- Understood how chunking strategies influence retrieval quality.
- Learned the distinction between retrieval quality and infrastructure scalability.

#### Technologies Explored

- Sentence Transformers
- all-MiniLM-L6-v2 Embedding Model
- Minsearch
- SQLite
- PostgreSQL
- PGVector
- Docker
- NumPy

#### Most Valuable Insight

One of the most important takeaways from this module was understanding that vector databases do not inherently improve retrieval quality.

> Retrieval quality is primarily determined by the quality of embeddings, chunking strategies, and retrieval techniques. Vector databases such as PGVector primarily provide persistence, scalability, concurrency, and production-ready infrastructure rather than improved semantic understanding.

#### Implementations

Throughout this module, I implemented:

* Semantic search using vector embeddings
* Persistent vector storage using SQLite
* Vector retrieval with PostgreSQL and PGVector
* Document ingestion pipelines
* Retrieval helper utilities
* Retrieval-Augmented Generation (RAG) components

📁 Detailed notes, notebooks, and implementations can be found in the `module-2` directory.

---

### Module 3 – Workflow Orchestration with Kestra

Module 3 introduces workflow orchestration using [Kestra](https://kestra.io/), moving away from manually executed notebooks and scripts toward automated, observable pipelines.

#### Topics Covered

* Workflow Orchestration Concepts
* Kestra Setup with Docker Compose
* Secrets Management for Orchestrated Workflows
* Kestra's Built-in AI Assistant

#### Key Learnings

* Understood why production AI systems need orchestration rather than manually run scripts.
* Set up Kestra locally alongside a dedicated PostgreSQL backend using Docker Compose.
* Learned how to manage API keys and secrets (Gemini, Tavily, OpenAI) securely within an orchestrated environment instead of hardcoding them into flows.

#### Status

This module is currently at the infrastructure stage — Kestra is running locally, but flow definitions that automate ingestion, embedding, and evaluation from Modules 1, 2, and 4 have not been added yet.

📁 Detailed notes and setup can be found in the `module-3` directory.

---

### Module 4 – Evaluation

Module 4 focused on evaluation: building a ground-truth dataset and using it to systematically score retrieval quality, generated answers, and agent behavior, instead of judging pipeline quality by eye. Monitoring is intentionally out of scope here and left for a later stage.

#### Topics Covered

* Synthetic Ground Truth Generation
* Search / Retrieval Evaluation (Hit Rate, MRR)
* Search Boosting Parameter Tuning
* RAG Answer Evaluation (LLM-as-a-Judge)
* Agentic Evaluation (Answer Quality + Tool-Use Trajectory)
* Token Usage and Cost Tracking

#### Key Learnings

* Generated a synthetic ground-truth question set by prompting an LLM to emulate a student, using structured outputs.
* Learned to evaluate retrieval using Hit Rate (is the right document found at all?) and MRR (how high does it rank?).
* Grid-searched field boosting weights against MRR instead of tuning search relevance by hand.
* Used an LLM-as-a-judge approach to score RAG-generated answers against the original FAQ answers.
* Extended evaluation to a tool-calling agent, scoring both its final answer and whether its tool-use trajectory made sense.
* Tracked token usage and cost across large batches of parallel LLM evaluation calls.

#### Most Valuable Insight

One of the most important takeaways from this module was that evaluating an agent requires looking past the final answer.

> A correct final answer reached through a nonsensical or wasteful tool-use trajectory is still a problem worth catching. Evaluation needs to score the answer and the path taken to get there.

📁 Detailed notes, notebooks, and implementations can be found in the `module-4` directory.

---

## Learning Journey

Current understanding developed through Modules 1–4:

```text
LLMs
  ↓
RAG
  ↓
Chunking
  ↓
Embeddings
  ↓
Vector Search
  ↓
Persistent Vector Storage
  ↓
PGVector
  ↓
Agents
  ↓
Agentic RAG
  ↓
Frameworks & Orchestration
  ↓
Workflow Orchestration (Kestra)
  ↓
Ground Truth Generation
  ↓
Search / RAG / Agent Evaluation
```

This journey has helped me understand how modern AI systems move from raw documents to production-ready retrieval pipelines, and from there to pipelines that are both automated and measurably evaluated.

---

## What's Next?

The next stage of the Zoomcamp focuses on finishing **Workflow Orchestration with Kestra** and moving from evaluation toward **monitoring**.

Key areas I expect to explore include:

* Defining actual Kestra flows for ingestion, embedding, and evaluation
* Scheduled, automated data ingestion
* Wiring the Module 4 evaluation notebooks into orchestrated pipelines
* Moving from one-off evaluation runs to ongoing monitoring of answer quality, cost, and latency
* Building reproducible and maintainable AI systems

A major goal remains moving from manually executed notebooks and scripts toward automated, production-oriented AI pipelines.

---

## Future Modules

Future modules will continue building upon the foundations established in Modules 1–4. Topics, projects, and implementations will be added as they are completed throughout the course.

Planned areas include:

* Workflow Orchestration (continued)
* Monitoring
* Agentic Systems
* Production AI Engineering Practices
* End-to-End AI Applications

---

## Why This Repository Exists

This repository serves as:

* A record of my learning journey through LLM Zoomcamp 2026.
* A collection of hands-on AI Engineering projects and experiments.
* A reference for concepts explored throughout the course.
* A portfolio demonstrating practical experience with modern LLM-based systems.

---

## About Me

I am a Computer Science student with interests in AI/ML, Software Engineering, and Large Language Model applications.

This repository documents my progress as I continue building practical skills through project-based learning, experimentation, and hands-on implementation of modern AI systems.
