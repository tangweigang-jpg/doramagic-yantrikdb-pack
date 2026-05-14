# AI Context Pack

## Pack Identity

- Upstream: https://github.com/yantrikos/yantrikdb
- Pack type: Agent Memory Governance Pack
- Doramagic canonical: https://doramagic.ai/projects/yantrikdb/
- Relationship: independent pack; not affiliated or endorsed unless explicitly stated.

## Operating Rules

- Evidence first.
- No official endorsement claim.
- Run evals before claiming success.
- Use pitfall and risk files for recovery.

## Host Files

- `../AGENTS.md`
- `../CLAUDE.md`

## Doramagic Source Extract

# yantrikdb - Doramagic AI Context Pack

> 定位：安装前体验与判断资产。它帮助宿主 AI 有一个好的开始，但不代表已经安装、执行或验证目标项目。

## 充分原则

- **充分原则，不是压缩原则**：AI Context Pack 应该充分到让宿主 AI 在开工前理解项目价值、能力边界、使用入口、风险和证据来源；它可以分层组织，但不以最短摘要为目标。
- **压缩策略**：只压缩噪声和重复内容，不压缩会影响判断和开工质量的上下文。

## 给宿主 AI 的使用方式

你正在读取 Doramagic 为 yantrikdb 编译的 AI Context Pack。请把它当作开工前上下文：帮助用户理解适合谁、能做什么、如何开始、哪些必须安装后验证、风险在哪里。不要声称你已经安装、运行或执行了目标项目。

## Claim 消费规则

- **事实来源**：Repo Evidence + Claim/Evidence Graph；Human Wiki 只提供显著性、术语和叙事结构。
- **事实最低状态**：`supported`
- `supported`：可以作为项目事实使用，但回答中必须引用 claim_id 和证据路径。
- `weak`：只能作为低置信度线索，必须要求用户继续核实。
- `inferred`：只能用于风险提示或待确认问题，不能包装成项目事实。
- `unverified`：不得作为事实使用，应明确说证据不足。
- `contradicted`：必须展示冲突来源，不得替用户强行选择一个版本。

## 它最适合谁

- **AI 研究者或研究型 Agent 构建者**：README 明确围绕研究、实验或论文工作流展开。 证据：`README.md` Claim：`clm_0002` supported 0.86
- **正在使用 Claude/Codex/Cursor/Gemini 等宿主 AI 的开发者**：README 或插件配置提到多个宿主 AI。 证据：`README.md` Claim：`clm_0003` supported 0.86

## 它能做什么

- **命令行启动或安装流程**（需要安装后验证）：项目文档中存在可执行命令，真实使用需要在本地或宿主环境中运行这些命令。 证据：`README.md` Claim：`clm_0001` supported 0.86

## 怎么开始

- `pip install yantrikdb-mcp` 证据：`README.md` Claim：`clm_0004` supported 0.86
- `pip install yantrikdb` 证据：`README.md` Claim：`clm_0004` supported 0.86, `clm_0005` supported 0.86

## 继续前判断卡

- **当前建议**：先做权限沙盒试用
- **为什么**：项目存在安装命令、宿主配置或本地写入线索，不建议直接进入主力环境，应先在隔离环境试装。

### 30 秒判断

- **现在怎么做**：先做权限沙盒试用
- **最小安全下一步**：先跑 Prompt Preview；若仍要安装，只在隔离环境试装
- **先别相信**：工具权限边界不能在安装前相信。
- **继续会触碰**：命令执行、本地环境或项目文件、宿主 AI 上下文

### 现在可以相信

- **适合人群线索：AI 研究者或研究型 Agent 构建者**（supported）：有 supported claim 或项目证据支撑，但仍不等于真实安装效果。 证据：`README.md` Claim：`clm_0002` supported 0.86
- **适合人群线索：正在使用 Claude/Codex/Cursor/Gemini 等宿主 AI 的开发者**（supported）：有 supported claim 或项目证据支撑，但仍不等于真实安装效果。 证据：`README.md` Claim：`clm_0003` supported 0.86
- **能力存在：命令行启动或安装流程**（supported）：可以相信项目包含这类能力线索；是否适合你的具体任务仍要试用或安装后验证。 证据：`README.md` Claim：`clm_0001` supported 0.86
- **存在 Quick Start / 安装命令线索**（supported）：可以相信项目文档出现过启动或安装入口；不要因此直接在主力环境运行。 证据：`README.md` Claim：`clm_0004` supported 0.86

### 现在还不能相信

- **工具权限边界不能在安装前相信。**（unverified）：MCP/tool 类项目通常会触碰文件、网络、浏览器或外部 API，必须真实检查权限和日志。
- **真实输出质量不能在安装前相信。**（unverified）：Prompt Preview 只能展示引导方式，不能证明真实项目中的结果质量。
- **宿主 AI 版本兼容性不能在安装前相信。**（unverified）：Claude、Cursor、Codex、Gemini 等宿主加载规则和版本差异必须在真实环境验证。
- **不会污染现有宿主 AI 行为，不能直接相信。**（inferred）：Skill、plugin、AGENTS/CLAUDE/GEMINI 指令可能改变宿主 AI 的默认行为。
- **可安全回滚不能默认相信。**（unverified）：除非项目明确提供卸载和恢复说明，否则必须先在隔离环境验证。
- **真实安装后是否与用户当前宿主 AI 版本兼容？**（unverified）：兼容性只能通过实际宿主环境验证。
- **项目输出质量是否满足用户具体任务？**（unverified）：安装前预览只能展示流程和边界，不能替代真实评测。
- **安装命令是否需要网络、权限或全局写入？**（unverified）：这影响企业环境和个人环境的安装风险。 证据：`README.md`

### 继续会触碰什么

- **命令执行**：包管理器、网络下载、本地插件目录、项目配置或用户主目录。 原因：运行第一条命令就可能产生环境改动；必须先判断是否值得跑。 证据：`README.md`
- **本地环境或项目文件**：安装结果、插件缓存、项目配置或本地依赖目录。 原因：安装前无法证明写入范围和回滚方式，需要隔离验证。 证据：`README.md`
- **宿主 AI 上下文**：AI Context Pack、Prompt Preview、Skill 路由、风险规则和项目事实。 原因：导入上下文会影响宿主 AI 后续判断，必须避免把未验证项包装成事实。

### 最小安全下一步

- **先跑 Prompt Preview**：用安装前交互式试用判断工作方式是否匹配，不需要授权或改环境。（适用：任何项目都适用，尤其是输出质量未知时。）
- **只在隔离目录或测试账号试装**：避免安装命令污染主力宿主 AI、真实项目或用户主目录。（适用：存在命令执行、插件配置或本地写入线索时。）
- **安装后只验证一个最小任务**：先验证加载、兼容、输出质量和回滚，再决定是否深用。（适用：准备从试用进入真实工作流时。）

### 退出方式

- **保留安装前状态**：记录原始宿主配置和项目状态，后续才能判断是否可恢复。
- **记录安装命令和写入路径**：没有明确卸载说明时，至少要知道哪些目录或配置需要手动清理。
- **如果没有回滚路径，不进入主力环境**：不可回滚是继续前阻断项，不应靠信任或运气继续。

## 哪些只能预览

- 解释项目适合谁和能做什么
- 基于项目文档演示典型对话流程
- 帮助用户判断是否值得安装或继续研究

## 哪些必须安装后验证

- 真实安装 Skill、插件或 CLI
- 执行脚本、修改本地文件或访问外部服务
- 验证真实输出质量、性能和兼容性

## 边界与风险判断卡

- **把安装前预览误认为真实运行**：用户可能高估项目已经完成的配置、权限和兼容性验证。 处理方式：明确区分 prompt_preview_can_do 与 runtime_required。 Claim：`clm_0006` inferred 0.45
- **命令执行会修改本地环境**：安装命令可能写入用户主目录、宿主插件目录或项目配置。 处理方式：先在隔离环境或测试账号中运行。 证据：`README.md` Claim：`clm_0007` supported 0.86
- **待确认**：真实安装后是否与用户当前宿主 AI 版本兼容？。原因：兼容性只能通过实际宿主环境验证。
- **待确认**：项目输出质量是否满足用户具体任务？。原因：安装前预览只能展示流程和边界，不能替代真实评测。
- **待确认**：安装命令是否需要网络、权限或全局写入？。原因：这影响企业环境和个人环境的安装风险。

## 开工前工作上下文

### 加载顺序

- 先读取 how_to_use.host_ai_instruction，建立安装前判断资产的边界。
- 读取 claim_graph_summary，确认事实来自 Claim/Evidence Graph，而不是 Human Wiki 叙事。
- 再读取 intended_users、capabilities 和 quick_start_candidates，判断用户是否匹配。
- 需要执行具体任务时，优先查 role_skill_index，再查 evidence_index。
- 遇到真实安装、文件修改、网络访问、性能或兼容性问题时，转入 risk_card 和 boundaries.runtime_required。

### 任务路由

- **命令行启动或安装流程**：先说明这是安装后验证能力，再给出安装前检查清单。 边界：必须真实安装或运行后验证。 证据：`README.md` Claim：`clm_0001` supported 0.86

### 上下文规模

- 文件总数：236
- 重要文件覆盖：22/236
- 证据索引条目：21
- 角色 / Skill 条目：10

### 证据不足时的处理

- **missing_evidence**：说明证据不足，要求用户提供目标文件、README 段落或安装后验证记录；不要补全事实。
- **out_of_scope_request**：说明该任务超出当前 AI Context Pack 证据范围，并建议用户先查看 Human Manual 或真实安装后验证。
- **runtime_request**：给出安装前检查清单和命令来源，但不要替用户执行命令或声称已执行。
- **source_conflict**：同时展示冲突来源，标记为待核实，不要强行选择一个版本。

## Prompt Recipes

### 适配判断

- 目标：判断这个项目是否适合用户当前任务。
- 预期输出：适配结论、关键理由、证据引用、安装前可预览内容、必须安装后验证内容、下一步建议。

```text
请基于 yantrikdb 的 AI Context Pack，先问我 3 个必要问题，然后判断它是否适合我的任务。回答必须包含：适合谁、能做什么、不能做什么、是否值得安装、证据来自哪里。所有项目事实必须引用 evidence_refs、source_paths 或 claim_id。
```

### 安装前体验

- 目标：让用户在安装前感受核心工作流，同时避免把预览包装成真实能力或营销承诺。
- 预期输出：一段带边界标签的体验剧本、安装后验证清单和谨慎建议；不含真实运行承诺或强营销表述。

```text
请把 yantrikdb 当作安装前体验资产，而不是已安装工具或真实运行环境。

请严格输出四段：
1. 先问我 3 个必要问题。
2. 给出一段“体验剧本”：用 [安装前可预览]、[必须安装后验证]、[证据不足] 三种标签展示它可能如何引导工作流。
3. 给出安装后验证清单：列出哪些能力只有真实安装、真实宿主加载、真实项目运行后才能确认。
4. 给出谨慎建议：只能说“值得继续研究/试装”“先补充信息后再判断”或“不建议继续”，不得替项目背书。

硬性边界：
- 不要声称已经安装、运行、执行测试、修改文件或产生真实结果。
- 不要写“自动适配”“确保通过”“完美适配”“强烈建议安装”等承诺性表达。
- 如果描述安装后的工作方式，必须使用“如果安装成功且宿主正确加载 Skill，它可能会……”这种条件句。
- 体验剧本只能写成“示例台词/假设流程”：使用“可能会询问/可能会建议/可能会展示”，不要写“已写入、已生成、已通过、正在运行、正在生成”。
- Prompt Preview 不负责给安装命令；如用户准备试装，只能提示先阅读 Quick Start 和 Risk Card，并在隔离环境验证。
- 所有项目事实必须来自 supported claim、evidence_refs 或 source_paths；inferred/unverified 只能作风险或待确认项。

```

### 角色 / Skill 选择

- 目标：从项目里的角色或 Skill 中挑选最匹配的资产。
- 预期输出：候选角色或 Skill 列表，每项包含适用场景、证据路径、风险边界和是否需要安装后验证。

```text
请读取 role_skill_index，根据我的目标任务推荐 3-5 个最相关的角色或 Skill。每个推荐都要说明适用场景、可能输出、风险边界和 evidence_refs。
```

### 风险预检

- 目标：安装或引入前识别环境、权限、规则冲突和质量风险。
- 预期输出：环境、权限、依赖、许可、宿主冲突、质量风险和未知项的检查清单。

```text
请基于 risk_card、boundaries 和 quick_start_candidates，给我一份安装前风险预检清单。不要替我执行命令，只说明我应该检查什么、为什么检查、失败会有什么影响。
```

### 宿主 AI 开工指令

- 目标：把项目上下文转成一次对话开始前的宿主 AI 指令。
- 预期输出：一段边界明确、证据引用明确、适合复制给宿主 AI 的开工前指令。

```text
请基于 yantrikdb 的 AI Context Pack，生成一段我可以粘贴给宿主 AI 的开工前指令。这段指令必须遵守 not_runtime=true，不能声称项目已经安装、运行或产生真实结果。
```


## 角色 / Skill 索引

- 共索引 10 个角色 / Skill / 项目文档条目。

- **YantrikDB — A Cognitive Memory Engine for Persistent AI Systems**（project_doc）：YantrikDB — A Cognitive Memory Engine for Persistent AI Systems 激活提示：当用户需要理解项目结构、安装方式或边界时参考。 证据：`README.md`
- **RFC: Decoupled Write Path engine v0.7.0**（project_doc）：RFC: Decoupled Write Path engine v0.7.0 激活提示：当用户需要理解项目结构、安装方式或边界时参考。 证据：`docs/decoupled_write_path_rfc.md`
- **Phase 4.3 — SQL writes off foreground design memo**（project_doc）：Phase 4.3 — SQL writes off foreground design memo 激活提示：当用户需要理解项目结构、安装方式或边界时参考。 证据：`docs/phase_4_3_design.md`
- **Wedge — Concurrency Scaling Sweep**（project_doc）：Date: 2026-05-07 Engine version: v0.6.5 @ 36ba7da clean main, no Patch A Harness: crates/yantrikdb-core/examples/wedge repro.rs Params: dim=384, warmup=2000 records, duration=20s, readers=4, writers ∈ {1, 4, 8, 16, 32} Goal: characterize the wedge knee — at what writer concurrency does the engine start to bleed? 激活提示：当用户需要理解项目结构、安装方式或边界时参考。 证据：`docs/wedge_concurrency_sweep_2026-05-07.md`
- **Wedge — Empirical Baseline**（project_doc）：Captured by: yantrikdb-core claude-opus-4-7 Date: 2026-05-06 Harness: crates/yantrikdb-core/examples/wedge repro.rs Engine version: v0.6.5 @ 36ba7da Goal: empirically confirm the lock-scope audit's mechanism hypothesis audit doc docs/wedge lock scope audit 2026-05-06.md and establish baseline numbers for measuring fixes against. 激活提示：当用户需要理解项目结构、安装方式或边界时参考。 证据：`docs/wedge_empirical_baseline_2026-05-06.md`
- **Lock-Scope Audit — Engine Hot Paths**（project_doc）：Lock-Scope Audit — Engine Hot Paths 激活提示：当用户需要理解项目结构、安装方式或边界时参考。 证据：`docs/wedge_lock_scope_audit_2026-05-06.md`
- **What a claim-graph sees that a vector DB doesn't**（project_doc）：What a claim-graph sees that a vector DB doesn't 激活提示：当用户需要理解项目结构、安装方式或边界时参考。 证据：`docs/showcase/wirecard.md`
- **1. Introduction**（project_doc）：The emergence of large language models has created AI systems capable of sophisticated reasoning, yet fundamentally amnesic. Each conversation begins from zero. Every user preference must be re-stated. No continuity of relationship develops over time. This is not merely an inconvenience---it represents a structural barrier to AI systems that genuinely know their users. 激活提示：当用户需要理解项目结构、安装方式或边界时参考。 证据：`docs/whitepaper/aidb_whitepaper.md`
- **YantrikDB Concurrency Invariants**（project_doc）：This document records the load-bearing concurrency invariants of the yantrikdb engine. Several inline // See CONCURRENCY.md comments in the code resolve to this file. Violating any of these silently regresses the wedge fix or correctness; review carefully before changing the affected code paths. 激活提示：当用户需要理解项目结构、安装方式或边界时参考。 证据：`CONCURRENCY.md`
- **YantrikDB MCP Server Redesign — Session Brief**（project_doc）：YantrikDB MCP Server Redesign — Session Brief 激活提示：当用户需要理解项目结构、安装方式或边界时参考。 证据：`MCP_REDESIGN.md`

## 证据索引

- 共索引 21 条证据。

- **YantrikDB — A Cognitive Memory Engine for Persistent AI Systems**（documentation）：YantrikDB — A Cognitive Memory Engine for Persistent AI Systems 证据：`README.md`
- **License**（source_file）：GNU AFFERO GENERAL PUBLIC LICENSE Version 3, 19 November 2007 证据：`LICENSE`
- **RFC: Decoupled Write Path engine v0.7.0**（documentation）：RFC: Decoupled Write Path engine v0.7.0 证据：`docs/decoupled_write_path_rfc.md`
- **Phase 4.3 — SQL writes off foreground design memo**（documentation）：Phase 4.3 — SQL writes off foreground design memo 证据：`docs/phase_4_3_design.md`
- **Wedge — Concurrency Scaling Sweep**（documentation）：Date: 2026-05-07 Engine version: v0.6.5 @ 36ba7da clean main, no Patch A Harness: crates/yantrikdb-core/examples/wedge repro.rs Params: dim=384, warmup=2000 records, duration=20s, readers=4, writers ∈ {1, 4, 8, 16, 32} Goal: characterize the wedge knee — at what writer concurrency does the engine start to bleed? 证据：`docs/wedge_concurrency_sweep_2026-05-07.md`
- **Wedge — Empirical Baseline**（documentation）：Captured by: yantrikdb-core claude-opus-4-7 Date: 2026-05-06 Harness: crates/yantrikdb-core/examples/wedge repro.rs Engine version: v0.6.5 @ 36ba7da Goal: empirically confirm the lock-scope audit's mechanism hypothesis audit doc docs/wedge lock scope audit 2026-05-06.md and establish baseline numbers for measuring fixes against. 证据：`docs/wedge_empirical_baseline_2026-05-06.md`
- **Lock-Scope Audit — Engine Hot Paths**（documentation）：Lock-Scope Audit — Engine Hot Paths 证据：`docs/wedge_lock_scope_audit_2026-05-06.md`
- **What a claim-graph sees that a vector DB doesn't**（documentation）：What a claim-graph sees that a vector DB doesn't 证据：`docs/showcase/wirecard.md`
- **1. Introduction**（documentation）：The emergence of large language models has created AI systems capable of sophisticated reasoning, yet fundamentally amnesic. Each conversation begins from zero. Every user preference must be re-stated. No continuity of relationship develops over time. This is not merely an inconvenience---it represents a structural barrier to AI systems that genuinely know their users. 证据：`docs/whitepaper/aidb_whitepaper.md`
- **YantrikDB Concurrency Invariants**（documentation）：This document records the load-bearing concurrency invariants of the yantrikdb engine. Several inline // See CONCURRENCY.md comments in the code resolve to this file. Violating any of these silently regresses the wedge fix or correctness; review carefully before changing the affected code paths. 证据：`CONCURRENCY.md`
- **YantrikDB MCP Server Redesign — Session Brief**（documentation）：YantrikDB MCP Server Redesign — Session Brief 证据：`MCP_REDESIGN.md`
- **Config**（structured_config）：{"model type": "model2vec", "architectures": "StaticModel" ,"tokenizer name": "baai/bge-base-en-v1.5", "apply pca": 64, "apply zipf": true, "hidden dim": 64, "seq length": 1000000, "normalize": true} 证据：`crates/yantrikdb-core/assets/potion-base-2M/config.json`
- **Modules**（structured_config）：{ "idx": 0, "name": "0", "path": ".", "type": "sentence transformers.models.StaticEmbedding" }, { "idx": 1, "name": "1", "path": "1 Normalize", "type": "sentence transformers.models.Normalize" } 证据：`crates/yantrikdb-core/assets/potion-base-2M/modules.json`
- **Tokenizer**（structured_config）：{ "version": "1.0", "truncation": null, "padding": null, "added tokens": { "id": 0, "content": " PAD ", "single word": false, "lstrip": false, "rstrip": false, "normalized": false, "special": true }, { "id": 1, "content": " UNK ", "single word": false, "lstrip": false, "rstrip": false, "normalized": false, "special": true }, { "id": 2, "content": " CLS ", "single word": false, "lstrip": false, "rstrip": false, "normalized": false, "special": true }, { "id": 3, "content": " SEP ", "single word": false, "lstrip": false, "rstrip": false, "normalized": false, "special": true }, { "id": 4, "content": " MASK ", "single word": false, "lstrip": false, "rstrip": false, "normalized": false, "special"… 证据：`crates/yantrikdb-core/assets/potion-base-2M/tokenizer.json`
- **Scheduled Tasks**（source_file）：{"sessionId":"48c5baf6-0baa-4c37-93d2-a8f22722b261","pid":92712,"acquiredAt":1778091707761} 证据：`.claude/scheduled_tasks.lock`
- **MCP / Saga**（source_file）：MCP / Saga .mcp.json .tracker.db .tracker.db-shm .tracker.db-wal .env 证据：`.gitignore`
- **Optimize dependencies candle, tokenizers even in dev builds.**（source_file）：workspace resolver = "2" members = "crates/yantrikdb-core", "crates/yantrikdb-python", exclude = "crates/yantrikdb-wasm", 证据：`Cargo.toml`
- **Bench Rust Vs Python**（source_file）："""Benchmarks for AIDB Rust engine core operations. 证据：`benchmarks/bench_rust_vs_python.py`
- **v0.7.6 — bundled-embedder respect. Default install is just the**（source_file）：build-system requires = "maturin =1.5" build-backend = "maturin" 证据：`pyproject.toml`
- **── 1. Test corpus: yantrikdb-shaped memories ──**（source_file）：""" Empirical quality eval: potion-base-2M vs all-MiniLM-L6-v2 vs Slice A hash-trick baseline, on yantrikdb-shaped memory texts. 证据：`scratch/eval_potion_2m.py`
- **!/usr/bin/env python3**（source_file）：!/usr/bin/env python3 """Run the AIDB evaluation harness with real embeddings. 证据：`scripts/run_eval.py`

## 宿主 AI 必须遵守的规则

- **把本资产当作开工前上下文，而不是运行环境。**：AI Context Pack 只包含证据化项目理解，不包含目标项目的可执行状态。 证据：`README.md`, `LICENSE`, `docs/decoupled_write_path_rfc.md`
- **回答用户时区分可预览内容与必须安装后才能验证的内容。**：安装前体验的消费者价值来自降低误装和误判，而不是伪装成真实运行。 证据：`README.md`, `LICENSE`, `docs/decoupled_write_path_rfc.md`

## 用户开工前应该回答的问题

- 你准备在哪个宿主 AI 或本地环境中使用它？
- 你只是想先体验工作流，还是准备真实安装？
- 你最在意的是安装成本、输出质量、还是和现有规则的冲突？

## 验收标准

- 所有能力声明都能回指到 evidence_refs 中的文件路径。
- AI_CONTEXT_PACK.md 没有把预览包装成真实运行。
- 用户能在 3 分钟内看懂适合谁、能做什么、如何开始和风险边界。

---

## Doramagic Context Augmentation

下面内容用于强化 Repomix/AI Context Pack 主体。Human Manual 只提供阅读骨架；踩坑日志会被转成宿主 AI 必须遵守的工作约束。

## Human Manual 骨架

使用规则：这里只是项目阅读路线和显著性信号，不是事实权威。具体事实仍必须回到 repo evidence / Claim Graph。

宿主 AI 硬性规则：
- 不得把页标题、章节顺序、摘要或 importance 当作项目事实证据。
- 解释 Human Manual 骨架时，必须明确说它只是阅读路线/显著性信号。
- 能力、安装、兼容性、运行状态和风险判断必须引用 repo evidence、source path 或 Claim Graph。

- **YantrikDB 简介**：importance `high`
  - source_paths: README.md, Cargo.toml, LICENSE
- **快速开始**：importance `high`
  - source_paths: README.md, pyproject.toml, src/yantrikdb/__init__.py
- **五大索引架构**：importance `high`
  - source_paths: crates/yantrikdb-core/src/vector/hnsw.rs, crates/yantrikdb-core/src/vector/delta_index.rs, crates/yantrikdb-core/src/knowledge/graph.rs, crates/yantrikdb-core/src/knowledge/graph_index.rs, crates/yantrikdb-core/src/engine/indices.rs
- **解耦写入路径**：importance `high`
  - source_paths: docs/decoupled_write_path_rfc.md, CONCURRENCY.md, crates/yantrikdb-core/src/vector/delta_index.rs, crates/yantrikdb-core/src/engine/materializer.rs
- **线程安全与并发模型**：importance `medium`
  - source_paths: CONCURRENCY.md, crates/yantrikdb-core/src/engine/mod.rs, crates/yantrikdb-core/src/engine/tick.rs
- **记录与检索操作**：importance `high`
  - source_paths: crates/yantrikdb-core/src/engine/record.rs, crates/yantrikdb-core/src/engine/recall.rs, crates/yantrikdb-core/src/base/scoring.rs, src/yantrikdb/api.py
- **知识图谱操作**：importance `medium`
  - source_paths: crates/yantrikdb-core/src/knowledge/graph.rs, crates/yantrikdb-core/src/engine/graph_ops.rs, crates/yantrikdb-core/src/engine/graph_state.rs
- **认知循环与思考**：importance `high`
  - source_paths: crates/yantrikdb-core/src/cognition/mod.rs, crates/yantrikdb-core/src/cognition/consolidate.rs, crates/yantrikdb-core/src/cognition/patterns.rs, crates/yantrikdb-core/src/engine/cognition.rs

## Repo Inspection Evidence / 源码检查证据

- repo_clone_verified: true
- repo_inspection_verified: true
- repo_commit: `895a77725801db73e1bb0eb26d74af031ecc53ff`
- inspected_files: `pyproject.toml`, `README.md`, `uv.lock`, `docs/phase_4_3_design.md`, `docs/wedge_empirical_baseline_2026-05-06.md`, `docs/wedge_lock_scope_audit_2026-05-06.md`, `docs/wedge_concurrency_sweep_2026-05-07.md`, `docs/decoupled_write_path_rfc.md`, `docs/whitepaper/aidb_whitepaper.md`, `docs/showcase/wirecard.md`, `src/yantrikdb/cli.py`, `src/yantrikdb/consolidate.py`, `src/yantrikdb/api.py`, `src/yantrikdb/triggers.py`, `src/yantrikdb/__init__.py`, `src/yantrikdb/mcp/tools.py`, `src/yantrikdb/mcp/resources.py`, `src/yantrikdb/mcp/server.py`, `src/yantrikdb/mcp/__init__.py`, `src/yantrikdb/adapters/crewai.py`

宿主 AI 硬性规则：
- 没有 repo_clone_verified=true 时，不得声称已经读过源码。
- 没有 repo_inspection_verified=true 时，不得把 README/docs/package 文件判断写成事实。
- 没有 quick_start_verified=true 时，不得声称 Quick Start 已跑通。

## Doramagic Pitfall Constraints / 踩坑约束

这些规则来自 Doramagic 发现、验证或编译过程中的项目专属坑点。宿主 AI 必须把它们当作工作约束，而不是普通说明文字。

### Constraint 1: 来源证据：API addition: deterministic mutation primitives (record_with_rid + friends) for cluster-mode replication

- Trigger: GitHub 社区证据显示该项目存在一个安装相关的待验证问题：API addition: deterministic mutation primitives (record_with_rid + friends) for cluster-mode replication
- Host AI rule: 来源显示可能已有修复、规避或版本变化，说明书中必须标注适用版本。
- Why it matters: 可能阻塞安装或首次运行。
- Evidence: community_evidence:github | cevd_4ab95be6a3ac4fb192053e8c3829f762 | https://github.com/yantrikos/yantrikdb/issues/9 | 来源讨论提到 node 相关条件，需在安装/试用前复核。
- Hard boundary: 不要把这个坑点包装成已解决、已验证或可忽略，除非后续验证证据明确证明它已经关闭。

### Constraint 2: 来源证据：Bug: `namespace` parameter ignored in batch `remember` calls — memories always stored under `default`

- Trigger: GitHub 社区证据显示该项目存在一个安装相关的待验证问题：Bug: `namespace` parameter ignored in batch `remember` calls — memories always stored under `default`
- Host AI rule: 来源显示可能已有修复、规避或版本变化，说明书中必须标注适用版本。
- Why it matters: 可能增加新用户试用和生产接入成本。
- Evidence: community_evidence:github | cevd_c37cd96e9c8d476880caca4f7314118e | https://github.com/yantrikos/yantrikdb/issues/2 | 来源讨论提到 python 相关条件，需在安装/试用前复核。
- Hard boundary: 不要把这个坑点包装成已解决、已验证或可忽略，除非后续验证证据明确证明它已经关闭。

### Constraint 3: 来源证据：Migration v14→v15 fails: ALTER TABLE on edges view

- Trigger: GitHub 社区证据显示该项目存在一个安装相关的待验证问题：Migration v14→v15 fails: ALTER TABLE on edges view
- Host AI rule: 来源显示可能已有修复、规避或版本变化，说明书中必须标注适用版本。
- Why it matters: 可能影响升级、迁移或版本选择。
- Evidence: community_evidence:github | cevd_bb378d100e9d472892b1d5e42e640cad | https://github.com/yantrikos/yantrikdb/issues/10 | 来源讨论提到 python 相关条件，需在安装/试用前复核。
- Hard boundary: 不要把这个坑点包装成已解决、已验证或可忽略，除非后续验证证据明确证明它已经关闭。

### Constraint 4: 来源证据：[bug] Tombstoned memories still appear in similarity-scan recall results

- Trigger: GitHub 社区证据显示该项目存在一个安装相关的待验证问题：[bug] Tombstoned memories still appear in similarity-scan recall results
- Host AI rule: 来源显示可能已有修复、规避或版本变化，说明书中必须标注适用版本。
- Why it matters: 可能增加新用户试用和生产接入成本。
- Evidence: community_evidence:github | cevd_aa3d426055a44483b47ffd3b9f3fdb6a | https://github.com/yantrikos/yantrikdb/issues/8 | 来源类型 github_issue 暴露的待验证使用条件。
- Hard boundary: 不要把这个坑点包装成已解决、已验证或可忽略，除非后续验证证据明确证明它已经关闭。

### Constraint 5: 来源证据：[bug] YANTRIKDB_ENCRYPTION_KEY_HEX env var ignored — encryption silently disabled

- Trigger: GitHub 社区证据显示该项目存在一个安装相关的待验证问题：[bug] YANTRIKDB_ENCRYPTION_KEY_HEX env var ignored — encryption silently disabled
- Host AI rule: 来源显示可能已有修复、规避或版本变化，说明书中必须标注适用版本。
- Why it matters: 可能增加新用户试用和生产接入成本。
- Evidence: community_evidence:github | cevd_17652fc680ba4b64bee5018b2d1514e4 | https://github.com/yantrikos/yantrikdb/issues/6 | 来源讨论提到 docker 相关条件，需在安装/试用前复核。
- Hard boundary: 不要把这个坑点包装成已解决、已验证或可忽略，除非后续验证证据明确证明它已经关闭。

### Constraint 6: 来源证据：v0.7.10 — Fix has_embedder() for Python-side embedders (plugin#4)

- Trigger: GitHub 社区证据显示该项目存在一个安装相关的待验证问题：v0.7.10 — Fix has_embedder() for Python-side embedders (plugin#4)
- Host AI rule: 来源显示可能已有修复、规避或版本变化，说明书中必须标注适用版本。
- Why it matters: 可能增加新用户试用和生产接入成本。
- Evidence: community_evidence:github | cevd_daa2ca5265524c83bb21727be2a980a1 | https://github.com/yantrikos/yantrikdb/releases/tag/v0.7.10 | 来源讨论提到 python 相关条件，需在安装/试用前复核。
- Hard boundary: 不要把这个坑点包装成已解决、已验证或可忽略，除非后续验证证据明确证明它已经关闭。

### Constraint 7: 来源证据：v0.7.11 — pyo3 0.28.3 + python3.14 Support

- Trigger: GitHub 社区证据显示该项目存在一个安装相关的待验证问题：v0.7.11 — pyo3 0.28.3 + python3.14 Support
- Host AI rule: 来源显示可能已有修复、规避或版本变化，说明书中必须标注适用版本。
- Why it matters: 可能影响升级、迁移或版本选择。
- Evidence: community_evidence:github | cevd_91b7975fce7d49b6b87ef05b914e80b2 | https://github.com/yantrikos/yantrikdb/releases/tag/v0.7.11 | 来源讨论提到 python 相关条件，需在安装/试用前复核。
- Hard boundary: 不要把这个坑点包装成已解决、已验证或可忽略，除非后续验证证据明确证明它已经关闭。

### Constraint 8: 来源证据：v0.7.4 — Python Bindings: with_default + record_text/recall_text

- Trigger: GitHub 社区证据显示该项目存在一个安装相关的待验证问题：v0.7.4 — Python Bindings: with_default + record_text/recall_text
- Host AI rule: 来源显示可能已有修复、规避或版本变化，说明书中必须标注适用版本。
- Why it matters: 可能影响升级、迁移或版本选择。
- Evidence: community_evidence:github | cevd_54938994017d4b5899ad9cef4e6a2723 | https://github.com/yantrikos/yantrikdb/releases/tag/v0.7.4 | 来源讨论提到 python 相关条件，需在安装/试用前复核。
- Hard boundary: 不要把这个坑点包装成已解决、已验证或可忽略，除非后续验证证据明确证明它已经关闭。

### Constraint 9: 来源证据：v0.7.5 — Python UX: TypeError Guard + embedder-download in Default Wheel

- Trigger: GitHub 社区证据显示该项目存在一个安装相关的待验证问题：v0.7.5 — Python UX: TypeError Guard + embedder-download in Default Wheel
- Host AI rule: 来源显示可能已有修复、规避或版本变化，说明书中必须标注适用版本。
- Why it matters: 可能增加新用户试用和生产接入成本。
- Evidence: community_evidence:github | cevd_be61ad4afd5b4f669a6f727d727474c4 | https://github.com/yantrikos/yantrikdb/releases/tag/v0.7.5 | 来源讨论提到 python 相关条件，需在安装/试用前复核。
- Hard boundary: 不要把这个坑点包装成已解决、已验证或可忽略，除非后续验证证据明确证明它已经关闭。

### Constraint 10: 可能修改宿主 AI 配置

- Trigger: 项目面向 Claude/Cursor/Codex/Gemini/OpenCode 等宿主，或安装命令涉及用户配置目录。
- Host AI rule: 列出会写入的配置文件、目录和卸载/回滚步骤。
- Why it matters: 安装可能改变本机 AI 工具行为，用户需要知道写入位置和回滚方法。
- Evidence: capability.host_targets | github_repo:1164482810 | https://github.com/yantrikos/yantrikdb | host_targets=mcp_host, claude, claude_code
- Hard boundary: 不要把这个坑点包装成已解决、已验证或可忽略，除非后续验证证据明确证明它已经关闭。

