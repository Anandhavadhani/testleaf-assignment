# QA Bot - Full Stack AI Question Answering System

A stateless, single-server AI-powered Q&A web app. Users upload documents (PDF, DOCX, CSV, TXT), ask questions, and receive AI-generated answers.

## Tech Stack
- **Backend**: Node.js + Express + TypeScript + LangChain
- **Frontend**: HTML5 + Vanilla JavaScript
- **LLM Providers**: OpenAI, Anthropic, Groq (configurable via environment variable)
- **File Parsers**: pdf-parse, mammoth, csv-parser

## Quick Start

### Prerequisites
- Node.js 18+
- npm

### Installation

```bash
# Backend setup
cd backend
npm install
cp .env.example .env
# Edit .env with your API keys

# Development
npm run dev

# Production
npm run build
npm start
```

### CI / Deployment

Add your `OPENAI_API_KEY` (or provider-specific key) to your CI/hosting secret store. Example providers:

- GitHub Actions: Repository Settings → Secrets → Actions → `OPENAI_API_KEY`
- Vercel / Netlify / Heroku: set config/env vars in project settings

We include a sample GitHub Actions workflow at `.github/workflows/ci.yml` that expects the `OPENAI_API_KEY` secret.

### API Endpoints
- `GET /` - Serve UI
- `GET /health` - Health check with model info
- `POST /api/search/document` - Query with text or file path
- `POST /api/search/upload` - Upload files and query

See `docs/API.md` for full documentation.

Note: The server accepts both `/api/search/*` and legacy `/search/*` endpoints for backward compatibility. Prefer `/api/search/*` for new integrations.

## Project Structure
```
qa-bot/
├── backend/          # Node.js + Express backend
├── frontend/         # HTML5 + Vanilla JS frontend
└── docs/             # Complete documentation
```

## Documentation
- `docs/ARCHITECTURE.md` - System design
- `docs/API.md` - API reference
- `docs/deployment.md` - Setup guide
- `docs/IMPLEMENTATION_PHASES.md` - Implementation roadmap

## Status
🚀 **Phase 1: Setup** - COMPLETE & TESTING
