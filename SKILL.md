---
name: geo-website-diagnosis
description: Diagnose and improve an official website for GEO, AI search visibility, citation readiness, and zero-click conversion. Use when Codex is asked to audit a company website, product site, landing page, docs site, blog, knowledge base, or owned content for ChatGPT Search, Google AI Overviews or AI Mode, Perplexity, Gemini, Claude, Grok, Doubao, Qianwen, Kimi, DeepSeek, Yuanbao, Wenxin, or other generative engines; produce website diagnosis, concrete page-level edits, structured data recommendations, authority-signal strategy, implementation roadmap, and monitoring plan.
---

# GEO Website Diagnosis

## Core Principle

Optimize an official website to be discoverable, trustworthy, extractable, and useful in generative AI answers. Treat GEO as an evidence-backed extension of search and content quality work: improve crawlability, entity clarity, unique expertise, citation-friendly content blocks, visible proof, structured data that matches page text, and multi-engine measurement. Do not promise guaranteed AI citation.

Load `references/diagnosis-rubric.md` for detailed scoring rules. Load `references/delivery-templates.md` when producing the final report. Load `references/research-basis.md` when explaining methodology, research support, source caveats, or why a recommendation matters. Load `references/open-source-ai-search.md` when the user asks for AI search aggregation tooling, open-source GEO monitoring, self-hosted prompt sampling, or how to test domestic engines and OpenAI-compatible model providers.

## Intake

Infer missing details when risk is low. Ask only when the website, target market, or business goal is unclear.

Collect:

- Website URL and priority page types: homepage, product pages, pricing, case studies, blog, docs, FAQ, comparison pages, help center, local pages.
- Brand/entity facts: official name, product names, aliases, founders, locations, categories, competitors, proof points, awards, certifications, customers, first-party data.
- Organization structure: group brand, sub-brands, product lines, business units, shared platform teams, regional teams, and likely owners.
- Target engines and market: global engines, China-facing engines, or both.
- Conversion goal: demo, signup, purchase, contact, download, subscription, brand trust, investor/media visibility.
- Constraints: CMS, engineering capacity, analytics access, Search Console access, legal/compliance limits.

If live browsing is available and the user requests actual diagnosis, inspect the live site, key templates, robots.txt, sitemap, metadata, visible text, structured data, page speed signals when available, and AI answer/citation samples. For current AI visibility, search or sample target engines instead of relying on memory.

## Workflow

### 1. Establish the AI Search Baseline

Build a prompt panel before judging the site:

- Brand prompts: "[brand] 是什么", "[brand] 官网", "[brand] 产品怎么样", "[brand] vs [competitor]".
- Category prompts: "best [category] tools", "[category] solution for [audience]", "[problem] how to solve".
- Commercial prompts: pricing, alternatives, comparison, implementation, ROI, security, integration, case studies.
- Trust prompts: reviews, customers, certifications, funding, leadership, data security, compliance.
- Support prompts: setup, migration, troubleshooting, API/docs, local availability.

For each engine tested, record answer presence, brand mention, citation/link, source type, sentiment, competitor mentions, outdated facts, and whether official pages are cited. Repeat priority prompts when practical and report variance.

If the user needs repeatable monitoring rather than a one-off audit, recommend an implementation pattern:

- Do not scrape logged-in consumer AI products unless the user has confirmed permission and terms allow it.
- Prefer API-backed or self-hosted answer engines for automated sampling.
- Use search-source aggregation plus model synthesis when official AI-search results are not available through APIs.
- Record raw prompts, timestamps, model/provider, retrieval source, answer text, citations, brand mentions, competitor mentions, and official-source share.

### 2. Diagnose the Website

Score the site on six dimensions:

| Dimension | Weight | What to inspect |
|---|---:|---|
| Technical discoverability | 20 | Indexability, robots, sitemap, canonical, JS-rendered content, internal links, text availability, page experience |
| Entity clarity | 15 | Consistent brand/product/category naming, about page, organization facts, sameAs profiles, author/person data |
| Citation-ready content | 25 | Definitions, standalone knowledge chunks, FAQ answers, comparison tables, claim-evidence pairs, dates, sources |
| Authority and trust | 20 | First-party data, author expertise, case studies, customers, certifications, third-party mentions, reviews, policy pages |
| Structured data integrity | 10 | JSON-LD/schema fit, visible-text parity, Organization, Product, Article, FAQPage, HowTo, BreadcrumbList |
| AI search conversion | 10 | Zero-click brand recall, soft CTA, next-step clarity, proof near claims, landing-page continuity |

Use status rules:

| Score | Status |
|---:|---|
| 85-100 | AI-Ready |
| 70-84 | AI-Ready with fixes |
| 50-69 | Needs Optimization |
| <50 | Needs Rework |

### 3. Find Page-Level Gaps

Prioritize pages that can become official sources for AI answers:

- Homepage: entity definition, category ownership, proof, navigation to source pages.
- Product/service pages: precise use case, target audience, differentiators, integrations, pricing cues, FAQs.
- Comparison pages: neutral criteria, transparent strengths/limits, evidence table, competitor entity clarity.
- Case studies: customer context, before/after metrics, implementation steps, quotes, dates, industry tags.
- Blog/guides: definitions, procedures, data-backed claims, freshness, cited sources, extractable summaries.
- Docs/help center: crawlable answers, task steps, error codes, API reference clarity, troubleshooting schema when suitable.
- About/trust pages: legal entity, leadership, author bios, security/compliance, media kit, contact and social profiles.

For each issue, state: page, evidence, impact on AI visibility, exact edit, owner, effort, priority, and validation method.

### 3B. Split by Brand and Business Unit

When the website belongs to a multi-product or multi-business organization, do not give one flat roadmap. Separate common governance from business-unit execution:

- Group/parent brand layer: entity architecture, brand facts, shared sitemap/robots/schema standards, cross-domain canonical policy, measurement, authority asset library, PR/IR/legal facts.
- Product or business-unit layer: product entity pages, commercial pages, pricing, FAQ, use cases, comparison pages, case studies, conversion paths, support content.
- Shared service layer: help center, docs, developer platform, trust/security, support, analytics, design system, CMS and frontend rendering.
- GEO governance layer: owners, publishing checklist, prompt panel, monitoring cadence, escalation path for AI answer errors.

For each layer, assign priority, owner, dependency, and acceptance criteria. If the user names separate brands, products, or business units, reflect those names in the deliverable instead of collapsing them into generic "website team" tasks.

### 4. Recommend Concrete Modifications

Give edits that a content, SEO, design, or engineering team can implement directly:

- Rewrite vague hero copy into a one-sentence entity definition plus category and audience.
- Add answer blocks of 50-150 words for high-intent questions.
- Convert unsupported claims into claim-evidence-source rows.
- Add first-party data, customer proof, dated benchmarks, or methodology notes where claims matter.
- Add comparison tables only when criteria are factual and visible on the page.
- Add FAQ sections only when answers are useful to users and visible, not schema-only.
- Add JSON-LD only when it matches visible content and follows search-engine guidelines.
- Improve internal links from broad pages to canonical source pages for each entity/topic.
- Add or repair author, reviewer, organization, product, and sameAs signals.
- Keep AI crawler controls intentional: do not block search crawlers needed for target AI search surfaces unless the user wants opt-out.

Avoid:

- Inventing citations, fake statistics, fake customer names, fake awards, or unverifiable authority signals.
- Claiming that `llms.txt`, special AI markup, or schema alone guarantees inclusion in AI answers.
- Mass-producing near-duplicate pages for fan-out query variants.
- Adding structured data for content hidden from users.
- Treating a single AI answer sample as stable evidence.

### 5. Produce the Landing Guide

Convert recommendations into a practical implementation plan:

- Default to priority order: P0 blockers, P1 business-critical fixes, P2 citation and trust improvements, P3 monitoring and authority expansion.
- Use time phases only if the user asks for a timeline or sprint plan.
- For multi-business organizations, show a "total + sub-layer" roadmap: group brand layer first, then each business unit/product line, then shared services and governance.
- Owners: content, SEO, engineering, design, legal, analytics, PR/partnerships.
- Acceptance criteria: what must be visible on page, valid in tools, indexed, cited, or measured.
- Monitoring: prompt panel, engine matrix, citation share, official-source citation rate, sentiment, competitor share, conversions.

## Tooling Guidance

When asked to build or recommend a GEO monitoring stack, distinguish three layers:

| Layer | Purpose | Examples |
|---|---|---|
| Search source | Retrieve web results and source URLs | SearXNG, Bing, Jina, Exa, SerpAPI-compatible providers |
| Answer engine | Generate cited answers from retrieved sources | Vane/Perplexica-style stacks, Open WebUI with web search, MindSearch |
| Workflow/reporting | Store prompts, run comparisons, score visibility | Dify, RAGFlow for knowledge workflows, custom CSV/DB scripts |

For China-facing GEO, state that most consumer products such as 豆包、Kimi、腾讯元宝、通义千问 and 文心/文小言 usually do not provide stable public APIs for their front-end AI search answers. Use API-compatible model providers and search-source aggregation for repeatable internal monitoring, and use manual UI sampling for products where official API access is absent or terms are restrictive.

## Output Contract

For a full audit, deliver:

1. Executive diagnosis: score, status, top 5 risks, top 5 opportunities.
2. AI answer baseline: tested engines, prompts, brand/source visibility, competitor pattern, limitations.
3. Website audit: six-dimension score with evidence.
4. Page-level modification list: concrete edits by page/template.
5. Structured data and technical recommendations: include JSON-LD examples only when useful.
6. GEO content map: required official source pages and knowledge chunks.
7. Authority-signal plan: owned, earned, third-party, community, review, media, and knowledge graph actions.
8. Landing roadmap: priority, owner, effort, dependencies, acceptance criteria. For multi-business organizations, use a total + sub-layer structure.
9. Measurement plan: prompt panel, cadence, KPI definitions, post-publish validation.
10. Risks and caveats: access limits, unverifiable data, platform variability, legal/compliance concerns.

For tooling requests, deliver:

1. Recommended architecture: search source, model provider, answer engine, storage, scoring, reporting.
2. Open-source project shortlist with fit, limits, and domestic-model adaptation path.
3. Sampling schema: prompts, engines/providers, runs, citation fields, brand/competitor scoring.
4. Compliance notes: login, scraping, robots, API terms, privacy, data retention.
5. Minimal pilot plan and acceptance criteria.

## Quality Bar

The report is acceptable only if every high-priority recommendation is tied to page evidence and an implementation action. Prefer fewer, sharper fixes over long generic checklists.

For Chinese users, write the report in Chinese unless asked otherwise. Preserve standard English terms such as GEO, AI Overviews, AI Mode, ChatGPT Search, RAG, Schema.org, JSON-LD, robots.txt, and Search Console.
