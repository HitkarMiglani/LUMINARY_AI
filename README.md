# ⚖️ LuminaryAI

> **Intelligent Legal Assistant for Indian Law**  
> Making Indian law understandable, accessible, and intelligent — for lawyers, students, and everyone.

---

## 📚 Table of Contents

1. [Overview & Features](#overview--features)
2. [Installation Guide](#installation-guide)
3. [Architecture & Project Structure](#architecture--project-structure)
4. [Memory System Documentation](#memory-system-documentation)
5. [Document Processing & OCR Setup](#document-processing--ocr-setup)
6. [API Reference](#api-reference)
7. [Troubleshooting](#troubleshooting)

---

# Overview & Features

## 🧩 What is LuminaryAI?

LuminaryAI is an **intelligent, proactive legal assistant** that makes case discovery easier and legal information accessible to everyone. Built specifically for the Indian legal system, it serves three distinct user groups with personalized experiences:

👨‍⚖️ **For Lawyers**: Technical legal analysis with detailed case law references  
📚 **For Students**: Educational explanations with clear concept breakdowns  
👥 **For Public**: Simple, accessible legal guidance in plain language

Built using **Agno Framework, Google Gemini, HuggingFace Models, ChromaDB RAG, and SQLite**, LuminaryAI offers:

- 🧠 **Persistent Memory System** - Remembers your preferences, chat history, and context across sessions
- 🤖 **Autonomous Agent** - Agno-powered agent with ChromaDB knowledge base and role-based prompts
- 📚 **Smart Document RAG** - ChromaDB-based semantic search with local embeddings (no API costs!)
- 🎯 **Unified Chat Interface** - Single endpoint with auto-detection for simple or agentic queries
- ⚡ **Role-Based Responses** - Automatically adapts complexity based on user type
- 🔍 **Intelligent Case Discovery** - Find relevant precedents with semantic matching

All through a modern Streamlit frontend and robust Flask backend with **encrypted user preferences** and **database-backed persistence**.

## 💡 Why LuminaryAI?

### The Problem We Solve

**Traditional Legal Research is:**

- ⏰ **Time-Consuming** - Hours spent searching through case law and statutes
- 🧩 **Complex** - Legal jargon makes information inaccessible to non-lawyers
- 💰 **Expensive** - Professional legal advice is costly for students and public
- 📚 **Overwhelming** - Too much information, difficult to find what's relevant
- 🔄 **Reactive** - Tools wait for you to ask instead of proactively helping

### Our Solution: Intelligent & Proactive Legal Assistance

**LuminaryAI Makes Legal Research:**

- ⚡ **Fast** - Semantic search finds relevant information in seconds
- 💡 **Accessible** - Role-based responses adapt to your understanding level
- 🎯 **Proactive** - Suggests relevant cases and documents before you ask
- 🧠 **Smart** - Learns from your preferences and remembers your context
- 🤝 **Inclusive** - Serves lawyers, students, and public with equal effectiveness

### Key Differentiators

1. **🧠 Persistent Memory** - Unlike ChatGPT, we remember your conversations and preferences across sessions
2. **🎯 Role-Based Intelligence** - Responses automatically adapt to lawyer/student/public expertise levels
3. **📚 Document-Aware** - Combines your uploaded documents with Indian case law for comprehensive answers
4. **🤖 Autonomous Agent** - Agno agent with ChromaDB knowledge base for intelligent document search
5. **🔍 Local Embeddings** - Sentence Transformers (all-MiniLM-L6-v2) - no API costs or quotas!
6. **🇮🇳 India-Specific** - Built specifically for Indian legal system with role-based prompts

## 🌟 Key Features

### 🧠 Intelligent Memory System

- **💾 Persistent Chat History** - All conversations saved and loaded on login
- **⚙️ User Preferences** - Customize practice area, response style, citation format, and language
- **🔐 Encrypted Storage** - Preferences stored securely using Fernet encryption
- **🎯 Context-Aware Responses** - AI adapts to your preferences automatically
- **📊 Settings Dashboard** - Manage preferences, export data, view chat statistics
- **🔄 Cross-Session Continuity** - Pick up where you left off, every time

### 🤖 Agno Autonomous Agent

- **🧠 Knowledge Base Search** - Integrated ChromaDB vector database with semantic search
- **🎯 Role-Based Prompts** - Specialized prompts for Lawyer/Student/Public users
- **🔍 Document Retrieval** - Automatic knowledge base search for relevant context
- **⚡ HuggingFace Models** - Qwen/Qwen2.5-7B-Instruct for intelligent responses
- **📚 Google Gemini Embeddings** - High-quality document embeddings
- **🔄 Sync/Async Query** - Flexible query interfaces for different use cases

### 📚 ChromaDB Document RAG

- **🔍 Semantic Search** - Find relevant document sections across your entire library
- **📄 Multi-Document Support** - Upload PDFs, DOCX, and TXT files
- **🎯 Context-Aware Retrieval** - Combines document content with case law
- **💬 Document Q&A** - Ask specific questions about any document
- **📊 Relevance Scoring** - See exactly how relevant each result is
- **🗂️ UUID-Based Management** - Consistent document tracking across database and vector store
- **🔄 OCR Support** - Handles scanned/image-based PDFs with Tesseract OCR

### ⚡ Role-Based Intelligence

- **👨‍⚖️ Lawyer Mode** - Technical analysis, detailed citations, case law focus
- **📚 Student Mode** - Educational explanations, concept breakdowns, learning context
- **👥 Public Mode** - Simple language, accessible explanations, practical guidance
- **🎨 Adaptive Responses** - Automatically adjusts complexity and terminology
- **📈 Personalized Learning** - Remembers your role and preferences across sessions

### 🔍 Proactive Legal Assistance

- **✨ Query Enhancement** - Automatically improves unclear queries (quality score < 8)
- **🎯 Smart Suggestions** - Recommends relevant documents and cases proactively
- **📋 Context Building** - Combines your documents, preferences, and case law
- **⚡ Real-Time Analysis** - Validates legal queries before processing
- **🔔 Intelligent Notifications** - Alerts when better tools are available for your query

### 🔐 Security & Privacy

- **🔒 Encrypted Preferences** - Fernet encryption for all sensitive data
- **🛡️ JWT Authentication** - Secure token-based auth with bcrypt password hashing
- **👤 User Isolation** - Documents and chat history strictly per-user
- **🔑 API Key Protection** - Environment-based configuration for sensitive keys
- **📊 Audit Logging** - Complete logging of all API interactions

---

# Installation Guide

## 📋 Prerequisites

- Python 3.9+
- Git
- 4GB+ RAM
- Windows, macOS, or Linux

## ⚙️ Installation Steps

### 1. Clone Repository

```bash
git clone https://github.com/HitkarMiglani/legal_Test.git
cd Agentic_Law_AI
```

### 2. Create Virtual Environment

**Windows:**

```powershell
python -m venv env
.\env\Scripts\Activate.ps1
```

> **Note:** If activation fails, run: `Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser`

**Linux/Mac:**

```bash
python3 -m venv env
source env/bin/activate
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

### 4. Configure Environment

Create `.env` file:

```env
# Google Gemini API
GOOGLE_API_KEY=your_gemini_api_key_here

# Database
DB_URL=sqlite:///luminary.db

# JWT Secret
JWT_SECRET_KEY=your_random_secret_key_here

# Memory Encryption
ENCRYPTION_KEY=your_fernet_encryption_key_here

# Flask Config
FLASK_ENV=development
FLASK_SECRET_KEY=your_flask_secret_key

# Upload Settings
UPLOAD_FOLDER=uploads
MAX_FILE_SIZE=16777216  # 16MB
```

**Generate Keys:**

```python
# Fernet Key
from cryptography.fernet import Fernet
print(Fernet.generate_key().decode())

# JWT Secret
import secrets
print(secrets.token_hex(32))
```

### 5. Initialize Database

```bash
python -c "from models import init_db; from config import Config; init_db(Config.DB_URL)"
```

### 6. Run Application

**Option A: Development (Flask + Streamlit)**

Terminal 1 (Backend):

```bash
python app.py
```

Terminal 2 (Frontend):

```bash
streamlit run main.py
```

**Option C: Windows PowerShell Script**

```powershell
.\run.ps1
```

This automatically starts both Flask backend and Streamlit frontend.

**Option B: Production**

```bash
# Using waitress
python run_waitress.py

# Or using gunicorn (Linux/Mac)
gunicorn -w 4 -b 0.0.0.0:5000 app:app
```

### 7. Access Application

- **Frontend**: http://localhost:8501
- **Backend API**: http://localhost:5000
- **API Health**: http://localhost:5000/api/health
- **API Documentation**: http://localhost:5000/

### 8. First Time Setup

1. Navigate to http://localhost:8501
2. Click "Get Started" on landing page
3. Register a new account (choose role: lawyer/student/public)
4. Start chatting or upload documents!

## 🔧 Optional: OCR Setup for Image-Based PDFs

If you need to process scanned PDFs, install OCR dependencies:

### Install Python Libraries

```bash
pip install pdf2image pytesseract pillow
```

### Install Tesseract Engine

**Windows:**

1. Download from [Tesseract at UB Mannheim](https://github.com/UB-Mannheim/tesseract/wiki)
2. Run installer (default: `C:\Program Files\Tesseract-OCR`)
3. Add to PATH:
   ```powershell
   $env:Path += ";C:\Program Files\Tesseract-OCR"
   ```

**Linux:**

```bash
sudo apt-get install tesseract-ocr
```

**Mac:**

```bash
brew install tesseract
```

### Verify Installation

```bash
tesseract --version
python -c "import pdf2image, pytesseract; print('OCR ready!')"
```

---

# Architecture & Project Structure

## 🏗️ Technology Stack

### Backend

- **Flask** - REST API framework
- **SQLAlchemy** - ORM and database management
- **SQLite** - Local database (production: PostgreSQL)
- **ChromaDB** - Vector database for semantic search
- **LangChain** - LLM orchestration framework
- **LangGraph** - Agent workflow management

### AI/ML

- **Google Gemini** - Primary LLM (gemini-1.5-flash) for answer generation
- **HuggingFace** - Qwen/Qwen2.5-7B-Instruct for Agno agent
- **Agno Framework** - Agentic AI with knowledge base integration
- **Sentence Transformers** - Local embeddings (all-MiniLM-L6-v2) - NO API costs!
- **ChromaDB** - Vector database for semantic document search
- **Tesseract OCR** - Image-based PDF extraction (optional)

### Frontend

- **Streamlit** - Interactive web interface
- **Plotly** - Data visualization

### Security

- **PyJWT** - JWT authentication
- **bcrypt** - Password hashing
- **Fernet** - Preference encryption

## 📁 Project Structure

```
Agentic_Law_AI/
├── app.py                    # Flask backend (main API)
├── main.py                   # Streamlit frontend
├── config.py                 # Configuration management
├── models.py                 # Database models (SQLAlchemy)
├── requirements.txt          # Python dependencies
│
├── modules/                  # Core modules
│   ├── __init__.py
│   ├── agno_agent.py        # Agno-based legal agent
│   ├── auth.py              # Authentication & JWT
│   ├── document_processor.py # PDF/DOCX extraction + OCR
│   ├── document_rag_chromadb.py # ChromaDB RAG implementation
│   ├── document_rag_langchain.py # LangChain tool wrappers
│   ├── document_rag_routes.py # Document API routes
│   ├── legal_retriever.py   # Indian Kanoon integration
│   ├── memory_manager.py    # Encrypted preference storage
│   └── reasoning_engine.py  # Gemini-based legal analysis
│
├── utils/                    # Utilities
│   ├── __init__.py
│   ├── exceptions.py        # Custom exceptions
│   ├── logger.py            # Logging configuration
│   └── middleware.py        # Request logging & error handling
│
├── uploads/                  # Uploaded documents
├── chromadb_storage/         # ChromaDB vector store
├── logs/                     # Application logs
├── env/                      # Virtual environment
│
└── Documentation Files
    ├── README.md            # This file - complete guide
    ├── ARCHITECTURE.md      # System architecture diagram
    ├── MEMORY_FLOW.md       # Memory system documentation
    └── SIMPLIFICATION_PLAN.md # Project simplification notes
```

## 🔄 System Architecture

> **📘 For detailed architecture documentation, see [ARCHITECTURE.md](ARCHITECTURE.md)**

```
┌─────────────────────────────────────────────────────────────┐
│              STREAMLIT FRONTEND (main.py)                    │
│     3 Pages: Chat | Documents | Settings                     │
└────────────────────┬────────────────────────────────────────┘
                     │ REST API Calls
                     ↓
┌─────────────────────────────────────────────────────────────┐
│                 FLASK BACKEND (app.py)                       │
│  JWT Auth | /api/chat | /api/documents | /api/rag/*         │
└────┬──────────┬──────────┬──────────┬──────────────────────┘
     │          │          │          │
     ↓          ↓          ↓          ↓
┌────────┐ ┌─────────┐ ┌──────────┐ ┌───────────┐
│SQLite  │ │ChromaDB │ │MemoryMgr │ │Agno Agent │
│Database│ │Vector DB│ │(Fernet)  │ │+Knowledge │
└────────┘ └─────────┘ └──────────┘ └─────┬─────┘
                                           │
                                           ↓
                              ┌────────────────────────┐
                              │   AI/ML Layer          │
                              ├────────────────────────┤
                              │ • Gemini LLM           │
                              │ • HuggingFace Models   │
                              │ • Sentence Transformers│
                              │ • Google Embeddings    │
                              └────────────────────────┘
```

## 📊 Data Flow

### Document Upload Flow

```
User Upload → File Validation → Save to uploads/
    ↓
Extract Text (PyPDF2/pdfminer/OCR)
    ↓
Clean & Chunk Text (500-1000 chars)
    ↓
Generate Embeddings (Sentence-BERT)
    ↓
Store in ChromaDB + Database
```

### Query Processing Flow

```
User Query → Validate & Enhance
    ↓
Load User Preferences & History
    ↓
Build Context (Role + Preferences + Documents)
    ↓
LangGraph Agent Selection
    ↓
Tool Execution (RAG Search / Case Lookup / etc)
    ↓
Gemini Generation with Context
    ↓
Save to Database → Return Response
```

---

# Memory System Documentation

## Overview

The memory system provides persistent storage for user preferences and chat history using SQLite database and encrypted preference management.

## Database Models

### Query Model

Stores all user queries and responses:

```python
class Query(Base):
    __tablename__ = 'queries'

    id = Column(Integer, primary_key=True)
    user_id = Column(Integer, ForeignKey('users.id'), nullable=False)
    query_text = Column(Text, nullable=False)
    response_text = Column(Text)
    context = Column(Text)  # JSON context used
    created_at = Column(DateTime, default=datetime.utcnow)

    user = relationship("User", back_populates="queries")
```

### Memory Model

Stores encrypted user preferences:

```python
class Memory(Base):
    __tablename__ = 'memories'

    id = Column(Integer, primary_key=True)
    user_id = Column(Integer, ForeignKey('users.id'), nullable=False)
    key = Column(String(100), nullable=False)
    value = Column(Text)  # Encrypted with Fernet
    created_at = Column(DateTime, default=datetime.utcnow)
    updated_at = Column(DateTime, default=datetime.utcnow, onupdate=datetime.utcnow)

    user = relationship("User", back_populates="memories")
```

## Memory Manager

### Key Methods

```python
class MemoryManager:
    def store_memory(self, user_id: int, key: str, value: str):
        """Encrypts and stores a user preference"""

    def retrieve_memory(self, user_id: int, key: str) -> Optional[str]:
        """Decrypts and retrieves a user preference"""

    def get_all_memories(self, user_id: int) -> Dict[str, str]:
        """Returns all user preferences as dictionary"""

    def build_user_context(self, user_id: int, role: str) -> str:
        """Builds context string for AI prompts"""
```

### Security Features

- **Fernet Encryption** - Symmetric encryption for all stored values
- **Automatic Encryption/Decryption** - Transparent to application code
- **Key Management** - Uses environment variable `ENCRYPTION_KEY`
- **Temporary Keys** - Generates session keys if none configured

## Implementation Flows

### 1. Login Flow

```
User Login (Streamlit)
    ↓
POST /api/auth/login (Flask)
    ↓
Validate Credentials
    ↓
Generate JWT Token
    ↓
GET /api/user/{id}/history
    ↓
Load Chat History from Database
    ↓
Load Preferences from Memory Table
    ↓
Return to Frontend
    ↓
Populate Session State
```

### 2. Query Flow

```
User Asks Question
    ↓
Load User Preferences from Session
    ↓
POST /api/query or /api/agent/query
    ↓
Backend Loads Memory Context
    ↓
Build Enhanced Prompt with Context
    ↓
LLM Generation
    ↓
Save Query + Response to Database
    ↓
Return Response
```

### 3. Preferences Update Flow

```
User Changes Settings
    ↓
POST /api/user/preferences
    ↓
Validate New Preferences
    ↓
Encrypt Values (MemoryManager)
    ↓
Store in Memory Table
    ↓
Return Success
    ↓
Update Session State
```

### 4. Agent Query Flow (with Tools)

```
User Query → Validate
    ↓
Load User Context (Preferences + History)
    ↓
LangGraph Agent Initialization
    ↓
Tool Selection (RAG / Case Lookup / etc)
    ↓
Execute Tools with Context
    ↓
Aggregate Results
    ↓
Gemini Generation
    ↓
Save to Database
    ↓
Return with Tool Attribution
```

## Supported Preferences

Users can customize:

- **Practice Area** - Criminal, Civil, Corporate, etc.
- **Response Style** - Detailed, Concise, Conversational
- **Citation Format** - Bluebook, ALWD, Chicago
- **Language** - English, Hindi, etc.
- **Notification Settings** - Email, SMS preferences

## API Endpoints

### Get User History

```
GET /api/user/{user_id}/history
Authorization: Bearer <token>

Response:
{
  "chat_history": [
    {"role": "user", "content": "..."},
    {"role": "assistant", "content": "..."}
  ],
  "agent_history": [...],
  "preferences": {
    "practice_area": "criminal",
    "response_style": "detailed",
    "citation_format": "bluebook"
  }
}
```

### Update Preferences

```
POST /api/user/preferences
Authorization: Bearer <token>

Body:
{
  "practice_area": "criminal",
  "response_style": "detailed",
  "citation_format": "bluebook",
  "language": "english"
}

Response:
{
  "message": "Preferences updated successfully",
  "preferences": {...}
}
```

### Get Preferences

```
GET /api/user/preferences
Authorization: Bearer <token>

Response:
{
  "preferences": {
    "practice_area": "criminal",
    "response_style": "detailed",
    "citation_format": "bluebook",
    "language": "english"
  }
}
```

## Configuration

### Environment Variables

```env
# Required
ENCRYPTION_KEY=your_fernet_key_here  # Generate with: Fernet.generate_key()

# Optional
CHAT_HISTORY_LIMIT=50  # Max queries to load per session
```

### Generate Encryption Key

```python
from cryptography.fernet import Fernet
key = Fernet.generate_key()
print(key.decode())  # Add to .env as ENCRYPTION_KEY
```

## Benefits

1. **Personalization** - AI adapts to user preferences automatically
2. **Continuity** - Pick up conversations where you left off
3. **Security** - All sensitive data encrypted at rest
4. **Scalability** - Database-backed, supports millions of users
5. **Privacy** - User data isolated, no cross-user leakage

---

# Document Processing & OCR Setup

## Document Processing Flow

### Supported Formats

- **PDF** - Text-based and image-based (with OCR)
- **DOCX** - Microsoft Word documents
- **TXT** - Plain text files

### Extraction Strategy

```
Document Upload
    ↓
┌─────────────────────┐
│  File Type Check    │
└────────┬────────────┘
         │
    ┌────┴────┐
    │   PDF?  │
    └────┬────┘
         ↓ Yes
┌─────────────────────┐
│ PyPDF2 Extraction   │ ← Fast, reliable for text PDFs
└────────┬────────────┘
         │
    Success? No ↓
         │
┌─────────────────────┐
│ pdfminer Extraction │ ← Fallback for complex PDFs
└────────┬────────────┘
         │
    <50 chars? Yes ↓
         │
┌─────────────────────┐
│ Image PDF Detected  │
└────────┬────────────┘
         │
    OCR Available? Yes ↓
         │
┌─────────────────────┐
│ Tesseract OCR       │ ← Extract from scanned images
└────────┬────────────┘
         │
    Success ↓
         │
┌─────────────────────┐
│ Clean & Chunk Text  │
└────────┬────────────┘
         │
┌─────────────────────┐
│ Generate Embeddings │
└────────┬────────────┘
         │
┌─────────────────────┐
│ Store in ChromaDB   │
└─────────────────────┘
```

## OCR Setup for Image-Based PDFs

### Problem: Scanned Documents

PDFs created by scanning physical documents contain **images of text**, not actual text data. This prevents normal extraction methods from working.

**Detection Indicators:**

- PyPDF2 extracts 0 characters
- pdfminer extracts < 50 characters for multi-page documents
- File appears blank when copied to text editor

### Solution: Tesseract OCR

#### Step 1: Install Python Libraries

```bash
# Activate virtual environment
# Windows
.\env\Scripts\Activate.ps1

# Linux/Mac
source env/bin/activate

# Install OCR dependencies
pip install pdf2image pytesseract pillow
```

#### Step 2: Install Tesseract Engine

**Windows:**

1. **Download Installer**

   - Visit: https://github.com/UB-Mannheim/tesseract/wiki
   - Download latest version (e.g., `tesseract-ocr-w64-setup-5.3.3.20231005.exe`)

2. **Run Installer**

   - Default location: `C:\Program Files\Tesseract-OCR`
   - Select "Add to PATH" during installation

3. **Verify Installation**

   ```powershell
   tesseract --version
   # Should show: tesseract 5.x.x
   ```

4. **Manual PATH Configuration** (if needed)

   ```powershell
   # Temporary (current session)
   $env:Path += ";C:\Program Files\Tesseract-OCR"

   # Permanent (requires admin PowerShell)
   [Environment]::SetEnvironmentVariable(
       "Path",
       $env:Path + ";C:\Program Files\Tesseract-OCR",
       "Machine"
   )
   ```

**Linux:**

```bash
sudo apt-get update
sudo apt-get install tesseract-ocr
```

**Mac:**

```bash
brew install tesseract
```

#### Step 3: Configure pytesseract (Windows only, if needed)

If Tesseract is in a non-standard location:

```python
# In config.py or at app startup
import pytesseract
pytesseract.pytesseract.tesseract_cmd = r'C:\Program Files\Tesseract-OCR\tesseract.exe'
```

#### Step 4: Test OCR

```bash
# Test extraction on sample PDF
python test_pdf_extraction_enhanced.py uploads\SECTION_226.pdf
```

**Expected Output:**

```
==================================================
ENHANCED PDF EXTRACTION TEST
==================================================

📄 Testing file: uploads\SECTION_226.pdf
📊 File size: 245678 bytes

✅ OCR libraries available (pdf2image, pytesseract)
✅ Tesseract OCR engine installed (version 5.3.3)

--------------------------------------------------
EXTRACTION PROCESS:
--------------------------------------------------

Attempting PyPDF2 extraction...
PDF has 1 pages
Page 1: 0 characters extracted
⚠️  PDF appears to be image-based (0 chars for 1 pages)

🔍 Attempting OCR extraction (image-based PDF detected)...
Converting PDF to images...
Processing 1 pages with OCR...
OCR processing page 1/1...
  Page 1: 1234 characters extracted

==================================================
✅ EXTRACTION SUCCESSFUL
==================================================

📊 Statistics:
   - Characters: 1,234
   - Words: 189
   - Chunks: 2

📝 Text Preview (first 500 characters):
--------------------------------------------------
SECTION 226 OF INDIAN PENAL CODE
...
```

### OCR Performance

**Extraction Times (approximate):**

- Text-based PDF (1 page): < 1 second
- Image-based PDF with OCR (1 page): 3-5 seconds
- Image-based PDF with OCR (10 pages): 30-50 seconds

**Tips for Faster OCR:**

1. Use high-quality scans (300+ DPI)
2. Ensure pages are properly aligned
3. Process in batches during off-hours
4. Consider cloud OCR services for large volumes

### Alternative Approaches

If OCR is too slow or unavailable:

#### Option 1: Convert PDF to Text-Based

**Using Adobe Acrobat Pro:**

1. Open PDF in Acrobat
2. Tools → Recognize Text → In This File
3. Save as new PDF
4. Upload the new version

**Using Online Converters:**

- ilovepdf.com - Free PDF OCR
- smallpdf.com - OCR + conversion
- onlineocr.net - Direct text extraction

#### Option 2: Upload as Text File

1. Copy text from PDF manually
2. Save as `.txt` file
3. Upload `.txt` instead of PDF
4. Instant processing (no OCR needed)

#### Option 3: Use ocrmypdf CLI

```bash
# Install
pip install ocrmypdf

# Convert PDF with OCR
ocrmypdf input.pdf output.pdf

# Upload output.pdf (now text-based)
```

### Troubleshooting

#### Error: "Tesseract not found"

**Solution:**

```powershell
# Check if installed
tesseract --version

# Add to PATH manually
$env:Path += ";C:\Program Files\Tesseract-OCR"

# Restart terminal
```

#### Error: "DLL load failed" (Windows)

**Solution:**

1. Install Visual C++ Redistributable
2. Download from: https://aka.ms/vs/17/release/vc_redist.x64.exe
3. Restart computer

#### OCR Produces Gibberish

**Possible Causes:**

- Poor scan quality
- Wrong language setting
- Corrupted PDF

**Solutions:**

```python
# Set language explicitly
pytesseract.image_to_string(image, lang='eng')

# For Hindi/multilingual
pytesseract.image_to_string(image, lang='eng+hin')

# Improve image preprocessing
from PIL import ImageEnhance
enhancer = ImageEnhance.Contrast(image)
image = enhancer.enhance(2.0)
```

### Verification Commands

```bash
# Check Python libraries
python -c "import pdf2image, pytesseract; print('✅ OCR libs installed')"

# Check Tesseract
tesseract --version

# Test end-to-end
python test_pdf_extraction_enhanced.py uploads\test.pdf
```

---

# API Reference

## Authentication Endpoints

### Register User

```
POST /api/auth/register

Body:
{
  "username": "john_doe",
  "email": "john@example.com",
  "password": "secure_password",
  "role": "lawyer"  // lawyer, student, or public
}

Response: 200 OK
{
  "message": "User registered successfully",
  "user": {
    "id": 1,
    "username": "john_doe",
    "role": "lawyer"
  }
}
```

### Login

```
POST /api/auth/login

Body:
{
  "username": "john_doe",
  "password": "secure_password"
}

Response: 200 OK
{
  "token": "eyJ0eXAiOiJKV1QiLCJhbGc...",
  "user": {
    "id": 1,
    "username": "john_doe",
    "email": "john@example.com",
    "role": "lawyer"
  }
}
```

## Document Endpoints

### Upload Document

```
POST /api/documents/upload
Authorization: Bearer <token>
Content-Type: multipart/form-data

Body:
- file: [PDF/DOCX/TXT file]

Response: 200 OK
{
  "message": "Document uploaded and processed successfully",
  "document_id": "uuid-here",
  "metadata": {
    "char_count": 5000,
    "word_count": 850,
    "file_type": "pdf"
  },
  "chunks_count": 5
}
```

### List Documents

```
GET /api/documents
Authorization: Bearer <token>

Response: 200 OK
{
  "documents": [
    {
      "doc_id": "uuid-1",
      "filename": "contract.pdf",
      "file_type": "pdf",
      "uploaded_at": "2025-11-17T10:30:00",
      "processed": "completed"
    }
  ]
}
```

### Analyze Document

```
POST /api/documents/{doc_id}/analyze
Authorization: Bearer <token>

Body:
{
  "query": "Summarize this document",
  "type": "comprehensive"  // comprehensive, summary, specific, qa
}

Response: 200 OK
{
  "doc_id": "uuid-here",
  "analysis": "...",
  "key_elements": {...},
  "metadata": {...}
}
```

### Delete Document

```
DELETE /api/documents/{doc_id}
Authorization: Bearer <token>

Response: 200 OK
{
  "message": "Document deleted successfully"
}
```

## Query Endpoints

### Basic Query

```
POST /api/query
Authorization: Bearer <token>

Body:
{
  "query": "What is Section 420 IPC?",
  "mode": "short"  // short or detailed
}

Response: 200 OK
{
  "query": "What is Section 420 IPC?",
  "response": "Section 420 of IPC deals with cheating...",
  "role": "lawyer",
  "timestamp": "2025-11-17T10:30:00"
}
```

### Agent Query (with Tools)

```
POST /api/agent/query
Authorization: Bearer <token>

Body:
{
  "query": "Find cases related to Section 420",
  "max_iterations": 10
}

Response: 200 OK
{
  "query": "Find cases related to Section 420",
  "answer": "...",
  "tools_used": [
    {"tool": "search_legal_cases", "result": "..."}
  ],
  "iterations": 3,
  "sources": [...],
  "confidence": 0.92
}
```

## RAG Endpoints

### Search Documents

```
POST /api/rag/search
Authorization: Bearer <token>

Body:
{
  "query": "contract termination clauses",
  "top_k": 5
}

Response: 200 OK
{
  "query": "contract termination clauses",
  "results": [
    {
      "chunk_id": "uuid_0",
      "doc_id": "uuid",
      "text": "...",
      "similarity": 0.89,
      "doc_title": "contract.pdf"
    }
  ]
}
```

### Query Document

```
POST /api/rag/documents/{doc_id}/query
Authorization: Bearer <token>

Body:
{
  "question": "What are the payment terms?"
}

Response: 200 OK
{
  "doc_id": "uuid",
  "question": "What are the payment terms?",
  "answer": "The payment terms are...",
  "sources": [...]
}
```

### Compare Documents

```
POST /api/rag/documents/compare
Authorization: Bearer <token>

Body:
{
  "doc_id1": "uuid-1",
  "doc_id2": "uuid-2"
}

Response: 200 OK
{
  "similarity": 0.75,
  "common_topics": [...],
  "unique_to_doc1": [...],
  "unique_to_doc2": [...]
}
```

## User Endpoints

### Get User History

```
GET /api/user/{user_id}/history
Authorization: Bearer <token>

Response: 200 OK
{
  "chat_history": [...],
  "agent_history": [...],
  "preferences": {...}
}
```

### Update Preferences

```
POST /api/user/preferences
Authorization: Bearer <token>

Body:
{
  "practice_area": "criminal",
  "response_style": "detailed",
  "citation_format": "bluebook"
}

Response: 200 OK
{
  "message": "Preferences updated successfully"
}
```

### Get Preferences

```
GET /api/user/preferences
Authorization: Bearer <token>

Response: 200 OK
{
  "preferences": {
    "practice_area": "criminal",
    "response_style": "detailed"
  }
}
```

## System Endpoints

### Status Check

```
GET /api/status

Response: 200 OK
{
  "status": "running",
  "version": "2.0.0",
  "services": {
    "orchestrator": true,
    "reasoning_engine": true,
    "rag_tool": true
  },
  "database": "connected"
}
```

---

# Troubleshooting

## Common Issues

### 1. "GOOGLE_API_KEY not configured"

**Problem:** Gemini API key missing or invalid

**Solution:**

```bash
# Add to .env file
GOOGLE_API_KEY=your_actual_api_key_here

# Verify
python -c "from config import Config; print(Config.GOOGLE_API_KEY[:10])"
```

### 2. "Could not extract text from PDF"

**Problem:** PDF is image-based (scanned)

**Solutions:**

1. Install OCR dependencies (see OCR Setup section)
2. Convert PDF to text-based format
3. Upload as `.txt` file instead

### 3. "ChromaDB collection not found"

**Problem:** Vector database not initialized

**Solution:**

```python
# Reinitialize ChromaDB
from modules.document_rag_chromadb import ChromaDBRAGTool
rag = ChromaDBRAGTool(storage_path="chromadb_storage")
```

### 4. "JWT token expired"

**Problem:** Authentication token expired (24h default)

**Solution:**

- Log out and log back in
- Token automatically refreshed

### 5. "Database locked" (SQLite)

**Problem:** Concurrent access conflict

**Solutions:**

```python
# Use connection pooling
from sqlalchemy.pool import StaticPool

engine = create_engine(
    'sqlite:///luminary.db',
    poolclass=StaticPool,
    connect_args={'check_same_thread': False}
)
```

### 6. Slow Document Processing

**Causes:**

- Large files (>10MB)
- Image-based PDFs requiring OCR
- Complex document structure

**Solutions:**

- Split large documents
- Use text-based PDFs when possible
- Process in background (async)

### 7. Memory/Preferences Not Saving

**Problem:** Encryption key missing or invalid

**Solution:**

```python
# Generate new key
from cryptography.fernet import Fernet
key = Fernet.generate_key()

# Add to .env
ENCRYPTION_KEY=<generated_key>
```

---

## 📄 Disclaimer

⚠️ **Important Legal Notice:**

LuminaryAI is an AI-powered research assistant and **should NOT be considered a substitute for professional legal advice**. While we strive for accuracy:

- AI-generated responses may contain errors or omissions
- Laws change frequently; always verify with current statutes
- Consult qualified legal professionals for specific legal matters
- Do not rely solely on AI for legal decisions

**Use responsibly and verify all information independently.**

---

## 📞 Support & Contact

- **GitHub Issues:** https://github.com/HitkarMiglani/legal_Test/issues
- **Documentation:** This file (COMPLETE_DOCUMENTATION.md)

---

## 📜 License

This project is licensed under the MIT License.

---

**Last Updated:** November 17, 2025  
**Version:** 2.0.0  
**Author:** HitkarMiglani, Keshav and Gurleen Kaur Baxi
