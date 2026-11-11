# AI Agent Testing & Quality Evaluation Using DeepEval and Local LLMs

## Overview

This project demonstrates an end-to-end AI Agent Testing framework built using:

- DeepEval
- LangChain
- Ollama
- Qwen 2.5
- Synthetic Test Generation
- Tool-Based Agents

The goal was to evaluate the quality of a customer support AI agent, automatically generate realistic test cases from business documents, identify capability gaps, and improve agent performance through iterative testing.

---

## Problem Statement

Traditional chatbot testing relies heavily on manually created test cases.

This approach does not scale well because:

- Important scenarios can be missed
- Knowledge gaps remain hidden
- Agent capabilities are difficult to measure objectively
- Quality evaluation becomes subjective

This project uses AI-generated test cases and AI-based evaluation metrics to systematically assess and improve an AI agent.

---

## Solution Architecture

```text
Business Policy Documents
          │
          ▼
DeepEval Synthesizer
          │
          ▼
Synthetic Goldens
(Test Cases)
          │
          ▼
Customer Support Agent
          │
          ▼
DeepEval Evaluation
          │
          ▼
Correctness Score
Task Completion Score
Quality Analysis
```

---

## Agent Capabilities

The final agent supports:

✅ Order Status Tracking

✅ Refund Policy Requests

✅ Warranty Requests

✅ Exchange Requests

✅ Furniture Defect Handling

✅ Delivery Investigation Requests

---

## Tools Implemented

### get_order_status()

Returns:

- Order status
- ETA
- Product category

### get_refund_policy()

Returns refund policy by product category.

### get_warranty_policy()

Returns:

- Warranty coverage
- Claim requirements
- Warranty exclusions

### get_exchange_policy()

Returns:

- Exchange process
- Approval requirements
- Replacement rules

### get_furniture_support_policy()

Returns:

- Furniture defect reporting process
- Required photos
- Assembly detail requirements

### get_delivery_investigation_policy()

Returns:

- Delivery investigation procedures
- Carrier escalation guidance
- Missing parcel process

---

## Synthetic Test Generation

Instead of manually creating evaluation datasets, DeepEval Synthesizer was used.

Source documents included:

- Order Management Policies
- Refund Policies
- Exchange Policies
- Warranty Policies
- Delivery Policies

DeepEval automatically generated:

- Questions
- Expected Outputs
- Evaluation Goldens

Example:

### Generated Question

```text
How should customers request an exchange through their account or support with order details and desired replacement?
```

### Generated Expected Output

```text
Customers should request an exchange through their account or contact support with the order number and desired replacement.

An exchange is not confirmed until support sends an approval or exchange confirmation.
```

---

## Evaluation Metrics

### GEval Correctness

Measures:

- Factual correctness
- Policy compliance
- Completeness
- Hallucinations

Custom correctness criteria were implemented using a local judge model.

### Task Completion

Measures:

- Whether the agent successfully completed the user's request
- Whether required information was provided

---

## Evaluation Journey

### Initial Evaluation

The first version of the agent supported only:

- Order Status
- Refund Policies

Results:

```text
Correctness Score : 0.38
Pass Rate         : 20%
```

---

### Issues Identified

Synthetic testing uncovered missing capabilities:

- Warranty Support
- Exchange Workflow
- Furniture Defect Handling
- Delivery Investigation Process

---

### Improvements Implemented

Added:

```python
get_warranty_policy()

get_exchange_policy()

get_furniture_support_policy()

get_delivery_investigation_policy()
```

Updated:

- System Prompt
- Tool Instructions
- Policy Coverage
- Evaluation Dataset Filtering

---

## Final Evaluation Results

### Correctness

```text
Average Score : 0.86
Pass Rate     : 100%
```

### Task Completion

```text
Average Score : 0.97
Pass Rate     : 100%
```

---

## Key Findings

### Before

```text
Correctness : 0.38
Pass Rate   : 20%
```

### After

```text
Correctness : 0.86
Task Completion : 0.97
Pass Rate : 100%
```

Improvement achieved through:

- Synthetic testing
- Gap analysis
- Tool expansion
- Prompt refinement
- Iterative evaluation

---

## Tech Stack

### AI & Evaluation

- DeepEval
- Ollama
- Qwen 2.5

### Agent Framework

- LangChain
- MCP Tools

### Embeddings

- nomic-embed-text

### Vector Database

- ChromaDB

### Language

- Python

---

## Project Structure

```text
.
├── documents/
│   ├── order_management.txt
│   ├── exchange_policies.txt
│   ├── refund_policy.txt
│
├── goldens/
│   └── goldens.json
│
├── agent_instrumented.py
├── ollama_embedder.py
├── test_agent_synthesizer.py
├── test_CustomMetric.py
│
├── screenshots/
│   ├── baseline_results.png
│   ├── final_results.png
│
└── README.md
```

---

## Installation

```bash
git clone https://github.com/<YOUR_USERNAME>/deepeval-ai-agent-testing.git

cd deepeval-ai-agent-testing
```

Create virtual environment:

```bash
python -m venv .venv
```

Activate:

```bash
.venv\Scripts\activate
```

Install dependencies:

```bash
pip install -r requirements.txt
```

---

## Run Synthetic Dataset Generation

```bash
python test_agent_synthesizer.py
```

Output:

```text
Generated 18 goldens
```

---

## Run Evaluation

```bash
python test_CustomMetric.py
```

Sample Output:

```text
Correctness [GEval] : 0.86

Task Completion : 0.97

Pass Rate : 100%
```

---

## Skills Demonstrated

- AI Agent Testing
- LLM Evaluation
- DeepEval
- Synthetic Test Generation
- Prompt Engineering
- LangChain
- Local LLM Evaluation
- AI Quality Assurance
- Root Cause Analysis
- Agent Improvement
- Tool-Based Agents

---

## Future Enhancements

Planned enhancements:

- ToolCorrectnessMetric
- AnswerRelevancyMetric
- Contextual Recall
- Contextual Precision
- RAG Evaluation Framework
- PDF Knowledge Base Testing

---

## Author

**Azharulla Mohammed**

Senior QA Engineer | AI QA Enthusiast

Specializing in:

- AI Agent Testing
- DeepEval
- RAG Evaluation
- Generative AI Quality Assurance
- Local LLM Testing
