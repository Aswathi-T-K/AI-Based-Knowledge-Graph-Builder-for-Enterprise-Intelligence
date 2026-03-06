# AI-Based-Knowledge-Graph-Builder-for-Enterprise-Intelligence

## Project Overview

This project implements a **Graph-Enhanced Retrieval-Augmented Generation (RAG) system** designed to improve enterprise knowledge discovery.

The system integrates:

* 🔎 **Semantic Search** using Sentence Transformers
* ⚡ **High-speed Vector Retrieval** with FAISS
* 🗂 **Knowledge Graph Storage** using Neo4j
* 🚀 **API Services** built with FastAPI
* 📊 **Interactive Dashboard** powered by Streamlit

By combining **vector similarity search with graph relationships**, the system enables intelligent retrieval and produces **context-aware responses grounded in structured data**.

-----------------------------------------------------

# Objective

The goal of this milestone is to build an intelligent backend that:

* Performs **semantic search on unstructured enterprise data**
* Combines **vector retrieval with graph-based filtering**
* Implements a **graph-aware RAG pipeline**
* Minimizes **hallucinated responses**
* Prepares backend APIs for integration with an **interactive dashboard**

-----------------------------------------------------

# System Architecture

The workflow of the system is illustrated below:

```
User Query (Streamlit Interface)
        ↓
Sentence Transformer Embedding
        ↓
FAISS Vector Similarity Search
        ↓
Retrieve Relevant Entity IDs
        ↓
Neo4j Graph Query
        ↓
Combine Semantic Context + Graph Relationships
        ↓
Generate Grounded RAG Response
```

This hybrid architecture merges **semantic similarity with relational reasoning** to deliver more reliable results.

-----------------------------------------------------

# Technologies Used

| Component            | Technology           | Purpose                                       |
| -------------------- | -------------------- | --------------------------------------------- |
| Embedding Model      | SentenceTransformers | Convert text into dense semantic vectors      |
| Vector Search        | FAISS                | Fast Approximate Nearest Neighbor search      |
| Graph Database       | Neo4j                | Store and query knowledge graph relationships |
| Backend API          | FastAPI              | Provide RAG services via REST endpoints       |
| Dashboard            | Streamlit            | User interface for querying the system        |
| Programming Language | Python               | Core implementation                           |

-----------------------------------------------------

# System Workflow

## 1. Semantic Embedding

Text data such as movie descriptions and metadata are transformed into **vector embeddings** using the model:

**all-MiniLM-L6-v2**

This representation captures the **contextual meaning of sentences**, enabling similarity search even when the wording differs.

-----------------------------------------------------

## 2. Vector Storage and Retrieval (FAISS)

The generated embeddings are stored using **Facebook AI Similarity Search (FAISS)**.

FAISS enables:

* Efficient **Approximate Nearest Neighbor (ANN)** retrieval
* **Low latency similarity search**
* High-performance **vector indexing**

-----------------------------------------------------

## 3. Query Processing

When a user submits a query:

1. The query text is converted into a vector embedding.
2. FAISS retrieves the most similar vectors.
3. Corresponding **entity IDs** are identified.

These entities represent relevant knowledge stored in the dataset.

-----------------------------------------------------

## 4. Graph Filtering using Neo4j

The retrieved entity IDs are passed to the **Neo4j knowledge graph**.

Neo4j enriches the results by extracting relationships.

This step adds **structured context and relational reasoning** to the retrieval pipeline.

-----------------------------------------------------

## 5. Graph-Aware RAG Response

The final response generation combines:

* **Semantic context** retrieved from FAISS
* **Graph relationships** retrieved from Neo4j

This ensures that generated answers remain **grounded in verified knowledge**, reducing the risk of hallucinated outputs.

-----------------------------------------------------

# Why FAISS Instead of Pinecone?

For this milestone, **FAISS** was selected because:

* It runs **locally without requiring cloud infrastructure**
* It is suitable for **rapid prototyping and experimentation**
* It provides efficient **ANN vector search**

For enterprise deployment, a **managed vector database such as Pinecone** could be used.

-----------------------------------------------------

# Reducing Hallucinations

The system minimizes hallucinated outputs by restricting generation to:

* Retrieved semantic documents
* Verified relationships from the knowledge graph

This **grounded retrieval approach** ensures that responses are derived only from **existing data sources**.

-----------------------------------------------------

# Installation & Setup

## 1. Clone Repository

```bash
git clone https://github.com/yourusername/AI_Knowledge_Graph.git
cd AI_Knowledge_Graph
```

-----------------------------------------------------

## 2. Create Virtual Environment

```bash
python -m venv kg_env
kg_env\Scripts\activate
```

-----------------------------------------------------

## 3. Install Dependencies

```bash
pip install -r requirements.txt
```

-----------------------------------------------------

## 4. Start Neo4j

Ensure Neo4j is running locally at:

```
bolt://localhost:7687
```

Update database credentials in the `.env` file.

-----------------------------------------------------

## 5. Build FAISS Index

Run the dataset loading script:

```bash
python load_full_dataset.py
```

This step generates embeddings and builds the FAISS vector index.

-----------------------------------------------------

## 6. Run FastAPI Backend

```bash
uvicorn app:app --reload
```

API will be available at:

```
http://127.0.0.1:8000
```

-----------------------------------------------------

## 7. Launch Streamlit Dashboard

```bash
streamlit run streamlit_app.py
```

The interface will open at:

```
http://localhost:8501
```

-----------------------------------------------------

# Implemented Features

* Semantic similarity search
* Vector-based document retrieval
* Knowledge graph integration with Neo4j
* Hybrid RAG architecture
* Grounded response generation
* REST API integration
* Dashboard-ready backend

-----------------------------------------------------

# Future Improvements

To scale this system for enterprise applications:

* Replace **FAISS with Pinecone or Weaviate**
* Containerize services using **Docker**
* Deploy Neo4j using **Neo4j Aura**
* Add **caching mechanisms**
* Implement **asynchronous request handling**
* Deploy on **Kubernetes for horizontal scaling**

-----------------------------------------------------

# Key Learning Outcomes

This project demonstrates:

* Implementation of **vector search using FAISS**
* Integration of **graph databases with vector retrieval**
* Development of a **hybrid RAG architecture**
* Techniques for **reducing hallucinations in LLM outputs**
* Designing **scalable AI systems**

-----------------------------------------------------

# Next Milestone

The current backend architecture is prepared for:

* Interactive **analytics dashboards**
* **Enterprise intelligence applications**
* **Cloud deployment and scaling**

-----------------------------------------------------

# 👨‍💻 Author

Aswathi T K
