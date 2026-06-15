# Module 1 -  Retrieval-Augmented Generation (RAG)

This folder contains my work and exercises completed as part of **LLM Zoomcamp 2026 - Module 1**.

## Topics Covered

* Large Language Models (LLMs)
* Prompt Engineering
* Retrieval-Augmented Generation (RAG)
* Document Retrieval Pipelines
* Persistent RAG Systems
* Agent-Based Applications

## Files

| File                          | Description                                |
| ----------------------------- | ------------------------------------------ |
| `notebook.ipynb`              | Module 1 learning notebook and experiments |
| `rag_clean.ipynb`             | Basic RAG implementation                   |
| `persistent_rag.ipynb`        | Persistent RAG workflow                    |
| `persistent_rag_ingest.ipynb` | Data ingestion pipeline for persistent RAG |
| `agents.ipynb`                | Agent-based LLM experiments                |
| `ingest.py`                   | Data ingestion script                      |
| `rag_helper.py`               | Helper functions for RAG workflows         |
| `main.py`                     | Entry point for testing and execution      |

## Technologies Used

* Python
* OpenAI API
* SQLite
* Jupyter Notebooks
* Retrieval-Augmented Generation (RAG)

## Key Takeaways and Learnings

### 1. Large Language Models (LLMs)

* Learned how LLMs generate responses based on patterns learned during training.
* Understood the role of prompts in influencing model behavior and output quality.
* Explored how LLM-powered applications differ from traditional software systems.

### 2. Retrieval-Augmented Generation (RAG)

* Learned why LLMs alone are insufficient for answering questions about external or private data.

* Understood the basic RAG workflow:

  User Query → Retrieve Relevant Information → Provide Context to LLM → Generate Response

* Built and experimented with simple RAG pipelines.

### 3. Chunking

* Learned that large documents are split into smaller chunks before retrieval.
* Understood that chunk size affects retrieval quality.
* Learned why overlapping chunks are often used to preserve context.

### 4. Persistent RAG

* Built a persistent RAG system that stores information for future retrieval.
* Learned the difference between document ingestion and querying.
* Explored how knowledge can be prepared and indexed before user interaction.

### 5. Agents

* Learned that agents are LLM-powered systems capable of reasoning and using tools.
* Understood that an agent can:

  * Analyze a task
  * Choose an action
  * Use tools when necessary
  * Return a final response

### 6. Agentic RAG

* Learned how retrieval can be integrated as one of several tools available to an agent.
* Understood that agents can decide when retrieval is necessary rather than always performing it.
* Explored the idea of tool-calling workflows.

### 7. Frameworks and Orchestration

One of the most important concepts learned during this module was the purpose of AI agent frameworks.

Key understanding:

* For small projects with a few tools and agents, manual orchestration is practical.
* As systems grow in complexity, coordinating agents, tools, memory, and workflows becomes difficult.
* Frameworks such as LangChain, LangGraph, CrewAI, and AutoGen provide an orchestration layer that manages these interactions.

Personal takeaway:

> The framework is not the intelligence of the system. The LLM is the brain, while the framework acts as a coordinator that manages communication, tool usage, memory, and workflow execution.

### 8. Personal Understanding

By the end of Module 1, my understanding is:

* LLMs provide reasoning and language capabilities.
* RAG improves responses by supplying relevant external context.
* Chunking is critical for effective retrieval.
* Agents add decision-making and tool usage.
* Agentic RAG combines retrieval with agent workflows.
* Frameworks help manage complex multi-agent and multi-tool systems through orchestration.


## Course

This project is part of the LLM Zoomcamp learning program and serves as a record of concepts, experiments, and implementations completed during Module 1.
