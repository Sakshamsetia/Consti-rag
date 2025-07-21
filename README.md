# 🏛️ Constitution QA Chatbot
Conversational Retrieval-Augmented Generation (RAG) app that answers questions about the Indian Constitution using Gemini-2 Flash, LangChain LCEL, FAISS, HuggingFace embeddings, and Gradio.

---

## ✨ Features
- **Keyword Extraction** – Gemini returns 5 + relevant keywords per query.  
- **Context-Aware Answers** – Combines Gemini knowledge with retrieved PDF passages.  
- **FAISS Retrieval** – Fast vector similarity search over embedded pages.  
- **HuggingFace Embeddings** – `all-MiniLM-L6-v2` sentence encoder.  
- **Gradio Chat UI** – One-click local web interface.  
- **LangChain LCEL Pipeline** – Clean, composable Runnable chain.

---

## 🛠️ Tech Stack
Gemini API · LangChain-core · LangChain-community · FAISS · HuggingFace Embeddings · Gradio · python-dotenv

---

## 📁 File Structure
repo/  
├── assets/  
│   └── constitution.pdf  
├── Model.ipynb   
├── requirements.txt  
└── .env      

---

## 🚀 Setup Instructions
1. **Clone the repo**  
       git clone https://github.com/Sakshamsetia/Consti-rag
       cd Consti-rag  

2. **Install dependencies**  
       pip install -r requirements.txt  

3. **Add your Gemini API key**  
       add .env and set GEMINI_API_KEY=your_key  

4. **Run the app**  
       python app.py  
        Gradio will print a local URL
---

## ⚙️ How It Works
1. **Load PDF** – `PyPDFLoader` splits *constitution.pdf* into pages.  
2. **Embed Pages** – Each page is embedded via HuggingFace `all-MiniLM-L6-v2`.  
3. **Build Vector Store** – All vectors are indexed with FAISS.  
4. **Keyword LLM Call** – Gemini Flash outputs ≥ 5 keywords for the user query.  
5. **Retrieve Context** – Keywords form a search string; FAISS returns top-5 pages.  
6. **Construct Prompt** – LangChain `ChatPromptTemplate` injects context + question.  
7. **Generate Answer** – Custom Gemini chat model produces the final response.  
8. **Serve via Gradio** – The chain runs behind a chat interface.