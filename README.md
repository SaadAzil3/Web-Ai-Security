# Web & AI Security — My Learning Journey

This repository is where I document and share my learning journey in Web and AI Security (including AI Red Teaming). Every day I'll post what I learned here: scripts I build, vulnerabilities I exploit, and systems I secure.

But first, I need to sharpen my existing skills and, of course, learn new ones. Here's my plan.

## Repository Structure

```
.
├── scripts/            # Security tools and automation I write (scanners, fuzzers, parsers)
├── exploits/           # Proof-of-concept exploits (HTB, labs, my own vulnerable apps)
├── vulnerable-apps/    # Apps built deliberately vulnerable to attack them (e.g. VulnBot)
└── secure-apps/        # Hardened versions of those apps, using the same folder names
```

Write-ups and explanations go on my blog. Each Daily Log entry links to the related post.

## Main Project: VulnBot

**VulnBot** is a chat app with an LLM assistant that has tools (read notes, fetch URLs, send emails) and a RAG knowledge base. I'll build it deliberately vulnerable, attack it, harden it, then publish both versions along with a pentest-style report.

**Stack:** FastAPI + PostgreSQL (pgvector) + React + Ollama + Docker Compose

**Phases:**

1. Backend with auth and database
2. LLM chat endpoint with streaming
3. Tools and RAG
4. Break it (prompt injection, indirect injection, insecure output handling, excessive agency, RAG poisoning, plus classic web bugs)
5. Harden it and re-test
6. Write the report and publish both versions on GitHub

## Skills I Need

**Python, backend, and Docker**

- Python fundamentals: functions, classes, type hints, virtual environments, async/await
- FastAPI: routing, dependency injection, Pydantic models
- SQL and PostgreSQL: queries, joins, indexes
- SQLAlchemy and Alembic: ORM and migrations
- REST API design, HTTP, and status codes
- Auth: password hashing (argon2/bcrypt), JWT, sessions, cookies
- Docker: Dockerfiles, images, containers, volumes, and Docker Compose for multi-service apps

**Frontend (keep it basic — I will use AI for this :) )**

- HTML, CSS, and JavaScript fundamentals
- `fetch()` and handling streamed responses
- React basics: components, state, hooks (TypeScript is optional at first)

**AI and ML**

- How LLMs work at a high level: tokens, context window, system prompts, temperature
- Running models locally with Ollama
- Calling LLM APIs, including streaming
- Embeddings and vector search (pgvector), RAG basics
- Tool calling / function calling
- ML basics: train a simple classifier with scikit-learn or PyTorch once, so adversarial ML makes sense later

**Engineering habits**

- Git and GitHub (branches, tags, pull requests)
- pytest for testing
- GitHub Actions for CI
- Linting with ruff, environment variables for secrets
- Reading documentation and debugging

**Security (where CPTS and my HTB path come in)**

- Web vulnerabilities: SQLi, IDOR, XSS, SSRF, broken auth
- OWASP Top 10 for LLM Applications and the OWASP Agentic Top 10
- Prompt injection (direct and indirect), jailbreaks
- Insecure output handling, excessive agency, RAG/data poisoning
- Threat modeling: data flow diagrams, trust boundaries
- Defensive controls: input/output filtering, least-privilege tools, human confirmation, rate limiting, logging

**Reporting**

- Pentest-style writing: finding, impact, reproduction, fix, severity
- Mapping findings to OWASP and MITRE ATLAS IDs
- Clear READMEs and diagrams

## Learning Order

1. Python + FastAPI + SQL + Docker (weeks 1–3)
2. Git, auth, Docker Compose (weeks 3–4)
3. LLMs, Ollama, embeddings, RAG (weeks 4–6)
4. React basics, only what I need for the chat UI (week 6)
5. Security testing and hardening (weeks 7–10)
6. Report and publish

I'll learn each skill by using it in the project, not in isolation.

## The Stack

| Layer        | Pick                                                         | Why                                                                                                             |
| ------------ | ------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------- |
| Backend      | **FastAPI**                                                  | Async (needed for streaming LLM responses), automatic request validation with Pydantic, auto-generated API docs |
| Frontend     | **React or Next.js** (TypeScript)                            | Standard for chat UIs, handles streaming and tool-call display well                                             |
| Database     | **PostgreSQL** + SQLAlchemy + Alembic migrations             | What real apps use; SQLite is fine only for prototyping                                                         |
| Vector store | **pgvector** (Postgres extension)                            | One database for everything, and RAG poisoning becomes easy to demo                                             |
| Auth         | **JWT** or session cookies, hashed passwords (argon2/bcrypt) | Standard API auth, and a good attack surface to test                                                            |
| LLM          | **Ollama** locally for dev, a hosted API for comparison      | Free to iterate on, no rate limits during testing                                                               |
| Packaging    | **Docker Compose**                                           | One command starts everything; also keeps the vulnerable lab safe and reproducible                              |
| Testing      | **pytest**                                                   | Shows engineering discipline                                                                                    |
| CI           | **GitHub Actions**                                           | Runs tests on every push; recruiters notice this                                                                |

## Hack The Box Journey

Right now I'm still learning penetration testing on HTB Academy and doing CTFs. I'm going to complete the CPTS and CWES paths. After that, I'll sharpen my skills by practicing what I've learned, while diving deeper into advanced topics at the same time.

## Daily Log

| Date | What I did | Type | Blog |
| ---- | ---------- | ---- | ---- |
|      |            |      |      |

**Type:** `script` · `exploit` · `vuln-app` · `secure-app` · `htb` · `learning`
