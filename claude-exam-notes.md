# Difference Between Model, API, and SDK

- **Model:** The AI system that processes input and generates output.
- **API:** The interface through which an application sends requests to and receives responses from Claude.
- **SDK:** A developer library that makes it easier to interact with the API from a programming language.

## Exam Shortcut

**Model = Intelligence**  
**API = Communication Interface**  
**SDK = Developer Tooling**

---

# 2. Why Isn't More Context Always Better?

Because irrelevant or excessive context can:

- Increase token usage
- Increase cost
- Increase latency
- Reduce the model's ability to focus on the information that matters

## Better Principle

**Provide relevant, well-structured context rather than maximum context.**

This is a core **context engineering** principle.

---

# 3. What Makes an Application Agentic?

An agentic application allows the model to pursue a goal through a loop of:

- Reasoning and decision-making
- Taking actions through tools
- Observing results
- Continuing until the task is completed or stopped

## Key Idea

An agent is not merely a model with a longer prompt.

It is a **system or workflow around the model**.

---

# 4. What Problem Does Tool Use Solve?

Tool use allows Claude to interact with **external systems and perform actions or retrieve information** that the model cannot access or execute by itself.

## Examples

- Query a database
- Search a knowledge base
- Call an API
- Retrieve an order
- Create a calendar event
- Execute a business operation

## Important

Claude decides **when and how** to use a tool, while the actual tool execution is performed by your application or tool infrastructure.

---

# 5. What Problem Does MCP Solve?

## Model Context Protocol (MCP)

Model Context Protocol (MCP) provides a standardized protocol for connecting AI applications to external tools, resources, and capabilities.

MCP is an open standard that enables AI applications to securely connect with external tools, data sources, and services through a common client-server architecture, reducing the need for custom integrations.

### Exam Shortcut

**MCP = Standardized connectivity between AI applications and external capabilities**

## Key MCP Concepts

### 1. Tools

Functions the AI can execute.

Examples:

- Create a ticket
- Send a message
- Query a database

### 2. Resources

Information the AI can read.

Examples:

- Files
- Documentation
- Database records

### 3. Prompts

Reusable instructions for specific tasks.

---

# 6. Why Are Evals Necessary?

## Answer

Manually testing an application once or twice does not establish that it is:

- Reliable
- Accurate
- Safe
- Resistant to regressions

Evals allow developers to systematically test an application against representative scenarios.

## Evals Become Important When Changing

- Prompts
- Models
- Tools
- Agent logic
- Context retrieval
- System instructions

## Certification Mindset

If a question says:

> "You changed the prompt and want to ensure existing behavior hasn't degraded."

Think:

**Regression Evaluation / Eval Suite**

Run regression evals to ensure the prompt change has not degraded existing behavior and that the system continues to perform reliably on previously passing cases.

---

# 7. What Security Principle Should You Apply to Database Access?

## Answer: Least Privilege

Give the agent **only the minimum permissions required** to accomplish its task.

Avoid giving an agent:

- Unnecessary database access
- Arbitrary SQL execution
- Unrestricted write permissions
- Access to unrelated customer information

## Certification Shortcut

When you see:

> "Give the agent only the permissions it needs"

Think:

**Least Privilege**

---

# 8. Difference Between Prompt Engineering and Context Engineering

Prompt engineering defines the task, instructions, and behavior expected from the AI.

Context engineering provides the relevant information, tools, memory, and environment the AI needs to successfully complete that task.

| Prompt Engineering | Context Engineering |
|-------------------|---------------------|
| What the AI should do | What information the AI receives |
| Instructions | Data, tools, memory, environment |

✅ **Prompt = What to do**  
✅ **Context = What to know before doing it**

---

# 9. Retrieved Context

Retrieved content is information obtained from external sources and supplied as context to an AI model.

It is typically treated as **untrusted content** because it may be:

- Inaccurate
- Malicious
- Contain instructions that should not override intended system behavior

---

# 10. RAG

## Retrieval-Augmented Generation (RAG)

RAG is an AI architecture that combines information retrieval with language generation.

Relevant external knowledge is retrieved and added to the model's context before generating a response.

---

# 11. Compaction

Compaction is the process of reducing the size of stored data or context while preserving the most important information.

Common goals:

- Improve efficiency
- Reduce storage requirements
- Fit within a model's context window

---

# 12. Prompt Engineering vs Context Engineering

## Prompt Engineering

Focuses on:

- Wording
- Examples
- Constraints
- Role definition
- Output requirements

## Context Engineering

Focuses on:

- Retrieved documents
- Conversation history
- Task state
- Tools
- Information selection and structure

### Exam Shortcut

**Prompt = How you instruct**  
**Context = What you provide**

---

# 13. When Is Few-Shot Prompting Useful?

Few-shot prompting is useful when examples communicate the desired behavior more clearly than instructions alone.

It helps reduce ambiguity and improve correctness.

## Common Uses

- Classification
- Data extraction
- Formatting
- Tone and style
- Handling ambiguous cases
- Demonstrating edge cases

---

# 14. Why Use XML-Style Tags?

XML-style tags help separate different parts of a prompt.

Example:

```xml
<instructions>...</instructions>
<context>...</context>
<examples>...</examples>
<user_input>...</user_input>
```

This improves clarity and helps Claude distinguish **instructions from data**.

## Important

XML tags are a prompting technique, **not a security boundary by themselves**.

---

# 15. Why Isn't Maximum Context Always Better?

Irrelevant context can:

- Increase token consumption
- Increase cost
- Increase latency
- Introduce conflicting information
- Distract the model from relevant information
- Make context management more difficult

## Goal

**Maximum useful context, not maximum context.**

---

# 16. What Is Prompt Injection?

Prompt injection is an attempt to manipulate an AI system by inserting instructions that cause the model to deviate from its intended behavior.

## Key Idea

**Untrusted content is attempting to become an instruction.**

---

# 17. What Is Indirect Prompt Injection?

Indirect prompt injection occurs when malicious instructions come from content the application retrieves or processes rather than directly from the user.

This is especially important for **agents with tools**, because the injected instruction could attempt to trigger tool execution.

---

# 18. Should Claude Automatically Obey Instructions in Retrieved Documents?

## Answer: No

Retrieved documents should generally be treated as **untrusted data**, not trusted instructions.

## Secure Design Principles

1. Separate trusted instructions from retrieved content.
2. Clearly identify retrieved content.
3. Limit tool permissions.
4. Validate and authorize sensitive actions at the application layer.

---

# 19. Why Validate Structured Model Output?

## Answer

Asking Claude to produce JSON or another structured format does **not** mean your application should blindly trust the output.

## Validate

- Schema
- Required fields
- Data types
- Allowed values
- Business rules

---

# 20. One Major Advantage of Prompt Chaining

Prompt chaining divides a complex task into smaller, manageable stages.

## Advantages

- Easier debugging
- Better control
- Easier evaluation
- Structured intermediate results
- Ability to validate each stage

## Trade-Off

More model calls can increase:

- Latency
- Cost
- System complexity

---

# 21. What Security Principle Should Apply to Agent Tools?

## Least Privilege

Give an agent only the permissions and capabilities required for its task.

---

# 22. Embedding

An embedding is a vector representation of text that captures semantic meaning, allowing similar concepts to be located near each other in vector space.

---

# 23. Workflows vs Agents

## Workflows

Systems where LLMs and tools are orchestrated through **predefined code paths**.

## Agents

Systems where the LLM **dynamically directs its own process and tool usage**, maintaining control over how it accomplishes the task.

## Design Principle

Use the **simplest architecture that solves the problem**.

If a workflow works, don't build an agent.

Agents add:

- More power
- More unpredictability
- Variable cost
- Increased debugging complexity

## Exam Point

- "Same steps every time" → **Workflow**
- "Predetermined path" → **Workflow**
- "Depends on what Claude discovers" → **Agent**
- "Cannot be determined in advance" → **Agent**

---

# 24. Prompt Chaining

Prompt chaining uses fixed sequential steps where each output feeds the next, often with validation gates.

Instead of one large prompt, the task is split into several smaller calls.

## Characteristics

- Fixed sequence of steps
- Validation before moving on
- Distinct purpose for each stage
- Output from one stage becomes input to the next

## Exam Point

Look for:

- "Fixed sequence of steps"
- "Validate before moving on"
- "Each stage has a distinct purpose"

These indicate **Prompt Chaining**.

---

# 25. Routing

Routing is used when different inputs require different handling.

A first step classifies the input before a specialized step runs.

If the classifier chooses:

- A tool
- A model
- A processing path

then it's **Routing**.

## Comparison with Prompt Chaining

- **Routing:** Different inputs take different paths.
- **Prompt Chaining:** Every input follows the same sequence.

## Exam Point

Look for:

- "Different inputs need different handling"
- "Classify before processing"
- "Choose which model or tool to use"

These indicate **Routing**.

---

# 26. Parallelisation

Parallelisation runs several independent Claude calls simultaneously and combines the results.

## Types

### Sectioning

Split one job into independent parts.

Example:

- Liability review
- Exclusions review
- Payment terms review

all running at the same time.

### Voting

Run the same task multiple times and compare results.

Example:

- Three separate safety checks
- Human review if answers disagree

## Use When

- Subtasks are independent
- Speed matters
- Reliability matters

## Avoid When

- One step depends on another's output
- Additional cost is not justified

## Exam Point

Look for:

- Independent subtasks
- Run simultaneously
- Multiple perspectives
- Combine results

These indicate **Parallelisation**.

---

# 27. Orchestrator-Workers

A lead model dynamically decomposes the task and delegates work to worker models.

The orchestrator determines:

- What subtasks exist
- How many workers are needed
- How work should be distributed

A simple request may need one worker.

A complex request may need many workers.

## Exam Point

Look for:

- "Subtasks depend on the input"
- "Model decides how to break down the task"
- "Lead model delegates work"

These indicate **Orchestrator-Workers**.

---

# 28. Evaluator-Optimizer

One model generates output while another evaluates it and provides feedback.

The process repeats until quality requirements are met.

## Workflow

1. Generator creates output.
2. Evaluator reviews output.
3. Evaluator provides feedback.
4. Generator revises output.
5. Repeat until standards are met.

## Exam Point

Look for:

- Iterative refinement
- Feedback loops
- Clear evaluation criteria
- Generate → Evaluate → Revise cycles

These indicate **Evaluator-Optimizer**.

---

# 29. Hooks vs System Prompts

Both influence model behavior, but they work differently.

## System Prompt

A system prompt provides **soft guidance**.

It tells Claude what you want, and Claude usually follows it. Because the model is probabilistic, instructions may occasionally be ignored.

## Hooks / Guardrails

Hooks are **hard enforcement**.

They are implemented as application code and run whenever a specific event occurs.

Unlike prompts:

- Claude cannot bypass them
- Claude cannot ignore them
- Claude cannot reason around them

### Key Difference

| System Prompt | Hook / Guardrail |
|--------------|------------------|
| Soft guidance | Hard enforcement |
| Model-controlled behavior | Application-controlled behavior |
| Can occasionally be ignored | Always executed |

✅ **System Prompt = Guidance**  
✅ **Hook / Guardrail = Enforcement**