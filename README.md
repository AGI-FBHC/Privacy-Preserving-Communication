# Privacy-Preserving Communication among LLMs with Local Semantic Compensation


> 🔒 **Note**: We will release the full source code upon acceptance of the paper. This repository currently serves as a placeholder for documentation and experimental setup.

---

## 🔍 Overview

Large Language Models (LLMs) have shown impressive capabilities, but their deployment in interactive and multi-agent systems raises serious **privacy concerns**. Existing approaches often:
- Focus solely on training-time protection (e.g., differential privacy)
- Suffer from semantic degradation due to masking
- Neglect privacy during **LLM-to-LLM communication**

### 💡 Our Contribution

We propose a **unified framework** that ensures both **privacy preservation** and **semantic fidelity**, through:
- ⚖️ Prompt-driven privacy judgment during inter-LLM messaging
- 🧩 Rule-based fuzzy anonymization for long user-side inputs
- 🤝 Multi-agent semantic compensation to restore degraded meaning

Our method effectively balances **privacy** and **utility**, making it suitable for real-world deployment in **sensitive multi-agent LLM applications**.

---

## 🧠 Key Features

### 1. Prompt-Driven Privacy Judgment (Inter-LLM)
- Uses NER + LLM prompts to evaluate sensitivity of entities
- Applies masking only when necessary, preserving task-relevant content

### 2. Rule-Based Fuzzy Anonymization (User-to-LLM)
- Splits long text inputs into chunks (≤512 tokens)
- Performs NER on each chunk and applies rule- or LLM-based replacement
- Ensures consistent anonymization of repeated entities

### 3. Multi-Agent Semantic Compensation
- Classifies question types (knowledge-based or logic-based)
- Invokes specialized expert agents and adversarial agents to verify/correct reasoning
- Supports semantic restoration and robustness in QA tasks

---

## 🧪 Experiments

We evaluate our approach on four public datasets:
- 📘 Knowledge Privacy Preservation (KPP)
- 🧠 Logic Privacy Preservation (LPP)
- ✍️ Trivia Creative Writing
- 🔍 Logic Grid Puzzle

### ✅ Performance Highlights

| Model               | BLEU↑ | SemSim↑ | Precision↑ | Recall↑ | F1↑ |
|---------------------|-------|---------|------------|---------|-----|
| GPT-4o Prompt       | 80    | 95      | 88         | 90      | 89  |
| NER + Regex Baseline| 69    | 95      | 82         | 84      | 83  |
| **Ours (Local + Agents)** | **86** | **97**  | **93**       | **95**     | **94** |

- GPT-4o and DeepSeek-R1 show strong built-in privacy-handling capability.
- Our method provides the best balance of **precision** and **semantic retention**.
- Multi-agent compensation significantly improves logic QA accuracy.

---

## 🧪 Example Workflow

```
Input → NER → Privacy Judgement → Fuzzy Masking → Multi-Agent Answering → Output
```

```python
# Example: Prompt-based sensitivity evaluation
entity = "John Doe"
context = "John Doe lives in Paris and wants a lawyer."
is_sensitive = LLM.prompt(f"Is '{entity}' sensitive in this context?")  # True or False
```

---

## 📂 Repository Structure

```
├── ner_module/                # NER models for entity extraction
├── privacy_masking/           # Fuzzification (rule-based & LLM-based)
├── multi_agent_framework/     # Classification, domain experts, adversarial checkers
├── datasets/                  # KPP, LPP, Trivia, LogicGrid
├── evaluation/                # Scripts for BLEU, Semantic Similarity, F1
└── README.md                  # This file
```

---

## 📜 Ethics Statement

- All data used were either anonymized or publicly available.
- No personally identifiable information (PII) is stored, exposed, or redistributed.
- Experiments follow ACL’s research ethics standards.

---

## 🙏 Acknowledgments

We acknowledge:
- OpenAI (GPT-4o), DeepSeek (R1), Meta (LLaMA 3), and Google (Gemini 2.0) for providing API/model access.
- Dataset authors for supporting open research.

---

## 📌 Citation

> We will update the citation and provide full source code once the paper is accepted.

---
