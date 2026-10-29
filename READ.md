# llama.cpp benchmarks

Building llama.cpp from source on Linux (WSL2, Ubuntu) and benchmarking latency, throughput and memory use.

## Setup
- Machine: Windows laptop, AMD Ryzen 7 4700U (8 cores / 8 threads), integrated Radeon graphics (not used), 8GB RAM (6GB allocated to WSL2), WSL2 with Ubuntu 26.04
- Model: Qwen2.5-1.5B-Instruct (Q4_K_M and Q8_0 GGUF)
- llama.cpp commit: 418f905a4efe910d2a75636bbe65d48eca38790a

See build-notes.md for how I built it.

## Results (CPU only, 8 threads, Ryzen 7, WSL2)

| | Q4_K_M (1.04 GiB) | Q8_0 (1.76 GiB) |
|---|---|---|
| Prompt processing, 8 threads | 179 t/s | 120 t/s |
| Generation, 4 threads | 26.5 t/s | 15.3 t/s |
| Generation, 8 threads | 27.6 t/s | 15.9 t/s |

## Findings
- Generation speed scaled with model size: Q4 was about 1.7x faster and about 1.7x smaller.
- Doubling threads barely changed generation speed, so it is likely limited by memory bandwidth.
- Prompt processing did scale with threads, so it looks compute-bound.

Raw output is in results-q4.md and results-q8.md.
