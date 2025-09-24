# 📘 Lecture 2: FastAPI Introduction & Setup

**Purpose:** Beginner → Intermediate knowledge of FastAPI for developers, ML engineers, and API builders  
**Format:** Theory + Hands-on Practical Example  
**Source:** Based on Ritesh's FastAPI Introduction video

---

## 📑 Table of Contents
1. [Introduction to FastAPI and Its Core Libraries](#introduction-to-fastapi-and-its-core-libraries)
2. [Core Philosophy Behind FastAPI](#core-philosophy-behind-fastapi-why-it-was-created)
3. [ASGI vs WSGI Protocols](#comparison-of-asgi-fastapi-vs-wsgi-flask-protocols-and-their-impact-on-performance)
4. [Async/Await in FastAPI](#how-asgi-enables-fastapi-to-handle-concurrent-requests-with-asyncawait)
5. [Developer Productivity Features](#fastapis-second-philosophy-fast-to-code-with-automatic-validation-and-documentation)
6. [Practical Setup & Hello World API](#practical-fastapi-setup-and-hello-world-api-example)
7. [Interactive Documentation](#interactive-auto-generated-documentation-in-fastapi)
8. [Key Insights](#key-insights)
9. [Outline](#outline)
10. [Keywords](#keywords)
11. [FAQ](#faq)

---

## Introduction to FastAPI and Its Core Libraries
The video begins with a recap on why learning FastAPI is important for data science, AI, and ML engineers.  
FastAPI is a **modern, high-performance Python web framework** built on two core libraries:
- **Starlette** – Handles HTTP requests/responses (ASGI-based).
- **Pydantic** – Validates incoming data, ensuring it matches expected formats.

This combination allows FastAPI to quickly receive client requests, validate data, and return responses efficiently.

---

## Core Philosophy Behind FastAPI: Why It Was Created
FastAPI was created to solve:
1. **Performance issues** in older frameworks like Flask (slow under heavy load).
2. **Developer productivity problems** due to boilerplate-heavy code.

FastAPI’s design philosophy:
- **Fast to run** – handle concurrent users with minimal latency.
- **Fast to code** – write fewer lines of code to build production APIs.

---

## Comparison of ASGI (FastAPI) vs WSGI (Flask) Protocols and Their Impact on Performance
- **WSGI (Flask):** Synchronous, blocking model → processes one request at a time. Uses Gunicorn + Werkzeug.  
- **ASGI (FastAPI):** Asynchronous model → handles multiple requests concurrently using `async` / `await`. Uses Uvicorn + Starlette.  

**Analogy:**  
Flask is like a waiter taking one order at a time and waiting until it's ready before taking the next.  
FastAPI’s waiter takes multiple orders and manages them simultaneously.

---

## How ASGI Enables FastAPI to Handle Concurrent Requests with Async/Await
- Supports **asynchronous programming** with `async`/`await`.
- Non-blocking execution: while one request waits (e.g., ML model query), other requests are processed.
- Improves scalability and latency under heavy load.

---

## FastAPI’s Second Philosophy: Fast to Code with Automatic Validation and Documentation
1. **Automatic Input Validation:** Pydantic ensures request data matches expected data types.
2. **Auto-Generated Interactive Docs:** Built-in Swagger UI (`/docs`) for testing APIs directly.
3. **Seamless Integrations:** Works with ML libraries, databases (SQLAlchemy), OAuth, Docker, Kubernetes, etc.

---

## Practical FastAPI Setup and Hello World API Example
Steps:
- Create a project folder and open in VS Code.
- Create/activate a virtual environment.
- Install dependencies: `fastapi` and `uvicorn`.
- Write `main.py`:
```python
from fastapi import FastAPI

app = FastAPI()

@app.get("/")
def home():
    return {"message": "Hello World"}

@app.get("/about")
def about():
    return {"info": "This is Campus X"}
