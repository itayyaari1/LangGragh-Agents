# test-agent

Test a specific agent node with custom input to verify behavior.

## Usage
```bash
# Test the classifier
python -c "
from main import classify_message
from langchain_core.messages import HumanMessage

result = classify_message({'messages': [HumanMessage(content='I feel sad')]})
print(result)
"
```

## What it does
- Runs a single node in isolation
- Allows testing classification, routing, or agent responses
- Useful for debugging specific node behavior

## Common use cases
- Verify classification works correctly for a message
- Check if an agent's response is appropriate
- Debug state transformations
