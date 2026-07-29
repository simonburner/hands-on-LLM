## Chapter 8: Semantic Search and Retrieval-Augmented Generation

### Key takeaways

- Semantic search: enables searching content by meaning, and not simply keyword matching.
- RAG: system that retrieves relevant up-to-date information and provides it to the LLM to generate more factual answers.

There's a lot of research on how LLMs are best used for search, the broad categories of these models are **dense retrieval**, **reranking** and **RAG**.

#### Dense retrieval

The LLM converts both the query and documents into embedding and retrieves the document embeddings what are nearest to the query embeddings.

One drawback of dense retrieval is that when a document doesn't include the answer to a query, we still get results and their distances. It's helpful to set a threshold for maximum distance, for example.

If we want to find an exact match for a specific phrase, it's better to go with a keyword matching approach. **Hybrid search** combines dense retrieval and keyword matching.

Dense retrieval systems don't work so well in fields the model hasn't been trained on.

If we only embed a representative part of the document, such as the tile, or the beginning of the document, the embedding leaves a lot of information out, therefore not searchable. To create meaningful embeddings, document chunking is necessary. The approaches of chunking are (in this book):

- One vector per document: embedding the document in chunks, embedding those chunks and then aggregating those chunks into a single vector (by averaging the vectors). However, this produces a highly compressed vector which also leaves a lot of information out.
- Multiple vectors per document: the document is chunked into smaller pieces and are embedded. The chunking approach is better as it captures more information of a document, which leads to a more expressive search index.

  <img width="563" height="269" alt="Screenshot 2026-07-29 at 14 10 27" src="https://github.com/user-attachments/assets/6faa47f5-71b0-4771-a187-208a1b295793" />
&nbsp;
  <img width="570" height="134" alt="Screenshot 2026-07-29 at 14 11 47" src="https://github.com/user-attachments/assets/a7281b67-49db-43e9-b0f0-ba2576eae2eb" />

These embedded chunks then get compared to the input query and the nearest neighbour is then presented as an answer.


#### Reranking

Tasked with scoring the relevance of a subset of document results against the query. Based on these scores, the order of importance of the documents is changed.

#### RAG

