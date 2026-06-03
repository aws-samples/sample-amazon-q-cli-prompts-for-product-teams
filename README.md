# Product Team's Tool Chest

A comprehensive toolkit that transforms AI coding assistants into your personal product development partner. Go from idea to interactive prototype with specialized support for AI/ML products.

## Overview

This toolkit provides **steering files for [Kiro](https://kiro.dev)** that guide an AI assistant through a complete product development workflow:

> **What is Kiro?** Kiro is an AI-powered IDE that uses "steering files" to guide AI behavior with project-specific instructions. Steering files are markdown documents in `.kiro/steering/` that provide context, workflows, and constraints. When you work in Kiro, these files automatically shape how the AI assistant responds - no manual prompting required.

```
Discovery → Deep Market Research → PRFAQ → PRD → Prototype
```

Each phase produces professional deliverables as styled HTML documents that can be viewed in a browser and shared with stakeholders.

## Quick Start (Kiro)

1. **Copy steering files** to your project:
   ```bash
   cp -r .kiro/steering/* your-project/.kiro/steering/
   cp .kiro/hooks.json your-project/.kiro/
   ```

2. **Open your project in Kiro** and describe your product idea

3. **The workflow runs automatically:**
   - Market research with web search
   - PRFAQ (Press Release / FAQ) using Working Backwards methodology
   - PRD with detailed requirements
   - Interactive HTML prototype with modular screens

All outputs are **standalone HTML files** that open directly in any browser - no build step or server required. Share them with stakeholders by simply sending the files.

## Workflow Phases

### Phase 1: Deep Market Research
- 6 parallel research dimensions (Industry, Competitive, Customer, Technology, Innovation, Policy/Regulatory)
- 120+ sources minimum with quality gates
- Market sizing (TAM/SAM/SOM with sources)
- Customer pain points research
- Technology radar mapped to AWS services
- Customer brand research (logo, colors) if applicable

**Output:** `MarketResearch_[Product]_[Date].html`

### Phase 1b: AI Framing (Optional)
Only for AI/ML products. Defines:
- ML problem type (classification, regression, etc.)
- Input/output schemas
- Success metrics and thresholds
- Training data requirements

### Phase 2: PRFAQ
Amazon-style Working Backwards documentation:
- Press Release (as if product already launched)
- FAQ addressing customer and business questions
- Incorporates market research findings

**Output:** `PRFAQ_[Product]_[Date].html`

### Phase 3: PRD (Requirements)
Implementation-ready specification:
- User personas with detailed profiles
- Requirements in EARS syntax (When/The/Shall format)
- User stories with acceptance criteria
- Current-year technology research (validated against latest AWS services)
- Inline SVG architecture diagrams
- Success metrics and business model
- Challenge Check stress-tests PRFAQ assumptions before writing

**Output:** `PRD_[Product]_[Date].html` + `.kiro/specs/[product]/requirements.md`

### Phase 4: Prototype
Interactive HTML prototype with:
- **Modular file structure** (not monolithic)
- Distinctive visual design (no generic "AI slop")
- Chart.js data visualizations (bundled locally, no CDN)
- Realistic interaction patterns (state persists via localStorage, no toast-only responses)
- Working navigation between screens
- Form validation with visible state changes
- Responsive layouts (desktop, tablet, mobile)
- Adversarial Bug Hunt pass (assumes bugs exist, finds and fixes them)
- Realistic data (no Lorem ipsum)

**Output:**
```
documents/
├── lib/chart.min.js                      (bundled Chart.js — no CDN)
├── [product-slug].css                    (shared design tokens)
├── DesignSystem_[Product]_[Date].html    (visual reference)
├── ScreenIndex_[Product]_[Date].html     (navigation hub)
├── Screen_Dashboard_[Product]_[Date].html
├── Screen_[Name]_[Product]_[Date].html   (one per screen)
└── ProjectDashboard_[Product]_[Date].html
```

## File Structure

```
CLAUDE.md                       (auto-loads in Claude Code)
.cursorrules                    (auto-loads in Cursor)

.kiro/
├── steering/
│   ├── product-workflow.md     (main orchestration - always loaded)
│   ├── design-standards.md     (visual standards - always loaded)
│   ├── market-research.md      (deep research guide - manual)
│   ├── prfaq-guide.md          (PRFAQ guide - manual)
│   ├── prd-guide.md            (PRD guide + tech research - manual)
│   ├── prototype-spec-guide.md (interaction spec - manual)
│   └── prototype-guide.md      (prototype guide - manual)
└── hooks.json                  (agent hooks for automation)

prompts/                        (Claude Code / Cursor workflow)
├── Claude_Code_Workflow.md     (main workflow guide)
├── Deep Research Agent.md      (6 parallel dimensions, quality gates)
├── PRFAQ Guide.md
├── PRD Creation Guide.md       (includes Technology Research)
├── Prototype Spec Guide.md     (interaction blueprint)
└── Prototype Creation Guide.md

documents/                      (auto-generated outputs)
├── MarketResearch_*.html       (Deep Research output)
├── PRFAQ_*.html
├── PRD_*.html
├── PrototypeSpec_*.html        (Interaction Spec)
├── DesignSystem_*.html
├── Screen_*.html
└── ProjectDashboard_*.html

samples/                        (example outputs for reference)
├── DesignSystem_TeenFit.html
├── PRFAQ_TeenFit.html
├── PRD_TeenFit.html
└── Screen_*.html
```

## Steering Files

| File | Inclusion | Purpose |
|------|-----------|---------|
| `product-workflow.md` | always | Main workflow orchestration |
| `design-standards.md` | always | Visual design standards |
| `market-research.md` | manual | Web-based research guide |
| `prfaq-guide.md` | manual | PRFAQ creation guide |
| `prd-guide.md` | manual | PRD and Kiro spec guide |
| `prototype-guide.md` | manual | Prototype creation guide |

## Agent Hooks

Pre-configured hooks in `.kiro/hooks.json` provide 26 PM-focused agents:

**Automatic Validation (on file save):**
- Deep Market Research, PRFAQ, PRD, AI Framing validators
- Design System Consistency (prevents AI slop)
- Tech Stack Validator (prefers AWS-native services)

**Core Workflow (manual):**
- Run Deep Market Research → Create PRFAQ → Create PRD → Create Prototype

**Research & Analysis:**
- Customer Interview Simulator (roleplay as personas)
- Competitive Response Analyzer
- User Journey Mapper
- Risk Analyzer
- Competitor Feature Matrix

**Strategy:**
- Feature Prioritizer (RICE)
- A/B Test Hypothesis Generator

**Prototype & UX:**
- Microcopy Writer
- Onboarding Flow Designer
- Accessibility Auditor (WCAG)

**Team & Communication:**
- Stakeholder Update Generator
- Demo Script Writer
- Meeting Notes to Requirements

See `.kiro/hooks.json` for the full hook configuration.

## Design Standards

The toolkit enforces distinctive design to avoid generic "AI slop":

**Anti-Patterns (never use):**
- Generic fonts: Inter, Roboto, Arial
- Purple-to-blue gradients on white
- Uniform card grids
- Bootstrap/Tailwind defaults
- Excessive emojis (unless essential to product tone)

**Required:**
- Distinctive typography per aesthetic direction
- 60-30-10 color rule (dominant/secondary/accent)
- Bouncy animations for key moments
- Visual texture (gradients, shadows, depth)
- Modular file structure for prototypes

## Validation

Each phase includes validation checkpoints:
- Completeness - All required sections present
- Quality - Content is specific and sourced
- Consistency - Aligns with previous phases
- Format - Correct naming conventions

The workflow will not proceed until validation passes.

## AWS-Native Architecture

As an AWS-provided toolkit, PRD technical designs prefer AWS services for enterprise-grade scalability, security, and compliance:

- **Compute:** Lambda, ECS, EC2, App Runner
- **Database:** DynamoDB, Aurora, RDS
- **Generative AI:** Amazon Bedrock, Bedrock AgentCore, Amazon Q
- **Storage:** S3, EFS
- **API:** API Gateway, AppSync
- **Auth:** Cognito

Amazon Bedrock provides access to foundation models from Amazon (Nova) and third-party providers (Anthropic Claude, Meta Llama, Mistral, and more).

## Claude Code / Cursor Mode

For Claude Code or Cursor, copy the auto-loading config files to your project:

```bash
cp CLAUDE.md your-project/       # For Claude Code
cp .cursorrules your-project/    # For Cursor
cp -r prompts/ your-project/prompts/
cp -r .claude/ your-project/.claude/   # Claude Code: subagents, skills, validation hooks
```

The workflow loads automatically when you open your project. Just describe your product idea and the AI will guide you through the phases.

### Native Claude Code primitives

Alongside the prose guides, the toolchest ships native Claude Code integration (the guides in `prompts/*.md` remain the single source of truth — these primitives are thin layers over them):

- **Subagents** (`.claude/agents/`) — `deep-research`, `prfaq`, `prd`, `design-system`, `screen-builder`, `product-reviewer`. A full build runs the Orchestrator, which dispatches these per phase. The Prototype phase runs `design-system` once, then one `screen-builder` per screen in parallel — each screen gets its own isolated context.
- **Skills** (`.claude/skills/`) — `product-research`, `product-prfaq`, `product-prd`, `product-prototype`. A solo user can invoke a single phase's expertise inline; the relevant guide loads only when that phase is active (progressive disclosure).
- **Validation hooks** (`.claude/settings.json`) — on Write/Edit of a `Screen_*.html` a JS syntax gate parses each inline `<script>`; on a `PRD_*.html` an SVG well-formedness + paint check runs. Advisory only (never blocks an edit). **Cross-platform:** it detects the machine and prefers native validators (macOS `osascript`/`xmllint`/`plutil`), falls back to `node --check`/`python3` on Linux/Windows, and if no validator exists it warns and skips rather than silently passing.

No code ships with the toolchest: hooks are inline config in `settings.json` (not committed scripts), and chart libraries are downloaded at build time into the gitignored `documents/lib/`.

See `prompts/Claude_Code_Workflow.md` for the complete workflow guide.

## Requirements

- **[Kiro](https://kiro.dev)** (recommended) - AI-powered IDE with native steering file support
- **Or** any AI coding assistant with file system access (Claude Code, Cursor, etc.)
- Web search capability for market research phase (built into most AI tools)

## Output Format

All documents are generated as **self-contained HTML files**:
- No external dependencies beyond Google Fonts CDN
- Chart.js is bundled locally in `documents/lib/` (no CDN required)
- Open directly in any browser (`open documents/PRD_MyProduct_2026-01-06.html`)
- Print to PDF for offline sharing
- Fully styled with professional formatting

## Sample Files

The `samples/` folder includes example outputs from a "TeenFit" project:

```
samples/
├── DesignSystem_TeenFit.html      (design tokens & components)
├── PRFAQ_TeenFit.html             (press release & FAQ)
├── PRD_TeenFit.html               (product requirements)
├── Screen_Dashboard_TeenFit.html  (prototype screen)
├── Screen_Welcome_TeenFit.html    (prototype screen)
└── Screen_WorkoutExecution_TeenFit.html
```

Open any sample in your browser to see the output quality and design standards. The Design System sample includes extensive comments explaining the design philosophy.

## Security

See [CONTRIBUTING](CONTRIBUTING.md#security-issue-notifications) for more information.

## License

This library is licensed under the MIT-0 License. See the LICENSE file.
