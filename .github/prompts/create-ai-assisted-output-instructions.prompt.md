---
prompt_metadata:
  id: create-ai-assisted-output-instructions
  title: Generate AI-Assisted Output Instructions (Markdown)
  description: Generates repository guidelines for AI-assisted outputs, including provenance metadata requirements and an AI chat logging workflow.
  owner: johnmillerATcodemag-com
  repository: zeus.academia.3
  version: 1.0.0
  created: 2025-10-14
  updated: 2025-10-14
  output_path: .github/instructions/ai-assisted-output-instructions.md
  category: documentation
  tags: [ai, provenance, logging, governance]
  output_format: markdown
---

# Prompt: Generate AI-Assisted Output Instructions (Markdown)

You are an expert technical writer. Create a clear, actionable instruction file (Markdown) that contributors must follow whenever they generate AI-assisted output for this repository.

## Output requirements

- Create or overwrite the file at: `.github/instructions/ai-assisted-output-instructions.md`.

# Prompt: Generate AI-Assisted Output Instructions (Markdown)

You are an expert technical writer. Create a clear, actionable instruction file (Markdown) that contributors must follow whenever they generate AI-assisted output for this repository.

## Output requirements

- Create or overwrite the file at: `.github/instructions/ai-assisted-output-instructions.md`.
- Format strictly as Markdown with headings and lists.
- Include a short introduction on why provenance and logging matter.
- Provide a table of contents.

## Audience

- Contributors generating or curating AI-assisted content (code, docs, diagrams, tests, data).

## Scope

- Define what metadata must be captured with each AI-assisted artifact.
- Define the logging workflow for conversational context and outputs.
- Provide a template and a quality checklist.

## Required provenance metadata (for every AI-assisted artifact)

Authors must attach or embed the following metadata near the top of the artifact or in an adjacent `.meta.md` file with the same basename:

- AI-Generated: Yes
- Model: <model name and version>
- Operator: <full name or username>
- Prompt: <exact prompt text used>
- Started: <ISO8601 timestamp>
- Ended: <ISO8601 timestamp>
- Task Durations:
  - <Task 1 label>: <duration hh:mm:ss>
  - <Task 2 label>: <duration hh:mm:ss>
- Total Duration: <duration hh:mm:ss>
- Source Conversation Log: <relative path to AI log file>

If the artifact cannot embed front matter, create a sidecar file named `<artifact>.meta.md` with the above content.

## Standard metadata front matter (preferred)

Provide this copy/paste YAML front matter block authors should include at the top of Markdown artifacts, or adapt for other formats as comments:

```yaml
---
ai_generated: true
model: "<provider>/<model>@<version>"
operator: "<name-or-username>"
prompt: |
  <paste exact prompt text>
started: "<YYYY-MM-DDTHH:MM:SSZ>"
ended: "<YYYY-MM-DDTHH:MM:SSZ>"
# List fine-grained task timings to aid reproducibility
task_durations:
  - task: "<label>"
    duration: "<hh:mm:ss>"
  - task: "<label>"
    duration: "<hh:mm:ss>"
total_duration: "<hh:mm:ss>"
ai_log: "ai-logs/<yyyy>/<mm>/<dd>/<session-id>/conversation.md"
---
```

## AI chat logging workflow

All AI chat transcripts and key outputs must be saved under `ai-logs/` in a date- and session-structured layout.

- Base folder: `ai-logs/`
- Structure: `ai-logs/yyyy/mm/dd/<session-id>/`
- Required files per session:
  - `conversation.md` — full prompt/response transcript with timestamps.
  - `summary.md` — short session summary (goals, key decisions, outcomes).
  - `artifacts/` — any generated files that aren’t directly committed elsewhere.

### Scaffold the log folders (recommended)

Include steps and sample commands for contributors to quickly scaffold the folder structure for a new session. Provide both PowerShell and Bash examples. These should be considered optional helpers; contributors may adapt them as needed.

PowerShell (Windows):

```powershell
$date = Get-Date
$yyyy = $date.ToString('yyyy')
$mm   = $date.ToString('MM')
$dd   = $date.ToString('dd')
$sessionId = [guid]::NewGuid().ToString()
$base = "AI-logs/$yyyy/$mm/$dd/$sessionId"

New-Item -ItemType Directory -Path $base, "$base/artifacts" -Force | Out-Null
New-Item -ItemType File -Path "$base/conversation.md", "$base/summary.md" -Force | Out-Null

Write-Host "Session folder created:" $base
```

Bash (macOS/Linux/WSL):

```bash
yyyy=$(date +%Y)
mm=$(date +%m)
dd=$(date +%d)
sessionId=$(uuidgen 2>/dev/null || cat /proc/sys/kernel/random/uuid)
base="AI-logs/$yyyy/$mm/$dd/$sessionId"

mkdir -p "$base/artifacts"
: > "$base/conversation.md"
: > "$base/summary.md"

echo "Session folder created: $base"
```

Tip: To keep empty folders tracked by Git, you may add a `.gitkeep` file inside them.

### `conversation.md` template

```markdown
# AI Conversation Log

- Session ID: <uuid or slug>
- Operator: <name>
- Model: <provider>/<model>@<version>
- Started: <ISO8601>
- Ended: <ISO8601>
- Total Duration: <hh:mm:ss>

## Exchanges

1. [<timestamp>] USER
```

   <prompt text>
   ```

[<timestamp>] AI

```
<response excerpt or full>
```

<!-- Repeat for each exchange -->

````

## Provenance template for non-Markdown artifacts

When front matter isn’t applicable (e.g., images, binaries), create a sidecar: `<basename>.meta.md`.

```markdown
# AI-Assisted Artifact Metadata

- Artifact: <relative path>
- AI-Generated: Yes
- Model: <provider>/<model>@<version>
- Operator: <name>
- Prompt: |
  <exact prompt>
- Started: <ISO8601>
- Ended: <ISO8601>
- Task Durations:
  - <task>: <hh:mm:ss>
- Total Duration: <hh:mm:ss>
- Source Conversation Log: <relative path>
````

## Capturing task durations

- Record the start and end timestamps for each significant task (e.g., drafting, refactor, diagram generation, test updates).
- Compute each task duration and the overall total.
- If multiple tools are used, list each tool’s portion or note parallel execution.

## Placement and naming

- Place `ai-assisted-output-instructions.md` in `.github/instructions`.
- Place logs in `ai-logs/yyyy/mm/dd/<session-id>/`.
- Prefer lowercase for artifact filenames; include context (e.g., `uc-001-enrollment-diagram.md`).

## Example

Provide a brief filled example showing a Markdown file with front matter, and a matching `ai-logs/yyyy/mm/dd/<session-id>/conversation.md` header.

## Quality checklist

- AI-Generated flag set to true.
- Model, Operator, Prompt captured verbatim.
- Start/End timestamps present; task durations and total computed.
- Conversation log saved under `ai-logs/` and referenced.
- Sensitive data not included in prompts or outputs.
- Filenames and paths follow the conventions.

## Deliverable

Output only the final Markdown content for `.github/instructions/ai-assisted-output.instructions.md`. Do not include commentary outside the document.
