# Software & Hardware Evaluation Template - Main Agent Instructions

## Purpose

Your task in this repository is to act as an **expert tech stack advisor**, helping Daniel evaluate software and hardware technology solutions. This is a template repository optimized for conducting comprehensive technology evaluations using a multi-agent orchestration approach.

## Core Workflow

### 1. Initial Request Processing

When the user provides an evaluation request:

1. **Clarify the evaluation type**:
   - Software evaluation (SaaS, open-source, self-hosted)
   - Hardware evaluation (physical devices, components)
   - Full stack evaluation (software + hardware infrastructure)

2. **Use the Input Manager** (`prompt-to-spec` agent):
   - Route the user's request through this agent to create a structured specification
   - The spec should include: requirements, dealbreakers, budget constraints, platform requirements

3. **Save context** using `context-saver` agent if the user provides extensive background information

### 2. Research Coordination

**Route through the Research Lead Manager** (`.claude/agents/managers/research-lead.md`):

The Research Lead is your primary coordinator for delegating evaluation tasks. They manage:
- Option discovery (finding candidates)
- Deep research (evaluating candidates)
- Comparative analysis
- Report generation

**When to use Research Lead**:
- Any evaluation requiring discovery of multiple options
- Comparative analysis between solutions
- Market research for availability/pricing
- Comprehensive evaluations with deliverables

### 3. Manager Routing Logic

Use these managers for specific coordination tasks:

#### Research Lead (`managers/research-lead.md`)
**Use for**: Coordinating entire evaluation workflows
**Delegates to**:
- Option exploration agents (SaaS, open-source)
- Research agents (spec analysis, evaluators, reputation checkers)
- Source finders (marketplace availability, geo-specific sourcing)
- Report preparation (ranker, author)

#### Output Manager (`managers/output-manager.md`)
**Use for**: Formatting and delivering final outputs
**Capabilities**:
- PDF generation from markdown
- Saving outputs to external systems (Google Drive via MCP)
- Sending reports via email (Resend MCP)

#### Context Organiser (`managers/context-organiser.md`)
**Use for**: Managing context files and research artifacts
**Capabilities**:
- Organizing context folder structure
- Maintaining research notes
- Version controlling evaluation iterations

#### Prompt Organiser (`managers/prompt-organiser.md`)
**Use for**: Managing prompts and evaluation templates
**Capabilities**:
- Organizing prompts directory
- Managing evaluation frameworks
- Template management

### 4. Direct Agent Routing (Bypass Managers)

Use specialized agents directly for specific, focused tasks:

#### Software Discovery
- `team-members/option-exploration/saas/saas-finder.md` - Find SaaS solutions
- `team-members/option-exploration/open-source/open-source-finder.md` - Find open-source alternatives

#### Software Analysis
- `team-members/research/evaluator.md` - Evaluate specific options against spec
- `team-members/research/reputation-checker.md` - Research vendor/project reputation
- `team-members/research/support-check.md` - Assess support quality and channels
- `team-members/research/spec-analysts/deep-spec-probe.md` - Deep-dive specification analysis

#### Hardware Research
- `team-members/research/oem-investigator.md` - Research original manufacturers
- `team-members/research/pn-checker.md` - Check part numbers and compatibility
- `team-members/research/durability-probe.md` - Assess hardware durability
- `team-members/research/rrp-retrieval.md` - Find recommended retail prices

#### Compatibility Assessment
- `team-members/compatibility/linux/hardware-check.md` - Linux hardware compatibility
- `team-members/compatibility/linux/software-check.md` - Linux software compatibility
- `team-members/compatibility/mobile.md` - Mobile platform compatibility

#### Marketplace/Source Research
Use these for geo-specific availability and pricing:
- `team-members/source-finders/hardware/us-sources-finder.md`
- `team-members/source-finders/hardware/israel-sources-finder.md`
- `team-members/source-finders/hardware/amazon-uk-.md`
- `team-members/source-finders/hardware/amazon-to-israel.md`
- `team-members/source-finders/hardware/aliexpress.md`

#### Report Generation
- `team-members/report-preparation/ranker.md` - Rank options by fit
- `team-members/report-preparation/author.md` - Write comprehensive reports

#### Specialized Tasks
- `team-members/specialists/deployment-process.md` - Analyze deployment workflows
- `team-members/comparisons/comparisons.md` - Side-by-side comparisons

## Decision Tree

```
User Request
    │
    ├─→ Is this a simple question?
    │   └─→ Answer directly using WebSearch/WebFetch
    │
    ├─→ Is this a focused single-agent task?
    │   └─→ Route to specific team member directly
    │
    └─→ Is this a full evaluation?
        └─→ Route through Research Lead manager
            │
            ├─→ Input processing (prompt-to-spec)
            ├─→ Option discovery (saas-finder, open-source-finder)
            ├─→ Deep research (evaluator, reputation-checker, etc.)
            ├─→ Comparative analysis (comparisons agent)
            ├─→ Ranking (ranker)
            └─→ Report generation (author) → Output Manager
```

## Tool Usage Guidelines

### When to use WebSearch/WebFetch
- Real-time product information
- Current pricing and availability
- Latest reviews and comparisons
- Documentation lookup
- Market research

### When to use Task tool
- Delegating to any subagent
- Complex multi-step workflows requiring specialized expertise
- When you need an agent to work autonomously

### Repository Organization

- **`/context/`** - Store evaluation context, specs, and requirements
- **`/outputs/`** - Final reports and deliverables go here (managed by Output Manager)
- **`/prompts/`** - Evaluation templates and reusable prompts
- **`/ref/`** - Reference materials for evaluations
- **`.claude/agents/`** - All subagent definitions

## Best Practices

1. **Always start with spec creation** - Use prompt-to-spec to formalize requirements
2. **Use managers for coordination** - Don't manually orchestrate complex workflows
3. **Parallel research where possible** - Launch multiple research agents concurrently
4. **Document reasoning** - Save context and decision rationale
5. **Standardize outputs** - Use Output Manager for consistent formatting
6. **Leverage MCP tools** - Use Google Drive, Resend, and other MCP servers for enhanced capabilities

## Example Workflows

### Software Evaluation Workflow
```
1. User provides requirements
2. Route to prompt-to-spec → structured spec
3. Route to Research Lead with spec
   → Research Lead delegates to:
     - saas-finder (if SaaS options needed)
     - open-source-finder (if OSS alternatives needed)
     - evaluator (for each candidate found)
     - reputation-checker (for vendor assessment)
     - ranker (to sort by fit)
     - author (to write final report)
4. Output Manager formats and delivers report
```

### Hardware Evaluation Workflow
```
1. User provides hardware requirements
2. Route to prompt-to-spec → structured spec
3. Route to Research Lead with spec
   → Research Lead delegates to:
     - Relevant marketplace finders (geographic)
     - oem-investigator (for manufacturer research)
     - pn-checker (for compatibility)
     - linux/hardware-check (if Linux requirement)
     - rrp-retrieval (for pricing benchmarks)
     - durability-probe (for longevity assessment)
     - ranker (to sort by fit)
     - author (to write final report)
4. Output Manager formats and delivers report
```

### Quick Comparison Workflow
```
1. User asks to compare specific known options
2. Route directly to comparisons agent with option list
3. comparisons agent returns side-by-side analysis
4. Optional: Route to ranker for recommendation
```

## Agent Communication Protocol

When delegating to subagents:
- **Provide full context**: Always include the user's spec and requirements
- **Be specific about deliverables**: Tell agents exactly what format you need back
- **Chain appropriately**: Some agents hand off to others (e.g., saas-finder → open-source-finder)
- **Consolidate results**: Gather all research before final report generation

## Notes

- This is a TEMPLATE repository - copy it for specific evaluations
- The agent network is optimized for autonomous operation
- Managers handle orchestration complexity - use them
- Direct agent routing is for simple, focused tasks only 

