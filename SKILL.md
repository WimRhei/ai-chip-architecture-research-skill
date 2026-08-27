---
name: ai-chip-architecture-research
description: Create or rewrite a complete Markdown report for a concrete AI accelerator architecture, covering hardware, execution, GPU differences and evidence-bounded tradeoffs. Use for company-chip surveys, generation-specific architecture reports and accelerator analysis; do not use for paper-only reading notes or generic market summaries.
---

# AI Chip Architecture Research

Explain why a concrete chip is designed this way, how work and data actually move through it, and what the design gives up. Preserve technical depth while minimizing wording.

## Establish scope

Before research, identify:

- company, chip family, exact generation and current product status;
- chip, board, multi-chip system and software layers in scope;
- requested output path or existing document, when supplied.

If only a company is named, select the latest chip with both adequate official documentation and confirmed availability. Accept general availability, direct ordering, customer delivery or named deployment as availability evidence; a launch announcement or future shipping window is insufficient. State ambiguous status and cover a newer announced generation separately.

Never merge generations silently. Reuse an older-generation mechanism only when current documentation confirms continuity or the vendor explicitly describes it as family-wide; label the inherited evidence and keep it out of generation-specific specifications.

## Evidence discipline

Use sources in this order:

1. official architecture manuals, specifications and source code;
2. official product pages, presentations and engineering articles;
3. patents and papers from the vendor;
4. independent technical analysis for gaps and criticism.

Trace every nontrivial fact to a source. Separate confirmed facts, derived calculations and evaluation. Label architectural inference explicitly. Omit unsupported implementation guesses and marketing comparisons. Verify current generations and product status live when practical.

Open software does not prove open hardware. A supported operator does not prove efficient execution. Peak throughput does not prove end-to-end performance.

## Default deliverable

When the user names a company or chip for research, create a complete standalone Markdown architecture report. Do not stop at a memo, outline, evidence map or chat summary unless the user explicitly requests that format.

Use the requested path. Otherwise create `<Company or Chip>架构.md` in the current project. In an Obsidian vault, use its established wide-note frontmatter. The report must remain understandable without reading chat history.

Read [references/writing-contract.md](references/writing-contract.md) completely and follow it. Adapt section depth to the evidence; keep its causal order.

Use existing official diagrams when they materially clarify hierarchy, topology or data flow. Store downloaded assets under the project's established image directory, grouped by company, and use relative Markdown paths. Record the original URL and caption. Generate diagrams only when the user explicitly permits it.

Preserve existing user edits and local repository rules. Put citations where the user requests; when citations are consolidated at the end, maintain a source map during research so every claim remains traceable.

## Validate

Before delivery, read and apply [references/review-checklist.md](references/review-checklist.md). Report missing evidence as a limitation. Do not fill gaps with confident prose.

For an explicitly short factual question, answer directly from the same evidence rules; do not create a report.
