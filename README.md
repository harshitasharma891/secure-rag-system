# Secure RAG: Sensitive Information Detection and Redaction

## Project Overview

This project implements a Secure Retrieval-Augmented Generation (RAG) system that detects and masks sensitive information before processing user queries.

The system combines Natural Language Processing, Named Entity Recognition (NER), regular expression-based detection, semantic retrieval, and a Large Language Model to provide context-grounded answers while identifying sensitive information in user input.

## Key Features

- Sensitive information detection using Hugging Face NER.
- Detection of email addresses and phone numbers.
- Detection of Aadhaar and PAN numbers using regular expressions.
- Sensitive information masking and redaction.
- Semantic document retrieval using embeddings and FAISS.
- Context-grounded answer generation using FLAN-T5.
- Security reports showing detected sensitive entities.
- End-to-end Secure RAG pipeline.

## How the System Works

1. A user submits a query.
2. The system detects sensitive information using NER and pattern matching.
3. Sensitive entities are masked in the query.
4. The relevant question is used to retrieve related documents from the knowledge base.
5. FAISS performs semantic similarity search to retrieve relevant context.
6. The FLAN-T5 model generates an answer based on the retrieved context.
7. The system returns the security report, masked query, retrieved context, and generated answer.

## Technologies Used

- Python
- Hugging Face Transformers
- Sentence Transformers
- FAISS
- PyTorch
- Pandas
- NumPy
- Google Colab

## Models Used

### Embedding Model

`sentence-transformers/all-MiniLM-L6-v2`

Used to convert knowledge-base documents and user queries into vector embeddings for semantic retrieval.

### Named Entity Recognition Model

`dslim/bert-base-NER`

Used to identify entities such as people, organizations, and locations.

### Language Model

`google/flan-t5-base`

Used to generate answers based on the retrieved context.

## Sensitive Information Detection

The system detects the following types of sensitive information:

| Information Type | Detection Method |
|---|---|
| Person, Organization, Location | Hugging Face NER |
| Email Address | Regular Expression |
| Phone Number | Regular Expression |
| Aadhaar Number | Regular Expression |
| PAN Number | Regular Expression |

Detected information is replaced with a corresponding masked label, such as:

`[EMAIL_MASKED]`

`[PHONE_MASKED]`

`[AADHAAR_MASKED]`

`[PAN_MASKED]`

## RAG Pipeline

The project uses the following RAG architecture:

**User Query → Sensitive Information Detection → Information Masking → Semantic Retrieval → FAISS → Context Retrieval → FLAN-T5 → Generated Answer**

The knowledge base is created from a CSV dataset containing question-and-answer pairs.

## Project Output

The Secure RAG pipeline returns:

- Original Query
- Masked Query
- Security Report
- Detected Entities
- Retrieved Context
- Generated Answer
- Processing Status

## Installation

Install the required libraries:

```python
pip install transformers sentence-transformers faiss-cpu accelerate sentencepiece torch pandas numpy
```

## Running the Project

1. Upload a CSV dataset containing `query` and `answer` columns.
2. Create the knowledge base from the dataset.
3. Generate embeddings using the Sentence Transformer model.
4. Build the FAISS vector index.
5. Load the NER and FLAN-T5 models.
6. Run the `secure_rag()` function with a user query.

## Project Structure

```text
Secure-RAG-System/
│
├── Sensitive_Information_Detection_and_Redaction.ipynb
├── README.md
└── dataset.csv
```

## Author

**Harshita Sharma**

AI/ML Engineer

GitHub: github.com/harshitasharma891  
LinkedIn: linkedin.com/in/harshita-sharma-b843031b5
