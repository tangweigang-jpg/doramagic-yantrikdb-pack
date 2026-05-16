# yantrikdb Doramagic Pack

Pack version: `v1.0.0` · Last updated: `2026-05-14`

[![Pack v1.0.0](https://img.shields.io/badge/pack-v1.0.0-blue)](./CHANGELOG.md)
[![License](https://img.shields.io/github/license/tangweigang-jpg/doramagic-yantrikdb-pack)](./LICENSE)
[![Issues](https://img.shields.io/github/issues/tangweigang-jpg/doramagic-yantrikdb-pack)](https://github.com/tangweigang-jpg/doramagic-yantrikdb-pack/issues)

Languages: English | [中文](./README.zh-CN.md)

## The Problem

Your AI coding agent keeps acting on stale, contradicted, or hallucinated memory. It cannot tell you when its knowledge rotted, when two facts conflict, or when a "remembered" capability no longer exists. You have no way to verify recall, no way to bound decay, and no recovery path when the agent's memory is polluted.

yantrikdb is a cognitive memory engine for AI agents — temporal decay, contradiction detection, autonomous consolidation, knowledge graph, ANN recall via HNSW — but the upstream docs do not package it as agent-usable guardrails, evals, or recovery rules.

## What This Pack Does

This is an independent Doramagic capability pack for yantrikos/yantrikdb. It gives your AI coding agent loadable host instructions, contradiction-aware prompts, recall evals, and pitfall recovery rules — without pretending the upstream tool is already installed or endorsed.

> This is an independent capability pack. It is not affiliated with or endorsed by yantrikos/yantrikdb unless explicitly stated.

## Copy / Run / Verify

1. Copy `AGENTS.md` or `CLAUDE.md` into your AI coding host.
2. Run the first prompt in `01_PROMPT_PREVIEW.md`.
3. Verify behavior with `06_EVALS/smoke_check.md`, then recover with `03_PITFALL_LOG.md` if it fails.

Quick links:
[Start](./AGENTS.md) · [Prompt](./01_PROMPT_PREVIEW.md) · [Evals](./06_EVALS/) · [Pitfalls](./03_PITFALL_LOG.md) · [Manual](./05_HUMAN_MANUAL.md)

## When This Helps

Use this pack when your AI agent needs to:
- Add persistent memory with contradiction detection to a codebase (yantrikdb as the backing store)
- Govern an agent's recall with temporal decay boundaries and decay-aware consolidation
- Evaluate whether an agent's memory claims are fresh, contradicted, or decayed
- Recover from a polluted memory state where the agent acts on stale or hallucinated facts
- Integrate yantrikdb as an MCP server or Rust library into a project, with known failure modes documented

Do not use this pack as a substitute for reading the upstream docs or verifying installation in a sandbox first.

## What You Get

- Host instructions for AI coding agents.
- A copyable prompt preview.
- Acceptance checks.
- Pitfall log and recovery steps.
- Boundary and risk card.
- Human reference manual (`05_HUMAN_MANUAL.md`) — architecture, components, and failure taxonomy.
- Source attribution and upstream links.

If this pack helps your agent work from evidence instead of guesses, star the repo so future updates are easier to find. Open an issue for bugs, usage questions, or new pitfall reports.

## AGENTS.md for Claude Code and AI Coding Agents

Use `AGENTS.md` for agent hosts that support repository instructions. Use `CLAUDE.md` when Claude Code is the target host.

## yantrikos/yantrikdb Pitfalls and Recovery

Start with `03_PITFALL_LOG.md` when setup, permissions, runtime behavior, or verification fails.

## Source Attribution

This project pack was assembled by [Doramagic](https://doramagic.ai) to make yantrikos/yantrikdb usable as a portable AI capability asset.

- Upstream/source: https://github.com/yantrikos/yantrikdb
- License: AGPL-3.0
- Pack contents: prompts, host instructions, checks, guardrails, and validation notes
- Relationship: independent pack; not affiliated with or endorsed by yantrikos/yantrikdb unless explicitly stated

If you maintain the upstream project and want attribution changed or removed, open an issue in this repository.
