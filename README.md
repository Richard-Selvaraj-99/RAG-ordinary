# General-Purpose RAG System using ChromaDB and Local LLM

## Overview

This project implements a **general-purpose Retrieval-Augmented Generation (RAG) system** designed to evaluate how RAG compares against **fine-tuning Large Language Models (LLMs)** in terms of **cost, computational efficiency, and accessibility**.

The system uses:
- **ChromaDB** as the vector store  
- **Cosine similarity** for embedding-based retrieval  
- **Default chunking parameters** to keep the pipeline simple  
- A **locally hosted LLM** for response generation  

The goal is to demonstrate that **RAG is often a more practical and less expensive alternative to fine-tuning**, especially for knowledge-intensive applications.

---

## System Architecture

The RAG pipeline consists of three core components:

### 1. Embedding Layer
- Converts documents into dense vector representations  
- Uses cosine similarity for semantic matching  
- Runs efficiently on **CPU**
- Does not require model retraining

### 2. Vector Store (ChromaDB)
- Stores embeddings and document metadata  
- Performs fast similarity search  
- Lightweight and scalable  
- CPU-friendly

### 3. Local LLM
- Consumes retrieved context and generates final responses  
- Typically requires **GPU** for efficient inference  
- Remains unchanged (no weight updates)

---

## RAG vs Fine-Tuning

### A Common Misconception

A frequent misunderstanding is:

> *Fine-tuning only changes model behavior.*

In reality, **fine-tuning modifies or adds new model weights**, which can effectively increase or reshape the model’s internal knowledge representation. This process introduces significant computational and operational overhead.

---

## Fine-Tuning: Cost and Complexity

Fine-tuning methods such as **AWQ**, **GPTQ**, and **QLoRA** introduce multiple challenges:

### Synthetic Data Generation
- Requires a capable LLM to generate training data  
- Often implemented using frameworks such as **LlamaIndex**  
- Adds additional inference cost before fine-tuning even begins

### Weight Integration Methods
- **AWQ / GPTQ**:  
  - Weights are *hard-merged* into the base model  
  - Increases model size and reduces flexibility  

- **QLoRA**:  
  - Uses *modular LoRA adapters*  
  - More flexible, but still requires GPU resources for training  

### Computational Overhead
- GPU-intensive training  
- High memory consumption  
- Increased energy and infrastructure costs  

---

## Why RAG Is More Accessible

RAG avoids most of the overhead associated with fine-tuning:

- No modification of base model weights  
- No retraining or gradient updates  
- Embeddings and vector stores run efficiently on **CPU**  
- Faster iteration and easier debugging  
- Knowledge updates only require re-embedding documents  

While **LLM inference itself is still computationally expensive**, RAG is **significantly less costly and more flexible** than fine-tuning for many use cases.

---

## Key Advantages of RAG

- Separation of **knowledge storage** and **language generation**
- Lower infrastructure requirements
- Easier domain adaptation
- Suitable for rapid prototyping and experimentation
- Scales well with growing datasets

---

## Conclusion

This project demonstrates that **Retrieval-Augmented Generation (RAG)** is a **lightweight, modular, and cost-effective approach** for enhancing LLM capabilities.

While fine-tuning remains valuable for deep behavioral alignment and specialized tasks, **RAG offers a more accessible solution** for knowledge-driven applications without the heavy computational burden of retraining or merging model weights.

---

## Future Work

- Compare response quality between RAG and fine-tuned models
- Benchmark latency and cost differences
- Experiment with different embedding models
- Add reranking and hybrid search
- Integrate multi-document reasoning

---
