# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

This project uses `uv` as the package manager.

- **Install dependencies:** `uv sync`
- **Run the app:** `uv run main.py`

No test or lint configuration is set up yet.

## Architecture

This is a LangGraph-based CLI chatbot that routes user messages to specialized agents.

**Graph flow:**
```
START → classify_message → router → [therapist_agent | logic_agent] → END
```

**Key components in [main.py](main.py):**

- `State` (TypedDict): Carries `messages` (conversation history) and `message_classifier` (routing label).
- `classify_message`: Uses Claude with structured output (Pydantic model) to classify each user message as `"emotional"` or `"logical"`.
- `router`: Reads `state["message_classifier"]` and returns the name of the next node as a conditional edge.
- `therapist_agent`: Responds with empathy and emotional support.
- `logic_agent`: Responds with factual, direct answers.
- `run_chatbot()`: CLI loop that invokes the compiled graph and prints the final assistant message.

The model is `claude-sonnet-4-6` initialized via `langchain.chat_models.init_chat_model()`. The `ANTHROPIC_API_KEY` is loaded from `.env` via `python-dotenv`.
