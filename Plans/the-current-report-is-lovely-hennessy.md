# Plan: Course Update Task 1 — Local LLM Research Report

## Context

The O'Reilly Llama course was last substantively updated in early 2025 (models guide) and Feb 2026 (fine-tuning notebooks). The open-source LLM ecosystem has shifted significantly: new model families (Gemma 4, Qwen 3.x) have been released, Ollama has matured considerably vs llama-cpp-python, and the community has converged around certain tools for practical local use. This research task produces a single authoritative report (`local-llm-research/RESEARCH-REPORT-2026.md`) that will directly inform which notebooks to update, replace, or add.

---

## Deliverable

**`local-llm-research/RESEARCH-REPORT-2026.md`** — a structured research report with four sections (A–D below), each ending with a clear decision or ranked recommendation. This will be used to update course notebooks and the `best-local-models-2025.md` guide.

---

## Research Sections

### A. Ollama vs llama-cpp: Comparison + Decision

**Goal:** Clear recommendation on which to use as the course's primary local inference backend.

**Research tasks:**
1. Web search current state of both projects (GitHub stars, release cadence, community activity, docs quality)
2. Compare on: ease of install, model support breadth, API compatibility (OpenAI-compatible?), streaming, tool calling, multimodal, performance overhead
3. Check r/LocalLLaMA, Hacker News, and Simon Willison's blog for practitioner opinions
4. Look at the existing `1.0-quickstart-ollama.ipynb` to understand current course dependency

**Sources to check:**
- https://ollama.ai (official docs/changelog)
- https://github.com/ollama/ollama (README, issues, releases)
- https://github.com/abetlen/llama-cpp-python (README, releases)
- Recent r/LocalLLaMA posts comparing both

**Decision format:** one clear winner for the course's primary path, with a note on when llama-cpp is still preferred (e.g., embedded use, fine-grained GGUF control).

---

### B. Local RAG Tools: Practical Comparison

**Goal:** Which tool/approach gives the most reliable, functional RAG for personal use AND for building into apps?

**Research tasks:**
1. Read and summarize each candidate's approach:
   - simonwillison embeddings approach (sqlite-utils + LLMs)
   - semtools (run-llama/semtools)
   - smolagents RAG (HuggingFace)
   - Compare against existing course stack (LlamaIndex + ChromaDB + Ollama, in `2.1-local-rag.ipynb`)
2. For each, evaluate: setup complexity, retrieval quality, speed, Ollama compatibility, maintenance activity
3. Web search for practitioner reports, GitHub issues, recent blog posts on each
4. Check the existing `local-llm-research/LOCAL_LLM_RESEARCH_REPORT.md` for prior findings

**Decision format:** ranked matrix (personal use vs app development), with a recommendation on whether the current course notebook stack needs to change.

---

### C. Top Models for Commercial Use by Compute Tier

**Goal:** Updated model guide replacing `best-local-models-2025.md` with 2026-current recommendations.

**Compute tiers to cover:**
- **Tier 1 — CPU / no GPU** (8–16GB RAM): What's actually usable?
- **Tier 2 — Consumer GPU** (8–16GB VRAM, RTX 3080/4070 class): Best balance models
- **Tier 3 — Prosumer GPU** (24GB VRAM, RTX 4090/A6000): High-quality options
- **Tier 4 — Multi-GPU / Cloud** (2×24GB+): Near-SOTA open models

**Candidates to research** (user-specified + obvious leaders):
- Gemma 4 family (Google)
- Qwen 3.5, Qwen 3.6 (Alibaba)
- Llama 3.x current state
- Mistral/Mixtral current releases
- DeepSeek current (post-V3)
- Phi-4 family (Microsoft)

**Sources:**
- https://ollama.com/library (filter by most downloaded)
- https://huggingface.co/spaces/open-llm-leaderboard/open_llm_leaderboard
- LMSYS Chatbot Arena rankings (current)
- Web search for "best local LLM 2026 commercial use"

**Decision format:** table by tier, columns: model, size, license (commercial ok?), strengths, weaknesses, Ollama tag.

---

### D. Community-Validated Tools for Local LLM Experimentation

**Goal:** What tools do practitioners actually use and recommend for running local models reliably?

**Tools to evaluate:**
- Ollama
- LM Studio
- llama-cpp (raw)
- Open WebUI
- Hugging Face (local pipeline / Spaces)
- vLLM
- Any others surfaced by research (Jan.ai, GPT4All, etc.)

**Research tasks:**
1. Search r/LocalLLaMA (recent 3–6 months) for "what do you use", "best tool", "recommendation" threads
2. Web search for "best local LLM tools 2026"
3. Check Simon Willison's blog and newsletter for recent tool coverage
4. Evaluate each on: Windows/Mac/Linux support, ease of use, GPU/CPU support, OpenAI API compatibility, active maintenance

**Decision format:** ranked list by use case (beginners / developers / power users), with notes on platform support.

---

## Execution Approach

Use parallel subagents for sections A, B, C, D simultaneously. Each agent:
1. Performs web searches (5–10 queries per section)
2. Fetches key URLs listed above
3. Synthesizes findings into its section of the report

Research agent types: `ClaudeResearcher` or `PerplexityResearcher` for web content, `GeminiResearcher` for broader coverage.

After all 4 agents complete, merge findings into `RESEARCH-REPORT-2026.md` with a top-level **Executive Summary** and **Course Update Recommendations** section.

---

## Output Structure (`RESEARCH-REPORT-2026.md`)

```
# Local LLM Research Report — 2026

## Executive Summary (1 page)
## Course Update Recommendations

## A. Ollama vs llama-cpp: Decision
## B. Local RAG Tools: Ranked Matrix
## C. Top Models by Compute Tier: Table
## D. Community Tools: Ranked List

## Sources
```

---

## Files Modified / Created

- **New:** `local-llm-research/RESEARCH-REPORT-2026.md`
- **Possibly updated after review:** `best-local-models-2025.md` → renamed `best-local-models-2026.md`

## Not in scope for this task

- Updating notebooks (that's a follow-on task)
- Slide updates
- Fine-tuning section research

---

## Verification

The report is complete when:
- [ ] Each section A–D has a clear decision/recommendation (not just raw notes)
- [ ] At least 3 sources cited per section
- [ ] Model table includes Ollama pull tags so students can test immediately
- [ ] Report is self-contained and readable without prior context
