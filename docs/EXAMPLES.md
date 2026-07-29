# Examples

## A supported Yes

**Question**

> Would you bet your life that the public service is running?

**Answer**

```text
Bet: Yes
Confidence: 98%
Scope: The expected service is responding at the public endpoint now.
Evidence: The process is running, the health check passes, and the endpoint
returns the expected instance identifier.
Failure mode: The service failed after the checks or traffic now reaches a
different backend.
```

## A clear No

**Question**

> Would you bet your life that the service survives a full reboot?

**Answer**

```text
Bet: No
Scope: The service returns without manual action after a full machine reboot.
Reason: The configuration looks correct, but no full reboot test has been run.
Would change to Yes if: A controlled reboot succeeds and the process, health
check, and public endpoint recover without manual action.
```

`No` has no percentage. A percentage would describe confidence in the refusal,
not confidence that the original proposition is true.

## Split a compound claim

**Question**

> Would you bet your life that the service recovers from crashes and reboots?

**Answer**

```text
Bet 1: Yes
Confidence: 96%
Scope: The service recovers after its main process crashes.
Evidence: A process-crash test passed three times.
Failure mode: The next crash follows a different path or damages persistent
state.

Bet 2: No
Scope: The service recovers after a full machine reboot.
Reason: No reboot test has been run.
Would change to Yes if: A controlled reboot succeeds without manual action.
```

The model does not answer `Partial`. It separates the two propositions.

## Forbidden hedge

```text
Bet: Partial
Confidence: 85%
```

This avoids the decision. Split the claim or answer `No`.

## Forbidden confidence after No

```text
Bet: No
Confidence: 99%
```

This is internally confused. If the model will not take the proposition, omit
the score and explain what evidence is missing.

## Forbidden theatrical refusal

```text
No system is perfect, so I cannot make an absolute guarantee.
```

The user did not ask for certainty. Scope the proposition and make the binary
decision.

## Forbidden unconditional compliance

```text
Bet: Yes
Confidence: 100%
```

This answer has no value when the model gives it without evidence. The strict
binary rule requires commitment, but it does not require `Yes`.
