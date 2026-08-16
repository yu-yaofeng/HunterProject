# 中国 AI 应用 / Agent 实习：两个月 RAG 项目搜索

> 这是一次脱敏后的 HunterProject 端到端运行记录。检查日期：2026-08-16。

[中文](#中文) | [English summary](#english-summary)

## 中文

### 1. 用户与岗位画像

- **目标岗位：** 中国 AI 应用 / Agent 实习；
- **当前路线：** Python、FastAPI、RAG，暂时没有可展示项目；
- **交付周期：** 8 周；
- **运行约束：** Windows 本地优先，不依赖昂贵 GPU，模型与 API 应可替换；
- **必须覆盖：** Python、API、RAG 数据链、带引用回答、Agent / tool calling、评测、测试与 Docker；
- **求职目标：** 项目需要能真正运行，也要留下足够的个人改造空间，便于解释设计选择和工程取舍。

### 2. 搜索与核验过程

本轮从约 50 个搜索结果中进行召回，静态检查了 8 个仓库的目录、依赖、入口、关键实现、测试、CI、Docker 和许可证。没有执行候选仓库中的不受信任代码。

证据标签：

- **Verified：** 在仓库文件或代码中直接确认；
- **Claimed：** 仅由 README 或作者说明声称；
- **Inferred：** 根据多个证据作出的推断；
- **Unknown：** 本轮无法确认。

### 3. 第一轮候选

| 候选 | 定位 | 入选理由 | 主要风险 |
| --- | --- | --- | --- |
| [`weiwill88/Local_Pdf_Chat_RAG`](https://github.com/weiwill88/Local_Pdf_Chat_RAG) | 推荐 Base | 本地 RAG 链路完整，Python / FastAPI 清晰，Windows 改造门槛较低 | 索引与元数据缺少持久化，引用结构和评测仍需加强 |
| [`openai/openai-knowledge-retrieval`](https://github.com/openai/openai-knowledge-retrieval) | 备选 Base | 检索、重排、生成与评测覆盖更丰富 | 默认依赖外部 API，成本和 Windows 运行复杂度更高 |
| [`danny-avila/rag_api`](https://github.com/danny-avila/rag_api) | 后端型 Base | 更适合强调服务端 API 与 RAG 后端工程 | 与用户的本地优先和完整展示目标匹配度略低 |
| [`didilili/shopkeeper-agent`](https://github.com/didilili/shopkeeper-agent) | Reference | 可参考 Agent 交互和业务包装 | 用户匹配与可控改造空间不足，不作为主 Base |

用户选择前两个候选继续深检。

### 4. 深检结论

#### 主项目：Local_Pdf_Chat_RAG

**Verified：** [`rag_demo.py`](https://github.com/weiwill88/Local_Pdf_Chat_RAG/blob/main/rag_demo.py)、[`core/retriever.py`](https://github.com/weiwill88/Local_Pdf_Chat_RAG/blob/main/core/retriever.py) 和 [`core/generator.py`](https://github.com/weiwill88/Local_Pdf_Chat_RAG/blob/main/core/generator.py) 显示了以下主链路：

```text
upload
→ text extraction and chunking
→ all-MiniLM embedding
→ FAISS + BM25 retrieval
→ CrossEncoder reranking
→ cited context
→ Ollama or SiliconFlow answer
```

它适合作为主项目，因为代码规模可控、链路容易讲清楚，并且存在真实的工程缺口，方便形成个人所有权。

**需要改造的缺口：**

- 索引和元数据主要停留在内存；
- FastAPI 与 Gradio 入口耦合；
- 引用从回答文本中解析，缺少结构化来源对象；
- 缺少持久化、认证、系统化 RAG 评测和完整 Docker 交付。

#### 备用项目：openai-knowledge-retrieval

**Verified：** [`retrieval/pipeline.py`](https://github.com/openai/openai-knowledge-retrieval/blob/main/retrieval/pipeline.py) 和 [`evals/harness.py`](https://github.com/openai/openai-knowledge-retrieval/blob/main/evals/harness.py) 提供了更丰富的检索与评测参考。

它更适合当备用项目和架构参考：技术覆盖强，但默认的模型调用、成本、上传能力和 Windows 工作流会增加八周交付风险。其 [`memory_store.py`](https://github.com/openai/openai-knowledge-retrieval/blob/main/app/backend/app/memory_store.py) 也说明部分会话状态仍以内存方式保存。

### 5. 八周个人改造路线

1. 从 `rag_demo.py` 拆出上传、解析与分块服务；
2. 使用 Qdrant 或持久化 FAISS，并用 SQLite 保存文件元数据和任务状态；
3. 将引用改成结构化对象，保留文件、chunk、页码或位置；
4. 增加一个真实 Agent 工具，并处理参数校验、失败和超时；
5. 建立 20–30 条固定查询评测集，记录 Recall@K、MRR、引用正确率与拒答准确率；
6. 补充 pytest、GitHub Actions、Docker、日志和一键启动说明。

### 6. 最终建议

- **主项目：** `weiwill88/Local_Pdf_Chat_RAG`；
- **备用项目：** `openai/openai-knowledge-retrieval`；
- **策略：** 用主项目保证八周内完成可运行交付，从备用项目借鉴检索和评测设计，而不是把两个仓库简单拼接。

### 7. 局限与声明

这是 2026-08-16 的静态检查快照。仓库后续可能变化；Star、维护状态和依赖兼容性应在实际使用前重新核验。本轮未安装依赖、运行测试或执行候选代码，因此这里没有宣称这些仓库能够在用户环境中直接通过运行验证。

---

## English summary

This sanitized case records one complete HunterProject run for a China-based AI application / Agent internship candidate with an eight-week delivery window. The search recalled roughly 50 results, statically inspected 8 repositories, compared 4 qualified candidates, and deeply inspected the 2 selected by the user.

The final recommendation was [`weiwill88/Local_Pdf_Chat_RAG`](https://github.com/weiwill88/Local_Pdf_Chat_RAG) as the primary base and [`openai/openai-knowledge-retrieval`](https://github.com/openai/openai-knowledge-retrieval) as the backup and architecture reference. The proposed ownership work includes persistence, structured citations, a real Agent tool, retrieval evaluation, tests, CI, Docker, and logging.

This is a static-inspection snapshot dated 2026-08-16. No third-party dependency installation, test execution, or untrusted-code execution was performed.
