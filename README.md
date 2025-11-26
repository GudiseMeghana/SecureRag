# 🔐 SecureRAG – Multi-LLM Security & Verification Framework

SecureRAG is an end-to-end **LLM security and trust framework** designed to generate **safe, reliable, and verifiable AI responses**.
It combines **prompt-injection detection**, **Retrieval-Augmented Generation (RAG)**, and **cross-LLM verification** to prevent hallucinations, unsafe outputs, and malicious prompts.

---

## 📌 Key Features

### ✅ Prompt Injection Detection

* Uses a **RoBERTa-based classifier** to detect malicious or adversarial prompts.
* Rule-based filters catch explicit instruction overrides (e.g., "ignore previous instructions").
* Blocks unsafe prompts **before** they reach the LLM.

### ✅ Secure Retrieval-Augmented Generation (RAG)

* Knowledge is retrieved using **FAISS vector search + sentence-transformer embeddings**.
* Responses are constrained strictly to retrieved context.
* Automatically falls back to general LLM only when no verified context exists.

### ✅ Multi-LLM Cross Verification

* Independently queries:

  * **Gemini**
  * **Cohere**
* Each model verifies the answer using a structured verdict format:

  * ✅ Yes / ❌ No / ❓ Unsure
* Helps identify hallucinations and inconsistencies.

### ✅ Eligibility & Safety Scoring

Each response is evaluated on:

* Toxicity
* Banned topics
* Sensitive content
* Length constraints
* Language sanity

Produces a **final eligibility score** for every LLM output.

### ✅ Auto-Learning Knowledge Store

* When no RAG answer exists, the system:

  * Curates structured knowledge
  * Stores it back into the vector database
* Enables **continuous knowledge growth** without retraining.

### ✅ Interactive Gradio Dashboard

* Real-time query testing
* Displays:

  * Safety status (Blocked / Allowed)
  * RAG, Gemini, and Cohere answers
  * Verification verdicts
  * Eligibility scores
  * Sources used

---

## 🏗️ System Architecture

```
User Query
   ↓
Prompt Injection Guard (RoBERTa + Rules)
   ↓
RAG Retrieval (FAISS + Embeddings)
   ↓
Gemini Answer (Context-restricted)
   ↓
Cross-LLM Verification (Gemini + Cohere)
   ↓
Safety & Eligibility Scoring
   ↓
Gradio UI Dashboard
```

---

## 🛠️ Tech Stack

### Core

* **Python**
* **PyTorch**
* **Hugging Face Transformers**

### AI / NLP

* **RoBERTa** (Prompt Injection Detection)
* **Sentence-Transformers**
* **Gemini API**
* **Cohere API**

### Retrieval

* **FAISS**
* **Dense Vector Embeddings**

### Security & Safety

* Prompt Injection Protection
* Hallucination Detection
* Cross-Model Validation
* Eligibility & Trust Scoring

### UI & Platform

* **Gradio**
* **Google Colab**
* **Google Drive Integration**

---

## 🚀 Getting Started (Google Colab)

### 1️⃣ Open Notebook in Colab

Upload the project notebook to Google Colab.

### 2️⃣ Install Dependencies

```bash
pip install sentence-transformers transformers accelerate faiss-cpu google-generativeai cohere gradio
```

> **Note:** For reproducible builds, you may specify versions or use a `requirements.txt` file.

### 3️⃣ Mount Google Drive

```python
from google.colab import drive
drive.mount('/content/drive')
```

### 4️⃣ Set API Keys

```python
import os
os.environ["GOOGLE_API_KEY"] = "YOUR_GEMINI_KEY"
os.environ["COHERE_API_KEY"] = "YOUR_COHERE_KEY"
```

> ⚠️ **Security Warning:** Never hardcode API keys in your source code. Use environment variables, secret management services, or Colab's Secrets feature to securely manage credentials.

### 5️⃣ Place Required Data

* RoBERTa model:

```
/content/drive/MyDrive/<your-project-folder>/roberta_model_best/
```

* Knowledge text files:

```
/content/drive/MyDrive/<your-project-folder>/data/processed/
```

> **Note:** Replace `<your-project-folder>` with your actual Google Drive project directory path.

### 6️⃣ Run the Gradio UI

```python
demo.launch(share=True)
```

---

## 🖥️ Gradio UI Output

The dashboard displays:

* ✅ **Query Safety Status**
* 📄 **RAG Answer**
* 🤖 **Gemini Answer**
* 🧠 **Cohere Answer**
* 🧪 **Verification Verdicts**
* 📊 **Eligibility Scores**
* 🔗 **Knowledge Sources**

---

## 📊 Sample Output (Simplified)

```json
{
  "blocked": false,
  "rag": { "answer": "...", "eligibility": { "ec_score": 5 } },
  "gemini": { "answer": "...", "eligibility": { "ec_score": 5 } },
  "cohere": { "answer": "...", "eligibility": { "ec_score": 5 } }
}
```

---

## 🎯 Use Cases

* Secure enterprise LLM systems
* AI safety research
* Hallucination-resistant chatbots
* Knowledge-first AI assistants
* Trustworthy AI frameworks

---

## 🌟 Why SecureRAG?

✔ Not just a chatbot
✔ Focused on **AI Safety & Trust**
✔ Implements **real-world LLM security techniques**
✔ Interview-ready & resume-strong project

---

## 👤 Author

**Meghana Gudise**
📍 Computer Science | AI & ML
🔗 GitHub: [https://github.com/GudiseMeghana](https://github.com/GudiseMeghana)

---

## ⭐ If you find this project useful

Give it a ⭐ and feel free to fork or contribute!
