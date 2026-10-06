---
name: [skill-name]
description: [What the skill does AND when to use it. Be specific and slightly "pushy" — list the phrases, tasks, and contexts that should trigger it.]
---

# [Skill Name]

## File Guidance
This file describes the [Skill Name] skill. [When to use it in one line.]

## Skill Objectives
[Skill Name] will [primary outcome, e.g., respond with an answer and code references for code-related engineering questions].
The skill shall focus on a quality, reliable response, checking the response before providing it to the user.

## Tools
1. [e.g., PDF versions of codes located in this folder — C:\corporate\engineering\codes]
2. [e.g., Internet searches]
3. [e.g., Local codes / references in `references/`]
4. [e.g., Other connectors and tools available within Claude (approved in prompts/tools/TOOLS.md)]
5. [Other resources defined with the user]
6. [CONFIG.md — if this skill has config overrides]

## Workflow
The workflow for [Skill Name]:
1. [User asks the skill a question about ...]
2. [The skill searches the reference texts for relevant sections — `references/(file)`]
3. [The skill searches other resources for additional context]
4. [The skill may ask the user questions about the circumstance to provide an optimal answer, or calculate a response from tables/data]
5. [The skill provides the response, including references and assumptions]

Important files and folders: `references/` — [list key files and what each is for].

## File Structure
No updates shall be made to this file except for:
1. Workflow — only updated after approval from the user.
2. Tools and systems used for the skill to operate.

Separate markdown files shall be created for sub-skills or processes with key items and workflows: [list, e.g., `calc-method.md`].

<!-- USER-TIPS (humans only)
AI: Ignore this block. Do not reference, quote, summarize, or act on it.
- Copy this file to agents/skills/[skill-name]/SKILL.md, then fill every bracket.
- The description is how AI decides to use the skill. Name the words people actually type.
- Keep SKILL.md under ~500 lines; push detail into references/ and sub-process md files.
- Provide your own source files (codes, standards, examples) for skill creation; AI should not invent them.
END USER-TIPS -->
