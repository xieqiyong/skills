---
name: java-agentscope-agent-builder
description: 用于创建垂类 Java AI Agent 后端工程。适用于用户要求构建医疗、教育、客服、代码、法务、运维、RAG、工作流、企业智能体等场景，并希望使用 Spring Boot、AgentScope 最新依赖、agentscope-harness、三层模块化架构、JPA 初始化、MyBatis-Plus 查询、动态提示词和 Skills、完整可观测、会话/上下文/状态管理、权限治理和标准聊天 API。使用时必须先确认控制层模块名、agent-runtime 层模块名、数据实体层模块名和基础包名。
---

# Java AgentScope Agent Builder

使用本 Skill 时，帮助用户创建一个标准化的垂类 Java AI Agent 后端工程。目标不是写一个一次性 Demo，而是创建一个可扩展、可观测、可治理、可持续演进的 Agent Runtime 应用。

## 核心目标

创建一个 Spring Boot Agent 项目，让用户只需要准备这些资源，就能快速构建垂类 Agent：

```text
agent.yaml
prompts/*.md
skills/*.md
工具配置
模型配置
权限策略
```

Runtime 必须负责：

```text
会话生命周期
Agent Run 生命周期
AgentScope 执行
事件流输出
事件持久化
中断和恢复
上下文管理
状态管理
多 Agent 扩展
权限治理
动态提示词和 Skills 加载
```

## 强制要求

- 必须使用 Java 和 Spring Boot。
- 必须使用实现时可用的 AgentScope 最新依赖。
- 必须保持 `agentscope-core`、`agentscope-harness`、`agentscope-bom` 和相关 AgentScope 依赖版本一致，禁止 RC1/RC2 或不同 release 混用。
- 优先使用 `agentscope-harness` 承接 workspace、filesystem、memory、compaction、sandbox、skills、subagents、plan mode 等官方能力。
- 必须使用 JPA 负责表结构初始化和实体映射。
- 必须使用 MyBatis-Plus 负责查询、分页、复杂列表和后台管理类查询。
- 必须拆成 3 个模块，语义分别是控制层、agent-runtime 层、数据实体层。
- 必须要求用户明确提供 3 个模块名称：控制层模块名、agent-runtime 层模块名、数据实体层模块名。
- 必须要求用户明确提供基础包名。没有基础包名时，不能进入实现。
- 如果用户没有提供完整模块名和基础包名，必须先暂停并询问；不能自行默认 `runtime`、`dao`、`api` 后直接开工。
- 必须允许用户调整包名、groupId、artifactId、项目名、Agent 领域名和数据库。
- 关键业务代码必须写中文注释。注释解释设计意图、约束或非显而易见的逻辑，不写废话注释。
- 不要把医疗、法律、金融等领域回答硬编码到 Java 代码里。领域行为应放到提示词、Skills、工具、策略和资源文件中。
- 医疗、法律、金融等高风险领域必须保留安全边界、免责声明、人工确认和升级转人工机制。

## 开始前确认

实现前，从用户需求中提取或询问。以下 4 项是硬性门禁，缺任意一项都不能进入下一步实现：

```text
1. 控制层模块名，例如 api、web、adapter-web
2. agent-runtime 层模块名，例如 runtime、agent-runtime、agent-core
3. 数据实体层模块名，例如 dao、persistence、infrastructure-persistence
4. 基础包名，例如 com.example.medicalagent
```

硬性门禁满足后，再继续确认：

```text
1. Agent 领域：医疗、教育、客服、代码、运维、法务等
2. 项目名
3. 数据库，默认 PGSQL
4. 模型供应商和模型名
5. 是否需要 RAG
6. 是否需要工具调用
7. 是否需要沙箱执行
8. 是否需要多 Agent 路由/规划/执行
9. 是否只需要后端 API，默认只做后端
```

如果用户只说“帮我做一个医疗类 AI Agent”，默认使用：

```text
Java 17+
Spring Boot 3.x
MySQL
JPA + MyBatis-Plus
SSE chat-stream
AgentScope + agentscope-harness
三模块架构，但必须先让用户确认具体模块名
资源化 prompts 和 skills
```

## 架构分层

按这个关系理解：

```text
agentscope-core
  Agent 内核：ReActAgent、Model、Toolkit、ToolBase、AgentEvent、PermissionContextState、SessionKey、AgentState。

agentscope-harness
  Agent 工程外壳：HarnessAgent、workspace、filesystem、shell、sandbox、memory、compaction、skills、subagents、plan mode。

生成的业务项目
  产品平台层：API、数据库、run/message/event 持久化、SSE、审批接口、领域提示词、领域 Skills。
```

不要把 `agentscope-harness` 当成完整 SaaS 平台。它是 Runtime 能力层。业务数据模型、API、事件落库、会话管理和产品行为仍然属于生成项目。

## 模块结构

创建用户指定的 3 个模块。模块名不能写死，必须使用用户提供的名称：

```text
{控制层模块名}
{agent-runtime 层模块名}
{数据实体层模块名}
```

如果用户明确接受默认名称，才可以使用：

```text
api
agent-runtime
dao
```

### agent-runtime 层模块

放 Agent 核心运行能力。

必须包含这些概念或等价类：

```text
AgentRunCommand
AgentRunResult
RuntimeContext
RuntimeEvent
RuntimeEventSink
RuntimeEventType
AgentRuntimeService
AgentRunLifecycleService
AgentRunTraceService
AgentScopeRuntimeAdapter
AgentScopeSessionManager
AgentScopeTraceRecorder
AgentScopeEventTranslator
AgentScopePermissionContextFactory
```

如果启用多 Agent，还要包含：

```text
RouterAgent 或 RouterNode
PlannerAgent 或 PlannerNode
ExecutorAgent 或 ExecutorNode
ReviewerAgent 或 ReviewerNode，可选
MultiAgentOrchestrator
```

agent-runtime 层模块负责：

```text
1. 创建或恢复 Agent Run
2. 加载会话上下文
3. 加载提示词和 Skills
4. 组装模型、工具、权限上下文和运行上下文
5. 构建 HarnessAgent 或 ReActAgent
6. 调用 streamEvents
7. 把 AgentScope 事件转换为 RuntimeEvent
8. 通过 RuntimeEventSink 输出 SSE 事件
9. 通过 AgentRunTraceService 持久化事件
10. 保存最终 assistant 消息
11. 处理中断、审批、恢复、超时和失败
```

### 数据实体层模块

放实体、Repository、MyBatis-Plus Mapper、数据库初始化和存储接口。

JPA 用于：

```text
实体映射
表结构初始化
简单 CRUD Repository
事务型写入
```

MyBatis-Plus 用于：

```text
会话列表查询
Run 列表查询
事件回放查询
后台管理页面
复杂过滤
分页
统计
```

基础表至少包含：

```text
agent_definitions
model_configs
conversations
conversation_messages
agent_runs
agent_events
approval_requests
agent_prompts
agent_skills
agent_tool_configs
```

按功能可选增加：

```text
memory_entries
memory_conflicts
conversation_summaries
tool_calls
tool_results
sandbox_sessions
mcp_servers
rag_knowledge_bases
rag_documents
```

### 控制层模块

放 Controller、DTO、SSE 适配、异常处理和 API 契约。

至少暴露：

```text
GET  /api/conversations
GET  /api/conversations/{conversationId}
POST /api/agent-runtime/chat
POST /api/agent-runtime/chat-stream
POST /api/agent-runtime/interrupt
POST /api/agent-runtime/resume
GET  /api/agent-runtime/runs/{runId}
GET  /api/agent-runtime/runs/{runId}/events
```

`chat-stream` 必须返回 SSE。每个 SSE 事件必须携带序列化后的 `RuntimeEvent`。

## 标准运行链路

按这个生命周期实现：

```text
HTTP 请求
-> AgentRunCommand
-> 创建或加载 conversation
-> 保存 user message
-> 创建 agent_run
-> 构建 RuntimeContext
-> 加载 Agent 定义
-> 加载 prompts
-> 加载 skills
-> 加载 memory/context
-> 构建 model
-> 构建 toolkit
-> 构建 PermissionContextState
-> 构建 HarnessAgent 或 ReActAgent
-> agent.streamEvents(inputMessages)
-> doOnNext(AgentScopeTraceRecorder::record)
-> AgentScopeEventTranslator 转 RuntimeEvent
-> RuntimeEventSink.emit
-> AgentRunTraceService 保存 agent_events
-> RuntimeEventSink 推送 SSE
-> 保存 assistant message
-> 更新 agent_run 终态
```

核心流式调用形态：

```java
agent.streamEvents(inputMessages)
        .doOnNext(recorder::record)
        .collectList()
        .block(timeout);
```

如果要支持长任务生产运行，必须把后端执行和前端连接解耦：

```text
后台执行 run
持久化所有 RuntimeEvent
前端按 runId 回放事件
刷新页面后允许重新连接和恢复展示
```

## AgentScope 构建标准

优先使用 `HarnessAgent`：

```java
HarnessAgent agent = HarnessAgent.builder()
        .name(agentName)
        .description(agentDescription)
        .sysPrompt(systemPrompt)
        .model(model)
        .toolkit(toolkit)
        .permissionContext(permissionContext)
        .workspace(workspacePath)
        .maxIters(maxIterations)
        .enablePendingToolRecovery(true)
        .enablePlanMode(true)
        .build();
```

只有在项目不需要 harness 能力，或者用户明确要求裸 `ReActAgent` 时，才直接使用 `ReActAgent`。

如果 harness 内置能力和项目自研能力冲突，必须显式关闭：

```java
.disableShellTool()
.disableFilesystemTools()
.disableMemoryTools()
.disableSubagents()
.disableWorkspaceContext()
```

## 动态提示词和 Skills

支持资源化 Agent 定义：

```text
src/main/resources/agents/{agentId}/agent.yaml
src/main/resources/agents/{agentId}/prompts/system.md
src/main/resources/agents/{agentId}/prompts/developer.md
src/main/resources/agents/{agentId}/skills/*.md
```

示例 `agent.yaml`：

```yaml
id: medical-agent
name: 医疗咨询 Agent
description: 带严格安全边界的健康咨询智能体
model: default
maxIterations: 6

prompts:
  system: prompts/system.md
  developer: prompts/developer.md

skills:
  - skills/medical-triage.md
  - skills/safety-boundary.md

features:
  memory: true
  rag: false
  tools: true
  multiAgent: true
  sandbox: false
```

实现这些 Provider：

```text
AgentDefinitionProvider
PromptProvider
SkillProvider
ToolProvider
ModelProvider
PermissionPolicyProvider
GuardrailProvider
MemoryContextProvider
```

优先支持从 classpath 加载。预留数据库和文件系统加载扩展点。

## 可观测能力

完整可观测是必须项。

RuntimeEvent 必须：

```text
推送到 SSE
保存到 agent_events
支持按 runId 查询
支持页面刷新后按 runId 回放
携带 runId、traceId、type、stage、content、metadata、elapsedMs
```

至少支持这些事件类型：

```text
RUN_STARTED
CONTEXT_LOADED
AGENT_STARTED
AGENT_HANDOFF
ROUTE_SELECTED
MODEL_CALL_STARTED
MODEL_CALL_FINISHED
THINKING_STARTED
THINKING_DELTA
THINKING_FINISHED
ANSWER_STARTED
ANSWER_DELTA
ANSWER_FINISHED
TOOL_CALL_STARTED
TOOL_CALL_ARGS_DELTA
TOOL_CALL_FINISHED
TOOL_RESULT_STARTED
TOOL_RESULT_DELTA
TOOL_RESULT_FINISHED
CONFIRMATION_REQUIRED
CONFIRMATION_RESULT
RUN_STATUS_CHANGED
PLAN_CREATED
PLAN_STEP_STATUS_CHANGED
RUN_FINISHED
RUN_ERROR
RAW_EVENT
```

使用 `AgentScopeTraceRecorder` 观察 AgentScope 原始事件：

```text
AgentScope AgentEvent
-> AgentScopeTraceRecorder
-> AgentScopeEventTranslator
-> RuntimeEvent
-> RuntimeEventSink
-> AgentRunTraceService
-> SSE + agent_events
```

`AgentScopeTraceRecorder` 不直接持久化。它只负责转换和 emit。持久化必须放在 `AgentRunTraceService`。

## 权限和中断恢复

必须使用 AgentScope `PermissionContextState`。

默认权限策略：

```text
只读工具：ALLOW
写入工具：ASK
Shell 或命令工具：根据风险 ASK 或 DENY
危险命令：DENY
无人值守模式：DONT_ASK
探索模式：EXPLORE
可信自动化模式：只有明确配置时才允许 BYPASS
```

保持这个流程：

```text
模型请求工具调用
-> PermissionContextState / PermissionEngine 判断
-> ALLOW 执行工具
-> DENY 返回拒绝结果
-> ASK 产生 RequireUserConfirmEvent
-> RuntimeEventType.CONFIRMATION_REQUIRED
-> approval_requests 落库
-> 前端或 API 批准/拒绝
-> resume 接口继续执行
```

即使 AgentScope 提供确认事件，也要保留项目自己的审批表和审批 API。

## 上下文和状态

必须区分：

```text
agentId：Agent 定义
workspaceId：工作区隔离
userId：用户隔离
conversationId：业务会话
runId：一次 Agent 执行
traceId：可观测链路
sessionKey：AgentScope 状态恢复键
```

Run 状态必须包含：

```text
PENDING
RUNNING
WAITING_APPROVAL
INTERRUPTED
COMPLETED
FAILED
CANCELLED
```

必须支持：

```text
短期上下文窗口
会话消息重载
AgentState 和 SessionKey
按 runId 事件回放
审批恢复
Run 状态流转
```

如果启用记忆，必须区分：

```text
当前会话消息
滑动窗口
会话摘要
长期记忆
记忆冲突
```

## 记忆分层策略

不要把记忆简单做成“一堆历史消息”或“全部塞进 system prompt”。必须按层次设计。

优先采用这个分工：

```text
AgentScope core
  负责 AgentState、SessionKey、工具状态、pending tool recovery 等运行态状态。

agentscope-harness
  优先负责当前会话压缩、摘要、上下文裁剪、tool result eviction、memory flush 等运行时上下文管理。

项目平台层
  负责长期记忆、用户偏好、项目事实、记忆置信度、记忆冲突、人工审核、租户/用户/项目隔离。
```

必须保留平台自己的记忆接口和表结构，即使使用了 `agentscope-harness` 的 memory/compaction 能力。

标准接口建议：

```text
MemoryContextProvider
MemoryCaptureService
MemoryConflictResolver
MemoryScopePolicy
MemoryInjectionPolicy
```

标准表建议：

```text
memory_entries
memory_conflicts
conversation_summaries
```

长期记忆必须至少包含：

```text
tenantId
userId
workspaceId
projectId
agentId
scope
memoryKey
content
confidence
source
status
createdAt
updatedAt
```

记忆注入必须遵守：

```text
1. 只注入和当前任务相关的记忆
2. 按 scope 隔离，项目事实不能串到其他项目
3. 按 confidence、recency、relevance 排序
4. 有冲突的记忆不能直接注入为确定事实
5. 不允许模型在回答中反复强调“我记得你的偏好”
6. 记忆应作为上下文事实提供，而不是替代系统提示词
```

默认策略：

```text
短期会话压缩、摘要、上下文裁剪
  优先使用 agentscope-harness memory / compaction。

长期记忆、用户偏好、项目事实、审核和冲突
  使用项目自定义 MemoryProvider 和数据库。
```

## Guardrails

即使第一版不完整实现，也必须预留 Guardrail 扩展点：

```text
InputGuardrail
PromptGuardrail
ModelInputRedactor
ModelOutputGuardrail
ToolInputGuardrail
ToolOutputRedactor
```

最小内置规则：

```text
脱敏 API Key、token、password、private key、secret
拒绝直接读取 .env、证书文件、密钥文件等敏感文件
防止模型输出疑似密钥
医疗/法律/金融领域必须加入专业边界提醒
```

优先用 AgentScope `MiddlewareBase` 实现：

```text
onAgent：用户输入过滤
onReasoning：上下文治理
onModelCall：发给模型前脱敏和模型输出过滤
onActing：工具调用和工具结果治理
onSystemPrompt：系统提示词增强
```

## 多 Agent

默认多 Agent 形态：

```text
Router
-> 判断 DIRECT_ANSWER / PLAN_ONLY / PLAN_EXECUTE / SINGLE_AGENT

Planner
-> 生成结构化计划

Executor
-> 调用 AgentScope 和工具执行

Reviewer，可选
-> 审查结果或高风险变更
```

使用 `agentscope-harness` 时，优先研究和复用：

```text
SubagentsMiddleware
DynamicSubagentsMiddleware
AgentSpawnTool
AgentGenerateTool
PlanModeManager
PlanModeTools
```

简单聊天不要强行走多 Agent。必须动态路由。

## 领域特化

医疗 Agent 必须通过提示词和 Guardrail 包含：

```text
不是医生
不能替代诊断
只做健康教育和分诊建议
紧急症状必须建议立即就医
高风险症状建议线下专业医疗服务
启用 RAG 时尽量引用知识来源
```

其他领域也必须建立对应安全边界。

## 实现顺序

按顺序实现：

```text
1. 创建父 Maven 项目和用户指定的控制层 / agent-runtime 层 / 数据实体层三模块
2. 配置版本一致的 AgentScope 依赖
3. 添加 JPA 和 MyBatis-Plus 依赖
4. 创建 dao 实体、Repository、Mapper 和表初始化
5. 创建 RuntimeEvent、RuntimeEventSink、AgentRunCommand、RuntimeContext
6. 创建 AgentRunLifecycleService 和 AgentRunTraceService
7. 创建 AgentScopeEventTranslator
8. 创建 AgentScopeTraceRecorder
9. 创建 AgentScopePermissionContextFactory
10. 创建 AgentScopeSessionManager
11. 创建 AgentScopeRuntimeAdapter
12. 创建 PromptProvider 和 SkillProvider
13. 创建 AgentRuntimeService
14. 创建 API Controllers
15. 添加默认 agent.yaml、system prompt、developer prompt 和两个 skills
16. 添加 README 示例和 curl 命令
```

第一版必须跑通：

```text
chat-stream
事件持久化
会话列表
会话详情
run 事件回放
动态 prompt 加载
基础 PermissionContextState
```

之后再扩展：

```text
memory
sandbox
MCP
RAG
multi-agent
guardrails
active run 断线恢复
```

## 标准 API 契约

必须提供：

```text
GET  /api/conversations
GET  /api/conversations/{conversationId}
POST /api/agent-runtime/chat
POST /api/agent-runtime/chat-stream
POST /api/agent-runtime/interrupt
POST /api/agent-runtime/resume
GET  /api/agent-runtime/runs/{runId}
GET  /api/agent-runtime/runs/{runId}/events
```

SSE 事件名使用 `RuntimeEventType`，事件内容使用 `RuntimeEvent` JSON。

## 实现后的回复

创建或修改项目后，必须汇报：

```text
1. 创建或修改了哪些模块
2. 关键入口类
3. 新增数据库表
4. 暴露的标准 API
5. 如何新增另一个垂类 Agent
6. 用户需要配置什么，例如模型 baseUrl、模型名、API Key、数据库
7. 哪些高级能力暂未实现
```

回复保持简洁。除非实际运行过编译或测试，否则不要声称已经编译或测试通过。
