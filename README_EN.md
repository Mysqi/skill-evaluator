# skill-evaluator

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) | [中文](README.md)

An AI Agent Skill for evaluating the quality of other Agent Skills. It scores Skills across 8 weighted dimensions, identifies weaknesses, provides actionable suggestions, and supports side-by-side comparison of multiple Skills.

Version 3.0.0 removes external model API execution. Multi-model evaluation uses only models natively supported by the current Agent platform. If native multi-model execution is unavailable, the Skill falls back to Strict, Pragmatic, and Expert perspectives.

## Features

- **Eight-dimension scoring**: 0-10 for each dimension with weighted total
- **Grade mapping**: S/A/B/C/D grade from the weighted score
- **Actionable feedback**: problem, impact, and suggestion for weak dimensions
- **Multi-Skill comparison**: score table, strengths, weaknesses, lessons, and ranking
- **Native multi-model cross-validation**: native models evaluate independently, peer-review, then arbitrate
- **Multi-perspective fallback**: Strict, Pragmatic, and Expert reviewers when native multi-model execution is unavailable
- **No external credentials**: no credential setup, no credential persistence, no external model API calls

## Evaluation Dimensions

| Dimension | Weight | Description |
|-----------|--------|-------------|
| D1. Metadata Quality | 15% | Whether `name` and `description` are clear, accurate, and triggerable |
| D2. Execution Guidance Clarity | 15% | Whether the Agent knows what to do after loading the Skill |
| D3. Domain Knowledge Density | 15% | Whether the Skill embeds expertise unavailable to a general Agent |
| D4. Workflow Completeness | 15% | Whether it defines an end-to-end workflow with branches and failure handling |
| D5. Input/Output Clarity | 10% | Whether users know what to provide and what to expect |
| D6. Resource Utilization | 10% | Whether `references/`, `scripts/`, and `assets/` are used appropriately |
| D7. Writing Quality | 10% | Whether structure and wording are easy for an Agent to execute |
| D8. Scope & Focus | 10% | Whether it focuses on one coherent problem area |

## Grade Scale

| Score | Grade | Meaning |
|-------|-------|---------|
| 9.0-10 | S | Benchmark-level |
| 7.5-8.9 | A | Excellent and ready to use |
| 6.0-7.4 | B | Usable with clear room for improvement |
| 4.0-5.9 | C | Weak and needs significant revision |
| 0-3.9 | D | Fundamental issues; consider redesigning |

## Installation

```bash
git clone https://github.com/sunxingboo/skill-evaluator.git ~/.claude/skills/skill-evaluator
```

You can also copy `SKILL.md` and the `references/` directory into your Agent Skill directory.

## Usage Examples

Evaluate a single Skill:

```text
Evaluate my-skill
```

Compare multiple Skills:

```text
Compare skill-a and skill-b. Which is better designed?
```

Evaluate by path:

```text
Evaluate ~/projects/my-skill/SKILL.md
```

Use cross-validation:

```text
Evaluate my-skill with multi-model cross-validation
```

Use multi-perspective mode:

```text
Evaluate my-skill with multi-perspective review
```

## Execution Strategies

### Strategy A: Native Multi-Model

When the current Agent platform supports multiple native models:

1. Each model evaluates the target Skill independently.
2. Each model reviews the other evaluations.
3. The main Agent arbitrates disagreements and final scores.

### Strategy B: Serial Multi-Perspective

When native multi-model execution is unavailable, insufficient, or explicitly not needed:

1. The Strict reviewer focuses on norms, boundaries, and omissions.
2. The Pragmatic reviewer focuses on usability, clarity, and execution experience.
3. The Expert reviewer focuses on depth, resource design, and scope control.
4. The final pass compares disagreements and arbitrates.

## Impact Of Removing External APIs

Positive effects:

- No credential setup is required.
- No credentials are stored.
- The Skill is lighter and easier to audit.
- Execution is more stable because it does not depend on a separate external service.

Tradeoffs:

- The Skill no longer calls additional models through an external API.
- If the current environment lacks native multi-model support, cross-validation falls back to single-model multi-perspective review.
- Result diversity may be lower, but maintainability and safety improve.

## Directory Layout

```text
skill-evaluator/
├── SKILL.md
├── references/
│   ├── dimensions.md
│   ├── prompts.md
│   └── report-formats.md
├── README.md
├── README_EN.md
├── CHANGELOG.md
└── LICENSE
```
