# W3 – LangChain Learning Project

This repository contains my **hands-on experiments with LangChain using VS Code and Python**.
The goal of this project is to understand **how LangChain works for loading documents and interacting with external knowledge sources**.

This repository will continue to grow as I learn more LangChain concepts.

---

# Table of Contents

1. [Project Overview](#1-project-overview)
2. [Tools & Technologies Used](#2-tools--technologies-used)
3. [Project Files](#3-project-files)
4. [Environment Setup](#4-environment-setup)
5. [Introduction to LangChain](#5-introduction-to-langchain)
6. [Understanding Document Loaders](#6-understanding-document-loaders)
7. [Example: Loading Documents with LangChain](#7-example-loading-documents-with-langchain)
8. [Example: Arxiv Research Paper Loader](#8-example-arxiv-research-paper-loader)
9. [Working with Jupyter Notebook in VS Code](#9-working-with-jupyter-notebook-in-vs-code)
10. [How to Run This Project](#10-how-to-run-this-project)
11. [Git & Version Control Workflow](#11-git--version-control-workflow)
12. [Future Learning Topics](#12-future-learning-topics)

---

# 1. Project Overview

This project is part of my learning journey into **LangChain and AI application development**.

In this repository I explored:

* Installing and configuring LangChain
* Understanding **packages, modules, and imports**
* Using **LangChain document loaders**
* Loading external documents and research papers
* Running experiments in **Jupyter Notebook inside VS Code**

The aim is to **build a strong foundation before moving into advanced topics like RAG and AI applications**.

---

# 2. Tools & Technologies Used

| Tool             | Purpose                                   |
| ---------------- | ----------------------------------------- |
| Python           | Programming language                      |
| VS Code          | Development environment                   |
| Jupyter Notebook | Interactive experimentation               |
| LangChain        | Framework for building AI applications    |
| Git & GitHub     | Version control and project documentation |

---

# 3. Project Files

Current files in this repository:

```
W3-Langchain
│
├── langchain.ipynb     → Main notebook containing experiments
├── notes.txt           → Learning notes and observations
├── IITM.pdf            → Sample document used for experiments
└── README.md           → Project documentation
```

More files and examples will be added as the learning progresses.

---

# 4. Environment Setup

To run this project locally:

### Install Python

python -m venv venv

Activate the environment 


---

### Install Required Libraries

Install LangChain and dependencies:

```
pip install langchain
pip install langchain-community
pip install arxiv
pip install pypdf
```

---

### Open Project in VS Code

1. Open VS Code
2. Select **File → Open Folder**
3. Choose this project folder

---

# 5. Introduction to LangChain

LangChain is a **framework that helps developers build applications powered by large language models (LLMs)**.

It simplifies tasks such as:

* Loading documents
* Processing knowledge sources
* Creating AI pipelines
* Building chatbots
* Retrieval Augmented Generation (RAG)

LangChain connects:

```
Documents → Processing → LLM → AI Application
```

---

# 6. Understanding Document Loaders

Document loaders are used to **load data from external sources into LangChain**.

Examples of sources:

* Text files
* PDFs
* Websites
* Research papers
* APIs

Example import:

```python
from langchain_community.document_loaders import TextLoader
```

This means:

| Component           | Meaning |
| ------------------- | ------- |
| langchain_community | Package |
| document_loaders    | Module  |
| TextLoader          | Class   |

The loader reads the document and converts it into **LangChain document objects**.

---

# 7. Example: Loading Documents with LangChain

Example code:

```python
from langchain_community.document_loaders import TextLoader

loader = TextLoader("data.txt")

documents = loader.load()

print(documents)
```

Explanation:

1. Import the **TextLoader class**
2. Create a loader object
3. Load the file
4. Convert it into LangChain documents

This allows the document to be processed by **AI models later**.

---

# 8. Example: Arxiv Research Paper Loader

LangChain can also fetch research papers from **Arxiv**.

Example:

```python
from langchain_community.document_loaders import ArxivLoader

loader = ArxivLoader(query="large language models", load_max_docs=2)

documents = loader.load()
```

What this does:

1. Searches Arxiv for research papers
2. Downloads the papers
3. Converts them into LangChain document objects

This is useful for **AI research and knowledge retrieval systems**.

---

# 9. Working with Jupyter Notebook in VS Code

The file:

```
langchain.ipynb
```

is a **Jupyter Notebook**.

Jupyter notebooks allow us to:

* Run Python code step-by-step
* Test ideas quickly
* View outputs immediately
* Document experiments

VS Code provides built-in support for running notebooks.

---

# 10. How to Run This Project

Steps:

1. Clone the repository
2. Open the project in VS Code
3. Install required libraries
4. Open `langchain.ipynb`
5. Run the notebook cells sequentially

---

# 11. Git & Version Control Workflow

This project is tracked using **Git and GitHub**.

Typical workflow:

### Add changes

```
git add .
```

### Commit changes

```
git commit -m "Update LangChain experiments"
```

### Push to GitHub

```
git push
```

This allows the project to be accessed from **multiple machines (home laptop / office laptop)**.

### Why Each Step Matters

| Step | Purpose | Analogy |
|------|---------|---------|
| **Load** | Get data into system | Opening a book |
| **Split** | Fit into context window | Cutting into digestible pages |
| **Embed** | Convert to searchable format | Creating an index |
| **Store** | Enable fast retrieval | Organizing in a library |
| **Retrieve** | Find relevant info | Searching the index |
| **Generate** | Create answer | Reading and summarizing |

## 📊 Quick Comparison Table

| Source Type | Loader Class | Output Format | Best For |
|-------------|--------------|---------------|----------|
| **PDF** | `PyPDFLoader` | One doc per page | Reports, books, papers |
| **Text** | `TextLoader` | One doc total | Notes, logs, configs |
| **Web** | `WebBaseLoader` | One doc per URL | Blogs, articles, docs |
| **Wikipedia** | `WikipediaLoader` | Multiple articles | Research, definitions |

### Common Pattern (All Loaders)
```python
# 1. Import
from langchain_community.document_loaders import [LoaderName]

# 2. Initialize
loader = LoaderName("source")

# 3. Load
docs = loader.load()

# 12. Future Learning Topics

This repository will continue to expand with the following topics:

* PDF document loaders
* Web page loaders
* Text splitting
* Embeddings
* Vector databases
* Retrieval Augmented Generation (RAG)
* LangChain agents
* AI pipelines

These topics will be added in future commits.

---

# Notes

This README is intentionally written in **simple explanations** so that beginners coming from non-AI backgrounds (like SAP or enterprise systems) can easily understand the concepts.

More examples and explanations will be appended as new experiments are added to this repository.

---
