# 🤖 AI Document Analyzer

An AI-powered document analysis automation built using **n8n, WhatsApp, Claude AI, and Google Gemini**.

## 📌 Overview

AI Document Analyzer allows users to send documents through WhatsApp and receive an AI-generated summary with important information, key points, and actionable insights.

## ✨ Features

- 📄 Document title and summary
- 🔑 Key points extraction
- 📅 Important dates and deadlines
- 💰 Amounts and prices extraction
- ⚠️ Risks and issues identification
- 👤 People and organizations extraction
- 📋 Action items and next steps
- 📲 Automated WhatsApp responses

## 🛠️ Technologies Used

- n8n — Workflow Automation
- WhatsApp Business Platform — Document Input and Responses
- Claude AI — Document Analysis
- Google Gemini — AI Agent
- Simple Memory — Conversation Context

## 🔄 Workflow

1. WhatsApp Trigger receives a document.
2. Switch node checks for document media.
3. HTTP Request retrieves and downloads the document.
4. Claude AI analyzes the document.
5. Google Gemini-powered AI Agent prepares the response.
6. WhatsApp sends the analysis to the user.

## 📂 Project Files

- `AI Document Analyzer (1).json` — Exported n8n workflow.
- `README.md` — Project documentation.
- `Screenshot 2026-10-26 175011.png` — Project workflow screenshot.

## 🚀 Setup

1. Import the JSON workflow into n8n.
2. Configure WhatsApp Business API credentials.
3. Configure Claude AI and Google Gemini access.
4. Verify document download and analysis settings.
5. Test the workflow by sending a sample document through WhatsApp.

## 🔐 Security

Never upload API tokens, access credentials, or private customer documents to a public repository. Review the workflow JSON before publishing.

## 👨‍💻 Author

**MDAinTechnical**

GitHub: [MDAinTechnical](https://github.com/MdainTechnical)

---

⭐ Built as a practical project to learn AI automation, API integration, and AI agent development.

