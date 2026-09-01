# 🤖 Agentic RAG Based CHATBOT

[![Python](https://img.shields.io/badge/Python-3.10%2B-blue.svg)](https://www.python.org/)
[![FastAPI](https://img.shields.io/badge/FastAPI-0.100%2B-009688.svg)](https://fastapi.tiangolo.com/)
[![LangGraph](https://img.shields.io/badge/LangGraph-Agentic_AI-FF6F00.svg)](https://langchain.com/)
[![Qdrant](https://img.shields.io/badge/Qdrant-Vector_Search-D0006F.svg)](https://qdrant.tech/)
[![Redis](https://img.shields.io/badge/Redis-Semantic_Caching-DC382D.svg)](https://redis.io/)
[![Google Cloud Run](https://img.shields.io/badge/GCP-Cloud_Run-4285F4.svg)](https://cloud.google.com/run)
[![Terraform](https://img.shields.io/badge/Terraform-IaC-7B42BC.svg)](https://www.terraform.io/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

An enterprise-grade **Agentic Retrieval-Augmented Generation (RAG) System** featuring multi-agent workflow orchestration, semantic vector search, intelligent reranking, guardrails, and cloud serverless deployment.

---

## 🌟 Key Resume Highlights & Technical Accomplishments

- **🤖 Agentic AI Backend**: Built an Agentic AI backend using **Python**, **FastAPI**, and **LangGraph** implementing a multi-agent **Planner–Retriever–Responder** workflow.
- **🔍 Vector Search & Reranking**: Implemented RAG utilizing **Qdrant** vector search and **FlashRank** cross-encoder reranking for context retrieval precision.
- **🛡️ Enterprise Guardrails & Caching**: Integrated **Redis** semantic caching for ultra-low latency queries, **NeMo Guardrails** for safety/hallucination checks, and **Portkey LLM Gateway** with automatic model fallback.
- **⚡ Event-Driven Ingestion Pipeline**: Built document processing using **Google Cloud Storage (GCS)**, **Eventarc**, **Document AI**, and **Vertex AI** embedding generation.
- **📊 RAG Evaluation & Observability**: Implemented **RAGAS** evaluation suite with tool-correctness validation and full trace observability via **LangSmith** and **Pydantic Logfire**.
- **☁️ Cloud Infrastructure & Deployment**: Containerized services with **Docker** and deployed microservices on **Google Cloud Run** using **Terraform** Infrastructure-as-Code.

---

## 🏗️ Multi-Agent Architecture

```
 User Query ────────> [ NeMo Guardrails / Portkey Gateway ]
                                  │
                                  ▼
                    ┌───────────────────────────┐
                    │     LangGraph Agent       │
                    │  Planner ──> Retriever    │
                    └─────────────┬─────────────┘
                                  │
                  ┌───────────────┴───────────────┐
                  ▼                               ▼
      ┌───────────────────────┐       ┌───────────────────────┐
      │ Qdrant Vector Store   │       │ Redis Semantic Cache  │
      │ + FlashRank Reranker  │       └───────────────────────┘
      └───────────┬───────────┘
                  │
                  ▼
      ┌───────────────────────┐
      │ LangGraph Responder   │ ────────> Response + RAGAS Evals
      └───────────────────────┘
```

---

## 📁 Repository Structure

```
Agentic-RAG-Based-Chatbot/
├── app/
│   ├── agents/             # LangGraph Planner-Retriever-Responder graph & state
│   ├── gateway/            # Portkey LLM gateway integration & fallbacks
│   ├── guardrails/         # NeMo Guardrails colang security rules
│   ├── ingestion/          # PDF, Office, HTML document loaders & chunking
│   ├── services/           # Qdrant vector store & FlashRank reranking
│   └── main.py             # FastAPI REST endpoints & WebSocket server
├── evals/                  # RAGAS evaluation pipeline & golden datasets
├── DOCS/                   # Comprehensive architecture & module design guides
├── Dockerfile              # Containerization definition
└── README.md               # Project documentation
```

---

## 📜 License

Distributed under the MIT License. See `LICENSE` for details.
