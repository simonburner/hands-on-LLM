## Notes

### Key takeaways
- LLMs using the Transformer architecture generate one token at a time, which is appended to the initial prompt and flows through the model again to generate the next token, repeating until the output is completed.
- There are three components to a Transformer LLM: the tokenizer, the transformer blocks and the language modeling head:

<img width="750" height="366" alt="Screenshot 2026-07-17 at 16 17 43" src="https://github.com/user-attachments/assets/d64b2ac3-5d9d-41b0-939e-12d0bda019a8" />

- Tokens get encoded to embeddings which flow through the transformer blocks and ultimately reach the LM head, which scores the probabilities of the next possible token. Sometimes the most probable next token is chosen, but sometimes it's chosen randomly.
- The Transformer is able to process all the input tokens at the same time, which flow through the transformer blocks one by one. To avoid additional processing effort, the results of the operations done on a token are cached inside the transformer blocks.
- A Transformer block is made of an attention layer and a feedforward neural network.
- The attention layer creates the contextual meaning of the input, which is calculated as follows:
  1. The embedding of a token is multiplied by trained weights W<sup>Q</sup>, W<sup>K</sup> and W<sup>V</sup> to obtain a query, key and value vector.
  2. A score is calculated to determine how much focus one token has on another in an input sequence, which is calculated by multiplying the query and key vector of the first token, and then the query vector by the key vector of the respective word we want to score.
  3. The score is divided by the square root of the key vector dimension.
  4. The previous result is normalized with a softmax function, so the scores become positive and add up to one.
  5. The softmax result is multiplied by the value vector, this makes sure the words that aren't relevant get drowned out (for example if the result of the softmax operation of one word is 0.001, the value vector gets multiplied by that value and will therefore not have much relevancy).
  6. The weighted value vectors of the words are summed together to create one vector.
    
     <img width="722" height="730" alt="Screenshot 2026-07-24 at 10 28 22" src="https://github.com/user-attachments/assets/48fa0a47-ce6c-4b3d-8f24-5fe967133594" />

- In the actual implementation, the above calculations are done with matrices for faster processing.
- The W<sup>Q</sup>, W<sup>K</sup> and W<sup>V</sup> are fixed value weights, therefore they're always the same for a specific attention head.
- In multi-headed attention, the above attention calculation is done for each attention head. As we obtain more than one matrix, we concat them into one single matrix and multiply them with a trained weight matrix W<sup>O</sup>.

  <img width="747" height="422" alt="Screenshot 2026-07-24 at 11 10 26" src="https://github.com/user-attachments/assets/12de500c-bf54-4440-831e-d61627b7f5f4" />

- Before the attention layer, the embedding vector gets summed up with a positional embedding, which defines the order of the words in the input sequence.

  <img width="747" height="452" alt="Screenshot 2026-07-24 at 11 20 02" src="https://github.com/user-attachments/assets/419ba587-dddf-49cc-b493-0f9f60dd792b" />

- This is how it would look like in real life for embeddings with 64 dimensions.

  <img width="521" height="200" alt="Screenshot 2026-07-24 at 11 19 10" src="https://github.com/user-attachments/assets/f7b622fe-7726-40af-9848-26099fc9ba87" />



### Useful links  
[Attention in transformers, step-by-step by 3Blue1Brown](https://www.youtube.com/watch?v=eMlx5fFNoYc)  
[The Illustrated Transformer by Jay Alammar](https://jalammar.github.io/illustrated-transformer/)


### Pending questions  
- When an embedding has gone through the transformer block, how does it get converted (or "translated") into a token id?
