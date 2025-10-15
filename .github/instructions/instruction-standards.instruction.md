# Instruction File Authoring Guide

## Introduction

This guide explains how to create clear, consistent instruction files for this repository. Use it whenever you document a repeatable process, standard, or policy that contributors should follow.

## Audience and Scope

- Audience: Contributors and maintainers authoring instruction files.
- Scope: Structure, placement, naming, and quality standards for instruction files; includes a reusable template, examples, and a checklist.
- Out of scope: Full architectural specifications, lengthy tutorials, or API reference documentation.

## File Placement and Naming Conventions

- Location: Store instruction files under `.github/instructions/`.
- Filename: Use hyphenated lowercase (kebab-case) and end with `.instruction.md`.
  - Example: `branch-naming-standards.instruction.md`
- One instruction file per topic.

## Standard Sections (Overview)

Every instruction file should include:

1. Title
2. Introduction (purpose and when to use)
3. Audience and Scope
4. Prerequisites
5. Output Requirements
6. Steps / Procedure
7. Examples / Samples
8. Templates / Snippets
9. Validation / Quality Checklist
10. File Placement and Naming
11. Versioning and Ownership
12. Security and Privacy
13. References / Glossary (optional)

## Copy/Paste Template (complete skeleton)

````
# Instruction File Title

## Introduction
<Brief purpose, when to use, and outcomes.>

## Audience and Scope
- Audience: <Who>
- Scope: <What’s included>
- Out of scope: <What’s not covered>

## Prerequisites
- <Tool/permission/context>

## Output Requirements
- <Exact output path(s)/formats>
- <No extra commentary/wrappers>

## Steps / Procedure
1. <Step>
2. <Step>
3. <Step>

## Examples / Samples
```example
<Short, complete example>
```

## Templates / Snippets
```markdown
<Reusable snippet or section>
```

## Validation / Quality Checklist
- [ ] Outputs and formats match requirements
- [ ] Steps are actionable and ordered
- [ ] Examples run or render as expected
- [ ] No secrets or sensitive data
- [ ] Naming and placement adhere to conventions

## File Placement and Naming
- Folder: `.github/instructions/`
- Filename: `<topic-name>.instruction.md`

## Versioning and Ownership
- Owner: <name/role>
- Last updated: YYYY-MM-DD
- Change policy: <how to propose changes>

## Security and Privacy
- <Redaction, secrets handling, PII guidance>

## References / Glossary
- <Links and definitions>
````

## Section-by-Section Guidance

- Title: Be specific and action-oriented (e.g., "CI Pipeline Instructions").
- Prerequisites: List only what’s required (tools, permissions); link to setup docs.
- Output Requirements: State exact outputs (paths, filenames), formats, and overwrite behavior.
- Steps / Procedure: Number steps; one action per step; capture expected outcomes/errors.
- Examples / Samples: Keep minimal yet complete; prefer copy/paste-ready commands or snippets.
- Templates / Snippets: Provide reusable blocks with placeholders and brief comments.
- Validation / Quality Checklist: Make criteria verifiable and short for quick scanning.
- File Placement and Naming: Reiterate `.github/instructions/` and `.instruction.md` suffix.
- Versioning and Ownership: Name a responsible owner and keep dates current.
- Security and Privacy: Avoid secrets and personal data; demonstrate redaction.
- References / Glossary: Link to related docs; define domain terms when helpful.

## Example (concise but realistic)

Title: Linting Instructions

- Audience: Contributors
- Scope: How to run and interpret linting locally

### Prerequisites

- Node.js and package manager installed

### Output Requirements

- Provide a passing lint run output excerpt; no extra commentary

### Steps / Procedure

1. Install dependencies
2. Run the linter
3. Fix reported issues and re-run

### Example Output

```text
$ npm ci
$ npm run lint
✔ No issues found
```

### Templates / Snippets

```markdown
- Command: `npm run lint`
- Expected: Exit code 0, no errors
```

## Quality Checklist

- Title and purpose are clear
- Steps are ordered, actionable, and testable
- Examples render/run as written
- Output path and format are explicit
- File lives under `.github/instructions/` and ends with `.instruction.md`
- No secrets, tokens, or personal data

## Versioning and Ownership

- Update "Last updated" whenever the file changes
- List an owner responsible for maintenance
- Increment versions when behavior changes (if applicable)

## Security and Privacy

- Do not include secrets, tokens, or PII
- Redact or omit sensitive content in examples and logs
- Follow organizational security policies

## References / Glossary

- Repository Prompt File Standards (if applicable)
- Related project docs
- Terminology used in this instruction
