<div align="center">

# HunterProject

**根据个人背景与 JD，从 GitHub 找到经过代码验证、值得继续改造的求职项目。**

[中文](#中文) | [English](#english)

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

---

## English

> Learn who the user wants to become as a programmer, then find open-source projects that fit their job search and leave meaningful room for extension.

HunterProject helps programmers discover, verify, and compare open-source repositories worth building on for internships, new-grad roles, job changes, and portfolio-based hiring.

It changes the interaction from “keyword in, repository out” to:

```text
person
→ target role or JD
→ role knowledge map
→ search profile
→ live GitHub discovery
→ code-evidence verification
→ 3–5 qualified candidates
→ user selects 1–2 for deep inspection
→ primary and backup recommendation
```

### Why it exists

Many developers know that GitHub contains valuable projects but do not know what to search for, how to distinguish a real engineering project from a tutorial, or which repository fits their skills, timeframe, and target role.

HunterProject evaluates repository quality, role fit, user fit, and career value separately. Important claims should be supported by repository metadata, manifests, configuration, entry points, tests, CI, or feature code rather than README text alone.

### Current status

This repository contains an early, instruction-first Agent Skill for workflow testing. It does not yet include a deterministic GitHub API search script or a complete role-pack library.

The Skill focuses on discovery and selection. It deliberately stops before implementation, deployment, resume writing, and interview preparation.

### Real example

[`China AI application / Agent internship: a two-month RAG project search`](examples/ai-agent-rag-internship.md) documents one end-to-end run: roughly 50 search results recalled, 8 repositories statically inspected, 4 candidates compared, and 2 user-selected projects deeply inspected before choosing a primary project, a backup, and an eight-week extension plan.

The case separates **Verified / Claimed / Inferred / Unknown** evidence. It is a static-inspection snapshot dated 2026-08-16; no third-party code was executed.

### Validation status

- 1 end-to-end real scenario completed;
- 12 behavior cases specified;
- the full automated suite has not been run, so no overall pass rate is claimed.

### Install

Clone the repository:

```bash
git clone https://github.com/yu-yaofeng/HunterProject.git
```

Copy or link the complete `skills/hunt-github-projects` directory into the Skills directory supported by your agent. For Codex, examples include:

```text
$HOME/.agents/skills/hunt-github-projects/
<project>/.agents/skills/hunt-github-projects/
```

Other agents may use different discovery directories. Keep the complete Skill folder together and consult that agent's current documentation.

### Try it

```text
$hunt-github-projects I have no projects yet. Help me find a GitHub project for my job search.
```

```text
$hunt-github-projects I know Java, Spring Boot, and MySQL, want a backend internship,
and have six weeks. Find several non-mall projects worth extending.
```

```text
$hunt-github-projects Here is my JD and background. Skip questions I already answered
and find 3–5 candidates supported by current repository evidence.
```

### Evaluation

Behavior cases are available in [`evaluations/cases.md`](evaluations/cases.md). They cover guided intake, fast-lane routing, honest no-web fallback, no-padding behavior, user-specific fit, stale-ranking invalidation, candidate feedback, and workflow boundaries.

## License

HunterProject is released under the [MIT License](LICENSE).

## Independence

HunterProject is an independent community project. It is not affiliated with or endorsed by GitHub, OpenAI, or the maintainers of repositories it may discover and evaluate. Product names and trademarks belong to their respective owners.
