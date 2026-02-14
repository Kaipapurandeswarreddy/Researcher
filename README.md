# 🧠 AI Researcher

<div align="center">
  <img src="image/image.png" alt="AI Researcher Logo" width="200" />
  
  **An autonomous AI-powered research agent that conducts comprehensive online research on any topic.**

  [![Python 3.10+](https://img.shields.io/badge/Python-3.10%2B-blue?logo=python&logoColor=white)](https://www.python.org/)
  [![Next.js](https://img.shields.io/badge/Next.js-14-black?logo=next.js)](https://nextjs.org/)
  [![FastAPI](https://img.shields.io/badge/FastAPI-0.104+-009688?logo=fastapi)](https://fastapi.tiangolo.com/)
  [![Gemini](https://img.shields.io/badge/Gemini-2.5_Flash-4285F4?logo=google&logoColor=white)](https://ai.google.dev/)
  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
</div>

---

## ✨ Features

- **🔍 Autonomous Research** — Generates detailed, factual, and unbiased research reports
- **🤖 Multi-Agent System** — Specialized agents (Academic, Business, Finance, Security, Travel) collaborate on complex research tasks
- **🌐 Multi-Source** — Searches the web, academic papers (ArXiv), local documents, and more
- **📊 Multiple Report Types** — Research reports, detailed reports, resource reports, subtopic reports
- **💬 Chat with Reports** — Ask follow-up questions about generated research reports
- **📤 Export Formats** — Download reports as PDF, DOCX, or Markdown
- **🔌 MCP Support** — Model Context Protocol integration for extended tool capabilities
- **🎨 Two Frontend Options** — Lightweight static HTML or full-featured Next.js app

---

## 🏗️ Architecture

```
gpt-researcher/
├── main.py                  # Application entry point
├── backend/
│   └── server/
│       ├── app.py           # FastAPI server (REST + WebSocket)
│       ├── server_utils.py  # WebSocket handler & research agent runner
│       └── report_store.py  # JSON-based report persistence
├── gpt_researcher/          # Core research engine
│   ├── agent/               # Research agent logic
│   ├── llm_provider/        # LLM provider abstraction (Gemini, OpenAI, etc.)
│   ├── scraper/             # Web scraping utilities
│   ├── memory/              # Embedding & vector store
│   └── utils/               # Enums, validators, costs
├── multi_agents/            # Multi-agent orchestration
├── frontend/
│   ├── index.html           # Static frontend (served by FastAPI)
│   ├── styles.css
│   ├── scripts.js
│   └── nextjs/              # Next.js frontend (React + TypeScript)
└── requirements.txt
```

---

## 🚀 Quick Start

### Prerequisites

- **Python 3.10+**
- **Node.js 18+** (for Next.js frontend)
- **API Keys**: [Gemini API](https://ai.google.dev/) + [Tavily API](https://tavily.com/)

### 1. Clone the Repository

```bash
git clone https://github.com/Kaipapurandeswarreddy/Researcher.git
cd Researcher
```

### 2. Install Python Dependencies

```bash
pip install -r requirements.txt
```

### 3. Configure Environment

Create a `.env` file in the project root:

```env
# Search API
TAVILY_API_KEY=your_tavily_api_key

# Google Gemini
GOOGLE_API_KEY=your_google_api_key
FAST_LLM=google_genai:gemini-2.5-flash
SMART_LLM=google_genai:gemini-2.5-flash
EMBEDDING=google_genai:text-embedding-004

# Document path (optional)
DOC_PATH=./my-docs
```

### 4. Start the Backend

```bash
python main.py
```

The backend will start at **http://localhost:8000** and serve the static frontend automatically.

### 5. (Optional) Start the Next.js Frontend

For the full-featured React frontend:

```bash
cd frontend/nextjs
npm install --legacy-peer-deps
npm run dev
```

The Next.js app will start at **http://localhost:3000**, connecting to the backend on port 8000.

---

## 🖥️ Frontends

| Feature | Static (HTML) | Next.js |
|---------|:---:|:---:|
| **URL** | `localhost:8000` | `localhost:3000` |
| **Setup** | None (auto-served) | `npm install && npm run dev` |
| **Real-time streaming** | ✅ | ✅ |
| **Research history** | ✅ | ✅ |
| **Chat with reports** | ✅ | ✅ |
| **File upload** | ✅ | ✅ |
| **Mobile responsive** | ⚠️ Basic | ✅ Full |
| **Settings panel** | ✅ | ✅ Advanced |
| **Multi-agent view** | ❌ | ✅ |
| **SEO optimized** | ❌ | ✅ |

---

## 🔧 Supported LLM Providers

| Provider | Config Prefix |
|----------|---------------|
| **Google Gemini** | `google_genai:gemini-2.5-flash` |
| **OpenAI** | `openai:gpt-4o` |
| **Anthropic** | `anthropic:claude-3-sonnet` |
| **Ollama (Local)** | `ollama:llama3` |
| **Azure OpenAI** | `azure_openai:gpt-4` |
| **Together AI** | `together:meta-llama/Llama-3` |
| **Groq** | `groq:llama3-70b` |
| **DeepSeek** | `deepseek:deepseek-chat` |

Change the `FAST_LLM` and `SMART_LLM` values in `.env` to switch providers.

---

## 📡 API Endpoints

| Endpoint | Method | Description |
|----------|--------|-------------|
| `/` | GET | Serve static frontend |
| `/ws` | WebSocket | Real-time research streaming |
| `/report/` | POST | Generate a research report |
| `/api/reports` | GET | List all saved reports |
| `/api/reports/{id}` | GET/PUT/DELETE | CRUD for individual reports |
| `/api/reports/{id}/chat` | GET/POST | Chat with a specific report |
| `/chat` | POST | General chat endpoint |
| `/files/` | GET | List uploaded documents |
| `/upload/` | POST | Upload a document |
| `/files/{filename}` | DELETE | Delete a document |
| `/api/multi_agents` | POST | Run multi-agent research |

Full API docs available at **http://localhost:8000/docs** (Swagger UI).

---

## 📝 Report Types

| Type | Description |
|------|-------------|
| **Research Report** | Comprehensive research on a topic (~2000 words) |
| **Detailed Report** | In-depth report with subtopics (~3000+ words) |
| **Resource Report** | Curated list of relevant resources and sources |
| **Subtopic Report** | Focused report on a specific subtopic |
| **Multi-Agent Report** | Collaborative report using specialized agents |

---

## 🎨 Research Agents

Each agent specializes in a domain with tailored prompts and search strategies:

| Agent | Specialty |
|-------|-----------|
| 🎓 **Academic Research** | Scholarly papers, citations, peer-reviewed sources |
| 📈 **Business Analyst** | Market analysis, industry trends, competitive intelligence |
| 💰 **Finance** | Financial data, market reports, economic analysis |
| 🔒 **Computer Security** | Cybersecurity, vulnerabilities, threat analysis |
| ✈️ **Travel** | Destinations, logistics, cultural information |
| 🤖 **Auto Agent** | General-purpose research (default) |
| 🧮 **Math** | Mathematical concepts, proofs, calculations |

---

## 🤝 Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

---

## 📄 License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.

---

## 🙏 Acknowledgments

- Built on [GPT Researcher](https://github.com/assafelovic/gpt-researcher) by Assaf Elovic
- Powered by [Google Gemini](https://ai.google.dev/), [LangChain](https://www.langchain.com/), and [Tavily](https://tavily.com/)

---

<div align="center">
  <b>Made with ❤️ by <a href="https://github.com/Kaipapurandeswarreddy">Kaipapurandeswarreddy</a></b>
</div>
