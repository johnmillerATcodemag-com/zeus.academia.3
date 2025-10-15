---
prompt_metadata:
	id: create-use-case-instruction-prompt
	title: Meta Prompt — Create Use Case Instruction Prompt
	description: Creates a prompt that generates a Markdown authoring guide for use cases with standard format and Mermaid diagrams.
	owner: johnmillerATcodemag-com
	repository: zeus.academia.3
	version: 1.0.0
	created: 2025-10-14
	updated: 2025-10-14
	output_path: .github/prompts/create-use-case-instructions.prompt.md
	category: documentation
	tags: [use-cases, documentation, prompt-generation]
	output_format: markdown
---

# Prompt to create a prompt that will create an instruction file for creating use cases in Markdown files

This is prompt 0, hand-written to seed the process by creating the downstream prompt used to generate the authoring instructions. It was then updated by the instructions for creating prompts.

## Output requirements

- Create or overwrite the file at: `.github/prompts/create-use-case-instructions.prompt.md`.
- The output must conform to the Repository Prompt File Standards and include YAML `prompt_metadata`.
- The generated prompt must instruct producing `.github/prompts/create-use-case.instructions.md` with the standard use case format and Mermaid diagram guidance.

## Deliverable

Output only the final `.github/prompts/create-use-case-instructions.prompt.md` content as Markdown. Do not include any additional commentary.

## Use Case Creation Instruction Prompt

Create a prompt file for this requirement: "create a prompt file that creates an instruction file to use when creating use cases defined in markdown files. Include instructions to follow the standard use case format and to include a mermaid diagram of the use case."
