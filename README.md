# 🤖 Enterprise Multi-Agent RAG Chatbot System

[![Python](https://img.shields.io/badge/Python-3.10%2B-blue.svg)](https://www.python.org/)
[![LangChain](https://img.shields.io/badge/LangChain-Latest-green.svg)](https://www.langchain.com/)
[![Qdrant](https://img.shields.io/badge/Qdrant-VectorDB-red.svg)](https://qdrant.tech/)
[![Streamlit](https://img.shields.io/badge/Streamlit-1.30%2B-FF4B4B.svg)](https://streamlit.io/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

An enterprise-grade **Retrieval-Augmented Generation (RAG) & Multi-Agent AI System** featuring automated document ingestion, **Qdrant Vector Database**, **FlashRank Neural Reranking**, **NeMo Guardrails**, LLM Gateway management, and an interactive **Streamlit** Web Interface.

This platform supports processing multi-format enterprise documents (PDF, DOCX, PPTX, HTML, TXT), hybrid retrieval scoring, guardrail validation, automated evaluation metrics, and containerized Docker deployment.

---

## 🌟 Key Capabilities

- **📄 Multi-Format Document Ingestion Engine**: Automated parsing and chunking for PDFs, Word documents (`.docx`), PowerPoint presentations (`.pptx`), HTML pages, and raw text files.
- **🔍 Qdrant Vector Search & FlashRank Reranking**: High-performance semantic vector similarity search combined with FlashRank neural re-ranking for ultra-precise context retrieval.
- **🛡️ Guardrails & LLM Gateway**: NeMo Guardrails integration (`colang_rules.py`, `rails.py`) for toxicity filtering, prompt injection prevention, and enterprise policy enforcement.
- **🤖 Multi-Agent Graph Architecture**: Modular LangGraph orchestration featuring Planner, Retriever, and Responder agent nodes (`app/agents/graph.py`).
- **📊 Automated Evals Pipeline**: Evaluates retrieval accuracy, answer relevancy, and safety guardrails using synthetic/golden datasets (`evals/golden_dataset.json`).
- **🎨 Interactive Streamlit UI & Dockerization**: Beautiful web UI for interactive chat, document upload, and evaluation visualization. Fully containerized with `Dockerfile`.

---

## 🏗️ System Architecture

```
 ┌────────────────┐      Query      ┌────────────────────────┐      Vector Search      ┌─────────────────┐
 │                │ ──────────────> │ Streamlit / Gateway    │ ──────────────────────> │ Qdrant Vector   │
 │ Streamlit UI   │                 │ (App / Main Entry)     │                         │ Database        │
 └────────────────┘ <────────────── └───────────┬────────────┘ <────────────────────── └─────────────────┘
                                                │
                                                ▼
                                    ┌────────────────────────┐
                                    │ LangGraph Agent Engine │
                                    │ (Planner ➔ Retriever   │
                                    │  ➔ Responder Node)     │
                                    └───────────┬────────────┘
                                                │
                                                ▼
                                    ┌────────────────────────┐
                                    │ FlashRank Neural       │
                                    │ Reranker & Guardrails  │
                                    └───────────┬────────────┘
```

---

## 📁 Repository Structure

```
RAG-based-Chatbot/
├── app/
│   ├── main.py                    # Core FastAPI / Application Entrypoint
│   ├── config.py                  # Environment & vector store settings
│   ├── agents/                    # LangGraph multi-agent nodes (Planner, Retriever, Responder)
│   ├── gateway/                   # LLM API Gateway client & load balancer
│   ├── guardrails/                # Safety rules & NeMo Guardrails integration
│   ├── ingestion/                 # Document loaders (PDF, DOCX, PPTX, HTML) & text splitters
│   └── services/                  # Embedding generation, Qdrant service & FlashRank reranker
├── DOCS/                          # In-depth architectural guides (Overview, Ingestion, Evals, etc.)
├── evals/                         # Automated RAG evaluation pipeline & golden datasets
├── notebooks/                     # Jupyter notebooks (Guardrails, Gateway, Evals)
├── processed_data/                # Output JSON embeddings & structured chunks
├── ui/                            # Streamlit web application interface (`app.py`, `st_cloud_ui.py`)
├── DATA/                          # Sample dataset repository (Noisy & True documents)
├── Dockerfile                     # Docker container configuration
└── requirements.txt               # Dependencies
```

---

## 🚀 Quick Start & Setup

### Prerequisites

- Python 3.10+
- Docker (optional for containerized setup)
- Qdrant Vector Database instance (local or Cloud)

### 1. Clone the Repository

```bash
git clone https://github.com/Slack-Hacker/RAG-based-Chatbot.git
cd RAG-based-Chatbot
```

### 2. Install Dependencies

```bash
python -m venv venv
# On Windows:
venv\Scripts\activate
# On Linux/macOS:
source venv/bin/activate

pip install -r requirements.txt
```

### 3. Environment Configuration

Copy `.env.example` to `.env` and fill in your credentials:

```env
QDRANT_URL=http://localhost:6333
QDRANT_API_KEY=your_qdrant_api_key
OPENAI_API_KEY=your_openai_api_key
```

### 4. Run the Streamlit Application

```bash
streamlit run ui/app.py
```

Open your browser to **`http://localhost:8501`** to interact with the RAG Chatbot.

---

## 📜 License

Distributed under the MIT License. See `LICENSE` for details.
