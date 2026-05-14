# Boundary & Risk Card

## Permissions

- Browser:
- Network:
- Filesystem:
- Credentials:
- External services:

## Hard Boundaries

- Do not use secrets without explicit user approval.
- Do not claim production safety without passing evals.
- Do not imply upstream endorsement.

## Known Risks

- External tool or browser access may expose sensitive state if used without boundaries.
- Host compatibility and installed version must be verified before real use.

## Stop Conditions

- Unknown license.
- Failed dogfooding.
- Missing source attribution.
- Tool permission unclear.

## Doramagic Source Extract

# Boundary & Risk Card / 安装前决策卡

项目：yantrikos/yantrikdb

## Doramagic 试用结论

当前结论：可以进入发布前推荐检查；首次使用仍应从最小权限、临时目录和可回滚配置开始。

## 用户现在可以做

- 可以先阅读 Human Manual，理解项目目的和主要工作流。
- 可以复制 Prompt Preview 做安装前体验；这只验证交互感，不代表真实运行。
- 可以把官方 Quick Start 命令放到隔离环境中验证，不要直接进主力环境。

## 现在不要做

- 不要把 Prompt Preview 当成项目实际运行结果。
- 不要把 metadata-only validation 当成沙箱安装验证。
- 不要把未验证能力写成“已支持、已跑通、可放心安装”。
- 不要在首次试用时交出生产数据、私人文件、真实密钥或主力配置目录。

## 安装前检查

- 宿主 AI 是否匹配：mcp_host, claude, claude_code
- 官方安装入口状态：已发现官方入口
- 是否在临时目录、临时宿主或容器中验证：必须是
- 是否能回滚配置改动：必须能
- 是否需要 API Key、网络访问、读写文件或修改宿主配置：未确认前按高风险处理
- 是否记录了安装命令、实际输出和失败日志：必须记录

## 当前阻塞项

- 无阻塞项。

## 项目专属踩坑

- 来源证据：API addition: deterministic mutation primitives (record_with_rid + friends) for cluster-mode replication（medium）：可能阻塞安装或首次运行。 建议检查：来源显示可能已有修复、规避或版本变化，说明书中必须标注适用版本。
- 来源证据：Bug: `namespace` parameter ignored in batch `remember` calls — memories always stored under `default`（medium）：可能增加新用户试用和生产接入成本。 建议检查：来源显示可能已有修复、规避或版本变化，说明书中必须标注适用版本。
- 来源证据：Migration v14→v15 fails: ALTER TABLE on edges view（medium）：可能影响升级、迁移或版本选择。 建议检查：来源显示可能已有修复、规避或版本变化，说明书中必须标注适用版本。
- 来源证据：[bug] Tombstoned memories still appear in similarity-scan recall results（medium）：可能增加新用户试用和生产接入成本。 建议检查：来源显示可能已有修复、规避或版本变化，说明书中必须标注适用版本。
- 来源证据：[bug] YANTRIKDB_ENCRYPTION_KEY_HEX env var ignored — encryption silently disabled（medium）：可能增加新用户试用和生产接入成本。 建议检查：来源显示可能已有修复、规避或版本变化，说明书中必须标注适用版本。

## 风险与权限提示

- no_demo: medium

## 证据缺口

- 暂未发现结构化证据缺口。

