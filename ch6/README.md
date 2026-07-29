## Chapter 6: Prompt Engineering

### Key takeaways

#### Controlling model output with 🤗 transformers:

- do_sample set to True will allow the model to sample more likely output tokens, and if set to false the most probable next token is selected.
- temperature controls the randomness/creativity of the output tokens. In theory, a temperature of 0 will generate the same output every time, whereas a temperature set closer to one will enhance the probability of different outputs.
- top_p is a sampling technique that controls which output tokens the LLM considers. If the top_p is set to 0.1, it will consider tokens until it reaches that value of cumulative probability, and if it's st to 1, it will consider all tokens.

<img width="696" height="267" alt="Screenshot 2026-07-25 at 20 00 53" src="https://github.com/user-attachments/assets/42cdf74e-e182-4066-98ad-3b9fcae492f3" />

#### Helpful prompting tips:

Although a prompt is a single piece of text, it is tremendously helpful to think of prompts as pieces of a larger puzzle. Have I described the context of my question? Does the prompt have an example of the output? Take the following into account:

- Specificity: Accurately describe what you want to achieve. Instead of asking the LLM to “Write a description for a product” ask it to “Write a description for a product in less than two sentences and use a formal tone.”

- Hallucination: LLMs may generate incorrect information confidently, which is referred to as hallucination. To reduce its impact, we can ask the LLM to only generate an answer if it knows the answer. If it does not know the answer, it can respond with “I don’t know.”

- Order: Either begin or end your prompt with the instruction. Especially with long prompts, information in the middle is often forgotten. LLMs tend to focus on information either at the beginning of a prompt (primacy effect) or the end of a prompt (recency effect).

- Persona: Describe what role the LLM should take on. For example, use “You are an expert in astrophysics” if you want to ask a question about astrophysics.

- Instruction: The task itself. Make sure this is as specific as possible.

- Context: Additional information describing the context of the problem or task. It answers questions like “What is the reason for the instruction?”.

- Format: The format the LLM should use to output the generated text. Without it, the LLM will come up with a format itself, which is troublesome in automated systems.

- Audience: The target of the generated text. This also describes the level of the generated output. For education purposes, it is often helpful to use ELI5 (“Explain it like I’m 5”).

- Tone: The tone of voice the LLM should use in the generated text. If you are writing a formal email to your boss, you might not want to use an informal tone of voice.

- Data: The main data related to the task itself.  

<img width="661" height="474" alt="Screenshot 2026-07-25 at 20 20 58" src="https://github.com/user-attachments/assets/61d1ab34-d952-4e88-a562-0cee31554ac0" />

#### In-context learning:

  <img width="682" height="378" alt="Screenshot 2026-07-28 at 09 32 29" src="https://github.com/user-attachments/assets/037596e5-9ac7-4ca0-abdc-de6589f5b120" />

#### Chain prompting:

  <img width="681" height="405" alt="Screenshot 2026-07-28 at 10 38 37" src="https://github.com/user-attachments/assets/66b6e3a2-f16d-4971-931e-80ec7b62ae61" />

#### Reasoning with generative models

- Chain-of-Thought: Think Before Answering: aims to have the generative model “think” first rather than answering the question directly without any reasoning.
  
  <img width="663" height="485" alt="Screenshot 2026-07-28 at 10 51 30" src="https://github.com/user-attachments/assets/e7f9862e-671f-4d29-9b84-f86d9e724866" />

  However, instead of providing examples as in the guide above, we can simply ask the model to do the reasoning itself, which is called zero-shot chain-of-thought.

  <img width="454" height="348" alt="Screenshot 2026-07-28 at 11 08 59" src="https://github.com/user-attachments/assets/b6f9f792-ef53-43f1-ae76-c4ff88dea733" />

- Self-consistency: A method that asks a generative model the same prompt multiple times and outputs the majority result. During the process, the temperature and top_p parameters can be modified to expand the potential answers.

  <img width="675" height="510" alt="Screenshot 2026-07-28 at 11 18 29" src="https://github.com/user-attachments/assets/3b6c9c06-94b3-4898-a55f-b59191e164d2" />

  Time tedious process, it becomes n times slower where n is  the number of output samples.

- Tree-of-Thought: Improves on Chain-of-Thought and Self-consistency. A method that breaks the reasoning process into smaller pieces. At each step, the model is prompted to explore different solutions to a problem. Then, it votes for the best solution and continues to the next step.

  <img width="453" height="485" alt="Screenshot 2026-07-28 at 11 25 19" src="https://github.com/user-attachments/assets/79f0a20d-4ec6-40a3-ae9d-973f7b3a2110" />

  The main disadvantage to this method is that it requires many calls to the generative models, thus slowing the process down. However, this can be mitigated to some degree: instead of calling the generative model multiple times, we can ask the model to mimic this process by emulating a conversation between multiple experts.

### Projects

**prompt_engineering:** implements the above concepts with 🤗 transformers.





