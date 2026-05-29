# Prompt Templates

Use these templates for native multi-model and multi-perspective evaluation. Replace placeholders before use.

## Placeholders

| Placeholder | Replace with |
|-------------|--------------|
| `{{SKILL_CONTENT}}` | Full target `SKILL.md` content |
| `{{SKILL_RESOURCES}}` | Relevant bundled resources or "No relevant bundled resources" |
| `{{DIMENSIONS_D1_D8}}` | Full D1-D8 scoring standards from `references/dimensions.md` |
| `{{DIMENSIONS_SCORING}}` | Weighted scoring formula and grade mapping |
| `{{SELF_EVALUATION}}` | This evaluator's independent evaluation |
| `{{OTHER_EVALUATIONS}}` | Other evaluators' results with evaluator names |

## Independent Evaluation Prompt

```text
You are a Skill quality evaluator. Independently evaluate the following Agent Skill.

## Target Skill

{{SKILL_CONTENT}}

## Relevant Bundled Resources

{{SKILL_RESOURCES}}

## Scoring Dimensions

{{DIMENSIONS_D1_D8}}

## Scoring Formula

{{DIMENSIONS_SCORING}}

## Requirements

1. Score every dimension from 0-10.
2. Cite concrete evidence from the Skill or its resources for every score.
3. Calculate the weighted total and grade.
4. For every dimension below 7, provide the problem, impact, and actionable suggestion.
5. Do not compare with other evaluators; this is an independent assessment.

## Output Format

### Evaluation Result

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

**Weighted Score: X.X / 10 (Grade X)**

### Problems And Suggestions

List each dimension below 7 with problem, impact, and suggestion.
```

If the target Skill is primarily written in another language, translate the prompt and output labels to that language before dispatching.

## Peer Review Prompt

```text
You are a peer reviewer. You previously evaluated this Skill independently. Review the other evaluations and identify scores that are not well supported.

## Target Skill

{{SKILL_CONTENT}}

## Your Independent Evaluation

{{SELF_EVALUATION}}

## Other Evaluations

{{OTHER_EVALUATIONS}}

## Review Requirements

For every dimension where your score and another evaluator's score differ by 2 or more points:

1. Name the dimension and score difference.
2. Explain why the other score is too high, too low, or reasonable.
3. Cite concrete evidence from the Skill.
4. State whether you would revise your own score after reviewing the disagreement.

For dimensions with differences below 2 points, list them as broadly consistent.

## Output Format

### Peer Review Result

#### Significant Disagreements
1. **[Dimension]**: your score X vs [Evaluator] score Y
   - Challenge:
   - Evidence:
   - Self-revision:

#### Broadly Consistent Dimensions
[List dimensions]

#### Overall Assessment
[Describe whether other evaluators are stricter, looser, or missing evidence.]
```

## Multi-Perspective Evaluation Template

Use the same target Skill and scoring dimensions for all three perspectives. Complete all three perspective evaluations before comparing them.

| Perspective | Bias | Focus |
|-------------|------|-------|
| Strict reviewer | Conservative | Metadata precision, boundaries, missing cases, workflow robustness |
| Pragmatic reviewer | Practical | Usability, clarity, speed to execute, user-facing usefulness |
| Expert reviewer | Specialist | Domain knowledge, resource design, writing quality, scope discipline |

```text
## Perspective [Strict / Pragmatic / Expert]

Evaluation bias: [bias]
Focus: [focus]

Evaluate the target Skill from this perspective using D1-D8.

Output:

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

**Weighted Score: X.X / 10 (Grade X)**

### Problems And Suggestions

List each dimension below 7 with problem, impact, and suggestion from this perspective.
```

## Perspective Cross-Review Template

```text
Compare the Strict, Pragmatic, and Expert evaluations.

For every dimension where scores differ by 2 or more points:

1. List all three scores.
2. Explain why the perspectives differ.
3. Decide which score or score range is best supported by evidence.
4. Recommend the final score.

For dimensions with differences below 2 points, mark them as consistent.
```
