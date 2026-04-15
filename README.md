# 🧠 Agentic RAG Service using .NET 8, Azure OpenAI & Semantic Kernel

A production-ready **Retrieval-Augmented Generation (RAG)** service built with **.NET 8**, **Microsoft Semantic Kernel**, **Azure OpenAI**, and **Azure AI Search**.

This project demonstrates both:
- ✅ Traditional RAG (retrieval + prompt injection)
- 🤖 Agentic RAG (multi-step reasoning with tool usage)

---

## 🚀 Features

- 🔎 Traditional RAG with hybrid retrieval (Azure AI Search)
- 🤖 Agentic RAG using Semantic Kernel Agents (`ChatCompletionAgent`)
- 🧠 Multi-step reasoning + tool calling
- 🌦 Plugin support (Weather plugin example)
- 🧩 Modular architecture (easy to extend)
- 📡 REST API endpoints for integration
- 📊 Structured responses with reasoning trace

---

## 🏗️ Architecture

```
User Query
   │
   ├──► Traditional RAG
   │       ├── Embed Query
   │       ├── Azure AI Search Retrieval
   │       ├── Prompt Construction
   │       └── Azure OpenAI Completion
   │
   └──► Agentic RAG
           ├── Agent Planning
           ├── Query Refinement
           ├── Tool Invocation (Plugins)
           ├── Iterative Reasoning
           └── Final Response
```

---

## 📁 Project Structure

```
AgenticRAG/
│
├── Controllers/
│   └── RagController.cs
│
├── Services/
│   ├── RagService.cs
│   ├── AzureSearchService.cs
│   └── OpenAIService.cs
│
├── Plugins/
│   └── WeatherPlugin.cs
│
├── Models/
│   └── RagRequest.cs
│
├── Program.cs
├── appsettings.json
└── Properties/
    └── launchSettings.json
```

---

## ⚙️ Configuration

Update your `launchSettings.json`:

```json
"environmentVariables": {
  "ASPNETCORE_ENVIRONMENT": "Development",
  "AZURE_OPENAI_URL": "https://<RESOURCENAME>.openai.azure.com",
  "AZURE_OPENAI_KEY": "<ADD_KEY>",
  "AZURE_AI_SEARCH_URL": "https://<RESOURCENAME>.search.windows.net",
  "AZURE_AI_SEARCH_KEY": "<ADD_KEY>",
  "EMBEDDING_DEPLOYMENT_NAME": "<EMBEDDING_MODEL>",
  "GPT_DEPLOYMENT_NAME": "<GPT_MODEL>",
  "INDEX_NAME": "<SEARCH_INDEX>"
}
```

---

## 🧪 Prerequisites

- .NET 8 SDK
- Azure OpenAI access
- Azure AI Search instance
- Semantic Kernel SDK

---

## ▶️ Running the Project

```bash
git clone https://github.com/your-username/AgenticRAG.git
cd AgenticRAG

dotnet restore
dotnet build
dotnet run
```

API will start at:
```
https://localhost:5001
```

---

## 📬 API Endpoints

### 🔹 Traditional RAG

```http
POST /rag/traditional
```

**Request**
```json
{
  "query": "Best hotels in Sedona"
}
```

---

### 🤖 Agentic RAG

```http
POST /rag/agentic
```

**Request**
```json
{
  "prompt": "Plan a weekend trip to Acadia National Park"
}
```

---

## 💡 Usage (Code)

### 🔎 Traditional RAG

```csharp
var result = await ragService.GenerateResponseUsingTraditionalRag(
    "Best hotels in Bar Harbor?"
);

Console.WriteLine(result);
```

### 🤖 Agentic RAG

```csharp
var result = await ragService.GenerateResponseUsingAgenticRag(
    "What's the weather like for a trip to Acadia National Park?"
);

Console.WriteLine(result);
```

---

## ⚡ How It Works

### Traditional RAG

1. Convert query → embedding
2. Retrieve documents from Azure AI Search
3. Inject context into prompt
4. Generate response using LLM

---

### Agentic RAG

1. Break query into sub-tasks
2. Optimize search queries
3. Retrieve relevant knowledge
4. Call tools (plugins)
5. Perform reasoning loop
6. Return:
   - Final Answer
   - Reasoning Trace
   - Tools Used

---

## 🧩 Plugins

### Weather Plugin Example

```csharp
kernel.ImportPluginFromType<WeatherPlugin>("searchWeather");
```

You can extend with:
- Database tools
- APIs
- Internal services
- Observability tools

---

## 🧱 Core Technologies

- .NET 8
- Microsoft Semantic Kernel
- Azure OpenAI
- Azure AI Search

---

## 🔐 Production Considerations

- Add authentication (JWT / Azure AD)
- Enable logging (Serilog / App Insights)
- Rate limiting & retries
- Secure key vault integration
- Observability (Prometheus / Grafana)

---

## 📈 Future Enhancements

- Multi-agent orchestration
- Streaming responses
- Memory (long-term context)
- Hybrid search (BM25 + Vector)
- UI dashboard (React / Blazor)

---

## 🤝 Contributing

Pull requests are welcome. For major changes, open an issue first.

---

## 📜 License

MIT License

---

## ⭐ Support

If you found this useful, give it a ⭐ on GitHub!

---
