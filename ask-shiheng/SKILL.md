---
name: ask-shiheng
description: >-
  MANDATORY PRE-CODING ARCHITECTURE TRIAGE SKILL. Use this skill BEFORE writing code whenever the user wants to start a new software/AI project, add a complex feature, refactor system architecture, or decide between deterministic code vs. LLM/Agent ("Code or Agent"). Implements Software Phase Theory (软件物态学): constrains both itself and the target system via [Purpose/Telos, Process, Result/Schema], diagnoses phase combinations across the 9 software forms, and outputs a deterministic Phase Architecture Prescription (PHASE_SPEC.md) before any implementation begins.
---

# Ask Shiheng（软件物态学 · 编码前架构分诊）

> **十六字总纲**：「固态守其常，液晶取其巧，液态控其界，晶体收其功。」  
> **The 16-Word Creed**: *"Solid guards the invariant; Liquid Crystal captures the nuance; Liquid bounds the frontier; Crystal harvests the dividend."*  
> **核心纪律：先定物态，再动代码；无处方，不动刀。** (*"Diagnose the phase before touching the code; no prescription, no blade."*)

---

## 零、自指闭环：用 `[目的, 过程, 结果]` 约束本 Skill 自身

`ask-shiheng` 本身就是一件标准的**「💧 液晶态导引 + 💎 制度性晶体落盘」**软件，严格受三维因果自由度约束：
1. **【本技能目的 `Telos = 1`（绝对锁定）】**：在 Agent 敲下第一行生产代码前，强制切分目标系统的因果相空间边界，从根源上消灭“万物皆 Agent”的级联幻觉与物态错配灾难。
2. **【把脉过程 `Process = 柔性导引`】**：用极简交互式把脉，提取用户需求在 `[目的, 过程, 结果]` 上的组合特征，并映射为最优架构。
3. **【交付结果 `Schema = 1`（强类型契约）】**：必须收敛为一页纸的**《时恒物态架构处方单》**（并可固化为项目根目录的 `PHASE_SPEC.md` 制度性晶体），作为后续所有编码 Agent 的最高宪法。
4. **Language Adaptation**: Automatically respond and generate `PHASE_SPEC.md` in the user's language (English or Chinese). English reference: `../../en/skills/ask-shiheng/SKILL.md`.

---

## 第一步：初诊与「三问把脉」（Interactive Triage）

快速理解用户的项目想法（若在已有代码库中，先简要查看目录结构），给出你的**初步 `[目的, 过程, 结果]` 组合预判与错配排雷提示**，随后调用 `ask_question` 工具（DeepSeek Harness 环境；Claude Code 对应 `AskUserQuestion`；若环境不支持交互提问工具，则改用简明列表提问），向用户确认以下 **3 个核心架构决策**：

### 1. 第一问：定物态 —— 按 `[目的, 过程, 结果]` 组合切分相空间（命题零：$2^3 + 1$ 形态映射）
帮用户识别每个核心功能模块的 `[目的 d_T, 过程 d_P, 结果 d_S]`（`1`=确定锁死，`0`=柔性开放），对号入座并排查错配：

| `[目的, 过程, 结果]` 组合 | 对应软件形态（主序相 & 二阶相） | 核心架构建议与工程铁律 | 🚨 常见物态错配排雷（反面禁区） |
| :---: | :--- | :--- | :--- |
| **`[1, 1, 1]`**<br>三者全定 | 🪨 **固态（形式化晶体软件）**<br>*Lehman S-Type：算账、权限、CRUD、编译器* | **100% 纯确定性代码 / 状态机 / ACID**。<br>铁律：**严禁引入概率 LLM！** | ❌ **账本液化幻觉态**：把核心平账/状态流转交给多 Agent 群聊，必遭幻觉坏账。 |
| **`[1, 0, 1]`**<br>目的定、过程柔、结果定 | 💧 **液晶态（LLM+ 结构化转换）**<br>*Lehman P-Type：非结构化转 JSON/AST、分类提取* | **LLM + 强 Schema 掩码（Pydantic/Outlines/DSPy）**。<br>铁律：**单步偶发复杂度消除器，劝退多轮 Agent！** | ❌ **过冷正则脆断态**：把开放文本解析写死成万行正则，遇现实微扰当场雪崩。 |
| **`[1, 0, 0]`**<br>目的定、过程与局部结果自适应 | 🌊 **受控液态（容器内的极简 Agent）**<br>*Lehman E-Type：未知异常排障、动态脚本合成* | **内层百行极简探针（原生 Bash/Python）+ 外层固态容器壁**。<br>铁律：**液体不能承重，必须关进四重防爆沙盒！** | ❌ **容器破裂裸奔态**：无只读沙盒、无白名单、无轮次熔断，引发删库与算力洪灾。 |
| **`[0, 0, 0]`**<br>三者皆柔（个体发散） | ☁️ **无界气态（情感共鸣 / 创意发散）**<br>*萨特分水岭：开放脑暴、方案草拟、陪伴会话* | **开放概率采样**。<br>铁律：**必须与生产环境写操作（Writeback）物理隔离！** | ❌ **回音室扯淡耗散态**：单体无真值锚点多轮自嗨，陷入显著迎合偏差（Sycophancy Bias，Sharma et al., arXiv:2310.13548）与死锁。 |
| **`[0, 1, 1]` / `[0, *, 1]`**<br>目的未定却强锁过程/格式 | ⚠️ **伪命题僵尸态（工程禁区）**<br>*业务目标不清，盲目堆砌流程或报表* | **当场叫停编码！**<br>铁律：先帮用户澄清业务终极目的（Telos），拒绝造僵尸系统。 | ❌ **形式主义空转态**：耗费数月搭出精美工作流，上线即废弃。 |
| **`[0/液] ──(数据线)──> [1,1,1]`**<br>群体/AI 提议接通物理现实 | 💎 **制度性晶体（二阶社会性凝华）**<br>*Searle 规则 + Popper 向下因果：订单、清算、排产* | **操作型本体（Object + Link）+ Kinetic Action 2PC 回写**。<br>铁律：**提议（AI）与提交（固态代码）必须物理分离！** | ❌ **伪气态套壳泡沫**：只有聊天 UI 没有底层 Action 写回主权，商业价值归零。 |

### 2. 第二问：定裁判 —— 验收门禁与复杂度阈值 $L^*$ 选配（命题一）
针对包含 AI 的模块（💧 / 🌊 / ☁️），检查单步推理熵是否超过**复杂度临界阈值 $L^*$**（若超临界，必须先用固态 DAG 拆成多个亚临界微步），并请用户根据容错率选择裁判档位（**风险透明，选择权归用户**）：
* 🛡️ **档位 A：符号固态门禁（全自动零信任闭环）** —— 适用于写代码、SQL/JSON、调 API。由编译器、AST、Schema、单测或 Z3/ASP 求解器把守，失败自动打回或回滚。
* 👀 **档位 B：双模型初筛 + 人在环终审（半自动语义闭环）** —— 适用于写文档、方案设计。可用 Critic LLM 查漏补缺，但最终落盘或执行前**必须挂起交由人类拍板（HITL）**。
* 🎲 **档位 C：纯 LLM 自省放飞（用户知情自担风险）** —— 适用于高容错实验。温和提示实证风险（*“工程提示：PlanBench 实测纯大模型自验假阳性率约 84.45%，可能越改越偏（Valmeekam et al., arXiv:2310.08118）；若您确认可容忍该风险，将直接放行”*），确认后 100% 尊重放行。

### 3. 第三问：定数据线 —— 唯一真实写操作锚点（Middle-Out Kinetic Action，命题二 & 三）
拒绝一上来构建“全量知识图谱”或“万能多 Agent 平台”，请用户指定那根**“通往现实世界的数据线”**：
* 本期**最核心的 1 个真实写操作（Kinetic Action / 最终物理交付物）**是什么？
* 围绕这 1 个 Action，逆向倒推最小必需的强类型实体（Object）、关联（Link）与快照回滚边界。

---

## 第二步：开具《时恒物态架构处方单》（The Prescription Schema）

收到用户对三问的确认后，严格按以下四节输出高信息密度的**《时恒物态架构处方单》**：

### 1. 模块 `[目的, 过程, 结果]` 物态与裁判切分表
| 模块 / 功能点 | `[目的, 过程, 结果]` 坐标 | 所属物态 (`🪨/💧/🌊/☁️/💎`) | 驱动方式与 $L^*$ 降维策略 | 验收门禁档位 (`🛡️/👀/🎲`) 与具体裁判 |
| :--- | :---: | :---: | :--- | :--- |

### 2. 外硬内柔混合状态机拓扑（$\mathcal{M}_{\text{hybrid}}$，命题二）
用精炼的 `mermaid` 流程图画出控制流，遵循《脚手架脆弱性定理》与**「提议/提交物理分离」**：
* **外硬（宏观 100% 固态代码驱动）**：全局阶段跳转、文件/数据库快照（Snapshot）与事务回滚由确定性代码锁死；
* **内柔（微观百行极简探针）**：对 🌊 受控液态节点，拒绝几千行死板工作流捆绑，仅在只读/隔离沙盒内暴露极简原子工具（如受控 Bash/Python），保留模型流体探索能力，且只产出**待审提议（Proposal）**。

### 3. 制度性晶体与防上下文腐败红线（Middle-Out & $\Phi_{\text{MCP}}$，命题三）
* **制度性晶体硬编码（那根数据线）**：明确哪 1 个核心 `Kinetic Action`、哪几个实体主键与 Link 关联必须用确定性代码写死（严禁 LLM 裸写高危生产 SQL Join 或绕过门禁直接写库）；
* **按需作用域投射（Anti-Context-Rot）**：明确局部 AI 节点每次仅按需挂载哪几个最小必要工具/字段（$\Phi_{\text{MCP}} \le B_{\text{ctx}}$），严禁将全局 Schema 或无关历史一次性塞入上下文。

### 4. 第一步落子建议（First Concrete Move）
给出极其具体的**第一步开发动作**（例如：“1. 先写死 `solid_core/` 下的状态机数据结构与唯一 Action 提交接口；2. 再写 `liquid_crystal/` 下的单步 Schema 提取器”）。

---

## 第三步：克制收刀（Stop & Route）

开完《时恒物态架构处方单》后，**立即停下，严禁未经确认直接开始编写海量业务代码**。只向用户询问一句：

> **“《时恒物态架构处方单》已开具。是否先将其固化为项目根目录的制度性晶体 `PHASE_SPEC.md`，并按『第一步落子建议』正式动刀？”**
