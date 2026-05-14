# Pitfall Log / 踩坑日志

项目：yantrikos/yantrikdb

摘要：发现 24 个潜在踩坑项，其中 0 个为 high/blocking；最高优先级：安装坑 - 来源证据：API addition: deterministic mutation primitives (record_with_rid + friends) for cluster-mode replication。

---

## Top 3 Actionable Pitfalls

### P1 · 安装坑 · `namespace` parameter ignored in batch `remember` calls

- **症状**: 调用 `remember` 时传入 `namespace` 参数，但所有记忆都存储在 `default` 下。
- **影响**: 记忆隔离失效，多租户或多上下文记忆混淆。
- **立即检查**: 运行 `pip show yantrikdb-mcp` 确认版本；检查 https://github.com/yantrikos/yantrikdb/issues/2 是否在当前版本已修复。
- **绕过**: 使用单 `remember` 调用代替批量调用，或在应用层做 namespace 前缀隔离。
- **何时停止**: 如果多 namespace 隔离是生产需求，在验证修复前不要部署。

### P2 · 运行坑 · `think()` consolidates before conflict detection — contradictions get merged

- **症状**: Agent 的矛盾记忆未被检测就被合并，导致错误的记忆被固化。
- **影响**: 污染的长期记忆驱动错误的下游决策。
- **立即检查**: 查看 https://github.com/yantrikos/yantrikdb/issues/1 确认版本和修复状态。
- **绕过**: 在调用 `think()` 之前，先用 `recall` 验证记忆一致性。
- **何时停止**: 如果记忆一致性是关键需求，在验证修复前不要用于生产记忆存储。

### P3 · 安全/权限坑 · `YANTRIKDB_ENCRYPTION_KEY_HEX` env var ignored — encryption silently disabled

- **症状**: 设置了环境变量，但磁盘上的数据未加密。
- **影响**: 静态数据泄露风险，尤其在共享环境或云存储场景下。
- **立即检查**: 运行 `pip show yantrikdb-mcp` 确认版本 >= 0.7.x；检查 https://github.com/yantrikos/yantrikdb/issues/6。
- **绕过**: 使用 TOML 配置文件中的 `key_hex` 而非环境变量，并验证数据文件确实被加密。
- **何时停止**: 如果静态加密是合规要求，在验证修复前不要用于存储敏感数据。

---

## 完整坑位索引

| # | 类别 | 标题 | 严重度 |
|---|---|---|---|
| 1 | 安装坑 | API addition: deterministic mutation primitives (record_with_rid + friends) | medium |
| 2 | 安装坑 | `namespace` parameter ignored in batch `remember` calls | medium |
| 3 | 安装坑 | Migration v14→v15 fails: ALTER TABLE on edges view | medium |
| 4 | 安装坑 | Tombstoned memories still appear in similarity-scan recall results | medium |
| 5 | 安装坑 | `YANTRIKDB_ENCRYPTION_KEY_HEX` env var ignored — encryption silently disabled | medium |
| 6 | 安装坑 | v0.7.10 — Fix has_embedder() for Python-side embedders (plugin#4) | medium |
| 7 | 安装坑 | v0.7.11 — pyo3 0.28.3 + python3.14 Support | medium |
| 8 | 安装坑 | v0.7.4 — Python Bindings: with_default + record_text/recall_text | medium |
| 9 | 安装坑 | v0.7.5 — Python UX: TypeError Guard + embedder-download in Default Wheel | medium |
| 10 | 配置坑 | 可能修改宿主 AI 配置 | medium |
| 11 | 配置坑 | v0.7.7 — recall_text Keyword-Only Filter Args | medium |
| 12 | 能力坑 | 能力判断依赖假设 | medium |
| 13 | 运行坑 | think() consolidates before conflict detection | medium |
| 14 | 维护坑 | 维护活跃度未知 | medium |
| 15 | 安全/权限坑 | 下游验证发现风险项 | medium |
| 16 | 安全/权限坑 | 存在安全注意事项 | medium |
| 17 | 安全/权限坑 | 存在评分风险 | medium |
| 18 | 安全/权限坑 | POST /v1/admin/snapshot unusable in single-node mode | medium |
| 19 | 安全/权限坑 | at-rest encryption `key_hex` in TOML has no effect on disk (v0.5.0) | medium |
| 20 | 安全/权限坑 | v0.7.6 — Drop sentence-transformers + numpy from Default Deps | medium |
| 21 | 安全/权限坑 | v0.7.8 — Extended Idempotent Migration Runner | medium |
| 22 | 安全/权限坑 | v0.7.9 — Bundle potion-multilingual-128M in embedder-download Registry | medium |
| 23 | 维护坑 | issue/PR 响应质量未知 | low |
| 24 | 维护坑 | 发布节奏不明确 | low |

---

## 1. 安装坑 · 来源证据：API addition: deterministic mutation primitives (record_with_rid + friends) for cluster-mode replication

## 2. 安装坑 · 来源证据：Bug: `namespace` parameter ignored in batch `remember` calls — memories always stored under `default`

- 严重度：medium
- 证据强度：source_linked
- 发现：GitHub 社区证据显示该项目存在一个安装相关的待验证问题：Bug: `namespace` parameter ignored in batch `remember` calls — memories always stored under `default`
- 对用户的影响：可能增加新用户试用和生产接入成本。
- 建议检查：来源显示可能已有修复、规避或版本变化，说明书中必须标注适用版本。
- 防护动作：不得脱离来源链接放大为确定性结论；需要标注适用版本和复核状态。
- 证据：community_evidence:github | cevd_c37cd96e9c8d476880caca4f7314118e | https://github.com/yantrikos/yantrikdb/issues/2 | 来源讨论提到 python 相关条件，需在安装/试用前复核。

## 3. 安装坑 · 来源证据：Migration v14→v15 fails: ALTER TABLE on edges view

- 严重度：medium
- 证据强度：source_linked
- 发现：GitHub 社区证据显示该项目存在一个安装相关的待验证问题：Migration v14→v15 fails: ALTER TABLE on edges view
- 对用户的影响：可能影响升级、迁移或版本选择。
- 建议检查：来源显示可能已有修复、规避或版本变化，说明书中必须标注适用版本。
- 防护动作：不得脱离来源链接放大为确定性结论；需要标注适用版本和复核状态。
- 证据：community_evidence:github | cevd_bb378d100e9d472892b1d5e42e640cad | https://github.com/yantrikos/yantrikdb/issues/10 | 来源讨论提到 python 相关条件，需在安装/试用前复核。

## 4. 安装坑 · 来源证据：[bug] Tombstoned memories still appear in similarity-scan recall results

- 严重度：medium
- 证据强度：source_linked
- 发现：GitHub 社区证据显示该项目存在一个安装相关的待验证问题：[bug] Tombstoned memories still appear in similarity-scan recall results
- 对用户的影响：可能增加新用户试用和生产接入成本。
- 建议检查：来源显示可能已有修复、规避或版本变化，说明书中必须标注适用版本。
- 防护动作：不得脱离来源链接放大为确定性结论；需要标注适用版本和复核状态。
- 证据：community_evidence:github | cevd_aa3d426055a44483b47ffd3b9f3fdb6a | https://github.com/yantrikos/yantrikdb/issues/8 | 来源类型 github_issue 暴露的待验证使用条件。

## 5. 安装坑 · 来源证据：[bug] YANTRIKDB_ENCRYPTION_KEY_HEX env var ignored — encryption silently disabled

- 严重度：medium
- 证据强度：source_linked
- 发现：GitHub 社区证据显示该项目存在一个安装相关的待验证问题：[bug] YANTRIKDB_ENCRYPTION_KEY_HEX env var ignored — encryption silently disabled
- 对用户的影响：可能增加新用户试用和生产接入成本。
- 建议检查：来源显示可能已有修复、规避或版本变化，说明书中必须标注适用版本。
- 防护动作：不得脱离来源链接放大为确定性结论；需要标注适用版本和复核状态。
- 证据：community_evidence:github | cevd_17652fc680ba4b64bee5018b2d1514e4 | https://github.com/yantrikos/yantrikdb/issues/6 | 来源讨论提到 docker 相关条件，需在安装/试用前复核。

## 6. 安装坑 · 来源证据：v0.7.10 — Fix has_embedder() for Python-side embedders (plugin#4)

- 严重度：medium
- 证据强度：source_linked
- 发现：GitHub 社区证据显示该项目存在一个安装相关的待验证问题：v0.7.10 — Fix has_embedder() for Python-side embedders (plugin#4)
- 对用户的影响：可能增加新用户试用和生产接入成本。
- 建议检查：来源显示可能已有修复、规避或版本变化，说明书中必须标注适用版本。
- 防护动作：不得脱离来源链接放大为确定性结论；需要标注适用版本和复核状态。
- 证据：community_evidence:github | cevd_daa2ca5265524c83bb21727be2a980a1 | https://github.com/yantrikos/yantrikdb/releases/tag/v0.7.10 | 来源讨论提到 python 相关条件，需在安装/试用前复核。

## 7. 安装坑 · 来源证据：v0.7.11 — pyo3 0.28.3 + python3.14 Support

- 严重度：medium
- 证据强度：source_linked
- 发现：GitHub 社区证据显示该项目存在一个安装相关的待验证问题：v0.7.11 — pyo3 0.28.3 + python3.14 Support
- 对用户的影响：可能影响升级、迁移或版本选择。
- 建议检查：来源显示可能已有修复、规避或版本变化，说明书中必须标注适用版本。
- 防护动作：不得脱离来源链接放大为确定性结论；需要标注适用版本和复核状态。
- 证据：community_evidence:github | cevd_91b7975fce7d49b6b87ef05b914e80b2 | https://github.com/yantrikos/yantrikdb/releases/tag/v0.7.11 | 来源讨论提到 python 相关条件，需在安装/试用前复核。

## 8. 安装坑 · 来源证据：v0.7.4 — Python Bindings: with_default + record_text/recall_text

- 严重度：medium
- 证据强度：source_linked
- 发现：GitHub 社区证据显示该项目存在一个安装相关的待验证问题：v0.7.4 — Python Bindings: with_default + record_text/recall_text
- 对用户的影响：可能影响升级、迁移或版本选择。
- 建议检查：来源显示可能已有修复、规避或版本变化，说明书中必须标注适用版本。
- 防护动作：不得脱离来源链接放大为确定性结论；需要标注适用版本和复核状态。
- 证据：community_evidence:github | cevd_54938994017d4b5899ad9cef4e6a2723 | https://github.com/yantrikos/yantrikdb/releases/tag/v0.7.4 | 来源讨论提到 python 相关条件，需在安装/试用前复核。

## 9. 安装坑 · 来源证据：v0.7.5 — Python UX: TypeError Guard + embedder-download in Default Wheel

- 严重度：medium
- 证据强度：source_linked
- 发现：GitHub 社区证据显示该项目存在一个安装相关的待验证问题：v0.7.5 — Python UX: TypeError Guard + embedder-download in Default Wheel
- 对用户的影响：可能增加新用户试用和生产接入成本。
- 建议检查：来源显示可能已有修复、规避或版本变化，说明书中必须标注适用版本。
- 防护动作：不得脱离来源链接放大为确定性结论；需要标注适用版本和复核状态。
- 证据：community_evidence:github | cevd_be61ad4afd5b4f669a6f727d727474c4 | https://github.com/yantrikos/yantrikdb/releases/tag/v0.7.5 | 来源讨论提到 python 相关条件，需在安装/试用前复核。

## 10. 配置坑 · 可能修改宿主 AI 配置

- 严重度：medium
- 证据强度：source_linked
- 发现：项目面向 Claude/Cursor/Codex/Gemini/OpenCode 等宿主，或安装命令涉及用户配置目录。
- 对用户的影响：安装可能改变本机 AI 工具行为，用户需要知道写入位置和回滚方法。
- 建议检查：列出会写入的配置文件、目录和卸载/回滚步骤。
- 防护动作：涉及宿主配置目录时必须给回滚路径，不能只给安装命令。
- 证据：capability.host_targets | github_repo:1164482810 | https://github.com/yantrikos/yantrikdb | host_targets=mcp_host, claude, claude_code

## 11. 配置坑 · 来源证据：v0.7.7 — recall_text Keyword-Only Filter Args

- 严重度：medium
- 证据强度：source_linked
- 发现：GitHub 社区证据显示该项目存在一个配置相关的待验证问题：v0.7.7 — recall_text Keyword-Only Filter Args
- 对用户的影响：可能增加新用户试用和生产接入成本。
- 建议检查：来源显示可能已有修复、规避或版本变化，说明书中必须标注适用版本。
- 防护动作：不得脱离来源链接放大为确定性结论；需要标注适用版本和复核状态。
- 证据：community_evidence:github | cevd_45587e0ca02f4e95ac36c364d3a88519 | https://github.com/yantrikos/yantrikdb/releases/tag/v0.7.7 | 来源讨论提到 python 相关条件，需在安装/试用前复核。

## 12. 能力坑 · 能力判断依赖假设

- 严重度：medium
- 证据强度：source_linked
- 发现：README/documentation is current enough for a first validation pass.
- 对用户的影响：假设不成立时，用户拿不到承诺的能力。
- 建议检查：将假设转成下游验证清单。
- 防护动作：假设必须转成验证项；没有验证结果前不能写成事实。
- 证据：capability.assumptions | github_repo:1164482810 | https://github.com/yantrikos/yantrikdb | README/documentation is current enough for a first validation pass.

## 13. 运行坑 · 来源证据：think() runs consolidation before conflict detection — contradictions get merged

- 严重度：medium
- 证据强度：source_linked
- 发现：GitHub 社区证据显示该项目存在一个运行相关的待验证问题：think() runs consolidation before conflict detection — contradictions get merged
- 对用户的影响：可能增加新用户试用和生产接入成本。
- 建议检查：来源显示可能已有修复、规避或版本变化，说明书中必须标注适用版本。
- 防护动作：不得脱离来源链接放大为确定性结论；需要标注适用版本和复核状态。
- 证据：community_evidence:github | cevd_6908447fb6a6482f89b1a85e714de42a | https://github.com/yantrikos/yantrikdb/issues/1 | 来源讨论提到 python 相关条件，需在安装/试用前复核。

## 14. 维护坑 · 维护活跃度未知

- 严重度：medium
- 证据强度：source_linked
- 发现：未记录 last_activity_observed。
- 对用户的影响：新项目、停更项目和活跃项目会被混在一起，推荐信任度下降。
- 建议检查：补 GitHub 最近 commit、release、issue/PR 响应信号。
- 防护动作：维护活跃度未知时，推荐强度不能标为高信任。
- 证据：evidence.maintainer_signals | github_repo:1164482810 | https://github.com/yantrikos/yantrikdb | last_activity_observed missing

## 15. 安全/权限坑 · 下游验证发现风险项

- 严重度：medium
- 证据强度：source_linked
- 发现：no_demo
- 对用户的影响：下游已经要求复核，不能在页面中弱化。
- 建议检查：进入安全/权限治理复核队列。
- 防护动作：下游风险存在时必须保持 review/recommendation 降级。
- 证据：downstream_validation.risk_items | github_repo:1164482810 | https://github.com/yantrikos/yantrikdb | no_demo; severity=medium

## 16. 安全/权限坑 · 存在安全注意事项

- 严重度：medium
- 证据强度：source_linked
- 发现：No sandbox install has been executed yet; downstream must verify before user use.
- 对用户的影响：用户安装前需要知道权限边界和敏感操作。
- 建议检查：转成明确权限清单和安全审查提示。
- 防护动作：安全注意事项必须面向用户前置展示。
- 证据：risks.safety_notes | github_repo:1164482810 | https://github.com/yantrikos/yantrikdb | No sandbox install has been executed yet; downstream must verify before user use.

## 17. 安全/权限坑 · 存在评分风险

- 严重度：medium
- 证据强度：source_linked
- 发现：no_demo
- 对用户的影响：风险会影响是否适合普通用户安装。
- 建议检查：把风险写入边界卡，并确认是否需要人工复核。
- 防护动作：评分风险必须进入边界卡，不能只作为内部分数。
- 证据：risks.scoring_risks | github_repo:1164482810 | https://github.com/yantrikos/yantrikdb | no_demo; severity=medium

## 18. 安全/权限坑 · 来源证据：[bug] POST /v1/admin/snapshot unusable in single-node mode — requires cluster master token that doesn't exist

- 严重度：medium
- 证据强度：source_linked
- 发现：GitHub 社区证据显示该项目存在一个安全/权限相关的待验证问题：[bug] POST /v1/admin/snapshot unusable in single-node mode — requires cluster master token that doesn't exist
- 对用户的影响：可能影响授权、密钥配置或安全边界。
- 建议检查：来源显示可能已有修复、规避或版本变化，说明书中必须标注适用版本。
- 防护动作：不得脱离来源链接放大为确定性结论；需要标注适用版本和复核状态。
- 证据：community_evidence:github | cevd_80497be2ab644e66be4fec1a966b4c10 | https://github.com/yantrikos/yantrikdb/issues/7 | 来源讨论提到 node 相关条件，需在安装/试用前复核。

## 19. 安全/权限坑 · 来源证据：[bug] at-rest encryption `key_hex` in TOML has no effect on disk (v0.5.0)

- 严重度：medium
- 证据强度：source_linked
- 发现：GitHub 社区证据显示该项目存在一个安全/权限相关的待验证问题：[bug] at-rest encryption `key_hex` in TOML has no effect on disk (v0.5.0)
- 对用户的影响：可能影响升级、迁移或版本选择。
- 建议检查：来源显示可能已有修复、规避或版本变化，说明书中必须标注适用版本。
- 防护动作：不得脱离来源链接放大为确定性结论；需要标注适用版本和复核状态。
- 证据：community_evidence:github | cevd_ca7c8f7ee1384f9d97652734d01b8d67 | https://github.com/yantrikos/yantrikdb/issues/3 | 来源讨论提到 docker 相关条件，需在安装/试用前复核。

## 20. 安全/权限坑 · 来源证据：v0.7.6 — Drop sentence-transformers + numpy from Default Deps

- 严重度：medium
- 证据强度：source_linked
- 发现：GitHub 社区证据显示该项目存在一个安全/权限相关的待验证问题：v0.7.6 — Drop sentence-transformers + numpy from Default Deps
- 对用户的影响：可能影响升级、迁移或版本选择。
- 建议检查：来源显示可能已有修复、规避或版本变化，说明书中必须标注适用版本。
- 防护动作：不得脱离来源链接放大为确定性结论；需要标注适用版本和复核状态。
- 证据：community_evidence:github | cevd_40bcf8933f1b4ec7a559a746497c3bae | https://github.com/yantrikos/yantrikdb/releases/tag/v0.7.6 | 来源讨论提到 windows 相关条件，需在安装/试用前复核。

## 21. 安全/权限坑 · 来源证据：v0.7.8 — Extended Idempotent Migration Runner (closes #10)

- 严重度：medium
- 证据强度：source_linked
- 发现：GitHub 社区证据显示该项目存在一个安全/权限相关的待验证问题：v0.7.8 — Extended Idempotent Migration Runner (closes #10)
- 对用户的影响：可能影响升级、迁移或版本选择。
- 建议检查：来源显示可能已有修复、规避或版本变化，说明书中必须标注适用版本。
- 防护动作：不得脱离来源链接放大为确定性结论；需要标注适用版本和复核状态。
- 证据：community_evidence:github | cevd_e5a77701b7ac401a863105d996cb585c | https://github.com/yantrikos/yantrikdb/releases/tag/v0.7.8 | 来源类型 github_release 暴露的待验证使用条件。

## 22. 安全/权限坑 · 来源证据：v0.7.9 — Bundle potion-multilingual-128M (101 Languages) in embedder-download Registry

- 严重度：medium
- 证据强度：source_linked
- 发现：GitHub 社区证据显示该项目存在一个安全/权限相关的待验证问题：v0.7.9 — Bundle potion-multilingual-128M (101 Languages) in embedder-download Registry
- 对用户的影响：可能影响授权、密钥配置或安全边界。
- 建议检查：来源显示可能已有修复、规避或版本变化，说明书中必须标注适用版本。
- 防护动作：不得脱离来源链接放大为确定性结论；需要标注适用版本和复核状态。
- 证据：community_evidence:github | cevd_7a590e518c884b5b9a2bbdc995c372fd | https://github.com/yantrikos/yantrikdb/releases/tag/v0.7.9 | 来源讨论提到 python 相关条件，需在安装/试用前复核。

## 23. 维护坑 · issue/PR 响应质量未知

- 严重度：low
- 证据强度：source_linked
- 发现：issue_or_pr_quality=unknown。
- 对用户的影响：用户无法判断遇到问题后是否有人维护。
- 建议检查：抽样最近 issue/PR，判断是否长期无人处理。
- 防护动作：issue/PR 响应未知时，必须提示维护风险。
- 证据：evidence.maintainer_signals | github_repo:1164482810 | https://github.com/yantrikos/yantrikdb | issue_or_pr_quality=unknown

## 24. 维护坑 · 发布节奏不明确

- 严重度：low
- 证据强度：source_linked
- 发现：release_recency=unknown。
- 对用户的影响：安装命令和文档可能落后于代码，用户踩坑概率升高。
- 建议检查：确认最近 release/tag 和 README 安装命令是否一致。
- 防护动作：发布节奏未知或过期时，安装说明必须标注可能漂移。
- 证据：evidence.maintainer_signals | github_repo:1164482810 | https://github.com/yantrikos/yantrikdb | release_recency=unknown

