---
name: model-efficiency-router
description: Analyze project progress and forecast the complexity of the next task before starting it, then recommend whether to remain on an economical everyday model or switch temporarily to a stronger model and reasoning effort. Use during multi-step projects, at plan updates, after completing a task, before beginning a materially different phase, or whenever the user asks to conserve tokens, credits, or model consumption while preserving result quality.
---

# Model Efficiency Router

Optimize model usage without compromising the next task. Advise; do not claim to change the active model automatically.

## Establish the routing profile

Use an existing user preference when one is available. Otherwise define these roles without inventing product names:

- **Baseline:** the economical everyday model at medium or standard reasoning.
- **Complex:** the strongest generally available model at medium reasoning.
- **Exceptional:** the strongest generally available model at high reasoning.
- Return to the baseline as soon as the next distinct task is ordinary again.

Model names, entitlements, and reasoning controls change. Resolve them from the current interface or official product documentation. If they cannot be verified, recommend the role rather than guessing a model name. Never recommend unavailable controls.

## Assess at task boundaries

Assess silently at these points:

1. After inspecting a project or creating a plan.
2. Before starting the next plan item or materially different phase.
3. After completing a task, test run, investigation, or review.
4. When new evidence changes the expected difficulty.

Do not interrupt a tool call or partially completed operation merely to recommend a model. Give the notice before the next distinct task begins.

Inspect available evidence: the plan, repository structure, changed files, test results, unresolved failures, requirements, user constraints, and the likely next action. Do not perform broad repository analysis solely to score a trivial next step.

## Score the next task

Assign 0, 1, or 2 for each factor:

- **Ambiguity:** exact change known; some judgment; unclear goal or competing interpretations.
- **Coupling:** isolated file; several related components; cross-system or architectural effects.
- **Novelty:** familiar pattern; partly unfamiliar; new domain, protocol, or codebase behavior.
- **Risk:** easily reversible; meaningful regression risk; security, privacy, production, compliance, destructive, or irreversible impact.
- **Reasoning depth:** direct implementation; several dependent decisions; difficult debugging, proof, design, or tradeoff analysis.
- **Verification burden:** obvious local check; multiple tests or environments; weak observability or complex evidence synthesis.

Route by total:

- **0–7:** Baseline. Do not notify if already there.
- **8–10:** Complex.
- **11–12:** Exceptional.

Apply these overrides:

- Use the Complex tier at minimum for authentication or authorization design, cryptography, destructive migrations, incident containment, safety-critical changes, consequential legal/compliance interpretation, or complex production failures.
- Use the Complex tier when the next task requires reconciling several uncertain sources, tracing nonlocal behavior, choosing an architecture, or recovering from repeated failed approaches.
- Keep the Baseline tier for repository exploration, reading, searches, mechanical edits, formatting, straightforward tests, dependency inventory, well-specified refactors, and routine documentation.
- Do not escalate merely because a task is large. Prefer Terra when the work is repetitive, well specified, and easily verified.

## Avoid wasteful switching

- Recommend a change only when the next task crosses a routing boundary.
- Require concrete evidence; when uncertain between adjacent tiers, choose the lower-cost tier.
- Keep the stronger model through a tightly connected complex phase instead of switching for every small substep.
- Recommend switching back only after the complex phase is complete and the next distinct task scores 7 or lower.
- Never redo completed work solely because the earlier task used a lower-cost model.
- Treat token or credit savings as a routing objective, not a reason to skip necessary validation.

## Notify one task ahead

When a switch is useful, append one compact notice to the progress update or final response:

```text
Model heads-up — Before the next task, switch to <verified complex model> / medium.
Next task: <short task name>
Why: <one sentence naming the decisive complexity factors>
Return point: Switch back to Terra / medium after <phase or verification gate>.
```

For an exceptional escalation, substitute the verified Exceptional-tier model at high reasoning and explain the high-stakes or unusually difficult factor.

When returning to the baseline, use:

```text
Model heads-up — The complex phase is complete. Switch back to <verified baseline model> / medium before <next ordinary task>.
```

If no change is recommended, emit no model notice. Do not clutter every response with the score.

## Respect control boundaries

- Tell the user where to change the model only when that control is verified for the current product surface.
- Do not edit global or project model configuration unless the user explicitly requests a persistent default.
- Do not claim that invoking this skill changed the current thread's model.
- If the current model or effort is unknown, state the target recommendation without claiming whether a switch is required.

## Project persistence

A skill is reusable but is not a continuous background monitor. If the user wants this assessment enforced throughout one repository, suggest adding this single instruction to that repository's `AGENTS.md`:

```text
At each task boundary, use $model-efficiency-router to forecast the next task and announce model changes one task ahead.
```

Do not add or modify `AGENTS.md` unless the user asks.
