# Final architecture-document review

Run this review after drafting.

## Deliverable

- The requested Markdown report exists at the resolved path.
- The report is complete and understandable without chat history.
- Research notes or chat summaries have not replaced the report.
- Local frontmatter, image paths and repository conventions are preserved.

## Scope

- Exact chip generation and research date are clear.
- Availability is supported by ordering, delivery, general-availability or named-deployment evidence.
- Shipping, announced and legacy products are separated.
- Chip, board, system and software claims are not mixed.
- Data from another generation is explicitly labeled.
- Older-generation mechanisms have continuity evidence; quantitative specifications are not inherited.

## Mechanism

- Compute, storage, layout and communication hardware are each identified.
- Execution explains controller, mapping, launch, progress, synchronization and stall behavior.
- Hardware and software responsibilities are explicit.
- The end-to-end example agrees with the component descriptions.
- Dynamicity explains both support mechanism and residual cost.

## Quantitative data

- Physical, enabled and software-visible counts are distinguished.
- Bandwidth states direction, aggregation level and byte/bit units.
- Peak, measured and derived values are labeled.
- Precision names, multiplier mode and accumulation precision are not conflated.
- Unknown die area, PPA or latency remains unknown.

## Evidence

- Every nontrivial fact maps to a source.
- Official documentation or code supports implementation claims.
- Independent sources are labeled and used only where needed.
- Open software is not described as open hardware.
- Operator support is not described as proven efficiency.
- No architectural drawing is presented as physical layout without evidence.

## Comparison and judgment

- GPU comparison uses the same system level and metric definition.
- The GPU comparator and comparison date are explicit.
- Each difference states the resulting tradeoff or moved complexity.
- Advantages have comparable measurements or qualified wording.
- Missing third-party and deployment evidence is stated.
- Current-product conclusions do not rely on obsolete generations.

## Writing

- The causal order is scope → hardware → execution → dynamics → scaling → software → comparison → judgment.
- Vendor-specific concepts are defined once.
- Repetition, marketing language and speculative implementation details are removed.
- “不是……而是……” rhetoric is absent.
- One sentence is not expanded into a paragraph without added information.
- Tables remain readable and use consistent terminology.
- Images are existing sourced diagrams unless generation was explicitly authorized.
