# GEO 官网诊断研究依据

## 核心来源

- GEO 原始论文：Pranjal Aggarwal 等，《GEO: Generative Engine Optimization》，arXiv:2311.09735，KDD 2024。论文提出以生成式引擎回答中的可见性为优化目标，GEO-Bench 包含 10K 查询，并报告部分 GEO 策略可提升最高约 40% 的可见性。来源：https://arxiv.org/abs/2311.09735
- Google Search Central，《Optimizing your website for generative AI features on Google Search》，最后更新 2026-06-05。Google 明确说明 AI Overviews/AI Mode 仍基于 Search 索引、RAG 和 query fan-out；基础 SEO、技术可访问性、非商品化内容、清晰结构仍然关键；不要为了操纵生成式回答批量制造 query 变体页面。来源：https://developers.google.com/search/docs/fundamentals/ai-optimization-guide
- Google Search Central，《AI features and your website》。Google 说明出现在 AI Overviews/AI Mode 的支持链接需页面可被索引且可显示 snippet；无额外技术要求，也不需要新的 AI 专用文件或特殊 schema；可用 robots、nosnippet、max-snippet、noindex 等控制展示。来源：https://developers.google.com/search/docs/appearance/ai-features
- Google Search Central，《Creating helpful, reliable, people-first content》。用于判断内容是否有原创信息、完整描述、超越显而易见的分析、标题是否准确、是否值得被引用。来源：https://developers.google.com/search/docs/fundamentals/creating-helpful-content
- Google Search Central，《General structured data guidelines》。结构化数据必须符合内容政策，推荐 JSON-LD，但正确标注不保证展示；结构化数据必须代表页面主体内容，不能标注隐藏或误导性内容。来源：https://developers.google.com/search/docs/appearance/structured-data/sd-policies
- Schema.org 官方类型：Article、FAQPage、HowTo、Organization。用于表达文章、问答、步骤、组织实体等机器可读关系。来源：https://schema.org/Article, https://schema.org/FAQPage, https://schema.org/HowTo, https://schema.org/Organization
- OpenAI Crawlers 官方文档。OAI-SearchBot 用于 ChatGPT 搜索结果展示；GPTBot 用于模型训练；两者 robots.txt 控制相互独立。允许 OAI-SearchBot 有助于网站出现在 ChatGPT 搜索答案中，禁止 GPTBot 表示内容不用于训练基础模型。来源：https://platform.openai.com/docs/bots
- OpenAI，《Introducing ChatGPT search》。ChatGPT Search 提供及时答案和相关网页来源链接，回答可包含来源侧栏。来源：https://openai.com/index/introducing-chatgpt-search/
- OpenAI，《SearchGPT Prototype》。SearchGPT 设计为清楚引用并链接出版方，搜索与训练分离，出版方可管理在搜索中的出现方式。来源：https://openai.com/index/searchgpt-prototype/

## 方法论吸收

来自用户提供资料的可复用原则：

- GEO 目标从传统排名转向被 AI 回答引用、摘录、提及和信任。
- 核心优化对象包括引用友好度、事实密度、结构化程度、权威信号、AI 可摘录度。
- 适合官网诊断的团队视角包括 AI 搜索研究、GEO 内容撰写、结构化优化、引用价值编辑、权威信号策略、AI 搜索转化。
- 商业可用的 GEO 诊断必须覆盖多引擎 prompt panel、重复采样、来源/引用提取、竞品对标、行动建议和业务关联。

## 诊断原则

1. 先验证可见性，再做建议。AI 搜索结果受时间、地区、登录状态、模型、检索模式和个性化影响，单次答案不能代表稳定结论。
2. 先保证基础 SEO 与可抓取性，再优化 GEO 表达。Google 官方说明没有进入 AI Overviews/AI Mode 的额外技术要求，且不需要特殊 AI 文件。
3. 用可见内容支撑结构化数据。schema 是说明页面内容，不是替代页面内容。
4. 用官方源页面承接核心实体问题。AI 引擎更容易引用清晰、权威、可验证、独立成块的页面。
5. 用证据提升可信度。统计、日期、案例、方法、作者、第三方背书和第一方数据比抽象形容词更有效。
6. 将零点击纳入转化。AI 回答可能不带来点击，因此官网需要强化品牌定义、差异化记忆、可信证据和后续查询路径。

## 不确定性与边界

- GEO 仍是快速变化领域。除原始论文和官方搜索/爬虫文档外，很多行业说法属于经验假设，必须通过 prompt panel 和发布后监测验证。
- Google 对 AI Overviews/AI Mode 的建议与第三方 GEO 工具建议可能冲突。处理冲突时优先官方可验证规则、用户价值和合规风险。
- `llms.txt` 等文件可作为内容发现或说明补充，但截至 2026-06-10，不能把它写成 Google AI 功能的必要条件。
- 生成式引擎优化不应使用隐藏文本、虚假引用、批量低质页面、误导性 schema、伪造评价或竞争对手诋毁。
