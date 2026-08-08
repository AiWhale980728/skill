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
cp -R social-visual-content-studio ~/.codex/skills/
```

重启或重新载入 Codex 后，通过对应名称显式调用；满足 `description` 中的使用场景时也可被自动触发。

### Claude Code

将所需 Skill 的完整目录复制到 Claude 的 Skills 目录，例如：

```bash
cp -R accelerated-domain-learning ~/.claude/skills/
cp -R social-visual-content-studio ~/.claude/skills/
```

具体路径和支持能力可能随客户端版本变化，请以所用客户端的当前文档为准。

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

## 新增 Skill 的约定

1. 使用小写字母、数字和连字符命名目录。
2. 必须包含有效的 `SKILL.md`，YAML frontmatter 只保留 `name` 和 `description`。
3. `description` 同时写清能力和触发场景。
4. 主流程保持精简，详细规则放入 `references/`。
5. 可重复且需要确定性的操作优先沉淀到 `scripts/`。
6. 不提交密钥、账号信息、私人素材或无授权资产。
7. 提交前检查相对链接、YAML、目录命名和示例提示词。
8. 每新增一个 Skill，同步更新本 README 的 Skills 清单。

## 维护原则

- 通用优先：避免硬编码个人身份、固定品牌、单一平台或特定年份。
- 事实可追溯：区分事实、观点、用户素材和创意表达。
- 渐进加载：只在任务需要时读取详细参考文件。
- 非破坏性：生成物和修改版保留版本号，不覆盖原始素材。
- 能力透明：没有所需工具时，交付可执行方案，不伪装成已完成外部操作。

## License

本仓库暂未添加开源许可证。在许可证明确之前，默认保留所有权利。
