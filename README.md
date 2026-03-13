# 💎 Lumina RAG Pro

![Status](https://img.shields.io/badge/status-active-success.svg)
![Python](https://img.shields.io/badge/python-3.10+-blue.svg)
![FastAPI](https://img.shields.io/badge/FastAPI-0.109.0-green.svg)
![License](https://img.shields.io/badge/license-MIT-blue.svg)

**Lumina RAG Pro** is a production-grade, modular Retrieval-Augmented Generation (RAG) system designed for enterprise knowledge management. It features hybrid search (keyword + vector), intelligent re-ranking using Cross-Encoders, and native citation support, all wrapped in a scalable FastAPI backend.

---

## 🚀 Key Features

- **Hybrid Search Architecture**: Combines semantic search (Vector DB) with keyword search (BM25) for high-precision retrieval.
- **Intelligent Re-ranking**: Uses SOTA Cross-Encoders to re-rank retrieved documents, ensuring the most relevant context reaches the LLM.
- **Native Citation Awareness**: Every generated response includes precise references to source documents and page numbers.
- **Scalable Document Ingestion**: Asynchronous pipeline for processing PDFs, TXT, and Markdown files with intelligent chunking.
- **Production Ready**: Fully dockerized with FastAPI, Pydantic type validation, and integrated observability.

## 🏗️ System Architecture

`mermaid
graph TD
    User[User/Client] -->|Query| API[FastAPI Gateway]
    API -->|1. Retrieve| HybridSearch[Hybrid Search Engine]
    HybridSearch -->|Vector| VectorDB[(ChromaDB / FAISS)]
    HybridSearch -->|Keyword| BM25[BM25 Index]
    API -->|2. Re-rank| ReRanker[Cross-Encoder Re-ranker]
    API -->|3. Generate| LLM[LLM Engine (OpenAI/Claude)]
    LLM -->|Response + Citations| API
    API -->|Display| UI[Streamlit / Web]
`

## 🛠️ Tech Stack

- **Core Framework**: Python 3.10+, FastAPI.
- **Vector Database**: ChromaDB / Pinecone.
- **Retrieval & Re-ranking**: Sentence-Transformers, LangChain.
- **Inference**: OpenAI GPT-4 / Anthropic Claude 3.
- **Infrastructure**: Docker, Kubernetes Ready.

## 📂 Project Structure

\\\
lumina-rag-pro/
├── src/
│   ├── engine/              # RAG pipeline and retrieval logic
│   ├── api/                 # FastAPI routes and schemas
│   ├── ingestion/           # Document processing and embedding
│   └── models/              # Pydantic data models
├── tests/                   # Integration and unit tests
├── Dockerfile               # Production containerization
└── requirements.txt         # Project dependencies
\\\

## 🚀 Quick Start

1. **Clone the repository**
   \\\ash
   git clone https://github.com/goelanshul22/lumina-rag-pro.git
   cd lumina-rag-pro
   \\\

2. **Install dependencies**
   \\\ash
   pip install -r requirements.txt
   \\\

3. **Run the API**
   \\\ash
   uvicorn src.api.main:app --host 0.0.0.0 --port 8000
   \\\

## 👨‍💻 Author

**Anshul Goel**
*Founding Engineer @ Garvik AI | Backend & AI Architect*
[LinkedIn](https://www.linkedin.com/in/goelanshul/)

---
*Building grounded and reliable AI systems for the enterprise.*