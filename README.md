# Skill

个人可复用 AI Agent Skills 仓库。这里集中维护可供 Codex、Claude Code 及其他兼容 Skills 机制的智能体使用说明、工作流和配套资源。

## 仓库结构

每个 Skill 使用一个独立的顶层目录，目录名必须与其 `SKILL.md` 中的 `name` 一致：

```text
skill/
├── README.md
└── <skill-name>/
    ├── SKILL.md
    ├── agents/
    │   └── openai.yaml
    ├── references/
    ├── scripts/
    └── assets/
```

除 `SKILL.md` 外，只有实际需要时才添加 `agents/`、`references/`、`scripts/` 或 `assets/`。

### 跨平台兼容性

- `SKILL.md` 是 Skill 的跨平台核心，包含触发条件和主要工作流。
- `references/`、`scripts/` 与 `assets/` 是按需加载的通用配套资源。
- `agents/openai.yaml` 是可选的 Codex/OpenAI 产品适配元数据，用于显示名称、简短说明和默认提示词等界面能力。
- Claude Code 使用 Skill 时不依赖 `agents/openai.yaml`；该文件不会替代或改变 `SKILL.md` 中的通用指令。
- 面向多个智能体平台发布时，可以保留各平台的可选适配文件，同时确保核心工作流不依赖任何单一平台。

## Skills

### accelerated-domain-learning

Accelerated Domain Learning（领域加速学习）帮助学习者快速建立陌生领域的可靠认知地图，并通过证据核查、深度问题和自适应追问检验真实理解。

主要能力：

- 校准学习目标、已有基础和可观察的完成标准
- 建立领域边界、前置概念、心智模型和概念关系
- 区分领域共识、主要争议、未知问题和前沿方向
- 按知识类型选择证据来源并标记事实、观点与推断
- 生成解释、辨析、边界、反例、迁移和证据判断问题
- 根据回答定位误区、补充前置知识并动态调整深度
- 用学习者自己的表达生成认知总结和后续学习路线
- 适用于科学、技术、人文、专业实践及一般知识领域

目录：[accelerated-domain-learning](./accelerated-domain-learning/)

### prd-writer

Universal PRD Writer（通用产品需求设计）把产品想法、业务需求、功能请求和已有规格整理成可评审、可验收、可执行的产品需求。

主要能力：

- 使用同一套需求内核覆盖普通数字产品、AI 产品、Agent 产品和多 Agent 系统
- 根据阅读对象、产品类型、需求规模和交付物自动选择输出深度
- 统一定义问题、用户、目标、范围、流程、功能、指标、风险和验收标准
- 按需加载普通产品交互、AI 能力、Agent 行为和 Coding Spec 模块
- 区分确定需求、假设、建议、风险、依赖和待决策事项
- 为 Codex、Claude Code、Cursor 等编程 Agent 派生实现规格
- 审核现有 PRD 的完整性、一致性、可测试性和 AI/Agent 安全边界
- 避免固定平台、框架、作者、目录和不必要的模板膨胀

目录：[prd-writer](./prd-writer/)

### ai-agent-vibe-coding

AI Agent Vibe Coding 把已确认的 PRD 或现有 AI Agent 代码库推进为分阶段、可测试、可验收、可上线的产品。

主要能力：

- 判断当前处于技术适配、核心 Agent 链路、正式前端、发布准备还是部署阶段
- 在后端先行与纵向切片之间选择适合产品形态的开发路径
- 约束 Agent 状态、持久化、Prompt、模型输出校验、工具权限和人工确认点
- 设计流式输出、轮询、失败、取消、断线、恢复和多媒体产物体验
- 区分 Mock 测试、真实模型冒烟、浏览器验证、远端部署和产品负责人验收
- 提供技术适配、阶段开发、状态矩阵、验收清单和交付报告模板
- 支持以火山引擎 veFaaS 为默认参考的上线流程，同时要求部署当日复核官方能力
- 保护凭据、数据隔离、备份恢复、成本授权和外部写入边界

目录：[ai-agent-vibe-coding](./ai-agent-vibe-coding/)

### social-visual-content-studio

把关键词、笔记、文章、链接、文件、截图、图表和混合素材转化为可信、清晰、可发布的社交媒体视觉内容。

主要能力：

- 从原始素材中提炼选题，而不是机械摘要
- 推荐目标受众、发布平台和图文或短视频形式
- 搜索、核验并记录事实来源和内容边界
- 生成轮播图、视觉笔记和短视频的完整分镜
- 建立适配用户品牌的视觉系统与生成提示词
- 逐图、逐镜审核事实、文字、可读性和平台规格
- 完成标题、正文、标签、Alt Text、旁白和字幕
- 支持小红书、Instagram、LinkedIn、TikTok、Reels、Shorts 等渠道

目录：[social-visual-content-studio](./social-visual-content-studio/)

## 安装

### Codex

复制所需 Skill 的完整目录到 Codex Skills 目录：

```bash
cp -R accelerated-domain-learning ~/.codex/skills/
cp -R prd-writer ~/.codex/skills/
cp -R ai-agent-vibe-coding ~/.codex/skills/
cp -R social-visual-content-studio ~/.codex/skills/
```

重启或重新载入 Codex 后，通过对应名称显式调用；满足 `description` 中的使用场景时也可被自动触发。

### Claude Code

将所需 Skill 的完整目录复制到 Claude 的 Skills 目录，例如：

```bash
cp -R accelerated-domain-learning ~/.claude/skills/
cp -R prd-writer ~/.claude/skills/
cp -R ai-agent-vibe-coding ~/.claude/skills/
cp -R social-visual-content-studio ~/.claude/skills/
```

具体路径和支持能力可能随客户端版本变化，请以所用客户端的当前文档为准。

## 组合工作流

这些 Skills 既可以独立使用，也可以根据任务阶段串联。前一阶段的输出可以作为后一阶段的输入，减少重复沟通，并让研究、产品定义和内容表达保持一致。

### 从陌生领域研究到产品需求

```text
accelerated-domain-learning
        ↓
     prd-writer
```

1. 使用 `accelerated-domain-learning` 建立领域地图，梳理核心概念、证据、争议和未知问题。
2. 使用 `prd-writer` 继承已经确认的研究结论，定义目标用户、产品范围、功能需求和验收标准。
3. 如需进入开发，可继续由 `prd-writer` 派生 Coding Spec。

示例：

```text
我想做一个帮助普通人理解个人碳足迹的 AI 产品。

先使用 $accelerated-domain-learning 帮我建立碳核算领域地图，
区分行业共识、争议和仍需验证的问题。

完成后，使用 $prd-writer 将研究结论整理成一份 MVP PRD，
并标记继承的事实、产品假设和待验证事项。
```

### 从产品需求到发布内容

```text
prd-writer
     ↓
social-visual-content-studio
```

1. 使用 `prd-writer` 明确产品定位、目标用户、核心功能、价值和能力边界。
2. 使用 `social-visual-content-studio` 将已确认的产品信息转化为适合目标平台的轮播图或短视频。
3. 发布内容中的产品能力、数据和限制应与 PRD 保持一致。

示例：

```text
先使用 $prd-writer 整理这款 AI 会议助手的 MVP PRD。

然后使用 $social-visual-content-studio，
基于已确认的目标用户、核心价值和能力边界，
制作一套适合 LinkedIn 发布的产品介绍轮播图。
不要把待验证假设写成已经实现的能力。
```

### 从产品需求到可验收 AI Agent 产品

```text
prd-writer
     ↓
ai-agent-vibe-coding
```

1. 使用 `prd-writer` 明确目标用户、产品范围、Agent 行为、风险边界和验收标准。
2. 使用 `ai-agent-vibe-coding` 读取已确认的 PRD 与现有代码，输出技术适配并选择后端先行或纵向切片路径。
3. 按真实业务闭环推进核心 Agent、正式前端、真实模型验证和上线准备；各阶段分别保留测试、部署与负责人验收证据。

示例：

```text
先使用 $prd-writer 把这款研究 Agent 整理成可评审的 MVP PRD。

PRD 确认后，使用 $ai-agent-vibe-coding 检查现有代码，
先给出简洁的技术适配，再完成第一条真实、可恢复、可验收的 Agent 闭环。
不要用 Mock 或构建成功冒充真实模型与产品验收。
```

### 从领域研究到产品定义与内容发布

```text
accelerated-domain-learning
        ↓
     prd-writer
        ↓
social-visual-content-studio
```

这条端到端工作流适用于从零进入一个领域并形成产品方案的任务：

1. 建立领域认知和证据基础。
2. 将机会转化为可评审、可验收的产品需求。
3. 将已经确认的产品信息转化为可信的发布内容。

每个阶段都应区分已确认事实、合理推断、产品假设和待验证事项，避免未经验证的信息被下游 Skill 当作事实使用。

## 使用示例

### Accelerated Domain Learning

```text
使用 $accelerated-domain-learning 帮我快速搞懂行为经济学。
先建立领域地图，再用深度问题检验我的理解。
```

```text
我两天后需要参加量子计算讨论，目前只有基础物理知识。
请帮我建立可靠的认知骨架，明确共识、争议和未知问题。
```

### Universal PRD Writer

```text
使用 $prd-writer 把这个产品想法整理成一份给产品和研发评审的 MVP PRD。
```

```text
为这个研究 Agent 编写 PRD，定义工具权限、上下文、人工确认、失败恢复和评估指标，
然后派生一份可交给 Codex 实现的 Coding Spec。
```

### Social Visual Content Studio

```text
使用 $social-visual-content-studio 分析这组文章和截图，
推荐最值得发布的选题、平台与内容形式，并给出完整制作方案。
```

```text
把这份行业报告做成适合 LinkedIn 的轮播图，
核验关键数据，先输出内容简报和逐页分镜。
```

```text
把这个产品演示整理成 45 秒竖屏短视频，
交付逐镜脚本、旁白、字幕和关键帧提示词。
```

### AI Agent Vibe Coding

```text
使用 $ai-agent-vibe-coding，根据这份已确认的 PRD 和现有代码，
判断当前阶段并完成下一条最小真实 Agent 闭环。
分别报告 Mock 测试、真实模型冒烟、浏览器验证和负责人验收状态。
```

## License

本仓库暂未添加开源许可证。在许可证明确之前，默认保留所有权利。
