# Sami Horani

Principal Software Engineer and Systems Architect with 25+ years of experience building backend platforms, APIs, distributed systems, observability platforms, and enterprise-scale production systems across media, telecommunications, cloud, and financial analytics domains.

I focus on backend leverage: clean API contracts, normalized data models, production observability, infrastructure automation, and product experiences that stay simple because the platform underneath is doing the hard work.

## Featured Project: Finance Analytics Platform

A full-stack investment analytics system designed around secure APIs, normalized financial data, portfolio performance services, Monte Carlo simulation, and a native iOS client.

I built an idempotent private cloud platform and finance data system with automated infrastructure, centralized secrets, observability, resilient backups, and a modular ETL pipeline that normalizes messy financial statements into API-ready analytics.

[View the project site](https://horani.net/projects/)

### iOS Product Screens

<p>
  <img src="https://horani.net/projects/IMG_3034.jpeg" width="260" alt="iOS retirement planning screen with Monte Carlo simulation and retirement balances">
  <img src="https://horani.net/projects/IMG_3037.jpeg" width="260" alt="iOS portfolio analytics screen showing market value and realized gain loss">
  <img src="https://horani.net/projects/IMG_3035.jpeg" width="260" alt="iOS tax dashboard showing taxable investment income and dividends">
  <img src="https://horani.net/projects/IMG_3036.jpeg" width="260" alt="iOS tax optimization screen showing taxable accounts and lot strategy comparison">
</p>

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

[View the full Finance Platform architecture diagram](https://projects.horani.net/architecture.jpg)

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

<p>
  <img src="https://projects.horani.net/grafana-live-logs-mobile.png" width="260" alt="Grafana live logs dashboard showing recent service log events and log volume">
  <img src="https://projects.horani.net/grafana-service-health-mobile.png" width="260" alt="Grafana service health dashboard showing success rate, database connections, errors, and throughput">
  <img src="https://camo.githubusercontent.com/b9960372dc2fc3692ed738e3693f80abaaa5a16bef34bc38c81797a554961984/68747470733a2f2f686f72616e692e6e65742f70726f6a656374732f67726166616e612d6c6f672d636f6e746578742d6d6f62696c652e706e67" width="260" alt="Grafana structured log context view for the finance-api service">
</p>

## Infrastructure Engineering

The platform is backed by repeatable provisioning, service configuration, deployment automation, and operational workflows.

- Terraform modules and cloud-init templates for application, database, proxy, media, network, DNS, and secrets services.
- Ansible inventories, variables, and service playbooks for WireGuard, Pi-hole, Vaultwarden, reverse proxy routing, web deployment, and DDNS.
- GitHub Actions workflows for Terraform formatting and validation, Ansible syntax checks, infrastructure plans, and manual service dispatches.
- Vaultwarden-backed helpers that sync selected credentials into the local Python keyring while keeping machine-specific values out of Git.

## Architecture Strengths

This is a small-scale production platform: automated provisioning, isolated workloads, centralized ingress, DNS, secrets, observability, storage, and backup/recovery. The strength of the architecture is that it is real infrastructure, not a toy demo.

- Clear separation of concerns across application, database, media, proxy, DNS, backup, and secrets services, reducing blast radius and creating clean ownership boundaries.
- Automation-first delivery with Terraform, Ansible, Docker Compose, Make, and GitHub Actions so environments are reproducible instead of manually assembled.
- Idempotent desired-state operations: playbooks and automation can be rerun to create users, mount storage, install services, configure Nginx Proxy Manager, deploy containers, apply DNS/cert settings, and recover after rebuilds without manually remembering steps.
- Production-style networking with reverse proxy routing, Cloudflare DNS, Pi-hole/Unbound, TLS automation, internal hostnames, and controlled service exposure.
- Practical secrets management with Vaultwarden-backed workflows, local secret caching, and Ansible/Make integration instead of hardcoded credentials.
- Observability maturity through Prometheus, Loki, Tempo, OpenTelemetry Collector, Grafana dashboards, and FastAPI instrumentation.
- Data durability and recovery planning with PBS, encrypted backup storage, restic history, LVM thin pool checks, and backup troubleshooting workflows.
- Modular internal platform design where the Finance API, visualization app, media stack, secrets service, proxy automation, and database services share reusable infrastructure patterns.
- Operator-level debugging discipline using system, storage, container, network, Grafana, and log diagnostics to validate and troubleshoot the platform.

## Private Cloud Infrastructure Platform

Infrastructure-as-code for a virtualized private cloud environment. The platform provisions VMs and containers with Terraform, configures hosts and services with Ansible, and wraps common operations in Make targets.

### What It Manages

- VMs and containers for app, database, proxy, media, DNS, secrets, and supporting infrastructure.
- WireGuard VPN, Pi-hole DNS/DHCP, Nginx Proxy Manager, Vaultwarden, and Cloudflare/DDNS automation.
- Plex, OpenCloud, media host preparation, proxy automation, and web deployment workflows.
- Virtualization host tasks including GPU preparation and encrypted backup disk automounting.
- Backup server encrypted disk setup and recovery-oriented storage workflows.

### IaC Repository Shape

```text
ansible/              production inventory, host/group vars, and service playbooks
install/              platform installer and first-boot helpers
scripts/              backup, keyring, template, and utility scripts
terraform/            virtual infrastructure resources and cloud-init templates
vars/                 Make variable definitions by domain
.github/workflows/    infrastructure CI/CD workflows
makefile              local automation entry point
```

### Common Automation Surface

```bash
make tf-init
make tf-plan
make tf-apply
make wireguard
make pihole
make vaultwarden
make secrets
make proxy-config
make web
make ddns
```

### Idempotency and Safety

Most day-to-day targets are designed to converge the environment toward desired state. Terraform manages resource lifecycle, while Ansible service targets rerun safely for configuration drift, rebuilds, and recovery work.

- `make tf-plan` is read-only.
- `make tf-apply` converges Terraform-managed resources.
- Service targets such as `wireguard`, `vaultwarden`, `secrets`, `proxy-config`, `web`, and `ddns` run Ansible playbooks intended to be rerunnable.
- App and media targets such as `app-data`, `app-loki-plugin`, `app-inject-secrets`, `media-hw-attach`, `media-guest-prep`, `media-plex`, and `media-opencloud` support operational configuration.
- `recreate-*` targets are intentionally destructive and are treated as rebuild operations, not routine configuration.

### GitHub Actions

Infrastructure CI/CD validates changes before they touch the private infrastructure environment.

- Pull requests run Terraform formatting, Terraform validation, and Ansible syntax checks.
- Pushes to `main` run validation and Terraform planning on a self-hosted Linux runner.
- Manual dispatch supports Terraform plan/apply plus service workflows for WireGuard, Pi-hole, Vaultwarden, secrets, proxy configuration, web deployment, and DDNS.
- Self-hosted runners are used where private infrastructure APIs and Ansible targets are required.

### WireGuard and Secrets Workflows

WireGuard provisioning is automated through Ansible playbooks and helper scripts that generate client keys, add peers idempotently, write client configs, and only restart the service when a peer is changed.

Vaultwarden-to-keyring helpers sync selected vault items into the local Python keyring. Sync operations reconcile renamed or deleted items, avoid exporting secrets into shell sessions, and provide Python helpers for applications that need password retrieval.

## ETL and Data Platform Strengths

The finance pipeline is built for messy real-world financial data, not clean demo CSVs. It ingests brokerage statements, credit-card activity, PDFs, and multi-institution records, then normalizes them into financial domain objects that APIs and visualizations can use.

- Modular ingestion by source and statement section, including Fidelity, credit cards, activity, holdings, options, and statement-specific sections.
- Clear pipeline shape: ingestion -> processing -> storage -> API -> visualization.
- Normalization layer that converts raw statements into structured holdings, activity, transactions, categories, summaries, and API-ready data.
- Extensible parser design so new statement formats or financial institutions can be added without rewriting the whole pipeline.
- Financial domain modeling across accounts, holdings, performance summaries, periods, portfolios, categories, tax views, cash views, and credit views.
- Analytics-ready outputs that support portfolio performance, tax intelligence, retirement planning, simulations, and spending analysis.

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
