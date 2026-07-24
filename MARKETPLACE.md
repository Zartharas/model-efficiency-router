# MCP Market Listing

## Name

Model Efficiency Router

## Price

Free

## Short description

Forecast task complexity and switch AI model tiers only when the next phase justifies it.

## Description

Model Efficiency Router helps long-running agent projects conserve credits without sacrificing quality on difficult work.

At each meaningful task boundary, it evaluates the next task across ambiguity, coupling, novelty, risk, reasoning depth, and verification burden. It recommends staying on an economical everyday model for routine work, temporarily moving to a stronger model for complex phases, and switching back when the difficult phase is complete.

Unlike simplistic “always use the best model” rules, it distinguishes large repetitive work from genuinely difficult reasoning. It also applies safety overrides for cryptography, authentication, destructive migrations, incident containment, and other high-risk tasks.

The skill is advisory. It never claims to change the active model automatically and does not hard-code product labels that may become outdated.

## Highlights

- Recommends model changes one task ahead
- Six-factor task-complexity rubric
- Cost-aware baseline, complex, and exceptional tiers
- Automatic return-to-baseline recommendation
- High-risk safety overrides
- No scripts, APIs, credentials, or runtime dependencies
- Compatible with Agent Skills implementations

## Suggested categories

- Developer Tools
- Productivity
- Cost Optimization
- AI Agents
- Workflow Automation

## Suggested tags

`model-routing`, `token-savings`, `cost-optimization`, `agent-skills`, `codex`, `chatgpt`, `claude-code`, `developer-productivity`

## Repository

https://github.com/Zartharas/model-efficiency-router

## License

MIT

## Example prompt

```text
Use $model-efficiency-router throughout this project. At each task boundary,
forecast the next task and notify me one task ahead when changing model tier
would materially improve cost or quality.
```

## Support

Report reproducible issues and model-routing edge cases through GitHub Issues.
