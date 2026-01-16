# Project 2: Automated Research Analyst

**Due Date**: End of Day 4
**Objective**: Build an AI agent that can accept a broad research topic, decompose it into sub-questions, gather information from the web (and optionally documents), and synthesize a structured research report with citations.

This project emphasizes **Prompting (Chain-of-Thought)**, **Web Grounding (Search)**, and **Structured Output**.

---

## 🚀 Scenario

You are working for a Market Research firm. Analysts spend hours manually searching Google to answer questions like "What are the latest trends in renewable energy for 2025?". Your goal is to automate this first pass of research.

The user provides a high-level **Topic**.
The agent must:
1.  **Plan**: Break the topic down into 3-5 specific sub-questions.
2.  **Research**: Use Google Search to find answers for each sub-question.
3.  **Synthesize**: Compile the findings into a cohesive report.

---

## 🛠️ Requirements

### 1. Research Planning (Chain-of-Thought)
*   **Input**: A broad topic (e.g., "The future of Generative AI in Education").
*   **Process**: Use a **Chain-of-Thought** prompt to generate a research plan consisting of 3-5 key sub-questions that need verification.
*   **Output**: A list of strings (the sub-questions).

### 2. Information Gathering (Search Grounding)
*   **Process**: Iterate through the generated sub-questions.
*   **Tool**: For each valid sub-question, use **Google Search Grounding** (Day 3) to retrieve the latest information.
*   **Data**: Collect the text summary and the source URLs (citations).

### 3. Synthesis & Verification (Pointwise Evaluation)
*   **Synthesis**: Feed the gathered search results back into the model to generate a section for each sub-question.
*   **Self-Correction**: Before finalizing a section, use a **Pointwise Evaluation** prompt (Day 1) to check: "Does this text actually answer the specific sub-question based on the provided search results?"
    *   If score < 3/5, try to re-synthesize or note that data was insufficient.

### 4. Final Report (Structured Output)
*   **Format**: The final output must be a valid Markdown report wrapped in a JSON structure (using Pydantic/Structured Output):
    *   `title`: A catchy title for the report.
    *   `executive_summary`: A 3-sentence high-level summary.
    *   `sections`: A list of objects, each with `heading`, `content`, and `citations` (URLs).

---

## 📂 Deliverables

1.  `analyst.py`: The main application code handling planning, searching, and synthesizing.
2.  `evaluate_research.py`: A script that runs the agent on 3 different topics and saves the Markdown reports.
3.  `project2_report.md`: A brief reflection on:
    *   How well the "Planning" step worked.
    *   Quality of Google Search results.
    *   Example of a generated report.

---

## 💡 Hints & Resources

*   **D1**: Chain-of-Thought prompting is crucial for the "Planning" phase.
*   **D1**: Use `day_1b_evaluation-and-structured-output.py` for defining the Report structure.
*   **D3**: Use `day_3_search_grounding.py` for the core research capability.
*   **Prompt Engineering**: You will need distinct system instructions for the Planner, the Researcher, and the Writer.

## ✅ Rubric

| Criteria | Points | Description |
| :--- | :--- | :--- |
| **Research Plan** | 20 | Model successfully breaks down broad topics into relevant sub-questions. |
| **Search Integration** | 20 | Successfully calls Google Search for each sub-question. |
| **Synthesis Quality** | 20 | Responses are grounded in search results, not hallucinated. |
| **Self-Correction** | 20 | Implementation of the "Judge" check for section relevance. |
| **Final Report** | 20 | Valid JSON output with Title, Summary, and Citations. |
| **Total** | **100** | |
