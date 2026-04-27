# How it works

Here’s what happened behind the scenes:
Discovery — When the chat session started, the agent scanned default skill directories and found your skill. It read only the name and description, just enough to know when the skill might be relevant.
Activation — When you asked about rolling dice, the agent matched your question to the skill’s description and loaded the full SKILL.md body into context.
Execution — The agent followed the instructions in the body, adapting the terminal command to the number of sides in your request.
This process uses progressive disclosure to let the agent access many skills without loading all their instructions up front.