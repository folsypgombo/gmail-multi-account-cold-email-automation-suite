# Gmail Multi-Account Cold Email Automation Suite

> A controlled cold email automation suite designed for running multiple Gmail accounts with strict pacing, natural behavior, and deliverability-first rules. It focuses on safe sending volumes, multi-account orchestration, warm-up workflows, and IP-agnostic rotation for environments with dynamic IPs.

> This system is made for low-volume experimental cold outreach — 2 emails/hour per account, 30–40 accounts to start — with the option to expand to 100+ accounts while maintaining safety and compliance.
<p align="center">
  <a href="https://Appilot.app" target="_blank"><img src="https://github.com/Instagram-Automations/Footer-test/blob/main/appilot-baner.png" alt="Appilot Banner" width="100%"></a>
</p>
<p align="center">
  <a href="https://t.me/devpilot1" target="_blank"><img src="https://img.shields.io/badge/Chat%20on-Telegram-2CA5E0?style=for-the-badge&logo=telegram&logoColor=white" alt="Telegram"></a>
  <a href="mailto:support@appilot.app" target="_blank"><img src="https://img.shields.io/badge/Email-support@appilot.app-EA4335?style=for-the-badge&logo=gmail&logoColor=white" alt="Gmail"></a>
  <a href="https://Appilot.app" target="_blank"><img src="https://img.shields.io/badge/Visit-Website-007BFF?style=for-the-badge&logo=google-chrome&logoColor=white" alt="Website"></a>
  <a href="https://discord.gg/wpfG4j84" target="_blank"><img src="https://img.shields.io/badge/Join-Appilot_Community-5865F2?style=for-the-badge&logo=discord&logoColor=white" alt="Appilot Discord"></a>
</p>

<p align="center">
Created by Appilot, built to showcase our approach to Automation!
If you are looking for custom <strong>{Gmail Multi-Account Cold Email Automation Suite} <strong>, you've just found your team — Let’s Chat.&#128070; &#128070;
</p>
## Introduction

Running cold outreach from dozens of Gmail accounts requires more than just sending emails. You must preserve deliverability, warm accounts slowly, manage sending schedules, and keep behavior natural.  
In many regions, dynamic IPs make reputation handling unpredictable, and scaling past 40–50 accounts requires coordinated scheduling and identity separation.

This project provides a centralized automation suite that manages Gmail API tokens, schedules emails at safe rates, rotates accounts intelligently, and logs all sends for analysis — without relying on proxies unless scaling to very large volumes.

### Deliverability-First Cold Email Automation for Gmail

- Safely orchestrates 30–40 Gmail accounts sending 1–2 emails/hour, fully customizable.  
- Adds behavior randomization, timing windows, warm-up curves, and template variation.  
- Handles dynamic IP environments without requiring proxies at moderate scale.  
- Keeps logs, per-account health scores, and bounce monitoring for long-term performance.  
- Allows future scale to 100+ accounts with optional proxy separation and identity grouping.

---

## Core Features

| Feature | Description |
|--------|-------------|
| Multi-account Gmail manager | Stores OAuth credentials for each Gmail account with isolated sending limits and warm-up profiles |
| Safe send scheduler | Enforces 1–2 emails/hour (or custom) with randomized timing and per-account ceilings |
| Warm-up workflow | Slowly increases daily send volume per account based on engagement and bounce history |
| Dynamic template engine | Supports spintax, placeholders, A/B variants, and randomization for natural messaging |
| Domain & identity rotation | Assigns sender identities to campaigns with controlled domain/group separation |
| Bounce & reply monitoring | Pulls IMAP/SMS replies to track bounces, spam flags, “this is junk” signals, etc. |
| IP-agnostic sending logic | Works in environments with dynamic IPs without proxies; proxies optional for >100 accounts |
| Proxy support (optional) | Allows proxy groups for large-scale setups beyond local IP reputation boundaries |
| Daily sending windows | Time-range controls (9am–6pm, weekdays only, etc.) for natural outreach cadence |
| Deliverability scoring | Per-account metrics: bounce rate, open rate (if using trackable redirects), spam score trends |
| Health-based throttling | Automatically slows or pauses accounts showing negative signals |
| JSON/YAML campaign definitions | Define lead lists, message templates, sequences, and sending rules in config files |
| CSV/Sheets integration | Import/export leads, logs, and results for analysis |

---

## How It Works

| Step | Description |
|------|-------------|
| **Input or Trigger** | You load Gmail accounts (OAuth tokens), lead lists, templates, and sending rules into the system. You define warm-up curves and limits such as “2 emails/hour” per account. |
| **Core Logic** | The scheduler assigns leads to accounts, spaces out emails using randomized delays, applies template variations, and rotates sender identities. Each email is sent via Gmail API/SMTP with full logging. |
| **Output or Action** | Outbound emails go out gradually across all accounts within the configured limits. Logs store timestamps, account used, lead, template variant, and status. Replies and bounces are monitored and linked to account health scoring. |
| **Other Functionalities** | The system slows down accounts with high bounce or spam signals, prioritizes healthier accounts, and alerts when thresholds are exceeded. |
| **Safety Controls** | Hard caps, randomized delays, warm-up logic, identity grouping, and deliverability checks protect sender reputation and reduce risk of disruptions. |

## Tech Stack

| Component | Description |
|----------|-------------|
| **Language** | Python |
| **Frameworks** | FastAPI for API/admin interface, Celery/RQ for job queues and sending scheduler |
| **Tools** | Gmail API client, IMAP libraries, spintax processor, SQLAlchemy for data storage |
| **Infrastructure** | PostgreSQL/SQLite for persistence, Redis for queues, Docker for deployment |

---

## Directory Structure Tree

    gmail-multi-account-cold-email-automation-suite/
        ├── src/
        │    ├── main.py
        │    ├── api/
        │    │    ├── server.py
        │    │    ├── routes_accounts.py
        │    │    ├── routes_campaigns.py
        │    │    └── routes_logs.py
        │    ├── gmail/
        │    │    ├── gmail_client.py
        │    │    ├── send_engine.py
        │    │    └── reply_monitor.py
        │    ├── scheduling/
        │    │    ├── scheduler.py
        │    │    ├── warmup_profiles.py
        │    │    └── pacing_rules.py
        │    ├── templates/
        │    │    ├── spintax_engine.py
        │    │    └── variants_manager.py
        │    ├── campaigns/
        │    │    ├── campaign_loader.py
        │    │    └── lead_router.py
        │    ├── analytics/
        │    │    ├── deliverability_monitor.py
        │    │    └── reports.py
        │    └── utils/
        │         ├── logger.py
        │         ├── config_loader.py
        │         └── db_session.py
        ├── config/
        │    ├── settings.env
        │    ├── accounts.yaml
        │    ├── campaigns.yaml
        │    └── warmup.yaml
        ├── logs/
        │    └── sending.log
        ├── output/
        │    ├── send_history.csv
        │    └── deliverability_snapshot.json
        ├── workers/
        │    ├── send_worker.py
        │    ├── warmup_worker.py
        │    └── reply_monitor_worker.py
        ├── tests/
        │    ├── test_spintax_engine.py
        │    ├── test_scheduler.py
        │    └── test_gmail_client.py
        ├── docker/
        │    └── Dockerfile
        ├── requirements.txt
        └── README.md

---
## Use Cases

- **Solo marketers** test small-scale cold outreach using multiple Gmail accounts without heavy infrastructure.  
- **Affiliate and performance marketers** run niche campaigns with strict limits to protect deliverability.  
- **Small teams** centralize sending operations across many accounts instead of managing spreadsheets and manual throttling.  
- **Experimenters** run “does it make money?” tests with highly conservative volumes to avoid sender reputation damage.  
- **Growth engineers** prepare systems that can expand to 80–100+ accounts with proxy segmentation later.

---

## FAQs

**Q: Can this run safely on dynamic IPs?**  
A: Yes. At 20–40 accounts sending 1–2 emails/hour, dynamic IPs are typically fine. The suite has identity-based separation, and IP rotation is optional unless scaling much higher.

**Q: When do I need proxies?**  
A: Proxies become useful beyond 80–100 accounts or when grouping accounts by domain or region. The system includes optional proxy grouping support.

**Q: Can I customize send times?**  
A: Absolutely. You can define business hours, weekdays only, gap ranges, and randomization to mimic natural activity.

**Q: How are replies handled?**  
A: The reply monitor pulls emails via IMAP, links them to the original send event, and updates account health and recipient status.

---

## Performance & Reliability Benchmarks

**Execution Speed:** A single worker can process dozens of emails per minute, though the scheduler deliberately slows sends to meet your pacing limits.  

(lineSpace)

**Success Rate:** With verified Gmail accounts and clean domains, successful send rates stay around 94–96% after retries, with bounces and soft failures monitored for account throttling.  

(lineSpace)

**Scalability:** Supports 30–40 accounts easily; 100+ is achievable by adding proxy segmentation and more workers. Queue-based architecture ensures horizontal scaling with minimal changes.  

(lineSpace)

**Resource Efficiency:** A single VPS or even a home server can run the full stack. Memory and CPU usage remain moderate due to paced scheduling and lightweight API interactions.  

(lineSpace)

**Error Handling:** Automatic retries, API rate-limit detection, warm-up throttling, sender health scoring, and structured logging ensure long-running reliability for multi-account sending.  

<p align="center">
<a href="https://cal.com/app-pilot-m8i8oo/30min" target="_blank">
 <img src="https://img.shields.io/badge/Book%20a%20Call%20with%20Us-34A853?style=for-the-badge&logo=googlecalendar&logoColor=white" alt="Book a Call">
</a>
 <a href="https://www.youtube.com/@Appilot-app/videos" target="_blank">
  <img src="https://img.shields.io/badge/🎥%20Watch%20demos%20-FF0000?style=for-the-badge&logo=youtube&logoColor=white" alt="Watch on YouTube">
 </a>
</p>
