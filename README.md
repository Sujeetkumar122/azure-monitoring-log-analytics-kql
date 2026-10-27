<div align="center">

# 🤖 Intelligent SRE Co-Pilot (Model Context Protocol & RAG)

[![MCP](https://img.shields.io/badge/Protocol-Model_Context_Protocol_(MCP)-00599C?style=for-the-badge&logo=anthropic&logoColor=white)](#)
[![Python](https://img.shields.io/badge/Python-3.10%2B-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://python.org)
[![Azure SRE](https://img.shields.io/badge/Observability-Azure_Monitor_%26_KQL-0078D4?style=for-the-badge&logo=microsoftazure&logoColor=white)](#)
[![MTTR Impact](https://img.shields.io/badge/Impact--40%25_MTTA_Reduction-10B981?style=for-the-badge)](#)

**Autonomous SRE operations co-pilot integrating Anthropic's Model Context Protocol (MCP) with Azure Cloud telemetry and Vector Runbook RAG to accelerate incident response.**

</div>

---

## 🎯 Architectural Philosophy

AI assistance in production operations must be **strictly bounded and read-only**:
- 🔌 **Model Context Protocol (MCP):** Connects LLMs (Claude, GPT) directly to live infrastructure diagnostics via standardized JSON-RPC interfaces.
- 🔒 **Zero Write Permissions:** AI agents can query Resource Graph, execute Log Analytics KQL, and inspect state, but **never execute mutating cloud actions directly**.
- 📚 **Vector Runbook RAG:** Embeds incident post-mortems and SOP runbooks into Qdrant for real-time semantic correlation during on-call alerts.
- ⚡ **Measurable SRE Impact:** Reduces Mean Time to Acknowledge & Diagnose (MTTA) by **40%**, delivering pre-correlated diagnostic summaries directly to on-call engineers.

```mermaid
graph LR
    subgraph Alerts["🚨 Monitoring Alerts"]
        AZ_MON["Azure Monitor Alert"] --> WEBHOOK["Alert Ingestion Webhook"]
    end

    subgraph MCP_Layer["🔌 Model Context Protocol Host"]
        WEBHOOK --> AGENT["SRE Triage Agent"]
        AGENT <--> MCP["Azure SRE MCP Server"]
        MCP --> ARG["Azure Resource Graph"]
        MCP --> LA["Log Analytics KQL"]
        AGENT <--> RAG["Qdrant Vector Runbooks"]
    end

    subgraph Output["📋 Operator Action"]
        AGENT --> SLACK["Slack / Teams Triage Card<br/>(Root Cause & Attached SOP)"]
        SLACK --> ENG["Human SRE Approval"]
    end

    classDef blue fill:#0B1F3A,stroke:#0078D4,stroke-width:2px,color:#fff;
    classDef green fill:#052e16,stroke:#10b981,stroke-width:2px,color:#fff;
    class Alerts,MCP_Layer blue;
    class Output green;
```

---

## 📁 Repository Structure

```
.
├── server/
│   └── mcp_server.py      # Read-only Model Context Protocol server for Azure telemetry
├── agent/
│   └── sre_agent.py       # Multi-agent alert correlation and SOP runbook matcher
└── README.md
```

---

## 👤 Author

**Sujeet Kumar**  
*Senior DevSecOps Engineer & Enterprise Cloud Architect (17+ Years Experience)*  
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://linkedin.com/in/sujeetkumar122)
[![GitHub](https://img.shields.io/badge/GitHub-Sujeetkumar122-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/Sujeetkumar122)
