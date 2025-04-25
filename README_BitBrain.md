# 🧠 Bit Brain

Bit Brain is a full-stack, multi-agent Retrieval-Augmented Generation (RAG) assistant designed to bridge the upstream knowledge gap in complex industries. Built with ⚡ FastAPI, 🧱 LangChain, 🧬 ChromaDB, and 🧠 OpenAI — and delivered via a sleek modern frontend using React, Vite, TailwindCSS, and ShadCN.

The tool ingests curated PDFs from domains like 🛢️ drilling, ⚙️ production, and 🧪 reservoir engineering. It provides conversational responses with citations — intelligently routing each query to the most qualified domain “agent.”

---

## 📁 Project Structure

```
multi-agent-rag/
├── agent_data/                       # Raw documents organized by domain
├── backend/
│   ├── app/
│   │   ├── main.py                   # FastAPI entry point
│   │   ├── models/
│   │   │   └── schemas.py            # Pydantic models
│   │   ├── routes/
│   │   │   ├── agents.py             # Ask endpoints
│   │   │   └── qa.py                 # Optional extensions
│   │   └── services/
│   │       ├── agent_manager.py      # Agent config + metadata
│   │       ├── ingestion.py          # Chunking + vectorstore creation
│   │       ├── rag_pipeline.py       # Query routing + LLM interaction
│   │       └── sync_blob.py          # Azure Blob sync logic
│   │   └── utils/                    # (Optional utility functions)
│   └── credential.env                # API keys and connection strings
├── frontend/
│   ├── src/
│   │   ├── assets/
│   │   │   └── bitbrain-logo.png     # Logo asset
│   │   ├── components/
│   │   │   ├── AgentSelector.jsx     # Agent dropdown
│   │   │   ├── ChatBox.jsx           # Input + send button
│   │   │   └── MessageBubble.jsx     # Answer formatting + metadata
│   │   ├── App.jsx                   # Main app container
│   │   ├── main.jsx                  # React entry
│   │   └── index.css                 # Tailwind + global styles
│   ├── public/
│   ├── tailwind.config.js
│   └── vite.config.js
├── vectorstore/                     # Chroma vector DBs by agent
└── README.md
```

---

## ✨ Features

- 🧠 Multi-agent architecture with expert agents per domain
- 📄 Document sync + chunking from Azure Blob
- 🧬 Dual embedding models for document & query (e5-embedding)
- 📊 Cosine similarity-based agent ranking + auto fallback
- 🤖 LLM responses via Cloudera-hosted LLaMA 3.1 8B endpoint
- 🧾 Citations (filename + page)
- 🎨 Beautiful dark-themed UI (React + Tailwind + ShadCN)

---

## 🧠 Backend Requirements

- Python 3.10+
- FastAPI
- LangChain + langchain-community + langchain-openai
- ChromaDB
- OpenAI Python SDK (for Cloudera endpoints)
- `pip install -r requirements.txt`

---

## 💻 Frontend Requirements

- Node.js 18+
- TailwindCSS + ShadCN + Vite
- `npm install` from `/frontend`

---

## 🔐 Environment Setup

Inside `backend/credential.env`:

```
API_KEY=your-openai-key
EMBED_MODEL_PASSAGE=e5-embedding
EMBED_MODEL_QUERY=e5-embedding
MODEL_ID_INSTRUCT=llama-31-8b
AZURE_STORAGE_CONNECTION_STRING=your-blob-string
```

---

## 🚀 Running the App

1. **Start the backend** (auto-ingests on launch):
```bash
uvicorn backend.app.main:app --reload
```

2. **Start the frontend**:
```bash
cd frontend
npm run dev
```

Visit `http://localhost:5173`

---

## 💡 How to Use

- Upload documents to Azure Blob under `/drilling`, `/reservoir`, etc.
- Bit Brain syncs and embeds documents on startup
- Ask questions via UI (default or specific agent)
- Get answers + citations (filename, page)

---

## 🛠️ Troubleshooting

- `.env` not found? Ensure it's correctly loaded
- Uploads failing? Confirm valid file types (.pdf, .docx, .txt)
- Blank frontend? Restart `npm run dev`
- No vectorstore created? Check logs during ingestion

---

## ☁️ Deployment Ideas

- Render / Azure App Service for backend
- Vercel / Azure Static Web Apps for frontend
- Blob sync via CRON or webhook

---

## 🧬 Name & Branding

**Bit Brain** = a fusion of:
- **“Bit”** – a reference to drill bits in upstream engineering
- **“Brain”** – symbolic of intelligent, contextual Q&A

The logo reflects a neural circuit embedded in a drill bit shape.

---