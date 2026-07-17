## Notes

### Key takeaways:

- Different models have different tokenization methods, this depends on the type of algorithm (i.e. BPE/WordPiece) but also the parameters we pass (such as special tokens, capitalization, vocabulary size) and the dataset the tokenizer is trained on. For example, a model developed to process and generate code, will have a dedicated token for indentation spaces.  
- In BERT models, which use WordPiece tokenization, the training of its tokenizer is as follows:
  1. Count how many times a word appears in a dataset.
  2. Create a list by splitting the words into indidivual characters (e.g. "hug" => "h" "##u" "##g").
  3. The vocabulary is created by only mentioning a character of a sequence of words once (if a character is repeated, it's not appended onto the vocabulary list).
  4. We select all frequent pairs of the list that was created in step ii and pass the following score function to them:

    <img width="676" height="51" alt="Screenshot 2026-07-17 at 13 26 53" src="https://github.com/user-attachments/assets/516aad20-ad55-41c1-8811-267146ca219b" />

  5. The pair with the highest result gets joined to a token and updated both in the vocabulary and the list created in step ii.
  6. The process is repeated from step iv until we reach the defined vocabulary size.

  To indicate if two or more subwords create a word, the ## characters are added to the
beginning of a subword, indicating it's part of a bigger word. Tokens without ## are assumed
to have a space before them.
    When the tokenizer is trained, we can pass an input with a new word, WordPiece will then search for the longest subword that is in the existing vocabulary. If the new word isn't related to any existing subword in the vocabulary, the word will be tokenized as "[UNK]". 
  
- In GPT models, which use BPE (byte pair encoding), the training of its tokenizer is as follows:
  1. Count how many times a word appears in a dataset.
  2. Create a list by splitting the words into indidivual characters (e.g. "hug" => "h" "u" "g").
  3. The vocabulary is created by only mentioning a character of a sequence of words once (if a character is repeated, it's not appended onto the vocabulary list).
  4. Look for the pair of characters that is together most frequent in the dataset.
  5. The pair which is repeated with highest frequency gets added in the vocabulary and updated in the list created in step ii.
  6. The process is repeated from step iv until we reach the defined vocabulary size.
 
  To indicate if two or more subwords create a word, the whitespace before a subword will be included in the tokenization of that subword (symbol Ġ in Huggingface).
  If a new word is to be tokenized, and only part of that word (subword) exists, the existing subword is tokenized as defined in the vocabulary, and the rest of the word is tokenized as "[UNK]".

- The essential difference between the two tokenizers are that BPE merges the most frequently occurring characters, and WordPiece uses a function to obtain a score the pair with the most likely mutual information.

- When a token gets embedded in the form of a vector, the dimension of said vector is the same throughout the model (at this embedding stage). Then, the dimension of these vectors changes as the context of the input is taken into account.  

<img width="814" height="596" alt="Screenshot 2026-07-16 at 22 58 09" src="https://github.com/user-attachments/assets/268d98d3-a1d2-4f40-897f-9bf05e6b1a61" />

### Helpful links  
[Tokenization summary by HuggingFace](https://huggingface.co/docs/transformers/tokenizer_summary)\
[More in depth tokenization (+training) by HuggingFace](https://huggingface.co/learn/llm-course/chapter6/1)  

### Projects  
1. **apology_email** uses Phi-3 to generate an apology email. Additionally, I converted the input into tokens and token ids, and the output into token ids, to get a better understanding how they are represented at each stage of tokenization.
2. **vector_dimension** is to better comprehend what dimension a vector is after a token is embedded. Interesting to see that the embedded vector when using the all-mpnet-base-v2 model is 768 dimensions, that's a lot of numbers for quite a short sentence!
3. **similar_words** searches for similar words to "king", returning a similarity score.
4. **song_embedding_model** trains a Word2Vec model to recommend songs based on one input song. It knows what songs are similar to the other based on how many times the input song and the recommended song exist in a same playlist (the playlists are a dataset).
5. **BPE_tokenization:** followed the HuggingFace guide for BPE tokenization training
6. **wordpiece_tokenization:** followed the HuggingFace guide for WordPiece tokenization training

