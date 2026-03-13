# Architecture Rules

## Graph Design
- Always use LangGraph's state-driven workflow pattern
- Define a `State` TypedDict that captures all necessary information for the graph
- Use conditional edges (`router` nodes) for branching logic rather than complex if/else
- Each node should have a single responsibility

## Agent Design
- Use system prompts with `langchain.chat_models.ChatAnthropic` to define agent personality
- Keep system prompts focused and concise
- Use pydantic models for structured outputs when classifying or parsing
- Always extract AI responses from message content before storing in state

## Code Organization
- Keep all main logic in `main.py` for now (single-file approach)
- Import langchain and langgraph at the top
- Define State, then models, then nodes, then graph, then CLI loop in that order
