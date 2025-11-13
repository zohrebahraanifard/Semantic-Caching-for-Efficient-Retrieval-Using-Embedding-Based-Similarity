# Semantic Caching System

This repository contains an implementation of a **semantic caching system** using modern embedding models, vector search, and fast in-memory storage. The notebook demonstrates how to build a cache that understands **semantic similarity**, enabling faster retrieval for repeated or related queries.

## Contents

* **Semantic_Caching.ipynb**

  * Installs and loads required libraries (Redis, FAISS, Transformers, SentenceTransformers, PyTorch)
  * Loads datasets using KaggleHub
  * Generates embeddings for text queries or documents
  * Stores and retrieves cached results using Redis
  * Uses FAISS for fast vector similarity search
  * Combines LLM-based embeddings with caching logic

## Overview

Semantic caching replaces traditional key-based caching with **meaning-based lookup**. Instead of retrieving from cache only when the exact query exists, semantic caching returns stored results when a new query is *similar in meaning*.

### Key Components

* **Embeddings:** Represent text queries as numerical vectors.
* **FAISS Index:** Provides approximate nearest-neighbor search.
* **Redis Cache:** Stores compressed or direct response objects.
* **Similarity Threshold:** Determines if a past result is relevant enough to reuse.

## Workflow

1. The user submits a query.
2. The system computes an embedding using a transformer model.
3. The embedding is compared with previous queries using FAISS.
4. If a similar cached result exists:

   * Retrieve it instantly from Redis.
5. Otherwise:

   * Process the query normally.
   * Store the new query/response in the semantic cache.

## Technologies Used

* **Python 3**
* **FAISS** for vector similarity search
* **Redis** for fast caching
* **SentenceTransformers / Transformers** for embedding generation
* **PyTorch** as the core ML framework
* **KaggleHub** for dataset loading

## Running the Notebook

Install dependencies if needed:

```
pip install redis faiss-cpu sentence-transformers transformers torch kagglehub
```

Launch the notebook:

```
jupyter notebook
```

Ensure Redis is running on your system before executing semantic cache sections.

## Output

* Embedding vectors for dataset items or queries
* Vector index creation and search
* Redis cache entries
* Cache hit vs. miss behavior
* Semantic similarity results

## Extensions

* Add TTL (time-to-live) cache policies
* Store additional metadata (timestamps, access frequency)
* Replace FAISS with a cloud vector DB (Pinecone, Milvus, Weaviate)
* Add batch processing for query groups
* Integrate with RAG/LLM retrieval pipelines

