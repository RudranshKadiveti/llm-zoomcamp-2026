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
| Module 3 | ⏳ In Progress   | Workflow Orchestration with Kestra                             |
| Module 4 | ⬜ Planned   | To be updated                                                  |
| Module 5 | ⬜ Planned   | To be updated                                                  |

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
* Supporting scripts and utilities
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

## Learning Journey

Current understanding developed through Modules 1 and 2:

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
```

This journey has helped me understand how modern AI systems move from raw documents to production-ready retrieval pipelines capable of supporting Large Language Models with external knowledge.

---

## What's Next?

The next stage of the Zoomcamp focuses on **Workflow Orchestration with Kestra**.

Key areas I expect to explore include:

* Workflow automation
* Pipeline orchestration
* Scheduled data ingestion
* Automated embedding generation
* Managing multi-step AI workflows
* Building reproducible and maintainable AI systems

A major goal will be moving from manually executed notebooks and scripts toward automated, production-oriented AI pipelines.

---

## Future Modules

Future modules will continue building upon the foundations established in Modules 1 and 2. Topics, projects, and implementations will be added as they are completed throughout the course.

Planned areas include:

* Workflow Orchestration
* Evaluation and Monitoring
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
