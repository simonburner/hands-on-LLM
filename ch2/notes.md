<img width="814" height="596" alt="Screenshot 2026-07-16 at 22 58 09" src="https://github.com/user-attachments/assets/268d98d3-a1d2-4f40-897f-9bf05e6b1a61" />

Helpful links:  
[Tokenization summary by HuggingFace](https://huggingface.co/docs/transformers/tokenizer_summary)\
[More in depth tokenization (+training) by HuggingFace](https://huggingface.co/learn/llm-course/chapter6/1)

*Look at what the difference is between WordPiece/SentencePiece/BPE in more detail

When a token gets embedded in the form of a vector, the dimension of said vector is the same throughout the model (at this embedding stage). Then, the dimension of these vectors changes as the context of the input is taken into account.
