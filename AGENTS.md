# AGENTS.md

## Repository purpose
This repo hosts public Agent Skills. Each skill is a self-contained folder under `skills/` with a required `SKILL.md` that follows the Agent Skills specification.

## Adding a new skill
- Create a new folder under `skills/<skill-name>/` using kebab-case.
- Ensure the directory name matches the `name` field in `SKILL.md`.
- Include clear instructions, examples, and references as needed.
- Keep `SKILL.md` concise; move large references into supporting files in the skill folder.

## Working on existing skills
- Keep changes scoped to the skill folder you are updating.
- Maintain the skill's existing structure and style.
- If adding scripts or assets, document how they are used within the `SKILL.md`.

## Validation
- Validate skills with the reference library when possible: https://github.com/agentskills/agentskills/tree/main/skills-ref
- Follow the canonical spec: https://agentskills.io/specification

## General guidelines
- Avoid secrets or credentials in any skill files.
- Prefer small, focused edits and clear commit messages.
