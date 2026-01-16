# Project 1: Smart Knowledge Assistant

**Due Date**: End of Day 4
**Objective**: Build a comprehensive "Smart Knowledge Assistant" that intelligently routes queries, retrieves information from documents or the web, executes tools, and evaluates its own responses.

This project consolidates learning from **Day 1 (Prompting & Evaluation)**, **Day 2 (Embeddings & RAG)**, and **Day 3 (Function Calling & Grounding)**.

---

## 🚀 Scenario

You are building an advanced AI assistant for a tech company. The assistant needs to handle various types of user requests:
1.  **Technical Questions**: Answered using internal documentation (RAG).
2.  **Current Events/Real-time Info**: Answered using Google Search.
3.  **Utility Tasks**: Performed using specific tools (e.g., getting weather, calculating dates).
4.  **General Chit-chat**: Handled by the model directly.

Your goal is to build a system that accepts a user query, **routes** it to the correct handler, operates the handler, and **evaluates** the quality of the answer.

---

## 🛠️ Requirements

### 1. Intelligent Routing (Classification)
You must implement a routing mechanism that decides which "Agent" or "Tool" should handle the user's query.
*   **Input**: User query string.
*   **Output**: One of `['RAG', 'SEARCH', 'TOOL', 'CHAT']`.
*   **Implementation**: You can use **Zero-shot Classification (Prompting)** OR **Embedding-based Classification**.

### 2. Knowledge Retrieval (RAG)
For queries routed to `RAG`:
*   **Source Material**: Use the provided "Company Policy" snippets (or any simple text dataset you choose).
*   **Pipeline**:
    1.  Embed the user query.
    2.  Retrieve top-k relevant chunks from your Vector DB (e.g., ChromaDB or in-memory array).
    3.  Generate an answer using these chunks as context.

### 3. Web Grounding (Search)
For queries routed to `SEARCH`:
*   Use **Google Search Grounding** (Day 3) to answer questions about current events or dynamic topics (e.g., "What is the stock price of Google today?").
*   Ensure the response includes citations if available.

### 4. Tool Execution
For queries routed to `TOOL`:
*   Implement at least **one** custom tool using **Function Calling** (e.g., `get_weather(city)`, `calculate_loan_payment()`, or `lookup_employee_email(name)`).
*   The model should extract parameters, call the function, and synthesize the result.

### 5. Structured Output & Self-Evaluation
*   **Structured Response**: Your final `generate_response` function must return a JSON object (using Pydantic/Structured Output) containing:
    *   `answer`: The text response.
    *   `source`: Which method was used (e.g., "RAG", "Google Search").
    *   `confidence_score`: A self-assessed score (1-5) of how well the model thinks it answered.
*   **Evaluation Script**: Write a separate script `evaluate.py` that:
    1.  Runs your assistant against 5 pre-defined test cases (one for each category).
    2.  Uses **Pointwise Evaluation** (LLM-as-a-Judge) to score the actual relevance of the answers 1-5.
    3.  Prints a comparison of `confidence_score` vs `judge_score`.

---

## 📂 Deliverables

1.  `assistant.py`: The main application code containing your Route, RAG, Search, and Tool logic.
2.  `evaluate.py`: The evaluation script processing test cases.
3.  `project1_report.md`: A brief (1-page) report containing:
    *   Your routing strategy explanation.
    *   Results of your 5 test cases.
    *   One challenge you faced and how you solved it.

---

## 💡 Hints & Resources

*   **D1**: Refer to `day_1b_evaluation-and-structured-output.py` for Pydantic models (Structured Output) and Evaluation prompts.
*   **D2**: Refer to `day_2_qa_rag.py` for setting up a simple RAG pipeline.
*   **D3**: Refer to `day_3_search_grounding.py` for Search, and `day_3_function_calling.py` for Tools.
*   **API Keys**: Ensure your `GOOGLE_API_KEY` is set in your environment.

## ✅ Rubric

| Criteria | Points | Description |
| :--- | :--- | :--- |
| **Routing Logic** | 20 | Correctly identifies when to use RAG, Search, or Tools. |
| **RAG Implementation** | 20 | Successfully retrieves relevant context and answers document-based questions. |
| **Tool/Search Use** | 20 | Successfully calls the search tool or custom function when appropriate. |
| **Structured Output** | 20 | Returns valid JSON with answer, source, and confidence. |
| **Evaluation Script** | 20 | Script runs and produces a "Judge Score" for the outputs. |
| **Total** | **100** | |
