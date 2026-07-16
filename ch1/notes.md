A complicated start! Followed the concepts without much issue until I reached "Encoding and Decoing Context with Attention", the foundation of the concept makes sense, however the broader "Attention" concept implemented in other architectures becomes hard to follow. The links below helped me understand the concepts a bit better.  

Helpful youtube videos:\
[RNNs explained by StatQuest](https://www.youtube.com/watch?v=AsNTP8Kwu80)\
[Attention explained by StatQuest](https://www.youtube.com/watch?v=PSs6nxngL6k)\
[Transformers explained by StatQuest](https://www.youtube.com/watch?v=zxQyTK8quyY)\
[Encoder-only transformers explained by StatQuest](https://www.youtube.com/watch?v=GDN649X_acE)\
[Decoder-only transformers explained by StatQuest](https://www.youtube.com/watch?v=bQ5BoolX9Ag)

As for the final exercise, I changed device_map to "auto" (instead of "cuda"), "cuda" didn't work on Colab. There seems to be some updates to the "transformers" library to include Phi-3 natively, consensus on the HuggingFace forum is to leave trust_remote_code out. Now a machine can take over my joke telling abilities, which wasn't hard in the first place! :)

Pending questions:
1. How does a model find the equivalent of a word in another language with context in mind?
2. Generative models are said to be Decoder-only, how is the input encoded to embeddings?
