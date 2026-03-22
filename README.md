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

## Test Questions Used
1. What are common techniques for credential access according to MITRE?
2. How does phishing relate to initial access in the ATT&CK framework?
3. What is lateral movement and what techniques do attackers use?
4. What does the NIST framework recommend for the Govern function?
5. What is internal spearphishing?

## Files
- `week-07-report.md` — Full evaluation report with test results and reflection
- `rag-documents/` — Knowledge base text files uploaded to the chatbot

See `report.md` for more.
