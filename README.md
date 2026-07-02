# Sami Horani

Principal Software Engineer and Systems Architect with 25+ years of experience building backend platforms, APIs, distributed systems, observability platforms, and enterprise-scale production systems across media, telecommunications, cloud, and financial analytics domains.

I focus on backend leverage: clean API contracts, normalized data models, production observability, infrastructure automation, and product experiences that stay simple because the platform underneath is doing the hard work.

## Featured Project: Finance Analytics Platform

A full-stack investment analytics system designed around secure APIs, normalized financial data, portfolio performance services, Monte Carlo simulation, and a native iOS client.

[View the project site](https://horani.net/projects/)

### Platform Scope

- Python / FastAPI backend services
- Secure REST APIs
- Statement ingestion and normalization
- Portfolio performance analytics
- Monte Carlo simulation
- Native iOS app integration
- Prometheus / Grafana / OpenTelemetry observability
- Terraform / Ansible infrastructure automation
- GitHub Actions CI/CD workflows

### What I Owned

- Product ownership from technical strategy and architecture through backend implementation, client integration, and operations.
- API-first design for portfolio analytics, holdings, transactions, performance, and simulations.
- Data-intensive backend pipelines that convert brokerage-specific inputs into a canonical financial model.
- Infrastructure automation for service provisioning, configuration, secrets workflows, and deployment validation.

## Architecture

The platform separates ingestion, normalization, analytics, and presentation layers so each capability can evolve independently. The iOS app is intentionally thin: the backend owns financial logic, analytics, data quality, and API contracts.

```text
Brokerage Statements
  -> Ingestion Pipeline
  -> Normalization Engine
  -> FastAPI Services
  -> iOS Client
```

## Backend APIs

APIs are organized around user-facing financial capabilities rather than implementation details. The goal is a clean developer experience, clear contracts, and backend services that can support multiple clients over time.

| Area | Example Endpoints | Purpose |
| --- | --- | --- |
| Portfolio APIs | `GET /portfolio/holdings`, `GET /portfolio/accounts`, `GET /portfolio/allocation` | Normalized holdings, account views, and allocation summaries |
| Performance APIs | `GET /performance/xirr`, `GET /performance/history`, `GET /performance/roi` | Historical performance, return metrics, and portfolio growth |
| Analytics APIs | `POST /analytics/monte-carlo`, `GET /analytics/risk`, `GET /analytics/mag7` | Risk analysis, scenario modeling, simulations, and portfolio insights |
| Import APIs | `POST /statements/import`, `GET /statements/{id}/validation`, `GET /transactions/normalized` | Statement uploads, validation, and canonical transactions |

## Data Pipelines

Brokerage statements and exports vary heavily by institution, format, terminology, and reporting quirks. The backend normalizes this data into consistent domain objects for holdings, transactions, contributions, performance, and account history.

- Statement parsing and extraction
- Domain validation and reconciliation
- Canonical transaction model
- Portfolio history and performance views
- Analytics-ready data services

```text
Raw Statement Data
  -> extraction
  -> row validation
  -> domain normalization
  -> canonical model
  -> analytics APIs
  -> iOS product experience
```

## Observability

The backend is instrumented with OpenTelemetry-style service metadata, Prometheus metrics, Grafana dashboards, and Loki-backed structured logs.

- API monitoring: request rate, success rate, 5xx error rate, status-code breakdowns, and component-level traffic.
- Performance visibility: P95 latency, throughput, slow-route analysis, and active database connection tracking.
- Structured troubleshooting: searchable live logs with service labels, Docker metadata, request paths, HTTP status, and timestamped context.

## Infrastructure Engineering

The platform is backed by repeatable provisioning, service configuration, deployment automation, and operational workflows.

- Terraform modules and cloud-init templates for application, database, proxy, media, network, DNS, and secrets services.
- Ansible inventories, variables, and service playbooks for WireGuard, Pi-hole, Vaultwarden, reverse proxy routing, web deployment, and DDNS.
- GitHub Actions workflows for Terraform formatting and validation, Ansible syntax checks, infrastructure plans, and manual service dispatches.
- Vaultwarden-backed helpers that sync selected credentials into the local Python keyring while keeping machine-specific values out of Git.

## iOS Product Capabilities

- Retirement planning with Monte Carlo simulation, withdrawal modeling, account aggregation, and long-term projection APIs.
- Tax intelligence for dividends, taxable income, multi-year account rollups, and normalized investment income services.
- Gain optimization workflows that compare taxable gain outcomes across accounts, tax rates, tickers, and sale targets.
- Portfolio analytics for holdings aggregation, market value analytics, realized gain/loss reporting, and cross-account portfolio views.
- Credit and spending analytics for transaction ingestion, merchant aggregation, category modeling, and monthly spend trends.

## Engineering Decisions

- Backend owns financial correctness: calculations, validation, and normalization live in services instead of being duplicated across clients.
- APIs map to product capabilities: endpoints reflect how users reason about portfolios, performance, risk, statements, and accounts.
- Canonical model reduces integration complexity: once data is normalized, analytics and client features can be built without re-solving statement-specific problems.
- Infrastructure is reproducible: service creation, configuration, validation, and deployment are expressed as code so environments can be rebuilt and audited.

## Core Strengths

- API and microservices architecture
- AI/ML-driven automation
- Cloud platforms: Azure and AWS
- Enterprise integration and DevOps
- Observability, monitoring, and incident reduction
- Technical leadership and cross-functional collaboration
