# AI-Assisted Output Instructions

This guide defines how contributors must create, record, and commit AI-assisted outputs (code, docs, diagrams, tests, data) with proper provenance and logs. Provenance and logging protect quality, enable reproducibility, and support governance.

## Table of Contents

- [Who Should Use This Guide](#who-should-use-this-guide)
- [What’s in Scope](#whats-in-scope)
- [Required Provenance Metadata](#required-provenance-metadata)
- [Standard Metadata Front Matter (Preferred)](#standard-metadata-front-matter-preferred)
- [AI Chat Logging Workflow](#ai-chat-logging-workflow)
  - [Folder Layout](#folder-layout)
  - [Scaffold the Log Folders](#scaffold-the-log-folders)
  - [conversationmd Template](#conversationmd-template)
- [Provenance Template for Non-Markdown Artifacts](#provenance-template-for-non-markdown-artifacts)
- [Capturing Task Durations](#capturing-task-durations)
- [Placement and Naming](#placement-and-naming)
- [Example](#example)
- [Quality Checklist](#quality-checklist)
- [Security and Privacy](#security-and-privacy)

## Who Should Use This Guide

Contributors generating or curating AI-assisted content: code, documents, diagrams, tests, and data.

## What’s in Scope

- What metadata must be captured with each AI-assisted artifact.
- How to log conversational context and outputs.
- Ready-to-copy templates and a quality checklist.

## Required Provenance Metadata

Attach or embed the following metadata near the top of the artifact or in an adjacent sidecar file named `<artifact>.meta.md` with the same basename:

- AI-Generated: Yes
- Model: <provider/model@version>
- Operator: <full name or username>
- Prompt: <exact prompt text used>
- Started: <ISO8601 timestamp>
- Ended: <ISO8601 timestamp>
- Task Durations:
  - <Task 1 label>: <duration hh:mm:ss>
  - <Task 2 label>: <duration hh:mm:ss>
- Total Duration: <duration hh:mm:ss>
- Source Conversation Log: <relative path to AI log file>

If the artifact cannot embed front matter, use the sidecar `.meta.md` file.

## Standard Metadata Front Matter (Preferred)

Include this YAML front matter at the top of Markdown artifacts. For other formats, adapt as comments near the top of the file.

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

## AI Chat Logging Workflow

All AI chat transcripts and key outputs must be saved under `ai-logs/` in a date- and session-structured layout.

### Folder Layout

- Base folder: `ai-logs/`
- Structure: `ai-logs/yyyy/mm/dd/<session-id>/`
- Required files per session:
  - `conversation.md` — full prompt/response transcript with timestamps.
  - `summary.md` — short session summary (goals, key decisions, outcomes).
  - `artifacts/` — any generated files that aren’t directly committed elsewhere.

Tip: To keep empty folders tracked by Git, add a `.gitkeep` file inside them.

### Scaffold the Log Folders

PowerShell (Windows):

```powershell
$date = Get-Date
$yyyy = $date.ToString('yyyy')
$mm   = $date.ToString('MM')
$dd   = $date.ToString('dd')
$sessionId = [guid]::NewGuid().ToString()
$base = "ai-logs/$yyyy/$mm/$dd/$sessionId"

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
base="ai-logs/$yyyy/$mm/$dd/$sessionId"

mkdir -p "$base/artifacts"
: > "$base/conversation.md"
: > "$base/summary.md"

echo "Session folder created: $base"
```

### conversation.md Template

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

   <prompt text>

   [<timestamp>] AI

   <response excerpt or full>

<!-- Repeat for each exchange -->
```

## Provenance Template for Non-Markdown Artifacts

When front matter isn’t applicable (e.g., images, binaries), create a sidecar file: `<basename>.meta.md`.

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
```

## Capturing Task Durations

- Record the start and end timestamps for each significant task (e.g., drafting, refactor, diagram generation, test updates).
- Compute each task duration and the overall total.
- If multiple tools are used, list each tool’s portion or note parallel execution.

## Placement and Naming

- This instruction file lives at `.github/instructions/ai-assisted-output.instructions.md`.
- Save logs under `ai-logs/yyyy/mm/dd/<session-id>/`.
- Prefer lowercase for artifact filenames; include context (e.g., `uc-001-enrollment-diagram.md`).
- When creating any new AI-assisted artifact, add a short bullet to the project `README.md` that links to the artifact and states its purpose. If a section like "AI-Assisted Artifacts" exists, add to it; otherwise, create one.

## Example

Example Markdown artifact with front matter and a matching log header:

```markdown
---
ai_generated: true
model: "openai/gpt-4o@2025-09-01"
operator: "jane.doe"
prompt: |
  Generate a short README for the enrollment service.
started: "2025-10-14T14:02:10Z"
ended: "2025-10-14T14:06:25Z"
task_durations:
  - task: "draft"
    duration: "00:03:10"
  - task: "polish"
    duration: "00:01:05"
total_duration: "00:04:15"
ai_log: "ai-logs/2025/10/14/5c2b8c9c-4d6e-4a9d-8c1e-7a2c3e9f6a10/conversation.md"
---

# Enrollment Service README (Draft)

A minimal service that manages course enrollments...
```

Matching `conversation.md` header:

```markdown
# AI Conversation Log

- Session ID: 5c2b8c9c-4d6e-4a9d-8c1e-7a2c3e9f6a10
- Operator: jane.doe
- Model: openai/gpt-4o@2025-09-01
- Started: 2025-10-14T14:02:10Z
- Ended: 2025-10-14T14:06:25Z
- Total Duration: 00:04:15
```

## Quality Checklist

- [ ] AI-Generated flag set to true.
- [ ] Model, Operator, Prompt captured verbatim.
- [ ] Start/End timestamps present; task durations and total computed.
- [ ] Conversation log saved under `ai-logs/` and referenced in the artifact.
- [ ] Sensitive data not included in prompts or outputs.
- [ ] Filenames and paths follow the conventions.
- [ ] Sidecar `.meta.md` used when front matter isn’t supported.
- [ ] Example renders correctly in Markdown preview.
- [ ] Project `README.md` updated to reference any newly generated artifact (with link and one-line description).

## Security and Privacy

- Do not include secrets, tokens, or personal data in prompts, logs, or outputs.
- Redact or generalize any sensitive context before saving.
- If sensitive data is unavoidable, store it outside the repository and reference it abstractly.
