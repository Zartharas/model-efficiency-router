# Model Efficiency Router

Forecast the complexity of the next project phase and recommend when to stay on an economical everyday model, temporarily switch to a stronger model, and switch back.

The skill is designed for long-running coding, research, security, and operational projects where indiscriminate use of the most expensive model wastes credits, but switching too late can compromise difficult work.

## What it does

- Scores the **next task**, not the work already completed.
- Uses ambiguity, coupling, novelty, risk, reasoning depth, and verification burden.
- Notifies the user one task before a stronger model would help.
- Keeps a stronger model through a coherent complex phase.
- Recommends returning to the baseline when the difficult phase ends.
- Advises only; it never pretends to change the selected model automatically.
- Resolves current model names from the active product instead of hard-coding labels.

## Install

### Download

Download [`dist/model-efficiency-router.skill`](dist/model-efficiency-router.skill) and install or upload it through a compatible Agent Skills interface.

### Manual installation

Copy `skill/model-efficiency-router` into the personal skills directory supported by your agent.

For Codex:

```text
~/.codex/skills/model-efficiency-router/
```

Start a new task after installation so the skill is discovered.

## Invoke

```text
Use $model-efficiency-router throughout this project. At each task boundary,
forecast the next task and notify me one task ahead when changing model tier
would materially improve cost or quality.
```

The skill can also activate when a user asks to conserve model credits or requests advance model-switch recommendations during a multi-step project.

## Routing method

Each factor receives a score from 0 to 2:

| Factor | Low | Medium | High |
|---|---|---|---|
| Ambiguity | Exact change known | Some judgment | Competing interpretations |
| Coupling | Isolated | Several components | Cross-system |
| Novelty | Familiar | Partly unfamiliar | New domain or behavior |
| Risk | Easily reversible | Regression risk | Security or irreversible impact |
| Reasoning depth | Direct | Dependent decisions | Proof, architecture, or difficult debugging |
| Verification | Obvious check | Multiple checks | Weak observability or complex synthesis |

The resulting tier is mapped to the models and reasoning controls actually available in the current product.

## Design boundaries

- A large but repetitive task does not automatically require a premium model.
- Security, cryptography, destructive migrations, incident containment, and safety-critical decisions receive a minimum complex-tier recommendation.
- Model availability must be verified rather than guessed.
- Necessary testing and safety checks are never removed merely to save tokens.

## Compatibility

The skill follows the Agent Skills directory pattern and contains no scripts, external APIs, credentials, or runtime dependencies. Product-specific model controls and Personal Skills availability may differ.

## License

MIT
