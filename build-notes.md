# Build notes

Machine: Windows laptop, AMD Ryzen 7 4700U (8 cores / 8 threads), integrated Radeon graphics (not used), 8GB RAM, WSL2 with Ubuntu 26.04
llama.cpp commit: 418f905a4efe910d2a75636bbe65d48eca38790a
Model: Qwen2.5-1.5B-Instruct (Q4_K_M and Q8_0 GGUF)

## Build commands
git clone https://github.com/ggml-org/llama.cpp
cmake -B build
cmake --build build --config Release -j4

## First run
./build/bin/llama-cli -m ~/models/qwen2.5-1.5b-instruct-q4_k_m.gguf -p "Hello, who are you?" -n 50
Worked and produced output.

## Problems and fixes
- WSL installed with no Ubuntu distro. Fixed by installing Ubuntu from the Microsoft Store.
- WSL showed 4GB of my 8GB RAM. Raised the limit with a .wslconfig file.
- wget gave an auth error on the first model repo. Used Qwen's own repo instead.
- Typed .build instead of ./build, which gave "no such file or directory".

