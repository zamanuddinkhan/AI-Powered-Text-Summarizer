# AI Text Summarizer

An AI-powered **Text Summarizer** built using **FastAPI** and **Python**.

This application allows users to submit long pieces of text and receive concise, meaningful summaries using **Natural Language Processing (NLP)** or **Large Language Models (LLMs)**.

The project exposes a REST API that can be used by web applications, mobile applications, desktop applications, or other backend services.

---

## Project Overview

The **AI Text Summarizer** takes a long piece of text as input and generates a shorter version containing the most important information.

For example:

### Input

```text
Artificial Intelligence is a field of computer science that focuses on
creating machines capable of performing tasks that normally require
human intelligence. These tasks include learning, reasoning,
understanding language, recognizing images, and making decisions.
AI is being used in healthcare, finance, education, transportation,
customer service, and many other industries.
```

### Output

```text
Artificial Intelligence enables machines to perform tasks such as
learning, reasoning, language understanding, and decision-making.
It is widely used across industries including healthcare, finance,
education, and transportation.
```

The goal is to reduce the length of the original content while preserving its important meaning.

---

## How It Works

The application follows a simple request-response flow:

```text
User
  |
  | Sends text
  v
FastAPI Application
  |
  | Validates request
  v
Summarization Model
  |
  | Generates summary
  v
FastAPI Application
  |
  | Returns JSON response
  v
User
```

### Step-by-Step

1. The user sends a piece of text to the API.
2. FastAPI receives the request.
3. Pydantic validates the incoming data.
4. The text is passed to the AI/NLP summarization model.
5. The model generates a concise summary.
6. FastAPI returns the summary as a JSON response.

---

## Features

* Summarize long text into short, readable content
* Fast REST API using FastAPI
* JSON-based request and response
* Interactive API documentation with Swagger UI
* ReDoc API documentation
* Easy integration with web applications
* Easy integration with mobile applications
* Lightweight architecture
* Automatic request validation
* Clear API responses
* Error handling for invalid requests
* AI-powered text processing
* Scalable backend structure

---

## Tech Stack

| Technology       | Purpose                    |
| ---------------- | -------------------------- |
| **Python 3.10+** | Programming language       |
| **FastAPI**      | Backend web framework      |
| **Uvicorn**      | ASGI server                |
| **Pydantic**     | Data validation            |
| **Transformers** | NLP/AI models              |
| **PyTorch**      | Machine learning framework |
| **Hugging Face** | Pre-trained NLP models     |

Depending on the implementation, the summarization model can also be provided through an external LLM API.

---

## Project Structure

A simple project structure can look like this:

```text
ai-text-summarizer/
│
├── app/
│   ├── __init__.py
│   ├── main.py
│   ├── models.py
│   └── summarizer.py
│
├── requirements.txt
├── .env
├── .gitignore
└── README.md
```

### File Description

#### `app/main.py`

Contains the FastAPI application and API routes.

```text
main.py
    ↓
Creates FastAPI application
    ↓
Defines /summarize endpoint
```

#### `app/models.py`

Contains Pydantic models used for validating API requests and responses.

#### `app/summarizer.py`

Contains the summarization logic and AI/NLP model interaction.

#### `requirements.txt`

Contains the Python packages required to run the application.

#### `.env`

Stores configuration values and API keys when an external AI service is used.

> Never commit secret API keys to GitHub.

#### `.gitignore`

Specifies files and folders that Git should ignore.

---

# Installation

## 1. Clone the Repository

```bash
git clone https://github.com/your-username/ai-text-summarizer.git
```

Move into the project directory:

```bash
cd ai-text-summarizer
```

---

## 2. Create a Virtual Environment

A virtual environment keeps the project's dependencies separate from other Python projects.

### Windows

```bash
python -m venv venv
```

Activate it:

```bash
venv\Scripts\activate
```

### macOS/Linux

```bash
python3 -m venv venv
```

Activate it:

```bash
source venv/bin/activate
```

After activation, you should see something similar to:

```text
(venv)
```

in your terminal.

---

## 3. Upgrade pip

```bash
python -m pip install --upgrade pip
```

---

## 4. Install Dependencies

Install the required packages:

```bash
pip install -r requirements.txt
```

---

# Running the Application

Start the FastAPI server using Uvicorn:

```bash
uvicorn app.main:app --reload
```

The application should start successfully.

Server:

```text
http://127.0.0.1:8000
```

The `--reload` option automatically restarts the server whenever you make code changes.

This is useful during development.

---

# API Documentation

FastAPI automatically generates interactive API documentation.

## Swagger UI

Open:

```text
http://127.0.0.1:8000/docs
```

Swagger UI allows you to:

* View available endpoints
* View request formats
* View response formats
* Send API requests
* Test the API directly from your browser

---

## ReDoc

Open:

```text
http://127.0.0.1:8000/redoc
```

ReDoc provides another interface for viewing the API documentation.

---

# API Endpoint

## POST `/summarize`

Generates a summary from the provided text.

### Method

```text
POST
```

### Endpoint

```text
/summarize
```

### Full URL

```text
http://127.0.0.1:8000/summarize
```

---

# Request and Response

## Request

The API expects a JSON object containing the text that needs to be summarized.

```json
{
  "text": "Artificial Intelligence is transforming industries by enabling machines to learn from data and make intelligent decisions..."
}
```

---

## Response

A successful request returns:

```json
{
  "summary": "Artificial Intelligence enables machines to learn from data and make intelligent decisions."
}
```

---

# Request Validation

Pydantic can be used to validate incoming requests.

For example:

```json
{
  "text": ""
}
```

can be rejected because the application expects meaningful text.

A validation error may look like:

```json
{
  "detail": [
    {
      "loc": ["body", "text"],
      "msg": "Text cannot be empty",
      "type": "value_error"
    }
  ]
}
```

The exact response depends on how validation is implemented.

---

# Testing the API

There are several ways to test the API.

## Method 1: Swagger UI

Open:

```text
http://127.0.0.1:8000/docs
```

Then:

1. Find `POST /summarize`
2. Click **Try it out**
3. Enter your text
4. Click **Execute**
5. View the generated summary

---

## Method 2: cURL

You can also use cURL from the terminal:

```bash
curl -X POST "http://127.0.0.1:8000/summarize" \
-H "Content-Type: application/json" \
-d "{\"text\":\"Artificial Intelligence is transforming many industries by enabling machines to learn from data and perform intelligent tasks.\"}"
```

---

## Method 3: Python

You can call the API from another Python program:

```python
import requests

url = "http://127.0.0.1:8000/summarize"

data = {
    "text": "Artificial Intelligence is transforming many industries by enabling machines to learn from data and perform intelligent tasks."
}

response = requests.post(url, json=data)

print(response.json())
```

---

# Requirements

Example `requirements.txt`:

```text
fastapi
uvicorn
pydantic
transformers
torch
```

If the project uses an external LLM API instead of a local Transformers model, the required package will depend on the provider.

For example, an API-based implementation may require an additional SDK.

---

# Environment Variables

If the application uses an external AI API, sensitive configuration should be stored in environment variables.

Example `.env`:

```text
API_KEY=your_api_key_here
```

The `.env` file should **not** be committed to GitHub.

Add it to `.gitignore`:

```text
.env
venv/
__pycache__/
*.pyc
```

---

# Error Handling

The API should provide meaningful errors when something goes wrong.

Common situations include:

### Empty Text

```json
{
  "text": ""
}
```

Possible response:

```json
{
  "detail": "Text cannot be empty"
}
```

### Missing Text Field

```json
{}
```

FastAPI/Pydantic can return a validation error indicating that the required field is missing.

### Server or Model Error

If the AI model fails to generate a summary, the API should return an appropriate HTTP error rather than exposing internal application details.

---

# Example Use Cases

The project can be used for many types of text.

### News Articles

Convert long news articles into short summaries.

### Research Papers

Extract the main ideas from lengthy research material.

### Blog Posts

Create short versions of long blog posts.

### Documents

Summarize large amounts of textual information.

### Study Material

Generate concise notes from longer educational content.

### Business Reports

Reduce lengthy reports to their key points.

---

# AI/NLP Approach

The summarizer can be implemented using different approaches.

## Transformer-Based Summarization

A pre-trained Transformer model can be used to generate summaries.

The general flow is:

```text
Input Text
    ↓
Tokenizer
    ↓
Transformer Model
    ↓
Generated Tokens
    ↓
Decoded Text
    ↓
Summary
```

Popular summarization models available through the Hugging Face ecosystem include models designed specifically for abstractive summarization.

---

## External LLM API

Another approach is to send the text to an external Large Language Model through an API.

The flow becomes:

```text
Client
   ↓
FastAPI
   ↓
LLM API
   ↓
Generated Summary
   ↓
FastAPI
   ↓
Client
```

The actual implementation depends on the AI provider being used.

---

# Architecture

The project follows a simple API architecture:

```text
                    ┌─────────────────┐
                    │      Client     │
                    │ Web / Mobile    │
                    └────────┬────────┘
                             │
                             │ HTTP Request
                             ▼
                    ┌─────────────────┐
                    │     FastAPI     │
                    │   REST API      │
                    └────────┬────────┘
                             │
                             ▼
                    ┌─────────────────┐
                    │  Validation     │
                    │   Pydantic      │
                    └────────┬────────┘
                             │
                             ▼
                    ┌─────────────────┐
                    │ Summarization   │
                    │   AI / NLP      │
                    └────────┬────────┘
                             │
                             ▼
                    ┌─────────────────┐
                    │     JSON        │
                    │    Response     │
                    └─────────────────┘
```

---

# Development Mode

For development, use:

```bash
uvicorn app.main:app --reload
```

For a specific host and port:

```bash
uvicorn app.main:app --host 0.0.0.0 --port 8000
```

---

# Production Considerations

Before deploying the application to production, consider:

* Proper environment variable management
* API authentication
* Rate limiting
* Request size limits
* Logging
* Error monitoring
* Model performance
* Memory usage
* HTTPS
* Input validation
* Secure API key management

---

# Performance Considerations

Text summarization can require significant computational resources, especially when using large local AI models.

Performance can depend on:

* Input text length
* Model size
* CPU/GPU availability
* Number of simultaneous requests
* External API response time
* Maximum generated summary length

For large-scale applications, model selection and resource management become important.

---

# Future Improvements

Possible improvements for future versions include:

* Add a web-based frontend
* Add user authentication
* Add summary length controls
* Support multiple languages
* Add document upload support
* Support PDF files
* Support `.txt` files
* Add summary history
* Add database storage
* Add API rate limiting
* Add automated tests
* Add Docker support
* Deploy the application to the cloud
* Add monitoring and logging

---

# Learning Objectives

This project is useful for learning:

* Python backend development
* FastAPI fundamentals
* REST API development
* HTTP methods
* JSON requests and responses
* Pydantic validation
* Uvicorn
* API documentation
* NLP fundamentals
* Transformer models
* LLM integration
* Environment variables
* Error handling
* Backend project structure
* API testing
* Deployment concepts

---

# Troubleshooting

## `uvicorn` is not recognized

Try:

```bash
python -m uvicorn app.main:app --reload
```

---

## Module Not Found Error

Make sure your virtual environment is activated:

```bash
venv\Scripts\activate
```

Then reinstall dependencies:

```bash
pip install -r requirements.txt
```

---

## Port Already in Use

Run the application on another port:

```bash
uvicorn app.main:app --reload --port 8001
```

Then open:

```text
http://127.0.0.1:8001
```

---

## Model Takes Too Long

Large NLP models can require considerable processing time.

Consider:

* Using a smaller model
* Reducing input length
* Using a GPU
* Using an optimized inference setup
* Using an external model API

---
