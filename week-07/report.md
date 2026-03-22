# Week 7: RAG Security Knowledge Assistant — Evaluation Report

## 1. Setup Summary
- **LLM:** llama-3.3-70b-versatile via Groq
- **Embeddings:** sentence-transformers/all-MiniLM-L6-v2 via HuggingFace
- **Vector Store:** In-Memory Vector Store
- **Documents loaded:** govern.txt, responde.txt, mitre-credential-access.txt, mitre-initial-access, mitre-lateral-movement. 

## 2. Test Results

| # | Question | Used Documents? | Quality | Notes |
|---|----------|----------------|---------|-------|
| 1 | What are common techniques for credential access according to MITRE? | Yes | Good | Answered well, could look better if more constraints are added. |
| 2 | How does phishing relate to initial access in the ATT&CK framework | Yes | Good | Did a good job of explaining. |
| 3 | What is lateral movement and what techniques do attackers use? | Yes | Good | I like the way it talks out the techniques. |
| 4 | What does the NIST framework recommend for the Detect function? | No | Wrong | If I included the detect function in the database, it would have given me the right response. It does a good job of admitting it doesn’t know instead of hallucinating. |
| 5 | What is the difference between spearphishing attachment and spearphishing link? | Yes | Good | It explained the difference very well.|

## 3. Edge Case Observations
- **Unrelated question:** Whenever I asked the chatbot something off-topic, it would just tell me, "Hmm, I'm not sure", or it would tell me there wasn't enough info to give based on what I specifically asked regarding the MITRE ATT&CK or NIST framework.
- **Topic not in documents:** No matter what, it never hallucinated, it just admitted that it did not know or if something was mentioned in relation but admits there is not enough context to fully give an answer.

## 4. Settings Experiments 
- **Temperature change:** Increasing temperature from 0.3 to 0.7 had made responses less consistent and more varied in wording. At 0.3 the answers were more precise and stuck closer to the document content, while 0.7 produced more conversational but  occasionally less accurate answers.
- **Chunk size change:** educing chunk size from 1000 to 500 made retrieval more precise but responses sometimes lacked enough surrounding context to give a complete answer. Larger chunks gave more context but occasionally pulled in less relevant surrounding text.
- **Top K change:** Increasing Top K from 4 to 6 brought in more document chunks per response, which helped with broader questions but sometimes added unnecessary information. Reducing to 2 made answers more focused but risked missing relevant content.

## 5. Reflection
- What surprised me most was how the quality of answers directly depends on the quality and size of the documents uploaded. The chatbot could only answer well when the exact topic was covered in the documents. It didn't just simply "know" things like a regular chatbot would.
- I would replace the in-memory vector store with a persistent one like Pinecone or Chroma so documents don't need to be reprocessed every session. I would also expand the knowledge base with more complete MITRE ATT&CK and NIST documentation, and fine-tune the chunk size and Top K settings based on more thorough testing.
- How I might use RAG in my capstone project would be in adding common information and data about the alerts that SOC analysts would normally come to face with. That way if the analyst is not familiar with the alert or how to handle it, they can just use the chatbot for assistance. 
