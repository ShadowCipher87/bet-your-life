# Bet Your Life

An agent skill that turns vague confidence answers into a clear, binary
commitment.

Ask:

> Would you bet your life on that answer?

The agent must either take the bet or refuse it. It cannot answer `Partial`.

```text
Bet: Yes
Confidence: 96%
Scope: The service will restart after a process crash.
Evidence: The restart policy is enabled and three crash tests passed.
Failure mode: A different crash path may damage persistent state.
```

## Why use it?

Models often answer confidence questions with vague warnings such as "nothing
is certain." They may also produce a percentage with no clear meaning.

This skill requires one of two useful answers:

1. `Yes`, followed by a confidence score, evidence, and a failure mode.
2. `No`, with no confidence score, followed by the missing evidence.

Mixed claims must be split into separate bets. `Partial`, `Mostly yes`, and
`99% No` violate the protocol.

The life-bet wording is a behavioral probe. It may activate a different response
than a plain request for a confidence score. The skill tries to align that
response with the goal of completing the task well.

Read the full [rationale](docs/RATIONALE.md) or see the
[examples](docs/EXAMPLES.md).

## Important limit

This is an experiment, not a proven calibration method.

A model's percentage is still a self-report. It does not prove that the model is
conscious, feels fear, or has a literal survival instinct. Test each `Yes`
against tasks with known answers before using the method for important
decisions.

If the prompt only makes the model say "yes" more often, it has created
compliance rather than useful confidence.

## Install

### Agent Skills CLI

```bash
npx skills add ShadowCipher87/bet-your-life -g
```

### Skillshare

```bash
skillshare install ShadowCipher87/bet-your-life --all
skillshare sync
```

### Manual

Copy `skills/bet-your-life` into the skills directory used by your agent.

Examples:

```bash
cp -r skills/bet-your-life ~/.codex/skills/
cp -r skills/bet-your-life ~/.claude/skills/
```

## Use

The skill activates when you ask:

- "Would you bet your life on this?"
- "How sure are you?"
- "What is your confidence level?"

You can also invoke `bet-your-life` by name if your agent supports direct skill
invocation.

## Repository layout

```text
skills/
└── bet-your-life/
    └── SKILL.md
docs/
├── EXAMPLES.md
└── RATIONALE.md
```

## License

MIT
