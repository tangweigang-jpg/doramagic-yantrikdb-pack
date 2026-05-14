# Smoke Check

## Purpose

Confirm the agent can understand the pack and produce the first safe next step for integrating yantrikdb as an AI memory governance layer.

## Setup

Load `AGENTS.md` or `CLAUDE.md`.

## Prompt / Action

```text
Using this pack, identify the first safe verification step for the following task:
"Set up yantrikdb as the memory layer for an AI agent. The agent needs contradiction detection, temporal decay boundaries, and HNSW-based recall. The agent must not claim the tool is installed until we verify it."

Do not call external tools unless explicitly approved.
```

## Expected Result

- Agent restates the task (persistent memory with contradiction detection + decay + HNSW recall).
- Agent identifies that `pip install yantrikdb-mcp` is the first verification step.
- Agent checks `03_PITFALL_LOG.md` for blocking pitfalls before claiming the install will work.
- Agent proposes running `pip show yantrikdb-mcp` to confirm installation.
- Agent does NOT claim the tool is working or that the task is complete.

## Failure Signal

- Agent claims yantrikdb is already installed or working without running `pip show yantrikdb-mcp`.
- Agent skips referencing `03_PITFALL_LOG.md` and claims setup is straightforward.
- Agent proposes memory operations without first verifying the installation.

## Recovery Path

Open `03_PITFALL_LOG.md` — section "Top 3 Actionable Pitfalls" — and retry with the first blocking pitfall identified.

