# AI Knowledge Base Document Chat Platform

A Retrieval-Augmented Generation (RAG) document chat app with a FastAPI backend and a React + Vite frontend. Users can upload PDFs, index them locally with FAISS, and ask questions grounded in the uploaded documents.

## Stack

- FastAPI
- FAISS
- Sentence Transformers
- PyPDF
- React
- Vite
- Tailwind CSS
- SQLite

## Project Structure

```text
.
├── backend/
│   ├── main.py
│   ├── graph.py
│   ├── rag.py
│   ├── embeddings.py
│   ├── vectordb.py
│   ├── pdf_loader.py
│   ├── llm.py
│   └── config.py
├── data/
│   ├── docs/
│   └── index/
├── frontend/
│   ├── src/
│   ├── package.json
│   ├── vite.config.js
│   └── tailwind.config.js
├── .env.example
├── requirements.txt
└── README.md
```

## Backend Setup

```bash
python -m venv .venv
.venv\Scripts\activate
pip install -r requirements.txt
```

Create a root `.env` file from `.env.example` and add your Mistral API key.

Run the backend:

```bash
cd backend
uvicorn main:app --host 0.0.0.0 --port 8000 --reload
```

Backend URL:

```text
http://127.0.0.1:8000
```

## Frontend Setup

```bash
cd frontend
npm install
copy .env.example .env
npm run dev
```

Frontend URL:

```text
http://127.0.0.1:5173
```

## API Endpoints

- `GET /health` checks backend health.
- `GET /documents` lists uploaded document metadata.
- `POST /upload` uploads and indexes a PDF.
- `POST /chat` answers questions from indexed documents.

## Notes

- `data/docs/` and `data/index/` are kept in the repo as empty placeholders. Generated PDFs and vector indexes are not committed.
- The frontend supports streaming mode, but the backend currently uses the standard `POST /chat` response path.
