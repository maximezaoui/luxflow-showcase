# Workflow-First Method

LuxFlow follows a Workflow-First production method.

The objective is to avoid uncontrolled project execution by defining a clear sequence:

```txt
Contract → Build → Gate → Patch → Export → Maintain
```

This method is used to keep work structured, traceable and easier to validate.

---

## Why Workflow-First?

Many projects fail or become messy because production starts too early.

Common issues:

```txt
Unclear scope
Missing acceptance criteria
Duplicated components
Untracked decisions
No validation gates
No delivery checklist
No maintenance plan
AI output without control
```

Workflow-First solves this by forcing every production effort to pass through a minimal structure.

---

## Core Sequence

### 1. Contract

The contract defines what should be done before production starts.

It should clarify:

- objective;
- scope;
- inputs;
- expected outputs;
- constraints;
- assumptions;
- acceptance criteria.

A contract does not need to be long.  
It needs to be clear.

Example:

```md
## Contract

Objective:
Create a public showcase README for LuxFlow.

Scope:
- Present the project vision
- Explain the architecture
- Add simplified code examples
- Keep private implementation details hidden

Outputs:
- README.md
- Supporting docs
- Validation checklist

Acceptance criteria:
- Clear for recruiters
- Clear for technical readers
- No private secrets
- No unsupported claims
```

---

### 2. Build

The build step creates the artefacts.

Artefacts can be:

```txt
Markdown files
Code files
Configuration files
Design tokens
Project templates
Validation scripts
Export bundles
Reports
Documentation
```

The build step should produce concrete outputs, not only discussion.

---

### 3. Gate

The gate step checks whether the build is acceptable.

A gate can be manual or automated.

Examples:

```txt
Required files exist
TypeScript passes
Build passes
No secret is exposed
No forbidden import is used
Documentation is complete
Theme contract is respected
Export bundle is valid
```

Gate results should be explicit:

```txt
PASS
WARN
FAIL
```

---

### 4. Patch

The patch step fixes issues detected during the gate.

A patch should be focused.

It should not restart the whole project unless necessary.

Example:

```txt
Issue:
README references a file that does not exist.

Patch:
Add the missing file or remove the broken reference.

Gate:
Run validation again.
```

---

### 5. Export

The export step prepares the work for reuse, delivery or execution.

An export can contain:

```txt
Final files
Prompt bundles
Project configuration
Delivery documentation
Client handoff
Technical notes
Validation report
```

The goal is to avoid losing context after production.

---

### 6. Maintain

The maintain step covers what happens after delivery.

It can include:

```txt
Post-launch checklist
Maintenance plan
Recurring audits
Improvement backlog
Version updates
Bug fixes
Client support
```

This prevents projects from being treated as finished too early.

---

## Workflow-First and AI

LuxFlow uses AI as a production assistant, not as an uncontrolled generator.

AI can help with:

```txt
Structuring plans
Generating documentation
Preparing code
Reviewing outputs
Creating prompts
Detecting inconsistencies
Summarizing reports
Producing patches
```

But AI should operate inside a structured workflow.

The system should define:

```txt
What is being produced
What files are expected
What constraints apply
What must be validated
What counts as done
```

---

## Chat vs Flow

LuxFlow distinguishes casual discussion from production work.

### Chat

Chat is useful for:

```txt
Thinking
Explaining
Exploring options
Clarifying direction
Discussing strategy
```

### Flow

A flow is used when the user wants production.

A flow should generate:

```txt
A contract
Artefacts
Gates
Patches if needed
Exports
```

This difference is important because not every conversation should immediately become a production run.

---

## Flow Example

```txt
User request:
Create a landing page project using LuxFlow.

Contract:
Define site type, sections, theme, integrations and output.

Build:
Generate ProjectConfig, prompt bundle and expected file tree.

Gate:
Validate required fields, sections, theme and delivery checklist.

Patch:
Fix missing items or invalid configuration.

Export:
Prepare JSON bundle and Markdown prompt.

Maintain:
Generate post-launch and maintenance checklists.
```

---

## Artefacts

A Workflow-First process should produce concrete artefacts.

Examples:

```txt
README.md
ARCHITECTURE.md
project-config.v2.json
theme.css
validation-gate.mjs
export-bundle.json
DELIVERY.md
MAINTENANCE.md
```

Artefacts make the work reusable.

---

## Gates

Gates are essential because they protect quality.

A gate can check:

```txt
Structure
Naming
Types
Build
Documentation
Security
Design tokens
Imports
Configuration
Deployment readiness
```

A good gate is specific and repeatable.

Example:

```js
import { existsSync } from "node:fs";

const requiredFiles = [
  "README.md",
  "docs/ARCHITECTURE.md",
  "docs/WORKFLOW_FIRST.md",
];

for (const file of requiredFiles) {
  if (!existsSync(file)) {
    throw new Error(`Missing required file: ${file}`);
  }
}

console.log("Gate passed.");
```

---

## Decision Tracking

LuxFlow should keep decisions explicit.

A decision should explain:

```txt
What was decided
Why it was decided
What alternatives existed
What impact it has
What should be reviewed later
```

This reduces confusion when a project evolves.

---

## Workflow Statuses

A project or run can use clear statuses:

```txt
DRAFT
READY
IN_PROGRESS
PASS
WARN
FAIL
PATCH_REQUIRED
EXPORTED
MAINTENANCE
```

The exact status model can evolve, but the important part is clarity.

---

## Benefits

Workflow-First helps LuxFlow improve:

```txt
Project clarity
Execution speed
Output quality
Documentation
Reuse
Validation
Delivery reliability
Maintenance readiness
```

It also makes AI-assisted production safer because the AI works inside explicit constraints.

---

## What Workflow-First Avoids

The method is designed to avoid:

```txt
Random generation
Unclear outputs
Unvalidated delivery
Missing documentation
Duplicated work
Inconsistent design
Hidden technical debt
Untraceable decisions
```

---

## Final Principle

A LuxFlow run should not end with only an answer.

It should end with something that can be inspected, reused, validated or delivered.

```txt
No vague output.
No hidden assumptions.
No delivery without gates.
No project without traceability.
```
