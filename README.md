# AI Text Summarizer

An AI-powered Text Summarizer built using **FastAPI** and **Python**. This application allows users to submit long pieces of text and receive concise, meaningful summaries using Natural Language Processing (NLP) or Large Language Models (LLMs).

---

## Features

- Summarize long text into short, readable content
- Fast REST API using FastAPI
- JSON-based request and response
- Interactive API documentation with Swagger UI
- Easy integration with web or mobile applications
- Lightweight and scalable architecture

---

## Tech Stack

- **Backend:** FastAPI
- **Language:** Python 3.10+
- **Server:** Uvicorn
- **AI/NLP:** Transformers / OpenAI / Hugging Face (depending on implementation)
- **Validation:** Pydantic

---

## Installation

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/ai-text-summarizer.git

cd ai-text-summarizer
```

### 2. Create a Virtual Environment

**Windows**

```bash
python -m venv venv

venv\Scripts\activate
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

---

## Running the Application

Start the FastAPI server using Uvicorn.

```bash
uvicorn app.main:app --reload
```

Server runs at:

```
http://127.0.0.1:8000
```

---

## API Documentation

Swagger UI

```
http://127.0.0.1:8000/docs
```

ReDoc

```
http://127.0.0.1:8000/redoc
```

---

## API Endpoint

### POST `/summarize`

Generate a summary from the input text.

### Request

```json
{
  "text": "Artificial Intelligence is transforming industries by enabling machines to learn from data and make intelligent decisions..."
}
```

### Response

```json
{
  "summary": "Artificial Intelligence enables machines to learn from data and make intelligent decisions."
}
```

---

## Requirements

Example `requirements.txt`

```
fastapi
uvicorn
pydantic
transformers
torch
```

---
