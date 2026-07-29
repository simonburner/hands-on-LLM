## Chapter 5: Text Clustering and Topic Modeling

## Key takeaways
- Clustering differs from classification in that it's an unsupervised learning method that groups unlabeled data to topics based on how similar it is.
- A common pipeline for text clustering is:
  1. Convert the data to embeddings with an embedding model.
  2. Reducing the dimensionality of the embeddings to simplify computation. There is a balance between reducing dimensionality and keeping as much imformation as possible. Well-known methods are Principal Component Analysis (PCA) and Uniform Manifold Approximation and Projection (UMAP).
  3. Cluster the reduced embeddings. Well-known clustering algorithms are centroid-based and density-based (which allows for outliers). In the project below HDBSCAN (a density-based algorithm) is used.
    
     <img width="588" height="312" alt="Screenshot 2026-07-25 at 17 42 47" src="https://github.com/user-attachments/assets/be341f21-07af-4709-83c5-461d11e70a11" />
     
- The next step up from text clustering could be topic modeling, if we want to describe what each cluster is about. In other words, topic modeling involves finding a set of keywords that best define the meaning of a topic.
- In the project below, BERTopic is used for topic modeling, which extends the above described pipeline. BERTopic does this implementing a bag-of-words count-vectorizer and subsequently a c-TF-IDF operation, which gives word importance based on how many times they appear in a cluster.

    <img width="636" height="110" alt="Screenshot 2026-07-25 at 17 56 51" src="https://github.com/user-attachments/assets/320a7e37-49ac-446b-9031-53dc3e8c5eab" />
    
<br/><br/>

  <img width="634" height="249" alt="Screenshot 2026-07-25 at 17 56 36" src="https://github.com/user-attachments/assets/09af31da-4ba0-4a61-9b5e-9742340ba47c" />

- An advantage of BERTopic is how modular it is:

  <img width="418" height="279" alt="Screenshot 2026-07-25 at 17 57 30" src="https://github.com/user-attachments/assets/0ce5079a-6ed7-4abe-8753-7aa35e6eb5e6" />

- To further specify the topic of a cluster, we can use maximal marginal relevance, which avoids topic representations that are similar. 

### Projects
- **arXiv-dataset-clustering:** the above described methods are carried out in practice. Used a slightly different embedding model and text generation model, due to performance and library deprecation reasons.
