# llama.cpp benchmarks

Building llama.cpp from source on Linux (WSL2, Ubuntu) and benchmarking latency, throughput and memory use.

## Setup
- Machine: Windows laptop, AMD Ryzen 7 4700U (8 cores / 8 threads), integrated Radeon graphics (not used), 8GB RAM (6GB allocated to WSL2), WSL2 with Ubuntu 26.04
- Model: Qwen2.5-1.5B-Instruct (Q4_K_M and Q8_0 GGUF)
- llama.cpp commit: 418f905a4efe910d2a75636bbe65d48eca38790a

See build-notes.md for how I built it.
