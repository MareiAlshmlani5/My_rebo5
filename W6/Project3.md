# Project 3: Intelligent Customer Support Simulator

**Due Date**: End of Day 4
**Objective**: Build a "Human-in-the-Loop" style support agent that classifies tickets, checks company policies via RAG, and executes sensitive actions (like refunds) using Function Calling.

This project emphasizes **Embeddings (Classification)**, **RAG**, and **Function Calling**.

---

## 🚀 Scenario

You are building the backend logic for a Customer Support Chatbot for an E-commerce store. The bot needs to handle 3 types of situations:
1.  **General Inquiries**: "How do I reset my password?" -> Answer using Docs (RAG).
2.  **Refund Requests**: "I want my money back." -> Check Policy (RAG) + Execute Refund (Tool).
3.  **Spam/Off-topic**: "Write me a poem." -> Refuse politely.

Your goal is to build the decision engine that takes a user message and executes the right workflow.

---

## 🛠️ Requirements

### 1. Triage (Classification)
*   **Input**: inbound user message.
*   **Process**: Use **Embeddings** (Day 2) to compute similarity against 3 anchor examples:
    *   Anchor A: "System issue, broken, login help" (Technical Support)
    *   Anchor B: "Refund, money back, return" (Billing/Refunds)
    *   Anchor C: "Hello, joke, poem, weather" (General/Chat)
*   *Alternatively*, you can use a **Classifier** Prompt.

### 2. Policy Check (RAG)
*   **Dataset**: A simple text file ruleset (e.g., "Refunds are only allowed within 30 days. No refunds on digital items.").
*   For **Refund Requests**:
    *   Perform a RAG lookup to see if the user's request violates any policy.
    *   The model must "Read" the retrieved policy before calling the tool.

### 3. Action Execution (Function Calling)
*   **Tools**: Implement dummy functions:
    *   `issue_refund(order_id: str, reason: str)`
    *   `create_support_ticket(subject: str, priority: str)`
*   **Logic**:
    *   If Policy Check PASSES -> Function Call `issue_refund`.
    *   If Policy Check FAILS -> Explain why to the user (no tool call).

### 4. Dynamic Response
*   Unlike Project 1, this agent must maintain a persona. It should be empathetic but firm on policy.
*   Generate the final response to the user summarizing what action was taken (e.g., "I've processed your refund of $50...").

---

## 📂 Deliverables

1.  `support_agent.py`: Main logic handling the Triage -> Policy -> Action flow.
2.  `evaluate_scenarios.py`: A script that runs 5 specific test cases (e.g., "Valid Refund", "Invalid Refund", "Tech Support").
3.  `project3_report.md`: A brief explanation of how you handled the "Policy Check" logic (did you use RAG context in the system instruction?).

---

## 💡 Hints & Resources

*   **D2**: Use Embeddings/Similarity for the Triage step (it's often faster/cheaper than a full LLM call).
*   **D2**: RAG is needed to make the agent "aware" of the refund rules.
*   **D3**: Function Calling is the specific way to trigger the `issue_refund` action.
*   **Persona**: You can use System Instructions (Day 1) to set the tone of the agent.

## ✅ Rubric

| Criteria | Points | Description |
| :--- | :--- | :--- |
| **Triage Logic** | 20 | Correctly categorizes incoming input (Refund vs Tech vs Chat). |
| **Policy RAG** | 20 | Successfully retrieves policy rules before making a decision. |
| **Decision Logic** | 20 | Agent respects the policy (doesn't refund if rules say no). |
| **Tool Execution** | 20 | Correctly formats the function call when a refund is valid. |
| **Persona flows** | 20 | Professional and empathetic responses. |
| **Total** | **100** | |
