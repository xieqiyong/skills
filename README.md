# 📚 AI Work Skills · 中文 Skill 创作中心

> 一套面向**中文场景**的 Agent Skills（技能）合集：从 AI 自媒体图文出图、技术科普漫画，到前后端脚手架、技术方案文档、Skill 工程本身。
>
> 每个 Skill 都是**独立、自包含的标准 `SKILL.md` 包**，兼容 Claude Code、Codex CLI、Cursor、Gemini CLI、OpenCode 等主流命令行 Agent。

作者：[@xieqiyong](https://github.com/xieqiyong) ｜ 在线预览：<https://ai.sugeapi.cn/tools/skills>

---

## ✨ 项目简介

很多通用 Agent 默认偏英文、偏代码场景，做中文自媒体图文、技术科普、国内技术栈脚手架时往往「差点意思」——风格不对、触发不灵、产出还要反复改。

本仓库把作者日常**真实在用**的 20 个 Skill 沉淀下来，统一为标准 `SKILL.md` 格式，开箱即用。覆盖四条主线：

- 🎨 **自媒体内容创作与出图**：AI 资讯、热点选题、去 AI 味写作、开源项目分享、技术图解、科普漫画、封面图
- 🛠️ **开发脚手架与代码规范**：Spring Boot 4 后端、Nuxt 3 前端、全栈编排、Java 代码规范
- 📄 **文档设计与规范**：技术方案文档、Skill 文档优化、产品规则
- ⚙️ **Skill 工程与元技能**：如何从 0 创建一个规范的 Skill

> 这些 Skill 大多围绕作者的自媒体栏目 **`@NullByte·零`**（暖橙编辑风）沉淀，可直接复用，也可改造成你自己的品牌体系。

---

## 📂 Skills 索引

共 **20** 个 Skill，按用途分为 4 类。点击目录名进入对应文件夹查看完整 `SKILL.md`。

### 🎨 一、自媒体内容创作与出图（10 个）

| 目录 | Skill 名称 | 简介 |
| --- | --- | --- |
| [`aihot`](./aihot) | aihot | 中文 AI 资讯查询：一句话拿到每日 AI HOT 日报与全部动态，无需配置任何 API Key / MCP。 |
| [`hot-topic`](./hot-topic) | 自媒体热点选题计划 | 基于真实热点事件生成结构化每日选题计划（事件背景 + 推荐标题 + 写作角度），全类目支持。 |
| [`generate-article`](./generate-article) | 去 AI 味写作 | 控制事实密度、段落节奏与表达润色，提供克制、真人感的写作约束，规避平台 AI 检测限流。 |
| [`ai-open-source`](./ai-open-source) | 今日分享 AI 开源项目 | 事实核验 + 主标题 + 文案 + 标签 + **4 张独立竖版海报**，暖橙编辑风。 |
| [`nullbyte-explainer-board`](./nullbyte-explainer-board) | Nullbyte 技术图解板 | 可爱手绘白板风：原理图 / 流程图 / 架构图 / 状态图 / 对比图。 |
| [`nullbyte-signal-board`](./nullbyte-signal-board) | Nullbyte 信号榜 | 榜单式策展与单项目拆解：AI 资讯 / 开源 / 技巧，榜单页 + 详情页。 |
| [`nullbyte-tip-manual`](./nullbyte-tip-manual) | Nullbyte 技巧手册 | 适合头条发布的中文技巧手册、命令速查表和多页知识卡。 |
| [`handdrawn-explainer-board`](./handdrawn-explainer-board) | 手绘白板图解板 | 手绘白板风信息图解、步骤流程板、原理图、对比卡及提示词模板。 |
| [`self-media-tech-thumbnail`](./self-media-tech-thumbnail) | 自媒体科技封面图 | 强视觉冲击力的中文 AI / 科技封面图与提示词（头条式戏剧化风格）。 |
| [`comic-gen-message`](./comic-gen-message) | 技术科普四格漫画 | 把技术知识 / 文章 / 概念提炼成一张简洁明亮的中文技术科普漫画。 |

### 🛠️ 二、开发脚手架与代码规范（5 个）

| 目录 | Skill 名称 | 简介 |
| --- | --- | --- |
| [`backend-springboot4-standard-framework`](./backend-springboot4-standard-framework) | Spring Boot 4 后端标准脚手架 | Spring Boot 4.0.1 + JDK 17 + Maven 多模块（DDD），整合 MyBatis-Plus / fastjson2 / Lombok。 |
| [`java-agentscope-agent-builder`](./java-agentscope-agent-builder) | Java AgentScope Agent 工程生成器 | 创建垂类 Java AI Agent 后端工程：Spring Boot + AgentScope + 三层模块化架构 + JPA/MyBatis-Plus + 可观测与会话治理。 |
| [`frontend-scaffold-setup`](./frontend-scaffold-setup) | Nuxt 3 前端脚手架 | Nuxt 3 + Vue 3 + TypeScript + Nuxt UI，路由 / 请求封装 / 权限 / 富文本一体化的中后台骨架。 |
| [`workflow-collaboration-fullstack-skills`](./workflow-collaboration-fullstack-skills) | 全栈搭建编排器 | 编排前后端两个 Skill，一次性输出全栈项目骨架、目录规划与接口协同。 |
| [`vibe-coding`](./vibe-coding) | Vibe Coding 代码规范 | Java / Spring 项目统一代码规范与改造约束（中文注释 / 分层 / 校验 / 事务）。 |

### 📄 三、文档设计与规范（3 个）

| 目录 | Skill 名称 | 简介 |
| --- | --- | --- |
| [`technical-solution-design`](./technical-solution-design) | 技术方案设计文档 | 一键生成完整技术设计方案（TDD / 系统设计 / 架构设计说明书）。 |
| [`llm-doc-china-skills`](./llm-doc-china-skills) | Skill 文档格式优化器 | 优化 Skill 文档格式与结构，让 LLM 更易理解、更易触发、执行更准确。 |
| [`product-rules`](./product-rules) | 产品规则 Skill | 项目级业务约束、交付边界与协作规则的统一沉淀。 |

### ⚙️ 四、Skill 工程与元技能（2 个）

| 目录 | Skill 名称 | 简介 |
| --- | --- | --- |
| [`skill-creator`](./skill-creator) | Skill 创建指南 | 高效 Skill 创建指南：从 0 到 1 写出一个规范、好用、易触发的 Skill。 |
| [`digital-employee`](./digital-employee) | 员工 Skill 创建者 | 为特定项目创建具备代码架构认知与排障能力的「员工 Skill」。 |

---

## 🚀 如何使用

这些 Skill 遵循标准的 `SKILL.md` 技能格式，**单个目录即一个完整技能**。任选一种方式接入：

**方式一：Claude Code（推荐）**

把需要的 Skill 目录复制到 Claude Code 的技能目录即可：

```bash
# 全局可用（所有项目）
cp -r <skill-name> ~/.claude/skills/

# 或仅当前项目可用
cp -r <skill-name> .claude/skills/
```

之后在对话中自然语言描述需求（如「今日分享一个开源 AI 项目，帮我出图」），对应 Skill 会自动触发。

**方式二：其他命令行 Agent**

本仓库的 `SKILL.md` 为通用格式，Codex CLI、Cursor、Gemini CLI、OpenCode 等兼容该格式的 Agent 均可加载，按各工具的技能/规则目录约定放置即可。

> 💡 不确定要哪个？先看下一节的在线预览，按效果图挑合适的 Skill。

---

## 🖼️ 在线预览

> **提示**：如果想预览这些 Skill 的实际效果图，请访问：
>
> 👉 **<https://ai.sugeapi.cn/tools/skills>**

页面展示了各自媒体 / 出图类 Skill 的真实产出样例（图解板、信号榜、技巧手册、封面图、开源项目海报等），方便你按效果挑选和参考。

---

## 🤝 贡献

欢迎提 Issue / PR：
- 补充新的中文场景 Skill
- 优化已有 Skill 的触发词、产出质量
- 修正描述或文档

## 📄 License

本仓库代码与 Skill 文档默认遵循 [Apache-2.0](./LICENSE) 协议（与 [`technical-solution-design`](./technical-solution-design) 一致），具体以各 Skill 目录内声明为准。欢迎个人学习与二次改造；如用于商业分发，请保留作者署名。
