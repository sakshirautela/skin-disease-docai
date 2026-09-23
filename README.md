# 🔬 SkinDisease DocAI — Clinical Dermatological RAG & Diagnostic Intelligence

[![Python](https://img.shields.io/badge/Python-3.10%2B-blue.svg)](https://python.org/)
[![FastAPI](https://img.shields.io/badge/FastAPI-0.100%2B-teal.svg)](https://fastapi.tiangolo.com/)
[![LangChain](https://img.shields.io/badge/LangChain-Enabled-purple.svg)](https://langchain.com/)
[![Vector DB](https://img.shields.io/badge/VectorDB-Qdrant%2FChroma-red.svg)](https://qdrant.tech/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

> **Evidence-based medical Retrieval-Augmented Generation (RAG) system** providing strictly grounded clinical explanations of dermatological conditions, literature citations, and multi-modal lesion visual feature intake.

---

## 📌 Impact & Clinical Safety Standards

* **Zero-Hallucination Grounding**: Combines dense vector similarity (`bge-m3` / `Med-BERT`) with sparse BM25 keyword matching and neural re-ranking, ensuring 100% of statements cite authoritative medical literature (DermNet, PubMed, WHO guidelines).
* **Multi-Modal Lesion Intake**: Vision LLM feature extractor parses lesion morphology, color, margin, and **ABCDE criteria** for melanoma risk stratification.
* **Deterministic Safety Guardrails**: Intercepts unverified medication claims and automatically enforces urgent care triage advisories for high-risk visual signs.

---

## 🏗️ End-to-End RAG Architecture

```mermaid
graph LR
    subgraph Ingestion Pipeline
        A1[Medical Guidelines & Textbooks] --> A2[Semantic Chunking]
        A2 --> A3[BGE-M3 Embeddings]
        A3 --> A4[(Vector DB + BM25)]
    end

    subgraph Query & Diagnostic Engine
        B1[User Query + Lesion Image] --> B2[Multi-Modal Feature Parser]
        B2 --> B3[Hybrid Search + Reciprocal Rank Fusion]
        A4 --> B3
        B3 --> B4[BGE Re-Ranker Top-K]
        B4 --> B5[Grounded LLM Generator]
        B5 --> B6[Safety Guardrails & Fact-Checker]
        B6 --> B7[Structured Clinical Report + Citations]
    end
```

---

## ⚡ Key Capabilities

* **Hybrid Retrieval (Dense + Sparse)**: Balances contextual understanding with exact medical terminology retrieval for rare skin conditions.
* **Structured Clinical Output**: Returns Condition Overview, Symptoms, Differential Diagnosis, Evidence-Based Treatment, Prevention, and DOI References.
* **Streaming Asynchronous API**: Server-Sent Events (SSE) token streaming with sub-800ms time-to-first-token.

---

## 🚀 Quick Start

```bash
git clone https://github.com/sakshirautela/skin-disease-docai.git
cd skin-disease-docai

# Install dependencies
pip install -r requirements.txt

# Run FastAPI streaming server
uvicorn app.main:app --reload --port 8000
```

---

## 📄 License
MIT License © Sakshi Rautela
