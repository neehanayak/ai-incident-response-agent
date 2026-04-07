# 🚨 AI Incident Response Agent

A production-ready AI agent that helps engineering teams investigate and respond to production incidents by analyzing service logs and runbook documentation using **LangGraph orchestration + Retrieval Augmented Generation (RAG)**.

---

## 🌟 Why this project exists

During incidents, engineers spend valuable time searching logs, dashboards, and runbooks to understand what went wrong.

This system acts as an **AI copilot for incident response**, helping reduce time to diagnose and improve troubleshooting accuracy.

The agent can:

• Analyze service logs and error traces  
• Retrieve relevant runbook documentation  
• Suggest likely root causes  
• Recommend next debugging steps  
• Maintain conversation memory across sessions  

---

## 🏗️ Architecture Overview

High level workflow:

User query or logs  
➡️ LangGraph orchestration  
➡️ RAG pipeline retrieves relevant logs and runbooks from pgvector  
➡️ LLM reasoning with tools and memory  
➡️ Structured incident response  

Core stack:

• **FastAPI** for async API backend  
• **LangGraph** for agent orchestration  
• **PostgreSQL + pgvector** for vector search  
• **OpenAI models** for reasoning and embeddings  
• **Prometheus + Grafana** for monitoring  
• **Docker** for containerization  
• **AWS ready deployment**

---

## 🤖 Key Features

### 🔎 Incident Investigation Agent

• Upload logs or paste incident details  
• Semantic search across runbooks and past incidents  
• Root cause analysis suggestions  
• Recommended debugging steps  
• Conversation memory per user  

---

### 🧠 Retrieval Augmented Generation Pipeline

This project uses a full RAG pipeline to ground responses in real engineering knowledge.

• Log ingestion and chunking pipeline  
• Document ingestion pipeline for runbooks  
• Embedding generation using OpenAI models  
• Vector similarity search with PostgreSQL + pgvector  
• Context injection into LLM prompts for grounded reasoning

---

### ⚙️ Production Backend

• FastAPI async REST API  
• JWT authentication and session management  
• Rate limiting and input validation  
• Structured logging with request context  
• Streaming responses support  

---

### 📊 Observability & Evaluation

• Prometheus metrics + Grafana dashboards  
• Langfuse LLM tracing  
• Automated evaluation framework  
• JSON reports with success metrics  

---

### ⚡ Performance & Reliability

• Docker + Docker Compose setup  
• Redis caching support  
• Automatic retry logic for LLM calls  
• Async database connection pooling  

---

## 💡 Example Use Cases

Example queries:

• “Here are logs from the payment service. Why is checkout failing?”  
• “We are seeing repeated 503 errors. What could be wrong?”  
• “Summarize this incident and suggest next steps.”

The agent retrieves relevant runbook sections and produces structured troubleshooting guidance.

---

## 📂 Project Structure

```
app/
 ├── api/                # REST API endpoints (auth + chat)
 ├── core/langgraph/     # LangGraph agent workflow & tools
 ├── services/
 │     ├── database.py   # PostgreSQL + pgvector integration
 │     └── llm.py        # LLM + embedding service
 ├── prompts/            # System prompts & RAG instructions

scripts/                 # Log + runbook ingestion pipeline (RAG indexing)
evals/                   # Evaluation framework for agent accuracy
prometheus/              # Metrics configuration
grafana/                 # Monitoring dashboards
```

---

## 🚀 Getting Started

### Prerequisites

• Python 3.13  
• PostgreSQL  
• Docker + Docker Compose  
• OpenAI API Key  

---

### 🔧 Local Setup

Clone the repo

```
git clone https://github.com/your-username/ai-incident-response-agent.git
cd ai-incident-response-agent
```

Install dependencies

```
uv sync
```

Create environment file

```
cp .env.example .env.development
```

Add required variables

```
OPENAI_API_KEY=your_key
POSTGRES_HOST=localhost
POSTGRES_DB=incident_agent
SECRET_KEY=your_secret
```

Run locally

```
make dev
```

Swagger docs available at  
http://localhost:8000/docs

---

## 🐳 Run with Docker

```
make docker-build-env ENV=development
make docker-run-env ENV=development
```

Monitoring dashboards

Prometheus → http://localhost:9090  
Grafana → http://localhost:3000  

---

## 🧪 Evaluation

Run automated evaluation

```
make eval-quick ENV=development
```

Reports generated in:

```
evals/reports/
```

Metrics include success rate and response quality.

---

## 🔮 Future Improvements

• Cloud log ingestion integrations  
• Slack and email alerting support  
• Larger evaluation datasets  
• Advanced multi-step agent workflows  

---

## 🙌 Acknowledgements

Built using a production FastAPI + LangGraph template and extended with a real-world incident response use case.
