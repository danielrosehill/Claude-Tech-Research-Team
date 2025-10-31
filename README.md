# Claude Stack Research Template

[![Claude Code](https://img.shields.io/badge/Claude-Code-8A2BE2?style=for-the-badge&logo=anthropic&logoColor=white)](https://claude.com/claude-code)

[![Claude Code Projects](https://img.shields.io/badge/Claude%20Code-Projects%20Index-blue?style=flat-square&logo=github)](https://github.com/danielrosehill/Claude-Code-Repos-Index)
[![Master Index](https://img.shields.io/badge/GitHub-Master%20Index-black?style=flat-square&logo=github)](https://github.com/danielrosehill/Github-Master-Index)

A comprehensive multi-agent system for conducting software and hardware technology evaluations using Claude Code.

## Overview

This repository is a **template for technology stack evaluations**. It provides a sophisticated network of specialized AI agents that work together to research, evaluate, and recommend technology solutions based on your requirements.

### What It Does

- **Software Evaluation**: Find and compare SaaS, open-source, and self-hosted solutions
- **Hardware Evaluation**: Research devices, components, and infrastructure
- **Full-Stack Analysis**: Evaluate complete technology solutions including dependencies
- **Comparative Research**: Side-by-side comparisons of known options
- **Market Research**: Pricing, availability, and sourcing information
- **Compatibility Assessment**: Platform and system compatibility verification

### Key Features

- **Multi-agent orchestration** with specialized subagents for different research tasks
- **Manager agents** that coordinate complex workflows automatically
- **Parallel research execution** for faster results
- **Structured deliverables** with consistent formatting
- **Geographic sourcing** support for hardware (US, UK, Israel, AliExpress)
- **Linux compatibility** checking built-in
- **MCP integration** for enhanced capabilities (Google Drive, Resend, etc.)

## Quick Start

### 1. Copy This Template

```bash
# Clone this repository as a template for your evaluation
cp -r Claude-Stack-Research-Template my-evaluation-project
cd my-evaluation-project
```

### 2. Start an Evaluation

Open Claude Code in this directory and provide your requirements:

```
I need to evaluate options for [describe your need]

Requirements:
- [Requirement 1]
- [Requirement 2]
- [Dealbreakers or constraints]

Budget: [Your budget]
Platform: [Linux, Windows, macOS, etc.]
```

Claude will automatically:
1. Convert your prompt to a structured specification
2. Delegate research to appropriate specialized agents
3. Conduct comprehensive evaluation
4. Generate a detailed report with recommendations

### 3. Review Your Results

Outputs will be organized in the `/outputs/` directory with:
- Executive summary with top recommendations
- Detailed analysis of each option
- Comparative tables
- Next steps and resources

## Repository Structure

```
Claude-Stack-Research-Template/
├── CLAUDE.md                      # Main agent instructions (routing logic)
├── README.md                      # This file
├── .claude/
│   ├── agents/
│   │   ├── input/                # Initial prompt processing
│   │   │   ├── prompt-to-spec.md
│   │   │   ├── context-saver.md
│   │   │   └── transcript-cleaner.md
│   │   ├── managers/             # Coordination agents
│   │   │   ├── research-lead.md       # Primary research coordinator
│   │   │   ├── output-manager.md      # Report formatting & delivery
│   │   │   ├── context-organiser.md   # Context management
│   │   │   ├── prompt-organiser.md    # Prompt organization
│   │   │   └── gitignore-manager.md   # Git management
│   │   └── team-members/         # Specialized research agents
│   │       ├── option-exploration/
│   │       │   ├── saas/saas-finder.md
│   │       │   └── open-source/open-source-finder.md
│   │       ├── research/
│   │       │   ├── evaluator.md
│   │       │   ├── reputation-checker.md
│   │       │   ├── support-check.md
│   │       │   ├── durability-probe.md
│   │       │   ├── oem-investigator.md
│   │       │   ├── pn-checker.md
│   │       │   ├── rrp-retrieval.md
│   │       │   └── spec-analysts/deep-spec-probe.md
│   │       ├── source-finders/hardware/
│   │       │   ├── us-sources-finder.md
│   │       │   ├── israel-sources-finder.md
│   │       │   ├── amazon-uk-.md
│   │       │   ├── amazon-to-israel.md
│   │       │   └── aliexpress.md
│   │       ├── compatibility/
│   │       │   ├── linux/hardware-check.md
│   │       │   ├── linux/software-check.md
│   │       │   └── mobile.md
│   │       ├── comparisons/comparisons.md
│   │       ├── report-preparation/
│   │       │   ├── ranker.md
│   │       │   └── author.md
│   │       └── specialists/deployment-process.md
│   └── commands/                 # Custom slash commands
├── context/                      # Evaluation context & background
├── outputs/                      # Generated reports & deliverables
├── prompts/                      # Evaluation requests & templates
└── ref/                         # Reference materials
```

## How It Works

### Agent Network Architecture

The system uses a **hierarchical multi-agent architecture**:

1. **Main Agent**: Entry point that routes requests based on type and complexity
2. **Manager Agents**: Coordinate specific domains (research, output, context, prompts)
3. **Specialist Agents**: Execute focused tasks (finding options, evaluating, ranking, reporting)

### Workflow Example: Software Evaluation

```
User Request
     ↓
Main Agent (analyzes request type)
     ↓
prompt-to-spec (creates structured specification)
     ↓
Research Lead Manager
     ↓
├─→ saas-finder (discovers SaaS options)
├─→ open-source-finder (discovers OSS alternatives)
     ↓
├─→ evaluator (evaluates each option against spec)
├─→ reputation-checker (checks vendor credibility)
├─→ support-check (assesses support quality)
     ↓
├─→ comparisons (side-by-side analysis)
├─→ ranker (ranks by fit)
     ↓
author (generates comprehensive report)
     ↓
Output Manager (formats and delivers)
     ↓
Final Report in /outputs/
```

### Key Managers

#### Research Lead (`managers/research-lead.md`)
Primary coordinator for all evaluation workflows. Delegates to specialized agents and synthesizes results.

**Use for:**
- Complete evaluations requiring discovery and analysis
- Multi-option comparisons
- Market research with deliverables

#### Output Manager (`managers/output-manager.md`)
Formats and delivers final reports.

**Capabilities:**
- PDF generation from markdown
- Google Drive integration (via MCP)
- Email delivery via Resend (via MCP)

#### Context Organiser (`managers/context-organiser.md`)
Manages background information and evaluation context.

#### Prompt Organiser (`managers/prompt-organiser.md`)
Organizes evaluation requests and maintains templates.

## Common Use Cases

### 1. Find SaaS Solutions
```
Main Agent → Research Lead → saas-finder → evaluator → ranker → author
```

### 2. Compare Known Options
```
Main Agent → comparisons agent → ranker → author
```

### 3. Hardware Research with Linux Compatibility
```
Main Agent → Research Lead → marketplace finders + linux/hardware-check → ranker → author
```

### 4. Find Open Source Alternatives
```
Main Agent → Research Lead → open-source-finder → evaluator → ranker → author
```

## Customization

### Adding Custom Agents

1. Create new agent file in appropriate directory:
   ```
   .claude/agents/team-members/[category]/[agent-name].md
   ```

2. Update manager agents to include new specialist in their documentation

3. Update CLAUDE.md routing logic if needed

### Adding Custom Templates

Add evaluation templates to `/prompts/templates/`:
```markdown
/prompts/templates/
├── saas-eval.md
├── oss-eval.md
├── hardware-eval.md
└── your-custom-template.md
```

## Advanced Features

### MCP Integration

The Output Manager can leverage MCP servers for:
- **Google Drive**: Automatic report saving to cloud storage
- **Resend**: Email delivery of completed reports
- **Other MCPs**: Extend with additional integrations as needed

### Parallel Research

Agents can be launched in parallel for faster results:
- Multiple marketplace finders run simultaneously
- Independent research tasks execute concurrently
- Reduces total evaluation time significantly

### Geographic Sourcing

Built-in support for hardware sourcing in:
- United States (US-based marketplaces)
- United Kingdom (Amazon UK)
- Israel (local vendors)
- International (AliExpress, Amazon international shipping)

## Best Practices

1. **Start with specs**: Always use prompt-to-spec to formalize requirements first
2. **Use managers for complexity**: Route complex evaluations through Research Lead
3. **Keep context organized**: Use context-organiser to maintain background info
4. **Archive completed work**: Move finished evaluations to archive folders
5. **Leverage templates**: Reuse evaluation templates for similar assessments

## Troubleshooting

### "Agent not finding options"
- Check your spec is clear and specific
- Verify budget constraints aren't too restrictive
- Try broadening requirements slightly

### "Inconsistent results from agents"
- Ensure all agents receive the full spec
- Check for conflicting requirements in spec
- Review context for ambiguities

### "Reports missing information"
- Verify all research agents completed their tasks
- Check that ranker received data from evaluators
- Ensure author agent has access to all findings

## Contributing

This is a template repository. Customize it for your specific evaluation needs:

1. Add industry-specific agents for your domain
2. Create evaluation templates for common patterns
3. Extend geographic sourcing for your region
4. Integrate additional MCP servers
 

## AI / Human Credit

This repository represents a collaborative effort between human and AI:

**Daniel (Human):**
- Wrote the subagent configurations
- Created the scaffold and directory structure
- Designed the slash commands for the system

**Claude (AI):**
- Fixed typos and improved clarity
- Optimised the manager configurations
- Wrote this README documentation

## Credits

Built for use with [Claude Code](https://claude.com/claude-code) by Anthropic.

## Support

For issues with this template:
- Review the CLAUDE.md routing logic
- Check agent prompt clarity
- Verify manager coordination workflows
- Consult Claude Code documentation

For Claude Code issues:
- Visit [Claude Code documentation](https://docs.claude.com/claude-code)
- Report issues at [GitHub](https://github.com/anthropics/claude-code/issues)
