---
name: ai-chip-architecture-research
description: Create or refine standalone Markdown reports on concrete AI chips and systems, explaining workload bottlenecks, hardware, execution and architectural tradeoffs. Use for vendor or generation-specific accelerator and AI-system CPU research; exclude paper-only reading notes and generic market summaries.
---

# AI Chip Architecture Research

Explain the architecture through one causal chain:

**Workload bottleneck → hardware and execution choices → benefit → cost and failure conditions.**

Write for a reader with computer-architecture fundamentals. Preserve mechanisms; remove repetition and details that do not change the conclusion.

## Scope

Identify the central question, exact chip generation, product status, system layers and output path. For an existing report, read it first and preserve user edits, questions and hypotheses as such.

If only a company is named, prefer its latest available chip with adequate architecture documentation. Availability requires ordering, delivery, general availability or named deployment; an announcement or future shipping window is insufficient. Cover a newer announced generation separately. An explicitly requested prototype or legacy chip remains in scope.

Keep die, package, board, node, rack and software claims distinct. Never merge generations silently. Inherit older mechanisms only with current corroboration or explicit family continuity; label that evidence and do not inherit generation-specific specifications.

## Research and explain

Read [references/writing-contract.md](references/writing-contract.md) for the report structure and mechanism questions. Adapt depth and headings to the architecture and user's question.

Find where computation and data are placed, when execution advances, and who controls each decision: hardware, compiler, runtime or programmer. Connect these through one sourced execution path. Distinguish fixed placement from fixed timing, runtime data changes from resource rescheduling, and shorter latency from latency hidden by independent work.

Compare against the relevant contemporary baseline: GPU for an accelerator, server CPU for a CPU, or a comparable system for a system claim. Explain the changed mechanism and resulting cost; common capabilities alone do not establish an advantage.

## Evidence

Prefer architecture manuals, specifications and source code, then official engineering material, vendor papers/patents and independent technical analysis. Check that each source describes the implementation and generation studied; a patent or proposed design does not confirm shipped hardware.

Trace every nontrivial fact to a source. Separate documented facts, calculations, architectural inference and evaluation. Keep reconstructions and user hypotheses separate from confirmed hardware. Verify time-sensitive product status and specifications live when practical.

State confirmed facts directly. Omit inconsequential uncertainty; qualify material inference once where it matters. Do not repeat source history or defensive caveats throughout the body.

Open software does not prove open hardware; operator support does not prove efficient execution; peak throughput or a local optimization does not prove end-to-end architecture gains.

## Deliver

For a chip/company research request, create a complete standalone Markdown report, unless the user requests another format. For a short factual question, answer directly. For an existing document, make the requested local edit rather than automatically rewriting the report.

Use the requested path; otherwise create `<Company or Chip>架构.md` in the current project. Follow local repository rules and established Obsidian wide-note frontmatter.

Use official diagrams when they clarify hierarchy, topology or data flow. Store assets in the established image directory, grouped by company, with relative Markdown paths and original URLs/captions. Generate diagrams only with explicit user permission.

Put citations where requested; retain claim-to-source traceability when references are consolidated at the end. Before delivery, apply [references/review-checklist.md](references/review-checklist.md).
