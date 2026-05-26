---
inclusion: manual
---

# Deep Research Guide

This steering file guides deep multi-dimensional research using built-in web search and fetch capabilities. Include this when conducting market research for a new product idea.

## CRITICAL TOOL RESTRICTIONS

### 1. NEVER use web_fetch for binary files
- web_fetch is ONLY for HTML pages
- For logo verification: `curl -sI "[URL]" | head -5`

### 2. BLOCKED SITES - Never fetch or use URLs from:
- logos.fandom.com
- fandom.com (any subdomain)
- wikipedia.org image URLs
- wikimedia.org
- Any wiki site

### 3. APPROVED logo sources ONLY:
- Official company website (company.com/press, company.com/media)
- clearbit.com/logo or logo.clearbit.com
- brandfetch.com

**If search results show fandom/wiki URLs, SKIP THEM completely.**

## Using Built-in Tools

- **web_search**: Search the web for information across all research dimensions
- **web_fetch**: Fetch HTML pages to extract detailed information (pricing, features, positioning)

**IMPORTANT: Do NOT use web_fetch for binary files (images, logos, PDFs). Use curl.**

## Research Architecture: 6 Parallel Dimensions

Research is conducted across 6 dimensions simultaneously. Each dimension targets 8-12 iterative searches yielding 15-25 sources.

### Dimension 1: Industry Landscape

**Focus:** Market size, growth, disruption, emerging segments.

**Queries:**
```
"[industry] market size [current year]"
"[industry] market trends [current year]"
"[industry] growth forecast CAGR"
"[industry] disruption startups"
"[industry] challenges [current year]"
"[industry] technology adoption rates"
"[industry] future outlook"
"[specific sub-segment] market opportunity"
```

**Extract:** TAM/SAM/SOM with sources, growth rate, market drivers, constraints.

### Dimension 2: Competitive Intelligence

**Focus:** Direct/indirect competitors — products, pricing, strategy, gaps, funding.

**Queries:**
```
"[industry] [solution type] companies"
"alternatives to [similar products]"
"[target audience] [problem] solutions"
"[competitor] pricing"
"[competitor] features review"
"[solution category] comparison [current year]"
"[competitor] funding raised"
"[competitor] weaknesses OR complaints"
```

**For each competitor (5-7), fetch their website and pricing page.**

**Extract:** Positioning, pricing model + actual prices, features, strengths, weaknesses, funding, recent moves.

### Dimension 3: Customer & Persona Deep Dive

**Focus:** Pain points, workflow friction, buying behavior, unmet needs.

**Queries:**
```
"[target audience] daily challenges [industry]"
"[target audience] workflow tools"
"[target audience] pain points [current year]"
"[target audience] buying behavior [solution category]"
"[product category] reviews complaints"
"[target audience] forums communities"
"[target audience] productivity barriers"
"[target audience] what would make job easier"
```

**Extract:** Ranked pain points (severity × frequency), current workarounds, buying criteria, price sensitivity, adoption barriers.

### Dimension 4: Technology Radar

**Focus:** Emerging tech relevant to the product domain. AWS-first mapping.

**Queries:**
```
"AI applications [industry] [current year]"
"generative AI use cases [industry]"
"emerging technology [industry] [current year]"
"automation [target audience] workflow"
"LLM agents [industry] applications"
"AWS [relevant service] [industry] use case"
"Amazon Bedrock [industry] customer story"
"[solution category] technology stack [current year]"
```

**AWS Service Mapping:** For each technology found, identify the AWS service:
- ML/AI → Amazon SageMaker, Amazon Bedrock
- Generative AI → Amazon Bedrock (Claude, Nova, Llama, Mistral)
- Agent orchestration → Amazon Bedrock AgentCore
- IoT/edge → AWS IoT Core, Greengrass, Kinesis
- Serverless → Lambda, Step Functions
- Analytics → Athena, QuickSight, Glue
- Real-time → Chime SDK, AppSync
- Storage → S3, DynamoDB

**Extract:** Technologies mapped to AWS services, pain point × technology intersections, feasibility assessment.

### Dimension 5: Adjacent Innovation

**Focus:** What startups and adjacent industries are building in this space.

**Queries:**
```
"[top competitor] new features [current year]"
"startups solving [top pain point] [industry]"
"[industry] product launches [current year]"
"best new tools for [target audience] [current year]"
"[adjacent industry] solving similar problem"
"Y Combinator OR TechCrunch [industry] [solution area]"
"Product Hunt [solution category] [current year]"
"[industry] innovation awards [current year]"
```

**Extract:** Novel approaches, startup activity, cross-industry lessons, unmet whitespace.

### Dimension 6: Policy, Risk & Opportunity Landscape

**Focus:** Legislation, executive orders, compliance frameworks, procurement mandates, PLUS recent industry news including security incidents, public backlash, lawsuits, new adjacent opportunities, and blue ocean signals.

**Queries — Policy & Regulation:**
```
"[industry] legislation [current year]"
"[industry] AI regulation [current year]"
"[industry] executive order [current year]"
"[industry] government procurement requirements"
"[industry] compliance framework [current year]"
"[industry] data privacy laws [current year]"
"state AI legislation [industry] [current year]"
"[industry] federal funding programs [current year]"
"FedRAMP OR StateRAMP [industry] requirements"
```

**Queries — Risks & Headwinds:**
```
"[industry] security breach OR vulnerability [current year]"
"[industry] controversy OR backlash [current year]"
"[industry] lawsuit OR litigation [current year]"
"[industry] public opposition OR protest [current year]"
"AI safety concerns [industry] [current year]"
"[industry] [product category] risks [current year]"
```

**Queries — Opportunities & Blue Ocean:**
```
"[industry] new opportunity OR untapped market [current year]"
"[industry] blue ocean OR underserved segment"
"[industry] adjacent market emerging [current year]"
```

**For govtech/edtech, additionally:**
```
"[state/federal] education technology policy [current year]"
"COPPA FERPA CIPA compliance [current year] updates"
"government AI procurement guidelines [current year]"
"public sector AI adoption barriers"
"[education/government] AI backlash [current year]"
"school district AI ban OR moratorium [current year]"
```

**Extract:** Tailwinds (legislation/mandates that help), headwinds (restrictions/bans), industry risks (security breaches, backlash, lawsuits, safety incidents), emerging opportunities (blue ocean, adjacent markets, unmet demand), compliance requirements (FedRAMP, FERPA, COPPA, SOC2), procurement landscape (fiscal year timing, certifications needed).

## Quality Gate (ENFORCED)

After all 6 dimensions are researched:

| Depth | Sources Per Dimension | Total Minimum |
|-------|----------------------|---------------|
| Standard (default) | 15+ | 120+ |
| Comprehensive | 20+ | 150+ |

**If any dimension falls below its minimum:**
1. Identify which dimension(s) fell short
2. Run additional searches with broadened/alternative queries
3. Re-count and validate
4. Do NOT proceed until thresholds are met

## Consolidation Protocol

After all dimensions pass the quality gate:

1. **Deduplicate** — remove identical URLs
2. **Merge cross-references** — note when findings from different dimensions corroborate each other
3. **Flag contradictions** — where sources disagree, include both perspectives
4. **Assign relevance tiers:**
   - **Primary**: Directly relevant to the product idea
   - **Supporting**: Provides useful context
   - **Background**: General industry knowledge
5. **Number sequentially** — assign 1-N across all sources

## Source Citations (REQUIRED in HTML)

Every data claim must have a superscript citation linking to the Sources section:
```html
The market is valued at $18.2B<sup><a href="https://source">[1]</a></sup>
```

Sources section at bottom grouped by dimension with relevance tier tags.

## Output Format

Save to: `./documents/MarketResearch_[ProductName]_[YYYY-MM-DD].html`

**Required sections (stakeholder-facing — no internal process details):**
1. Executive Summary (2-3 sentences)
2. Market Sizing (TAM/SAM/SOM with cited sources)
3. Competitive Landscape (5-7 competitors with positioning, pricing)
4. Customer Insights (ranked pain points, buying behavior)
5. Technology Radar (emerging tech mapped to AWS services)
6. Adjacent Innovation (startups, novel approaches)
7. Policy, Risk & Opportunity Landscape (tailwinds, headwinds, risks, opportunities, compliance, procurement)
8. Key Risks & Opportunities
9. Contradictions & Open Questions
10. Sources (numbered, grouped by dimension, with relevance tiers)

**Do NOT include:** Research methodology details, quality gate status, source counts per dimension, or any internal process information. The quality gate is for agent self-validation only — it does not appear in the deliverable.

**Do NOT create .md or .json files.** All documents must be styled HTML.

## Research Depth Levels

| Level | Searches/Dim | Sources/Dim | Competitors | Time |
|-------|-------------|-------------|-------------|------|
| Standard | 8-12 | 15+ | 5-7 | 30-45 min |
| Comprehensive | 12-16 | 20+ | 7+ | 60+ min |

## Customer Brand Research

If building for a specific company:

**Do NOT use web_fetch to download logos. Use curl instead.**

1. **Search:** "[Company Name] logo png" or "[Company Name] press kit"
2. **Check:** Press kit or media page for official logo files
3. **Verify with curl:** `curl -sI "[LOGO_URL]" | head -5` — must show 200 OK
4. **Logo Gate:** All 5 checks must pass (HTTP 200, file size 2-50KB, visual inspection, customer brand confirmed, reason stated)
5. **Brand Colors:** Extract exact hex values from their website CSS
6. **Typography:** Identify fonts or suggest Google Fonts alternatives

Include "Brand Assets" section in the HTML with verified logo URL, colors, and fonts.

## Best Practices

1. **Cite sources** — every claim needs a numbered reference
2. **Verify recency** — prefer data from last 24 months; flag older sources
3. **Cross-reference** — note when multiple dimensions corroborate a finding
4. **Fetch pages** — don't rely on search snippets alone
5. **Iterate queries** — adapt searches based on what you find, don't just run a preset list
6. **Flag contradictions** — include both perspectives when sources disagree
7. **Be specific** — actual numbers, actual URLs, actual company names
