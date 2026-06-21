# Repository Instructions

## Scope

These instructions apply to the whole repository.

This repository packages `worldcup-predictor`, an agent skill for structured World Cup and international football match analysis.

## Source Of Truth

- Keep `SKILL.md` as the authoritative skill entrypoint.
- Keep detailed reusable analysis rules in `references/prediction-framework.md`.
- Keep `agents/openai.yaml` aligned with `SKILL.md` when changing display name, summary, or default prompt.
- Keep `README.md` and `README_CN.md` as GitHub-facing documentation, not as duplicated skill logic.
- Keep `CLAUDE.md` as a compatibility pointer to this file only.

## Editing Guidelines

- Make small, scoped changes. Do not introduce extra frameworks, scripts, generated assets, or package metadata unless explicitly needed.
- Keep the skill portable and agent-agnostic. Avoid instructions that only work in one specific agent runtime unless they are isolated under the relevant file, such as `agents/openai.yaml`.
- Keep `SKILL.md` concise. Move detailed weighting rules, templates, and examples into `references/`.
- Do not duplicate long sections across `SKILL.md`, `README.md`, and `README_CN.md`; summarize in README files and link conceptually to the skill.
- Use ASCII in code/config files by default. Chinese documentation is acceptable in `README_CN.md`.

## Safety And Disclaimer Requirements

- Preserve the informational-use disclaimer in `SKILL.md`, `references/prediction-framework.md`, `README.md`, and `README_CN.md`.
- Do not frame odds, betting markets, exchange prices, or score predictions as guaranteed outcomes, betting advice, financial advice, or instructions to wager.
- When adding examples, keep them clearly analytical and avoid language that encourages betting.
- Prefer public market pages for baseline odds/probabilities. Treat screenshots as fallback and API/orderbook data as optional detail only when specifically needed.
- Do not include secrets, API keys, tokens, or private data in any file.

## Validation

After editing skill metadata or structure, validate:

```bash
python <path-to-skill-creator>/scripts/quick_validate.py .
```

If that validator is unavailable in the current environment, manually check that:

- `SKILL.md` starts with YAML frontmatter.
- Frontmatter includes only valid fields, especially `name` and `description`.
- `name` is lowercase hyphen-case.
- `description` clearly says when to use the skill and stays under 1024 characters.
- Referenced files in `SKILL.md`, README files, and `agents/openai.yaml` exist.

For documentation-only changes, also scan for stale file names, broken structure examples, and missing disclaimer language.

## Publishing Notes

- Keep `LICENSE` in sync with README license text if reuse terms change.
- If turning this folder into a Git repository, check status before committing and avoid bundling unrelated local files.
- Keep release-facing documentation in both English and Chinese when changing public behavior.
