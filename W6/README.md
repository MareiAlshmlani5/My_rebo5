# Building Generative AI Applications

**Objective**: The student is able to build AI applications to solve problems, beyond manual copy-pasting into commonly available chat interfaces like ChatGPT and Gemini.

## 8-Day AI Engineering Course Outline

### Day 1: Foundations
*   **Prompting** (`day_1a_prompting.py`)
    *   Zero-Shot Prompting
    *   Few-Shot Prompting
    *   Chain-of-Thought Prompting
    *   System Instructions
    *   Code Generation and Execution
*   **Evaluation and Structured Output** (`day_1b_evaluation-and-structured-output.py`)
    *   Structured Output
    *   Pointwise Evaluation
    *   Pairwise Evaluation
    *   Evaluation Methods

### Day 2: Embeddings & RAG
*   **Embeddings and Similarity Scores** (`day_2_similarity.py`)
    *   Understanding Embeddings
    *   Semantic Similarity Calculations
*   **Classifying Embeddings with PyTorch** (`day_2_classifier_pytorch.py`)
    *   Classification tasks using embeddings
    *   Building classification models with PyTorch
*   **Document Q&A with RAG** (`day_2_qa_rag.py`)
    *   Retrieval Augmented Generation implementation
    *   Using ChromaDB for vector storage

### Day 3: Function Calling & Grounding
*   **Function Calling with the Gemini API** (`day_3_function_calling.py`)
    *   Function Calling basics
    *   Automatic Function Calling
    *   Database integration with function calling
*   **Google Search Grounding** (`day_3_search_grounding.py`)
    *   Grounding with Google Search
    *   Inspecting grounding metadata
    *   Adding inline citations

### Project 1:

* Option 1: Project 1: Smart Knowledge Assistant
* Option 2: Automated Research Analyst
* Option 3: Intelligent Customer Support Simulator

### Day 4: From Prompt to Action & Agent Architectures
*   **From Prompt to Action** (`day_4a_from_prompt_to_action.py`)
    *   Building your first AI agent with ADK
    *   Agent Development Kit (ADK) setup
    *   Creating agents with tools
*   **Multi-Agent Systems & Workflow Patterns** (`day_4b_agent_architectures.py`)
    *   Sequential Agents
    *   Parallel Agents
    *   Loop Agents
    *   Multi-agent orchestration patterns

### Day 5: Agent Tools & Best Practices
*   **Agent Tools** (`day_5a_agent_tools.py`)
    *   Custom Function Tools
    *   Agent Tools (using agents as tools)
    *   Built-in Code Executor
    *   Tool types overview
*   **Agent Tool Patterns and Best Practices** (`day_5b_agent_tools_best_practices.py`)
    *   Model Context Protocol (MCP) integration
    *   Long-Running Operations (LRO)
    *   Human-in-the-loop approvals
    *   Resumable workflows

### Day 6: Sessions & Memory
*   **Memory Management - Part 1: Sessions** (`day_6a_agent_sessions.py`)
    *   Session Management
    *   Persistent Sessions with DatabaseSessionService
    *   Context Compaction
    *   Session State management
*   **Memory Management - Part 2: Memory** (`day_6b_agent_memory.py`)
    *   Long-term memory with MemoryService
    *   Memory ingestion and retrieval
    *   Automatic memory storage with callbacks
    *   Memory consolidation concepts

### Day 7: Observability & Evaluation
*   **Agent Observability** (`day_7a_agent_observability.py`)
    *   Logs, Traces & Metrics
    *   Debugging with ADK Web UI
    *   LoggingPlugin for production
    *   Custom plugins and callbacks
*   **Agent Evaluation** (`day_7b_agent_evaluation.py`)
    *   Interactive evaluation with ADK Web UI
    *   Systematic evaluation with test cases
    *   Tool trajectory and response metrics
    *   Regression testing

### Day 8: Agent2Agent Communication & Deployment
*   **Agent2Agent (A2A) Communication** (`day_8a_agent2agent_communication.py`)
    *   A2A Protocol overview
    *   Exposing agents via A2A
    *   Consuming remote agents
    *   Cross-framework and cross-organization integration
*   **Agent Deployment** (`day_8b_agent_deployment.py`)
    *   Deploying to Vertex AI Agent Engine
    *   Production-ready agent configuration
    *   Testing deployed agents
    *   Long-term memory with Vertex AI Memory Bank
    *   Cost management and cleanup
