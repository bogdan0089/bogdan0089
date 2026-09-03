# 👋 Hi, I'm Bohdan Kaliushyk

### Python Backend Developer | AI / LLM Integration

![Python](https://img.shields.io/badge/Python-3.11-3776AB?logo=python&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-async-009688?logo=fastapi&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-336791?logo=postgresql&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-DC382D?logo=redis&logoColor=white)
![Celery](https://img.shields.io/badge/Celery-37814A?logo=celery&logoColor=white)
![RabbitMQ](https://img.shields.io/badge/RabbitMQ-FF6600?logo=rabbitmq&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?logo=docker&logoColor=white)
![AWS EC2](https://img.shields.io/badge/AWS-EC2-FF9900?logo=amazonaws&logoColor=white)
![Claude API](https://img.shields.io/badge/Anthropic-Claude%20API-D97757?logo=anthropic&logoColor=white)
![MCP](https://img.shields.io/badge/MCP-server-6E56CF)
![Microservices](https://img.shields.io/badge/Microservices-4B5563)

Building production-grade async backend systems. Clean Architecture. Real deployments. AI features that ship, not demos.

---

## 🚀 About Me

- 💼 2+ years of commercial experience building and shipping production async backend systems on FastAPI
- 🏭 Currently backend engineer on a multi-module call-center CRM at **UnderTalk**, built from scratch — configurable discipline rules engine, operator and client analytics computed per connected CRM, telephony and Viber integrations, on Celery/RabbitMQ/Redis microservices
- 🔌 Shipped a production **MCP (Model Context Protocol) server** — 38 tools that let Claude configure live payroll rules from chat, with OAuth 2.1, a gated write path that refuses to save an unpriced config, and concurrency-safe session state
- 🤖 Built the **in-CRM AI copilot** behind the same tools — an Anthropic tool-use loop that self-corrects on tool errors and turns plain language into a validated payroll configuration
- 🧩 At **SECL Group**, worked across backend modules (auth, client records, notifications, reporting) — including zero-downtime Alembic migrations against a live production database and replacing polling with a WebSocket push layer
- ☁️ Independently deployed a full e-commerce platform on **AWS EC2** — from architecture to running server, with CI/CD via GitHub Actions
- 🧪 I write tests for side projects too — 231 on Trend Radar, 107 on the Telegram bot, 65 on the shop
- 🌍 Poland | Polish C2 | English B2 | Ukrainian native | German A1
- 📡 Open to remote and hybrid Python Backend / AI Engineer roles

---

## 🛠️ Tech Stack

**Backend:** FastAPI · Django · asyncio · WebSockets · Celery · RabbitMQ · REST API

**AI & LLM:** Anthropic Claude API (tool use, structured outputs) · MCP server development · agentic tool-calling loops with guardrails · RAG pipelines · LangChain · HuggingFace embeddings · pgvector · ChromaDB · Groq API · LLaMA 3.3-70b · token cost optimization · provider fallback

**Architecture:** Microservices · Clean Architecture · Unit of Work · Repository pattern · rules engines · 3-layer (Router → Service → Repository)

**Databases:** PostgreSQL · pgvector · Redis · SQLite · SQLAlchemy 1.4 & 2.0 (async) · Alembic · ChromaDB

**Integrations:** Telephony (Binotel) · external CRM sync · Viber · Google Calendar · Stripe · webhooks · polling APIs · message queues · idempotent syncs · cross-system identity mapping

**Auth:** JWT (access + refresh) · bcrypt · OAuth2 / OAuth 2.1 · Auth0 · RBAC · Pydantic V2

**Frontend:** Vue.js · Next.js · React · TypeScript · JavaScript · HTML · CSS

**Testing:** pytest · pytest-asyncio · Postman · Swagger / OpenAPI · ruff

**DevOps:** Docker · Docker Compose · AWS EC2 · GitHub Actions · Nginx · Linux

**Tools:** Git · Jira · Claude Code · Cursor

---

## 🔥 Featured Projects

### 📡 Trend Radar — Amazon product scoring pipeline

![Tests](https://img.shields.io/badge/tests-231-brightgreen) ![CI](https://img.shields.io/badge/CI-ruff%20%2B%20pytest%20%2B%20compose-blue)

Scrapes Amazon best sellers with Playwright, reads demand dynamics on Google Trends, and scores each product 0–100 with written reasoning.

| Feature | Details |
|---|---|
| 🧠 Scoring | Five LLM providers behind one adapter — a missing key, timeout, 429 or invalid JSON moves that product onto a deterministic weighted formula and logs why. A product never comes back unscored |
| ⏱️ Run safety | A time budget stops the run outliving the Celery soft limit; after three failures in a row a provider is treated as down for the rest of the run |
| 🕸️ Scrapers | Split into a pure HTML-to-data function and a thin Chromium driver — parsers tested against saved snapshots in milliseconds, a layout change means fixing one function |
| 🚨 Honest failure | A blocked scrape falls back to a bundled snapshot and the run is marked **partial**, never success — a dead scraper stays visible |
| 🧪 Testing | 231 tests against real Postgres (the code relies on JSONB, ARRAY, DISTINCT ON) |
| 🔁 CI | ruff, full suite, alembic upgrade/downgrade round trip with drift check, seed run twice to prove idempotency, frontend build, Docker Compose smoke test |
| 🖥️ Frontend | Vue 3 SPA behind nginx with JWT auth — every pipeline stage writes counters, so the dashboard shows real progress instead of a spinner |

**Repo:** [github.com/bogdan0089/trend-radar](https://github.com/bogdan0089/trend-radar)

---

### 🛒 FastAPI E-Commerce Platform

![CI](https://img.shields.io/badge/CI-passing-brightgreen) ![CD](https://img.shields.io/badge/CD-auto--deploy-blue) ![Tests](https://img.shields.io/badge/tests-65-brightgreen)

🌐 Live: [bohdan-shop.duckdns.org](https://bohdan-shop.duckdns.org) · Swagger: `/docs`

Production-ready async REST API and storefront — independently built, deployed and maintained on AWS EC2.

| Feature | Details |
|---|---|
| 🏗️ Architecture | Clean Architecture — Router → Service → UoW → Repository → DB |
| 🤖 AI Integration | Groq API (LLaMA 3.3-70b) — recommendations, semantic search, chatbot, description generation |
| 🔐 Auth & Security | JWT access + refresh, bcrypt, RBAC (3 roles), Redis-backed email verification, full password reset flow |
| 💳 Payments | Stripe PaymentIntent + webhooks — pessimistic locking (SELECT FOR UPDATE) on every balance-sensitive operation, so a double click cannot spend the same money twice |
| 🖥️ Storefront | Next.js 16 · React 19 · TypeScript — 13 routes, catalog with search and filters, cart, checkout, five-tab profile, superadmin panel |
| 🔴 Real-time | Admin panel holds a WebSocket open for live order notifications |
| ⚡ Async Tasks | Celery + Redis — background email delivery |
| 🔁 CI/CD | GitHub Actions — 65 tests on every push, auto-deploy to AWS EC2 on merge |
| ☁️ Infrastructure | Docker Compose · AWS EC2 · Nginx · Let's Encrypt SSL |

**Repos:** [backend](https://github.com/bogdan0089/fastapi-ecommerce-backend) · [frontend](https://github.com/bogdan0089/ecommerce-frontend)

---

### 🤖 Djinni Job Bot

![Tests](https://img.shields.io/badge/tests-107-brightgreen)

Telegram bot delivering filtered Djinni.co vacancies by stack, seniority and salary.

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
| 🎯 Grounding | Answers grounded strictly in document content — no hallucinated content |
| 📚 Docs | Documented with Swagger/OpenAPI |

**Repo:** [github.com/bogdan0089/document-rag-api](https://github.com/bogdan0089/document-rag-api)

---

## 💼 Experience

### Full Stack Python Developer @ UnderTalk · *Apr 2026 – Present*

`FastAPI` `PostgreSQL` `SQLAlchemy async` `Celery` `RabbitMQ` `Redis` `Anthropic Claude API` `MCP` `Microservices` `Docker` `Linux` `Vue.js`

Backend engineer on a call-center CRM built from scratch as a set of independent modules over a shared operator/client data layer — operator workspace, discipline control, telephony analytics, shift scheduling and recruiting. I own the full cycle on each module: requirements with the client, technical spec, database schema, implementation, tests, dev-server verification, production deployment and incident handling.

- **Shipped a production MCP (Model Context Protocol) server** — 38 tools that let Claude configure a position's payroll rules directly from chat: read-only schema introspection across all non-sensitive tables, live CRM-screen and metric lookups, draft mutation, validation, salary simulation on real data, and a gated write path. Reused the existing tool executors and validator rather than duplicating domain logic — MCP is a second transport over the same code, deployed from the same image as the API with a different container command.
  
- **Hardened that connector for production** — the write tool refuses to persist unless validation and a money-impact simulation both passed against the current draft; any edit resets the gate, so an agent cannot save a config a human never priced. Per-session draft state in a `WeakKeyDictionary` with a version counter and defensive copies, because MCP dispatches one session's tool calls concurrently. Two-layer auth: OAuth 2.1 with Auth0 as authorization server and the connector as a pure resource server, forwarding the caller's own token downstream so existing backend role checks apply unchanged.
  
- **Built the in-CRM AI copilot** behind the same tool set — an Anthropic tool-use loop (bounded at 12 iterations, tool errors returned to the model so it self-corrects) that turns a plain-language instruction into a validated payroll configuration. Cut per-call token cost by compacting tool results to the fields the model actually needs and making the full breakdown opt-in — the raw simulation table ran to tens of thousands of tokens per call.
  
- **Designed a configurable rules engine** driving automatic discipline violations: three parameterized rule types (count limit, multi-level accumulation threshold, event-in-time-window) with output format derived from the rule type — new thresholds and rules are added as configuration, not new code.
  
- **Built the quality-control and discipline subsystem** (the largest module): a pause-accounting model with six time categories, a violation state machine with values that mature over time (trigger fires immediately, final duration resolves later) and an audit trail on manager decisions — a single source of truth, so the same incident is never editable in two places. Eliminated a class of desynchronization bugs.
  
- **Built operator analytics and client analytics** as separate subsystems, each computed per connected CRM and then aggregated across all of them, on top of an identity-mapping layer that resolves the same operator or client across systems that identify them differently. Client complexity is a weighted coefficient over three normalized metrics, recomputed nightly by cron over two time windows and finalized monthly.
  
- **Integrated multiple external systems** — Binotel telephony (call events, statistics, port-to-operator mapping), an external CRM and order source, and Viber chat for operators (text, photos, files, presence check, MinIO storage). Data flows via webhooks, polling APIs and queues in a microservice layout, with idempotent syncs so retried events never produce duplicates.
  
- Optimized heavy data flows to stay responsive — batched upserts, query profiling, caching and background recomputation; delivered further modules (shift planning, recruiting funnel with break-even and tenure analytics, earnings calculator) on the same architecture.
  
- Wrote automated tests, verified releases on the dev server and deployed to production; maintained and refactored existing code, fixed bugs and resolved incidents in production, running dev and prod servers on Linux.
  
- Worked directly with the client and across departments — joined requirement calls, wrote and maintained technical specifications per module, managed tasks in Jira, and drove design decisions through review and iteration.
  
- Build and maintain the Vue.js frontend (HTML, CSS) where a module needs it.

### Python Backend Developer @ SECL Group · *Jan 2025 – Mar 2026*

`FastAPI` `PostgreSQL` `Redis` `WebSockets` `SQLAlchemy async` `Alembic` `Docker` `Pydantic V2`

- **Shipped Alembic migrations against a live production database with zero downtime**, and profiled and rewrote the slowest queries on the highest-traffic endpoints.
  
- **Replaced browser-side polling of our own API with a WebSocket layer** for real-time push notifications, and layered Redis caching onto hot endpoints — cut redundant requests and reduced server load.
  
- **Tracked down and fixed recurring production incidents** in JWT auth and async session handling — session lifecycle, transaction boundaries and data consistency under concurrent load.
  
- Worked across several backend modules — authentication, client records, notifications and reporting — implementing endpoints, data access and background logic, and taking each one through review to release.
  
- Integrated third-party services over REST APIs, including Google Calendar (OAuth 2.0, event synchronization).
  
- Ran Docker-based production deployments on Linux (Ubuntu) end to end, inside a cross-functional team with a strict PR-review culture — every pull request reviewed and tracked in Jira.

---

## 📫 Contact Me

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?logo=linkedin&logoColor=white)](https://linkedin.com/in/bohdan-kaliushyk)
[![Gmail](https://img.shields.io/badge/Gmail-D14836?logo=gmail&logoColor=white)](mailto:bohdankaliushyk@gmail.com)
[![Live Project](https://img.shields.io/badge/Live-bohdan--shop.duckdns.org-blue)](https://bohdan-shop.duckdns.org)

⚡ Open to remote and hybrid Python Backend / AI Engineer opportunities
