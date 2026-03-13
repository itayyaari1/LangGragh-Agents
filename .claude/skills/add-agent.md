# add-agent

Scaffold a new agent node to extend the LangGraph workflow.

## Steps
1. Define a new classification type in the `ClassificationResult` Pydantic model (add to the `classification` field)
2. Create a new agent function following the pattern:
   ```python
   def new_agent_name(state: State) -> dict:
       messages = state["messages"]
       system_prompt = "Your system prompt here..."
       response = model.invoke([SystemMessage(content=system_prompt)] + messages)
       return {"messages": messages + [response]}
   ```
3. Add the node to the graph: `graph.add_node("new_agent_name", new_agent_name)`
4. Update the `router` function to handle the new classification type
5. Test with `/run-chatbot` or `/test-agent`

## Common use cases
- Add specialized agents (writer, coder, analyst, etc.)
- Extend routing logic with new message types
