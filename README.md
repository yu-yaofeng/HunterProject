<div align="center">

# HunterProject

**根据个人背景与 JD，从 GitHub 找到经过代码验证、值得继续改造的求职项目。**

**中文** | [English](README_EN.md)

![version](https://img.shields.io/badge/version-v0.1.0-44cc11?style=flat-square)
![license](https://img.shields.io/badge/license-MIT-2094f3?style=flat-square)
![audience](https://img.shields.io/badge/audience-Software%20Job%20Seekers-f28c45?style=flat-square)
![workflow](https://img.shields.io/badge/workflow-Discover--Verify--Choose-a500a5?style=flat-square)

</div>

---

## 中文

> 先了解这个人想成为什么样的程序员，再为他从 GitHub 找到适合求职、能够继续改造的开源项目。

HunterProject 帮助程序员发现、验证和比较值得用于求职二次开发的开源项目。它把交互方式从“输入关键词，输出仓库”变成：

```text
个人背景
→ 目标岗位或 JD
→ 岗位知识点地图
→ 搜索画像
→ 实时 GitHub 项目发现
→ 代码证据核验
→ 3–5 个合格候选
→ 用户选择 1–2 个深入检查
→ 主项目与备用项目建议
```

### 为什么需要它

很多开发者知道 GitHub 上有高质量项目，却不知道：

- 应该搜索什么；
- 如何区分真实工程项目和教程；
- 哪个仓库符合自己的技术基础、时间和目标岗位；
- 上游已经做了什么，自己还能贡献什么；
- 项目能否支撑简历和面试中的深入追问。

HunterProject 不会只根据 Star 排名。它分别评估仓库质量、岗位匹配、用户匹配和求职价值，并要求重要结论尽可能由依赖、配置、入口、测试、CI 或关键代码支持。

### 当前状态

这是一个用于工作流测试的早期 **instruction-first Agent Skill**。它目前专注于项目发现和选择，尚未包含确定性的 GitHub API 搜索脚本或完整岗位模板库。

Skill 会停在以下范围：

- 了解用户和目标岗位；
- 建立搜索画像；
- 搜索、过滤和验证候选仓库；
- 给出 3–5 个合格候选，不足时不凑数；
- 深检用户选择的 1–2 个项目；
- 推荐主项目、备用项目和个人改造方向。

项目实现、部署、简历写作和面试准备属于下游工作流，不在本 Skill 内完成。

### 真实案例

[`中国 AI 应用 / Agent 实习：两个月 RAG 项目搜索`](examples/ai-agent-rag-internship.md) 记录了一次完整运行：从个人背景和岗位知识点出发，召回约 50 个结果、静态检查 8 个仓库、比较 4 个候选，再对用户选择的 2 个项目做代码级深检，最终给出主项目、备用项目和八周改造路线。

案例明确区分 **Verified / Claimed / Inferred / Unknown**。它是一份 2026-08-16 的静态检查快照，没有运行第三方代码，也不把 README 声明当作已经验证的事实。

### 验证状态

- 1 个端到端真实案例已完成；
- 12 个行为案例已定义；
- 完整自动化评测尚未运行，因此当前不声明整体通过率。

### Skill 位置

可移植的 Skill 位于：

```text
skills/hunt-github-projects/
```

核心 `SKILL.md` 仅依赖标准的 `name`、`description` 和 Markdown 指令。`agents/openai.yaml` 是可选的 OpenAI 界面元数据，核心流程不依赖它。

### 安装

先克隆仓库：

```bash
git clone https://github.com/yu-yaofeng/HunterProject.git
```

然后将完整的 `skills/hunt-github-projects` 文件夹复制或链接到 Agent 支持的 Skills 目录。

Codex 用户级目录示例：

```text
$HOME/.agents/skills/hunt-github-projects/
```

Codex 项目级目录示例：

```text
<project>/.agents/skills/hunt-github-projects/
```

其他 Agent 可能使用不同的发现目录，请查阅对应平台的当前文档。无论使用哪种平台，都应保持整个 Skill 文件夹完整，不要只复制 `SKILL.md`。

### 使用示例

几乎没有背景信息时：

```text
$hunt-github-projects 我目前没有项目，想找一个用于求职的 GitHub 项目。
```

已经知道技术栈和时间时：

```text
$hunt-github-projects 我会 Java、Spring Boot 和 MySQL，想找后端实习，
有六周时间。帮我找几个值得继续改造、不是商城换皮的项目。
```

已有 JD 和完整背景时：

```text
$hunt-github-projects 这是我的 JD 和个人背景。
跳过我已经回答的信息，直接寻找 3–5 个经过代码证据验证的候选。
```

### 评测

行为案例位于 [`evaluations/cases.md`](evaluations/cases.md)。v0.1 的测试重点包括：

- 渐进式了解用户；
- 信息完整时走快速通道；
- 无实时访问时诚实降级；
- 合格候选不足时拒绝凑数；
- 分开判断仓库质量和用户匹配；
- 用户改变条件后废除过期排名；
- 先让用户选择候选，再给最终主项目和备用项目；
- 明确项目发现与下游实现之间的边界。

## 许可证

HunterProject 基于 [MIT License](LICENSE) 开源。

## 独立性声明

HunterProject 是独立的社区项目，与 GitHub、OpenAI 以及它可能发现和评估的仓库维护者不存在隶属或背书关系。产品名称和商标归各自权利人所有。
