# Vectorless Retrieval-Augmented Generation (RAG) System

## Overview

This repository contains a comprehensive pipeline for building and executing a vectorless Retrieval-Augmented Generation (RAG) system utilizing the PageIndex API and Google Gemini language models (via LangChain). Traditional RAG frameworks rely heavily on vector embeddings and chunk-based similarity search. In contrast, this project leverages hierarchical document parsing, structural tree-indexing, and targeted retrieval via the PageIndex platform to extract precise contexts directly from source documents without embedding generation.

The codebase supports both interactive Jupyter Notebook environments (such as Google Colab) and a web-based user interface powered by Streamlit for document indexing and querying.

---

## Key Features

- **Vectorless Indexing:** Bypasses conventional embedding databases by submitting PDF documents directly to the PageIndex hierarchical indexing engine.
- **Hierarchical Document Parsing:** Generates a structured document tree with automated section summaries for granular context extraction.
- **LLM Integration:** Connects seamlessly with Google Gemini (`gemini-2.5-flash`) via LangChain to generate structured, context-constrained responses.
- **Interactive Web Interface:** Includes a fully functional Streamlit application supporting multi-document upload, background tracking, and query execution.

---

## System Architecture

1. **Document Ingestion:** PDF files are downloaded or uploaded, registered via the `PageIndexClient`, and tracked asynchronously until retrieval readiness is established.
2. **Context Retrieval:** User queries trigger PageIndex retrieval tasks to pull relevant sections directly from the hierarchical document nodes.
3. **Generative Synthesis:** Retrieved contexts are consolidated and passed to the Gemini model with strict prompting rules to ensure answers are derived exclusively from the provided text.

---

## Prerequisites and Dependencies

The pipeline requires Python 3.12 or higher and depends on the following principal packages:

- `pageindex`
- `langchain`
- `langchain-google-genai`
- `google-generativeai`
- `streamlit`
- `requests`
- `pydantic`

---

## Installation and Configuration

### 1. Install Required Libraries
```bash
pip install pageindex
pip install langchain langchain-google-genai google-generativeai streamlit -q
```

### 2. Environment Variables
Ensure that the necessary API credentials are configured in your environment or secrets manager:
- `pi_key`: PageIndex API Key
- `gemini_key`: Google Gemini API Key

---

## Usage Guide

### Jupyter Notebook Workflow
Execute the cells sequentially within a Jupyter or Google Colab environment:
1. Initialize the `PageIndexClient` using your API key.
2. Submit a target document (e.g., an arXiv PDF) for hierarchical indexing.
3. Poll the client until retrieval status is marked as `completed`.
4. Execute queries using the `vectorless_rag` function to retrieve structured answers containing explanations, important points, and references.

### Streamlit Web Application
To run the web interface locally, save the Streamlit script portion into an application file (e.g., `app.py`) and execute:
```bash
streamlit run app.py
```
This interface allows users to:
- Upload multiple PDF documents simultaneously.
- Monitor automated indexing and document ID generation.
- Submit natural language queries against the indexed repository.

---

## License

This project is licensed under the terms specified in the repository root.