# LangChain PDF Document Loader
[![LangChain](https://img.shields.io/badge/Framework-LangChain-green)](https://www.langchain.com/)
[![Python](https://img.shields.io/badge/Python-3.9%2B-blue)](https://www.python.org/)
[![Data Ingestion](https://img.shields.io/badge/Pipeline-Data%20Ingestion-orange)](https://python.langchain.com/docs/modules/data_connection/document_loaders/)

## 🏗️ Project Overview
This repository focuses on **Data Ingestion**, the critical first step in any Retrieval-Augmented Generation (RAG) architecture. Before an AI can answer questions about a proprietary document, that document must be converted into a machine-readable format. This project demonstrates how to use LangChain's **`PyPDFLoader`** to reliably transform static PDF files into a list of structured `Document` objects, ready for downstream processing and vectorization.

---

## 🛠️ Key Technical Implementations

### 1. Document Ingestion
* **`PyPDFLoader` Integration:** Utilizing a standard, battle-tested library to open and read PDF files, bypassing the complexities of raw byte parsing.
* **Lazy Loading Capabilities:** Understanding how to load documents into memory efficiently, which is crucial when dealing with massive, hundreds-of-pages-long text files.

### 2. The `Document` Object Model
* **Content Extraction:** Isolating the raw text (`page_content`) from the visual formatting of the PDF.
* **Metadata Preservation:** Automatically capturing and storing the `source` (file path) and `page` number alongside the extracted text. This is essential for building AI systems that can accurately cite their sources.

### 3. Pipeline Readiness
* **Pre-Chunking State:** Outputting data in the exact format required by LangChain's Text Splitters, creating a seamless handoff to the next stage of the data engineering pipeline.

---

## 💻 Tech Stack
* **Language:** Python 3.9+
* **Framework:** LangChain Community (`langchain-community`)
* **Dependencies:** `pypdf`
* **Environment:** Virtual Environment / `python-dotenv`

---

## 🚀 Getting Started

1. **Clone the repository:**
   ```bash
   git clone [https://github.com/your-username/langchain-pdf-document-loader.git](https://github.com/your-username/langchain-pdf-document-loader.git)

2. **Install Dependencies:**
   ```bash
   pip install -U langchain-community pypdf python-dotenv

3. **Add a Sample PDF:**
   Place a sample PDF file (e.g., sample_paper.pdf) in the root directory.
  
4. **Run the Implementation:**
   ```bash
   python pdf_loader.py   
