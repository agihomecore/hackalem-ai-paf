# Architecture

PAF is designed as a layered system so the user interface, execution logic, model runtime, and memory can evolve independently.

## 1. Interaction layer

The user works through GALYMZHAN / PAF interfaces. The public layer does not expose the model runtime directly.

## 2. Protected gateway

Authentication and routing sit between the public interface and the private runtime. This keeps the model and internal services behind a controlled boundary.

## 3. Task pipeline

PAF converts a free-form task into an execution structure. The pipeline can validate required fields before a run is accepted as complete.

## 4. Model runtime

The current text runtime uses a self-hosted **Qwen 2.5 14B** model.

The model is a component of the system, not the system itself. PAF is responsible for orchestration, validation, state, and evidence.

## 5. Memory and persistence

The runtime separates short-lived execution context from persistent project state.

The production stack contains relational, vector, and graph-oriented storage layers. Exact production configuration is intentionally not published here.

## 6. Validation

A run should have an explicit completion condition.

For the hackathon demo, the key proof is:

```text
task accepted
→ model executed
→ required output present
→ result persisted
→ same result reopened
→ PASS evidence shown
```

## Design principles

- Observer before action.
- Reproducible state over one-off chat output.
- Local/private inference where practical.
- Explicit validation instead of pretending success.
- Public showcase separated from production infrastructure.
- Secrets and private memory never committed to Git.
