# RAG-LANGECHIAN
# 📚 MCQ Generator using HuggingFace + LangChain (RAG Based)

## 🚀 Project Overview

This project builds an **MCQ (Multiple Choice Question) Generator** using:

* 🤗 HuggingFace Models
* 🔗 LangChain
* 📄 PDF Document Loader
* 🧠 FAISS Vector Database
* 🔎 RAG (Retrieval Augmented Generation)

The system extracts content from a PDF file, stores embeddings in a vector database, and generates MCQs based on the retrieved context.

---

## 🏗️ Architecture Flow

1. Load PDF
2. Split text into chunks
3. Generate embeddings using HuggingFace
4. Store embeddings in FAISS
5. Retrieve relevant context
6. Generate MCQs using LLM
7. Parse output in JSON format

---

## 📦 Technologies Used

* Python 3.10+
* LangChain
* HuggingFace Endpoint / Embeddings
* FAISS
* PyPDFLoader
* RecursiveCharacterTextSplitter
* JSONOutputParser

---

## 📂 Project Structure

```
project/
│
├── huggingface.ipynb     # Main notebook implementation
├── sample.pdf            # Input PDF file
├── README.md             # Project documentation
```

---

## ⚙️ Installation

### 1️⃣ Create Virtual Environment

```bash
python -m venv venv
source venv/bin/activate  # Mac/Linux
venv\Scripts\activate     # Windows
```

### 2️⃣ Install Dependencies

```bash
pip install langchain
pip install langchain-community
pip install langchain-core
pip install langchain-huggingface
pip install faiss-cpu
pip install pypdf
pip install huggingface_hub
```

---

## 🔐 Setup HuggingFace API Token

1. Go to: https://huggingface.co/settings/tokens
2. Generate a new API token
3. Set environment variable:

### Mac/Linux

```bash
export HUGGINGFACEHUB_API_TOKEN="your_token_here"
```

### Windows

```bash
set HUGGINGFACEHUB_API_TOKEN="your_token_here"
```

---

## 🧠 How It Works (Step-by-Step)

### Step 1: Load PDF

```python
loader = PyPDFLoader("sample.pdf")
documents = loader.load()
```

### Step 2: Split Text

```python
text_splitter = RecursiveCharacterTextSplitter(
    chunk_size=1000,
    chunk_overlap=200
)
docs = text_splitter.split_documents(documents)
```

### Step 3: Create Embeddings

```python
embeddings = HuggingFaceEmbeddings()
```

### Step 4: Store in FAISS

```python
vectorstore = FAISS.from_documents(docs, embeddings)
```

### Step 5: Create Retriever

```python
retriever = vectorstore.as_retriever()
```

### Step 6: Generate MCQs Using LLM

* Create prompt template
* Pass retrieved context
* Generate structured MCQ output

---

## 📄 Example Output Format (JSON)

```json
{
  "question": "What is Artificial Intelligence?",
  "options": [
    "A type of database",
    "Simulation of human intelligence",
    "A programming language",
    "A hardware device"
  ],
  "answer": "Simulation of human intelligence"
}
```

---

## 🎯 Features

✔️ PDF-based MCQ generation
✔️ RAG implementation
✔️ JSON structured output
✔️ Vector search using FAISS
✔️ HuggingFace LLM integration

---

## 🛠️ Possible Improvements

* Add FastAPI endpoint for MCQ generation
* Add Streamlit UI
* Export MCQs to PDF
* Add difficulty level control
* Store questions in database

---

## 🐛 Common Errors & Solutions

### ❌ HuggingFace Import Error

Use:

```python
from langchain_huggingface import HuggingFaceEndpoint
```

Instead of:

```python
from langchain import HuggingFaceHub
```

---

## 📌 Future Scope

* Multi-language MCQ generation
* Quiz API for frontend apps
* LMS integration
* Auto evaluation system

---

## 👩‍💻 Author

Developed for learning and experimenting with:

* LangChain
* HuggingFace
* Retrieval Augmented Generation (RAG)

---

## ⭐ If You Like This Project

Give it a ⭐ on GitHub and share with others!
