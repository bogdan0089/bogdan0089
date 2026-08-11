# 👋 Hi, I'm Bohdan Kaliushyk

### Python Backend Developer

![Python](https://img.shields.io/badge/Python-3.11-3776AB?logo=python&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-async-009688?logo=fastapi&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-336791?logo=postgresql&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-DC382D?logo=redis&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?logo=docker&logoColor=white)
![AWS EC2](https://img.shields.io/badge/AWS-EC2-FF9900?logo=amazonaws&logoColor=white)
![Celery](https://img.shields.io/badge/Celery-37814A?logo=celery&logoColor=white)
![RabbitMQ](https://img.shields.io/badge/RabbitMQ-FF6600?logo=rabbitmq&logoColor=white)
![Microservices](https://img.shields.io/badge/Microservices-4B5563)

Building production-grade async backend systems. Clean Architecture. Real deployments. AI-powered features that ship, not demos.

---

## 🚀 About Me

- 💼 2+ years of commercial experience building and shipping production async backend systems on FastAPI
- 🏭 Currently backend engineer on a call-center CRM at **UnderTalk**, built from scratch — a configurable discipline rules engine, weighted client-complexity analytics, telephony + Viber integrations, on Celery/RabbitMQ/Redis microservices
- 🧩 Previously owned 5 production modules (auth, RBAC, notifications, reporting) end-to-end at **SECL Group** — including zero-downtime schema migrations on a live database
- 🤖 Hands-on AI/LLM integration: built a production **RAG pipeline** (LangChain + ChromaDB + HuggingFace) and shipped an **LLM-powered e-commerce backend** live on AWS (Groq API, LLaMA 3.3-70b)
- ☁️ Independently deployed a full e-commerce backend on **AWS EC2** — from architecture to running server, with CI/CD via GitHub Actions
- 🧵 Built a Telegram job bot with 107 automated tests and a fault-isolated daily digest pipeline
- 🌍 Based in Warsaw, Poland | Polish C2 | English B2 | Ukrainian native | German A1
- 📡 Open to remote and hybrid Python Backend roles

---

## 🛠️ Tech Stack

**Backend:** FastAPI · Django · asyncio · WebSockets · Celery · RabbitMQ · REST API

**Architecture:** 3-layer (Router → Service → Repository) · Clean Architecture · Unit of Work · Microservices

**Databases:** PostgreSQL · Redis · SQLite · SQLAlchemy 1.4 & 2.0 (async) · Alembic · ChromaDB

**AI & LLM:** Groq API · LLaMA 3.3-70b · RAG pipelines · LangChain · HuggingFace embeddings · Anthropic Claude API · prompt engineering · agentic coding

**Auth:** JWT (access + refresh) · bcrypt · OAuth2 · Auth0 · RBAC · Pydantic V2 · Stripe API

**Frontend:** Vue.js · Next.js · JavaScript · HTML · CSS

**Testing:** pytest · pytest-asyncio · Postman · Swagger / OpenAPI

**DevOps:** Docker · Docker Compose · AWS EC2 · GitHub Actions · Nginx · Linux

**Tools:** Git · Jira · Claude Code 

---

## 🔥 Featured Projects

### 🛒 FastAPI E-Commerce Backend
![CI](https://img.shields.io/badge/CI-passing-brightgreen) ![CD](https://img.shields.io/badge/CD-auto--deploy-blue)

🌐 Live demo: [bohdan-shop.duckdns.org](https://bohdan-shop.duckdns.org) · Swagger: `/docs`

Production-ready async REST API — independently built, deployed and maintained on AWS EC2.

| Feature | Details |
|---|---|
| 🏗️ Architecture | Clean Architecture — Router → Service → UoW → Repository → DB |
| 🤖 AI Integration | Groq API (LLaMA 3.3-70b) — recommendations, semantic search, chatbot, description generation |
| 🔐 Auth & Security | JWT access + refresh tokens, bcrypt, RBAC (3 roles), email verification via Redis |
| 💳 Payments | Stripe PaymentIntent + webhook — automatic balance top-up on payment success |
| ⚡ Async Tasks | Celery + Redis — background email delivery, order status notifications |
| 🔴 Real-time | WebSocket broadcasts to admins on checkout events |
| 🔒 DB Safety | Pessimistic locking (SELECT FOR UPDATE) on all balance operations |
| 🔁 CI/CD | GitHub Actions — 65 tests on every push, auto-deploy to AWS EC2 on merge |
| 🧪 Testing | pytest integration tests with NullPool + FakeRedis async setup |
| ☁️ Infrastructure | Docker Compose · AWS EC2 · Nginx · Let's Encrypt SSL |

**Repo:** [github.com/bogdan0089/fastapi-ecommerce-backend](https://github.com/bogdan0089/fastapi-ecommerce-backend)

---

### 🤖 Djinni Job Bot

Telegram bot delivering filtered [Djinni.co](https://djinni.co) vacancies by stack, seniority and salary.

| Feature | Details |
|---|---|
| 🏗️ Architecture | Layered (handlers → services → repository) with DI middlewares (per-update DB session + service injection, anti-flood) |
| 📬 Delivery | Timezone-aware daily digest + on-demand search sharing one delivery-history dedup engine — a vacancy is never sent twice |
| 🔒 Transaction safety | Repositories never commit — the middleware owns the transaction, so vacancies are marked sent only after successful delivery |
| 🛡️ Fault isolation | A blocked user or source outage never aborts the run; blocked users auto-unsubscribe |
| 🧪 Testing | 107 pytest tests (in-memory SQLite, no network), ruff |
| 🔁 CI/CD | GitHub Actions CI on Python 3.11 / 3.12 |

**Repo:** [github.com/bogdan0089/djinni-job-bot](https://github.com/bogdan0089/djinni-job-bot)

---

### 📄 Document RAG API

Full RAG pipeline with responses grounded strictly in document content.

| Feature | Details |
|---|---|
| 🏗️ Architecture | Layered (api → ingestion / retrieval / llm services → core), each layer independently testable |
| 🤖 Pipeline | PDF upload → LangChain chunking → local HuggingFace embeddings → ChromaDB vector storage → LLM answer generation |
| 🎯 Grounding | Responses grounded strictly in document content — no hallucinated answers |
| 📚 Docs | Documented with Swagger/OpenAPI |

**Repo:** [github.com/bogdan0089/document-rag-api](https://github.com/bogdan0089/document-rag-api)

---

### 🧰 Python Toolbox

A growing collection of small, self-contained Python CLI tools.

| Feature | Details |
|---|---|
| 📦 Structure | Each tool lives in its own folder with its own README and `requirements.txt`, runs independently |
| 🧩 Tools | `qr-generator` — generates a QR code from any text or URL via a real CLI (`argparse`) |
| ✅ Quality | Input validated, errors reported clearly instead of crashing |

**Repo:** [github.com/bogdan0089/python-toolbox](https://github.com/bogdan0089/python-toolbox)

---

## 💼 Experience

**Python Backend Developer @ UnderTalk** *(Apr 2026 – Present)*
- Backend engineer on a call-center CRM built from scratch — FastAPI, PostgreSQL, Redis, Celery, RabbitMQ
- Built a configurable discipline rules engine and a weighted client-complexity analytics model
- Integrated Binotel telephony, an external CRM and Viber chat for operators, with media in MinIO
- Also build/maintain the Vue.js frontend where needed

**Python Backend Developer @ SECL Group** *(Jan 2025 – Mar 2026)*
- Production CRM backend — FastAPI, PostgreSQL, Redis, WebSockets, Alembic
- Auth flows, role management, client records, notifications, reporting modules
- Query optimization, async session handling, production incident resolution
- Structured Jira-based code review on every PR

---

## 📫 Contact Me

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?logo=linkedin&logoColor=white)](https://linkedin.com/in/bohdan-kaliushyk)
[![Gmail](https://img.shields.io/badge/Gmail-D14836?logo=gmail&logoColor=white)](mailto:bohdankaliushyk@gmail.com)
[![Live Project](https://img.shields.io/badge/Live-bohdan--shop.duckdns.org-blue)](https://bohdan-shop.duckdns.org)

⚡ Open to remote Python Backend opportunities
