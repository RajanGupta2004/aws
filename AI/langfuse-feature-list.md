

## Langfuse — Feature List

| #  | Feature                         | What it does                                                | Business/Technical Value                             |
| -- | ------------------------------- | ----------------------------------------------------------- | ---------------------------------------------------- |
| 1  | **LLM Tracing**                 | Tracks the complete flow of an AI request                   | Understand exactly what happened during each request |
| 2  | **LLM Observability**           | Monitors LLM calls, prompts, outputs, latency, errors, etc. | Makes AI applications easier to operate              |
| 3  | **Prompt Management**           | Create, manage, version, and monitor prompts                | Prevents uncontrolled prompt changes                 |
| 4  | **Prompt Versioning**           | Maintains different versions of prompts                     | Compare old vs new prompt performance                |
| 5  | **Token Tracking**              | Tracks input, output, and total tokens                      | Understand usage and optimize token consumption      |
| 6  | **Cost Tracking**               | Estimates/records LLM usage costs                           | Control and optimize AI spending                     |
| 7  | **Latency Monitoring**          | Measures execution time of LLM calls and application steps  | Identify performance bottlenecks                     |
| 8  | **Error Tracking**              | Records failures in LLM calls and application workflows     | Faster troubleshooting and debugging                 |
| 9  | **RAG Observability**           | Tracks retrieval and RAG-related operations                 | Identify poor retrieval or context problems          |
| 10 | **Agent Observability**         | Tracks agent steps, decisions, tool calls, and LLM calls    | Debug complex AI agents                              |
| 11 | **Tool/Function Call Tracking** | Records tools/functions called by the AI                    | Understand and debug tool execution                  |
| 12 | **Evaluation**                  | Evaluate the quality of AI responses                        | Measure whether the AI is producing useful results   |
| 13 | **User Feedback**               | Capture feedback/scores associated with AI outputs          | Understand real user satisfaction                    |
| 14 | **Dataset Management**          | Manage datasets used for testing/evaluation                 | Build repeatable AI evaluation workflows             |
| 15 | **Experimentation**             | Compare different prompts, models, or configurations        | Determine which configuration performs better        |
| 16 | **Model Monitoring**            | Track which models are being used and their performance     | Compare models and optimize model selection          |
| 17 | **Sessions**                    | Group related traces/interactions into sessions             | Understand multi-step user conversations             |
| 18 | **Metadata & Tags**             | Add custom metadata, tags, users, environments, etc.        | Filter and analyze AI activity                       |
| 19 | **Dashboards/Analytics**        | Visualize AI usage and performance                          | Give engineering/business teams visibility           |
| 20 | **Production Monitoring**       | Monitor AI applications after deployment                    | Detect production issues                             |
| 21 | **OpenTelemetry Support**       | Integrate with broader observability standards              | Connect AI observability with existing systems       |
| 22 | **SDK/API Integration**         | Integrate Langfuse into applications through SDKs/APIs      | Easy integration with application code               |
| 23 | **Framework Integrations**      | Integrate with popular LLM/AI frameworks                    | Reduce custom integration work                       |
| 24 | **Self-Hosting**                | Deploy Langfuse in your own infrastructure                  | Greater control over data and infrastructure         |
| 25 | **Security & Access Control**   | Manage access to Langfuse resources                         | Support enterprise security requirements             |

### The features can be grouped into 6 major areas

```text
                    LANGFUSE
                       │
       ┌───────────────┼────────────────┐
       │               │                │
       ↓               ↓                ↓
  OBSERVABILITY     EVALUATION       PROMPTS
       │               │                │
  • Tracing        • Scores         • Management
  • Tokens         • Datasets       • Versioning
  • Cost           • Experiments    • Testing
  • Latency        • Feedback
  • Errors
       │
       ├─────────────────────────────────┐
       │                                 │
       ↓                                 ↓
   AI WORKFLOWS                    INTEGRATION
       │                                 │
   • RAG                              • SDK
   • Agents                           • API
   • Tools                            • OpenTelemetry
   • Sessions                         • Frameworks
       │
       └─────────────────────────────────┐
                                         ↓
                                  ENTERPRISE
                                         │
                                  • Self-hosting
                                  • Security
                                  • Access control
                                  • Data control
```
