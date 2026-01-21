---
user-invocable: true
name: execute-plan
description: Execute implementation plan using parallel subagents. Use when you have a plan URL/file to implement.
---

# Execute Plan

You are executing an implementation plan using the superpowers:executing-plans skill with systematic parallel subagents.

**Announce at start:** "I'm using the execute-plan skill to implement this plan."

## Step 1: Get Plan Location

Parse the user's command for a URL or file path argument. Examples:
- `/ant:execute-plan https://docs.google.com/document/d/xxx` → use that URL
- `/ant:execute-plan /path/to/plan.md` → use that file path
- `/ant:execute-plan` (no argument) → ask the user

If no argument was provided, ask the user using AskUserQuestion tool:
- Question: "What is the URL or file path of the plan you want to execute?"
- Header: "Plan URL"
- Options:
  - "I'll paste it now" - User will provide URL/path
  - "It's in my clipboard" - Ask user to paste it

## Step 2: Get Execution Mode

Ask the user using AskUserQuestion tool:
- Question: "How do you want to execute the plan steps?"
- Header: "Exec mode"
- Options:
  - "All at once (Recommended)" - Execute all steps using parallel subagents where possible
  - "In batches of 3" - Execute 3 steps at a time, report progress, wait for feedback
  - "Custom batch size" - User specifies how many steps per batch
  - "One by one" - Execute each step individually with confirmation between steps

If user selects "Custom batch size", ask follow-up using AskUserQuestion tool:
- Question: "How many steps per batch?"
- Header: "Batch size"
- Options:
  - "2 steps"
  - "5 steps"
  - "10 steps"

## Step 3: Load Plan

If the plan location is a Google Docs URL:
- Use the `ant:google-docs` skill to load the document content
- Select "Full document" when asked

If the plan location is a local file:
- Read the file using the Read tool

## Step 4: Execute

Invoke the `superpowers:executing-plans` skill with this context:

**Execution mode:** [the mode from Step 2]
**Instruction:** Use systematically parallel subagents (Task tool with appropriate subagent_type) for independent tasks within each batch.

Follow the executing-plans skill exactly as presented to you.
