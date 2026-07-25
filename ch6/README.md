- do_sample set to True will allow the model to sample more likely output tokens, and if set to false the most probable next token is selected.
- temperature controls the randomness/creativity of the output tokens. In theory, a temperature of 0 will generate the same output every time, whereas a temperature set closer to one will enhance the probability of different outputs.
- top_p is a sampling technique that controls which output tokens the LLM considers. If the top_p is set to 0.1, it will consider tokens until it reaches that value of cumulative probability, and if it's st to 1, it will consider all tokens.

<img width="696" height="267" alt="Screenshot 2026-07-25 at 20 00 53" src="https://github.com/user-attachments/assets/42cdf74e-e182-4066-98ad-3b9fcae492f3" />


"Although a prompt is a single piece of text, it is tremendously helpful to think of
prompts as pieces of a larger puzzle. Have I described the context of my question?
Does the prompt have an example of the output?"
