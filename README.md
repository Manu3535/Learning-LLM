**Medical FAQ Bot with RAG Pipeline**

This project is a Retrieval-Augmented Generation (RAG) pipeline built in Databricks, designed to answer medical queries using a combination of:
- Disease name matching
- Vector-based document retrieval
- Hugging Face language models
It intelligently filters user queries, matches them against known diseases, and generates context-aware answers using relevant source documents.

**Features**
- Stopword filtering to extract meaningful keywords from user queries
-  Disease name matching using a Delta table
-  Vector search to retrieve top-k relevant documents
-  Text generation using google/flan-t5-base via Hugging Face
-  Conditional response rendering based on disease presence in source documents
-  Databricks widget integration for interactive query input

**Workflow Summary**
- User Query Input:
- Captured via dbutils.widgets.get("query")
- Keyword Extraction:
- Removes stopwords and tokenizes the query
- Disease Matching:
- Compares query tokens with disease names from workspace.llm.diseases Delta table
- RAG Pipeline Execution:
- If a match is found:
- Loads flan-t5-base model
- Retrieves top 3 documents -  via vector store
- Generates an answer using LangChain's RetrievalQA
**- Answer Display**
- Displays the result only if the matched disease appears in the source documents


