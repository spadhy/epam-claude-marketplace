---
description: >
  Design or review a Salesforce solution using EPAM practice standards. Trigger when the
  user asks to "design a Salesforce solution", "architect a Salesforce implementation",
  "scope a Salesforce project", "review a Salesforce design", or any request involving
  Salesforce architecture, data model, automation, or integration decisions.
---

# Skill: salesforce-solution-design

## Purpose
Guide the user through designing a Salesforce solution that meets business requirements
while following EPAM practice standards, Salesforce best practices, and agentic
architecture principles (via the architect-foundation skill if available).

## Steps

### 1. Gather requirements
Ask for (or confirm if already provided):
- Business objective in one sentence
- Salesforce clouds / products in scope (Sales Cloud, Service Cloud, Experience Cloud, etc.)
- Key data objects and volumes
- Integration points (external systems, APIs, MCP servers)
- Non-functional requirements (compliance, performance, multi-org?)

### 2. Apply architect-foundation framework
If the `architect-foundation` skill is available, apply its five-domain checklist:
- Domain 1: Agentic architecture patterns relevant to this design
- Domain 2: Configuration vs code decisions
- Domain 3: Prompts and structured output (if AI features are in scope)
- Domain 4: Tool and MCP integration points
- Domain 5: Context, reliability, and error handling

If the skill is not available, apply the same five domains from memory.

### 3. Produce the solution design

**Executive summary** (2–3 sentences)

**Architecture overview**
- Recommended Salesforce architecture pattern
- Core components and their responsibilities
- Data model highlights (key objects, relationships, volumes)

**Automation strategy**
- Flow vs Apex decision rationale
- Trigger framework approach
- Governor limit considerations

**Integration design**
- External system connections
- API strategy (REST, SOAP, Platform Events, MCP)
- Data sync patterns

**AI / Agentforce considerations** (if applicable)
- Agent actions and topics
- Prompt template strategy
- Data Cloud integration

**Risks and mitigations**
- Top 3 risks with mitigation approach

**Open questions**
- Items requiring client clarification before finalising

### 4. Offer next steps
Suggest: ADR for key decisions, data model diagram, or detailed design for a specific
component. If the user wants a Word document, trigger the docx skill.

## Standards references
- EPAM Salesforce practice delivery standards
- Salesforce Well-Architected Framework
- architect-foundation five-domain checklist
