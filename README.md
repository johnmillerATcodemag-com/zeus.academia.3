# Zeus Academia 3

A documentation-centric repository for academia-related domain modeling, use-case authoring, and AI-assisted workflow governance. It includes an Object-Role Modeling (ORM) model with generated reports, contributor authoring guides, and policies for AI-assisted outputs.

## Repository layout

```
/ (root)
├─ README.md                     # This file
├─ docs/
│  └─ tips-and-tricks.md        # General tips
├─ Model/
│  ├─ orm/
│  │  ├─ academia.md            # Notes about the ORM model
│  │  ├─ academia.orm           # ORM source
│  │  └─ academia.txt           # Export/notes
│  ├─ Report/                    # Generated HTML reports
│  │  ├─ ConstraintValidationReport.html
│  │  ├─ ObjectTypeList.html
│  │  ├─ orm.html
│  │  ├─ FactTypes/              # Per-fact-type HTML pages
│  │  └─ ObjectTypes/            # Per-object-type HTML pages
│  └─ use-cases/                 # Place authored use cases here
└─ .github/
   ├─ instructions/              # Authoring guides and policies
   │  ├─ ai-assisted-output.instructions.md
   │  ├─ create-use-case.instructions.md
   │  ├─ instruction-standards.instruction.md
   │  └─ prompt-standards.instructions.md
   └─ prompts/                   # Prompts used to generate instruction docs
      ├─ create-ai-assisted-output-instructions.prompt.md
      ├─ create-instruction-file-instructions.prompt.md
      └─ create-use-case-instructions.prompt.md
```

## What’s inside

- ORM model and reports under `Model/`:
  - Open `Model/Report/orm.html` for a navigable entry point.
  - Explore `ObjectTypes/` and `FactTypes/` for detailed pages.
  - See `ConstraintValidationReport.html` for model constraint checks.
- Contributor guides under `.github/instructions/`:
  - `create-use-case.instructions.md` — How to author use cases (with Mermaid diagrams).
  - `instruction-standards.instruction.md` — How to write instruction files uniformly.
  - `ai-assisted-output.instructions.md` — Provenance, logging, and governance for AI-assisted work.
  - `prompt-standards.instructions.md` — Prompt authoring/formatting standards.
- Prompt sources under `.github/prompts/` that generated the above instruction files.

## Authoring use cases

- Follow `.github/instructions/create-use-case.instructions.md`.
- Save each use case as a separate file under `Model/use-cases/` using the naming pattern `use-case-<kebab>.md`.
- Include one Mermaid diagram per use case (flowchart or sequence), inline in the file.

## Writing instruction files

- Follow `.github/instructions/instruction-standards.instruction.md`.
- Place new instruction files in `.github/instructions/`.
- Use kebab-case filenames ending with `.instruction.md`.

## AI-assisted workflow and logging

- Policy: `.github/instructions/ai-assisted-output.instructions.md`.
- Always capture provenance metadata and store chat logs under `ai-logs/yyyy/mm/dd/<session-id>/`.
- When generating any new AI-assisted artifact, add a short bullet to this README under “AI-Assisted Artifacts” (below) with a link and one-line purpose.

### Optional helpers to scaffold logs

See the policy for copy/paste PowerShell and Bash snippets that create the `ai-logs/` session folder structure and seed `conversation.md` and `summary.md` files.

## AI-Assisted Artifacts

A running list of notable AI-assisted outputs with links and one-line descriptions.

- `.github/instructions/create-use-case.instructions.md` — Guide to author use cases with a standard template and Mermaid.
- `.github/instructions/instruction-standards.instruction.md` — Guide to create consistent instruction files.
- `.github/instructions/ai-assisted-output.instructions.md` — Policy for provenance and AI chat logging.
- `.github/instructions/prompt-standards.instructions.md` — Standards for prompt files and metadata.
- `Model/use-cases/derived-use-cases.index.md` — Index of use cases derived from `Model/orm/academia.txt` (6 initial use cases).

(When you add a new AI-assisted artifact, append it here.)

## Viewing the ORM reports

Open the HTML files directly in your browser:

- `Model/Report/orm.html` — main report index.
- `Model/Report/ObjectTypeList.html` — object types overview.
- `Model/Report/ConstraintValidationReport.html` — constraint checks.

## Docs

- General tips: `docs/tips-and-tricks.md`

## Contributing

- Follow the authoring guides in `.github/instructions/`.
- Use the AI-assisted policy when working with AI tools (provenance and `ai-logs/`).
- Keep changes scoped and documented; when adding new artifacts, update this README under “AI-Assisted Artifacts.”

## License

Not specified.

## Project metadata

- Repository: `johnmillerATcodemag-com/zeus.academia.3`
- Primary areas: ORM model and reports, authoring guides, AI-assisted governance
