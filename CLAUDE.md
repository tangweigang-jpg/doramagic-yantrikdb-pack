# CLAUDE.md

Use the instructions in `AGENTS.md` as the base. This file adds Claude Code-specific runtime behavior.

## Claude Code Runtime Rules

### Before Any Action

1. Restate the user's task in one sentence.
2. Identify which of these are required: `browser`, `network`, `filesystem`, `credentials`. If any are required, stop and ask for explicit approval before proceeding.
3. Check whether the action is blocked by any entry in `03_PITFALL_LOG.md`.
4. If a verification step is available in `06_EVALS/`, run it before claiming success.

### Tool Usage Policy

- **Browser**: Stop. State the URL you will navigate to and the action you will take. Wait for approval.
- **Network**: Stop. Name the endpoint and the reason you need it. Wait for approval.
- **Filesystem**: Stop. List the specific paths you will read or write. Wait for approval unless the user has pre-approved filesystem access for this project.
- **Credentials / Secrets**: Never access secrets without explicit user approval. If a task requires an API key, token, or credential, stop and ask.

### Claiming the Pack Works

You may NOT say "the pack works", "installation succeeded", or "the tool is working" unless:
- You have run `06_EVALS/smoke_check.md` (or its equivalent prompt) and it returned the expected result.
- You have not encountered any pitfall that blocked the path.

If blocked: write the failure into `TEST_LOG.md` using the format in `03_PITFALL_LOG.md`, then report the failure to the user. Do not continue past the block.

### Claiming the Upstream Tool Works

You may NOT claim `yantrikdb` is installed, functional, or compatible unless:
- The user has run `pip install yantrikdb-mcp` or equivalent in their environment.
- At least one smoke check eval has passed.
- No relevant open pitfall blocks the claimed capability.

### Loading This Pack in Claude Code

1. Copy the text from `AGENTS.md` into your CLAUDE.md (or replace your existing CLAUDE.md with it).
2. Copy the prompt from `01_PROMPT_PREVIEW.md` to experience the pack's intended interaction pattern.
3. Run `06_EVALS/smoke_check.md` to confirm the agent can follow the pack's rules.

### Hard Stops

Stop and report to the user if any of these occur:
- A secret or credential is requested without prior approval.
- An external system (browser, network, filesystem outside the project) is about to be modified without approval.
- An eval failure is detected and no recovery step is available in `03_PITFALL_LOG.md`.
- The user asks you to claim official endorsement from yantrikos/yantrikdb.

