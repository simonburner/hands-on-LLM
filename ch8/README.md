## Chapter 8: Semantic Search and Retrieval-Augmented Generation

### Key takeaways

- Semantic search: enables searching content by meaning, and not simply keyword matching.
- RAG: system that retrieves relevant up-to-date information and provides it to the LLM to generate more factual answers.

There's a lot of research on how LLMs are best used for search, the broad categories of these models are **dense retrieval**, **reranking** and **RAG**.

#### Dense retrieval

The LLM converts both the query and documents into embedding and retrieves the document embeddings what are nearest to the query embeddings.

#### Reranking

Tasked with scoring the relevance of a subset of document results against the query. Based on these scores, the order of importance of the documents is changed.

#### RAG

