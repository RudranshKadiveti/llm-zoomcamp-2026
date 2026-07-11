# Module 3: Workflow Orchestration with Kestra

This folder contains my work and exercises completed as part of LLM Zoomcamp 2026 – Module 3.

This module moves away from manually run notebooks and scripts toward automated, orchestrated workflows using [Kestra](https://kestra.io/), an open-source orchestration platform.

The goal of this module is to understand how data ingestion, embedding generation, and retrieval pipelines can be automated, scheduled, and monitored instead of being triggered by hand.

---

## Learning Objectives

By completing this module, I aim to:

* Understand the role of workflow orchestration in production AI systems
* Set up Kestra locally using Docker
* Learn how Kestra flows are defined and executed
* Connect orchestration to the ingestion and retrieval components built in earlier modules
* Manage secrets and API keys securely within an orchestrated environment

---

## Topics Covered

### Why Orchestration?

Manually running notebooks and scripts works for experimentation, but production systems need:

* Repeatable, scheduled execution
* Visibility into pipeline runs and failures
* A single place to manage secrets and configuration
* The ability to chain multi-step workflows (ingest → embed → index → evaluate)

Kestra provides this layer on top of the retrieval and RAG components built in Modules 1 and 2.

### Kestra Setup

The current setup runs Kestra together with a dedicated PostgreSQL instance via Docker Compose:

* `kestra_postgres` – backing store for the Kestra repository and queue
* `kestra` – the Kestra server, running in `standalone` mode

Secrets (`GEMINI_API_KEY`, `TAVILY_API_KEY`, `OPENAI_API_KEY`) are injected as environment variables and exposed to flows as Kestra secrets, rather than being hardcoded into flow definitions.

Kestra's built-in AI assistant is also configured, using Gemini (`gemini-2.5-flash`) as the backing model.

---

## Project Structure

```text
module-3/
│
├── docker-compose.yml
└── README.md
```

### File Descriptions

| File                | Purpose                                                        |
| ------------------- | --------------------------------------------------------------- |
| `docker-compose.yml` | Spins up Kestra and its PostgreSQL backend for local development |

> This module is currently at the infrastructure stage: Kestra itself is up and running, but flow definitions (the actual orchestrated pipelines) haven't been added to this folder yet. Those will follow as the module progresses.

---

## Setup Instructions

### Clone the Repository

```bash
git clone https://github.com/RudranshKadiveti/llm-zoomcamp-2026.git
cd llm-zoomcamp-2026/module-3
```

### Environment Variables

Create a `.env` file in `module-3/` with:

```env
SECRET_GEMINI_API_KEY=your_gemini_api_key_here
SECRET_TAVILY_API_KEY=your_tavily_api_key_here
SECRET_OPENAI_API_KEY=your_openai_api_key_here
```

### Start Kestra

```bash
docker compose up -d
```

Kestra will be available at:

```text
http://localhost:8080
```

Login with the configured basic-auth credentials (`admin@kestra.io`).

---

## Key Takeaways (so far)

* Orchestration tools like Kestra separate *what* a pipeline does from *when and how* it runs.
* Secrets management is a first-class concern once workflows move out of notebooks.
* Running Kestra locally with Docker Compose is a lightweight way to prototype orchestration before deploying it in production.

---

## Next Steps

With Kestra running, the next step is to define actual flows that automate the pipeline built in earlier modules:

```text
Trigger
   ↓
Ingest FAQ Data
   ↓
Chunk + Embed Documents
   ↓
Store in Vector Database
   ↓
Run Retrieval Evaluation
   ↓
Notify / Report Results
```

This will turn the manually-run `ingest.py` scripts and notebooks from Modules 1, 2, and 4 into a scheduled, observable pipeline.

## References

* LLM Zoomcamp 2026 – Module 3
* [Kestra Documentation](https://kestra.io/docs)

## Course

This project is part of the LLM Zoomcamp learning program and serves as a record of concepts, experiments, and implementations completed during Module 3.
