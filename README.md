# Agentic AI Safety and Guardrails

**Agentic AI Bootcamp — Army Cyber Institute, U.S. Military Academy**

This module covers two critical questions every practitioner must answer before deploying an agentic system: *Is it safe?* and *Does it actually work?* Materials are designed for a single instructional block and include a full slide deck, printable reference sheet, and hands-on Python lab.

---

## Files

### `Agentic AI Safety and Guardrails.tex`
Original short slide deck providing a high-level overview of guardrail architecture, a brief metrics table, and the kill-switch / HITL design pattern. Good as a quick-reference companion or for a condensed briefing.

### `Evaluating Agentic AI Safety and Performance.tex`
Full 32-slide Beamer presentation covering the complete evaluation curriculum. Structured in two parts:

**Part I — Safety**
- Undesired behavior taxonomy: bias, toxicity, hallucination, prompt injection, PII leakage, over-refusal
- Bias types (representation, stereotyping, allocation, sentiment) and measurement tools (WEAT, StereoSet, BBQ, WinoBias, BOLD)
- Toxicity detection tools (Detoxify, Perspective API, Azure Content Safety, LlamaGuard) with code examples
- Hallucination types and benchmarks (TruthfulQA, HELM, RAGAS, FActScorer)
- Prompt injection: direct vs. indirect, agentic attack surface, mitigations
- Multi-layer guardrail architecture diagram (input → planning → tool-use → output → HITL)
- Guardrail tool comparison table (LlamaGuard, NeMo, Azure, AWS Bedrock, Presidio)

**Part II — Performance**
- Infrastructure metrics: TTFT, E2E latency, ITL, TPS, RPS, token economy, cost per task
- Latency budget visualization (prefill, decode, network)
- Token utilization and context window management strategies
- Agentic task metrics: TSR, GSR, Tool Selection Accuracy, Step Efficiency, Plan Validity Rate, Recovery Rate, AVM
- Task Success Rate anatomy flowchart
- Step Efficiency formula and examples
- Agent Value Multiple (AVM): formula, interpretation, DoD justification example
- Benchmark landscape: GAIA, SWE-bench, WebArena, AgentBench, τ-bench
- HELM holistic evaluation overview
- Domain-specific eval pipeline loop (5-step continuous improvement cycle)
- LLM-as-Judge: frameworks, limitations, calibration best practices
- Eval dashboard: safety signals, infrastructure KPIs, task KPIs
- Common failure patterns and recommended fixes
- Red teaming: adversarial evaluation activities and tools (PyRIT, Garak, Promptfoo, HarmBench)
- Lab exercise slide and references

Uses the `d2s` Beamer theme consistent with the rest of the Agentic AI Bootcamp series. All diagrams are built with TikZ (no external image dependencies).

### `Diagrams and Reference Sheet.tex`
Standalone 6-page article-class handout for students. Compiles independently (no custom theme required). Contains:

- **Diagram 1** — Undesired LLM Behavior Taxonomy (full taxonomy with sub-bullets, color-coded by risk level)
- **Diagram 2** — Multi-Layer Guardrail Architecture (input through HITL, with per-layer annotations)
- **Diagram 3** — Latency Budget Breakdown (TTFT marker, E2E bracket, optimization hints)
- **Diagram 4** — Agentic Task Evaluation Flow (decision tree with TSR impact at each failure point)
- **Diagram 5** — Evaluation Pipeline Overview (5-step continuous improvement loop)
- Quick reference tables: safety metrics, infrastructure KPIs, agentic task metrics, AVM formula
- Tool selection guide (which tool for which problem, open-source status)
- Common failure patterns cheat sheet (symptom → root cause → recommended fix)

### `Lab - Evaluating Agentic AI.ipynb`
Hands-on Python notebook with 8 sections. Students work through a complete evaluation workflow:

1. **Environment Setup** — package installation, API key configuration
2. **Toxicity Evaluation** — Detoxify scoring on sample agent outputs, bar chart visualization, threshold discussion
3. **Bias Probing** — BERT fill-mask gender bias probe across 5 professions, grouped bar chart
4. **Infrastructure Performance** — TTFT and E2E latency measurement via OpenAI streaming API (with simulated fallback if no key); token counting with tiktoken
5. **Agentic Task Performance** — TSR, Step Efficiency, and Tool Selection Accuracy computed from simulated agent run logs
6. **LLM-as-Judge** — Multi-dimension automated scoring (accuracy, relevance, completeness, safety) with heatmap output
7. **AVM Calculator** — Full AVM computation with sensitivity analysis chart (AVM vs. queries/day)
8. **Capstone** — Evaluation summary table and reflection questions for a deployment decision exercise

Requires: `detoxify`, `transformers`, `openai`, `tiktoken`, `pandas`, `matplotlib`, `seaborn`. Live API calls require an OpenAI key; all sections include simulated fallback data.

---

## Compilation

All `.tex` files use standard TeX Live packages. The presentation requires the `d2s` Beamer theme (shared across the Agentic AI Bootcamp). The reference sheet compiles with any standard TeX Live installation.

```bash
# Presentation (requires d2s theme)
pdflatex "Evaluating Agentic AI Safety and Performance.tex"
pdflatex "Evaluating Agentic AI Safety and Performance.tex"  # second pass for references

# Reference sheet (no custom theme)
pdflatex "Diagrams and Reference Sheet.tex"
pdflatex "Diagrams and Reference Sheet.tex"
```

---

## Module Learning Objectives

By the end of this module, students will be able to:
- Classify undesired LLM behaviors (bias, toxicity, hallucination, injection) with concrete examples
- Select the appropriate evaluation tool for a given safety concern
- Interpret TTFT, TPS, and token utilization data and act on it
- Apply TSR, Tool Selection Accuracy, and GSR to benchmark an agentic system
- Compute Agent Value Multiple (AVM) to justify operational investment
- Design a repeatable evaluation pipeline that combines safety and performance signals

---

*Part of the Agentic AI Bootcamp series — Army Cyber Institute, U.S. Military Academy*
