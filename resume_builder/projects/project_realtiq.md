# Project: RealtIQ

## Overview
- **Type:** Personal
- **Repo:** https://github.com/bhargavram0211/RealtIQ

## Stack
- **Languages:** Python
- **LLM & Framework:** Google Gemini (via langchain-google-genai), LangChain (v0.3+)
- **Embeddings:** HuggingFace all-MiniLM-L6-v2
- **Vector Database:** ChromaDB
- **Relational Database:** MySQL
- **Interface:** Streamlit

## What It Does
A conversational real estate database retrieval system that translates natural language questions into SQL queries using few-shot learning and semantic embeddings. Users can query property data without SQL knowledge through a Streamlit web interface. Leverages Google Gemini LLM with LangChain, ChromaDB vector storage, and HuggingFace embeddings for semantic understanding of complex property-related questions covering location, price, amenities, and specifications.

## Quantitative
- Semantic search via embeddings and vector storage
- Few-shot learning approach for query accuracy
- Support for complex property-related multi-field queries
- Web-based interface on localhost:8501

## Bullets

### DevOps/Infra Frame
**Bullet (2L):** Designed and deployed multi-layer data retrieval pipeline combining MySQL relational database, ChromaDB vector storage, and HuggingFace embeddings; architected few-shot learning system using Google Gemini for semantic query translation, enabling scalable natural language database interaction.

**Bullet (1L):** Built NLP database system: MySQL, ChromaDB, embeddings, Gemini; semantic query translation.

### FullStack/Product Frame
**Bullet (2L):** Built RealtIQ, a conversational real estate database system leveraging Google Gemini, LangChain, and ChromaDB to translate natural language queries into SQL; designed few-shot learning approach with HuggingFace embeddings for semantic understanding, enabling property-related questions covering location, price, amenities.

**Bullet (1L):** Built conversational database system; natural language to SQL translation via Gemini + LangChain.

## Tags
llm, langchain, google-gemini, chromadb, vector-database, mysql, streamlit, nlp, embeddings, database, ai, semantic-search, few-shot-learning
