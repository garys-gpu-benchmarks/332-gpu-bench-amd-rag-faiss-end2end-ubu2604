# Results: 332 RAG Pipeline Sweep

**Main goal:** Measure end-to-end RAG retrieval plus generation performance  
**Tools:** Run scripts/gpu-bench-rag-faiss-end2end.py for squad_v2 retrieval, BGE embeddings, FAISS search, and Mistral generation

Reference results measured by the maintainer on the system shown in each section (generator TEMPLATE_00_148 · recorded 2026-11-19). Your own runs write `results/RESULTS_ACTUAL.md` in the same format.

> Smoke runs use deliberately small sizes. They check that the workload installs and runs end to end; their numbers are not performance results. Baseline and extended are.

<!-- profile:smoke -->
## smoke

- **System:** 1× AMD Instinct MI300X VF (196288 MB) · INTEL(R) XEON(R) PLATINUM 8568Y+ · Ubuntu 26.04.1 LTS · kernel 7.0.0-43-generic · driver 7.1.9.31600000
- **Run:** 2026-11-19T16:28:23Z · status **PASS** (exit 0)
- **Time (mm:ss):** setup 03:09 · benchmark 00:16 · whole run 03:34
- **Source:** run 332_20261119_162823
- **Command:** `bash run_benchmark.sh --smoke --chunk-size 64 --chunk-overlap 32 --corpus-dataset rajpurkar/squad_v2 --top-k 5 --embedding-model BAAI/bge-small-en-v1.5 --query-length 32 --batch-size 2 --llm-model mistralai/Mistral-7B-v0.3 --query-count 2 --reranker-model BAAI/bge-reranker-base`

| # | Metric | Result |
|---|---|---|
| 1 | E2E mean over queries, ms (end_to_end_query_latency_retrieval_generation_ms) | 305.09555600019667 |
| 2 | Generation TTFT, ms (generation_phase_time_to_first_token_ms) | 43.327211999894644 |
| 3 | CPU FAISS retrieval latency, ms (retrieval_latency_vector_search_ms) | 0.09579300058248919 |
| 4 | Gen throughput, tok/s (generation_throughput_output_tokens_s) | 55.21802140355689 |
| 5 | Embedding throughput, chunks/s (embedding_throughput_chunks_s) | 76.61324370461053 |
| 6 | FAISS index vectors (faiss_index_ntotal) | 217.0 |
<!-- /profile:smoke -->
