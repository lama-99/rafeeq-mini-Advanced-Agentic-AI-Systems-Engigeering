# Rafeeq Mini · رفيق المصغّر

Rafeeq Mini is a bilingual multi-agent delivery-support system developed as part of the **Advanced Agentic AI Systems Engineering** training program.

رفيق المصغّر هو نظام متعدد الوكلاء وثنائي اللغة لدعم عمليات التوصيل، تم تطويره ضمن برنامج **هندسة أنظمة الذكاء الاصطناعي التوكيلي المتقدمة**.

---

## About the Project

Rafeeq Mini demonstrates a safe agentic AI workflow for handling delivery-support requests in Arabic and English.

The system uses a Supervisor to coordinate specialized agents for order and refund requests, with scoped tools, memory, security controls, and human approval for sensitive actions.

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

### Agent Responsibilities

- **Supervisor** — routing, delegation, coordination, and escalation.
- **Orders Agent** — handles order-status requests using scoped read tools.
- **Refund Agent** — handles refund eligibility and controlled refund actions.

Each agent receives only the tools and context required for its task, following the **principle of least privilege**.

---

## Workflow

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

Refunds above **SAR 500** require human approval before the sensitive action proceeds.

---

## Key Capabilities

- Arabic and English support
- Supervisor-based routing
- Specialized Orders and Refund agents
- Session and scoped memory
- Policy retrieval and filtering
- Human-in-the-loop approval
- Safe agent handoffs
- Security guardrails
- Redacted tracing and monitoring
- Bounded execution

---

## Security Evaluation

The project was tested against security scenarios including:

- Cross-customer access
- Approval bypass
- Duplicate refunds
- Direct and indirect prompt injection
- Write retry attempts
- Step exhaustion
- Privilege escalation

**Security evaluation: 8 / 8 cases passed.**

---

## Functional Evaluation

**8 / 8 functional cases passed.**

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

## Evidence & Artifacts

Key assessment artifacts include:

```text
reports/assessment_results.json
reports/SECURITY_ASSESSMENT.md
reports/PROJECT_REPORT.md
reports/monitoring_dashboard.png
trace.jsonl
```

---

## Learning Progress

| Stage | Status |
|---|---|
| Setup | COMPLETE |
| Day 1 | COMPLETE |
| Day 2 | COMPLETE |
| Day 3 | COMPLETE |
| Final Assessment | COMPLETE |

Detailed progress is documented in `LEARNING_PROGRESS.md`.

---

## Training Environment & Limitations

Rafeeq Mini is a **training project** developed and tested using Google Colab.

The current implementation uses synthetic course data and an offline deterministic environment. It is not connected to real customer, delivery, payment, or production systems.

---

## Training Program

**Advanced Agentic AI Systems Engineering**  
**هندسة أنظمة الذكاء الاصطناعي التوكيلي المتقدمة**

[SDAIA Academy on GitHub](https://github.com/SDAIAAcademy)

---

## Project

**Rafeeq Mini · رفيق المصغّر**
