# SRE Dashboard Design Checklist
**Goal:** Creating actionable, high-signal visualizations for distributed systems.

---

## 1. The "5-Second Rule"
A responder should be able to look at a dashboard and understand the system's health in under 5 seconds.
* [ ] **Critical KPI at the top:** Success Rate, Error Count, and p95 Latency.
* [ ] **Color Coding:** Use Red/Yellow/Green thresholds clearly.
* [ ] **Clear Titles:** Avoid cryptic names; use "Payment API Success Rate" instead of "svc_py_200_count".

## 2. The Four Golden Signals (Google SRE Standard)
Every service dashboard must visualize these four metrics:
* [ ] **Latency:** Time it takes to service a request (Focus on p95 and p99).
* [ ] **Traffic:** Demand placed on the system (Requests per second).
* [ ] **Errors:** Rate of requests that fail (Explicitly, implicitly, or by policy).
* [ ] **Saturation:** How "full" your service is (CPU, Memory, Thread Pool).

## 3. Context & Correlation
* [ ] **Deployment Markers:** Overlays showing when a new version was shipped.
* [ ] **Comparison Overlays:** Current metrics vs. "Same time last week" to detect anomalies.
* [ ] **Log Correlation:** Direct links from metric spikes to Splunk/Datadog logs.

## 4. Hierarchy of Information
* [ ] **Level 1 (Executive):** Global health and SLO status.
* [ ] **Level 2 (Triage):** Per-service metrics and dependencies.
* [ ] **Level 3 (Debug):** Low-level infrastructure (CPU, Disk I/O, JVM metrics).

## 5. Maintenance & Hygiene
* [ ] **No Dead Panels:** Remove widgets that are consistently flat or "No Data".
* [ ] **Documentation Link:** A link to the "Incident Playbook" at the top of the dashboard.
* [ ] **Owner Tags:** Every dashboard must have a clear owning team.

---
*Reference: Inspired by the "Monitoring Distributed Systems" chapter of the Google SRE Book.*
