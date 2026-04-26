# Qwen3-0.6B

## Links

**Huggingface:** https://huggingface.co/Qwen/Qwen3-0.6B

**Blog:** https://qwenlm.github.io/blog/qwen3/

## Hardware

* vCPU 8
* RAM 32 GB
* HDD 240 GB
* NVidia RTX 4090 (24 GB HBM, bandwidth 1 TB/s, FP16 @ 82 TFLOPS)

## Inference performance

See `benchmark_vllm.sh` for settings. The same docker has been used as for Qwen3-0.6B

| Input len | Output len | Max num seqs (batch size) | Number of prompts | Throughput (RPS) | Throughput (total tokens per sec) | Output throughput (output tokens per sec)
|-|-|-|-|-|-|-|
| 512 | 128 | 4 | 64 | 10.88 | 6961 | 1392 |
| 2048 | 512 | 4 | 64 | 2.20 | 5645 | 1129 |
| 16000 | 1024 | 4 | 64 | 0.34 | 5734 | 345 |

**Issues**
- Default context length (40960) does not fit with default GPU memory utilization so I halved it to 20480. This leads to 1.15x concurrency so that's the limit

