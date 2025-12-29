# Sales Copilot MCP

AI-powered sales execution plugin for Claude Code. Combines proven methodologies with deal intelligence to help you close more deals.

## What This Does

- **Teaches you how to sell** - 5 proven frameworks (Braun, Voss, Sandler, MEDDPICC, Challenger)
- **Coaches your calls** - Analyzes transcripts, scores performance, identifies gaps
- **Qualifies your deals** - MEDDPICC scorecards, stakeholder mapping, deal health
- **Handles objections** - Complete library with methodology-driven responses
- **Writes your outreach** - Cold email, LinkedIn, and follow-up templates
- **Prepares for battle** - Competitive positioning and battle card templates

---

## Installation

In Claude Code, run:
```
/plugin marketplace add Daniiar9/sales-copilot-mcp
/plugin install sales-copilot-mcp
```

Or via CLI:
```bash
npx claude-plugins install @Daniiar9/sales-copilot-mcp
```

---

## Methodologies Included

| Framework | Best For | Core Principle |
|-----------|----------|----------------|
| **Josh Braun** | Cold outreach | Detachment sells. Neediness repels. |
| **Chris Voss** | Negotiations | Tactical empathy disarms resistance. |
| **Sandler** | Discovery | Pain drives action. No pain, no sale. |
| **MEDDPICC** | Enterprise deals | Rigor prevents happy ears. |
| **Challenger** | Complex sales | Teach, don't pitch. |

---

## Usage Examples

**Prepare for a call:**
> "Help me prepare for a discovery call with Acme Corp. They're a Series B fintech."

**Analyze a transcript:**
> "Review this call transcript and score it against the coaching rubric."

**Handle an objection:**
> "The prospect said 'it's too expensive.' How should I respond?"

**Write outreach:**
> "Write a cold email to a VP of Sales at a 200-person SaaS company."

**Qualify a deal:**
> "Score this deal on MEDDPICC. Here's what I know: [context]"

**Map stakeholders:**
> "Help me build a stakeholder map for this deal. My main contact is [name]."

**Competitive positioning:**
> "We're competing against [competitor]. What landmine questions should I ask?"

---

## What's Included

### Core Skill
- `SKILL.md` - Main skill with methodology overview, deal stages, and qualification framework

### Reference Files
| File | What It Contains |
|------|------------------|
| `methodologies.md` | Deep dive on all 5 sales frameworks with scripts and techniques |
| `stakeholder-mapping.md` | Power mapping, multi-threading, buying committee analysis |
| `outreach-templates.md` | Cold email, LinkedIn, follow-up, and voicemail templates |
| `objection-bank.md` | Complete objection library with L.A.R.P. framework |
| `call-coaching-rubric.md` | 8-dimension scoring system for call analysis |
| `integration-spec.md` | Technical spec for CRM and call tool integrations |
| `battle-cards-template.md` | Template for competitive battle cards |

---

## Call Coaching Dimensions

When you ask the AI to analyze a call, it scores on:

1. **Talk Ratio** - Did you talk <40%?
2. **Question Quality** - Open-ended, strategic questions?
3. **Pain Discovery** - Specific, quantified pain found?
4. **Listening** - Mirrored, labeled, followed threads?
5. **Stakeholders** - Mapped the org and politics?
6. **Next Steps** - Specific, mutual, dated commitment?
7. **Objection Handling** - Probed root cause?
8. **Methodology** - Applied frameworks appropriately?

---

## MEDDPICC Qualification

| Element | Question |
|---------|----------|
| **M**etrics | What business outcome are they measuring? |
| **E**conomic Buyer | Who signs the check? |
| **D**ecision Criteria | What are they evaluating on? |
| **D**ecision Process | What's the buying process? |
| **P**aper Process | Legal, procurement, security? |
| **I**mplicate Pain | What happens if unsolved? |
| **C**hampion | Who sells internally for you? |
| **C**ompetition | Who else are they evaluating? |

---

## Future Integrations

The plugin includes specs for connecting to:

- **CRM**: HubSpot, Salesforce, Pipedrive
- **Call Intelligence**: Fathom, Fireflies, Gong
- **Knowledge Base**: Notion, Confluence
- **Competitive Intel**: Klue, Crayon

---

## Contributing

PRs welcome! Especially for:

- Additional objection responses
- Industry-specific templates
- New methodology frameworks
- Integration implementations

---

## License

MIT

---

## Author

Built by [@Daniiar9](https://github.com/Daniiar9) reach out sdaniiar95@gmail.com

**Methodologies referenced:**
- Josh Braun - Detachment Selling
- Chris Voss - Never Split the Difference
- Sandler Training - Pain Funnel
- MEDDPICC - Enterprise Qualification
- Challenger Sale - Teach, Tailor, Take Control
