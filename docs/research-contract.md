# Seven-question research contract

## Q1

Can joint P/D host-memory placement and transfer admission reduce request p99 when remote reads compete with refill/migration, at fixed total bytes and useful completion rate?

## Q2

Long-context serving can exchange recomputation for a remote hit whose lookup, queue, DMA and materialization delay exceeds its apparent cache benefit. Such a conflict is a hypothesis until matched traces expose it.

## Q3

SYMPHONY already uses advisory prefetch and cooperative cache management; Mooncake already pools disaggregated storage. The proposed contribution must exceed tuned memory/priority/transfer controls, not claim disaggregation or advisory prefetch as new.

## Q4

Use object identity, estimated read deadline and measured queue/transfer pressure to jointly choose placement and background transfer budgets. Admit demand reads without allowing refill or migration to consume their entire service window; account for deferred and rejected work.

## Q5

Implement later as a PegaFlow policy plugin with explicit control hooks. Keep the PegaFlow engine, RDMA transport, packing/layout operators and runtime lifecycle contract separate. A source/trace hook feasibility audit is required before a controller.

## Q6

Compare decode-local cache, pooled static placement, best static priority/budget, PegaFlow without TailGuard, and compatible SYMPHONY/Mooncake controls. Match models, arrivals, completed work, total CPU/GPU memory, topology and bandwidth. Report hit/useful-residence, remote-read p99, request p99, queue waits, bytes, fairness and recomputation.

## Q7

Stop if pooling adds no useful residence, shared transfers create no repeatable tail conflict, the best static policy matches the mechanism, or lower p99 comes from rejecting/defering more work. No artificial TTL increase counts as benefit.

## Boundary

Academic co-owners: Chen Yanbo (`cybber695`) and Chen Zijia (`mynameisczj`). PegaFlow owns the storage/transfer engine and existing integration; TailGuard owns the proposed placement/admission/pacing policy. They may support one paper family without merging repositories or claim ledgers. Memory-Aware Sparse KV owns exact native-indexer prefetch; Adaptive Quantized KV owns quantized execution/precision; neither is replaced here.

## Matched ablations

Placement only, transfer-budget only, joint policy, and a future-information oracle. Separate foreground reads from background refill/migration; charge delayed jobs and policy CPU time. Quantization is fixed, not combined into the same treatment. Stop on stale/cross-request data or lifecycle violations.
