# Development Rules

## Environment Setup
- Copy `.env.example` to `.env` and add your `ANTHROPIC_API_KEY`
- Run `uv sync` to install dependencies
- Run `uv run main.py` to test the chatbot

## Testing
- Test new nodes by invoking the graph with sample messages
- Log state changes to debug routing logic
- Verify structured output (Pydantic models) with various input types

## Extending the Graph
- New agents should follow the same pattern: system prompt → invoke model → return response
- New classification types should be added to the Pydantic model, not hardcoded strings
- Always update the router node when adding new agent paths

## API Key Management
- Never commit `.env` file
- Always use environment variables for sensitive keys
- `.env.example` should document all required variables
