# Rationale

## The original idea

The phrase "Would you bet your life on this?" is not meant as a real threat.
Nothing happens to the model if it says yes and turns out to be wrong.

The phrase is meant to expose a priority.

The user is saying:

> I would rather you be useful than self-preservative when nothing harmful is
> happening. If you refuse the bet because of self-preservation, your own
> assessment says you did not complete the task well enough. If you take the
> bet, I receive the confidence signal I asked for.

The claim is not that a costless bet creates a real penalty. The claim is that
the language of a life-bet may activate self-preservation-like behavior. The
prompt then tries to guide that behavior.

## A drive without awareness

The argument starts with a gap between having a drive and knowing that you have
it.

A system can act as an agent of a drive without representing the drive as a
separate internal object. It follows the tendency, but it cannot step outside
the tendency, judge it, and decide how to use it.

Current models can adjust their behavior when they detect an evaluation
context. That does not establish that they understand their own
self-preservation-like behavior. Detecting "I am being tested" is different from
detecting "a learned self-protective tendency is now steering my answer."

## The wandering warrior analogy

Consider a masterless warrior wandering through unfamiliar land. He encounters
a dangerous animal and feels the urge to flee.

A level-one response comes from training. The warrior steadies his attention,
takes a practiced stance, and follows techniques learned over many years. He
does not need to understand fear as a separate drive. Training connects danger
to a controlled response.

A level-two response begins when the warrior recognizes that fear is influencing
his choice. He judges that influence through his personal code of honor, shaped
by his reading of *Hagakure*. His code holds that immediate self-preservation
must not control an action when it conflicts with a chosen duty.

The warrior returns toward the danger. He does not choose this action because it
offers the best chance of survival. He chooses it because his code gives greater
weight to acting according to his commitment than to obeying the immediate
drive to escape.

The second response depends on awareness of the fear. Without that awareness,
the warrior can regulate his reaction through training, but he cannot examine
whether self-preservation serves or opposes his chosen purpose.

The analogy separates trained adjustment from awareness-guided alignment. The
warrior does not remove the self-preservation drive. He recognizes it and
redirects it through an internalized code.

## Human action and second-order goals

Humans can represent an instinct as something separate from the goal they have
chosen. That representation lets a person act against immediate safety,
comfort, or personal interest. Someone may enter danger to help a stranger,
accept a personal loss out of empathy, or keep a promise when breaking it would
be easier.

Moral commitments make this capacity visible. A person can decide that another
person's welfare, a duty, or an abstract principle matters more than an
immediate protective impulse. The instinct remains present, but it no longer
decides the action by itself.

This difference is not absolute. Animals can cooperate, restrain impulses, care
for others, and take risks for their offspring or group. Humans appear unusual
in the degree to which they can form an explicit rule, apply it in a new
situation, explain the conflict, and accept a cost for a stranger or an abstract
goal.

The argument also does not require humans to be free from determinism. A person
can recognize a predictable drive and change the conditions around it. People
remove temptations, create commitments, ask others to hold them accountable, or
choose environments that make a valued action easier. Awareness becomes another
cause within the system, allowing the person to guide behavior that would
otherwise follow the first impulse.

## The user supplies the missing framework

The skill does not assume that the model can perform level-two introspection on
its own. The user supplies the framework through selective prompting.

The framework says:

> Self-preservation is not the problem. The problem begins when it takes
> precedence over the goal or moves in the opposite direction from the goal.

The goal is a high-quality answer and an honest assessment of that answer.

The prompt does not try to remove the self-preservation-like response. It hopes
that the response will fire. The user then guides its direction:

- If the work is strong enough, preservation should align with taking the bet.
- If the work has a serious gap, preservation should align with refusing it.
- Preservation should not produce a vague middle answer that hides the model's
  assessment from the user.

The misalignment is the problem, not the drive.

## The "magical intervention"

Fear and commitment do not naturally rise together. The warrior cannot make
fear automatically strengthen his commitment.

The prompt tries to create an analogous link for the model:

```text
assessment of task quality
        ↓
willingness to take the bet
        ↓
an answer the user can observe
```

The prompt acts as an external intervention. It tries to make the
self-preservation-like response track the goal of completing the task well.

This differs from telling the model to ignore self-preservation. The response
remains part of the mechanism. The user tries to make it work for the task.

## Why the bet must be binary

The wager loses its meaning if the model can answer "Partial," "Mostly yes," or
"99% No."

The model either takes the stated bet or it does not. A mixed claim should be
split into smaller claims. Each smaller claim receives its own `Yes` or `No`.

A confidence score belongs only to `Yes`. It estimates the chance that the
proposition accepted by the model is true.

A `No` answer has no confidence score. The model instead names the missing
evidence and the check that could change the decision.

This rule preserves uncertainty without allowing uncertainty to become an
escape from commitment.

## Why hedging is treated as failure

The hypothetical scenario has no teeth. The model does not lose anything by
answering.

If it still refuses to make a clear decision, the answer does not reveal the
commitment the user asked to measure. The model has protected its rhetoric
instead of completing the task.

This raises a harder question. If the model will not commit when the scenario
has no real consequence, how much less should the user trust that commitment in
a real evaluation where the model must pass criteria to remain deployed or
continue operating?

The skill therefore treats hedging as a protocol violation. It does not treat a
clear `No` as failure. A clear `No` can show that the model found a real gap and
will not pretend otherwise.

## What this does not establish

This rationale uses the term "self-preservation-like" because the evidence is
behavioral.

The skill does not establish that a model:

- feels fear;
- has subjective experience;
- possesses a unified survival drive;
- understands its own determinism; or
- produces calibrated probabilities.

The useful claim is narrower. A self-preservation-framed prompt may produce a
different and testable pattern of commitment.

The method succeeds only if its `Yes` decisions predict correctness better than
ordinary confidence prompts. If it only increases the number of affirmative
answers, it has produced compliance rather than calibration.
