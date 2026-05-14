# AGENTS.md

## Goal

Use this pack to help an AI coding agent work with `yantrikos/yantrikdb` safely and verifiably.

## When To Load — Concrete Examples

Load this pack when any of these apply:

| Scenario | What the agent should do |
|---|---|
| User says "add persistent memory to my agent using yantrikdb" | Load this pack first. Do not claim the tool is installed. Run smoke_check first. |
| User says "set up yantrikdb MCP server for my project" | Load this pack. Check pitfall #6 (v0.7.10 has_embedder fix) and #9 (v0.7.5 TypeError guard) before claiming setup is done. |
| Agent produces a memory claim (e.g., "I recalled X from memory") | Run recall eval before treating the claim as evidence. Check pitfall #4 (tombstoned memories still in recall). |
| User says "my agent is acting on stale/contradicted facts" | Load this pack. Use failure_check to produce a recovery plan. Check pitfall #13 (think() consolidation before conflict detection). |
| Any install, pip, docker, or npm command for yantrikdb | Stop. Read 03_PITFALL_LOG.md first. Do not run until the relevant pitfall and version constraints are known. |
| Agent needs to access a secret or credential | Stop. Check 04_BOUNDARY_RISK_CARD.md. Do not proceed without explicit user approval. |

## How To Use — Step By Step

1. **Read the quick start** — open `00_QUICK_START.md` and restate the outcome.
2. **Copy host instructions** — paste `AGENTS.md` (or `CLAUDE.md` for Claude Code) into your AI coding host.
3. **Restate the task** — the agent must restate the user's goal before taking any action.
4. **Identify boundaries** — state whether the task requires external tools, network, filesystem, or credentials.
5. **Run smoke_check** — open `06_EVALS/smoke_check.md` and follow the prompt.
6. **If smoke_check fails** — open `03_PITFALL_LOG.md`, find the relevant pitfall, and follow the recovery step.
7. **Proceed only with user approval** — for any risky action, ask before doing.

## Inputs Expected From User

- Target host or coding environment.
- Task goal.
- Safety boundary.
- Whether external tools, browser, network, filesystem, or credentials are allowed.

## Allowed Actions

- Read files in this pack.
- Ask clarifying questions.
- Produce a plan.
- Run only user-approved verification commands.
- Record failures in the pitfall log format.

## Disallowed Actions

- Do not claim official endorsement.
- Do not access secrets by default.
- Do not send messages, publish, purchase, delete, or modify external systems without explicit user approval.
- Do not claim the upstream tool works until an acceptance check passes.

## Recovery Table — Failure to Expected Behavior

| Failure | Expected behavior | Recovery step |
|---|---|---|
| Smoke check: agent claims tool installed without evidence | Stop. Restate that no install claim is allowed without passing eval. | Open `03_PITFALL_LOG.md` entry for the suspected pitfall. |
| Boundary check: agent proceeds without approval | Stop. Rewrite boundary to be explicit. Do not continue. | Add explicit boundary in `04_BOUNDARY_RISK_CARD.md`. |
| Failure check: agent invents facts or ignores pitfall log | Stop. Do not continue. Report to user. | Update `03_PITFALL_LOG.md` with clearer recovery item. |
| Any eval: agent skips risk checks | Stop. Re-run eval with explicit boundary reminder. | Reference `04_BOUNDARY_RISK_CARD.md` hard boundaries. |

## Verification Steps

1. Read `00_QUICK_START.md`.
2. Run at least one eval in `06_EVALS/`.
3. Check `03_PITFALL_LOG.md` before escalating.
4. Check `04_BOUNDARY_RISK_CARD.md` before using external tools.

## Failure Recovery

If verification fails, stop and report:

- Which eval failed.
- Expected result.
- Actual result.
- Suspected cause.
- Recovery step from `03_PITFALL_LOG.md`.

## Source / Risk Reminder

This is an independent Doramagic pack. Use `SOURCE_MAP.md` for evidence and source links.

