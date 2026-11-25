# Contributing

Thanks for adding to the skill layer. A good skill turns a GTM play that works into steps an agent can run on its own.

## Add a skill

1. Fork the repo and create `skills/<skill-name>/SKILL.md`. Use lowercase words joined by hyphens for the name.
2. Start from the template below.
3. Only use tools listed in [llms.txt](https://tryingrow.com/llms.txt) or the [catalog](https://tryingrow.com/catalog.json), with the price shown there.
4. Run the skill once end to end with your own key, and paste what it returned and what it cost in the pull request.
5. Add a row for it to the table in `README.md`, under the right group.

## Template

```markdown
---
name: skill-name
description: What the skill does, in one or two sentences. Use when the user asks for ...
---

# Skill title

Why this play works, in one or two sentences.

## Before you start

Ask the user for anything below that they have not given you:

- Input one.
- Input two.

## Steps

1. What to do and why.  
   InGrow tool `toolName` (`POST /public-api/provider/endpoint`), $0.001 per call.

## What to return

- The shape of the answer, for example a table with named columns.

## Cost

What one run costs, per account, person or call.

## Guardrails

- What the agent must not do.
```

## What makes a skill good

- The description says when to use it, so the agent loads it at the right time.
- It does the cheap checks first and the expensive calls only for what is left.
- It asks before spending on long lists, and reports the total spent.
- It never invents data. When a source returns nothing, it says so.
- It respects people. No scraping of private data, no identifying anonymous reviewers, no spam.

## Improve a skill

Open a pull request with the change and a short note on what got better, with a before and after run if you can.

## Questions

Open an issue, or write to akshay@tryingrow.com.
