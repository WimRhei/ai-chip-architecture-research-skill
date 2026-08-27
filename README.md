# AI Chip Architecture Research Skill

A Codex skill for writing concise, source-grounded architecture reports for concrete AI accelerator generations.

It keeps hardware, execution, runtime dynamics, software ownership, scaling, and GPU tradeoffs in one causal structure. Claims must remain traceable to evidence; unsupported implementation guesses are omitted.

## Install

```bash
git clone https://github.com/WimRhei/ai-chip-architecture-research-skill.git \
  ~/.codex/skills/ai-chip-architecture-research
```

Restart Codex, then invoke:

```text
$ai-chip-architecture-research Research <company/chip generation> and write a complete Markdown architecture report.
```

## Structure

- `SKILL.md`: routing and core workflow
- `references/writing-contract.md`: report structure and evidence rules
- `references/review-checklist.md`: final validation checklist
- `agents/openai.yaml`: Codex UI metadata

## License

MIT
