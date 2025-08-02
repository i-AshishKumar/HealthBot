# 🩺 HealthBot: A Medical Encyclopedia Chatbot

HealthBot is an AI-powered chatbot that answers medical questions using factual information from a medical encyclopedia. It combines OpenAI's GPT-4.0-mini with Hugging Face sentence transformer embeddings and a retrieval-augmented generation (RAG) pipeline. The goal is simple: provide accurate, grounded medical responses—not guesses.

![Diagram](https://i.ibb.co/ks3FFcq5/healthbot.png)

---

## 🚀 Features

- **Retrieval-Augmented Generation (RAG)**: Combines semantic search with OpenAI GPT for grounded responses.
- **Medical-Fact Based**: Powered by a trusted medical encyclopedia, not open web data.
- **Fast Semantic Search**: Uses Pinecone vector database for real-time document retrieval.
- **Local Embedding Pipeline**: Uses Hugging Face's `sentence-transformers` for embeddings.
- **Flask Web App**: Lightweight frontend for user interaction.

---

## 🧠 Tech Stack

| Component        | Tech                                       |
|------------------|--------------------------------------------|
| Language Model    | OpenAI gpt-4o                        |
| Embeddings        | `sentence-transformers` (Hugging Face)     |
| Vector Store      | Pinecone DB                                |
| Framework         | Flask (Python)                             |
| Data Source       | Medical Encyclopedia (curated static data) |

---


---

## ⚙️ Setup Instructions

### 1. Clone the Repository

```bash
git clone https://github.com/i-AshishKumar/HealthBot.git
cd HealthBot
```

### 2. Install Dependencies

Create a virtual environment and install the requirements:

```bash
python3 -m venv venv
source venv/bin/activate  # or venv\Scripts\activate on Windows
pip install -r requirements.txt
```

### 3. Set Up Environment Variables

Create a `.env` file in the root directory with the following:

```env
OPENAI_API_KEY=your_openai_key
PINECONE_API_KEY=your_pinecone_key
```

### 4. Prepare Your Vector Store

Before running the app, you need to embed your encyclopedia data and push it to Pinecone. Below command does that. You can add your own data souce files in "Data" folder

```bash
python store_index.py
```

### 5. Run the App

```bash
python app.py
```

Go to `http://localhost:8080` to start chatting with HealthBot.

---

## 🧩 How It Works

1. **User asks a question** via the UI.
2. **Query is embedded** using Hugging Face `sentence-transformers`.
3. **Semantic search**: top relevant chunks are pulled from Pinecone.
4. **Prompt construction**: these chunks are passed to GPT-4o as context.
5. **Response is generated** and returned to the user.

This pipeline ensures GPT responds based only on verified content from the source, not general pre-trained LLM knowledge.

---

## 📚 Data Source

All responses are grounded in a preloaded medical Gale encyclopedia of medicine 2nd edition.

---