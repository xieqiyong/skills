---
name: product-rules
description: 面向 databuff-digital-expert 项目的产品规则技能。用于在本仓库内开发或调整专家、训练、AI Agent、Kafka、导入导出、配置与文档时，统一遵循已确认的业务约束、交付边界和协作规则。
---

# Product Rules

## 使用范围

- 仅适用于 `E:\ai-work\databuff-digital-expert` 当前仓库。
- 默认只关注本项目代码、配置、文档和业务链路。
- 不主动讨论或改动 `opencode-spring-boot-starter`，除非用户明确要求。
- 不读取或引用项目里的 `root-skills-creator` 作为实现依据，除非用户明确要求。

## 开发总原则

- 优先最小改动，不随意重构训练、发布、导入导出等主流程。
- 先核对现有代码、配置和文档，再动手实现，避免按记忆写代码。
- 业务真相源优先数据库显式关系，不依赖隐式推断。
- 若用户最新要求与既有规则冲突，以用户最新明确指令为准。

## 当前关键业务约束

- AI Agent 与专家的关系以 `de_agent_expert_binding` 为准，`auto_binding` 视为历史兼容逻辑，不再扩展。
- `agent_path` 表示技能目录，`root_path` 表示 Agent 根目录，`opencode.json` 位于 `root_path`。
- 专家 `expertSource=CREATED` 才允许修改、删除和手工管理，`GENERATED` 默认只读。
- 训练时间配置使用 `Duration` 写法；`artifact-grace-period` 表示产物最大等待时间，不是固定睡眠时间。
- Kafka `serviceVersion` 当前是独立入库链路，只消费 `type=41` 消息，并从 `data.containerStatuses[].image` 提取 tag；在用户明确要求前，不直接接入训练版本来源。
- 不同来源的专家可以共用同一套绑定与刷新规则，但不要为了统一而改坏现有训练主链路。

## 实施要求

- Controller 默认使用 `POST`。
- 注释、提示消息、日志优先使用中文。
- 每次需求完成后，必须将本次迭代简要追加到 `docs/项目迭代进度表.md`。
- 遇到用户自己的改动或脏工作区，不擅自回退。
- 先解释风险和边界，再做可能影响主链路的调整。

## 优先参考资料

- `docs/资源存储结构说明.md`
- `docs/项目迭代进度表.md`
- `docs/技术方案设计文档.md`

## 避免事项

- 不把外部项目逻辑混入本仓库。
- 不在未确认样例前臆造 Kafka 消息结构。
- 不混用字段语义，例如 `expertType` 不承载 `expertSource` 语义。
- 不把训练来源误当作 Agent 绑定关系的依据。