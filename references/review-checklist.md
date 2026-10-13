# Architecture report review

Check the final report against these questions; correct gaps without adding a separate validation artifact.

## Scope and evidence

- Is the requested report/edit complete, standalone and consistent with local frontmatter and image paths?
- Are generation, product status, date and chip/system scope clear? Are inherited mechanisms supported and labeled?
- Does every nontrivial fact map to a source for the studied implementation? Are calculations, reconstructions and user hypotheses distinct from confirmed hardware?
- Are consequential unknowns stated once, without guesses or repeated caveats?

## Architectural explanation

- Does the report connect workload bottleneck → design choice → benefit → cost/failure condition?
- Are compute granularity, storage/layout and communication paths concrete?
- Are placement, execution progress and runtime adaptation distinguished, with hardware/compiler/runtime/programmer responsibilities?
- Does one consistent execution path identify data location, controlling components, synchronization and stalls?
- Does latency hiding name independent work while preserving true dependencies?
- Where relevant, are dynamicity/sparsity costs, numerical paths and multi-chip communication limits explained?

## Comparison and quantities

- Is the baseline appropriate for an accelerator, CPU or system, with comparable scope and metric definitions?
- Does each claimed difference identify a changed mechanism or resource allocation and its consequence?
- Are bandwidth direction/aggregation, MAC/FLOP, precision and peak/measured/derived values clear where known?
- Are benchmark conditions sufficient to interpret results, with local software gains separated from architecture and end-to-end gains?
- Are addressing, coherence and locality kept distinct? Are logical diagrams kept distinct from physical layouts?

## Writing

- Does every section add a mechanism, evidence or decision-changing consequence?
- Are definitions, specifications and judgments maintained in one place, with no glossary padding or repeated defensive prose?
- Are diagrams sourced, with generation only when explicitly permitted?
- Are user edits/questions preserved and references placed as requested?
