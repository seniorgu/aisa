# FAQs on AI Solution Architecture (ASA) - Architectural Levels

This page answers frequently asked questions about the ASA architectural levels.

## How are the ASA architecture elements mapped to implementation services or service components? Is that a one-to-one mapping?

The ASA functional elements should not be assumed to map one-to-one to implementation service components. Here, I use the six key AI-specific elements (TOCKAM) to explain the level coverage.

ASA can express different levels of abstrations. Generally, it can represent three levels:

**Level 1 — Metamodel (Logical AI Elements)**

Level 1 generally answers the question: What AI responsibilities exist? So, it's indicated by the model element naming:

- AG  Agent
- AC  Orchestrator
- CN  Context Management
- KA  Knowledge Access
- ML  Model
- TL  Tools

**Level 2 — Solution Services**

Level 2 generally answers the question: What services realize those responsibilities? Example:

- Agent Runtime Service
- Workflow Service
- Memory Service
- RAG Service
- Model Gateway
- Tool Gateway

**Level 3 — Implementation Orientation**

Level 3 generally answers the question: what products, containers, libraries, APIs, databases, and platforms implement the services? Example:

- LangGraph
- OpenAI API
- Pinecone
- Redis
- PostgreSQL
- MCP Server
- SAP API
- Azure AI Search

## Could you give me some mapping examples?

Sure. Again, I use some AI-specific elements to illustrate the typical mapping as seen in Table 1.

| Logical Element  | Candidate Service                                                                                                          | Implemented By                                              |
| ---------------- | -------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------- |
| Context State    | Session Memory Service, Conversation Store, Working Memory Service, Long-Term Memory Service, and Memory Retrieval Service | Redis, PostgreSQL, Vector DB, and Object Storage            |
| Knowledge Access | RAG Service, Search Service, Knowledge Graph Service, and Document Access Service                                          | Azure AI Search, Elastic, Neo4j, SharePoint, and Confluence |
| Orchestrator     | Workflow Engine, Agent Runtime, Task Scheduler, Event Router, and State Manager                                            | LangGraph, Temporal, Kafka, and Custom Services             |
| Tools            | ERP Connector, CRM Connector, Email Connector, Search Connector, Database Connector, and MCP Tool Registry                 | Potentially dozens or hundreds of components.               |

Similarly, Agent can be realized by Agent Runtime, and Goal Manager, and AI Model can be realized by Model Gateway, LLM Providers, and Embedding Providers.

So, you can put different levels of elements in your AI architecture repository:

- **AI Service Architecture**
  
  - Agent Runtime Service
  - Workflow Service
  - Memory Service
  - Knowledge Retrieval Service
  - Model Gateway Service
  - Tool Gateway Service

- **AI Component Architecture**
  
  - LangGraph
  - Redis
  - Azure AI Search
  - OpenAI API
  - MCP Server
  - SAP Connector

The strength of using AI architecture elements is that they remain stable even when technologies change. 

## What is the distinction between model capability and service capability?

Good question. One reason many AI discussions can become confusing is that people often mix three different levels of capability:

- **Model capability**: reasoning, summarization, self-critique, planning
- **Service capability**: reflection, adaptation, recommendation, decision support, automation
- **Architectural capability**: governance, orchestration, observability, resilience, cost-of-change management

In fact, from an ASA perspective, there is an interesting **hierarchy**:

1. Model Capability [Example: Self-Critique (ML)]
2. Service Capability [Example: Service (AC + CN + KA + ML)]
3. Architectural Capability [Example: Adaptive Enterprise Solution (ASA)]

## How can I use the agent element in the multi-agent architecture?

The ASA elements are technology-neutral and pattern-neutral. So, for the single-agent architecture, you just use the tockam naming. For the multi-agent architecture, you can distinguish different agents by 1) same element, different description (AG-Sales Agent, AG-Procurement Agent, etc.), 2) different prefix id (AG-1, AG-2, etc.), and 3) different naming, so long as its underneath primitive element is mapped.
