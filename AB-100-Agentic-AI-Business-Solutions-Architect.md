# AB 100 Agentic AI Business Solutions Architect

## Question 1

After deploying an enterprise AI agent, the operations team reports severe alert fatigue. The current monitoring setup routes all logs — routine access events, low-level debug traces, cost events, and critical security anomalies — into a single alerting channel. Important security signals are being missed. The team suggests simply disabling non-critical alerts to solve the problem.

### What should the architect redesign to properly address this?

**Choices:**

* Disable all non-critical alerts and retain only system downtime notifications
* Reduce log verbosity to errors only and suppress informational and debug-level events
* Move all logs to a third-party SIEM and let the security team manage all routing independently
* Build dedicated dashboards for quality, safety, and cost; configure alerts specifically for anomalies and budget thresholds; and route security alerts to SOC workflows for triage and escalation

**Response:** Build dedicated dashboards for quality, safety, and cost; configure alerts specifically for anomalies and budget thresholds; and route security alerts to SOC workflows for triage and escalation

---

## Question 2

### Customer Background

Contoso HealthServices Group (CHG) is a mid-sized US healthcare services organization operating across 12 states with approximately 8,500 employees spanning administrative, clinical support, and field operations. CHG manages patient intake, claims processing, HR onboarding, and field service coordination. The organization runs on a Microsoft 365 E5 license stack and uses Dynamics 365 Customer Service for patient case management.

### Technology Background

| Component        | Detail                                                                  |
| ---------------- | ----------------------------------------------------------------------- |
| Productivity     | Microsoft 365 E5 (Teams, SharePoint, Outlook)                           |
| CRM / Operations | Dynamics 365 Customer Service + Field Service                           |
| Data Platform    | Azure Data Lake (basic), Power Automate                                 |
| AI Maturity      | Early-stage — No AI CoE (Center of Excellence), no prompt library       |
| Data Quality     | HR and claims data siloed in 3 legacy systems with inconsistent schemas |
| Compliance       | Patient data subject to HIPAA                                           |

### Key Challenges

**Challenge 1 — Data Fragmentation & Compliance:** Patient and claims data is fragmented across 3 legacy systems with no unified index. HIPAA mandates strict data residency, access controls, and audit logging for any AI workload touching patient records.

**Challenge 2 — Governance Gap:** When a CoE is missing or inadequate, shadow AI and under-governance become critical risks — overcentralization leads to bottlenecks, while under-governance leads to ungoverned AI adoption. CHG has no AI CoE, no agent governance charter, and no responsible AI policy. Business teams are already deploying agents in Copilot Studio without architecture review.

**Challenge 3 — ROI Uncertainty & Adoption Risk:** The CTO wants 4 AI agent use cases live within 90 days. However, CHG has conducted no use case prioritization exercise, has no executive sponsor, and IT is concerned about low user adoption due to the absence of change management planning.

### Scenario

You are establishing an AI operating model at CHG to support governance, deployment, and ongoing operations.

### Items

* Define AI use cases and architecture approach
* Establish secure landing zones and environments
* Define governance and compliance policies
* Monitor deployed agents and manage operations

### Choices

* Platform engineering team
* Solution architect
* Security and compliance team
* Shared responsibility between architecture and platform teams

### Responses

| Item                                            | Response                                                      |
| ----------------------------------------------- | ------------------------------------------------------------- |
| Define AI use cases and architecture approach   | Solution architect                                            |
| Establish secure landing zones and environments | Security and compliance team                                  |
| Define governance and compliance policies       | Shared responsibility between architecture and platform teams |
| Monitor deployed agents and manage operations   | Platform engineering team                                     |

---

## Question 3

An enterprise AI agent in a legal firm operates in two distinct modes: it retrieves case documents on behalf of a logged-in attorney during active sessions, and it performs overnight background batch analysis on case sentiment data without user interaction. A developer proposes using a single elevated service account for both modes to simplify identity management.

### What is the correct authorization architecture the architect should enforce?

**Choices:**

* Use a single elevated service account with full permissions to cover both operating modes
* Use OAuth client credentials for all modes to standardize authentication across both scenarios
* Use a single managed identity scoped to the highest-permission level so both modes always succeed
* Propagate the attorney's permissions when the agent acts on their behalf; use a narrowly scoped service role when the agent acts as itself for background batch processing

**Response:** Propagate the attorney's permissions when the agent acts on their behalf; use a narrowly scoped service role when the agent acts as itself for background batch processing

---

## Question 4

**Statement:** "When building an executive ROI business case for an AI agent, a solution architect should present only the expected-case savings projection, since conservative and optimistic bands add unnecessary complexity for stakeholders."

**Choices:**

* True
* False

**Response:** False

---

## Question 5

During a monthly operations review, the architect notices a significant spike in guardrail intervention events for a deployed customer service agent over the past two weeks. User satisfaction scores have declined, and several conversations were abandoned after the guardrail blocked responses. The operations manager recommends temporarily disabling guardrails to restore service quality.

### What is the MOST appropriate diagnostic step the architect should take?

**Choices:**

* Disable guardrails temporarily to resume normal service and restore satisfaction scores quickly
* Expand the knowledge base by adding more documents to broaden agent response coverage
* Analyze telemetry for guardrail trigger patterns and review conversation transcripts to identify whether guardrails are misconfigured or legitimately blocking risk
* Roll back the agent to its previous release version immediately

**Response:** Analyze telemetry for guardrail trigger patterns and review conversation transcripts to identify whether guardrails are misconfigured or legitimately blocking risk

---

## Question 6

A logistics company is building a multi-agent AI system in Azure AI Foundry. The system handles three task types: simple package status lookups, moderately complex route optimization queries, and highly complex supply chain disruption analysis requiring deep reasoning.

### How should the architect configure the model router to balance cost and performance?

**Choices:**

* Route all three task types to a single GPT-4 LLM for consistency
* Route all tasks to an SLM to reduce token costs uniformly
* Use static routing rules: SLM for simple tasks, fine-tuned model for moderate tasks, LLM for complex tasks
* Use weighted routing to distribute all tasks equally across all available models

**Response:** Use static routing rules: SLM for simple tasks, fine-tuned model for moderate tasks, LLM for complex tasks

---

## Question 7

An operations manager at a regional bank insists that since Copilot for Service generates high-quality case resolution summaries, the human review step in the Power Automate flow sending summaries to customers is unnecessary overhead. Removing it would reduce case handling time by 35% and improve the team's SLA performance metrics.

**TRUE or FALSE:** "In a governed enterprise Copilot for Service deployment, human review before sending externally generated Copilot content to customers is an optional step that architects can remove to improve operational speed and SLA performance."

**Choices:**

* True
* False

**Response:** False

---

## Question 8

A solution architect is preparing to release a new AI Copilot agent for case summarization in Dynamics 365 Customer Service. The agent has passed DEV and TEST validation. The product owner is pushing for a direct deployment to PROD to meet a customer launch deadline. The UAT/PRE-PROD environment has not been used in this release cycle.

### What should the architect do FIRST?

**Choices:**

* Deploy to PROD immediately and use post-deployment telemetry to catch issues
* Re-run regression tests in the DEV environment using production data to save time
* Stage the agent in PRE-PROD for final business acceptance, performance, safety, and compliance validation before deploying to PROD
* Export the managed solution package and push it to PROD via Azure DevOps with monitoring alerts enabled

**Response:** Stage the agent in PRE-PROD for final business acceptance, performance, safety, and compliance validation before deploying to PROD

---

## Question 9

An insurance company's Power Automate-based claims processing flow is experiencing intermittent failures when connecting to a downstream policy management system. The failures occur during peak load and cause incomplete claims records. The system has no retry logic or fallback path configured.

### Which Power Platform Well-Architected pillar is primarily being violated, and what should the architect recommend?

**Choices:**

* Performance Efficiency — offload tasks to Azure Functions
* Operational Excellence — implement ALM with Azure DevOps
* Reliability — add retry policies and configure redundant connectors with failover paths
* Security — apply DLP policies to prevent connector exposure

**Response:** Reliability — add retry policies and configure redundant connectors with failover paths

---

## Question 10

An enterprise architect is designing a Teams-based AI agent for a cross-functional project team. The goal is to allow team members to retrieve project documents, summarize recent channel discussions, and automate task creation from messages. The architect must decide the grounding strategy before configuring the agent.

### Which grounding approach should the architect establish FIRST?

**Choices:**

* Use Microsoft Graph as the primary retrieval engine to maximize cross-tenant content coverage
* Use Azure Blob Storage to host project documents and expose them via a custom connector
* Use SharePoint sites as the primary knowledge source, ensuring content is well-structured and tagged
* Enable external web search to supplement any missing project information gaps

**Response:** Use SharePoint sites as the primary knowledge source, ensuring content is well-structured and tagged

---

## Question 11

A bank deploys an autonomous Copilot agent that automatically approves or denies personal loan applications based on AI-generated credit assessments. After launch, the compliance team discovers that the agent produces denial decisions without any explanation to applicants and with no human review step.

### Which two Responsible AI principles are MOST directly violated?

**Choices:**

* Fairness and Inclusiveness
* Transparency and Accountability
* Reliability and Privacy
* Security and Inclusiveness

**Response:** Transparency and Accountability

---

## Question 12

A retail organization wants to give warehouse staff access to demand planning insights through Copilot. Staff rarely leave the operational workspace view. Two options are under discussion: a sidecar Copilot experience or an embedded AI approach. The architect must select the best fit.

### Which AI experience model best fits this scenario, and why?

**Choices:**

* Sidecar Copilot — because it supports natural language chat and is easier to configure
* External orchestration — because it allows cross-application automation
* Embedded AI — because it surfaces insights directly within the workspace, reducing navigation overhead
* Sidecar Copilot — because it supports workflow summaries across modules using standardized entity metadata

**Response:** Embedded AI — because it surfaces insights directly within the workspace, reducing navigation overhead

---

## Question 13

A retail company is deploying an AI agent for customer collections summaries in Dynamics 365 Finance. The CFO also wants the agent to answer general regulatory finance questions using LLM capabilities to reduce analyst workload. The architect has not yet completed a risk assessment for LLM enablement in this regulated environment.

### How should the architect advise the CFO?

**Choices:**

* Enable general knowledge immediately — the productivity gains outweigh the risk
* Enable general knowledge in production and configure a compliance review process post-deployment
* Delay general knowledge enablement until risks are formally assessed and mitigated; keep the agent restricted to validated internal knowledge in the interim
* Build a custom Azure OpenAI model to handle regulatory questions separately and bypass the governance review

**Response:** Delay general knowledge enablement until risks are formally assessed and mitigated; keep the agent restricted to validated internal knowledge in the interim

---

## Question 14

A manufacturing company wants to build a Copilot Studio autonomous agent to manage supplier follow-up workflows. The business goal is to send automated reminders to overdue suppliers, update ERP records, and escalate unresolved cases to procurement managers.

### According to agent design best practices, what should the architect do FIRST?

**Choices:**

* Connect all ERP tables as knowledge sources to maximize agent context
* Configure event triggers for all inbound supplier communications
* Start with one high-value, well-scoped workflow before expanding agent scope
* Deploy the agent to Microsoft Teams for user acceptance testing immediately

**Response:** Start with one high-value, well-scoped workflow before expanding agent scope

---

## Question 15

A financial services firm is deploying Copilot within Dynamics 365 Finance to support regulatory audit workflows. The business sponsor wants to enable general LLM knowledge so that auditors can ask broad natural-language questions beyond internal documents. The CISO has mandated that all AI-generated responses must derive exclusively from validated, internally controlled content to meet regulatory compliance standards.

### What should the architect do?

**Choices:**

* Enable general knowledge to improve natural language flexibility for auditors
* Restrict general knowledge and configure Copilot to use only validated internal knowledge sources
* Deploy Copilot in pilot mode with general knowledge enabled and monitor for compliance violations
* Escalate to the business sponsor to obtain executive approval before enabling LLM-based knowledge

**Response:** Restrict general knowledge and configure Copilot to use only validated internal knowledge sources

---

## Question 16

An organization is designing a governance framework for a Copilot agent that handles sensitive HR compensation data. The HR Director proposes using a shared cloud identity across DEV, TEST, and PROD environments to reduce identity management overhead and cut operational costs. The architect must evaluate this proposal.

### What is the architect's correct guidance?

**Choices:**

* Accept the shared identity model and apply environment-specific DLP policies to compensate for the risk
* Allow the shared identity between DEV and TEST only, with a separate identity for PROD
* Assign a unique cloud identity per agent per environment — DEV, PRE-PROD, and PROD — recording ownership, version, and lifecycle metadata for each
* Use a shared identity but restrict its permissions to read-only in non-production environments

**Response:** Assign a unique cloud identity per agent per environment — DEV, PRE-PROD, and PROD — recording ownership, version, and lifecycle metadata for each

---

## Question 17

A professional services firm wants to deploy Microsoft 365 Copilot for Sales. During pre-deployment validation, the architect discovers that several CRM opportunity fields are incomplete and that sales documents stored in SharePoint do not have sensitivity labels applied. The business owner wants to begin rollout within the week.

### What must the architect complete FIRST before enabling Copilot for Sales?

**Choices:**

* Enable Copilot for Sales licenses and proceed with a limited pilot
* Configure Power Automate flows to automate proposal drafting workflows
* Ensure CRM fields are complete, standardized, and SharePoint documents have proper sensitivity labels applied
* Map seller roles to Dynamics 365 opportunity records and test email summarization

**Response:** Ensure CRM fields are complete, standardized, and SharePoint documents have proper sensitivity labels applied

---

## Question 18

### Customer Background

Contoso HealthServices Group (CHG) is a mid-sized US healthcare services organization operating across 12 states with approximately 8,500 employees spanning administrative, clinical support, and field operations. CHG manages patient intake, claims processing, HR onboarding, and field service coordination. The organization runs on a Microsoft 365 E5 license stack and uses Dynamics 365 Customer Service for patient case management.

### Technology Background

| Component        | Detail                                                                  |
| ---------------- | ----------------------------------------------------------------------- |
| Productivity     | Microsoft 365 E5 (Teams, SharePoint, Outlook)                           |
| CRM / Operations | Dynamics 365 Customer Service + Field Service                           |
| Data Platform    | Azure Data Lake (basic), Power Automate                                 |
| AI Maturity      | Early-stage — No AI CoE (Center of Excellence), no prompt library       |
| Data Quality     | HR and claims data siloed in 3 legacy systems with inconsistent schemas |
| Compliance       | Patient data subject to HIPAA                                           |

### Key Challenges

**Challenge 1 — Data Fragmentation & Compliance:** Patient and claims data is fragmented across 3 legacy systems with no unified index. HIPAA mandates strict data residency, access controls, and audit logging for any AI workload touching patient records.

**Challenge 2 — Governance Gap:** When a CoE is missing or inadequate, shadow AI and under-governance become critical risks — overcentralization leads to bottlenecks, while under-governance leads to ungoverned AI adoption. CHG has no AI CoE, no agent governance charter, and no responsible AI policy. Business teams are already deploying agents in Copilot Studio without architecture review.

**Challenge 3 — ROI Uncertainty & Adoption Risk:** The CTO wants 4 AI agent use cases live within 90 days. However, CHG has conducted no use case prioritization exercise, has no executive sponsor, and IT is concerned about low user adoption due to the absence of change management planning.

### Scenario

You are aligning solution design decisions across CHG’s AI use cases.

### Items

* HR agent requires consistent responses across departments
* Claims agent needs HIPAA-compliant processing and auditing
* Routing agent must process multiple dependent steps
* Patient intake crosses regulated system boundaries

### Choices

* Sequential orchestration for controlled execution
* Centralized prompt governance and templates
* Custom platform supporting compliance pipelines
* Multi-agent architecture with boundary separation

### Responses

| Item                                                       | Response                                          |
| ---------------------------------------------------------- | ------------------------------------------------- |
| HR agent requires consistent responses across departments  | Centralized prompt governance and templates       |
| Claims agent needs HIPAA-compliant processing and auditing | Custom platform supporting compliance pipelines   |
| Routing agent must process multiple dependent steps        | Sequential orchestration for controlled execution |
| Patient intake crosses regulated system boundaries         | Multi-agent architecture with boundary separation |

---

## Question 19

A healthcare organization is beginning its AI adoption journey using the Cloud Adoption Framework. The leadership team has agreed on high-level objectives such as improving patient satisfaction and reducing administrative workload, but has not yet identified specific AI use cases or assessed data quality.

### What is the NEXT step the architect should take?

**Choices:**

* Immediately begin configuring Copilot Studio agents for appointment scheduling
* Establish program governance and Responsible AI standards before proceeding
* Identify measurable AI scenarios with high feasibility and high business impact
* Assess AI feasibility by evaluating data quality, security, and model appropriateness

**Response:** Identify measurable AI scenarios with high feasibility and high business impact

---

## Question 20

A solution architect is designing a SharePoint agent for an enterprise where multiple departments have different access levels. A business leader argues that since the agent is an AI system — not a human user — it should be granted elevated permissions to access all site content so it can serve all employees equally, regardless of individual access rights.

**TRUE or FALSE:** "Microsoft 365 agents can be configured with elevated admin-level access to override SharePoint security boundaries and retrieve content on behalf of all users, regardless of their individual permissions."

**Choices:**

* True
* False

**Response:** False

---

## Question 21

**Statement:** "A custom connector built in Power Automate can be created in any Power Platform environment, including the default environment, as long as the correct OpenAPI definition and OAuth 2.0 authentication are configured."

**Choices:**

* True
* False

**Response:** False

---

## Question 22

A financial services firm is deploying Copilot within Dynamics 365 Finance to support regulatory audit workflows. The business sponsor wants to enable general LLM knowledge so that auditors can ask broad natural-language questions beyond internal documents. The CISO has mandated that all AI-generated responses must derive exclusively from validated, internally controlled content to meet regulatory compliance standards.

### What should the architect do?

**Choices:**

* Enable general knowledge to improve natural language flexibility for auditors
* Restrict general knowledge and configure Copilot to use only validated internal knowledge sources
* Deploy Copilot in pilot mode with general knowledge enabled and monitor for compliance violations
* Escalate to the business sponsor to obtain executive approval before enabling LLM-based knowledge

**Response:** Restrict general knowledge and configure Copilot to use only validated internal knowledge sources

---

## Question 23

A global enterprise is deploying a SharePoint-based Copilot agent for cross-departmental policy guidance. Each department maintains its own SharePoint site with restricted access. A business leader requests that the agent be granted global read permissions via a service account so it can serve all employees regardless of their individual access levels.

### What architectural boundary must the architect enforce?

**Choices:**

* Configure a service account with global read permissions to enable uniform cross-department access
* Enable agent-level admin override so the agent can bypass SharePoint permission boundaries
* Enforce that agents inherit the requesting user's permissions and cannot access content the user cannot access
* Use a custom API connector to route all content queries through a centralized knowledge repository with elevated access

**Response:** Enforce that agents inherit the requesting user's permissions and cannot access content the user cannot access

---

## Question 24

### Scenario

A government agency is deploying an AI agent that assists officers in reviewing case files and producing preliminary recommendations. The agency's governance team mandates that no AI system should make final decisions autonomously on any case. The solution architect is asked to design the enforcement mechanism.

### Question

Which control best enforces the governance mandate?

**Choices:**

* Add a disclaimer in the agent's welcome message stating it does not make final decisions.
* Define explicit behavior envelopes in the agent configuration: "Agent may summarize and recommend; Agent may not decide or execute case outcomes," combined with mandatory human-in-the-loop checkpoints for high-impact actions.
* Configure the agent with lower model temperature to reduce confidence in outputs.
* Use Azure AI Content Safety to block any output that contains decision language.

**Response:** Define explicit behavior envelopes in the agent configuration: "Agent may summarize and recommend; Agent may not decide or execute case outcomes," combined with mandatory human-in-the-loop checkpoints for high-impact actions.

---

## Question 25

An architect has successfully deployed an AI agent that has reached a 96% success rate after three months in production — matching the Finance Assistant benchmark. The project manager proposes reducing the monitoring cadence to ad-hoc reviews only when user complaints are escalated, arguing that the high success rate proves the agent is stable and self-sustaining.

**TRUE or FALSE:** "Once an AI agent reaches a high success rate, architects can safely reduce monitoring to ad-hoc reviews and focus improvement cycles only when issues are escalated by users."

**Choices:**

* True
* False

**Response:** False

---

## Question 26

A DevOps lead recommends consolidating the DEV and TEST environments into a single shared environment to reduce infrastructure costs for an AI agent development project. The lead argues that since both are non-production environments with no customer data, the risk of merging them is negligible.

**TRUE or FALSE:** "Consolidating DEV and TEST into a single shared AI development environment is an acceptable cost-optimization strategy that does not compromise ALM governance integrity."

**Choices:**

* True
* False

**Response:** False

---

## Question 27

A manufacturing company has deployed three Copilot agents in production. During a quarterly review, the Analytics Coach shows an 88% success rate, 3.2-second average response time, and 21 logged issues—the lowest performer in the portfolio. The product owner is requesting an immediate fix. The architect must determine what to do first.

### What should the architect do FIRST?

**Choices:**

* Disable the Analytics Coach temporarily to prevent further issue accumulation
* Review conversation transcripts and telemetry to identify root cause categories driving the failures
* Immediately update the knowledge files and republish the agent
* Escalate to the vendor and request model replacement

**Response:** Review conversation transcripts and telemetry to identify root cause categories driving the failures

---

## Question 28

### Scenario

An enterprise is deploying a generative AI agent using Microsoft Foundry. The agent must call three external APIs for product pricing, inventory, and shipping. The security team mandates that no sensitive customer data should be stored persistently, and all API calls must be restricted to approved domains.

### Which combination of constraints should the solution architect enforce?

**Choices:**

* Define ephemeral memory policy, implement least-privilege permissions per tool, and restrict external tool calls to allow-listed domains.
* Enable persistent message logging for audit purposes, grant broad API access to improve agent performance, and apply Azure Content Safety.
* Use public networking for all API calls to reduce latency, and set connector scoping to maximum to ensure comprehensive data retrieval.
* Store all interactions in Dataverse for auditability and open API gateway access to all third-party domains.

**Response:** Define ephemeral memory policy, implement least-privilege permissions per tool, and restrict external tool calls to allow-listed domains.

---

## Question 29

A product manager argues that prompt injection vulnerabilities are only relevant for public-facing consumer chatbots, not for internal enterprise AI agents — because internal users are trusted, authenticated employees operating under corporate policy. The manager wants to skip input/output filtering controls to reduce deployment complexity for an internal agent.

**TRUE or FALSE:** "Prompt injection vulnerabilities only affect public-facing AI agents and do not require mitigation controls in internal enterprise AI agents used by authenticated employees."

**Choices:**

* True
* False

**Response:** False

---

## Question 30

### Customer Background

Contoso HealthServices Group (CHG) is a mid-sized US healthcare services organization operating across 12 states with approximately 8,500 employees spanning administrative, clinical support, and field operations. CHG manages patient intake, claims processing, HR onboarding, and field service coordination. The organization runs on a Microsoft 365 E5 license stack and uses Dynamics 365 Customer Service for patient case management.

### Technology Background

| Component        | Detail                                                                  |
| ---------------- | ----------------------------------------------------------------------- |
| Productivity     | Microsoft 365 E5 (Teams, SharePoint, Outlook)                           |
| CRM / Operations | Dynamics 365 Customer Service + Field Service                           |
| Data Platform    | Azure Data Lake (basic), Power Automate                                 |
| AI Maturity      | Early-stage — No AI CoE (Center of Excellence), no prompt library       |
| Data Quality     | HR and claims data siloed in 3 legacy systems with inconsistent schemas |
| Compliance       | Patient data subject to HIPAA                                           |

### Key Challenges

**Challenge 1 — Data Fragmentation & Compliance:** Patient and claims data is fragmented across 3 legacy systems with no unified index. HIPAA mandates strict data residency, access controls, and audit logging for any AI workload touching patient records.

**Challenge 2 — Governance Gap:** When a CoE is missing or inadequate, shadow AI and under-governance become critical risks — overcentralization leads to bottlenecks, while under-governance leads to ungoverned AI adoption. CHG has no AI CoE, no agent governance charter, and no responsible AI policy. Business teams are already deploying agents in Copilot Studio without architecture review.

**Challenge 3 — ROI Uncertainty & Adoption Risk:** The CTO wants 4 AI agent use cases live within 90 days. However, CHG has conducted no use case prioritization exercise, has no executive sponsor, and IT is concerned about low user adoption due to the absence of change management planning.

### Scenario

You are designing the Claims Summarization Agent. The solution requires:

* Transformation of inconsistent data from Azure Data Lake
* HIPAA-compliant audit logging at the data level
* Integration with custom data pipelines

The team suggests using Copilot Studio for faster delivery.

### Question

Which is the best platform choice to accomplish all the requirements?

**Choices:**

* Copilot Studio with Azure AI Search for faster deployment
* Microsoft Foundry to support custom pipelines and compliance controls
* Microsoft 365 Copilot because it provides built-in retrieval
* Containerized model deployment to isolate workloads

**Response:** Microsoft Foundry to support custom pipelines and compliance controls

---

## Question 31

A solution architect has uploaded new compliance policy documents as a knowledge source for a Copilot agent in Dynamics 365. The upload completed but the knowledge source status still shows **"Processing."** The business owner is pressing for immediate publication to meet a regulatory go-live deadline. The architect must decide how to respond.

### What should the architect do?

**Choices:**

* Publish the agent immediately to meet the deadline and patch any knowledge issues post-deployment
* Wait for the knowledge source to show "Ready," perform scenario-based testing, and then publish
* Publish the agent with a disclaimer to users that knowledge may be incomplete
* Replace the new documents with an older version that already has a Ready status

**Response:** Wait for the knowledge source to show "Ready," perform scenario-based testing, and then publish

---

## Question 32

### Scenario

A logistics company asks its solution architect to build a multi-agent system with seven specialized agents — one each for dispatch, routing, inventory, billing, compliance, customer service, and analytics — all within the first project sprint. The development team has moderate AI skills. The solution architect reviews the requirements and finds that routing and dispatch can cover 80% of the business value independently.

### Question

What is the most architecturally sound decision?

**Choices:**

* Accept the seven-agent design, as multi-agent systems provide better modularity and future-proofing.
* Delay the full multi-agent design and first validate a single-agent or two-agent solution covering routing and dispatch, scaling only after validating complexity drivers.
* Use Copilot Studio for all seven agents simultaneously to benefit from rapid, low-code deployment.
* Immediately deploy using Foundry with a sequential orchestration pipeline across all seven agents.

**Response:** Delay the full multi-agent design and first validate a single-agent or two-agent solution covering routing and dispatch, scaling only after validating complexity drivers.

---

## Question 33

A manufacturing company has deployed three Copilot agents in production. During a quarterly review, the Analytics Coach shows an 88% success rate, 3.2-second average response time, and 21 logged issues—the lowest performer in the portfolio. The product owner is requesting an immediate fix. The architect must determine what to do first.

### What should the architect do FIRST?

**Choices:**

* Disable the Analytics Coach temporarily to prevent further issue accumulation
* Review conversation transcripts and telemetry to identify root cause categories driving the failures
* Immediately update the knowledge files and republish the agent
* Escalate to the vendor and request model replacement

**Response:** Review conversation transcripts and telemetry to identify root cause categories driving the failures

---

## Question 34

A retail organization wants to build an autonomous agent in Copilot Studio to automatically process customer refund requests. The agent should access order records, calculate refund eligibility, and execute refund transactions in the ERP system — all without human approval.

### What is the MOST critical architectural risk the solution architect must address before deploying this agent?

**Choices:**

* The agent may not support enough knowledge sources to ground responses
* The agent lacks sufficient trigger configuration for scheduled events
* The agent has unrestricted action permissions that violate the principle of least privilege
* The agent cannot be published to Microsoft Teams without admin approval

**Response:** The agent has unrestricted action permissions that violate the principle of least privilege

---

## Question 35

### Customer Background

Contoso HealthServices Group (CHG) is a mid-sized US healthcare services organization operating across 12 states with approximately 8,500 employees spanning administrative, clinical support, and field operations. CHG manages patient intake, claims processing, HR onboarding, and field service coordination. The organization runs on a Microsoft 365 E5 license stack and uses Dynamics 365 Customer Service for patient case management.

### Technology Background

| Component        | Detail                                                                  |
| ---------------- | ----------------------------------------------------------------------- |
| Productivity     | Microsoft 365 E5 (Teams, SharePoint, Outlook)                           |
| CRM / Operations | Dynamics 365 Customer Service + Field Service                           |
| Data Platform    | Azure Data Lake (basic), Power Automate                                 |
| AI Maturity      | Early-stage — No AI CoE (Center of Excellence), no prompt library       |
| Data Quality     | HR and claims data siloed in 3 legacy systems with inconsistent schemas |
| Compliance       | Patient data subject to HIPAA                                           |

### Key Challenges

**Challenge 1 — Data Fragmentation & Compliance:** Patient and claims data is fragmented across 3 legacy systems with no unified index. HIPAA mandates strict data residency, access controls, and audit logging for any AI workload touching patient records.

**Challenge 2 — Governance Gap:** When a CoE is missing or inadequate, shadow AI and under-governance become critical risks — overcentralization leads to bottlenecks, while under-governance leads to ungoverned AI adoption. CHG has no AI CoE, no agent governance charter, and no responsible AI policy. Business teams are already deploying agents in Copilot Studio without architecture review.

**Challenge 3 — ROI Uncertainty & Adoption Risk:** The CTO wants 4 AI agent use cases live within 90 days. However, CHG has conducted no use case prioritization exercise, has no executive sponsor, and IT is concerned about low user adoption due to the absence of change management planning.

You are the Solution Architect for CHG. The CTO requests deployment of four AI agents within 90 days. However, CHG currently lacks an AI Center of Excellence, has no governance framework, and handles HIPAA-regulated patient data.

You must recommend the first agent to deploy to demonstrate measurable business value while minimizing implementation and compliance risk.

### Question

Which agent should you prioritize?

**Choices:**

* Patient Intake Orchestration Agent, because it directly impacts patient operations
* Field Service Routing Agent, because it introduces multi-agent orchestration capabilities
* HR Policy Q&A Agent, because it uses existing Microsoft 365 data with minimal compliance risk
* Claims Summarization Agent, because it processes the highest volume of data

**Response:** HR Policy Q&A Agent, because it uses existing Microsoft 365 data with minimal compliance risk

---

## Question 36

### Scenario

A financial services firm needs to deploy an AI agent that can execute multi-step loan approval workflows, integrate with three internal APIs, and enforce strict separation of duties between teams. The compliance team requires full auditability of every agent action. The IT team has strong developer expertise.

### Question

Which platform architecture decision best satisfies all stated constraints?

**Choices:**

* Deploy using Copilot Studio with prebuilt connectors, relying on its built-in safety filters for compliance.
* Use Microsoft 365 Copilot (SaaS) as a productivity-first approach, minimizing customization effort.
* Build using Microsoft Foundry with role-scoped agents, explicit action boundaries, evaluation pipelines, and audit trails.
* Use GPUs and containers to host a custom model for maximum compliance isolation.

**Response:** Build using Microsoft Foundry with role-scoped agents, explicit action boundaries, evaluation pipelines, and audit trails.

---

## Question 37

A retail enterprise is deploying a production Copilot agent that connects to multiple Azure-hosted backend services. The development team has embedded service principal credentials directly into the agent's configuration files to simplify deployment. The security architect raises a concern about credential rotation cycles and secret exposure risk. The team argues that encrypting the config files is sufficient.

**Choices:**

* Rotate the embedded credentials every 30 days using an automated Key Vault script
* Encrypt the configuration files using AES-256 and restrict file access to production admins only
* Replace embedded secrets with managed identities for agent-to-Azure authentication to remove secrets entirely and simplify rotation
* Store credentials in Azure Key Vault and reference them dynamically from the agent configuration

**Response:** Replace embedded secrets with managed identities for agent-to-Azure authentication to remove secrets entirely and simplify rotation

---

## Question 38

### Scenario

An organization's AI CoE was established 18 months ago with a centralized model, approving every AI project and owning all delivery. Business units are now complaining about delays. The CoE has successfully standardized governance frameworks and published reusable AI templates that product teams have adopted.

### Question

What is the most appropriate NEXT step for the AI CoE's operating model evolution?

**Choices:**

* Maintain the centralized model — it ensures consistent governance and prevents ungoverned AI adoption.
* Dissolve the CoE entirely, as product teams are now self-sufficient.
* Transition to a hybrid or advisory CoE model, where product teams take ownership of delivery while the CoE maintains standards and acts as a consultant.
* Expand the CoE team to handle the increased demand from business units.

**Response:** Transition to a hybrid or advisory CoE model, where product teams take ownership of delivery while the CoE maintains standards and acts as a consultant.

---

## Question 39

### Scenario

An insurance company is designing a multi-agent claims processing solution. The workflow requires: (1) extracting claim details, (2) translating foreign-language documents, (3) running a QA validation on completeness, and (4) routing to the appropriate team. Each step must complete before the next begins, and any failure must halt the pipeline.

### Question

Which orchestration pattern should the architect select?

**Choices:**

* Concurrent orchestration, so all agents process in parallel to reduce latency.
* Group chat orchestration, so agents negotiate the task sequence dynamically.
* Sequential orchestration, where each agent processes in a deterministic stage-by-stage pipeline.
* Handoff orchestration, so each agent decides independently who to route to next.

**Response:** Sequential orchestration, where each agent processes in a deterministic stage-by-stage pipeline.

---

## Question 40

### Scenario

A retail enterprise wants to deploy an AI agent to handle product recommendation queries across 50,000 daily customers. The CTO demands a 3-week go-live. The data engineering team warns that product catalog data is outdated, inconsistently labeled, and spread across three legacy systems. The business team insists the agent should still launch on time.

### Question

As the solution architect, what is the FIRST action you should take?

**Choices:**

* Begin building the agent in Copilot Studio immediately, as it supports rapid deployment and can be refined post-launch.
* Defer the agent launch and mandate a data quality remediation effort, as agent reliability depends on grounding data quality and freshness.
* Deploy the agent using Azure AI Foundry with private networking to handle the complexity of multiple data sources.
* Build a custom SLM trained on historical product data to compensate for data quality gaps.

**Response:** Defer the agent launch and mandate a data quality remediation effort, as agent reliability depends on grounding data quality and freshness.

---

## Question 41

### Scenario

A large enterprise has 12 AI use case proposals submitted to the AI Center of Excellence. The CoE has limited capacity, and the executive sponsor wants to approve all 12 for simultaneous execution. The AI CoE leader raises concerns about governance readiness and agent quality.

### Question

According to Microsoft's AI CoE framework, what should the AI CoE do FIRST?

**Choices:**

* Approve all 12 and assign a governance lead to each project to ensure oversight.
* Evaluate each use case for business value, technical feasibility, risk level, and organizational readiness before prioritizing a subset for execution.
* Begin delivering all 12 using Copilot Studio to minimize risk through the platform's built-in safeguards.
* Escalate to the legal team to validate compliance for all 12 simultaneously.

**Response:** Evaluate each use case for business value, technical feasibility, risk level, and organizational readiness before prioritizing a subset for execution.

---

## Question 42

A professional services firm wants to deploy Microsoft 365 Copilot for Sales. During pre-deployment validation, the architect discovers that several CRM opportunity fields are incomplete and that sales documents stored in SharePoint do not have sensitivity labels applied. The business owner wants to begin rollout within the week.

### What must the architect complete FIRST before enabling Copilot for Sales?

**Choices:**

* Enable Copilot for Sales licenses and proceed with a limited pilot
* Configure Power Automate flows to automate proposal drafting workflows
* Ensure CRM fields are complete, standardized, and SharePoint documents have proper sensitivity labels applied
* Map seller roles to Dynamics 365 opportunity records and test email summarization

**Response:** Ensure CRM fields are complete, standardized, and SharePoint documents have proper sensitivity labels applied

---

## Question 43

A healthcare company's Copilot for Service agent generates case resolution summaries that are automatically sent to patients via Power Automate flows — with no human review step. The compliance team has flagged this as a violation of their data handling policy. The business team argues that removing the review step improves resolution speed by 40%.

### What action should the architect take?

**Choices:**

* Restrict the Copilot model to reduce verbosity of summaries so risk exposure is minimized
* Enable DLP policies to intercept outbound messages after they are generated
* Require human review before any externally generated Copilot content is sent to patients, and update the automation governance guardrails accordingly
* Disable all automated flows until the vendor provides compliance certification for the Copilot model

**Response:** Require human review before any externally generated Copilot content is sent to patients, and update the automation governance guardrails accordingly

---

## Question 44

A government agency is deploying a Copilot Studio agent for benefits enrollment. All user questions follow predictable, structured patterns defined by a legal mandate. The agency requires deterministic responses with no generative behavior to meet audit requirements.

### Which language understanding approach should the architect configure?

**Choices:**

* Generative AI orchestration — to handle open-ended user queries dynamically
* Azure CLU — to support multilingual intent recognition across varied phrasing
* Standard NLU — for strict intent matching with deterministic, non-generative responses
* NLU Boost with generative answers — to answer questions from internal SharePoint knowledge

**Response:** Standard NLU — for strict intent matching with deterministic, non-generative responses

---

## Question 45

A financial services firm is scheduled for a production go-live of a new AI loan advisory agent. Reviewing the AI Release Readiness Checklist, the architect discovers that prompts have not been regression tested and monitoring dashboards have not been configured. The CTO is demanding deployment by end of day to support a high-visibility client demo.

### What should the architect do?

**Choices:**

* Deploy to PROD since the demo is read-only and production data will not be modified
* Deploy to PROD with the demo user operating under restricted permissions and complete the checklist next week
* Delay the production release until prompts are regression tested and monitoring dashboards are operational, regardless of the demo deadline
* Deploy to PROD and manually shadow-monitor the agent session live during the demo

**Response:** Delay the production release until prompts are regression tested and monitoring dashboards are operational, regardless of the demo deadline

---

## Question 46

A financial services AI agent processing customer loan applications is flagged by the SOC for exhibiting unusual inference patterns — returning unexpected data fragments and potentially exposing customer PII in response outputs. The incident is unconfirmed but escalating rapidly. A business manager suggests waiting 24 hours to gather more evidence before taking technical action.

### What should the architect do FIRST?

**Choices:**

* Notify the Data Protection Officer and wait for their formal guidance before taking any technical action
* Increase monitoring verbosity on the agent and wait 24 hours to determine whether the pattern stabilizes
* Re-run all recent prompts against the previous model version to compare output differences
* Disable the compromised model endpoint, preserve inference logs and model artifacts for forensic analysis, and initiate rollback procedures to restore the prior model version

**Response:** Disable the compromised model endpoint, preserve inference logs and model artifacts for forensic analysis, and initiate rollback procedures to restore the prior model version

---

## Question 47

### Scenario

A healthcare organization in the European Union is planning to deploy a patient-facing AI assistant that will help users book appointments and retrieve general health FAQs. The legal team flags GDPR obligations and the EU AI Act as potentially applicable. The project sponsor wants to skip the regulatory review to accelerate the timeline.

### Question

What should the solution architect do FIRST?

**Choices:**

* Proceed with deployment since the agent only retrieves public FAQs and poses minimal risk.
* Conduct a regulatory evaluation across applicable jurisdictions before finalizing the architecture.
* Implement Azure AI Content Safety and assume it covers all regulatory requirements.
* Deploy to a non-EU region to avoid EU AI Act compliance obligations.

**Response:** Conduct a regulatory evaluation across applicable jurisdictions before finalizing the architecture.

---

## Question 48

### Scenario

A pharmaceutical company needs an AI model to classify drug interaction reports with high accuracy. The data is highly domain-specific, regulatory restrictions prevent data from leaving a specific sovereign region, and model response latency must be under 200ms. The IT budget is moderate.

### Question

Which model architecture decision is most appropriate?

**Choices:**

* Use a general-purpose LLM via Azure OpenAI, as it provides the best reasoning capability across complex documents.
* Deploy a customized Small Language Model (SLM) trained on domain-specific data, hosted within the sovereign region.
* Use Microsoft 365 Copilot with a custom knowledge base of drug interaction documents.
* Build a multi-agent system where one agent retrieves documents and another classifies them using a general LLM.

**Response:** Deploy a customized Small Language Model (SLM) trained on domain-specific data, hosted within the sovereign region.

---

## Question 49

### Customer Background

Contoso HealthServices Group (CHG) is a mid-sized US healthcare services organization operating across 12 states with approximately 8,500 employees spanning administrative, clinical support, and field operations. CHG manages patient intake, claims processing, HR onboarding, and field service coordination. The organization runs on a Microsoft 365 E5 license stack and uses Dynamics 365 Customer Service for patient case management.

### Technology Background

| Component        | Detail                                                                  |
| ---------------- | ----------------------------------------------------------------------- |
| Productivity     | Microsoft 365 E5 (Teams, SharePoint, Outlook)                           |
| CRM / Operations | Dynamics 365 Customer Service + Field Service                           |
| Data Platform    | Azure Data Lake (basic), Power Automate                                 |
| AI Maturity      | Early-stage — No AI CoE (Center of Excellence), no prompt library       |
| Data Quality     | HR and claims data siloed in 3 legacy systems with inconsistent schemas |
| Compliance       | Patient data subject to HIPAA                                           |

### Key Challenges

**Challenge 1 — Data Fragmentation & Compliance:** Patient and claims data is fragmented across 3 legacy systems with no unified index. HIPAA mandates strict data residency, access controls, and audit logging for any AI workload touching patient records.

**Challenge 2 — Governance Gap:** When a CoE is missing or inadequate, shadow AI and under-governance become critical risks — overcentralization leads to bottlenecks, while under-governance leads to ungoverned AI adoption. CHG has no AI CoE, no agent governance charter, and no responsible AI policy. Business teams are already deploying agents in Copilot Studio without architecture review.

**Challenge 3 — ROI Uncertainty & Adoption Risk:** The CTO wants 4 AI agent use cases live within 90 days. However, CHG has conducted no use case prioritization exercise, has no executive sponsor, and IT is concerned about low user adoption due to the absence of change management planning.

You are reviewing the design of a Patient Intake Agent. The proposed design:

* Automatically commits patient records
* Uses generative responses
* Has no human approval checkpoints
* Does not include content safety controls

**Statement:** This design is acceptable because built-in Copilot safeguards are sufficient for regulated healthcare workloads.

**Choices:**

* True
* False

**Response:** False

---

## Question 50

A financial services organization wants to automate 40% of its manual loan-processing data entry using a Copilot Studio agent. The project sponsor estimates a 60% productivity gain in Year 1. However, the architecture team has not yet baselined current processing time, and no usage telemetry is available.

### As the solution architect, what should you do FIRST before building a ROI business case for executive approval?

**Choices:**

* Submit the ROI projections using industry benchmark data since no internal data exists
* Proceed to design the agent and collect ROI data during the pilot phase
* Establish a baseline by measuring current task time, volume, and error rates before modeling ROI
* Request Copilot Studio licensing immediately to access ROI analytics dashboards

**Response:** Establish a baseline by measuring current task time, volume, and error rates before modeling ROI

---

## Question 51

### Customer Background

Contoso HealthServices Group (CHG) is a mid-sized US healthcare services organization operating across 12 states with approximately 8,500 employees spanning administrative, clinical support, and field operations. CHG manages patient intake, claims processing, HR onboarding, and field service coordination. The organization runs on a Microsoft 365 E5 license stack and uses Dynamics 365 Customer Service for patient case management.

### Technology Background

| Component        | Detail                                                                  |
| ---------------- | ----------------------------------------------------------------------- |
| Productivity     | Microsoft 365 E5 (Teams, SharePoint, Outlook)                           |
| CRM / Operations | Dynamics 365 Customer Service + Field Service                           |
| Data Platform    | Azure Data Lake (basic), Power Automate                                 |
| AI Maturity      | Early-stage — No AI CoE (Center of Excellence), no prompt library       |
| Data Quality     | HR and claims data siloed in 3 legacy systems with inconsistent schemas |
| Compliance       | Patient data subject to HIPAA                                           |

### Key Challenges

**Challenge 1 — Data Fragmentation & Compliance:** Patient and claims data is fragmented across 3 legacy systems with no unified index. HIPAA mandates strict data residency, access controls, and audit logging for any AI workload touching patient records.

**Challenge 2 — Governance Gap:** When a CoE is missing or inadequate, shadow AI and under-governance become critical risks — overcentralization leads to bottlenecks, while under-governance leads to ungoverned AI adoption. CHG has no AI CoE, no agent governance charter, and no responsible AI policy. Business teams are already deploying agents in Copilot Studio without architecture review.

**Challenge 3 — ROI Uncertainty & Adoption Risk:** The CTO wants 4 AI agent use cases live within 90 days. However, CHG has conducted no use case prioritization exercise, has no executive sponsor, and IT is concerned about low user adoption due to the absence of change management planning.

You are designing a Field Service Routing solution that:

* Retrieves technician data from Dynamics 365
* Uses HIPAA-sensitive patient location data
* Triggers workflows via Power Automate
* Escalates complex cases to supervisors

You must design a secure and scalable multi-agent architecture.

### Question

Which design decisions are appropriate? (Select ALL that apply)

**Choices:**

* Design a sequential workflow for controlled end-to-end processing
* Use a single agent to manage all operations and simplify architecture
* Separate agents based on security boundaries (patient data vs operations)
* Use parallel processing where independent data retrieval tasks exist
* Host all models in isolated compute environments by default

### Responses

* Design a sequential workflow for controlled end-to-end processing
* Use a single agent to manage all operations and simplify architecture
* Separate agents based on security boundaries (patient data vs operations)
* Use parallel processing where independent data retrieval tasks exist

---

## Question 52

**Statement:** "For a high-volume enterprise workflow automation scenario that requires dynamic AI-driven insights, developer extensibility, and automated suggestions, combining generative pages, agent feed, and code-first enhancements is a recommended architectural pattern."

**Choices:**

* True
* False

**Response:** True

---

## Question 53

A business unit requests urgent deployment of a custom connector that integrates an external market intelligence vendor into Copilot for Dynamics 365 Sales. The connector is built and tested, but the legal team has not reviewed the third-party vendor's privacy policy or data terms. The business sponsor insists on a same-week launch.

### What should the architect recommend?

**Choices:**

* Deploy the connector immediately and schedule the legal review for post-launch
* Enable the connector in the dev environment only until legal review is complete
* Delay deployment until legal and compliance review of the external data source is completed
* Certify the connector organization-wide to streamline the compliance review process

**Response:** Delay deployment until legal and compliance review of the external data source is completed

---

## Question 54

A solution architect is beginning the ALM design for a new AI-powered sentiment detection feature in Dynamics 365 Customer Service. The development team is eager to start building prompts and configuring conversation boosters. The architect must determine the correct first step before any development activity begins.

### What should the architect do FIRST?

**Choices:**

* Build prompts for sentiment classification and configure conversation boosters in Copilot
* Set up environment variables for connectors, API endpoints, and knowledge indices
* Package and version the agent assets inside a solution file using semantic versioning
* Define AI use cases, required data sources, customer data flows, sensitivity labels, and compliance constraints

**Response:** Define AI use cases, required data sources, customer data flows, sensitivity labels, and compliance constraints

---

## Question 55

A global pharmaceutical company needs a conversational AI agent to assist regulatory compliance officers. The process involves highly proprietary compound data, strict FDA-governed decision workflows, and internal IP that cannot be shared with any external vendor. The organization has a mature AI engineering team.

### Which AI development approach should the architect recommend?

**Choices:**

* Buy — Use a prebuilt Microsoft 365 Copilot solution to accelerate time-to-value
* Extend — Customize Copilot Studio with grounding documents from SharePoint
* Build — Develop a fully custom AI solution to maintain data control and regulatory compliance
* Extend — Use Azure AI Foundry with a fine-tuned model connected to SharePoint

**Response:** Build — Develop a fully custom AI solution to maintain data control and regulatory compliance

---

## Question 56

A retail organization wants to give warehouse staff access to demand planning insights through Copilot. Staff rarely leave the operational workspace view. Two options are under discussion: a sidecar Copilot experience or an embedded AI approach. The architect must select the best fit.

### Which AI experience model best fits this scenario, and why?

**Choices:**

* Sidecar Copilot — because it supports natural language chat and is easier to configure
* External orchestration — because it allows cross-application automation
* Embedded AI — because it surfaces insights directly within the workspace, reducing navigation overhead
* Sidecar Copilot — because it supports workflow summaries across modules using standardized entity metadata

**Response:** Embedded AI — because it surfaces insights directly within the workspace, reducing navigation overhead

---

## Question 57

A public-facing AI customer support agent for a bank allows users to upload PDF attachments as part of their service requests. During red team testing, the security team discovers that attackers have embedded hidden override instructions within uploaded PDFs, successfully steering the agent to bypass its system-level safety instructions and return restricted account information.

### What is the MOST effective mitigation the architect should implement?

**Choices:**

* Disable PDF upload support entirely to eliminate the attack vector
* Add CAPTCHA verification to the upload form to ensure only human users can submit files
* Enable daily manual review of all uploaded files by a security analyst
* Strengthen input and output filtering — strip unsafe embedded content and HTML from inputs, limit accepted file types, apply safety filters on model outputs, and block code execution attempts

**Response:** Strengthen input and output filtering — strip unsafe embedded content and HTML from inputs, limit accepted file types, apply safety filters on model outputs, and block code execution attempts

---

## Question 58

An IT lead at a financial services firm argues that storing service principal credentials in encrypted Azure Key Vault secrets is functionally equivalent to using managed identities for AI agent-to-Azure authentication, since both provide secure, governed access to Azure resources. The lead recommends using Key Vault credentials to maintain flexibility for multi-cloud deployments.

**TRUE or FALSE:** "Storing encrypted service principal credentials in Azure Key Vault is an acceptable substitute for managed identities when securing AI agent-to-Azure authentication in an enterprise AI deployment."

**Choices:**

* True
* False

**Response:** False

---

## Question 59

An insurance company is preparing to launch an AI agent for claims triage. During a structured Responsible AI review, the fairness assessment reveals that the agent generates statistically different outcomes for similar claim profiles submitted by customers from different demographic groups. The product owner wants to launch on the scheduled date and address the bias issue in a post-launch patch.

### What should the architect recommend?

**Choices:**

* Launch on schedule but add a disclaimer that the agent's recommendations are AI-generated and subject to change
* Launch to a limited pilot group and use production telemetry to quantify the bias before patching
* Delay the launch until the fairness issue is identified, root-caused, and mitigated — Fairness is a core Responsible AI principle that must be satisfied before deployment
* Replace the AI agent with a manual rules-based triage system to eliminate bias risk entirely

**Response:** Delay the launch until the fairness issue is identified, root-caused, and mitigated — Fairness is a core Responsible AI principle that must be satisfied before deployment

---

## Question 60

### Customer Background

Contoso HealthServices Group (CHG) is a mid-sized US healthcare services organization operating across 12 states with approximately 8,500 employees spanning administrative, clinical support, and field operations. CHG manages patient intake, claims processing, HR onboarding, and field service coordination. The organization runs on a Microsoft 365 E5 license stack and uses Dynamics 365 Customer Service for patient case management.

### Technology Background

| Component        | Detail                                                                  |
| ---------------- | ----------------------------------------------------------------------- |
| Productivity     | Microsoft 365 E5 (Teams, SharePoint, Outlook)                           |
| CRM / Operations | Dynamics 365 Customer Service + Field Service                           |
| Data Platform    | Azure Data Lake (basic), Power Automate                                 |
| AI Maturity      | Early-stage — No AI CoE (Center of Excellence), no prompt library       |
| Data Quality     | HR and claims data siloed in 3 legacy systems with inconsistent schemas |
| Compliance       | Patient data subject to HIPAA                                           |

### Key Challenges

**Challenge 1 — Data Fragmentation & Compliance:** Patient and claims data is fragmented across 3 legacy systems with no unified index. HIPAA mandates strict data residency, access controls, and audit logging for any AI workload touching patient records.

**Challenge 2 — Governance Gap:** When a CoE is missing or inadequate, shadow AI and under-governance become critical risks — overcentralization leads to bottlenecks, while under-governance leads to ungoverned AI adoption. CHG has no AI CoE, no agent governance charter, and no responsible AI policy. Business teams are already deploying agents in Copilot Studio without architecture review.

**Challenge 3 — ROI Uncertainty & Adoption Risk:** The CTO wants 4 AI agent use cases live within 90 days. However, CHG has conducted no use case prioritization exercise, has no executive sponsor, and IT is concerned about low user adoption due to the absence of change management planning.

CHG is experiencing inconsistent AI outputs across departments due to fragmented data sources and lack of unified business definitions. A proposal suggests simplifying the solution by relying only on existing data models and Copilot capabilities.

**Statement:** This approach will provide consistent and governed cross-domain reasoning for CHG.

**Choices:**

* True
* False

**Response:** False
