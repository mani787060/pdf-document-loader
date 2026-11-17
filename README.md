# LangChain PDF Document Loader

[![Python](https://img.shields.io/badge/Python-3.9%2B-blue)](https://www.python.org/)
[![LangChain](https://img.shields.io/badge/Framework-LangChain-green)](https://www.langchain.com/)
[![PDF](https://img.shields.io/badge/Input-PDF-red)](https://pypi.org/project/pypdf/)
[![RAG](https://img.shields.io/badge/Concept-RAG%20Data%20Ingestion-orange)](https://python.langchain.com/)

A beginner-friendly implementation of LangChain's `PyPDFLoader` for extracting text and page-level metadata from PDF documents. This project demonstrates how raw PDF content can be converted into structured LangChain `Document` objects, forming the data-ingestion stage of a Retrieval-Augmented Generation (RAG) pipeline.

**Repository:** https://github.com/mani787060/pdf-document-loader

---

## Project Overview

PDF documents often contain useful information that cannot be directly passed to an LLM as structured input. Before building a document-based question-answering system, we need to load the PDF and extract its text.

This project uses **`PyPDFLoader`**, provided by LangChain Community, to read a PDF and convert its pages into a list of LangChain `Document` objects.

Each document contains:
- `page_content`: The extracted text from a PDF page.
- `metadata`: Additional information about the document, such as its source file and page information.

The repository currently demonstrates this workflow using the included `dl-curriculum.pdf` file.

## Key Concepts Demonstrated

### 1. PDF Document Loading

- Uses LangChain's `PyPDFLoader` to read a PDF file.
- Loads the PDF using the `load()` method.
- Converts the PDF pages into a list of structured `Document` objects.

### 2. Page-Level Text Extraction

- Extracts the total number of loaded page documents using `len(docs)`.
- Accesses the extracted text through `docs[0].page_content`.
- Demonstrates how to inspect the content of an individual PDF page.

### 3. Metadata Inspection

- Accesses document metadata through `docs[1].metadata`.
- Demonstrates how source and page-related information can be associated with extracted content.
- Shows why metadata is useful when tracing information back to its original document.

### 4. RAG Pipeline Preparation

PDF loading is an early stage of a typical RAG workflow:

```text
PDF Document
     |
     v
PyPDFLoader
     |
     v
LangChain Document Objects
     |
     v
Text Splitting / Chunking
     |
     v
Embeddings
     |
     v
Vector Database
     |
     v
Retriever + LLM
     |
     v
Context-Aware Answers
```

This repository focuses on the **PDF loading and document inspection stage**. Text splitting, embedding generation, vector storage, and question answering are not implemented in the current script.

---

## Tech Stack

| Technology | Purpose |
|---|---|
| Python | Main programming language |
| LangChain Community | Provides the PDF document loader |
| PyPDF | PDF parsing dependency |
| PyPDFLoader | Loads PDF pages into LangChain documents |

## Repository Structure

```text
pdf-document-loader/
│
├── dl-curriculum.pdf    # Sample PDF used for loading
├── pdf_loader.py        # PyPDFLoader implementation
└── README.md            # Project documentation
```

## Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com/mani787060/pdf-document-loader.git
```

### 2. Navigate to the Project Directory

```bash
cd pdf-document-loader
```

### 3. Create a Virtual Environment (Recommended)

```bash
python -m venv .venv
```

Activate it on Windows:

```bash
.venv\Scripts\activate
```

Activate it on macOS/Linux:

```bash
source .venv/bin/activate
```

### 4. Install Dependencies

```bash
python -m pip install --upgrade pip
pip install -U langchain-community pypdf
```

### 5. Run the Implementation

The repository already contains `dl-curriculum.pdf`, which is used by the Python script.

Run:

```bash
python pdf_loader.py
```

The script loads the PDF, prints the number of page documents, displays the extracted text from the first page, and prints metadata from the second page.

**Note:** The current implementation accesses `docs[0]` and `docs[1]`, so the input PDF must contain at least two pages.

---

## Understanding the Python Implementation

The core implementation is intentionally simple:

```python
from langchain_community.document_loaders import PyPDFLoader

loader = PyPDFLoader('dl-curriculum.pdf')

docs = loader.load()

print(len(docs))

print(docs[0].page_content)

print(docs[1].metadata)
```

### How It Works

1. **Import `PyPDFLoader`:** Imports the PDF loader from LangChain Community.
2. **Create the loader:** Initializes the loader with the PDF file path.
3. **Load the PDF:** Calls `loader.load()` to obtain a list of `Document` objects.
4. **Count the pages:** Uses `len(docs)` to display the number of loaded page documents.
5. **Extract page text:** Reads the first document's `page_content`.
6. **Inspect metadata:** Displays the metadata associated with the second document.

## Why Is This Important for Generative AI?

Document loading is an essential step in building applications that use private or domain-specific knowledge.

For example, a PDF-based AI assistant needs to:

- Read information from PDF documents.
- Convert the extracted content into a usable format.
- Preserve document metadata for source tracking.
- Prepare the content for chunking and embedding generation.
- Retrieve relevant information when a user asks a question.

Understanding `PyPDFLoader` provides a foundation for developing document-based RAG applications.

## Current Scope and Limitations

This repository is a focused learning implementation, not a complete RAG application.

- It loads a local PDF file.
- It uses the standard `load()` method.
- It inspects extracted page text and metadata.
- It does not currently implement lazy loading, OCR, text splitting, embeddings, vector databases, or LLM-based question answering.
- Scanned PDFs containing only images may require an OCR-based extraction workflow.

## Future Improvements

Possible extensions include:

- Support for loading multiple PDF files.
- Exploring `lazy_load()` for page-by-page processing.
- Adding text splitters for chunking long documents.
- Generating embeddings from extracted content.
- Integrating a vector database such as FAISS or Chroma.
- Building a PDF question-answering application using RAG.
- Exploring OCR for scanned PDF documents.

## Learning Outcomes

Through this implementation, I explored:

- How LangChain document loaders work.
- How to load PDF documents using `PyPDFLoader`.
- How PDF pages are represented as LangChain `Document` objects.
- How to access extracted text through `page_content`.
- How to inspect document metadata.
- How document loading fits into a larger RAG architecture.

## References

- [LangChain Documentation](https://python.langchain.com/docs/introduction/)
- [LangChain Community Document Loaders](https://python.langchain.com/docs/integrations/document_loaders/)
- [PyPDF Documentation](https://pypdf.readthedocs.io/)

---
