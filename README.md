## Hey, I'm Peng Hian

Building a Solana validator operation from scratch — solo founder handling everything from bare metal to monitoring.

### Architecture

```
┌───────────────────────────────────────────────────────────────────┐
│                     Solana Validator Operation                    │
├───────────────────────────────────────────────────────────────────┤
│                                                                   │
│  DELEGATION (how stakers find you)                                │
│  ┌──────────────────┐  ┌──────────────────┐                       │
│  │ validators.app   │  │ Landing Page     │                       │
│  │ stakewiz.com     │  │ (your website)   │                       │
│  │ Free listings    │  │ Planned          │                       │
│  └──────────────────┘  └──────────────────┘                       │
│           │                    │                                  │
│           └────────────────────┘                                  │
│                    │                                              │
│                    │ Delegators stake via wallet (Phantom, etc.)  │
│                    ▼                                              │
│  VALIDATOR OPERATIONS (what you build + run)                      │
│  ┌──────────────────┐  ┌──────────────────┐  ┌──────────────────┐ │
│  │ solana-repro-    │  │ solana-ansible-  │  │ solana-          │ │
│  │ builds           │  │ kit              │  │ exporter         │ │
│  │                  │  │                  │  │                  │ │
│  │ Reproducible     │  │ Fleet provision  │  │ Prometheus       │ │
│  │ builds + release │  │ OS hardening     │  │ metrics +        │ │
│  │ Agave, Jito,     │  │ Client deploys   │  │ Grafana          │ │
│  │ Firedancer       │  │ Upgrades/rollback│  │ dashboards       │ │
│  │                  │  │                  │  │ 30+ metrics      │ │
│  │ ✅ Live          │  │ ✅ Live          │  │ ✅ Live          │ │
│  └──────────────────┘  └──────────────────┘  └──────────────────┘ │
│                                 │                                 │
│                                 ▼                                 │
│  MONITORING                                                       │
│  ┌──────────────────────────────────────────────────────────────┐ │
│  │ Prometheus + Grafana ✅    Alerting (PagerDuty) Planned      │ │
│  └──────────────────────────────────────────────────────────────┘ │
│                                 │                                 │
│                                 ▼                                 │
│  INFRASTRUCTURE                                                   │
│  ┌──────────────────────────────────────────────────────────────┐ │
│  │ Validator servers (dedicated hardware)                       │ │
│  │ Solana clients: Agave, Jito, Firedancer                      │ │
│  │ Security: SSH hardening, fail2ban, UFW (via ansible-kit)     │ │
│  └──────────────────────────────────────────────────────────────┘ │
└───────────────────────────────────────────────────────────────────┘
```

### How Solana Delegation Works

1. You run a validator with a **vote account**
2. Stakers delegate SOL to your vote account using any wallet
3. Rewards are automatic — stakers get their share, you take commission
4. No backend needed — delegation happens on-chain

### Live Repositories

The validator operations layer is built and running:

| Project | What it does | Status |
|---------|-------------|--------|
| [solana-repro-builds](https://github.com/angpenghian/solana-repro-builds) | Reproducible builds + release pipeline for Agave, Jito, Firedancer | ✅ Live |
| [solana-ansible-kit](https://github.com/angpenghian/solana-ansible-kit) | Fleet provisioning, OS hardening, validator deploys, upgrades | ✅ Live |
| [solana-exporter](https://github.com/angpenghian/solana-exporter) | Prometheus exporter — 30+ metrics, Grafana dashboard | ✅ Live |

### Roadmap

| What | Status |
|------|--------|
| Validator operations (build, deploy, monitor) | ✅ Done |
| CI/CD (GitHub Actions) | Next |
| Landing page for delegators | Planned |
| Alerting (PagerDuty/Slack) | Planned |

### Background

Solo founder running a Solana validator. Built the infrastructure layer first — secure builds, fleet automation, and monitoring. Now focused on operational maturity (CI/CD, alerting) before scaling.
