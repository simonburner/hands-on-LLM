Helpful links:  
[Tokenization summary by HuggingFace](https://huggingface.co/docs/transformers/tokenizer_summary)\
[More in depth tokenization (+training) by HuggingFace](https://huggingface.co/learn/llm-course/chapter6/1)  

### Key takeaways:
- When a token gets embedded in the form of a vector, the dimension of said vector is the same throughout the model (at this embedding stage). Then, the dimension of these vectors changes as the context of the input is taken into account.

<img width="814" height="596" alt="Screenshot 2026-07-16 at 22 58 09" src="https://github.com/user-attachments/assets/268d98d3-a1d2-4f40-897f-9bf05e6b1a61" />

- Different models have different tokenization methods, this depends on the type of algorithm (i.e. BPE/WordPiece) but also the parameters we pass (such as special tokens, capitalization, vocabulary size) and the dataset the tokenizer is trained on. For example, a model developed to process and generate code, will have a dedicated token for indentation spaces.  
- In BERT models, which use WordPiece tokenization, the training of its tokenizer is as follows:
  1. Count how many times a word appears in a dataset.
  2. Create a list by splitting the words into indidivual characters (e.g. "hug" => "h" "##u" "##g").
  3. The vocabulary is created by only mentioning a character of a sequence of words once (if a character is repeated, it's not appended onto the vocabulary list).
  4. We select all frequent pairs of the list that was created in step ii and pass the following score function to them:

    <img width="676" height="51" alt="Screenshot 2026-07-17 at 13 26 53" src="https://github.com/user-attachments/assets/516aad20-ad55-41c1-8811-267146ca219b" />

  5. The pair with the highest result gets joined to a token and updated both in the vocabulary and the list created in step ii.
  6. The process is repeated from step iv until we reach the defined vocabulary size.

    To indicate if two or more subwords create a word, the ## characters are added to the beginning of a subword, indicating it's part of a bigger word. Tokens without ## are assumed to have a space before them.
- In GPT models, which use 
