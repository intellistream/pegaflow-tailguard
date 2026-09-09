# PegaFlow TailGuard

**Proposal; no implementation or measured results.**

Pooling host memory across prefill and decode nodes can retain more KV state, yet remote hits compete with refill and migration for shared transfer resources. TailGuard studies whether object placement and request-aware transfer budgets can reduce exposed remote-read tails under a fixed total memory budget. It is a policy plugin for PegaFlow, whose storage and transfer engine remains an independent dependency. The proposed controller couples placement, demand-read admission and background transfer pacing, while preserving object identity and lifecycle correctness. Strong controls include tuned static placement and transfer budgets, PegaFlow without the policy, and supported disaggregated-cache systems with advisory prefetch. The first milestone must establish a repeatable capacity-versus-tail conflict before policy implementation. This repository contains a research proposal only: no policy implementation, RDMA trace, NPU validation or performance result is reported.

## Ownership and boundary

Academic co-owners: Chen Yanbo (`cybber695`) and Chen Zijia (`mynameisczj`). PegaFlow owns the storage/transfer engine and existing integration; TailGuard owns the proposed placement/admission/pacing policy. They may support one paper family without merging repositories or claim ledgers. Memory-Aware Sparse KV owns exact native-indexer prefetch; Adaptive Quantized KV owns quantized execution/precision; neither is replaced here.

See [the seven-question contract](docs/research-contract.md), [paper](paper/main.tex), [first necessity gate](docs/necessity-gate.md), and [dependency policy](docs/dependencies.md). This extends the plugin proposed in [PegaFlow issue #23](https://github.com/vLLM-HUST/pegaflow-hust/issues/23); it does not claim that the proposal is implemented.
