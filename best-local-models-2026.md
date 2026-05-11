# Best Open-Source LLMs for Local Deployment (2026 Edition)

*Updated May 2026 — Covers models runnable on consumer hardware up to 48GB VRAM*

---

## Course Default: Gemma 4

**Gemma 4** (Google DeepMind, April 2026) is the primary model for this course. One family covers every student regardless of hardware, is multimodal by default, and carries a clean Apache 2.0 license with no usage restrictions.

| Variant | VRAM / RAM | Ollama Tag | Use When |
|---------|-----------|------------|----------|
| `gemma4:e2b` | CPU, ≤8GB RAM | `gemma4:e2b` | Very constrained hardware |
| `gemma4:e4b` | CPU, 8–16GB RAM | `gemma4:e4b` | No GPU available |
| `gemma4:26b` | 8GB VRAM | `gemma4:26b` | Most students — fits on any gaming GPU |
| `gemma4:31b` | 20GB VRAM | `gemma4:31b` | Prosumer GPUs, best quality |

- **Multimodal** — image and audio input across all sizes, no extra model needed
- **Apache 2.0** — no MAU caps, no EU geographic restrictions, safe for commercial products
- **#3 on Chatbot Arena** among all open-weight models as of May 2026
- **26B (MoE)** activates only 3.8B parameters per token — fits 8GB VRAM at Q4 quantization

```bash
ollama pull gemma4:e4b    # CPU-only
ollama pull gemma4:26b    # 8GB VRAM (recommended for most students)
ollama pull gemma4:31b    # 20GB VRAM
```

---

## Model Tiers by Hardware

### Tier 1 — CPU Only (8–16GB RAM)

**Start here:** `ollama pull qwen3:4b` (general) or `ollama pull phi4-mini` (reasoning/math)

| Model | Size | License | Ollama Tag | Strength | Notes |
|-------|------|---------|------------|----------|-------|
| **Qwen3 4B** ★ | 4B | Apache 2.0 | `qwen3:4b` | General, multilingual | 2.5GB disk; hybrid thinking/non-thinking mode; 100+ languages |
| **Phi-4 Mini** ★ | 3.8B | MIT | `phi4-mini` | Reasoning, math | MMLU 68.5%; 128K context; ~20–30 tok/s on CPU |
| Gemma 4 E4B | ~4.5B active (8B MoE) | Apache 2.0 | `gemma4:e4b` | Multimodal (image + audio) | 9.6GB disk; only CPU option with native multimodal |
| Gemma 4 E2B | ~2.3B active (5.1B MoE) | Apache 2.0 | `gemma4:e2b` | Ultra-lightweight | 7.2GB disk; best for ≤8GB RAM systems |
| Qwen3 1.7B | 1.7B | Apache 2.0 | `qwen3:1.7b` | Minimal footprint | 1.4GB disk; Raspberry Pi / embedded |
| DeepSeek-R1 7B (distill) | 7B | MIT | `deepseek-r1:7b` | Chain-of-thought reasoning | 4.7GB disk; distilled from 671B; strong math; slow on CPU |

**Picking a model at Tier 1:**
- Default general use → **Qwen3 4B**: smallest footprint, multilingual, hybrid thinking mode
- STEM, math, or structured reasoning → **Phi-4 Mini**: best reasoning at this size class
- Need image or audio input on CPU → **Gemma 4 E4B**: only option with native multimodal here

---

### Tier 2 — Consumer GPU (6–16GB VRAM)

**Start here:** `ollama pull phi4` (if 10–16GB VRAM) or `ollama pull qwen3:8b` (if 8GB VRAM)

| Model | Size | License | Ollama Tag | Strength | Notes |
|-------|------|---------|------------|----------|-------|
| **Phi-4 14B** ★ | 14B dense | MIT | `phi4` | Reasoning, STEM | 9.1GB disk; MMLU ~80%; matches Llama 3.3 70B on reasoning at 5× smaller |
| **Qwen3 8B** ★ | 8B | Apache 2.0 | `qwen3:8b` | Coding, multilingual | 5.2GB disk; fits 8GB VRAM; hybrid thinking mode; tool calling |
| **Gemma 4 26B (MoE)** ★ | 26B total / 3.8B active | Apache 2.0 | `gemma4:26b` | General, multimodal | 18GB disk; fits 8GB VRAM at Q4; 256K context; #3 Chatbot Arena |
| Qwen3 14B | 14B | Apache 2.0 | `qwen3:14b` | Long context, coding | 9.3GB disk; solid all-rounder |
| DeepSeek-R1 14B (distill) | 14B | MIT | `deepseek-r1:14b` | Reasoning, math | 9.0GB disk; chain-of-thought; fits 12GB VRAM |
| Phi-4 Mini Reasoning | 3.8B | MIT | `phi4-mini-reasoning:3.8b` | Math specialist | MATH-500: 94.6%; ideal for STEM tutoring on 6GB VRAM |
| Mistral Small 3.2 | 24B dense | Apache 2.0 | `mistral-small3.2:24b` | Multilingual, vision | 128K context; text + image; 1.9M Ollama pulls; fits 16GB VRAM at Q4 |
| LFM2 (Liquid AI) | 24B total / 2B active | Apache 2.0 | `lfm2` | Fast inference | MoE; 2B active → very fast despite 24B total; 1.1M Ollama pulls |

**Picking a model at Tier 2:**
- Best overall quality on 10–16GB VRAM → **Phi-4 14B**: punches far above its weight
- Only have 8GB VRAM → **Qwen3 8B**: fast, capable, best fit for that constraint
- Want best quality + multimodal on 8GB VRAM → **Gemma 4 26B (MoE)**: MoE architecture makes it fit

---

### Tier 3 — Prosumer GPU (20–24GB VRAM)

**Start here:** `ollama pull qwen3.6:27b` (coding/agentic) or `ollama pull gemma4:31b` (general + multimodal)

| Model | Size | License | Ollama Tag | Strength | Notes |
|-------|------|---------|------------|----------|-------|
| **Qwen3.6 27B** ★ | 27B dense | Apache 2.0 | `qwen3.6:27b` | Coding, agentic | Artificial Analysis score 46; SWE-bench Verified 77.2%; vision; 256K context |
| **Gemma 4 31B** ★ | 30.7B dense | Apache 2.0 | `gemma4:31b` | General, multimodal | AA score 39; MMLU-Pro 85.2%; AIME 89.2%; 20GB disk at Q4 |
| **DeepSeek-R1 32B (distill)** ★ | 32B | MIT | `deepseek-r1:32b` | Math, reasoning | Best reasoning model fitting 24GB VRAM; 20GB disk |
| Qwen3 32B | 32B | Apache 2.0 | `qwen3:32b` | General, multilingual | 20GB disk; hybrid thinking mode |
| Qwen3 30B (MoE) | 30B total / 3B active | Apache 2.0 | `qwen3:30b` | Fast inference | 19GB disk; 3B active → very fast for quality level; 256K context |
| Qwen3-Coder-Next | 80B total / 3B active MoE | Apache 2.0 | `qwen3-coder-next` | Code generation | 1.3M Ollama pulls; 3B active → fast despite 80B total |

**Picking a model at Tier 3:**
- Coding, agents, tool use → **Qwen3.6 27B**: #8 on Artificial Analysis, best SWE-bench at this tier
- General + multimodal → **Gemma 4 31B**: best multimodal quality that fits 24GB VRAM
- Pure reasoning / math / science → **DeepSeek-R1 32B (distill)**: strongest chain-of-thought at this tier

---

### Tier 4 — Multi-GPU / Cloud (48GB+ VRAM)

Most of these require multi-GPU infrastructure or cloud-routed access. Self-hostable options are flagged.

**Best self-hostable:** `ollama pull deepseek-r1:70b` (43GB, MIT, single A100 80GB)
**Best cloud-access:** `ollama pull kimi-k2.6` (cloud-routed, #1 on Artificial Analysis)

| Model | AA Score | Size | License | Ollama Tag | Self-hostable? | Strength |
|-------|----------|------|---------|------------|----------------|---------|
| **Kimi K2.6** ★ (Moonshot AI) | 54 | 1T total / 32B active | Modified MIT | `kimi-k2.6` (cloud) | No | SWE-bench 80.2%; AIME 96.4%; agentic coding |
| DeepSeek V4 Pro | 52 | 1.6T total / 49B active | MIT | `deepseek-v4-pro` (cloud) | Yes (8× H200) | SWE-bench 80.6%; MMLU-Pro 87.5% |
| GLM-5.1 (Z.AI) | 51 | 754B MoE | MIT | `glm-5.1` (cloud) | Yes (massive infra) | #1 open model on SWE-bench Pro |
| Qwen3.5 397B (MoE) | 45 | 397B total / 17B active | Apache 2.0 | `qwen3.5:397b` (cloud) | Yes (multi-GPU) | Frontier reasoning; AIME competitive with o3-mini |
| Qwen3.5 122B (MoE) | 42 | 122B total / 10B active | Apache 2.0 | `qwen3.5:122b` | Yes (2× A100 80GB) | Strong coding + reasoning; good VRAM efficiency |
| **DeepSeek-R1 70B (distill)** ★ | — | 70B | MIT | `deepseek-r1:70b` | **Yes (43GB, 1× A100 80GB)** | MMLU 90.8%; best self-hostable reasoning model |
| **Llama 3.3 70B** ★ | — | 70B dense | Llama 3.3 Community | `llama3.3:70b` | **Yes (43GB)** | MMLU 86%; strong coding; 3.8M Ollama pulls |
| Llama 4 Scout | — | 109B total / 17B active | Llama 4 Community | `llama4:16x17b` | Yes (67GB) | 10M context; multimodal; EU restrictions apply |

---

## Model Family Reference

### Gemma 4 (Google, April 2026)
Apache 2.0. Four variants: E2B, E4B, 26B MoE, 31B dense. Native multimodal (images, video, audio) across all sizes — a major leap from Gemma 3's text-only smaller models. The 26B MoE activates only 3.8B parameters per token, fitting consumer GPUs. The 31B dense ranks #3 among all open models on Chatbot Arena, ahead of Llama 4 Maverick on math and coding.

### Qwen 3 / 3.5 / 3.6 (Alibaba, 2025–2026)
Apache 2.0. Qwen3 launched April 2025 with 8 dense and MoE sizes (0.6B–235B) introducing a **hybrid thinking/non-thinking mode** — toggle with a system prompt. Qwen3.5 expanded multimodal capabilities and added larger MoE variants up to 397B. Qwen3.6-27B (April 2026) is a 27B dense model hitting 77.2% SWE-bench Verified, outperforming models many times its size on coding.

### DeepSeek R1 / V4 (DeepSeek, 2025–2026)
DeepSeek-R1 (January 2025, MIT) is the reference reasoning model. All distilled variants (7B, 14B, 32B, 70B) are MIT-licensed. DeepSeek V4 Pro (April 2026, MIT) scales to 1.6T parameters with 49B active, reaching 80.6% SWE-bench Verified and topping Artificial Analysis rankings.

### Phi-4 (Microsoft, 2025)
MIT license. Phi-4 14B achieves MMLU 80.4% — competitive with models 5× its size. Phi-4 Mini (3.8B) brings strong reasoning to sub-4GB disk. Phi-4 Mini Reasoning (April 2025) is a math specialist scoring 94.6% on MATH-500. No Phi-5 as of May 2026.

### Llama 3.3 / 4 (Meta, 2024–2026)
Llama 3.3 70B (late 2024) remains competitive on coding benchmarks. Llama 4 Scout and Maverick (April 2025) are multimodal MoE models with 17B active parameters and context windows up to 10M tokens. **License note:** restricts EU-domiciled users and companies with 700M+ MAU. Llama 4 Behemoth (~2T parameters) previewed but weights unreleased as of May 2026.

### Mistral (2025–2026)
Mistral Small 3.2 (24B, Apache 2.0, `mistral-small3.2:24b`) is the current small-tier model with vision. Magistral (24B, Apache 2.0, `magistral`) is the thinking/reasoning variant. Mistral Medium 3.5 (April 2026, 128B dense) is the flagship self-hostable model with a built-in coding agent at 77.6% SWE-bench Verified.

---

## Quick Start

### Install Ollama

```bash
curl -fsSL https://ollama.com/install.sh | sh
```

### Course Default (Gemma 4)

```python
import ollama

response = ollama.chat(
    model='gemma4:26b',
    messages=[
        {'role': 'user', 'content': 'Explain the difference between RAG and fine-tuning.'}
    ]
)
print(response['message']['content'])
```

### Gemma 4 Multimodal (Image Input)

```python
import ollama
import base64

with open('image.jpg', 'rb') as f:
    image_data = base64.b64encode(f.read()).decode()

response = ollama.chat(
    model='gemma4:26b',
    messages=[
        {
            'role': 'user',
            'content': 'Describe what you see in this image.',
            'images': [image_data]
        }
    ]
)
print(response['message']['content'])
```

### Qwen3 with Thinking Mode

```python
import ollama

response = ollama.chat(
    model='qwen3:8b',
    messages=[
        {'role': 'system', 'content': 'You are a helpful assistant. /think'},
        {'role': 'user', 'content': 'Write a Python function to find all prime numbers up to N using the Sieve of Eratosthenes.'}
    ]
)
print(response['message']['content'])
```

### OpenAI-Compatible Endpoint (Drop-in Replacement)

```python
from openai import OpenAI

client = OpenAI(base_url='http://localhost:11434/v1', api_key='ollama')

response = client.chat.completions.create(
    model='gemma4:26b',
    messages=[
        {'role': 'user', 'content': 'What is retrieval-augmented generation?'}
    ]
)
print(response.choices[0].message.content)
```

---

## Deployment Tools

### Ollama — Recommended for most users
Always-on OpenAI-compatible endpoint at `localhost:11434/v1`. Default choice for the course.

```bash
ollama serve                    # start server (auto-starts on install)
ollama pull gemma4:26b          # download model
ollama list                     # list downloaded models
ollama run gemma4:26b           # interactive chat in terminal
```

### LM Studio — Best for beginners and model discovery
Point-and-click GUI with a built-in Hugging Face model browser. Best model discovery experience, especially on Apple Silicon. API server must be started manually. 3M+ cumulative downloads.

### Open WebUI — Chat interface for Ollama
Browser-based ChatGPT-style UI that connects to any Ollama or OpenAI-compatible backend. Includes RAG, multi-user auth, voice I/O, and a plugin system. Install after Ollama:

```bash
docker run -d -p 3000:8080 \
  --add-host=host.docker.internal:host-gateway \
  -v open-webui:/app/backend/data \
  --name open-webui \
  ghcr.io/open-webui/open-webui:main
```

### llama-cpp-python — Advanced / in-process inference

For loading any GGUF directly from Hugging Face, in-process Python inference with no daemon, or AMD GPU with Vulkan support.

```bash
pip install llama-cpp-python                  # CPU only
CMAKE_ARGS="-DGGML_CUDA=on" pip install llama-cpp-python  # CUDA GPU
```

```python
from llama_cpp import Llama

llm = Llama.from_pretrained(
    repo_id='bartowski/gemma-3-27b-it-GGUF',
    filename='*Q4_K_M.gguf',
    n_gpu_layers=-1
)

output = llm.create_chat_completion(messages=[
    {'role': 'user', 'content': 'Explain quantization in LLMs.'}
])
print(output['choices'][0]['message']['content'])
```

### vLLM — Production serving (concurrent users)
Required when serving 5+ simultaneous users. Linux + NVIDIA GPU only. Delivers 2,300+ tok/s on H100. Not needed for local development — graduate to this when moving to production.

```bash
pip install vllm
python -m vllm.entrypoints.openai.api_server \
  --model google/gemma-3-27b-it \
  --max-model-len 32768
```

---

## Model Selection by Use Case

| Use Case | Best Pick | Alternative |
|----------|-----------|-------------|
| Course default / general | `gemma4:26b` (8GB VRAM) or `gemma4:e4b` (CPU) | `qwen3:8b` |
| Coding + agentic workflows | `qwen3.6:27b` | `qwen3:8b` |
| Math / science / reasoning | `deepseek-r1:32b` | `phi4-mini` (CPU) |
| Multimodal (image/audio) | `gemma4:26b` | `gemma4:e4b` (CPU) |
| Multilingual | `qwen3:4b` or `qwen3:8b` | `gemma4:26b` |
| Minimal hardware (≤8GB RAM) | `qwen3:4b` | `gemma4:e2b` |
| Best quality, any hardware | `gemma4:31b` (24GB VRAM) | `deepseek-r1:70b` (A100) |

---

## Hardware Configuration Guide

**CPU only / integrated graphics (8–16GB RAM)**
→ `gemma4:e4b` or `qwen3:4b`

**Entry gaming GPU (RTX 4060 / 6–8GB VRAM)**
→ `qwen3:8b` or `gemma4:26b` (Q4 quant)

**Mid-range GPU (RTX 4070 / 10–12GB VRAM)**
→ `phi4` (14B) or `qwen3:14b`

**High-end GPU (RTX 4090 / 24GB VRAM)**
→ `gemma4:31b` or `qwen3.6:27b` or `deepseek-r1:32b`

**Prosumer / workstation (48GB+ VRAM)**
→ `deepseek-r1:70b` or `llama3.3:70b`

---

## Keeping Updated

- **Chatbot Arena (overall quality):** https://huggingface.co/spaces/lmsys/chatbot-arena-leaderboard
- **Artificial Analysis (open-source rankings):** https://artificialanalysis.ai
- **Ollama model library:** https://ollama.com/library
- **Hugging Face trending:** https://huggingface.co/models?sort=trending
- **Community:** r/LocalLLaMA (636k+ members)
