# GEO Website Diagnosis

一个用于官网 GEO（Generative Engine Optimization）诊断的 Codex Skill。它帮助你审计官网、产品站、落地页、文档站、博客、帮助中心等自有内容在 ChatGPT Search、Google AI Overviews / AI Mode、Perplexity、Gemini、Claude、Grok、豆包、通义千问、Kimi、DeepSeek、腾讯元宝、文心/文小言等生成式搜索场景中的可见度、可引用性和转化承接能力。

> GEO 不承诺“保证被 AI 引用”。本 Skill 的目标是用可验证的网站质量、实体清晰度、可引用内容块、权威信号、结构化数据和监测体系提升官网成为 AI 答案来源的概率。

## What It Does

- 建立 AI 搜索基线：品牌、品类、商业、信任、支持类 prompt 面板。
- 按六个维度给官网打分：技术可发现性、实体清晰度、可引用内容、权威与信任、结构化数据完整性、AI 搜索转化。
- 输出页面级修改建议：具体页面、证据、影响、改法、优先级、负责人和验收标准。
- 生成 GEO 知识块地图：定义、FAQ、对比、案例、步骤、证据块。
- 给出 Schema.org / JSON-LD 和技术 SEO 建议。
- 设计落地路线图和监测计划，支持多品牌、多产品线、多事业部场景。
- 提供开源 AI 搜索/监测工具栈建议。

## Repository Structure

```text
.
├── SKILL.md
├── agents/
│   └── openai.yaml
└── references/
    ├── delivery-templates.md
    ├── diagnosis-rubric.md
    ├── open-source-ai-search.md
    └── research-basis.md
```

## Usage

把本目录作为 Codex Skill 安装或复制到你的 Codex skills 目录后，在对话中使用：

```text
Use $geo-website-diagnosis to audit https://example.com for GEO visibility.
```

中文示例：

```text
用 $geo-website-diagnosis 诊断我们官网 https://example.com 的 GEO 可见度，输出页面级修改建议、Schema 建议和 30 天落地路线图。
```

更完整的输入建议：

```text
请诊断 https://example.com：
- 目标市场：中国 + 海外
- 重点引擎：ChatGPT Search、Google AI Overviews、Perplexity、豆包、通义千问、Kimi
- 转化目标：预约演示和销售线索
- 重点页面：首页、产品页、定价页、案例页、帮助中心
- 竞品：A、B、C
```

## Output Format

完整诊断通常包含：

1. 执行摘要：总分、状态、Top 风险、Top 机会。
2. AI 搜索基线：测试引擎、prompt、品牌出现、官方源引用、竞品模式。
3. 六维评分表：证据驱动的打分和优先改进项。
4. 页面级修改建议：可直接交给内容、SEO、设计、工程团队执行。
5. 结构化数据和技术建议：JSON-LD 示例仅在匹配可见内容时提供。
6. GEO 内容地图：官方源页面和知识块规划。
7. 权威信号计划：自有、外部、社区、媒体、评论、知识图谱。
8. 落地路线图：优先级、owner、依赖、验收标准。
9. 监测计划：prompt panel、频率、KPI 定义、发布后验证。
10. 风险与限制：样本量、登录限制、平台波动、合规边界。

## Notes

- 不要伪造客户、奖项、数据、引用或案例。
- 不要添加与页面可见内容不一致的结构化数据。
- 不要把 `llms.txt`、特殊 AI 标记或 Schema 当作保证收录的方案。
- 自动化监测应优先使用 API 或自托管工具；对登录态消费级 AI 产品要遵守产品条款和权限边界。

## License

MIT License. See [LICENSE](./LICENSE).
