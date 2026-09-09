# M0: establish the pooling-versus-tail conflict

No hardware run is authorized by this document. Student owners choose and freeze the model, runtime, topology, workloads and budgets before execution.

Implement later as a PegaFlow policy plugin with explicit control hooks. Keep the PegaFlow engine, RDMA transport, packing/layout operators and runtime lifecycle contract separate. A source/trace hook feasibility audit is required before a controller.

Compare decode-local cache, pooled static placement, best static priority/budget, PegaFlow without TailGuard, and compatible SYMPHONY/Mooncake controls. Match models, arrivals, completed work, total CPU/GPU memory, topology and bandwidth. Report hit/useful-residence, remote-read p99, request p99, queue waits, bytes, fairness and recomputation.

Required evidence: a matched workload where pooled capacity improves useful retention/hits while uncontrolled remote traffic reproducibly increases exposed read/request tails. Include cold/warm cache, load sweeps, fixed offered and completed work, full bytes and failure receipts. Stop if pooling adds no useful residence, shared transfers create no repeatable tail conflict, the best static policy matches the mechanism, or lower p99 comes from rejecting/defering more work. No artificial TTL increase counts as benefit.
