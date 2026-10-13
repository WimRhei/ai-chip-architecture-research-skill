# Architecture report writing contract

## Organizing principle

Lead with the architectural conclusion and explain the shortest causal chain that supports it. A complete report covers the relevant mechanisms, not a fixed number of sections. Combine or omit topics that add no evidence or architectural consequence; do not pad undocumented areas.

Use the following sequence as a default. For a CPU or system question, introduce the workload and baseline differences before component details when that makes the argument clearer.

## 1. Scope, bottleneck and central bet

State the chip/generation, product status and research date. Define the chip and system boundaries.

Explain the target workload, limiting resource or dependency, and what the design assumes about regularity, locality, concurrency or reuse. Give the central architectural choice in one sentence, followed by its main cost. Introduce vendor terms only when needed for the mechanism.

## 2. Key specifications and hardware

Use a compact specification table with relevant disclosed values: process/area, compute resources, numerical formats, SRAM, external memory, interconnect and power. Label the unit of scope; distinguish physical, enabled and software-visible resources. Consolidate consequential unknowns once.

Describe the actual paths:

- **Compute:** matrix/vector/scalar units, hardware operation granularity versus software tile, and precision/conversion responsibilities. Separate control processors from compute datapaths.
- **Storage:** registers, SRAM/cache and external memory; who manages placement; tensor/tile/page/shard layout; local versus remote access, copying and coherence.
- **Communication:** endpoints, topology and transfer mechanisms; address generation, routing, multicast/collectives and completion signaling. Separate protocol, physical link and connector.

Define software-managed SRAM as such even if the vendor calls it “L1”. Unified addressing or coherence does not erase separate memory pools, access distance or locality costs. A logical block diagram does not establish physical layout or area proportions.

## 3. Execution: placement, progress and control

Explain the path from framework/compiler to executable, launch and completion. Define vendor Program, Kernel or configuration terms once and state what users can actually program.

Separate three decisions:

| Decision | Questions |
|---|---|
| Placement | Who assigns computation, data and communication paths? At compile time, launch or runtime? |
| Progress | What permits execution: a scheduled cycle, ready operands, buffer space, an event or a barrier? |
| Adaptation | Can execution change addresses/loop counts, select ready instructions, or reassign tasks/resources? |

A static spatial mapping can still advance dynamically. A data-dependent address does not imply task rescheduling. Specify the affected level instead of calling the whole chip “static” or “dynamic”.

Use one sourced operation or workload phase to connect **initial data → movement/layout → compute → synchronization → output**. Name the controlling component and release event at each boundary. Explain what stalls and how backpressure propagates when a stage is slower. Mark an illustrative mapping as an example if the vendor has not documented that exact path.

For latency hiding, identify the independent work that overlaps and the wait it covers. Threads, OoO, prefetch and software pipelines cannot break true dependencies. Distinguish shortening the critical path from filling otherwise idle time; fewer copies, launches or barriers require an explicit before/after path.

## 4. Dynamics, numerical formats and scaling

Expand these only where they change the conclusion:

- **Dynamics/sparsity:** trace an address, shape, mask or routing decision to the executing mechanism. State remaining costs: padding, gather/scatter, reordering, synchronization and load imbalance. Distinguish operator support, hardware skipping and measured benefit.
- **Formats:** distinguish storage, input, multiplier mode and accumulation. Explain unusual bit/byte organization with a small example when necessary; software tile width is not hardware multiplier width.
- **Scaling:** distinguish die, board, node and rack links. Connect sharding and collectives to topology, bandwidth, latency and memory semantics. Identify which communication becomes limiting and why; link bandwidth alone does not establish scaling efficiency.

## 5. Baseline differences and judgment

Choose a named baseline from the same product period and comparable workload/system level. Label a present-day comparison to older hardware explicitly.

Use a short table: **dimension | baseline mechanism | target change | consequence/cost**. Keep only differences that explain the design. Distinguish existing capabilities, changed resource proportions and custom mechanisms. For each major choice, explain where complexity moved and what happens when its workload assumption fails.

Conclude with the supported benefit, limiting cost and conditions of applicability. Separate architecture effects from compiler/kernel improvements, reused hardware standards from software ecosystems, and vendor results from independent evidence. Do not declare a winner without comparable measurements. Keep research opportunities or user hypotheses separate from the architecture judgment.

## Quantitative and source rules

- Bandwidth: specify per-link/aggregate, direction and payload/signaling where known; use `B/s` for data bandwidth. Do not invent an undisclosed convention.
- Compute: distinguish MAC/FLOP, precision, sparsity and peak/measured throughput. For derived values, show inputs and assumptions; multiple feasible configurations do not reveal the actual microarchitecture.
- Benchmarks: retain the model/workload, batch/concurrency, sequence lengths, precision, system size and metric definition needed to interpret the result, where disclosed. Distinguish token latency, request latency, throughput and power efficiency; local gains do not establish whole-system gains.
- Sources: keep a claim-to-source map during research, including status and generation/system scope. Group final references by topic when useful. Patents, third-party reconstructions and user annotations must retain their evidence status.

## Concise writing

Use concrete verbs and define each concept once. Prefer a table or short data path when it removes repeated prose. Keep vendor-specific mechanisms and causal costs; omit textbook explanations, exhaustive glossaries, promotional adjectives and “不是……而是……” rhetoric. Put each fact in one main location. A short report must still explain how the chip executes work.
