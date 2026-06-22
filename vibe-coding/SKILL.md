---
name: vibe-coding
description: 为 Java/Spring 项目提供统一代码规范与改造约束。用于用户要求“按 vibe coding 规范改造代码”、要求注释/提示/日志使用中文、或要求统一 Controller/Service/Entity/Request/VO/DAO/异常处理风格时。
---

# Vibe Coding

按以下顺序执行：

1. 先读取 `vibe-coding.md`，按其规则约束代码改造。
2. 仅在与现有项目冲突时做最小偏离，并在回复中说明原因。
3. 优先保证以下高优先级约束：
   - 注释、提示消息、日志优先使用中文。
   - 保持分层结构清晰：Controller / Service / DAO / Entity / DTO。
   - 统一返回封装与异常处理风格。
   - 写操作补齐事务边界。
   - Request 参数补齐校验注解。
4. 新增接口或改造接口时，保持路径和命名风格一致，避免破坏兼容性。
5. 若用户要求与规范冲突，以用户显式要求为准。

# 详细规范

完整规范见：`vibe-coding.md`

# 项目迭代表
- `docs/项目进度表.md` 每次做完需求必须追加需求内容

