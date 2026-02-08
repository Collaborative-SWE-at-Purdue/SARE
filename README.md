# SARE  
**Secure Agent-Runtime Evaluations**

SARE is the **evaluation, testing, and analysis suite** for the **Agent Runtime** project.

This repository contains tooling for:
- adversarial testing of agent proposals,
- multi-agent and conflict simulations,
- runtime performance benchmarking,
- behavioral, security, and policy-enforcement analysis,
- structured metrics, logs, and report generation.

SARE is **not** the runtime itself. It is a *consumer* of the runtime, used to validate correctness, robustness, and security properties under controlled scenarios.

---

## Relationship to Agent Runtime

The system is intentionally split into two repositories:

- **Agent Runtime** (TypeScript)  
  Defines the agent execution runtime, proposal handling, validation, policy evaluation, and logging.

- **SARE** (this repository)  
  Exercises the runtime under adversarial, edge-case, and load scenarios, and produces metrics and reports.

The two repositories are linked but **decoupled by design**. This separation keeps:
- runtime logic clean and minimal,
- evaluation and simulation flexible and experimental,
- Python tooling isolated from production code.

➡️ **Agent Runtime repository:**  
*https://github.com/Collaborative-SWE-at-Purdue/Sec-Agent-Runtime*

---

## Scope of This Repository

SARE focuses on **evaluation**, not implementation.

### Included
- Adversarial proposal generation (malformed, unauthorized, boundary-probing)
- Multi-agent interaction and conflict testing
- Runtime throughput, latency, and determinism measurements
- Structured log ingestion and metric computation
- Human-readable reports (tables, figures, summaries)

### Explicitly Out of Scope
- Runtime implementation
- Agent proposal schema definitions
- Policy or capability logic design
- Production execution paths

---

## Architecture Overview

    High-level flow:
    Agent Runtime
    - produces structured logs  
    
    SARE
    - ingests logs
    - computes metrics
    - classifies outcomes
    - generates reports


SARE treats the runtime as a **black box** with a stable interface:
- inputs: proposals, execution parameters
- outputs: logs, responses, outcomes

---

## Repository Structure (Expected)
 
    /sare  
    /eval      # evaluation drivers and experiments  
    /sim       # adversarial and multi-agent simulations  
    /metrics   # metric definitions and computation  
    /ingest    # log parsing and normalization  
    /reports   # report generation (tables/figures/text)  
    /data      # generated datasets (gitignored)  
    README.md  


Exact structure may evolve as experiments expand.

---

## How SARE Interfaces with the Runtime

SARE may interact with the Agent Runtime via one or more of:
- CLI invocation
- Node.js subprocess execution
- Structured log file exchange

The precise integration mechanism is intentionally flexible and documented alongside the relevant experiments.

---

## Status

This repository is under active development.  
Interfaces, metrics, and scenarios may change as evaluation goals evolve.

---

## Design Principle

> **The runtime enforces behavior.  
> SARE observes, measures, and challenges it.**

This separation is intentional and architectural.

