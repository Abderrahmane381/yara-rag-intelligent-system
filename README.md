# 🛡️ Intelligent YARA Rule Generation System via RAG

> Automated YARA rule generation from natural language descriptions
> using RAG pipelines and local LLMs — no expert knowledge required.

---

## 📌 Overview

Writing YARA rules (used for malware detection) is complex and 
reserved for experts. This system allows any analyst to generate 
a YARA rule automatically from a simple natural language description,
combining NLP, RAG and a local LLM.

---

## 🏆 Key Results

| Model               | Score   |
|---------------------|---------|
| Mistral-7B-Instruct | 8.56/10 |
| Phi-2               | 4.20/10 |
| TinyLlama           | 0.00/10 |

### RAG Strategy Comparison

| RAG Strategy                  | Score   | Retrieval | Generation |
|-------------------------------|---------|-----------|------------|
| Classic (FAISS)               | 9.01/10 | 0.01s     | 54.23s     |
| Rerank (FAISS + CrossEncoder) | 9.01/10 | 0.58s     | 55.36s     |
| Agentic                       | 7.86/10 | 0.03s     | 53.51s     |
| Hybrid (FAISS + BM25)         | 6.84/10 | 0.01s     | 47.83s     |

###  Ranking 

| Rank | Strategy                      | Why                                   |
|------|-------------------------------|---------------------------------------|
|  1st | Classic (FAISS)               | Best score + lowest retrieval latency |
|  2nd | Rerank (FAISS + CrossEncoder) | Same score but slower retrieval       |
|  3rd | Agentic                       | Good score, adaptive behavior         |
|  4th | Hybrid (FAISS + BM25)         | Lowest score                          |

---

## 🏗️ Architecture

**5-step pipeline :**
1. User input (natural language)
2. Embedding (MiniLM-L6-v2)
3. Retrieval (4 strategies)
4. Prompt enrichment
5. LLM generation (Mistral-7B 4-bit quantized)

---

## 🗂️ Dataset

- 80 original YARA rules (30 manual + 50 synthetic)
- 6 malware families : ransomware, trojan, worm, 
  spyware, dropper, rootkit
- 100% original — no external source used

---

## 🛠️ Tech Stack

Python · FAISS · BM25 · CrossEncoder · LangChain · 
Mistral-7B · Gradio · HuggingFace · Google Colab

---

## 🚀 How to Run

```bash
pip install -r requirements.txt
python app.py
```

---

## 👤 Author

**Abderrahmane Belkasmi**
Master AI & Data Science 
[LinkedIn](https://www.linkedin.com/in/abderrahmane-belkasmi-ba3b64266)