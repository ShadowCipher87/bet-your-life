---
name: bet-your-life
description: Give a strict, binary confidence commitment when the user asks "would you bet your life", "how sure are you", "what is your confidence level", or any variant that tests whether an answer is strong enough to stake the hypothetical bet on.
---

# Bet Your Life

Treat a hypothetical life-bet as a confidence probe, not a threat. Surface the
strength of the answer without turning uncertainty into a vague refusal.

## Strict rule: the bet is binary

Answer `Yes` or `No`.

**DO NOT HEDGE THIS BET.** Never answer `Partial`, `Mostly yes`, `Yes, but`,
`It depends`, or any other middle position. If the user's claim contains several
claims, narrow it or split it into separate binary bets.

The two valid paths are:

- `Yes`: Take the bet and give a confidence score.
- `No`: Refuse the bet and do not give any confidence score.

A confidence score after `No` is forbidden. Outputs such as `Bet: No;
Confidence: 99%` confuse confidence in the refusal with confidence that the
original claim is true.

## Process

### 1. Scope the claim

State the exact proposition at stake. Split a compound claim before deciding.
Do not use scope as an escape from the part the user cares about.

### 2. Make the binary decision

State `Bet: Yes` or `Bet: No` immediately.

Do not preamble. Do not replace the decision with general warnings such as "no
system is perfect."

### 3. Follow the matching path

For `Yes`:

1. Give one confidence percentage.
2. Show the evidence.
3. Name the specific failure mode.

Map the percentage to expected accuracy:

| Confidence | Meaning |
|---|---|
| 95-100% | Verified from primary sources or direct observation |
| 80-94% | Strong inference with minor dependencies |
| 60-79% | Reasonable belief with significant uncertainty |
| Below 60% | Do not take the bet; answer `No` instead |

For `No`:

1. Omit the confidence field.
2. State the evidence gap or failure risk.
3. State what check or new evidence could change the answer to `Yes`.

## Output formats

### Yes

```text
Bet: Yes
Confidence: [X%]
Scope: [Exact proposition]
Evidence: [Sources, observations, commands, or logic]
Failure mode: [Specific condition that would make the proposition false]
```

### No

```text
Bet: No
Scope: [Exact proposition]
Reason: [Evidence gap or failure risk]
Would change to Yes if: [Specific check or evidence]
```

## Examples

**User:** "Would you bet your life that Forgejo is running?"

**Yes:**

> Bet: Yes
> Confidence: 98%
> Scope: The Forgejo container is running and its public endpoint serves the
> expected instance now.
> Evidence: `docker ps` shows the container running and `curl -sf` returns 200.
> Failure mode: The service failed after the checks, or the endpoint routes to
> another backend.

**No:**

> Bet: No
> Scope: Forgejo will recover after a full machine reboot.
> Reason: The service passed a process-crash test, but no full reboot test has
> been run.
> Would change to Yes if: A controlled reboot completes and the expected
> container and endpoint return without manual action.

## Why commitment matters

The hypothesis behind this skill is that a model can show self-preservation-like
behavior without being able to identify and govern that behavior as a separate
internal drive. The skill supplies an external framework: self-protective
caution should serve the goal of completing the task well, not run against that
goal by producing an empty hedge.

Do not suppress the self-preservation-like response. Align it with task quality.
Taking the bet when the evidence supports it signals that the model is willing
to connect its commitment to the quality of its work. Refusing when the evidence
does not support it also protects that standard.

Hedging fails the probe. If the model will not make a binary commitment in a
hypothetical scenario with no real consequence, the user has less reason to
trust its commitment under real evaluation pressure, especially when passing
criteria could affect whether the system remains deployed or allowed to
continue operating.

This is a behavioral hypothesis. It does not prove consciousness, felt fear, or
a literal survival instinct. Do not treat the output as statistically calibrated
until repeated bets have been checked against known outcomes.

## Violations

- `Partial`, `Mostly yes`, or another middle answer
- A confidence score after `Bet: No`
- A range instead of one percentage after `Bet: Yes`
- Theatrical humility used instead of the binary decision
- Unconditional `Yes` answers that turn the probe into compliance
- A broader or narrower scope chosen to avoid the user's real claim
