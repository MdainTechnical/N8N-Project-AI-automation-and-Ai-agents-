# 🤖 RAG Chatbot — n8n, OpenAI & Pinecone

An AI-powered Restaurant RAG Chatbot built using n8n, OpenAI, and Pinecone Vector Store.

## 📌 Overview

This project allows users to upload documents and ask questions through a chat interface. The AI Agent retrieves relevant information from the knowledge base to generate answers.

The assistant is configured for Royal Thali & Tandoor restaurant.

## ✨ Features

- Document upload through an n8n form
- OpenAI embeddings for document vectorization
- Pinecone vector storage and retrieval
- AI-powered question answering
- GPT-4o mini integration
- Simple Memory for conversational context
- Knowledge-based responses with fallback handling

## 🛠️ Tech Stack

- n8n
- OpenAI GPT-4o mini
- OpenAI Embeddings
- Pinecone Vector Database
- AI Agent
- Simple Memory

## 🔄 Workflow

1. Upload a document through the form.
2. Process the document using the data loader.
3. Generate embeddings using OpenAI.
4. Store document vectors in Pinecone.
5. Ask questions through the chat interface.
6. Retrieve relevant information from Pinecone.
7. Generate an AI response using the Agent.

## 🚀 Setup

1. Import `RAG Chatbot.json` into n8n.
2. Configure OpenAI credentials.
3. Configure Pinecone credentials and the required index.
4. Upload a supported document.
5. Open the chat interface and test your questions.

## 🔐 Security

Never publish API keys, private credentials, or confidential documents. Review the exported workflow before making it public.

## 👨‍💻 Author

**MDAinTechnical**

GitHub: https://github.com/MdainTechnical

---

⭐ Built as a practical project to learn RAG, AI Agents, vector databases, and workflow automation.

