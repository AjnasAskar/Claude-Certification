# 1. Difference Between Model, API, and SDK

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

---

# 30. Context Editing

Context editing is an automatic cleanup mechanism for an agent's working memory.

As the context window fills up, the agent removes older tool calls and results that are no longer relevant. This helps the agent continue operating efficiently without requiring manual cleanup or intervention from the user.

The goal is to keep the most useful and relevant information available while freeing up space for new tasks and interactions.

## How It Works

1. The agent performs tasks and accumulates tool calls and results.
2. The context window gradually fills with information.
3. Context editing identifies content that is no longer important.
4. Unnecessary tool calls and results are removed.
5. The agent continues working with the remaining relevant context.

## Exam Point

Look for scenarios where the agent:

- Runs for a long period of time
- Accumulates large numbers of tool calls and results
- Needs to remain focused on relevant information
- Operates without manual cleanup or intervention

These are strong indicators that **Context Editing** is being used.

---

# Memory Tool

## Description

The Memory Tool enables Claude to store and retrieve information outside the context window using a file-based storage system.

Claude can create, read, update, and delete files in a dedicated memory directory that persists across conversations. This allows agents to retain information beyond a single session, build knowledge over time, maintain project state, and reference previous learnings without keeping everything in the active context window.

## How It Works

1. Claude stores important information in files within a dedicated memory directory.
2. The stored data persists across conversations and sessions.
3. Claude can read existing memory files when relevant information is needed.
4. Memory files can be updated or deleted as information changes.
5. The agent uses stored knowledge without relying solely on the current context window.

## Exam Point

Look for scenarios where an agent:

- Needs information to persist across conversations
- Maintains project state over multiple sessions
- Builds a long-term knowledge base
- Stores and retrieves information outside the context window
- Requires durable memory beyond working context

These are indicators of the **Memory Tool**.

Also remember:

- The Memory Tool provides **persistent storage**.
- It complements, rather than replaces, the context window.
- Information remains available even after the original conversation has ended.

---

# 31. SDK Authentication Providers

## Description

The SDK can authenticate with multiple providers, giving developers flexibility in how they access Claude models.

Supported authentication providers include:

- **Anthropic API**
- **Amazon Bedrock**
- **Google Vertex AI**
- **Microsoft Foundry**

Authentication is configured through API keys and environment variables, depending on the selected provider.

---

# Tool Error Handling

## Description

When a tool call fails, Claude must be explicitly informed that the operation was unsuccessful.

This is done by setting `is_error: true` on the `tool_result`. Doing so allows Claude to correctly interpret the failure, avoid making unsupported assumptions, and respond appropriately based on the error.

Without proper error signaling, Claude may interpret the result as successful and generate responses that are not supported by actual tool data.

## Exam Point

Look for scenarios where:

- Claude gives a confident answer that the tool data does not support.
- A failed tool call is returned as an empty or successful result.
- The model appears unaware that a tool operation failed.
- Error handling behavior is being evaluated.

These are indicators that the tool result should have been returned with **`is_error: true`**.

Also remember:

- Failed tool calls should be clearly marked with `is_error: true`.
- Include a meaningful error message describing what went wrong.
- The solution is proper error reporting, **not** a stronger prompt.

---

# 32. Determining When an Agent Is Finished
 
## Description
 
An agent should determine whether Claude has finished by checking the `stop_reason` field, not by examining the content type of the response.
 
A response may contain both generated text and a tool request in the same turn. Therefore, the presence of text does not indicate that Claude has completed its work. The reliable indicator is the value of `stop_reason`.
 
## How It Works
 
1. Claude generates a response.
2. The response may include text, tool calls, or both.
3. Check the `stop_reason` field to determine the next action.
4. If the response requires tool execution, continue the agent loop.
5. Only consider the task complete when `stop_reason` indicates completion.
 
## Exam Point
 
Look for scenarios where:
 
- An agent stops after receiving text from Claude.
- A response contains both text and a tool request.
- The system incorrectly assumes text means the task is finished.
- Agent loop termination logic is being evaluated.
 
These are indicators that completion should be determined using **`stop_reason`**.
 
Also remember:
 
- If an agent **stops too early after Claude says something**, the issue is usually incorrect completion logic. Check **`stop_reason`**.
- If an agent **loops forever**, check whether a **turn cap** or maximum iteration limit is configured.
- If there is a **poor handoff to a human**, check what context and information were passed during the handoff.
 
---

# 33. LangGraph

## Description

LangGraph models an agent as a flowchart with memory.

It provides a framework for building durable, stateful agents by defining a shared state, a set of processing steps (nodes), and connections between those steps (edges). The framework manages execution, saves progress during runtime, and supports pausing, resuming, and human intervention when needed.

### Core Building Blocks

| Component | Description | Analogy |
|------------|------------|----------|
| **State** | A shared record that every step can read and update | A case file passed between departments |
| **Nodes** | Functions that perform a specific task and return updates to the state | Desks where each person performs one task |
| **Edges** | Connections that determine what runs next, either fixed or conditional | Arrows on an office flowchart |

## How It Works

1. Define a shared **State** that holds the agent's data.
2. Create **Nodes** that perform individual tasks and update the state.
3. Connect nodes using **Edges** to define the workflow.
4. The framework executes the graph and tracks progress.
5. State is persisted so execution can be paused, resumed, or reviewed.
6. Human intervention can be introduced at specific checkpoints when needed.

## Exam Point

Look for scenarios involving:

- Durable agent execution
- Stateful workflows
- Graph-based orchestration
- Long-running processes
- Human checkpoints or approvals
- Pausing and resuming execution

These are indicators of **LangGraph**.

Also remember:

- **LangGraph** focuses on durable, stateful, graph-based agent orchestration.
- **State**, **Nodes**, and **Edges** are its three core building blocks.
- If a question describes a **Claude-native agent framework with built-in tools**, the answer is **Claude Agent SDK**, not LangGraph.

---

# 34. Strands

## Description

Strands is an agent framework built from three core ingredients: a **model**, a **system prompt**, and **tools**.

You define these components, and the model decides how to use the available tools to accomplish a goal. Compared to other frameworks, Strands is highly model-driven, relying on Claude's reasoning and planning rather than extensive workflow scaffolding.

### Three Ingredients

| Ingredient | Description | Example |
|------------|------------|----------|
| **Model** | The Claude model that performs reasoning and decision-making | Claude Sonnet on Amazon Bedrock |
| **System Prompt** | Instructions that define the agent's role and behavior | "You are ShopKart's inventory assistant." |
| **Tools** | Functions the agent can call to perform actions | `check_stock`, `reorder_item` |

## How It Works

1. Define a model, system prompt, and set of tools.
2. The user provides a task or goal.
3. The model decides which tools should be used.
4. Strands executes the selected tools and returns results.
5. Tool outputs are fed back to the model.
6. The process continues until the goal is completed.

### Key Features

- Lightweight agent loop that manages model calls and tool execution.
- `@tool` decorator for easily converting Python functions into agent tools.
- MCP support for connecting to Model Context Protocol servers.
- Multi-agent patterns, including:
  - **Swarms**: agents collaborate as a group.
  - **Graphs**: agents operate in a structured flow.
  - **Workflows**: agents execute predefined sequences.
  - **Agent-to-Agent**: agents communicate directly with each other.
- Native integration with AWS services and Amazon Bedrock.
- OpenTelemetry support for monitoring, tracing, and debugging.

## Exam Point

Look for scenarios involving:

- AWS-native agent development
- Model + system prompt + tools architecture
- `@tool` decorator
- Amazon Bedrock integration
- MCP support
- Swarms, Graphs, Workflows, or Agent-to-Agent patterns
- OpenTelemetry observability

These are indicators of **Strands**.

Also remember:

- **Strands** is highly model-driven, allowing Claude to determine how tools should be used.
- It is commonly associated with AWS environments and Amazon Bedrock.
- If a question emphasizes **durable state, graph-based orchestration, and human checkpoints**, the answer is **LangGraph**, not Strands.

---

# 35. PydanticAI

## Description

PydanticAI is an agent framework that makes an agent's inputs and outputs strictly typed.

Built on **Pydantic**, the popular Python validation library, PydanticAI helps catch data errors during development rather than in production. It enforces structured inputs and outputs using predefined schemas, making agent behavior more reliable and predictable.

Its primary focus is ensuring that data returned by an AI agent matches the expected format before it is passed to downstream systems.

## How It Works

1. Define input and output schemas using Pydantic models.
2. The agent validates incoming data against those schemas.
3. Agent responses are generated in a structured format.
4. Outputs are validated before being returned or passed to other systems.
5. Invalid or malformed data is caught early, reducing runtime errors.

## Exam Point

Look for scenarios involving:

- Type-safe AI applications
- Validated structured outputs
- Pydantic models
- Schema-based input and output validation
- Catching bad or malformed data before it reaches downstream systems
- Strong data contracts between agents and applications

---

# 36. Multi-Agent System

## Description

A multi-agent system is a team of Claude instances working together, with each agent having its own separate memory and context.

A lead agent coordinates the overall task by planning work, delegating responsibilities to subagents, and combining their results. Each subagent focuses on a specific task and operates independently without access to the lead agent's full conversation history.

This separation allows complex tasks to be broken into smaller, focused pieces that can be performed in parallel.

## How It Works

1. The lead agent receives a task.
2. The lead agent breaks the task into smaller, focused subtasks.
3. Subagents are assigned specific responsibilities.
4. Each subagent works independently within its own context.
5. Results are returned to the lead agent.
6. The lead agent combines the outputs and produces the final response.

## Exam Point

Look for scenarios involving:

- Multiple agents collaborating on a task
- A lead agent coordinating specialized subagents
- Context isolation between agents
- Parallel execution of independent work
- Task delegation and result aggregation

These are indicators of a **Multi-Agent System**.

Also remember:

- Subagents **do not inherit the parent agent's conversation history**.
- Any required context must be explicitly included in the task brief sent to a subagent.
- Subagents are most useful for **context isolation** and **parallelizable work**.
- If a subagent fails because it lacks information known by the lead agent, the solution is a **better task brief**, not a larger model.

---

# 37. Vision

## Description

Vision allows Claude to process images alongside text inputs.

Images can be provided as URLs or as base64-encoded data, enabling Claude to understand and analyze visual content in addition to written prompts. This makes Vision a multimodal capability where information is extracted directly from images rather than text.

Common use cases include reading invoices and receipts, analyzing charts, reviewing screenshots for UI issues, and extracting information from scanned documents.

## How It Works

1. Provide an image as a URL or base64-encoded data.
2. Include the image and text prompt in the same request.
3. Claude analyzes the image content.
4. Claude combines visual understanding with the text prompt.
5. Claude generates a response based on both sources of information.

## Exam Point

Look for scenarios where:

- Important information exists in an image rather than text.
- Documents need to be read from screenshots, scans, receipts, or invoices.
- Charts, diagrams, or visual content must be analyzed.
- A multimodal workflow is required.

These are indicators of **Vision**.

---

# 38. Prefill

## Description

Prefill is a technique where you provide the beginning of Claude's response and allow the model to continue from that starting point.

It is often used to guide output formatting, such as encouraging JSON generation by starting the response with `{`.

Prefill helps steer the model toward a desired response structure, though support varies by model.

## How It Works

1. Provide the initial portion of the assistant's response.
2. Submit the request along with the prefilled content.
3. Claude continues generating from the supplied starting text.
4. The completed response follows the structure implied by the prefill.

## Exam Point

Look for scenarios where:

- The beginning of Claude's response is provided in advance.
- Output formatting is being guided through partial responses.
- JSON or structured output is encouraged by supplying an initial structure.

These are indicators of **Prefill**.

Also remember:

- Prefill is a steering technique.
- It is **not supported on newer models**, including Opus 4.6+ and Sonnet 4.6+.
- Always verify model support before relying on prefill.

---

# 39. Adaptive Thinking

## Description

Adaptive Thinking allows Claude to decide whether reasoning is needed and how much reasoning effort should be used for a particular request.

Rather than specifying a fixed reasoning budget, developers can provide an `effort` setting while Claude dynamically determines the appropriate amount of thinking required.

## How It Works

1. A request is submitted to Claude.
2. Claude evaluates the complexity of the task.
3. The model determines whether explicit reasoning is needed.
4. Claude decides how much reasoning effort to use.
5. A response is generated with or without visible thinking content.

## Exam Point

Look for scenarios where:

- The model determines its own reasoning depth.
- Reasoning is applied only when necessary.
- An `effort` setting guides, rather than controls, the reasoning process.
- Thinking blocks may or may not appear in responses.

These are indicators of **Adaptive Thinking**.

Also remember:

- A response may contain **no thinking block at all**.
- Applications should never assume a thinking block is always present.
- Code should gracefully handle both cases.

---

# 40. Extended Thinking

## Description

Extended Thinking allows developers to allocate a fixed reasoning budget using `budget_tokens`.

Claude can use up to the specified token budget for reasoning before producing an answer, enabling deeper analysis for complex tasks.

Unlike Adaptive Thinking, the reasoning budget is explicitly controlled by the developer.

## How It Works

1. A reasoning budget is defined using `budget_tokens`.
2. Claude uses the allocated budget for internal reasoning.
3. The model performs deeper analysis before answering.
4. Claude generates the final response after completing its reasoning process.

## Exam Point

Look for scenarios where:

- A fixed reasoning budget is configured.
- `budget_tokens` is explicitly specified.
- Deep reasoning is required for complex tasks.
- Token allocation is controlled by the developer.

These are indicators of **Extended Thinking**.

Also remember:

- Extended Thinking requires a minimum budget of **1,024 tokens**.
- For very large budgets (**greater than 32K tokens**), the recommended approach is the **Batch API**.
- Batch processing helps avoid timeouts that can occur in long-running single requests.

---