# 🧠 Cancer Chatbot using RAG (Retrieval-Augmented Generation)

A medical assistant chatbot designed to answer cancer-related questions using RAG and LLM technology (Groq's LLaMA3-8B). It retrieves the most relevant context from a cancer Q\&A dataset and generates human-like, medically accurate responses.

---

## 📂 Project Structure

```bash
cancer-chatbot-rag/
├── cancer-chatbot.ipynb     # Core notebook with RAG implementation
└── README.md                # This documentation
```

---

## ⚙️ How It Works

### 1. 🔍 **Retrieval Step**

* **Embedding model**: `all-MiniLM-L6-v2` from SentenceTransformers.
* The dataset of cancer-related Q\&A pairs is embedded.
* Given a query, cosine similarity is used to retrieve the most similar question and its corresponding answer.

### 2. 🧠 **Augmented Generation Step**

* The retrieved answer becomes the context.
* The LLM (`llama3-8b-8192` via Groq API) uses this context to generate a new, doctor-style response.
* Responses avoid copy-pasting and instead rephrase concisely and informatively.

---

📂 Dataset

We use the Cancer Q&A Dataset from Kaggle, which includes questions and answers about various cancer topics.

🔗 Dataset URL: Cancer Q&A Dataset on Kaggle

## 📉 Training Details

While this project does not include a training phase for the language model (LLM is accessed via API), some processing and thresholds include:

* Cosine similarity threshold: `0.5` to ensure relevance
* Filtering out unrelated domains (e.g., diabetes, Alzheimer’s)

---

## 🧪 Example Queries

```
Q: what is metastasis in general?
A: Metastasis refers to the spread of cancer cells from the primary tumor to distant organs through the blood or lymph system... [detailed medical explanation follows]

Q: hey i was just diagnosed with breast cancer what are the following steps i should do
A: Firstly, take a deep breath. Breast cancer is treatable. Here's what to do next: 1) Meet with your oncologist... [7-step action plan]
```

---

## 🔥 LLM Details (Groq API)

* **Model**: LLaMA 3 8B (8192 token context)
* **Temperature**: `0.3` for focused output
* **System Prompt**: Custom instructions to act like a professional doctor

---


## 🚀 Future Improvements

* Support for multi-condition Q\&A (expand beyond cancer)
* Fine-tune retrieval embeddings using domain-specific sentence transformers
* Integrate human feedback loop for more reliable generation

---

## 🧠 Requirements

```bash
pip install sentence-transformers
pip install numpy pandas scikit-learn groq
```

---

📜 License & Disclaimer

This project is intended for educational purposes only. It is not a substitute for professional medical advice, diagnosis, or treatment. Always consult your physician.

🙌 Acknowledgments

HuggingFace for SentenceTransformer models

Groq for LLM API access

Kaggle dataset for cancer-related Q&A

🔐 Security Notes

API keys are stored using environment variables.

Groq API usage is rate-limited and should be secured.
