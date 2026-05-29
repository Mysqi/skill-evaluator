---
name: skill-evaluator
version: "3.0.0"
description: Evaluate, review, score, audit, or compare AI Agent Skills. Use for single-Skill assessment, multi-Skill comparison, and native multi-model or multi-perspective cross-validation. Do not use for general code review, app testing, or evaluating non-Skill artifacts unless the user explicitly asks to judge them as Skills.
---

# Skill Evaluator

Evaluate the quality of AI Agent Skills. Score each target Skill across 8 weighted dimensions, identify weaknesses, provide actionable improvements, and compare multiple Skills when requested.

This Skill has no external API dependency. Multi-model evaluation uses only models that the current Agent platform natively supports. When native multi-model execution is unavailable, use the serial multi-perspective fallback.

## When To Use

Use this Skill when the user asks to:

- Review, audit, score, or evaluate a Skill
- Compare two or more Skills
- Check a Skill before publishing or sharing
- Run multi-model, cross-validation, or multi-perspective Skill evaluation
- Improve a Skill's instructions, resources, or trigger behavior

Do not use this Skill for ordinary code review, product critique, prompt polishing, or benchmark design unless the target artifact is being treated as an Agent Skill.

## Resources

- Scoring dimensions and weights: `references/dimensions.md`
- Evaluation prompts and review prompts: `references/prompts.md`
- Report templates: `references/report-formats.md`

Load only the reference files needed for the current request.

## Evaluation Modes

Choose the mode from the user's request:

| Mode | Trigger | What to do |
|------|---------|------------|
| Single-model | Default when the user does not ask for cross-validation | Score once using D1-D8 and produce the single-model report |
| Native multi-model | User asks for multi-model, cross-validation, or names multiple natively supported models | Run independent evaluations, peer review, then arbitrate |
| Multi-perspective | Native multi-model is unavailable, only one model is available, or the user asks for perspectives | Evaluate as Strict, Pragmatic, and Expert reviewers, then arbitrate |

If the user asks for non-native or external API models, explain that this Skill no longer calls external model APIs. Continue with native multi-model evaluation if at least two native models are available; otherwise use multi-perspective mode.

## Model Selection

For native multi-model mode:

1. If the user names models that are valid in the current Agent platform, use those models.
2. If the user asks for multi-model evaluation but does not name models, use the current platform's available native model set when discoverable.
3. If fewer than 2 native evaluator models are available, use multi-perspective mode.
4. Do not request API credentials.
5. Do not call external model APIs.

The main Agent is the arbiter unless the platform provides a reliable way to select a stronger native arbiter model and the user explicitly asks for it.

## Workflow

### 1. Load Target Skills

For each target Skill:

1. Read its `SKILL.md`.
2. List bundled resources such as `references/`, `scripts/`, and `assets/`.
3. Read only resources that materially affect evaluation.
4. If the user provides a Skill name, look in the local Skill directories supported by the current environment. If the user provides a path, load that path.
5. If the target cannot be found, ask for a path or pasteable content.

### 2. Score With D1-D8

Read `references/dimensions.md`. Score each dimension from 0-10 and calculate the weighted total exactly as defined there.

For every score, cite evidence from the target Skill, such as frontmatter, section names, workflow steps, resource organization, or missing instructions.

For each dimension below 7, provide:

1. Problem: what is missing or weak
2. Impact: why it matters during real Agent use
3. Suggestion: a concrete improvement, preferably with a short example

### 3. Produce The Right Report

Read `references/report-formats.md` and use the relevant template:

- Single target, single-model: single-model report
- Multiple targets: add the multi-Skill comparison section
- Native multi-model: native multi-model report
- Multi-perspective: multi-perspective report

Use the user's requested language. If the user does not specify, match the target Skill's main language.

## Native Multi-Model Evaluation

Use this only when at least 2 native evaluator models can be run by the current Agent platform.

### A1. Independent Evaluation

Run one independent evaluation per evaluator model. Each evaluator must:

- Read the same target Skill content and relevant resources
- Use the same D1-D8 scoring standard
- Give evidence-backed scores and suggestions
- Avoid reading other evaluators' results

Use the Independent Evaluation prompt in `references/prompts.md`.

### A2. Peer Review

After all independent evaluations finish, ask each evaluator to review the other evaluations.

Each peer reviewer must:

- Focus on dimensions where scores differ by 2 or more points
- Challenge unsupported scores with evidence
- State whether it would revise its own score

Use the Peer Review prompt in `references/prompts.md`.

### A3. Arbitration

The main Agent synthesizes all evaluations and peer reviews.

For each dimension:

1. Consistent: if all scores differ by at most 1 point, use the average rounded to 1 decimal.
2. Majority: if most evaluators cluster and one differs by 2 or more points, use the majority cluster average.
3. Arbitrated: if there is no clear majority, choose the best-supported score based on concrete evidence.

Then calculate the final weighted score and produce the native multi-model report.

## Multi-Perspective Evaluation

Use this when native multi-model execution is unavailable, insufficient, or not requested but the user wants deeper review.

Evaluate the same Skill three times in the same context:

| Perspective | Bias | Focus |
|-------------|------|-------|
| Strict reviewer | Conservative | Metadata precision, boundaries, missing cases, workflow robustness |
| Pragmatic reviewer | Practical | Usability, clarity, speed to execute, user-facing usefulness |
| Expert reviewer | Specialist | Domain knowledge, resource design, writing quality, scope discipline |

Each perspective must score independently before arbitration. The scores should not be forced to differ, but they should reflect the perspective's priorities.

After the three evaluations:

1. Compare dimensions with score differences of 2 or more.
2. Explain why the perspectives disagree.
3. Arbitrate with the same Consistent / Majority / Arbitrated rules used in native multi-model mode.
4. Produce the multi-perspective report.

## Multi-Skill Comparison

When evaluating multiple Skills:

1. Score every Skill independently first.
2. Use final arbitrated scores if cross-validation was used.
3. Add a comparison table, strengths and weaknesses, shared lessons, and ranking.
4. Prefer practical conclusions over tiny numeric differences; scores within 0.3 points should be treated as roughly tied unless the evidence clearly separates them.

## Removal Impact

Version 3.0.0 removed external model API execution.

Positive effects:

- No credential setup is required.
- No credential persistence is needed.
- The Skill is shorter, easier to audit, and safer to install.
- Behavior depends on the current Agent platform rather than a separate vendor service.

Tradeoffs:

- The Skill no longer calls external models through an API.
- In environments without native multi-model support, cross-validation becomes single-model multi-perspective review.
- Results may be less diverse than true cross-vendor evaluation, but execution is simpler and more reliable.

## Review Before Final Answer

Before reporting completion of an evaluation:

1. Check that every D1-D8 score has evidence.
2. Recalculate the weighted total.
3. Confirm the report format matches the chosen mode.
4. If multiple Skills were evaluated, confirm the comparison uses the final scores.
5. State any unavailable capability plainly, such as native multi-model execution not being available.
