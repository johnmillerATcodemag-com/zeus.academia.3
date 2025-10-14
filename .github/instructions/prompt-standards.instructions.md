## applyTo: "\*_/_.prompt.md"

# Repository Prompt File Standards

These standards apply to all prompt files in this repository (e.g., files ending with `.prompt.md`). They ensure prompts are discoverable, toolable, and produce consistent outputs.

## 1) Front matter (required)

Each prompt MUST begin with YAML front matter containing `prompt_metadata` with the following fields:

```yaml
---
prompt_metadata:
  id: <kebab-case-slug>
  title: <human-friendly title>
  description: <what this prompt generates>
  owner: <name-or-handle>
  repository: zeus.academia.3
  version: 1.0.0
  created: <YYYY-MM-DD>
  updated: <YYYY-MM-DD>
  output_path: <relative path of generated artifact>
  category: documentation | codegen | governance | testing | data | infra | analysis | other
  tags: [<keyword>, <keyword>]
  output_format: markdown | json | text | yaml | md
---
```

- Use ISO dates.
- Increment `version` on behavioral changes.
- Keep `id` globally unique within the repo (kebab-case).
- Optional sections: `inputs`, `runtime`, `compliance` per `.github/prompt.meta.schema.json`.

## 2) Structure inside the prompt

Prompts SHOULD follow this structure:

- H1 title matching `prompt_metadata.title`.
- Introduction or role specification (1–3 sentences max).
- Output requirements (clear path(s), format, constraints).
- Audience and scope (short bullets).
- Main instructions organized by headings.
- Deliverable section clearly stating what the AI must output and any “no extra commentary” rules.

## 3) Code fences and examples

- Use labeled code fences for syntax highlighting (e.g., `yaml`, `markdown`, `powershell`, `bash`).
- For nested verbatim blocks inside examples, prefer `~~~` to avoid fence collisions.
- Keep examples minimal but complete.

## 4) Paths and side effects

- Always specify output paths relative to repo root.
- If the prompt writes files, state overwrite behavior explicitly.
- If the prompt requires creating directories, include safe, cross-OS scaffolding guidance when helpful.

## 5) Compliance with schema

- Front matter MUST validate against `.github/prompt.meta.schema.json`.
- Use consistent key names and formats.

## 6) Security and privacy

- Do not include secrets, tokens, or personal data in examples.
- Recommend omitting or redacting sensitive material in logs or outputs.

## 7) Quality checklist

Every prompt SHOULD include a checklist covering:

- Output path and format are specified.
- Inputs/assumptions are stated (if any).
- No extra commentary beyond the deliverable.
- Examples render correctly.

## 8) Versioning and ownership

- Update `updated` on edits; bump `version` when behavior changes.
- Keep `owner` current. Transfer ownership when maintainers change.

## 9) Filenames

- All prompt filenames MUST be lowercase and end with `.prompt.md`.
- Use only lowercase letters, numbers, and hyphens in the basename (kebab-case), e.g., `create-ai-assisted-output-instructions.prompt.md`.
- Recommended location: `.github/prompts/`.

## References

- Schema: `.github/prompt.meta.schema.json`
- Examples: `.github/prompts/create-ai-assisted-output-instructions.prompt.md`
