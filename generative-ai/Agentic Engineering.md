# AI Agent engineering


# Prep guide
https://oracle.sharepoint.com/teams/External-Ekore/Shared%20Documents/Forms/AllItems.aspx?d=webaa8f6e1f70426b91f13b5fa0bad30c&csf=1&web=1&e=GVeOKb&CID=3078ea4d%2D49ee%2D42f2%2Dbd12%2D9abaa1ebad3b&FolderCTID=0x0120002A7006AB05E87A49A9A777F6E12572E7&id=%2Fteams%2FExternal%2DEkore%2FShared%20Documents%2FIDC%2FRaj%2FAI%20Hackathon%20AI%2D%20Agent%20Engineering%20From%20Prototype%20to%20Production%2FPre%20work

Ops pilot

# user account
Cloud Account / Tenancy: dajayanth
chandrasekar.srinivasan@oracle.com


# Vector database
pinecone
qdrant (quicker easier for hackathon)

# Day 1
Problem statement

# Day 2

Lang chain
Vector search

lang chain to lang graph
human approval


# Lang chain
- orchestration layer
- open source framework
- lang chain expression language
    - llm | prompt
- tools: executable functions (ex: API call) that helps to take action in the outside world.
    - name, definition (very important for llm to choose a tool)
    - input schema
    - execution function
- Agent - LLM + right tools
- Available tools:
    - Tavily - websearch

# Agent architecture:
## Hub and spoke models
- co-ordinator agent (Orchestrator agent)
    - manages lot of sub agent.
    - the sub agent should not talk to the each other
- coordinator sub agents if we want to manage sub group of agents

# Embedding
- converting data into vectors (numbers representing semantic meaning)

# RAG
- required to provide additional context to Agent.

# Reflex agent and multi conversational agents
Simple reflex agent
