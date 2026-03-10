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
13. [Why Each Step Matters](#Why-Each-Step-Matters)
14. [Quick Comparison Table](#Quick-Comparison-Table)
15. [Common Pattern (All Loaders)](#Common-Pattern-(All-Loaders))
16. [Text Splitter](#text-splitter)
17. [CharacterTextSplitter vs RecursiveCharacterTextSplitter](#charactertextsplitter-vs-recursivecharactertextsplitter)


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






### Text Splitter
## CharacterTextSplitter vs RecursiveCharacterTextSplitter

When working with LangChain, large documents must be split into smaller chunks before sending them to embeddings or LLMs. Two commonly used splitters are:

* **CharacterTextSplitter**
* **RecursiveCharacterTextSplitter**

Both use parameters like:

* `chunk_size`
* `chunk_overlap`

But they behave differently when splitting text.

---

# Example Input

```text
this is computer and i am a student who started learning AI recently, feeling wonderful about this course. i am very happy to have started this journey.
```

Settings used in this example:

```python
chunk_size = 50
chunk_overlap = 5
```

---
# CharacterTextSplitter

`CharacterTextSplitter` splits text **strictly based on character limits**.
It does not try to preserve sentence or word boundaries.

Example code:

```python
from langchain_text_splitters import CharacterTextSplitter

splitter = CharacterTextSplitter(
    chunk_size=50,
    chunk_overlap=5
)
```

### Output

| Chunk   | Text                                            |
| ------- | ----------------------------------------------- |
| Chunk 1 | this is computer and i am a student who started |
| Chunk 2 | arted learning AI recently, feeling wonderful   |
| Chunk 3 | derful about this course. i am very happy to    |
| Chunk 4 | y to have started this journey.                 |

⚠️ Notice the problems:

* Words are broken (`started → arted`)
* Sentences lose meaning
* Context becomes harder for LLMs to understand

---

# RecursiveCharacterTextSplitter

`RecursiveCharacterTextSplitter` is smarter.
It tries multiple separators in the following order:

```
paragraph → sentence → word → character
```

This helps preserve **sentence structure and meaning**.

Example code:

```python
from langchain_text_splitters import RecursiveCharacterTextSplitter

splitter = RecursiveCharacterTextSplitter(
    chunk_size=50,
    chunk_overlap=5
)
```

### Output

| Chunk   | Text                                            |
| ------- | ----------------------------------------------- |
| Chunk 1 | this is computer and i am a student who started |
| Chunk 2 | started learning AI recently, feeling wonderful |
| Chunk 3 | wonderful about this course.                    |
| Chunk 4 | i am very happy to have started this journey.   |

Here you can see:

* Words are not broken
* Sentences remain readable
* Overlap preserves context

Example overlap:

```
Chunk1 ends → started  
Chunk2 begins → started
```

---

# Side-by-Side Comparison

| Chunk | CharacterTextSplitter                           | RecursiveCharacterTextSplitter                  |
| ----- | ----------------------------------------------- | ----------------------------------------------- |
| 1     | this is computer and i am a student who started | this is computer and i am a student who started |
| 2     | arted learning AI recently, feeling wonderful   | started learning AI recently, feeling wonderful |
| 3     | derful about this course. i am very happy to    | wonderful about this course.                    |
| 4     | y to have started this journey.                 | i am very happy to have started this journey.   |

---

# Key Differences

| Feature               | CharacterTextSplitter  | RecursiveCharacterTextSplitter |
| --------------------- | ---------------------- | ------------------------------ |
| Splitting method      | Direct character split | Smart hierarchical split       |
| Sentence awareness    | ❌ No                   | ✅ Yes                          |
| Word breaking         | Often                  | Rare                           |
| Used in RAG pipelines | Rare                   | Very common                    |

---

# Visual Representation

### CharacterTextSplitter

```
this is computer and i am a student who started
arted learning AI recently, feeling wonderful
derful about this course. i am very happy to
y to have started this journey
```

### RecursiveCharacterTextSplitter

```
this is computer and i am a student who started
started learning AI recently, feeling wonderful
wonderful about this course
i am very happy to have started this journey
```

---

# Recommended Usage

For most **LangChain / RAG / AI document processing pipelines**, developers prefer:

```python
RecursiveCharacterTextSplitter
```

Typical configuration used in production systems:

```python
chunk_size = 1000
chunk_overlap = 200
```

This balances **context preservation and embedding performance**.

---

# References

LangChain Documentation:

https://python.langchain.com/docs/modules/data_connection/document_transformers/

# visual comparision ( CharacterTextSplitter vs RecursiveCharacterTextSplitter)
---

# 17. Visual Flow Comparison

Below is a simplified visual flow showing how each splitter processes the same text.

---

# CharacterTextSplitter Flow

CharacterTextSplitter performs **direct character-based cutting** without understanding sentences or words.

```id="flow1"
Input Text
    ↓
Apply chunk_size limit
    ↓
Split strictly by character length
    ↓
Words may break
    ↓
Output Chunks
```

Example visual:

```id="flow2"
this is computer and i am a student who started
arted learning AI recently, feeling wonderful
derful about this course. i am very happy to
y to have started this journey
```

Key idea:

* Splitting happens **mechanically**
* Text meaning may be partially lost
* Words may break in the middle

---

# RecursiveCharacterTextSplitter Flow

RecursiveCharacterTextSplitter tries to preserve meaning by splitting text using a **hierarchical separator strategy**.

Separator priority:

```id="flow3"
Paragraph → Sentence → Word → Character
```

Processing flow:

```id="flow4"
Input Text
    ↓
Try split by paragraph
    ↓
If chunk still too large → split by sentence
    ↓
If still too large → split by words
    ↓
If still too large → split by characters
    ↓
Output Chunks
```

Example visual:

```id="flow5"
this is computer and i am a student who started
started learning AI recently, feeling wonderful
wonderful about this course
i am very happy to have started this journey
```

Key idea:

* Tries to **preserve sentence boundaries**
* Words rarely break
* Chunks are **more meaningful for LLM processing**

---

# Summary Visualization

```id="flow6"
                Input Text
                    │
        ┌───────────┴───────────┐
        │                       │
CharacterTextSplitter   RecursiveCharacterTextSplitter
        │                       │
Direct character cut     Smart recursive splitting
        │                       │
Words may break          Sentence structure preserved
        │                       │
Less context             Better context for LLM
```

---

# Why This Matters for AI Applications

When building **RAG (Retrieval Augmented Generation) pipelines**, chunk quality directly affects answer quality.

Better chunks lead to:

* better embeddings
* better retrieval
* better LLM responses

For this reason, most LangChain pipelines prefer:

```python id="flow7"
RecursiveCharacterTextSplitter
```

over simple character splitting.

---


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
