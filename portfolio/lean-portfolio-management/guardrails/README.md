# Guardrails

Guardrails are policies that guide decentralized portfolio decision-making. They enable autonomy while ensuring alignment with strategic intent and financial discipline.

## Types of Guardrails

| Type | Description |
|---|---|
| **Spending Guardrails** | Budget thresholds per value stream or category |
| **WIP Limits** | Max number of epics in flight simultaneously |
| **Architecture Guardrails** | Non-negotiable technical standards and policies |
| **Compliance Guardrails** | Regulatory, legal, or security mandates |

## Current Guardrails

### Budget Guardrails

<!-- TODO: Define budget allocation rules -->

| Category | Max % of Portfolio Budget | Notes |
|---|---|---|
| New Features / Business Epics | ~60% | Core value delivery |
| Enabler / Technical Debt | ~20% | Architectural runway |
| Innovation / Exploration | ~10% | Spikes, prototypes |
| Operations / Run costs | ~10% | Keep the lights on |

### WIP Limits

<!-- TODO: Set WIP limits per Portfolio Kanban state -->

| Kanban State | WIP Limit |
|---|---|
| Reviewing | 5 |
| Analyzing | 3 |
| Implementing | 8 |

### Architecture Guardrails

<!-- TODO: Add non-negotiable architecture standards -->

- All systems must expose APIs (REST or GraphQL)
- Cloud-first: prefer managed services
- Security: zero-trust model required for all new solutions
- Observability: all services must emit structured logs and traces

<!-- TODO: Update guardrails after each Participatory Budgeting session -->
