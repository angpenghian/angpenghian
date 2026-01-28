## Hey, I'm Peng Hian

Building a Solana staking operation from scratch — solo founder handling everything from bare metal to frontend.

### Full Stack Architecture

```
┌───────────────────────────────────────────────────────────────────┐
│                     Solana Staking Platform                       │
├───────────────────────────────────────────────────────────────────┤
│                                                                   │
│  FRONTEND                                                         │
│  ┌──────────────────┐  ┌──────────────────┐  ┌──────────────────┐ │
│  │ Staking Portal   │  │ Validator        │  │ Admin            │ │
│  │ Next.js          │  │ Analytics        │  │ Dashboard        │ │
│  │                  │  │ React            │  │ Fleet mgmt       │ │
│  │ Planned          │  │ Planned          │  │ Planned          │ │
│  └──────────────────┘  └──────────────────┘  └──────────────────┘ │
│                                 ▼                                 │
│  BACKEND                                                          │
│  ┌──────────────────┐  ┌──────────────────┐  ┌──────────────────┐ │
│  │ Staking API      │  │ Rewards Engine   │  │ Auth + Billing   │ │
│  │ Delegation mgmt  │  │ Epoch tracking   │  │ API keys         │ │
│  │ Validator pool   │  │ Payout calc      │  │ Usage metering   │ │
│  │ Planned          │  │ Planned          │  │ Planned          │ │
│  └──────────────────┘  └──────────────────┘  └──────────────────┘ │
│                                 ▼                                 │
│  INFRASTRUCTURE + DEVOPS                                          │
│  ┌──────────────────────────────────────────────────────────────┐ │
│  │                                                              │ │
│  │  Cloud + Networking          CI/CD + Release                 │ │
│  │  ┌──────────────────────┐    ┌──────────────────────────┐    │ │
│  │  │ Terraform (IaC)      │    │ GitHub Actions           │    │ │
│  │  │ AWS / bare metal     │    │ Build → Test → Deploy    │    │ │
│  │  │ VPC, firewall, DNS   │    │ Artifact verification    │    │ │
│  │  │ Planned              │    │ Planned                  │    │ │
│  │  └──────────────────────┘    └──────────────────────────┘    │ │
│  │                                                              │ │
│  │  Security                    Secrets + Config                │ │
│  │  ┌──────────────────────┐    ┌──────────────────────────┐    │ │
│  │  │ Hardened SSH         │    │ HashiCorp Vault          │    │ │
│  │  │ fail2ban, UFW        │    │ Validator keys           │    │ │
│  │  │ Audit logging        │    │ API secrets, certs       │    │ │
│  │  │ Done (ansible-kit)   │    │ Planned                  │    │ │
│  │  └──────────────────────┘    └──────────────────────────┘    │ │
│  │                                                              │ │
│  └──────────────────────────────────────────────────────────────┘ │
│                                 ▼                                 │
│  VALIDATOR OPERATIONS                                             │
│  ┌──────────────────┐  ┌──────────────────┐  ┌──────────────────┐ │
│  │ solana-repro-    │  │ solana-ansible-  │  │ solana-          │ │
│  │ builds           │  │ kit              │  │ exporter         │ │
│  │                  │  │                  │  │                  │ │
│  │ Reproducible     │  │ Fleet provision  │  │ Prometheus       │ │
│  │ builds + release │  │ OS hardening     │  │ metrics +        │ │
│  │ Agave, Jito,     │  │ Client deploys   │  │ Grafana          │ │
│  │ Firedancer       │  │ Upgrades/rollback│  │ dashboards       │ │
│  │                  │  │                  │  │ 26+ metrics      │ │
│  │ ✅ Live          │  │ ✅ Live         │  │ ✅ Live         │ │
│  └──────────────────┘  └──────────────────┘  └──────────────────┘ │
│                                 ▼                                 │
│  OBSERVABILITY                                                    │
│  ┌──────────────────────────────────────────────────────────────┐ │
│  │ Prometheus + Grafana    Logging (Loki/ELK)    Alerting       │ │
│  │ ✅ Live                 Planned               PagerDuty     │ │
│  │                                               Planned        │ │
│  └──────────────────────────────────────────────────────────────┘ │
│                                 ▼                                 │
│  BARE METAL / CLOUD                                               │
│  ┌──────────────────────────────────────────────────────────────┐ │
│  │ Validator servers (dedicated hardware)                       │ │
│  │ Solana clients: Agave, Jito, Firedancer                      │ │
│  └──────────────────────────────────────────────────────────────┘ │
└───────────────────────────────────────────────────────────────────┘
```

### Live Repositories

The validator operations layer is built and running in production:

| Project | What it does | Status |
|---------|-------------|--------|
| [solana-repro-builds](https://github.com/angpenghian/solana-repro-builds) | Reproducible builds + release pipeline for Agave, Jito, Firedancer | ✅ Live  |
| [solana-ansible-kit](https://github.com/angpenghian/solana-ansible-kit) | Fleet provisioning, OS hardening, validator deploys, upgrades | ✅ Live |
| [solana-exporter](https://github.com/angpenghian/solana-exporter) | Prometheus exporter — 30+ metrics, Grafana dashboard, production tested | ✅ Live |

### Roadmap

| Layer | What | Status |
|-------|------|--------|
| Validator Ops | Build, deploy, monitor validators | ✅ Done |
| CI/CD | GitHub Actions across all repos | Next |
| Infrastructure | Terraform for cloud/network provisioning | Planned |
| Secrets | HashiCorp Vault for key management | Planned |
| Logging | Centralized log aggregation (Loki or ELK) | Planned |
| Alerting | PagerDuty/Slack incident routing | Planned |
| Backend | Staking API, rewards engine, delegation management | Planned |
| Frontend | Staking portal, validator analytics, admin dashboard | Planned |

### Background

Solo founder building a Solana staking operation. Started from the infrastructure layer up — validator builds, fleet automation, and monitoring are live. Now working upward through CI/CD, cloud provisioning, and eventually the staking platform itself.
