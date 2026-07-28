<img width="569" height="157" alt="Screenshot 2026-07-28 at 17 06 33" src="https://github.com/user-attachments/assets/b177b65f-4552-4939-b5df-c44d76606bd1" />

### Chains

- LLMs truly shine when used together with additional components. Chains extend the capabilities of LLMs as they connect multiple components together (such as an additional tool, feature or prompt).
- Example: Phi-3 expects a specific prompt template, so we can create a prompt template using chains.
  
  <img width="417" height="122" alt="Screenshot 2026-07-28 at 17 15 01" src="https://github.com/user-attachments/assets/b5d96c5a-d09b-4166-892a-a0296ef4e1cd" />

  <img width="437" height="237" alt="Screenshot 2026-07-28 at 17 15 20" src="https://github.com/user-attachments/assets/87c1714c-4725-4879-b383-cbca133862f3" />

  <img width="478" height="122" alt="Screenshot 2026-07-28 at 17 16 15" src="https://github.com/user-attachments/assets/5083b458-f63b-4659-93d0-af1fc435f2d7" />

- We can also break a complex prompt into smaller subtasks which run sequentially:

  <img width="503" height="190" alt="Screenshot 2026-07-28 at 18 14 26" src="https://github.com/user-attachments/assets/a621ae4d-53b7-4b31-96fa-56025c08eb73" />

### Memory

- LLMs are stateless, they have no memory of any previous conversation.
- To make them have memory of a conversation, we can add a conversation buffer or conversation memory:
  - Conversation buffer: copying the entire previous conversation and pasting it into the new prompt.
  
    <img width="559" height="250" alt="Screenshot 2026-07-28 at 18 31 14" src="https://github.com/user-attachments/assets/8a7aa36e-ae9e-4be8-9c45-7f2ea45c8b6f" />

    There's also a windowed conversation buffer, which takes only a specified amount of tokens as chat history.

  - Conversation summary: a summarization of a chat history which is done by a separate LLM.

    <img width="568" height="247" alt="Screenshot 2026-07-28 at 18 56 25" src="https://github.com/user-attachments/assets/77bf5999-ecbd-4abe-955c-d8f3ef743e8c" />

    This means that when we ask an LLM a question, the user prompt and the summarization prompt are called.

    <img width="543" height="208" alt="Screenshot 2026-07-28 at 19 47 12" src="https://github.com/user-attachments/assets/4f0cc2c7-680d-4740-9d80-54dba84b928d" />

    Summarization helps to keep the chat history small without using too many tokens.

    <img width="604" height="271" alt="Screenshot 2026-07-28 at 19 51 13" src="https://github.com/user-attachments/assets/c68ff864-177a-4034-847d-31a0b1c5bbb3" />

### Agents

- Agents are systems that use a LLM to determine which actions they should take and it what order.
- They can make use of model I/O, chains and memory, plus:
  - Tools: to do things the agent can't do itself
  - Agent type: which plans the actions to take or tools to use

- They're able to create and self correct themselves to achieve a goal, and also interact with the real world with tools.
- Many agent-based systems use the ReAct (Reasoning and Acting) framework.
- ReAct merges the concepts of allowing reasoning to affect acting and actions to affect reasoning. In practice, the framework iterates following these steps: Thought, Action, Observation.

  <img width="515" height="284" alt="Screenshot 2026-07-28 at 20 10 48" src="https://github.com/user-attachments/assets/b8cff92a-3bec-47c3-a08f-1c93e2058bde" />

  <img width="580" height="431" alt="Screenshot 2026-07-28 at 20 11 13" src="https://github.com/user-attachments/assets/307be3ca-c199-4df7-8f26-adca3f0ea4d3" />

## Projects

LangChain


