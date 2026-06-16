# Module 2: Vector Search and Vector databases

This folder contains my work and exercises completed as part of LLM Zoomcamp 2026 - Module 2.

This module explores the retrieval layer of Retrieval-Augmented Generation (RAG) systems through semantic search, vector databases, and production-oriented retrieval architectures.

The goal of this module is to understand how Large Language Models can retrieve relevant information from a knowledge base by converting text into vector embeddings and performing similarity search.

---

## Learning Objectives

By completing this module, I learned how to:

* Generate embeddings for textual data
* Build semantic search systems using vector representations
* Compare traditional keyword search with vector search
* Store and retrieve embeddings efficiently
* Implement persistent vector search using SQLite
* Use PostgreSQL with PGVector for production-ready retrieval systems
* Understand chunking strategies and their impact on retrieval quality
* Build the retrieval component of a RAG pipeline

---

## Topics Covered

### Embeddings

Embeddings convert text into dense numerical vectors that capture semantic meaning.

Instead of searching for exact keywords, vector search allows retrieval based on similarity in meaning.

Example:

Query:

```text
How do I reset my password?
```

Retrieved document:

```text
Instructions for changing account credentials
```

Even without matching keywords, semantic similarity can identify relevant content.

---

### Semantic Search

Semantic search works by:

1. Converting documents into embeddings
2. Converting user queries into embeddings
3. Comparing vectors using similarity metrics
4. Returning the most relevant results

This enables retrieval based on intent and meaning rather than exact text matches.

---

### Minsearch

Minsearch was used as an introductory vector search engine.

Characteristics:

* In-memory storage
* Exact cosine similarity search
* Lightweight setup
* Ideal for experimentation and learning

Limitations:

* Embeddings are lost when the session ends
* Embeddings must be regenerated after restart
* Not suitable for production workloads

---

### Persistent Vector Search with SQLite

SQLite provides a lightweight persistence layer for embeddings.

Benefits:

* Embeddings are stored on disk
* Faster startup times
* No need to recompute embeddings after every restart
* Suitable for personal projects and small applications

---

### PGVector

PGVector extends PostgreSQL with vector search capabilities.

Advantages:

* Persistent vector storage
* Concurrent reads and writes
* Transaction support
* Better scalability
* Integration with existing PostgreSQL applications
* Production-ready architecture

This module introduced the concept of separating:

```text
Ingestion Pipeline
        ↓
Generate Embeddings
        ↓
Store in Database

Application
        ↓
Load Existing Index
        ↓
Search
        ↓
Generate Response
```

This approach avoids regenerating embeddings whenever the application starts.

---

### Chunking Strategies

Chunking is a critical step in RAG systems.

Documents are divided into smaller pieces before generating embeddings.

Strategies explored:

* Fixed-size chunking
* Overlapping chunks
* Recursive chunking
* Parent-child chunking

Key insight:

> Retrieval quality is often influenced more by chunking strategy and embedding quality than by the choice of vector database.

---

## Project Structure

```text
module-2/
│
├── notebook.ipynb
├── ingest.py
├── rag_helper.py
├── vector_rag.py
├── vector_search_persistent.ipynb
├── vector_search_PGvector.ipynb
└── README.md
```

### File Descriptions

| File                           | Purpose                                     |
| ------------------------------ | ------------------------------------------- |
| notebook.ipynb                 | Main notebook for vector search experiments |
| ingest.py                      | Data ingestion and embedding generation     |
| rag_helper.py                  | Helper functions used across the module     |
| vector_rag.py                  | RAG implementation using vector search      |
| vector_search_persistent.ipynb | Persistent vector search using SQLite       |
| vector_search_PGvector.ipynb   | Vector search using PostgreSQL and PGVector |

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

## Running SQLite-Based Vector Search

Open:

```text
module-2/vector_search_persistent.ipynb
```

Run all cells to:

* Generate embeddings
* Store vectors in SQLite
* Perform similarity search

---

## Running PGVector

Start PostgreSQL with PGVector:

```bash
docker run -it \
    --name pgvector \
    -e POSTGRES_USER=user \
    -e POSTGRES_PASSWORD=pswd \
    -e POSTGRES_DB=faq \
    -v pgvector_data:/var/lib/postgresql/data \
    -p 5432:5432 \
    pgvector/pgvector:pg17
```

Then open:

```text
module-2/vector_search_PGvector.ipynb
```

and run the notebook to:

* Create tables
* Store embeddings
* Perform vector similarity search
* Query the knowledge base

---

## Key Takeaways

* Embeddings power semantic search.
* Retrieval quality depends heavily on chunking and embedding quality.
* Persistence prevents unnecessary embedding regeneration.
* SQLite is suitable for small projects.
* PGVector provides production-grade infrastructure for vector search.
* Vector databases improve scalability and persistence, while embeddings determine semantic understanding.

---

## Next Steps

This module focused on the retrieval layer of a RAG system by exploring embeddings, vector search, persistent storage, and production-ready retrieval using PGVector.

The next stage is to move beyond individual notebooks and scripts and begin building automated, reproducible AI workflows.

### Workflow Orchestration with Kestra

The next module introduces workflow orchestration using Kestra.

Key goals include:

* Automating data ingestion pipelines
* Scheduling recurring tasks
* Managing multi-step AI workflows
* Tracking pipeline executions
* Building reproducible data and AI processes

Instead of manually running scripts, orchestration tools allow workflows to be defined and executed automatically.

Example workflow:

```text
Load Documents
      ↓
Chunk Documents
      ↓
Generate Embeddings
      ↓
Store in Vector Database
      ↓
Evaluate Retrieval
      ↓
Deploy Application
```

### From Retrieval to Production Systems

While this module focused on creating and querying vector indexes, production systems require reliable pipelines to keep knowledge bases updated.

Workflow orchestration helps solve challenges such as:

* Processing newly added documents
* Rebuilding vector indexes
* Updating embeddings
* Running scheduled evaluations
* Monitoring system health

### Building Towards End-to-End RAG

By combining:

* Vector Search
* Embeddings
* Persistent Storage
* Workflow Orchestration

it becomes possible to build scalable Retrieval-Augmented Generation (RAG) systems that can be maintained and updated automatically.

### Key Takeaway

Module 2 answered the question:

> "How do we retrieve the right information?"

The next module focuses on:

> "How do we automate and manage the entire pipeline that keeps that information up to date?"


## References

* LLM Zoomcamp 2026 – Module 2
* PGVector Documentation
* PostgreSQL Documentation
* OpenAI Embeddings Documentation
* Retrieval-Augmented Generation (RAG)

## Course

This project is part of the LLM Zoomcamp learning program and serves as a record of concepts, experiments, and implementations completed during Module 2.
