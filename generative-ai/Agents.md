# Agents

While a standard LLM is like a person who can speak but is stuck in a dark room, an AI agent is that same person given a flashlight, a notepad, and a set of tools to interact with the world.

An agent is typically built using four core architectural components that "wrap" around the LLM:  

The Brain (LLM): The core engine that handles reasoning, planning, and language understanding.  
Planning: The agent’s ability to break down a complex goal (e.g., "Plan a trip to Paris") into smaller, manageable sub-steps (e.g., "Search flights," "Find hotels," "Check weather").  
Memory: * Short-term: Storing the current conversation and reasoning steps (the "scratchpad").  
Long-term: Using vector databases to retrieve relevant documents or past experiences (RAG).
Tools (Action Space): A set of APIs or functions the agent is allowed to use, such as a calculator, a web search tool, or a Python code interpreter.