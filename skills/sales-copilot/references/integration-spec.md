# Integration Specification

Technical spec for connecting Sales Copilot with external tools.

---

## Architecture Overview
```
SALES COPILOT MCP
|
|-- Methodology Engine (Braun, Voss, Sandler, MEDDPICC, Challenger)
|
|-- Context Engine
|   |-- Product Knowledge Base
|   |-- Deal Context
|   |-- Competitor Intel
|
|-- Feedback Engine
|   |-- Call Analysis
|   |-- Deal Scoring
|   |-- Coaching
|
INTEGRATION LAYER
|
|-- CRM (HubSpot, Salesforce, Pipedrive)
|-- Calls (Fathom, Fireflies, Gong)
|-- Knowledge Base (Notion, Confluence)
|-- Competitive (Klue, Crayon)
|-- Social Listening (LinkedIn, G2, Reddit)
```

---

## 1. CRM Integration

**Purpose**: Pull deal context, update stages, track activities

**Supported Platforms**:

| Platform | API Type | Auth Method |
|----------|----------|-------------|
| HubSpot | REST | OAuth 2.0 / API Key |
| Salesforce | REST | OAuth 2.0 |
| Pipedrive | REST | API Key |
| Close | REST | API Key |

**Data to Pull**:

- Deal: id, name, stage, amount, close_date, owner
- Contacts: name, role, email, title
- Activities: type, date, notes
- Custom fields

**Data to Push**:

- Update deal stage
- Add notes
- Log activities
- Update contact roles

**Example Tools**:
```
crm_get_deal(deal_id) -> Deal
crm_list_deals(filters) -> Deal[]
crm_update_deal(deal_id, updates) -> Deal
crm_add_note(deal_id, note) -> void
crm_log_activity(deal_id, activity) -> void
```

---

## 2. Call Intelligence Integration

**Purpose**: Analyze transcripts, provide coaching

**Supported Platforms**:

| Platform | Features |
|----------|----------|
| Fathom | Transcripts, summaries, action items |
| Fireflies | Transcripts, sentiment, topics |
| Gong | Transcripts, talk ratio, questions |
| Chorus | Transcripts, deal insights |
| Otter | Transcripts, highlights |

**Data to Pull**:

- Call metadata: date, duration, participants
- Transcript: speaker, timestamp, text
- Metrics: talk_ratio, question_count, longest_monologue
- Summary and action items

**Example Tools**:
```
calls_get_recent(limit) -> Call[]
calls_get_transcript(call_id) -> Transcript
calls_analyze(call_id) -> CallAnalysis
calls_get_coaching(call_id) -> CoachingFeedback
```

**Analysis Output**:
```
call_analysis:
  scores:
    talk_ratio: 4
    question_quality: 3
    pain_discovery: 5
    listening: 4
    stakeholder_mapping: 2
    next_steps: 5
    objection_handling: 3
    methodology: 4
    total: 30
  
  highlights:
    - timestamp: 245
      type: good_question
      quote: "What happens if you don't solve this?"
      feedback: "Great implication question"
  
  action_items:
    - "Ask about other stakeholders next call"
    - "Quantify the pain in dollars"
```

---

## 3. Knowledge Base Integration

**Purpose**: Load product context so AI knows what you sell

**Supported Sources**:

| Source | Method |
|--------|--------|
| Notion | API |
| Confluence | API |
| Google Docs | API |
| Markdown files | Local / Git |

**Data Structure**:
```
knowledge_base:
  product:
    name: string
    description: string
    features:
      - name: string
        description: string
        differentiator: boolean
    pricing:
      model: string
      tiers: Tier[]
    use_cases: UseCase[]
    
  competitors:
    - name: string
      strengths: string[]
      weaknesses: string[]
      when_they_win: string
      when_we_win: string
      
  customers:
    - name: string
      industry: string
      use_case: string
      results: string
      quotable: string
```

**Example Tools**:
```
kb_search(query) -> KBResult[]
kb_get_product() -> ProductInfo
kb_get_competitor(name) -> CompetitorInfo
kb_get_objection_response(objection) -> string
```

---

## 4. Competitive Intelligence Integration

**Purpose**: Battle cards and competitive positioning

**Supported Platforms**:

| Platform | Features |
|----------|----------|
| Klue | Battle cards, win/loss, alerts |
| Crayon | Competitive intel, tracking |
| Custom | Manual battle cards |

**Data Structure**:
```
battle_card:
  competitor: string
  last_updated: date
  
  strengths:
    - point: string
      counter: string
      
  weaknesses:
    - point: string
      how_to_exploit: string
      
  feature_comparison:
    - feature: string
      us: string
      them: string
      
  landmines:
    - question: string
      purpose: string
```

**Example Tools**:
```
compete_get_battle_card(competitor) -> BattleCard
compete_list_competitors() -> string[]
compete_get_landmines(competitor) -> Landmine[]
```

---

## 5. Social Listening Integration

**Purpose**: Monitor market signals, competitor activity

**Supported Sources**:

| Source | What to Monitor |
|--------|-----------------|
| LinkedIn | Competitor posts, job postings |
| G2 | Reviews, comparisons |
| Reddit | Industry discussions |
| Twitter/X | Announcements, sentiment |

**Data Structure**:
```
signal:
  source: string
  type: string
  date: datetime
  content: string
  url: string
  relevance_score: number
  sentiment: string
  summary: string
```

**Example Tools**:
```
listen_get_recent(sources) -> Signal[]
listen_search(query) -> Signal[]
listen_get_competitor_activity(competitor) -> Signal[]
```

---

## Authentication

Store credentials as environment variables:
```
# CRM
HUBSPOT_API_KEY=xxx
SALESFORCE_ACCESS_TOKEN=xxx
PIPEDRIVE_API_KEY=xxx

# Calls
FATHOM_API_KEY=xxx
FIREFLIES_API_KEY=xxx
GONG_ACCESS_KEY=xxx

# Knowledge Base
NOTION_TOKEN=xxx
CONFLUENCE_API_TOKEN=xxx

# Competitive
KLUE_API_KEY=xxx
```

---

## Error Handling

Standard error response:
```
{
  "isError": true,
  "content": [{
    "type": "text",
    "text": "Error: [description]. Try: [suggestion]."
  }]
}
```

---

## Implementation Priority

**Phase 1 (Core)**:
1. CRM integration (HubSpot first)
2. Call intelligence (Fathom first)
3. Knowledge base (Notion/Markdown)

**Phase 2 (Enhanced)**:
4. Additional CRM platforms
5. Additional call platforms
6. Competitive intelligence

**Phase 3 (Advanced)**:
7. Social listening
8. Real-time alerts
9. Workflow automation
