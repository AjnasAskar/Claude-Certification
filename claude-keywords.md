# Claude Keywords

## stop_reason

When Claude finishes generating a response, the API tells you why it stopped. That reason is stored in a field called `stop_reason`.

### Common stop_reason Values

#### `end_turn`

The normal, successful ending.

Claude completed everything it wanted to say and finished the response naturally.

#### `max_tokens`

A token limit was reached before Claude could finish.

Tokens are roughly word pieces, so if the limit is too small, Claude may stop mid-sentence or mid-thought.

**Common beginner mistake:**

```python
max_tokens=50
```

This often truncates responses unexpectedly.

#### `stop_sequence`

Occurs when a predefined stop string is encountered.

Example:

```python
stop_sequences=["END"]
```

Claude stops immediately after generating:

```text
END
```

#### `tool_use`

Indicates that Claude wants to use a tool.

Claude's reply is not just one text string. Instead, it is returned as a **list of content blocks**, where each block represents part of the response.

Example content block types:

- Text
- Tool use
- Tool result

#### `/compact`

Claude Code's built-in compaction that preserves key facts

#### `pause_turn`

Used during long-running tool operations.

Some server-side tools, such as web search, may take time to complete. Instead of making the application wait, Claude can temporarily pause the conversation.

Workflow:

1. Claude pauses the turn.
2. Your application receives the partial response.
3. You return that response unchanged.
4. Claude resumes where it left off.

#### `refusal`

Indicates that Claude declined part or all of a request due to safety policies.

Typical reasons:

- Dangerous requests
- Harmful instructions
- Restricted content

#### `model_context_window_exceeded`

The conversation is larger than the model can handle.

The combined size of:

- User messages
- Claude responses
- Tool outputs
- System instructions

has exceeded the model's context window.

**Common causes:**

- Very long chats
- Large documents
- Large tool results
- Extensive retrieved context

---

## stop_details

`stop_details` is an optional field that provides additional information about why Claude stopped.

It is most useful when `stop_reason` alone does not provide enough detail.

### Example

If:

```json
"stop_reason": "refusal"
```

then:

```json
"stop_details": {
  ...
}
```

may explain:

- What was refused
- Why it was refused
- Which safety policy was involved

### Easy Way to Remember

- **stop_reason** = Label on the package
- **stop_details** = Note inside the package

Example:

```text
stop_reason  = "refusal"
stop_details = explanation of what was refused and why
```

---

# Quick Exam Cheat Sheet

| Term | Meaning |
|--------|---------|
| `end_turn` | Claude finished normally |
| `max_tokens` | Token limit reached |
| `stop_sequence` | A configured stop string was encountered |
| `tool_use` | Claude wants to call a tool |
| `pause_turn` | Claude temporarily paused while waiting for a tool/process |
| `refusal` | Claude declined due to safety rules |
| `model_context_window_exceeded` | Conversation exceeded model context size |
| `stop_details` | Additional explanation for the stop reason |

## Memory Shortcut

```text
end_turn     → Finished normally
max_tokens   → Hit response limit
stop_sequence→ Hit custom stop text
tool_use     → Needs a tool
pause_turn   → Waiting
refusal      → Safety block
context_exceeded → Too much information
stop_details → Extra explanation
```