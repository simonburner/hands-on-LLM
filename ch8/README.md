# Chapter 8: Semantic Search and Retrieval-Augmented Generation

## Key takeaways

- Semantic search: enables searching content by meaning, and not simply keyword matching.
- RAG: system that retrieves relevant up-to-date information and provides it to the LLM to generate more factual answers.

There's a lot of research on how LLMs are best used for search, the broad categories of these models are **dense retrieval**, **reranking** and **RAG**.

### Dense retrieval

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

### Reranking

Tasked with scoring the relevance of a subset of document results against the query. Based on these scores, the order of importance of the documents is changed.

<img width="568" height="210" alt="Screenshot 2026-07-29 at 14 33 29" src="https://github.com/user-attachments/assets/5211b4f9-0c3b-489b-a887-b3095e7704ee" />

A popular way to build LLM search rerankers is by presenting each possible result to the model together with the query independently, which produces a relevance score:

<img width="568" height="156" alt="Screenshot 2026-07-29 at 14 54 49" src="https://github.com/user-attachments/assets/5c8c407b-6d4f-4ce5-8877-5109d7ee5dd3" />

### RAG

<img width="592" height="257" alt="Screenshot 2026-07-29 at 15 16 43" src="https://github.com/user-attachments/assets/820a270f-3d2c-43e0-828b-e9810eaa1c15" />

RAG systems include search and generation abilities, improving on generation models as they reduce their hallucinations and provide more factual answers.

To make a RAG system out of a search system, we add a LLM to the end of the search pipeline. We present the question and the top ranked retrieved documents to the LLM and ask it to answer the question based on the context that is provided. This generation step is called **grounded generation** because the retrieved relevant
information we provide the LLM establishes a certain context that grounds the LLM in the domain we’re interested in.

<img width="601" height="726" alt="Screenshot 2026-07-29 at 15 27 16" src="https://github.com/user-attachments/assets/0940297e-d732-4210-aa6a-a7ebc21c7d6a" />

- Advanced RAG Techniques:
  - Query rewriting: if a question is very verbose, we can use a LLM to rewrite the query into one that helps the retrieval step in getting the right information.
  - Multi-query RAG: we can extend the query rewriting to be able to search multiple queries if more than one is needed to answer a question.
  - Multi-hop RAG: a complex question may require a series of sequential queries. For example:
      *User Question: “Who are the largest car manufacturers in 2023? Do they each make EVs or not?”*  
      *Step 1, Query 1: “largest car manufacturers 2023”*  
      *Step 2, Query 1: “Toyota Motor Corporation electric vehicles”*  
      *Step 2, Query 2: “Volkswagen AG electric vehicles”*  
      *Step 2, Query 3: “Hyundai Motor Company electric vehicles”*
  - Query routing: giving the model the ability to search multiple data sources. For example, accessing a company's HR or CRM program.
  - Agentic RAG

## Useful links

- [Open source retrieval and reranking with sentence transformers](https://www.sbert.net/examples/sentence_transformer/applications/retrieve_rerank/README.html)

