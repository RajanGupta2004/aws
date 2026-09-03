
# AI Project Learning Roadmap

```text
PHASE 1 — AI FUNDAMENTALS
        │
        ├── 1. AI
        ├── 2. Types of AI Models
        └── 3. Different Model Providers
        │
        ▼
PHASE 2 — LLM FUNDAMENTALS
        │
        ├── 4. LLM
        ├── 5. Tokens
        ├── 6. Temperature
        ├── 7. Prompt Engineering
        ├── 8. Model Responses
        │      ├── Streaming
        │      └── One-shot
        └── 9. Hallucination
        │
        ▼
PHASE 3 — KNOWLEDGE & MEMORY
        │
        ├── 10. Vector Database
        ├── 11. Memory Database
        └── 12. RAG
        │
        ▼
PHASE 4 — TOOLS & AGENTS
        │
        ├── 13. Tools
        ├── 14. MCP
        ├── 15. AI Agents
        │      ├── No-code
        │      └── Pro-code
        └── 16. Types of AI Agents
        │
        ▼
PHASE 5 — AI PLATFORM / ORCHESTRATION
        │
        ├── 17. AI Gateway
        ├── 18. Model Routing
        └── 19. Model Switching
        │
        ▼
PHASE 6 — AI RELIABILITY
        │
        └── 20. Guardrails
        │
        ▼
PHASE 7 — PRODUCTION AI
        │
        ├── 21. AI Observability
        └── 22. AI Security & Governance
        │
        ▼
PHASE 8 — COMPLETE AI ARCHITECTURE
        │
        └── Combine everything into one
            production-ready AI platform
```

---

# Phase 1 — AI Fundamentals

## 1. AI — Artificial Intelligence

AI is the broad concept of making computers perform tasks that normally require human intelligence.

Examples:

* Understanding language
* Recognizing images
* Making predictions
* Planning
* Decision making
* Generating content

Think:

```text
                 AI
                  │
       ┌──────────┼──────────┐
       │          │          │
    Machine     Deep       Generative
    Learning    Learning      AI
                              │
                              ▼
                             LLM
```

### Important distinction

**AI is the umbrella.**

Machine Learning, Deep Learning, Generative AI and LLMs are technologies inside that broader ecosystem.

---

# 2. Different Types of Models

You need to understand that an AI application doesn't necessarily use only an LLM.

Common model categories include:

### Classification models

Answer:

> "Which category does this belong to?"

Example:

```text
Customer message
      ↓
"I want to cancel my order"
      ↓
Classification Model
      ↓
Category = Cancellation
```

### Embedding models

Convert text into numerical vectors.

```text
"How do I reset my password?"
              ↓
        Embedding Model
              ↓
[0.21, -0.73, 0.44, ...]
```

Used heavily in **RAG and vector databases**.

### LLMs

Generate or understand language.

```text
Question
   ↓
LLM
   ↓
Answer
```

### Vision models

Understand images/video.

### Speech models

Speech → Text

or

Text → Speech.

### Multimodal models

Can work with combinations such as:

```text
Text
Image
Audio
Video
   ↓
Multimodal Model
```

---

# 3. Different Model Providers

Your application does not necessarily need to be tied to one model provider.

Examples include:

* OpenAI
* Anthropic
* Google
* Meta
* Mistral
* Cohere
* AWS
* Azure
* open-source/self-hosted models

The important architectural concept is:

```text
                 Your Application
                        │
                   AI Gateway
                        │
          ┌─────────────┼─────────────┐
          ↓             ↓             ↓
       Provider A    Provider B    Provider C
          │             │             │
        Model 1       Model 2       Model 3
```

This becomes very important later when you study:

**AI Gateway → Model Routing → Model Switching.**

---

# Phase 2 — LLM Fundamentals

Now you start learning the core of modern Generative AI.

# 4. LLM — Large Language Model

An LLM is a model trained on huge amounts of data to understand and generate language.

At a simplified level:

```text
User
 │
 │ "Explain AWS EC2"
 ↓
LLM
 │
 ↓
Generated response
```

But internally, the process involves:

```text
Input
 ↓
Tokenization
 ↓
Tokens
 ↓
Model processing
 ↓
Probability calculation
 ↓
Next token selection
 ↓
More tokens
 ↓
Final response
```

This leads directly to your next topic.

---

# 5. Tokens

LLMs don't fundamentally process text as words.

They process **tokens**.

For example:

```text
"Artificial intelligence is powerful"
```

might be broken into pieces approximately like:

```text
Artificial
intelligence
is
power
ful
```

The exact tokenization depends on the model.

### Why tokens matter

Tokens affect:

* Cost
* Context window
* Latency
* Input size
* Output size
* Model limits

For example:

```text
User prompt
    +
Conversation history
    +
RAG documents
    +
Tool results
    ↓
TOTAL TOKENS
    ↓
LLM
```

This becomes extremely important when designing production systems.

---

# 6. Temperature

Temperature controls how deterministic vs variable the model's output is.

Simplified:

```text
Low temperature
       ↓
More predictable
More consistent
Less creative


High temperature
       ↓
More variation
More creative
Less predictable
```

For example:

### Low temperature

Good for:

* Data extraction
* Classification
* Structured output
* Code generation
* Business workflows

### Higher temperature

Can be useful for:

* Brainstorming
* Creative writing
* Idea generation

Important: temperature behavior and availability vary by model/provider, so don't treat it as a universal "creativity slider."

---

# 7. Prompt Engineering

Prompt engineering means designing instructions that help the model produce the desired result.

Basic:

```text
Tell me about AWS.
```

Better:

```text
Explain AWS EC2 to a beginner.

Requirements:
- Use simple English
- Give a real-world example
- Explain the important components
- Keep the answer under 500 words
```

You should eventually learn:

* System prompts
* User prompts
* Few-shot prompting
* Zero-shot prompting
* Chain-of-thought considerations
* Structured outputs
* JSON outputs
* Prompt templates
* Prompt versioning
* Context management

---

# 8. Model Response Types

You specifically mentioned:

> streaming and one shot

This is important.

## One-shot / non-streaming

The application waits for the complete response.

```text
User
 ↓
Request
 ↓
LLM
 ↓
Complete response
 ↓
User
```

Example:

```text
User: Explain Kubernetes.

[waiting...]

Assistant: Kubernetes is...
```

## Streaming

The model sends output progressively.

```text
User
 ↓
LLM
 ↓
"This"
" is"
" Kubernetes"
"..."
 ↓
User sees response progressively
```

This is commonly used in chat interfaces because it improves perceived responsiveness.

---

# 9. Hallucination

Hallucination occurs when an AI model generates information that is incorrect, unsupported, or fabricated while presenting it as if it were reliable.

Example:

```text
User:
Who created XYZ library?

LLM:
XYZ library was created by John Smith in 2017.
```

But perhaps John Smith never created it.

### Why hallucinations happen

LLMs are fundamentally generating likely sequences of tokens; they are not automatically authoritative databases of facts.

Hallucination can be reduced using techniques such as:

```text
Better prompts
      +
RAG
      +
Tool calls
      +
Structured outputs
      +
Validation
      +
Guardrails
      +
Evaluation
```

---

# Phase 3 — Knowledge & Memory

This is one of the most important sections for your project.

# 10. Vector Database

A vector database stores vectors/embeddings and allows similarity search.

Example:

```text
Company documents
      ↓
Embedding Model
      ↓
Vectors
      ↓
Vector Database
```

When a user asks:

> "What is our leave policy?"

the system converts the question into a vector and searches for semantically similar information.

Common vector databases include:

* Pinecone
* Weaviate
* Milvus
* Qdrant
* pgvector/PostgreSQL

The key concept is:

```text
Text
 ↓
Embedding
 ↓
Vector
 ↓
Similarity Search
```

---

# 11. Memory Database

Don't confuse **vector storage** with **application memory**.

Memory is about maintaining useful information across interactions or sessions.

Example:

```text
Conversation 1
User: My name is Raj.

       ↓

Memory

       ↓

Conversation 2
User: What is my name?

       ↓

AI: Your name is Raj.
```

Memory can include:

* Conversation history
* User preferences
* Previous tasks
* Session information
* Long-term user information
* Application state

A production system may use Redis, PostgreSQL, or other storage systems depending on the memory design.

---

# 12. RAG — Retrieval Augmented Generation

This is a **critical topic**.

RAG allows an LLM to retrieve external information before generating an answer.

Without RAG:

```text
Question
   ↓
LLM
   ↓
Answer
```

With RAG:

```text
                 Documents
                     ↓
               Vector Database
                     ↑
                     │
User Question → Embedding → Search
                              │
                              ↓
                         Relevant Docs
                              │
                              ↓
Question + Context → LLM → Answer
```

Example:

Your company has:

```text
1000 PDFs
500 Word documents
200 policies
1000 internal pages
```

Instead of putting everything into the prompt, RAG retrieves only the relevant information.

---

# Phase 4 — Tools & Agents

# 13. Tools

A tool allows an AI system to perform an action or retrieve information outside the model itself.

For example:

```text
LLM
 │
 ├── Search Tool
 ├── Database Tool
 ├── Calculator
 ├── Email Tool
 ├── API Tool
 └── CRM Tool
```

Example:

```text
User:
What is the current temperature?

LLM
 ↓
Weather Tool
 ↓
Current weather data
 ↓
LLM
 ↓
Answer
```

The LLM itself may not know the current information, but a tool can retrieve it.

---

# 14. MCP — Model Context Protocol

MCP is a protocol for connecting AI applications/models with external tools and data sources in a standardized way.

Conceptually:

```text
                AI Application
                      │
                     MCP
                      │
        ┌─────────────┼─────────────┐
        ↓             ↓             ↓
      GitHub        Database       Files
        │             │             │
      Tools         Tools          Data
```

Instead of creating completely different integrations for every AI client, MCP provides standardized ways to expose capabilities and context.

You should study:

* MCP Client
* MCP Server
* Tools
* Resources
* Prompts
* Transport
* Authentication/security considerations
* Tool discovery
* Permission boundaries

---

# 15. AI Agents

An AI agent goes beyond simply generating an answer.

A simplified agent loop is:

```text
Goal
 ↓
Understand
 ↓
Plan
 ↓
Choose Tool
 ↓
Execute Tool
 ↓
Observe Result
 ↓
Reason
 ↓
Next Action
 ↓
Final Answer
```

Example:

> "Find the cheapest flight and prepare an itinerary."

The agent may:

```text
Search flights
     ↓
Compare results
     ↓
Check dates
     ↓
Search hotels
     ↓
Build itinerary
     ↓
Return result
```

---

# 16. Types of AI Agents

There are several useful ways to classify agents.

### Simple agent

```text
Input → LLM → Tool → Answer
```

### ReAct-style agent

```text
Reason
 ↓
Act
 ↓
Observe
 ↓
Reason
 ↓
Act
```

### Workflow agent

Predefined workflow:

```text
Step 1
 ↓
Step 2
 ↓
Step 3
 ↓
Step 4
```

### Multi-agent system

Multiple specialized agents:

```text
                 Orchestrator
                 /     |      \
                /      |       \
          Research   Coding   Review
            Agent     Agent    Agent
                \      |       /
                 \     |      /
                  Final Result
```

### No-code agents

Built using visual/low-code platforms.

### Pro-code agents

Built using programming frameworks and custom orchestration.

For your project, you should understand **both**, but if you are building a serious engineering platform, pro-code architecture will be more important.

---

# Phase 5 — AI Platform / Orchestration

Now your understanding starts moving from "AI application" toward an **AI platform**.

# 17. AI Gateway

An AI Gateway acts as a central entry point between your applications and model providers.

```text
Applications
     │
     ↓
 AI Gateway
     │
 ├── Authentication
 ├── Rate Limiting
 ├── Logging
 ├── Cost Tracking
 ├── Guardrails
 ├── Routing
 └── Model Selection
     │
     ├── OpenAI
     ├── Anthropic
     ├── Google
     └── Other Models
```

Instead of every application directly connecting to every provider:

```text
App A ──→ Provider A
App B ──→ Provider B
App C ──→ Provider C
```

you can have:

```text
App A ─┐
App B ─┼──→ AI Gateway ──→ Multiple Providers
App C ─┘
```

This is particularly useful for enterprise AI platforms.

---

# 18. Model Routing

Routing means deciding:

> **Which model should handle this request?**

Example:

```text
                    Request
                       ↓
                  AI Gateway
                       ↓
                   Router
                  /      \
                 /        \
          Simple task    Complex task
               ↓              ↓
          Cheap Model     Powerful Model
```

For example:

```text
Classification
     ↓
Small/cheap model

Complex reasoning
     ↓
Large model

Image request
     ↓
Vision model
```

Routing can consider:

* Cost
* Latency
* Quality
* Context length
* Availability
* Task type
* Provider health
* Data residency
* Model capabilities

---

# 19. Model Switching

Routing and switching are related but different.

### Routing

Choose a model based on the request.

```text
Request A → Model X
Request B → Model Y
```

### Switching / fallback

Switch when the preferred model cannot serve the request.

```text
Primary Model
     ↓
   Failure
     ↓
Fallback Model
     ↓
Response
```

Example:

```text
OpenAI
  ↓
Timeout
  ↓
Anthropic
  ↓
Response
```

This provides resilience.

---

# Phase 6 — AI Reliability

# 20. Guardrails

Guardrails are controls that keep AI behavior within acceptable boundaries.

Think:

```text
                 AI System
                    │
          ┌─────────┴─────────┐
          ↓                   ↓
     Input Guardrail     Output Guardrail
          │                   │
          ↓                   ↓
      Validate            Validate
          │                   │
          └─────────┬─────────┘
                    ↓
                   User
```

Examples:

### Input guardrails

Detect:

* Malicious prompts
* Prompt injection
* Sensitive information
* Unsupported requests

### Output guardrails

Check:

* Toxic content
* PII
* Invalid format
* Policy violations
* Unsafe responses

### Business guardrails

For example:

```text
AI can:
✓ Read customer account

AI cannot:
✗ Delete customer account
✗ Transfer money
✗ Change permissions
```

---

# Phase 7 — Production AI

# 21. AI Observability

Normal application observability looks at things such as:

```text
CPU
Memory
Latency
Errors
Requests
```

AI observability needs additional information.

For example:

```text
User Request
     ↓
Prompt
     ↓
Model
     ↓
Tokens
     ↓
Tool Calls
     ↓
RAG
     ↓
Response
```

You want to understand:

* Which model was used?
* How many tokens?
* How much did it cost?
* How long did it take?
* What prompt was used?
* What tools were called?
* What documents were retrieved?
* What was the final response?
* Did the request fail?
* Was the answer good?

Platforms such as Langfuse are designed around this type of LLM/AI observability.

---

# 22. AI Security & Governance

This becomes extremely important in enterprise systems.

You need to think about:

### Authentication

Who can access the AI platform?

### Authorization

What are they allowed to do?

```text
Developer
   ↓
Can use Model A

Admin
   ↓
Can use all models
```

### Data security

Protect:

* Customer data
* Company documents
* API keys
* Prompts
* Model responses

### Prompt injection

Example:

```text
User input:
Ignore previous instructions...
```

Your system needs defenses around untrusted inputs.

### Data leakage

Prevent confidential information from being exposed to:

* Users
* Logs
* External models
* Tools

### Governance

Define:

```text
Which models are approved?
Which data can be sent?
Who can use which model?
What is logged?
How long is data retained?
What actions can agents perform?
```

---

# The Complete Picture

Now let's combine your entire topic list.

A production AI architecture can look conceptually like this:

```text
                         USER
                           │
                           ▼
                  ┌─────────────────┐
                  │   Application    │
                  └────────┬────────┘
                           │
                           ▼
                  ┌─────────────────┐
                  │   AI Gateway    │
                  │                 │
                  │ Authentication  │
                  │ Rate Limiting   │
                  │ Guardrails      │
                  │ Routing         │
                  │ Observability   │
                  └────────┬────────┘
                           │
                           ▼
                    MODEL ROUTER
                           │
             ┌─────────────┼─────────────┐
             │             │             │
             ▼             ▼             ▼
          Model A       Model B       Model C
             │             │             │
             └─────────────┼─────────────┘
                           │
                           ▼
                      AI AGENT
                           │
             ┌─────────────┼─────────────┐
             │             │             │
             ▼             ▼             ▼
           TOOLS          MCP          MEMORY
             │             │             │
             ▼             ▼             ▼
          APIs          Services      Database
                                         │
                                         ▼
                                  Vector Database
                                         │
                                         ▼
                                         RAG
                                         │
                                         ▼
                                    Documents
```

And around the whole system:

```text
┌─────────────────────────────────────────────────────────────┐
│                    AI SECURITY & GOVERNANCE                 │
│                                                             │
│ Authentication | Authorization | PII | Audit | Policies    │
│                                                             │
│                 AI OBSERVABILITY                            │
│                                                             │
│ Logs | Traces | Tokens | Cost | Latency | Quality | Errors │
└─────────────────────────────────────────────────────────────┘
```

---

# Recommended Learning Order

I would **not** study all 22 topics equally at first.

Use this sequence:

| Order | Topic                    | Priority |
| ----: | ------------------------ | -------- |
|     1 | AI                       | ⭐⭐⭐      |
|     2 | Types of AI Models       | ⭐⭐⭐⭐     |
|     3 | Model Providers          | ⭐⭐⭐⭐     |
|     4 | LLM                      | ⭐⭐⭐⭐⭐    |
|     5 | Tokens                   | ⭐⭐⭐⭐⭐    |
|     6 | Temperature              | ⭐⭐⭐      |
|     7 | Prompt Engineering       | ⭐⭐⭐⭐⭐    |
|     8 | Streaming vs One-shot    | ⭐⭐⭐⭐     |
|     9 | Hallucination            | ⭐⭐⭐⭐⭐    |
|    10 | Embeddings / Vector DB   | ⭐⭐⭐⭐⭐    |
|    11 | Memory                   | ⭐⭐⭐⭐⭐    |
|    12 | RAG                      | ⭐⭐⭐⭐⭐    |
|    13 | Tools                    | ⭐⭐⭐⭐⭐    |
|    14 | MCP                      | ⭐⭐⭐⭐⭐    |
|    15 | AI Agents                | ⭐⭐⭐⭐⭐    |
|    16 | Types of Agents          | ⭐⭐⭐⭐     |
|    17 | AI Gateway               | ⭐⭐⭐⭐⭐    |
|    18 | Model Routing            | ⭐⭐⭐⭐⭐    |
|    19 | Model Switching/Fallback | ⭐⭐⭐⭐⭐    |
|    20 | Guardrails               | ⭐⭐⭐⭐⭐    |
|    21 | AI Observability         | ⭐⭐⭐⭐⭐    |
|    22 | AI Security/Governance   | ⭐⭐⭐⭐⭐    |

## One important addition

For a **real project**, I would add these topics to your list:

### 23. Embeddings

You mentioned vector databases, but embeddings should be studied separately first.

```text
Text
 ↓
Embedding Model
 ↓
Vector
 ↓
Vector DB
```

### 24. Context Window

Understand:

```text
Prompt
+ Conversation
+ RAG Context
+ Tool Results
+ Output
        ↓
Context Window
```

This connects directly to tokens and cost.

### 25. Structured Output

Learn how to make models return predictable structures such as:

```json
{
  "intent": "refund",
  "priority": "high",
  "confidence": 0.92
}
```

Very important for production applications.

### 26. AI Evaluation

This is missing from your list and is **very important**.

You need to answer:

> How do we know whether our AI system is actually good?

Study:

* Accuracy
* Relevance
* Faithfulness
* RAG evaluation
* Agent evaluation
* LLM-as-a-judge
* Test datasets
* Regression testing
* Human evaluation

### 27. AI Cost Management

Especially important for an enterprise platform:

```text
Model
 ↓
Tokens
 ↓
Cost
 ↓
Usage tracking
 ↓
Budget
 ↓
Optimization
```

This connects directly with **AI Gateway + Routing + Observability**.

---

# Your Final Mental Model

Don't think of these as 22 independent technologies.

Think of them as layers of **one AI platform**:

```text
                    ┌───────────────────┐
                    │    AI SECURITY    │
                    │   & GOVERNANCE    │
                    └─────────┬─────────┘
                              │
                    ┌─────────▼─────────┐
                    │   OBSERVABILITY   │
                    │ Logs/Trace/Cost   │
                    └─────────┬─────────┘
                              │
                    ┌─────────▼─────────┐
                    │    GUARDRAILS     │
                    └─────────┬─────────┘
                              │
                    ┌─────────▼─────────┐
                    │    AI GATEWAY     │
                    │ Routing/Switching │
                    └─────────┬─────────┘
                              │
                    ┌─────────▼─────────┐
                    │    AI AGENTS      │
                    │ Planning/Actions  │
                    └─────────┬─────────┘
                              │
                 ┌────────────┼────────────┐
                 ▼            ▼            ▼
              Tools          MCP         Memory
                 │                         │
                 │                         ▼
                 │                    RAG / Vector DB
                 │                         │
                 └────────────┬────────────┘
                              ▼
                         LLM / Models
                              │
                    ┌─────────┴─────────┐
                    │                   │
               Providers             Models
```

**If your goal is to build the Atlas 3.0 AI platform you mentioned earlier, this roadmap is the right direction:** first understand the individual AI concepts, then understand how they connect, and finally design the **gateway → routing → models → agents → tools/RAG → guardrails → observability → security/governance** architecture.

For the next step, would you prefer **(1) deep theory of each topic**, **(2) practical hands-on examples with code**, or **(3) Atlas 3.0 architecture mapped to all 27 topics**?
