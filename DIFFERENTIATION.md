# Differentiation

## What This Pack Adds vs. Upstream

| Dimension | Upstream (yantrikos/yantrikdb) | This Doramagic Pack |
|---|---|---|
| **Format** | README + official docs | Loadable AGENTS.md + CLAUDE.md for AI coding hosts |
| **Install verification** | Quick start commands | Smoke eval that refuses to claim success without evidence |
| **Failure modes** | Scattered across GitHub issues and release notes | Centralized pitfall log with Top 3 actionable entries + full index |
| **Boundary/risk policy** | Not packaged for agents | Explicit boundary card with hard stops, credential policy, and stop conditions |
| **Recall verification** | No eval framework | smoke_check, boundary_check, and failure_check evals |
| **Memory contradiction handling** | Docs describe `think()` behavior | Pitfall log entry #13 documents consolidation-before-detection risk |
| **Namespace isolation risk** | GitHub issue #2 | Pack calls out version range and single-call workaround |
| **Encryption silent-failure risk** | GitHub issue #6 | Pack calls out env var vs TOML distinction and verification step |
| **Host targets** | MCP, Claude Code, Cursor, Codex (generic) | AGENTS.md maps each host to its instruction variant |
| **Recovery path on failure** | Not provided | failure_check eval + pitfall log recovery steps per failure type |

## What This Pack Does NOT add

- This pack does not install yantrikdb for you.
- This pack does not modify the upstream codebase.
- This pack does not replace the upstream README or official documentation.
- This pack does not claim official endorsement from yantrikos/yantrikdb.

## Existing GitHub Assets Found

- Official docs: https://github.com/yantrikos/yantrikdb
- Official upstream README explains how to install and use the project.
- Release and issue history expose setup, runtime, or integration failure modes that a normal quickstart rarely packages as agent recovery rules.
- This pack is scoped as a portable AGENTS.md / CLAUDE.md capability bundle with evals, source mapping, and pitfall recovery.

## Why This Doramagic Pack Is Different

- Risk-first angle: this pack starts with pitfalls, boundaries, and verification.
- Eval-backed checks: the repo includes smoke, boundary, and failure checks.
- Host portability: it provides AGENTS.md and CLAUDE.md.
- Failure recovery: it includes a pitfall log and failure eval.
- Source-backed packaging: SOURCE_MAP.md records Doramagic and upstream sources so users can inspect what was used.

## What This Pack Deliberately Does Not Do

- Not an official mirror.
- Not a generic starter.
- Not an awesome list.
- Not an SEO backlink repo.

