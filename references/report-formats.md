# Report Format Templates

Use the template matching the selected evaluation mode. Keep reports evidence-based and concise.

## Single-Model Report

```markdown
## Skill Evaluation Report

### [Skill Name]

**Weighted Score: X.X / 10 (Grade X)**

| Dimension | Score | Evidence |
|-----------|-------|----------|
| D1. Metadata Quality | X/10 | ... |
| D2. Execution Guidance Clarity | X/10 | ... |
| D3. Domain Knowledge Density | X/10 | ... |
| D4. Workflow Completeness | X/10 | ... |
| D5. Input/Output Clarity | X/10 | ... |
| D6. Resource Utilization | X/10 | ... |
| D7. Writing Quality | X/10 | ... |
| D8. Scope & Focus | X/10 | ... |

#### Problems And Suggestions
1. **[Dimension]**: [problem] -> [impact] -> [suggestion]

---
```

## Native Multi-Model Report

```markdown
## Skill Evaluation Report (Native Multi-Model Cross-Validation)

### [Skill Name]

> Arbiter: [current Agent or native model] | Evaluators: [native model A], [native model B], [native model C]

#### Independent Evaluations

##### [Evaluator A]
| Dimension | Score | Evidence |
|-----------|-------|----------|
| D1. Metadata Quality | X/10 | ... |
| D2. Execution Guidance Clarity | X/10 | ... |
| D3. Domain Knowledge Density | X/10 | ... |
| D4. Workflow Completeness | X/10 | ... |
| D5. Input/Output Clarity | X/10 | ... |
| D6. Resource Utilization | X/10 | ... |
| D7. Writing Quality | X/10 | ... |
| D8. Scope & Focus | X/10 | ... |
| **Weighted Score** | **X.X/10 (Grade X)** | |

##### [Evaluator B]
[Same format]

#### Peer Review Highlights

| Dimension | Disagreement | Evidence Summary |
|-----------|--------------|------------------|
| [Dimension] | [Evaluator A X] vs [Evaluator B Y] | ... |

> Significant disagreements: N dimensions. Broadly consistent: M dimensions.

#### Final Arbitration

**Final Weighted Score: X.X / 10 (Grade X)**

| Dimension | Final Score | Consensus | Arbitration Rationale |
|-----------|-------------|-----------|-----------------------|
| D1. Metadata Quality | X/10 | Consistent / Majority / Arbitrated | ... |
| D2. Execution Guidance Clarity | X/10 | Consistent / Majority / Arbitrated | ... |
| D3. Domain Knowledge Density | X/10 | Consistent / Majority / Arbitrated | ... |
| D4. Workflow Completeness | X/10 | Consistent / Majority / Arbitrated | ... |
| D5. Input/Output Clarity | X/10 | Consistent / Majority / Arbitrated | ... |
| D6. Resource Utilization | X/10 | Consistent / Majority / Arbitrated | ... |
| D7. Writing Quality | X/10 | Consistent / Majority / Arbitrated | ... |
| D8. Scope & Focus | X/10 | Consistent / Majority / Arbitrated | ... |

#### Problems And Suggestions
1. **[Dimension]** (Consensus: [type]): [problem] -> [impact] -> [suggestion]

---
```

## Multi-Perspective Report

```markdown
## Skill Evaluation Report (Multi-Perspective Cross-Validation)

### [Skill Name]

> Strategy: Serial multi-perspective | Perspectives: Strict / Pragmatic / Expert

#### Perspective Evaluations

##### Strict Reviewer
| Dimension | Score | Evidence |
|-----------|-------|----------|
| D1. Metadata Quality | X/10 | ... |
| D2. Execution Guidance Clarity | X/10 | ... |
| D3. Domain Knowledge Density | X/10 | ... |
| D4. Workflow Completeness | X/10 | ... |
| D5. Input/Output Clarity | X/10 | ... |
| D6. Resource Utilization | X/10 | ... |
| D7. Writing Quality | X/10 | ... |
| D8. Scope & Focus | X/10 | ... |
| **Weighted Score** | **X.X/10 (Grade X)** | |

##### Pragmatic Reviewer
[Same format]

##### Expert Reviewer
[Same format]

#### Cross-Review Highlights

| Dimension | Disagreement | Evidence Summary |
|-----------|--------------|------------------|
| [Dimension] | Strict X / Pragmatic Y / Expert Z | ... |

> Significant disagreements: N dimensions. Broadly consistent: M dimensions.

#### Final Arbitration

**Final Weighted Score: X.X / 10 (Grade X)**

| Dimension | Final Score | Consensus | Arbitration Rationale |
|-----------|-------------|-----------|-----------------------|
| D1. Metadata Quality | X/10 | Consistent / Majority / Arbitrated | ... |
| D2. Execution Guidance Clarity | X/10 | Consistent / Majority / Arbitrated | ... |
| D3. Domain Knowledge Density | X/10 | Consistent / Majority / Arbitrated | ... |
| D4. Workflow Completeness | X/10 | Consistent / Majority / Arbitrated | ... |
| D5. Input/Output Clarity | X/10 | Consistent / Majority / Arbitrated | ... |
| D6. Resource Utilization | X/10 | Consistent / Majority / Arbitrated | ... |
| D7. Writing Quality | X/10 | Consistent / Majority / Arbitrated | ... |
| D8. Scope & Focus | X/10 | Consistent / Majority / Arbitrated | ... |

#### Problems And Suggestions
1. **[Dimension]** (Consensus: [type]): [problem] -> [impact] -> [suggestion]

---
```

## Multi-Skill Comparison Section

Append this section after all individual reports when evaluating 2 or more Skills.

```markdown
### Comparison

| Dimension | Skill A | Skill B | Skill C |
|-----------|---------|---------|---------|
| D1. Metadata Quality | X | X | X |
| D2. Execution Guidance Clarity | X | X | X |
| D3. Domain Knowledge Density | X | X | X |
| D4. Workflow Completeness | X | X | X |
| D5. Input/Output Clarity | X | X | X |
| D6. Resource Utilization | X | X | X |
| D7. Writing Quality | X | X | X |
| D8. Scope & Focus | X | X | X |
| Weighted Score | X.X / Grade | X.X / Grade | X.X / Grade |

#### Strengths And Weaknesses
- **Skill A**: ...
- **Skill B**: ...

#### Shared Lessons
- ...

#### Ranking
1. **[Skill]**: [one-sentence reason]
2. **[Skill]**: [one-sentence reason]
```
