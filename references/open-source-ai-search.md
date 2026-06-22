# 开源 AI 搜索聚合与 GEO 监测工具选型

## 使用场景

当用户需要“聚合豆包、通义千问、Kimi、DeepSeek、元宝、文心等 AI 搜索结果”“搭建 GEO 监测工具”“自动采样 AI 回答”“找开源 AI 搜索项目”时使用本参考。

核心判断：多数消费级 AI 搜索产品没有稳定公开的“前台答案聚合 API”。不要默认通过爬取登录态网页实现自动化。更稳妥的方案是用开源 AI answer engine + 搜索源 + 模型 API 或 OpenAI-compatible 模型网关，构建可复现的内部采样系统；对没有 API 的产品，保留人工采样队列。

## 项目清单

| 项目 | 类型 | 适合场景 | 注意事项 |
|---|---|---|---|
| Vane / Perplexica | 开源 AI answer engine | 类 Perplexity 搜索体验，回答带来源 | 默认更偏国际模型和 SearXNG，需要适配国内模型网关 |
| Open WebUI | 多模型 UI + Web Search + RAG | 内部 GEO 采样、研究台、多模型对比 | 适合接 OpenAI-compatible API；搜索源需单独配置 |
| MindSearch | 多 Agent AI 搜索框架 | 深度搜索、多步搜索、研究型任务 | 更偏框架和研究，需要工程化封装 |
| SearXNG | 元搜索引擎 | 作为搜索结果和来源聚合层 | 不是大模型 answer engine，需要接 LLM |
| Dify | 工作流/Agent/RAG 平台 | 搭 prompt panel、采样流程、评分流程 | 不是现成 AI 搜索引擎，需要设计工作流 |
| RAGFlow | RAG/知识库问答 | 企业内部知识库和文档问答 | 更适合私有知识，不适合直接监测公网 AI 搜索 |

## 国内模型适配

优先选择支持 OpenAI-compatible API 的平台或自行写 adapter：

- 通义千问/Qwen：优先查 DashScope/百炼是否可用 OpenAI-compatible 接口。
- DeepSeek：通常可通过 OpenAI-compatible 方式接入。
- 豆包：通常走火山方舟/豆包模型 API，确认是否支持 OpenAI SDK 或兼容 endpoint。
- Kimi、文心、腾讯混元、智谱等：按官方 API 能力适配；不要把消费端网页答案等同于 API 答案。

重要边界：API 模型输出不等同于豆包、Kimi、元宝、通义千问 App/Web 前台“AI 搜索”结果。前台产品可能有自有检索、排序、引用卡片和个性化策略。自动化报告必须标注采样来源是“API 模拟”还是“产品 UI 手动采样”。

## 推荐架构

```text
Prompt 面板
  ↓
搜索源层：SearXNG / Bing / Jina / Exa / SerpAPI-compatible
  ↓
模型层：Qwen / DeepSeek / 豆包 / Kimi / OpenAI-compatible gateway
  ↓
答案生成层：Vane / Open WebUI / MindSearch / Dify workflow
  ↓
结构化记录：answer, citations, source URLs, brand mentions, competitor mentions
  ↓
评分报表：Prompt Coverage, Official Citation Rate, Citation Share, Sentiment
```

## 选型规则

| 需求 | 推荐 |
|---|---|
| 快速内部原型 | Open WebUI + SearXNG + OpenAI-compatible 国内模型 |
| 类 Perplexity 产品体验 | Vane/Perplexica + SearXNG + 模型网关 |
| 深度研究/多步检索 | MindSearch + 自定义搜索源 + 模型 API |
| 流程编排和报表 | Dify + 自定义工具节点 + 数据库/表格 |
| 企业知识库问答 | RAGFlow 或 Dify RAG |
| 只要搜索结果来源 | SearXNG |

## GEO 采样字段

每次采样至少记录：

| 字段 | 说明 |
|---|---|
| date | 采样日期和时区 |
| market | 中国/海外/全球 |
| prompt | 原始 prompt |
| intent | 品牌/品类/比较/购买/支持/安全/价格/案例 |
| engine_or_provider | 产品 UI、API 模型或自建 answer engine |
| retrieval_source | SearXNG/Bing/Jina/Exa/手动 UI/无检索 |
| answer_present | 是否给出答案 |
| brand_mentioned | 是否提及本品牌 |
| brand_rank | 本品牌在推荐列表中的位置 |
| official_cited | 是否引用官方页面 |
| citation_urls | 引用 URL 列表 |
| competitor_mentions | 竞品名称 |
| sentiment | 正/中/负/混合 |
| error_or_limit | 登录、验证码、地区、拒答、无来源等限制 |

## 评分口径

- Prompt Coverage：目标 prompts 中品牌出现的比例。
- Official Citation Rate：AI 回答引用官网或官方子域的比例。
- Citation Share：同一 prompt panel 中本品牌引用数 / 全部品牌引用数。
- Competitor Presence：竞品出现频率和推荐位次。
- Mention-Citation Gap：品牌被提及但官方源未被引用的比例。
- Source Quality：官方源、媒体、社区、百科、评测、应用商店、论坛等来源结构。

## 合规与质量边界

- 不建议爬取消费级 AI 产品的登录态前台结果，除非用户确认权限、平台条款允许且采集方式不绕过访问控制。
- 采样结果必须标注日期、地区、登录状态、模型/API 版本、检索源和重复次数。
- 不要把 API 模型结果冒充为真实产品 UI 结果。
- 不要用单次回答判定品牌 AI 可见度。
- 对当前排名、月活榜单、产品支持清单、API 兼容性等容易变化的信息，必须联网或查官方文档确认。
