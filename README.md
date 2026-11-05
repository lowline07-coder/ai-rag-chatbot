# 📄 AI RAG Chatbot (AI Learning Coach)

**AI RAG Chatbot** is a Retrieval-Augmented Generation (RAG) application that lets you chat with your own PDF documents. Upload one or more PDFs, ask questions in natural language, and get answers grounded **only** in the content of your files. If the answer isn't in the documents, the bot says so instead of making something up.

It is built with Streamlit, LangChain, HuggingFace embeddings, ChromaDB and Groq-hosted LLMs, and is designed as a study aid for students, learners and anyone who needs quick answers from long documents.

---

## ✨ Features

- Upload multiple PDF files at once
- Automatic text extraction and chunking
- Semantic search using HuggingFace sentence embeddings
- Vector storage with ChromaDB
- Answers generated strictly from retrieved context (reduces hallucination)
- Chat interface with conversation history
- Clear fallback message when information is not found

## 🛠️ Technology Stack

- Python 3.11+
- Streamlit
- LangChain
- HuggingFace Embeddings (`all-MiniLM-L6-v2`)
- ChromaDB
- Groq API (`openai/gpt-oss-20b`)
- python-dotenv

## 📁 Folder Structure

```
AI_RAG_CHATBOT/
│
├── app.py                  # Streamlit UI and app flow
├── .env                    # API keys (never commit this)
├── requirements.txt        # Python dependencies
├── doc_files/              # Sample PDFs for testing
├── assets/                 # Screenshots and images
├── utils/
│   ├── __init__.py
│   ├── document_loader.py  # PDF loading and chunking
│   ├── vector_store.py     # Embeddings and Chroma retriever
│   └── rag_chain.py        # Prompt, LLM and answer generation
└── README.md
```

## 🧠 How It Works

1. **Upload**: PDFs are read with `PyPDFLoader`.
2. **Chunk**: Text is split into 1000-character chunks with 200-character overlap.
3. **Embed**: Each chunk is converted to a vector using `all-MiniLM-L6-v2`.
4. **Store**: Vectors are saved in ChromaDB.
5. **Retrieve**: For each question, the top 3 most relevant chunks are fetched.
6. **Generate**: The Groq LLM answers using only those chunks as context.

## 🚀 Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/<your-username>/ai-rag-chatbot.git
cd ai-rag-chatbot
```

### 2. Create a virtual environment (recommended)

```bash
python -m venv venv
source venv/bin/activate      # On Windows: venv\Scripts\activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Add your Groq API key

Get a free key from the [Groq Console](https://console.groq.com/keys), then edit `.env`:

```
GROQ_API_KEY=your_groq_api_key_here
```

### 5. Run the app

```bash
streamlit run app.py
```

The app opens at `http://localhost:8501`.

## 💬 Usage

1. Upload one or more PDFs (you can try the files in `doc_files/`).
2. Wait for the "PDFs processed" message.
3. Ask questions in the chat box.

## 🔐 Security Note

Never upload your `.env` file to GitHub. It is already listed in `.gitignore`.

## 🔮 Future Improvements

- Show source page numbers with each answer
- Conversation memory for follow-up questions
- Support for DOCX and TXT files
- Persistent vector store across sessions
- Option to choose different LLMs

## 📄 License

This project is open source and available under the [MIT License](LICENSE).
