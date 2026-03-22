# Week 7: RAG Security Knowledge Assistant

A retrieval-augmented generation (RAG) chatbot built with Flowise and Groq that answers 
cybersecurity questions using MITRE ATT&CK and NIST CSF documents as its knowledge base.

## Project Overview
This chatbot uses RAG to ground its answers in real security documentation rather than 
relying solely on the LLM's training data. When asked a question, it searches through 
uploaded documents to find relevant chunks before generating a response.

## Tech Stack
- **Flowise** — visual AI pipeline builder.
- **Groq (llama-3.3-70b-versatile)** — LLM for response generation.
- **HuggingFace Inference API** — embeddings model (sentence-transformers/all-MiniLM-L6-v2).
- **In-Memory Vector Store** — document chunk storage and similarity search.

## Pipeline Architecture
```
Text File Nodes → Character Text Splitter
                          ↓
HuggingFace Embeddings → In-Memory Vector Store
                          ↓
Groq               → Conversational Retrieval QA Chain
```

## Knowledge Base Documents
| File | Source | Topic |
|------|--------|-------|
| mitre-initial-access.txt | MITRE ATT&CK | Phishing and initial access techniques |
| mitre-credential-access.txt | MITRE ATT&CK | Credential theft techniques |
| mitre-lateral-movement.txt | MITRE ATT&CK | Internal movement techniques |
| govern.txt | NIST CSF | Governance framework categories |
| respond.txt | NIST CSF | Incident response framework |

## Live Chatbot
https://cloud.flowiseai.com/chatbot/7d827648-622a-474d-9455-541bb6310896

See report.md for more.
