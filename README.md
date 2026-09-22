# Rafeeq Mini · رفيق المصغّر

Rafeeq Mini is a bilingual delivery-support agent developed as part of the **Advanced Agentic AI Systems Engineering** course.

رفيق المصغّر هو وكيل ذكي ثنائي اللغة لدعم عمليات التوصيل، تم تطويره ضمن دورة **هندسة أنظمة الذكاء الاصطناعي التوكيلي المتقدمة**.

## About the Project

Rafeeq Mini demonstrates an agentic AI workflow for handling delivery-support requests in Arabic and English.

The project focuses on safe agent coordination, routing, memory, policy retrieval, refund decisions, human-in-the-loop approval, security controls, and monitoring.

## Current Capabilities

- Arabic and English support
- Supervisor-based orchestration and routing
- Specialized Orders and Refund agents
- Session memory
- Scoped long-term memory retrieval
- Policy retrieval and filtering
- Refund eligibility decisions
- Human-in-the-loop approval for sensitive actions
- Plan, execute, and re-plan workflows
- Safe agent handoffs
- Security guardrails and attack-case testing
- Redacted tracing and monitoring
- Functional and security evaluation

## Learning Progress

| Stage | Status |
|---|---|
| Setup | READY |
| Day 1 | PASS |
| Day 2 | PASS |
| Day 3 | PASS |
| Final Assessment | COMPLETE |

Detailed progress is documented in `LEARNING_PROGRESS.md`.

## Architecture

Rafeeq Mini uses a **Supervisor + Specialist Agents** architecture.

The Supervisor coordinates the workflow and routes requests to specialized agents:

- **Orders Agent** — handles order-status related tasks.
- **Refund Agent** — handles refund-related tasks and controlled refund actions.
- **Supervisor** — manages routing, delegation, coordination, and escalation.

Each specialist operates with a limited tool scope and receives only the context required for its task.

## Safety & Security

The project includes safety controls designed for agentic workflows, including:

- Customer-scoped access controls
- Human approval for high-value refund actions
- Duplicate refund protection
- Prompt injection detection
- Write-retry protection
- Step and reflection limits
- Privilege escalation controls
- Redacted trace logging
- Controlled tool permissions

## Evaluation

The final assessment includes functional, security, safety, and learner checks.

Final project status:

- Functional tests: **PASS**
- Security tests: **PASS**
- Critical gates: **PASS**
- Learner exercises: **COMPLETE**
- Final readiness: **READY**

## Run & Test

The project was developed and tested using **Google Colab**.

The workflow was evaluated using controlled synthetic course data and deterministic test scenarios.

Assessment evidence and project reports are generated as structured artifacts, including JSON reports and monitoring outputs.

## Expected Behavior

Rafeeq Mini routes delivery-support requests to the appropriate specialist workflow, retrieves scoped information, applies current refund policies, and pauses sensitive refund actions when human approval is required.

The system is designed to maintain bounded execution, controlled permissions, safe handoffs, and traceable decisions.

## Limitations

- The project uses controlled synthetic course data and scenarios.
- The current implementation operates in an offline deterministic training environment.
- It is not connected to real delivery, payment, or customer systems.
- Production identity, policy, secrets, and operational integrations are outside the current project scope.
- Final deployment is outside the scope of this training project.

## Training Program

**Advanced Agentic AI Systems Engineering**  
**هندسة أنظمة الذكاء الاصطناعي التوكيلي المتقدمة**

Training-program reference: SDAIA Academy on GitHub

## Project

**Rafeeq Mini · رفيق المصغّر**
