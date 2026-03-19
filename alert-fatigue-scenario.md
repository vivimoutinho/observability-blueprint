# Case Study: Eliminating Alert Fatigue

### Context
In a high-pressure financial environment, multiple monitoring tools (Datadog, Grafana, Splunk) were generating a high volume of redundant alerts, leading to "alert blindness" among the SRE team.

### The Problem
* **Redundancy:** The same incident triggered alerts in three different tools simultaneously.
* **Lack of Context:** Alerts like "CPU > 90%" triggered even when user experience was unaffected.
* **Burnout:** Engineers were receiving 50+ non-actionable notifications per shift.

---

### Engineering Strategy: "Signal over Noise"

#### 1. Consolidation & Deduplication
* Established **Datadog** as the primary source of truth for infrastructure metrics.
* Used **Splunk** exclusively for deep-dive log analysis and security auditing.
* Integrated alerts into a centralized incident bus (e.g., Slack/PagerDuty) to merge duplicates.

#### 2. Severity Classification
We categorized alerts into three distinct tiers:
* **Critical (P1):** Immediate customer impact. Wakes up the on-call engineer.
* **Warning (P2):** System is degraded but functional. To be addressed within 4 hours.
* **Informational (P3):** Trends and anomalies for review during business hours.

#### 3. Transitioning to SLO-Based Alerting
Instead of monitoring raw infrastructure (CPU/RAM), we shifted focus to **Service Level Indicators (SLIs)**:
* **Success Rate:** % of successful payment transactions.
* **Latency:** 95th percentile (p95) response time for API calls.

---

### Outcomes
* **Alert Volume:** 60% reduction in non-actionable notifications.
* **MTTR (Mean Time to Recovery):** Improved by 25% due to clearer incident signals.
* **Team Trust:** Engineers regained confidence in the monitoring system.

### Key SRE Learnings
* **An alert without a playbook is a bug:** If an engineer doesn't know exactly what to do when an alert fires, the alert shouldn't exist.
* **Observe the User, not just the Server:** Infrastructure metrics are secondary to the actual service availability.
