# Agentic AI

A collection of hands-on Jupyter notebooks exploring LangChain-based agentic AI patterns — from basic LLM calls to RAG pipelines and tool-using agents with persistent memory.

## Projects

| Notebook | Description |
|---|---|
| [llm_calling](llm_calling/llm_call.ipynb) | Direct LLM calls via Groq (Qwen3-32b) and Google Gemini/Gemma, with temperature exploration |
| [product_query_agent](product_query_agent/product_agent.ipynb) | Tool-using agent (Llama 3.3 70B) that answers product queries using custom `@tool` functions |
| [product_agent_with_memory](product_agent_with_memory/product_agent_with_memory.ipynb) | Same agent extended with in-session memory via LangGraph `InMemorySaver` |
| [multi_model](multi_model/multi_modal.ipynb) | Multi-modal agent with medical report image analysis |
| [rag_apps](rag_apps/rag_basics.ipynb) | Full RAG pipeline: PDF → chunking → HuggingFace embeddings → ChromaDB → Groq LLM Q&A |
| [vector_db](vector_db/vector_db.ipynb) | ChromaDB fundamentals: collections, upsert, metadata filtering, similarity search |

## Tech Stack

- **LLMs** — Google Gemini 2.5 Flash / Gemma 4, Groq-hosted Llama 3.3 70B and Qwen3 32B
- **Orchestration** — LangChain, LangGraph
- **Embeddings** — `sentence-transformers/all-MiniLM-L6-v2` via HuggingFace
- **Vector store** — ChromaDB
- **Runtime** — Python 3.14+, Jupyter

## Setup

```bash
# Install dependencies (requires uv)
uv sync

# Copy and fill in API keys
cp .env.example .env
```

Required keys in `.env`:

```
GOOGLE_API_KEY=...
GROQ_API_KEY=...
```

Then launch Jupyter:

```bash
uv run jupyter notebook
```

## Code Quality

Pre-commit hooks run automatically on each commit:

```bash
# Install hooks
pre-commit install

# Run manually against all files
pre-commit run --all-files
```

Hooks: `ruff` (lint + format), `nbstripout` (strip notebook outputs), secret detection via `gitleaks`, and standard file hygiene checks.
