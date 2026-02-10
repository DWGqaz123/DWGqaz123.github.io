---
title: "AI-Powered Real-Time Memory Assistant"
date: 2026-01-15
summary: "A macOS-native productivity tool that turns voice conversations into structured knowledge with real-time transcription, intelligent summarization, and local semantic search"
tags: 
  - AI/ML
  - macOS
  - Full-Stack
  - RAG
tech_stack:
  - Swift
  - SwiftUI
  - Python
  - FastAPI
  - OpenAI GPT-4
  - ElevenLabs
  - FAISS
  - SentenceTransformers
  - SQLite
  - WebSocket
links:
  - type: github
    url: https://github.com/DWGqaz123/realtime_transcriber_WG
    label: Source Code
  - type: download
    url: https://github.com/DWGqaz123/realtime_transcriber_WG/releases/latest
    label: Download v1.0.1
featured: true
status: "Released"
role: "Solo Developer"
duration: "3 months"
highlights:
  - "Sub-100ms transcription latency"
  - "Local semantic search with FAISS"
  - "Privacy-first: all data stored locally"
  - "Real-time structured summarization"
---

A full-stack AI application designed to close the loop between **capturing information** and **retrieving knowledge**. Unlike traditional recorders that leave you with hours of raw audio, this assistant acts as a "second brain".

## 🎯 Problem & Solution

**The Problem**: Taking notes during meetings/lectures is distracting, but raw recordings are nearly impossible to search through later.

**The Solution**: A three-stage pipeline that:
1. **Listens** - Low-latency transcription using ElevenLabs Scribe (<100ms)
2. **Thinks** - Context-aware summarization every ~120 seconds using GPT-4
3. **Remembers** - Local semantic search via FAISS vector embeddings

## ✨ Key Features

### Real-Time Intelligence
- **Live Transcription**: Sub-100ms latency speech-to-text integration
- **Smart Ticker**: Generates structured summaries (bullet points & action items) without interrupting flow
- **Adaptive Triggering**: Hybrid algorithm ensures summaries at natural pauses, not arbitrary cuts
- **Dual Mode**: Switch between 'Lecture' and 'Discussion' capture modes

### Long-Term Memory (RAG)
- **Local Vectorization**: CPU-based embeddings using `paraphrase-multilingual-MiniLM-L12-v2` (~6 texts/sec)
- **Semantic Search**: FAISS-powered similarity search - find content by meaning, not keywords
- **Zero API Cost**: All embeddings and storage handled locally
- **Asynchronous Indexing**: Non-blocking background indexing keeps UI responsive

### Privacy First
- All vector embeddings stored locally on user's machine
- SQLite + FAISS databases never leave your device
- No cloud storage of sensitive conversation data

## 🏗 Technical Architecture

### Double-Container Pipeline

Solved the core race condition between continuous WebSocket streaming and latent LLM inference:
```
WebSocket Stream → Ingestion Buffer → [Atomic Transfer] → Processing Snapshot
                                                               ↓
                                                          GPT-4 Summary
                                                               ↓
                                                     SQLite + Frontend
```

**Key Innovation**: Separate ingestion and processing buffers enable atomic transfers, preventing data loss during LLM inference delays.

### Local RAG Engine

Privacy-focused Retrieval-Augmented Generation:

1. **Ingest**: Chunk finished sessions into semantic segments
2. **Embed**: Convert to 384-dim vectors using local CPU (no API calls)
3. **Index**: Store in FAISS IndexFlatIP for efficient cosine similarity
4. **Retrieve**: Query vectorization + Top-K matching for relevant segments

### Context Management
- Extracts last 3 sentences from each snapshot
- Injects into next GPT-4 prompt for continuity
- Maintains conversation flow across summary boundaries

## 🛠 Tech Stack Details

**Backend (Python 3.10+)**
- FastAPI for async web server
- WebSockets for real-time communication
- SQLAlchemy + SQLite for data persistence
- OpenAI API for summarization
- ElevenLabs Scribe v2 for STT
- SentenceTransformers for local embeddings
- FAISS for vector indexing

**Frontend (macOS native)**
- Swift 5 + SwiftUI
- MVVM + Combine architecture
- AVFoundation for audio capture
- Real-time WebSocket client

**Infrastructure**
- Conda for Python environment management
- Xcode 14.0+ for iOS/macOS development
- Local-first data architecture

## 📊 Performance Metrics

- **Transcription Latency**: <100ms average
- **Embedding Speed**: ~6 texts/second (CPU only)
- **Summary Generation**: ~3-5 seconds (depends on text length)
- **Search Response**: <200ms for typical queries
- **Storage Footprint**: ~50MB per hour of conversation

## 🎓 Technical Challenges & Solutions

### Challenge 1: Race Conditions in Streaming
**Problem**: LLM inference takes 3-5 seconds while WebSocket pushes new data every 100ms

**Solution**: Double-container buffering with atomic transfers - ingestion never blocks processing

### Challenge 2: Summary Coherence
**Problem**: Time-based triggers created summaries mid-sentence

**Solution**: Hybrid algorithm combining time threshold + sentence count + semantic integrity checks

### Challenge 3: Search Quality vs Speed
**Problem**: Cloud-based embedding APIs too slow/expensive for real-time use

**Solution**: Local CPU embeddings with FAISS IndexFlatIP - 6x faster than API calls with zero cost

## 🚀 Future Roadmap

- [ ] iOS companion app
- [ ] Multi-language transcription support
- [ ] Custom embedding model fine-tuning
- [ ] Export to Notion/Obsidian
- [ ] Team collaboration features
- [ ] Advanced analytics dashboard

## 🎯 Use Cases

- **Students**: Capture lectures and search by topic later
- **Researchers**: Interview transcription with semantic retrieval
- **Professionals**: Meeting notes with automatic action items
- **Creatives**: Brainstorming sessions with idea clustering

## 📖 Lessons Learned

1. **Local-First > Cloud-First**: Privacy wins user trust; local processing is fast enough for most use cases
2. **Architecture Matters**: The double-buffer pattern solved weeks of debugging race conditions
3. **Context is King**: Even 3 sentences of context drastically improved summary coherence
4. **User Testing**: Real users revealed edge cases (accents, background noise) we hadn't considered

---

**Project Status**: ✅ Released (v1.0.1)  
**GitHub**: [View Source](https://github.com/DWGqaz123/realtime_transcriber_WG)  
**Download**: [Latest Release](https://github.com/DWGqaz123/realtime_transcriber_WG/releases/latest)

*Built with ❤️ at Carnegie Mellon University*