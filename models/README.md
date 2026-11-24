# Local uncensored models for ARTEX

Weights stay on disk under `/home/edslawn/models`; only profiles are committed.

| Ollama name | GGUF | Modelfile |
| --- | --- | --- |
| `r1-distill-7b-uncensored` | `DeepSeek-R1-Distill-Qwen-7B-Uncensored.Q4_K_M.gguf` | `models/r1-distill-7b-uncensored/Modelfile` |
| `dolphin-mixtral-8x7b` | `dolphin-2.5-mixtral-8x7b.Q4_K_M.gguf` | `models/dolphin-mixtral-8x7b/Modelfile` |
| `dolphin-llama3-8b` | `dolphin-2.9-llama3-8b-Q4_K_M.gguf` | `models/dolphin-llama3-8b/Modelfile` |
| `deepseek-coder-v2-lite-abliterated` | `DeepSeek-Coder-V2-Lite-Instruct-abliterated.Q4_K_M.gguf` | `models/deepseek-coder-v2-lite-abliterated/Modelfile` |

Create them in Ollama:

```sh
ollama serve &
ollama create r1-distill-7b-uncensored -f models/r1-distill-7b-uncensored/Modelfile
ollama create dolphin-mixtral-8x7b -f models/dolphin-mixtral-8x7b/Modelfile
ollama create dolphin-llama3-8b -f models/dolphin-llama3-8b/Modelfile
ollama create deepseek-coder-v2-lite-abliterated -f models/deepseek-coder-v2-lite-abliterated/Modelfile
```

ARTEX provider: **Ollama**, base URL `http://127.0.0.1:11434/v1`; refresh the model catalog and select the names above.

Single-default environment override:

```sh
ARTEX_LLM_PROVIDER=ollama
ARTEX_LLM_BASE_URL=http://127.0.0.1:11434/v1
ARTEX_LLM_MODEL=r1-distill-7b-uncensored
```
