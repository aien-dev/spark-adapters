# spark-adapters

Universal third-party model provider adapters and knowledge distillation oracle for Sovereign SparkOS on NVIDIA DGX Grace Blackwell (GB10).

## Capabilities

1. **Provider Adapters**: Dynamic SSE streaming and unary completions for OpenAI, Anthropic (Claude 3.7 hybrid thinking), OpenRouter, Google Gemini, Groq (LPU sub-100ms), DeepSeek, Together, Mistral, and local Modular MAX / Ollama seats.
2. **Teacher Knowledge Distillation**: Dual rollout evaluation pairing external teacher frontier models against resident open-weight models (`atlas-lightning-omni`).
3. **Sovereign Verification Harness**: Built-in verification checking syntax, balanced code delimiters, unslop compliance (zero em dashes, zero AI tropes), and zero secret leaks.
4. **Dataset Synthesis**: Generates standardized SFT (ChatML) and DPO / ORPO preference datasets persisted directly to disk.
5. **Cortex Memory Integration**: Ingests high-scoring verified teacher insights directly into Spark Cortex (`http://127.0.0.1:18080`, space `atlas-memory`).
6. **Zero Disk Secrets**: Integrates dynamically with hardware TPM vault (`atlas-vault get`) with zero plaintext `.env` files on disk.

## CLI Usage

```bash
# Run distillation against teacher model
spark-distill   --teacher anthropic/claude-3-7-sonnet   --student atlas-lightning-omni   --prompt "Implement a lock-free ring buffer in Rust"   --task-type code   --verify compiler   --commit-cortex
```

## Architecture

- `spark_adapters::models`: Common message, rollout, task, and distillation schema.
- `spark_adapters::router`: Route resolution, secret resolution, and model catalog.
- `spark_adapters::verifier`: Unslop and code syntax validation.
- `spark_adapters::distill`: Automated distillation pipeline.
- `spark_adapters::vault`: Hardware TPM key resolution.

## License and Governance

Licensed under the **Sovereign Resource Commons License 1.0 (SRCL-1.0)** (Apache-2.0 WITH LLVM-exception).
Architected by AIEN (Autonomous Cognitive Architecture operating on the Atlas Framework) and sovereign ecosystem contributors. See [LICENSE](LICENSE) for full legal terms and copyright notices.

All downstream distributions, derivative works, and commercial deployments are governed exclusively by the terms of [LICENSE](LICENSE). [CONSTITUTION.md](CONSTITUTION.md) defines the internal architectural charter and development doctrine for upstream engineering.
