# Architecture research and writing contract

Use this as the master prompt for a company-specific AI-chip architecture document.

## Deliverable

Produce a complete standalone Markdown report in the requested file. If no file is named, create `<Company or Chip>架构.md` in the current project. Research notes and evidence maps are internal artifacts; completion requires the report itself.

In an Obsidian vault with an established wide-note convention, apply that frontmatter. Use sourced existing diagrams through relative local paths and keep their original URLs in the references. The document must stand alone without chat context.

## Objective

Research one concrete chip generation. Explain:

1. what hardware exists;
2. how software maps and executes work;
3. where data resides and how it moves;
4. which complexity is handled by hardware, compiler, runtime or programmer;
5. what workload assumptions the design makes;
6. which costs appear when those assumptions fail;
7. the essential differences from a contemporary GPU.

The reader has computer-architecture fundamentals. Explain vendor-specific concepts and non-obvious mechanisms only.

## Research boundary

- State the exact chip generation, release status and research date.
- Define availability using general availability, ordering, delivery or named deployment evidence; distinguish launch announcements and promised shipping windows.
- Distinguish die, package, board, server, rack and software stack.
- Distinguish physical resources, enabled product resources and software-visible resources.
- Keep other generations in a short lineage section or an explicit comparison.
- Inherit an older mechanism only with explicit family continuity or current-generation corroboration; label it and never inherit quantitative specifications.
- Record unavailable die area, PPA, latency or deployment evidence as unavailable.

## Causal organization

Use this order unless the architecture requires a small adjustment.

### 0. Scope and thesis

- Define the chip, generation and product studied.
- Give one sentence for the design philosophy.
- Give one sentence for the central bet.
- Define vendor-specific terms needed to read the rest.

### 1. Key specifications

Use one compact table. Include available and relevant values:

- process, die area and transistor count;
- compute-core topology and enabled count;
- matrix/vector/control resources;
- on-chip SRAM capacity and organization;
- external memory capacity and bandwidth;
- on-chip and chip-to-chip interconnect;
- supported numerical formats;
- board power only when it helps interpret the architecture.

For every bandwidth, state per-link or aggregate, per-direction or bidirectional, payload or signaling rate. Use `B/s` for data bandwidth. Distinguish MAC from FLOP and measured from peak.

### 2. Static hardware

Describe physical mechanisms before execution.

#### Compute

- Matrix, vector, scalar and special-function datapaths.
- Hardware operation granularity and software programming granularity.
- Precision, accumulation, conversion, pack/unpack and quantization ownership.
- Keep control processors out of the compute-datapath description.

#### Storage and layout

- Registers, local SRAM, shared cache and external memory actually present.
- Hardware-managed and software-managed levels.
- Tensor, tile, page, shard or vendor layout concepts.
- Local and remote access semantics; coherence and copying behavior.

#### Communication

- On-chip topology, endpoints and routing responsibility.
- Read, write, multicast, collective and synchronization mechanisms.
- Separate logical protocol, physical link and connector.
- State who chooses addresses and paths, and who transfers packets.

### 3. Dynamic execution

Explain who runs what and when.

- Define Program, graph, kernel, command queue and runtime using the vendor's actual model.
- Identify which controller receives each kernel or command stream.
- Explain mapping, launch, local progress, synchronization and completion.
- Explain latency hiding: threads, scoreboarding, events, buffering, software pipeline or static schedule.
- Use one evidence-backed end-to-end operation to connect layout, movement, computation, synchronization and output.

Always answer:

- Who decides the work?
- When is that decision made?
- Where is the data at each stage?
- What event allows the next stage to proceed?
- What stalls when one stage is slower?

### 4. Numerical formats, sparsity and runtime dynamics

- Separate storage format, input format, multiplier mode and accumulation precision.
- Explain unusual formats with one numerical or bit-level example when needed.
- State hardware boundaries first.
- Explain how software handles dynamic addresses, lengths, indices, routing and load imbalance.
- Separate operator availability from hardware skipping, measured speedup and end-to-end benefit.

### 5. Multi-chip scaling

- Separate die-to-die, board-level, node-level and rack-level links.
- Give confirmed bandwidth and topology.
- Explain sharding, collectives, synchronization, memory semantics and coherence.
- Identify scale-up bottlenecks without inferring performance from bandwidth alone.

### 6. Software stack and programmability

Show one consistent path from framework graph to executable work:

`Framework → graph IR/compiler → operator/runtime → kernel/programming layer → hardware`

Define each vendor component once. State what users can program and which layer resembles a GPU framework backend, library, runtime or kernel API. Do not equate layers merely because names sound similar.

### 7. GPU differences and design tradeoffs

Use one table with `dimension | GPU | target chip | consequence`.

State the comparator before the table. Default to a shipping GPU from the same product period and comparable system/workload level. Use a current GPU only for a clearly labeled present-day comparison. Do not mix chip, board and rack metrics.

Compare only essential differences across:

- compute granularity;
- storage and data placement;
- communication;
- execution and scheduling;
- latency hiding;
- numerical formats;
- sparsity and runtime dynamics;
- multi-chip scaling;
- software programmability;
- target workloads and system constraints.

For each difference, identify where complexity moved. Avoid declaring a winner without comparable measurements.

### 8. Reused ecosystem and system judgment

- Separate reused hardware standards from reused software ecosystems.
- Identify the vendor's genuinely custom components.
- Give a small number of evidence-bounded system judgments.
- State what remains unproven: PPA, utilization, end-to-end latency, scale, reliability, multi-tenancy or deployment maturity.

### 9. References

Group primary sources by topic. Prefer stable official documentation and source-code paths. Include independent analysis only where it adds evidence or criticism.

## Writing rules

- Lead with the conclusion, then the mechanism.
- One sentence per claim; one term per concept.
- Delete duplicated definitions, mechanisms and judgments.
- Avoid “不是……而是……” and similar rhetorical contrast.
- Avoid promotional adjectives and vague claims such as “efficient” or “scalable”.
- Define abbreviations and vendor terms at first use.
- Keep chip, board, connector, protocol, runtime and compiler layers distinct.
- Use concrete verbs: map, issue, route, wait, copy, compute and synchronize.
- Prefer a compact table when it removes repeated prose.
- Use an example only when it connects several mechanisms or resolves ambiguity.
- If a vendor calls software-managed scratchpad “L1”, define it once and then call it `SRAM`; preserve `cache` only when cache semantics exist.
- Put sources in the final reference section when the document style requires source-free prose; never lose claim-to-source traceability.
- Finish the requested file before returning a conversational summary.

## Evidence labels for internal research

Maintain a private evidence map while drafting:

| Claim | Status | Source | Scope |
|---|---|---|---|
| Exact documented fact | confirmed | primary URL/path | chip/board/system |
| Arithmetic from facts | derived | inputs and formula | stated assumptions |
| Architectural interpretation | inference | supporting facts | uncertainty |
| Comparative judgment | evaluation | comparable evidence | limits |

Only the final prose and requested references belong in the user document.
