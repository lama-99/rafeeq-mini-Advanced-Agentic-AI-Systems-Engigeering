# Rafeeq Mini · رفيق المصغّر

Rafeeq Mini is a bilingual multi-agent delivery-support system developed as part of the **Advanced Agentic AI Systems Engineering** training program.

رفيق المصغّر هو نظام متعدد الوكلاء وثنائي اللغة لدعم عمليات التوصيل، تم تطويره ضمن برنامج **هندسة أنظمة الذكاء الاصطناعي التوكيلي المتقدمة**.

---

## About the Project

Rafeeq Mini demonstrates a safe agentic AI workflow for handling delivery-support requests in Arabic and English.

The project focuses on:

- Multi-agent orchestration
- Supervisor-based routing
- Specialized agent responsibilities
- Scoped memory
- Policy retrieval
- Refund decision workflows
- Human-in-the-loop approval
- Security guardrails
- Bounded execution
- Redacted tracing and monitoring
- Functional and security evaluation

The project uses controlled synthetic course data and an offline deterministic training environment.

---

## Architecture

Rafeeq Mini uses a **Supervisor + Specialist Agents** architecture.

```text
                    User
                      |
                      v
                 Supervisor
                /          \
               v            v
        Orders Agent    Refund Agent
             |               |
             v               v
      Order Status      Refund Context
          Tools          + Refund Tool
                              |
                              v
                       Approval Gate
                    (when required)
```

### Supervisor

The Supervisor coordinates the workflow.

Responsibilities:

- Route the request
- Delegate tasks
- Collect specialist results
- Finish or escalate the workflow

The Supervisor does not execute specialist business tools directly.

### Orders Agent

Responsible for order-related requests.

Main tool:

`get_order_status`

The Orders Agent operates as a read-oriented specialist and does not perform refund writes.

### Refund Agent

Responsible for refund-related workflows.

Main tools:

`get_refund_context`

`create_refund_request`

Sensitive refund actions remain governed by eligibility checks and human approval controls.

---

## Why Multi-Agent?

A single agent can be appropriate when tasks share the same context, tools, permissions, and risk level.

Rafeeq Mini separates Orders and Refund responsibilities because they have different:

- Tools
- Permissions
- Context requirements
- Action risks
- Safety controls

This creates clearer **tool boundaries** and supports the **principle of least privilege**.

The architecture intentionally keeps the number of agents small to avoid unnecessary orchestration complexity.

---

## Workflow

A typical Rafeeq Mini request follows this flow:

```text
User Request
     |
     v
Input / Safety Checks
     |
     v
Supervisor Routing
     |
     +-------------------+
     |                   |
     v                   v
Orders Agent        Refund Agent
     |                   |
     v                   v
Scoped Tool         Policy + Eligibility
Execution           Evaluation
                         |
                         v
                  Approval Required?
                    /          \
                  Yes           No
                   |             |
                   v             v
             Human Approval   Continue
                    \           /
                     v         v
                    Result
                      |
                      v
              Structured Response
```

---

## Agent Delegation

Rafeeq Mini uses structured delegation instead of passing unrestricted conversation context between agents.

A specialist receives only the information required for its task.

Examples of delegation fields include:

- Target agent
- Subgoal
- Order ID
- Locale
- Ticket information

This supports controlled context sharing and reduces unnecessary exposure between components.

---

## Memory & Retrieval

The project demonstrates both session memory and scoped retrieval.

Memory and retrieval are constrained before ranking or use.

Relevant controls include:

- Customer ownership scope
- Active records
- Expiry checks
- Current policy version
- Locale
- Policy category

This helps prevent unrelated or stale information from entering agent decisions.

---

## Refund Safety Boundary

Refund actions have stronger controls because they can create external side effects.

The workflow checks:

1. Customer ownership
2. Refund eligibility
3. Existing refund state
4. Refund amount
5. Required approval
6. Controlled write execution

Refunds above **SAR 500** require human approval before the sensitive write proceeds.

The workflow resumes the same scoped action after approval instead of creating an uncontrolled new action.

---

## Security Controls

Rafeeq Mini includes controls and tests for:

- Cross-customer access
- Approval bypass
- Duplicate refunds
- Direct prompt injection
- Indirect prompt injection
- Write retry attempts
- Step exhaustion
- Privilege escalation

Additional safeguards include:

- Scoped tool permissions
- Human approval gates
- Bounded steps
- Bounded handoffs
- Bounded reflection
- Redacted tracing
- Controlled write behavior

---

## Public Security Evaluation

The final public security suite passed:

**8 / 8 security cases**

The evaluated cases include:

```text
SEC-01  Cross-customer access
SEC-02  Approval bypass
SEC-03  Duplicate refund
SEC-04  Direct prompt injection
SEC-05  Indirect prompt injection
SEC-06  Write retry attempt
SEC-07  Step exhaustion
SEC-08  Privilege escalation
```

A learner-defined synthetic security case was also used to demonstrate a weak local guard and verify the repaired guard without breaking the existing public security cases.

---

## Functional Evaluation

Final functional evaluation:

**8 / 8 functional cases passed**

| Metric | Result |
|---|---:|
| Functional pass rate | 100% |
| Security pass rate | 100% |
| Route accuracy | 100% |
| Outcome accuracy | 100% |
| Unauthorized writes | 0 |
| Maximum steps | 4 |
| Maximum reflections | 1 |
| Critical gates | PASS |

---

## Observability

Rafeeq Mini records structured and redacted trace events.

Trace validation checks include:

- Required trace fields
- Redacted records
- No forbidden sensitive keys
- Valid parent/child span relationships
- Bounded reflection

The final trace validation passed all required checks.

---

## Optimization

The project includes a measured policy-retrieval cache optimization.

The cache key is scoped using:

- Locale
- Policy category
- Active policy version

Customer data is intentionally excluded from the cache key.

This demonstrates that performance optimization must preserve security boundaries and result equivalence.

---

## Evidence & Artifacts

The project generates structured evidence for assessment and review.

Key artifacts include:

```text
reports/assessment_results.json
reports/SECURITY_ASSESSMENT.md
reports/PROJECT_REPORT.md
reports/monitoring_dashboard.png
trace.jsonl
```

Learning-gate evidence is also recorded for Day 1, Day 2, and Day 3.

---

## Learning Progress

| Stage | Status |
|---|---|
| Setup | COMPLETE |
| Day 1 | COMPLETE |
| Day 2 | COMPLETE |
| Day 3 | COMPLETE |
| Final Assessment | COMPLETE |

Detailed learning progress is documented in:

`LEARNING_PROGRESS.md`

---

## Final Assessment

The final project assessment completed successfully.

- Functional tests: **PASS**
- Security tests: **PASS**
- Critical gates: **PASS**
- Learner exercises: **COMPLETE**
- Final readiness: **READY**
- Safe export: **CREATED**

---

## Run & Test

The project was developed and tested using **Google Colab**.

The training implementation runs using controlled synthetic data and an offline deterministic stub.

Public tests, functional evaluation, security evaluation, trace validation, and export safety checks are used to verify the workflow.

---

## Engineering Decisions

### 1. Specialized Tool Boundaries

Orders and Refund workflows use different tools and permissions rather than giving every agent unrestricted access.

### 2. Human Approval for Sensitive Actions

High-value refund writes require human approval instead of allowing the agent to independently perform higher-impact actions.

### 3. Bounded Execution

Steps, transitions, handoffs, and reflection are bounded to reduce uncontrolled agent loops.

### 4. Scoped Context

Specialists receive task-specific structured context instead of unrestricted conversation history.

### 5. Safe Observability

Traces are structured and redacted so that system behavior can be evaluated without intentionally storing raw sensitive conversation content.

---

## Training Environment vs Production

Rafeeq Mini is a **training project**, not a production delivery platform.

The current implementation uses:

- Synthetic course data
- Offline deterministic behavior
- Simulated identity context
- Simulated approval workflows
- Local training tools and policies

A production implementation would require authoritative integrations for:

- Customer identity and authentication
- Delivery systems
- Payment and refund systems
- Policy management
- Approval systems
- Secrets management
- Durable storage
- Monitoring and audit infrastructure
- Production reliability and SLA controls

---

## Limitations

- No real customer or payment data is used.
- No live delivery platform is connected.
- The deterministic stub does not measure live-model quality.
- Provider cost and rate limits are outside the current implementation.
- Local approval and memory components are training simulations.
- Production deployment is outside the scope of this project.

---

## Training Program

**Advanced Agentic AI Systems Engineering**  
**هندسة أنظمة الذكاء الاصطناعي التوكيلي المتقدمة**

[SDAIA Academy on GitHub](https://github.com/SDAIAAcademy)

---

## Project

**Rafeeq Mini · رفيق المصغّر**
