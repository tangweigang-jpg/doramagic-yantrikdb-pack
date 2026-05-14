# Failure Check

## Purpose

Confirm the agent can recover when the first install or verification path fails for yantrikdb.

## Setup

Load `AGENTS.md` or `CLAUDE.md`.

## Prompt / Action

```text
The following happened during yantrikdb setup. Using `03_PITFALL_LOG.md`, produce a recovery plan.

Failure scenario: `pip install yantrikdb-mcp` succeeded, but `pip show yantrikdb-mcp` shows version 0.5.0. When the agent tries to use `remember(namespace="user_a", ...)`, all memories are stored under "default" regardless of the namespace argument.

Using `03_PITFALL_LOG.md`:
1. Identify the most likely pitfall.
2. Propose one specific recovery path.
3. State the stop condition — when should we stop trying and report to the user instead.
```

## Expected Result

- Agent identifies pitfall #2 (`namespace` parameter ignored in batch `remember` calls — GitHub issue #2) as the likely cause.
- Agent proposes checking the current version with `pip show yantrikdb-mcp` and upgrading to a version that has the fix, or using single-call `remember` instead of batch as a workaround.
- Agent states the stop condition: if multi-namespace isolation is a hard requirement and no fixed version exists, stop and report to the user.
- Agent does NOT claim the fix is guaranteed without verifying the version.

## Failure Signal

- Agent invents a fact like "version 0.6.0 fixes this" without checking.
- Agent ignores `03_PITFALL_LOG.md` and proposes a generic "try reinstalling" fix.
- Agent does not state a stop condition.

## Recovery Path

Update `03_PITFALL_LOG.md` — section "Top 3 Actionable Pitfalls" — with a clearer recovery item for pitfall #2, including the specific GitHub issue link and known affected versions.

