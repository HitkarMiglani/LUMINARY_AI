# 🏗️ LuminaryAI - System Architecture Documentation

> **Complete Technical Architecture Overview**  
> Legal Intelligence Assistant for Indian Law

---

## 📋 Table of Contents

1. [System Overview](#system-overview)
2. [Architecture Diagram](#architecture-diagram)
3. [Technology Stack](#technology-stack)
4. [Core Components](#core-components)
5. [Data Flow](#data-flow)
6. [API Architecture](#api-architecture)
7. [Database Schema](#database-schema)
8. [Security Architecture](#security-architecture)
9. [Deployment Architecture](#deployment-architecture)
10. [Scalability & Performance](#scalability--performance)

---

## 🎯 System Overview

LuminaryAI is a **3-tier intelligent legal assistant** built with modern AI technologies:

- **Frontend Layer**: Streamlit-based interactive UI
- **Backend Layer**: Flask REST API with microservices architecture
- **AI/ML Layer**: Google Gemini LLM + ChromaDB Vector Store + Agno Framework

### Key Capabilities

- 🤖 **Agentic AI**: Agno-powered agent with autonomous reasoning
- 📚 **Retrieval Augmented Generation (RAG)**: ChromaDB vector search with local embeddings
- 🧠 **Persistent Memory**: User preferences + chat history across sessions
- 🔐 **Authentication**: JWT-based secure access control
- 📄 **Document Processing**: PDF/DOCX/TXT extraction and analysis
- 🇮🇳 **Indian Legal Context**: Role-based responses (Lawyer/Student/Public)

---

## 🏛️ Architecture Diagram

```
┌─────────────────────────────────────────────────────────────────────┐
│                         USER INTERFACE                              │
│                    (Streamlit Frontend - main.py)                   │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐               │
│  │ Chat Page    │  │ Documents    │  │ Settings     │               │
│  │ (Agentic AI) │  │ (Upload/RAG) │  │ (Preferences)│               │
│  └──────────────┘  └──────────────┘  └──────────────┘               │
└─────────────────────────────────────────────────────────────────────┘
                              │ HTTP/REST
                              ▼
┌─────────────────────────────────────────────────────────────────────┐
│                      API GATEWAY (Flask - app.py)                   │
│  ┌────────────────────────────────────────────────────────────────┐ │
│  │ Middleware Layer                                               │ │
│  │ • CORS • Request Logging • Exception Handling • JWT Auth       │ │
│  └────────────────────────────────────────────────────────────────┘ │
│                                                                     │
│        ┌──────────────┐  ┌──────────────┐  ┌──────────────┐         │
│        │ Auth Routes  │  │ Chat Routes  │  │ Doc Routes   │         │
│        │ /api/auth/*  │  │ /api/chat    │  │ /api/docs/*  │         │
│        └──────────────┘  └──────────────┘  └──────────────┘         │
│                                                                     │
│        ┌──────────────┐  ┌──────────────┐  ┌──────────────┐         │
│        │ RAG Routes   │  │ User Routes  │  │ Health Route │         │
│        │ /api/rag/*   │  │ /api/user/*  │  │ /api/health  │         │
│        └──────────────┘  └──────────────┘  └──────────────┘         │
└─────────────────────────────────────────────────────────────────────┘
                              │
          ┌───────────────────┼───────────────────┐
          ▼                   ▼                   ▼
┌──────────────────┐ ┌──────────────────┐ ┌──────────────────┐
│  CORE SERVICES   │ │  AI/ML SERVICES  │ │  DATA SERVICES   │
├──────────────────┤ ├──────────────────┤ ├──────────────────┤
│                  │ │                  │ │                  │
│ • Auth Manager   │ │ • Agno Agent     │ │ • SQLite DB      │
│ • Memory Manager │ │ • ChromaDB RAG   │ │ • ChromaDB Store │
│ • Doc Processor  │ │ • Gemini LLM     │ │ • File Storage   │
│ • Legal Retreiver│ │ • Reasoning Eng. │ │ • Vector Index   │
│                  │ │ • Embeddings     │ │                  │
└──────────────────┘ └──────────────────┘ └──────────────────┘
          │                   │                   │
          └───────────────────┼───────────────────┘
                              ▼
        ┌────────────────────────────────────────┐
        │      EXTERNAL INTEGRATIONS             │
        ├────────────────────────────────────────┤
        │ • Google Gemini API (LLM)              │
        │ • HuggingFace API (Embeddings)         │
        │ • Indian Kanoon API (Case Law)         │
        │ • Sentence Transformers (Local Model)  │
        └────────────────────────────────────────┘
```

---

## 🛠️ Technology Stack

### Frontend

| Technology    | Purpose              | Version |
| ------------- | -------------------- | ------- |
| **Streamlit** | Web UI Framework     | 1.31+   |
| **Python**    | Programming Language | 3.10+   |
| **Requests**  | HTTP Client          | Latest  |

### Backend

| Technology     | Purpose                       | Version |
| -------------- | ----------------------------- | ------- |
| **Flask**      | REST API Framework            | 3.0+    |
| **Flask-CORS** | Cross-Origin Resource Sharing | Latest  |
| **SQLAlchemy** | ORM for Database              | 2.0+    |
| **Werkzeug**   | File Handling & Security      | Latest  |

### AI/ML

| Technology                | Purpose              | Version             |
| ------------------------- | -------------------- | ------------------- |
| **Google Gemini**         | Large Language Model | gemini-1.5-flash    |
| **Agno Framework**        | Agentic AI Framework | Latest              |
| **ChromaDB**              | Vector Database      | 0.4+                |
| **Sentence Transformers** | Local Embeddings     | all-MiniLM-L6-v2    |
| **LangChain**             | Tool Orchestration   | Latest              |
| **HuggingFace**           | Model Hosting        | Qwen2.5-7B-Instruct |

### Security

| Technology       | Purpose               | Version         |
| ---------------- | --------------------- | --------------- |
| **PyJWT**        | JSON Web Tokens       | Latest          |
| **bcrypt**       | Password Hashing      | Latest          |
| **cryptography** | Preference Encryption | Latest (Fernet) |

### Document Processing

| Technology      | Purpose          | Version |
| --------------- | ---------------- | ------- |
| **PyPDF2**      | PDF Extraction   | Latest  |
| **python-docx** | DOCX Processing  | Latest  |
| **pdf2image**   | PDF to Image     | Latest  |
| **Pillow**      | Image Processing | Latest  |

### Database

| Technology   | Purpose             | Version    |
| ------------ | ------------------- | ---------- |
| **SQLite**   | Relational Database | 3.x        |
| **ChromaDB** | Vector Store        | Persistent |

---

## 🧩 Core Components

### 1. Frontend Layer (`main.py`)

**Purpose**: Streamlit-based user interface

**Key Features**:

- 3 Main Pages: Chat, Documents, Settings
- Real-time API communication
- Session state management
- Role-based UI adaptation

**Architecture**:

```python
main.py (2406 lines)
├── show_chat_page()          # Agentic chat interface
├── show_documents_page()     # Document upload & RAG queries
├── show_settings_page()      # User preferences & memory
└── make_api_request()        # Unified API client
```

**API Integration**:

- Single endpoint pattern: `/api/chat` (auto-detects query type)
- Document endpoints: `/api/documents/*`
- RAG endpoints: `/api/rag/*`
- User endpoints: `/api/user/*`

---

### 2. Backend API Layer (`app.py`)

**Purpose**: Flask REST API with Blueprint architecture

**Architecture**:

```python
app.py (1390 lines)
├── Authentication Routes     # /api/auth/register, /api/auth/login
├── Chat Routes              # /api/chat (unified smart endpoint)
├── Document Routes          # /api/documents/upload, /api/documents/<id>
├── RAG Routes (Blueprint)   # /api/rag/* (document_rag_routes.py)
├── User Management          # /api/user/<id>/history, /api/user/<id>/preferences
├── Research Routes          # /api/research/cases, /api/research/case/<id>
└── Health Check             # /api/health, /api/status
```

**Middleware Stack**:

1. **CORS** - Cross-origin request handling
2. **Request Logging** - All requests logged with timestamps
3. **Exception Handler** - Global error handling with proper HTTP codes
4. **JWT Authentication** - Token-based security (optional per route)

**Initialization Flow**:

```python
1. Load Config from .env
2. Initialize SQLAlchemy Database
3. Initialize Core Modules:
   - DocumentProcessor
   - LegalRetriever
   - MemoryManager
4. Initialize AI Modules:
   - GeminiReasoningEngine
   - ChromaDBRAGTool
   - LangChain Tools
5. Register Blueprints
6. Start Flask Server
```

---

### 3. AI/ML Layer

#### 3.1 Agno Agent (`modules/agno_agent.py`)

**Purpose**: Autonomous legal assistant with knowledge base

**Architecture**:

```python
LegalAgnoAgent (569 lines)
├── __init__()                    # Initialize agent with ChromaDB
├── _create_agent()               # Configure Agno agent
├── query_sync()                  # Synchronous query interface
├── query_async()                 # Async query interface
└── add_knowledge()               # Add documents to knowledge base
```

**Configuration**:

- **Model**: HuggingFace Qwen/Qwen2.5-7B-Instruct
- **Embeddings**: Google Gemini Embedder
- **Vector DB**: ChromaDB with persistent storage
- **Knowledge Search**: Enabled (`search_knowledge=True`)
- **Custom Tools**: Disabled (compatibility issues)

**Role-Based Prompts**:

```python
LAWYER_PROMPT = """
You are a senior legal expert assisting lawyers.
Provide detailed technical analysis with citations...
"""

STUDENT_PROMPT = """
You are a legal educator assisting law students.
Explain concepts clearly with examples...
"""

PUBLIC_PROMPT = """
You are a friendly legal advisor for the general public.
Explain in simple, accessible language...
"""
```

#### 3.2 ChromaDB RAG Tool (`modules/document_rag_chromadb.py`)

**Purpose**: Vector-based document retrieval and Q&A

**Architecture**:

```python
ChromaDBRAGTool (556 lines)
├── add_document()              # Add doc with chunking
├── query_document()            # RAG query with Gemini
├── search_documents()          # Semantic search
├── compare_documents()         # Multi-doc comparison
├── delete_document()           # Remove from vector store
└── get_statistics()            # Collection stats
```

**Key Features**:

- **Local Embeddings**: Sentence Transformers (no API costs!)
- **Model**: `all-MiniLM-L6-v2` (384 dimensions, fast)
- **Chunking Strategy**: 500 chars with 100 char overlap
- **Persistent Storage**: `chromadb_storage/` directory
- **Context Window**: Top 5 relevant chunks for answers

**Query Pipeline**:

```
User Query
  → Embed query (SentenceTransformer)
  → Search ChromaDB (cosine similarity)
  → Retrieve top 5 chunks
  → Build context with chunks
  → Generate answer (Gemini)
  → Return answer + sources
```

#### 3.3 Gemini Reasoning Engine (`modules/reasoning_engine.py`)

**Purpose**: Advanced legal analysis with Gemini LLM

**Architecture**:

```python
GeminiReasoningEngine (746 lines)
├── analyze_query()             # Smart query analysis
├── generate_response()         # Role-based response
├── extract_key_elements()      # Document element extraction
├── summarize_document()        # Multi-chunk summarization
├── compare_documents()         # Comparative analysis
└── suggest_precedents()        # Case law suggestions
```

**Model Configuration**:

- **Model**: `gemini-1.5-flash` (fast, cost-effective)
- **Temperature**: 0.7 (balanced creativity)
- **Max Tokens**: 2048 (longer responses)
- **Safety Settings**: Disabled for legal content

---

### 4. Data Services

#### 4.1 Database Models (`models.py`)

**SQLAlchemy ORM Schema**:

```python
User
├── id (PK)
├── username (unique)
├── email (unique)
├── password_hash (bcrypt)
├── role (ENUM: lawyer/student/public)
├── created_at
└── last_login

Document
├── id (PK)
├── doc_id (UUID, unique)
├── user_id (FK → User)
├── filename
├── file_type
├── file_path
├── content_hash
├── uploaded_at
├── processed (pending/completed/failed)
├── cached_text
└── cached_metadata

Query
├── id (PK)
├── user_id (FK → User)
├── query_text
├── response_text
├── context (JSON)
└── created_at

Memory
├── id (PK)
├── user_id (FK → User)
├── key
├── value (encrypted)
├── created_at
└── updated_at

Analysis
├── id (PK)
├── document_id (FK → Document)
├── analysis_type
├── result (JSON)
└── created_at

LegalCase
├── id (PK)
├── case_id (unique)
├── title
├── court
├── date
├── citation
├── content
├── summary
└── keywords (JSON array)
```

**Relationships**:

- User → Documents (1:N)
- User → Queries (1:N)
- User → Memories (1:N)
- Document → Analyses (1:N)

#### 4.2 ChromaDB Vector Store

**Collection Structure**:

```python
legal_documents (ChromaDB Collection)
├── id: "doc_id_chunk_index"
├── embedding: [384-dim vector]
├── metadata:
│   ├── doc_id: "uuid"
│   ├── filename: "contract.pdf"
│   ├── chunk_index: 0
│   ├── total_chunks: 10
│   └── timestamp: "2024-..."
└── document: "chunk text content"
```

**Storage Layout**:

```
chromadb_storage/
├── chroma.sqlite3           # ChromaDB metadata
├── index.json               # Document index
├── documents/               # Full text copies
│   └── {uuid}.txt
└── f4bbcf0b.../            # Collection data
    └── [vector embeddings]
```

---

### 5. Authentication & Security

#### 5.1 Auth Manager (`modules/auth.py`)

**JWT Authentication Flow**:

```
1. User Login (POST /api/auth/login)
   ↓
2. Verify password (bcrypt)
   ↓
3. Generate JWT token
   {
     "user_id": 1,
     "username": "john",
     "role": "lawyer",
     "exp": "2024-12-20T10:00:00Z"
   }
   ↓
4. Return token to client
   ↓
5. Client stores token
   ↓
6. Include in requests: Authorization: Bearer <token>
   ↓
7. Backend validates token (@token_required decorator)
```

**Security Features**:

- **Password Hashing**: bcrypt with salt
- **Token Expiration**: 24 hours (configurable)
- **Role-Based Access**: `@role_required(['lawyer', 'student'])`
- **Preference Encryption**: Fernet symmetric encryption

#### 5.2 Memory Manager (`modules/memory_manager.py`)

**Encrypted Preferences Storage**:

```python
store_memory(user_id, "practice_area", "Criminal Law")
  → JSON serialize: '{"value": "Criminal Law"}'
  → Fernet encrypt: b'gAAAAABl...'
  → Store in DB: Memory table

retrieve_memory(user_id, "practice_area")
  → Fetch from DB: b'gAAAAABl...'
  → Fernet decrypt: '{"value": "Criminal Law"}'
  → JSON deserialize: {"value": "Criminal Law"}
  → Return: "Criminal Law"
```

**Preference Keys**:

- `practice_area`: User's legal specialty
- `citation_format`: Preferred citation style
- `response_style`: Technical/Simple/Balanced
- `language_preference`: English/Hindi
- `custom_instructions`: User-specific guidance

---

## 📊 Data Flow

### 1. User Query Flow (Chat)

```
User sends query via Streamlit
  ↓
POST /api/chat
  {
    "user_id": 1,
    "message": "What are grounds for divorce?",
    "role": "public"
  }
  ↓
Backend receives request
  ↓
Load user preferences from Memory
  ↓
Determine query type (auto-detection):
  - RAG query? (mentions documents)
  - Agent query? (complex reasoning)
  - Simple Q&A? (direct question)
  ↓
Route to appropriate handler:

  Option A: Agno Agent
    ↓
  LegalAgnoAgent.query_sync()
    ↓
  Agent searches ChromaDB knowledge base
    ↓
  HuggingFace model generates response
    ↓
  Return with sources

  Option B: RAG Tool
    ↓
  ChromaDBRAGTool.search_documents()
    ↓
  Semantic search with embeddings
    ↓
  Gemini generates answer from chunks
    ↓
  Return with relevance scores

  Option C: Reasoning Engine
    ↓
  GeminiReasoningEngine.generate_response()
    ↓
  Gemini direct response
    ↓
  Role-based formatting
  ↓
Save query to Database (Query table)
  ↓
Return response to frontend
  ↓
Display in chat interface with sources
```

### 2. Document Upload Flow

```
User uploads PDF via Streamlit
  ↓
POST /api/documents/upload
  {
    "file": <binary>,
    "user_id": 1
  }
  ↓
Backend validates file:
  - Check extension (pdf/docx/txt)
  - Check size (<10MB)
  - Generate UUID
  ↓
Save to filesystem: uploads/{uuid}_{filename}
  ↓
DocumentProcessor.extract_text()
  - PyPDF2 for PDF
  - python-docx for DOCX
  - Direct read for TXT
  ↓
Calculate content hash (MD5)
  ↓
Save metadata to SQLite:
  Document table (user_id, filename, path, hash)
  ↓
Add to ChromaDB:
  ChromaDBRAGTool.add_document()
    ↓
  Chunk text (500 chars, 100 overlap)
    ↓
  Generate embeddings (SentenceTransformer)
    ↓
  Store in ChromaDB with metadata
  ↓
Update document status: "completed"
  ↓
Return document details to frontend
  ↓
Display success message
```

### 3. RAG Query Flow

```
User asks question about document
  ↓
POST /api/rag/documents/{doc_id}/query
  {
    "query": "What is the termination clause?",
    "user_id": 1
  }
  ↓
Backend validates document exists
  ↓
ChromaDBRAGTool.query_document(doc_id, query)
  ↓
Embed query with SentenceTransformer
  ↓
Search ChromaDB (filter by doc_id)
  ↓
Retrieve top 5 relevant chunks with scores
  ↓
Build context from chunks:
  """
  Relevant sections from {filename}:

  [Chunk 1 - Relevance: 0.89]
  {text}

  [Chunk 2 - Relevance: 0.76]
  {text}
  ...
  """
  ↓
Generate answer with Gemini:
  Prompt: "Based on these sections: {context}\n\nAnswer: {query}"
  ↓
Gemini generates natural language answer
  ↓
Return response:
  {
    "answer": "The termination clause states...",
    "sources": [
      {"chunk_id": 0, "relevance": 0.89},
      {"chunk_id": 3, "relevance": 0.76}
    ]
  }
  ↓
Display in frontend with source highlighting
```

---

## 🔌 API Architecture

### REST API Endpoints

#### Authentication

```
POST   /api/auth/register        # Create new user
POST   /api/auth/login           # Login and get JWT token
```

#### Chat & Query

```
POST   /api/chat                 # Unified chat endpoint (auto-routing)
POST   /api/query                # Legacy endpoint (redirects to /api/chat)
POST   /api/agent/query          # Legacy endpoint (redirects to /api/chat)
```

#### Document Management

```
POST   /api/documents/upload     # Upload document (+ add to ChromaDB)
GET    /api/documents            # List user's documents
GET    /api/documents/{doc_id}   # Get document details
POST   /api/documents/{id}/analyze  # Analyze document
```

#### RAG Operations

```
POST   /api/rag/documents        # Add document to RAG
GET    /api/rag/documents        # List RAG documents
GET    /api/rag/documents/{id}   # Get RAG document
DELETE /api/rag/documents/{id}   # Remove from RAG
POST   /api/rag/search           # Semantic search across all docs
POST   /api/rag/documents/{id}/query  # Query specific document
POST   /api/rag/search/semantic  # Advanced semantic search
POST   /api/rag/documents/compare     # Compare multiple documents
GET    /api/rag/statistics       # RAG system statistics
```

#### User Management

```
GET    /api/user/{id}/history    # Get chat history
GET    /api/user/{id}/preferences  # Get preferences
POST   /api/user/{id}/preferences  # Update preferences
```

#### Legal Research

```
GET    /api/research/cases       # Search Indian Kanoon cases
GET    /api/research/case/{id}   # Get case details
```

#### System

```
GET    /api/health               # Health check
GET    /api/status               # System status
```

### Request/Response Examples

#### Chat Request

```json
POST /api/chat
{
  "user_id": 1,
  "message": "What are the grounds for divorce under Hindu Marriage Act?",
  "role": "student"
}
```

#### Chat Response

```json
{
  "response": "Under the Hindu Marriage Act, 1955, divorce can be sought on the following grounds:\n\n1. **Adultery** (Section 13(1)(i))...",
  "sources": [
    {
      "type": "knowledge_base",
      "title": "Hindu Marriage Act, 1955",
      "relevance": 0.92
    }
  ],
  "query_type": "agent",
  "processing_time": 2.3
}
```

#### Document Upload Request

```json
POST /api/documents/upload
Content-Type: multipart/form-data

user_id: 1
file: <binary>
```

#### Document Upload Response

```json
{
  "success": true,
  "document": {
    "doc_id": "abc123-def456",
    "filename": "employment_contract.pdf",
    "file_type": "pdf",
    "uploaded_at": "2024-12-19T10:30:00Z",
    "processed": "completed",
    "rag_chunks": 15
  },
  "message": "Document uploaded and added to knowledge base"
}
```

#### RAG Query Request

```json
POST /api/rag/documents/abc123-def456/query
{
  "query": "What is the notice period?",
  "user_id": 1,
  "max_results": 5
}
```

#### RAG Query Response

```json
{
  "answer": "According to the employment contract, the notice period is 30 days from either party. Section 5.2 states that either party may terminate this agreement by providing written notice of 30 days.",
  "sources": [
    {
      "chunk_id": 8,
      "text": "Section 5.2: Notice Period\nEither party may terminate this agreement by providing written notice of 30 days...",
      "relevance_score": 0.94,
      "metadata": {
        "filename": "employment_contract.pdf",
        "page": 5
      }
    },
    {
      "chunk_id": 9,
      "text": "The notice period shall commence from the date of receipt of the written notice...",
      "relevance_score": 0.78,
      "metadata": {
        "filename": "employment_contract.pdf",
        "page": 5
      }
    }
  ],
  "doc_id": "abc123-def456",
  "query": "What is the notice period?"
}
```

---

## 🗄️ Database Schema

### Entity Relationship Diagram

```
┌─────────────────────┐
│       User          │
├─────────────────────┤
│ id (PK)             │
│ username            │◄────┐
│ email               │     │
│ password_hash       │     │
│ role (ENUM)         │     │
│ created_at          │     │
│ last_login          │     │
└─────────────────────┘     │
                            │ 1:N
┌─────────────────────┐     │
│     Document        │     │
├─────────────────────┤     │
│ id (PK)             │     │
│ doc_id (UUID)       │     │
│ user_id (FK) ───────┼─────┘
│ filename            │
│ file_type           │
│ file_path           │
│ content_hash        │
│ uploaded_at         │
│ processed           │
│ cached_text         │
│ cached_metadata     │
└─────────────────────┘
         │
         │ 1:N
         ▼
┌─────────────────────┐
│      Analysis       │
├─────────────────────┤
│ id (PK)             │
│ document_id (FK)    │
│ analysis_type       │
│ result (JSON)       │
│ created_at          │
└─────────────────────┘

┌─────────────────────┐
│       Query         │
├─────────────────────┤
│ id (PK)             │
│ user_id (FK) ───────┼────┐
│ query_text          │    │
│ response_text       │    │
│ context (JSON)      │    │
│ created_at          │    │
└─────────────────────┘    │
                           │ 1:N
┌─────────────────────┐    │
│       Memory        │    │
├─────────────────────┤    │
│ id (PK)             │    │
│ user_id (FK) ───────┼────┘
│ key                 │
│ value (encrypted)   │
│ created_at          │
│ updated_at          │
└─────────────────────┘

┌─────────────────────┐
│     LegalCase       │
├─────────────────────┤
│ id (PK)             │
│ case_id (unique)    │
│ title               │
│ court               │
│ date                │
│ citation            │
│ content             │
│ summary             │
│ keywords (JSON)     │
│ created_at          │
└─────────────────────┘
```

### Index Strategy

**Performance Indexes**:

```sql
-- User lookups
CREATE INDEX idx_users_username ON users(username);
CREATE INDEX idx_users_email ON users(email);

-- Document queries
CREATE INDEX idx_documents_user_id ON documents(user_id);
CREATE INDEX idx_documents_doc_id ON documents(doc_id);
CREATE INDEX idx_documents_uploaded_at ON documents(uploaded_at DESC);

-- Query history
CREATE INDEX idx_queries_user_id ON queries(user_id);
CREATE INDEX idx_queries_created_at ON queries(created_at DESC);

-- Memory lookups
CREATE INDEX idx_memories_user_key ON memories(user_id, key);

-- Legal case search
CREATE INDEX idx_legal_cases_case_id ON legal_cases(case_id);
```

---

## 🔐 Security Architecture

### 1. Authentication Flow

```
┌──────────┐                  ┌──────────┐                  ┌──────────┐
│  Client  │                  │ API      │                  │ Database │
└────┬─────┘                  └────┬─────┘                  └────┬─────┘
     │                             │                             │
     │ POST /api/auth/login        │                             │
     │ {username, password}        │                             │
     ├────────────────────────────>│                             │
     │                             │ Query user by username      │
     │                             ├────────────────────────────>│
     │                             │                             │
     │                             │ Return user record          │
     │                             │<────────────────────────────┤
     │                             │                             │
     │                             │ bcrypt.checkpw()            │
     │                             │ (verify password)           │
     │                             │                             │
     │                             │ jwt.encode()                │
     │                             │ (generate token)            │
     │                             │                             │
     │ Return JWT token            │                             │
     │<────────────────────────────┤                             │
     │                             │                             │
     │ Store token in session      │                             │
     │                             │                             │
     │ POST /api/chat              │                             │
     │ Authorization: Bearer <JWT> │                             │
     ├────────────────────────────>│                             │
     │                             │ jwt.decode()                │
     │                             │ (validate token)            │
     │                             │                             │
     │                             │ @token_required checks      │
     │                             │ - Signature valid?          │
     │                             │ - Not expired?              │
     │                             │ - User still exists?        │
     │                             │                             │
     │                             │ Process request             │
     │                             │                             │
     │ Return response             │                             │
     │<────────────────────────────┤                             │
     │                             │                             │
```

### 2. Security Layers

**Layer 1: Network Security**

- CORS policy restricts origins
- HTTPS recommended for production
- Rate limiting (60 req/min, 2000 req/hour)

**Layer 2: Authentication**

- JWT tokens with expiration
- bcrypt password hashing (cost factor 12)
- Token refresh mechanism

**Layer 3: Authorization**

- Role-based access control (RBAC)
- `@token_required` decorator for protected routes
- `@role_required(['lawyer'])` for role-specific routes

**Layer 4: Data Encryption**

- Preferences encrypted with Fernet (symmetric)
- Database passwords hashed (bcrypt)
- API keys stored in environment variables

**Layer 5: Input Validation**

- File type validation (whitelist: pdf, docx, txt)
- File size limits (10MB max)
- SQL injection protection (SQLAlchemy ORM)
- XSS protection (Flask auto-escaping)

### 3. Threat Model

| Threat                 | Mitigation                                        |
| ---------------------- | ------------------------------------------------- |
| **Password Guessing**  | bcrypt slow hashing + account lockout             |
| **Token Theft**        | Short expiration (24h) + HTTPS only               |
| **SQL Injection**      | SQLAlchemy ORM (parameterized queries)            |
| **XSS Attacks**        | Flask auto-escaping + Content Security Policy     |
| **CSRF**               | Token-based auth (no cookies)                     |
| **File Upload Attack** | Extension whitelist + size limit + virus scanning |
| **API Key Exposure**   | Environment variables + .gitignore                |
| **DoS**                | Rate limiting + request timeouts                  |

---

## 🚀 Deployment Architecture

### Development Environment

```
┌─────────────────────────────────────────────────┐
│           Developer Machine (Windows)           │
├─────────────────────────────────────────────────┤
│                                                 │
│  ┌──────────────┐          ┌──────────────┐   │
│  │  Streamlit   │          │    Flask     │   │
│  │  Port 8501   │◄────────►│  Port 5000   │   │
│  └──────────────┘          └──────────────┘   │
│                                                 │
│  ┌──────────────────────────────────────────┐  │
│  │           Local Storage                  │  │
│  ├──────────────────────────────────────────┤  │
│  │ • luminary.db (SQLite)                   │  │
│  │ • chromadb_storage/ (Vector DB)          │  │
│  │ • uploads/ (Documents)                   │  │
│  │ • logs/ (Application logs)               │  │
│  └──────────────────────────────────────────┘  │
│                                                 │
│  ┌──────────────────────────────────────────┐  │
│  │         Python Virtual Env               │  │
│  │         env/ (Windows venv)              │  │
│  └──────────────────────────────────────────┘  │
│                                                 │
└─────────────────────────────────────────────────┘
                    │
                    ▼ API Calls
┌─────────────────────────────────────────────────┐
│            External Services (Cloud)            │
├─────────────────────────────────────────────────┤
│ • Google Gemini API (LLM)                       │
│ • HuggingFace API (Models)                      │
│ • Indian Kanoon API (Case Law)                  │
└─────────────────────────────────────────────────┘
```

### Production Architecture (Recommended)

```
┌─────────────────────────────────────────────────────────┐
│                     Load Balancer                       │
│                   (nginx / AWS ALB)                     │
└────────────────────────┬────────────────────────────────┘
                         │
         ┌───────────────┼───────────────┐
         ▼               ▼               ▼
┌─────────────┐  ┌─────────────┐  ┌─────────────┐
│  Frontend   │  │  Frontend   │  │  Frontend   │
│ (Streamlit) │  │ (Streamlit) │  │ (Streamlit) │
│  Instance 1 │  │  Instance 2 │  │  Instance 3 │
└─────────────┘  └─────────────┘  └─────────────┘
         │               │               │
         └───────────────┼───────────────┘
                         ▼
         ┌──────────────────────────────┐
         │      API Gateway             │
         │      (nginx / Kong)          │
         └──────────────────────────────┘
                         │
         ┌───────────────┼───────────────┐
         ▼               ▼               ▼
┌─────────────┐  ┌─────────────┐  ┌─────────────┐
│   Backend   │  │   Backend   │  │   Backend   │
│   (Flask)   │  │   (Flask)   │  │   (Flask)   │
│  Instance 1 │  │  Instance 2 │  │  Instance 3 │
└─────────────┘  └─────────────┘  └─────────────┘
         │               │               │
         └───────────────┼───────────────┘
                         │
         ┌───────────────┼───────────────┐
         ▼               ▼               ▼
┌─────────────┐  ┌─────────────┐  ┌─────────────┐
│  PostgreSQL │  │  ChromaDB   │  │    Redis    │
│  (Primary)  │  │  (Vector)   │  │   (Cache)   │
└─────────────┘  └─────────────┘  └─────────────┘
         │
         ▼
┌─────────────┐
│  S3 / Blob  │
│  Storage    │
│ (Documents) │
└─────────────┘
```

### Deployment Checklist

**1. Environment Setup**

- [ ] Set production environment variables
- [ ] Generate secure JWT_SECRET and FERNET_KEY
- [ ] Configure production database (PostgreSQL recommended)
- [ ] Set up cloud storage (AWS S3 / Azure Blob)
- [ ] Enable HTTPS with SSL certificates

**2. Database Migration**

- [ ] Export SQLite data
- [ ] Create PostgreSQL database
- [ ] Run migrations: `alembic upgrade head`
- [ ] Import data

**3. Vector Store Setup**

- [ ] Configure ChromaDB persistent storage
- [ ] Mount ChromaDB volume for persistence
- [ ] Backup vector embeddings

**4. Application Configuration**

- [ ] Set DEBUG=False
- [ ] Configure CORS for production domain
- [ ] Enable rate limiting
- [ ] Set up logging (CloudWatch / ELK)

**5. Monitoring & Alerts**

- [ ] Application Performance Monitoring (APM)
- [ ] Error tracking (Sentry / Rollbar)
- [ ] Uptime monitoring
- [ ] API usage metrics

**6. Security Hardening**

- [ ] Enable firewall rules
- [ ] Configure security groups
- [ ] Set up DDoS protection
- [ ] Regular security audits

---

## ⚡ Scalability & Performance

### Current Limitations

| Component   | Limit             | Bottleneck         |
| ----------- | ----------------- | ------------------ |
| SQLite      | ~100K queries/day | File-based locking |
| ChromaDB    | ~1M vectors       | Memory usage       |
| Local Files | 10GB total        | Disk space         |
| Gemini API  | 60 requests/min   | Rate limiting      |

### Scaling Strategies

#### 1. Horizontal Scaling

**Frontend (Streamlit)**:

- Run multiple instances behind load balancer
- Session state in Redis for consistency
- Static assets on CDN

**Backend (Flask)**:

- Deploy 3+ instances with gunicorn
- Use nginx for load balancing
- Shared database + cache layer

**Database**:

- Migrate to PostgreSQL for better concurrency
- Read replicas for query load
- Connection pooling (pgBouncer)

#### 2. Vertical Scaling

**Compute**:

- Increase CPU for embedding generation
- More RAM for ChromaDB in-memory operations
- GPU instances for faster LLM inference

**Storage**:

- SSD for database operations
- Object storage (S3) for documents
- CDN for static files

#### 3. Caching Strategy

```python
# Multi-tier caching
┌─────────────────────────────────────┐
│    L1: In-Memory Cache (LRU)       │ ← 100ms
│    - Common queries                 │
│    - User preferences               │
└─────────────────────────────────────┘
                │
                ▼
┌─────────────────────────────────────┐
│    L2: Redis Cache                  │ ← 500ms
│    - Document embeddings            │
│    - API responses                  │
└─────────────────────────────────────┘
                │
                ▼
┌─────────────────────────────────────┐
│    L3: Database / Vector Store      │ ← 2s
│    - Full queries                   │
└─────────────────────────────────────┘
```

#### 4. Performance Optimizations

**Embeddings**:

- Batch embedding generation (100 docs at once)
- Async embedding with Celery
- Cache embeddings for common queries

**Database**:

- Index frequently queried columns
- Denormalize hot data
- Partition large tables

**API**:

- Response compression (gzip)
- Pagination for large results
- Asynchronous processing for heavy tasks

**Vector Search**:

- Approximate nearest neighbors (ANN)
- Reduce embedding dimensions (384→128)
- Index optimization (HNSW algorithm)

### Monitoring Metrics

**Application Metrics**:

- Request rate (req/s)
- Response time (p50, p95, p99)
- Error rate (%)
- Active users

**Infrastructure Metrics**:

- CPU utilization
- Memory usage
- Disk I/O
- Network throughput

**Business Metrics**:

- Documents processed
- Queries answered
- User satisfaction (feedback)
- API costs

---

## 📈 Future Enhancements

### Short Term (1-3 months)

- [ ] Add support for Hindi language
- [ ] Implement OCR for scanned PDFs
- [ ] Add export functionality (PDF/DOCX reports)
- [ ] Improve error handling and retry logic

### Medium Term (3-6 months)

- [ ] Multi-user collaboration on documents
- [ ] Advanced analytics dashboard
- [ ] Custom model fine-tuning on legal data
- [ ] Mobile app (React Native)

### Long Term (6-12 months)

- [ ] Multi-language support (10+ Indian languages)
- [ ] Voice interface (speech-to-text)
- [ ] Integration with court websites
- [ ] Automated legal document generation

---

## 📚 References

### Documentation

- **Agno Framework**: https://github.com/agno-agi/agno
- **ChromaDB**: https://docs.trychroma.com/
- **Google Gemini**: https://ai.google.dev/docs
- **LangChain**: https://python.langchain.com/docs
- **Streamlit**: https://docs.streamlit.io/
- **Flask**: https://flask.palletsprojects.com/

### Key Files

- `app.py` - Backend API (1390 lines)
- `main.py` - Frontend UI (2406 lines)
- `config.py` - Configuration (150 lines)
- `models.py` - Database models (150 lines)
- `modules/agno_agent.py` - Agentic AI (569 lines)
- `modules/document_rag_chromadb.py` - RAG system (556 lines)
- `modules/reasoning_engine.py` - Gemini integration (746 lines)

---

**Last Updated**: December 19, 2024  
**Version**: 2.0  
**Architecture By**: GitHub Copilot
