# HackAlem Demo Flow

## Goal

Show one complete PAF run from user intent to persisted evidence.

## Scenario

A user submits a concrete task with a measurable expected result.

PAF should:

1. accept the task;
2. structure the execution fields;
3. ask for clarification only when a required field is genuinely missing;
4. send the language/reasoning step to Qwen 2.5 14B;
5. validate the returned structure;
6. persist the run;
7. reopen the stored run;
8. show a PASS only when the stored evidence satisfies the completion rule.

## What the jury should be able to see

- The same input is represented as a structured task.
- The model used for the run is visible.
- Required fields are not silently invented.
- The result survives page/session reopening.
- The evidence belongs to the same run.
- Failure remains FAIL instead of being manually edited into success.

## Five-minute presentation

**0:00–0:45 — Problem**  
Chat answers disappear into conversation history. Real work needs state, validation, and evidence.

**0:45–1:30 — Product**  
PAF wraps an LLM in a task lifecycle.

**1:30–3:30 — Live run**  
Create task → execute → validate → save → reopen.

**3:30–4:30 — Architecture**  
Public UI → protected gateway → PAF pipeline → self-hosted Qwen → persistence.

**4:30–5:00 — Why it matters**  
The output is not just text: it becomes a reproducible, inspectable unit of work.
