# Code Style Rules

## Python
- Use Python 3.10+ features (type hints, match statements)
- Follow PEP 8 naming conventions
- Use type hints for all function parameters and returns
- Keep functions focused and under 30 lines when possible

## Imports
- Group imports: stdlib, third-party, local
- Use specific imports, avoid `import *`

## LangGraph/LangChain
- Use descriptive node names with underscores (e.g., `classify_message`, `therapist_agent`)
- Use `state["key"]` to access state values, not attributes
- Always invoke the graph with `input={"messages": [...]}` format
