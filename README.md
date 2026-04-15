🧠 Agentic Multi-Source RAG Copilot

Production-grade Agentic Retrieval-Augmented Generation (RAG) system built using Semantic Kernel, Azure OpenAI, and Azure AI Search.
This project demonstrates multi-step reasoning, tool-calling agents, and hybrid retrieval to generate grounded, context-aware responses.

🚀 Features
🤖 Agentic RAG Architecture
Semantic Kernel ChatCompletionAgent
Multi-step reasoning & planning
Dynamic tool invocation
🔍 Hybrid Retrieval
BM25 + Vector Search (Azure AI Search)
Context-aware document retrieval
Reduced hallucinations via grounded context
🔌 Plugin-Based System
Modular tool-calling architecture
Easily extensible for APIs / enterprise tools
🧠 Semantic Kernel Integration
Native Microsoft AI orchestration framework
Prompt pipelines and agent workflows
🏗️ Architecture
User Query
   ↓
Agent (Planner)
   ↓
Retriever Plugin → Azure AI Search
   ↓
Context Builder
   ↓
LLM (Azure OpenAI)
   ↓
Final Response + Validation
🛠️ Tech Stack
C#, .NET 8
Semantic Kernel (Microsoft)
Azure OpenAI Service
Azure AI Search
REST APIs
📂 Project Structure
/AgenticRAG
  /Controllers
  /Services
  /Plugins
  /Models
  /Constants
  Program.cs
