# 🛡️ SOC Alert Triage & Incident Management in ServiceNow

![Domain](https://img.shields.io/badge/Domain-SOC%20Alert%20Triage%20%26%20Incident%20Response-blue) ![SIEM](https://img.shields.io/badge/SIEM-Splunk%20Enterprise-orange) ![ITSM](https://img.shields.io/badge/ITSM-ServiceNow-green) ![Framework](https://img.shields.io/badge/Framework-MITRE%20ATT%26CK-brightgreen)

---

## 📌 Project Overview
This project documents an evidence-based **SOC Triage Workflow** simulating real-world security operation workflows. Alerts generated in **Splunk Enterprise** were correlated, analyzed, and managed through **ServiceNow** incident management.

The objective was to execute a defensible, evidence-based triage workflow—moving from initial alert review to final disposition, supported by verified log telemetry and structured ITSM ticket documentation.

---

## 📁 Repository Structure

* [**`README.md`**](./README.md) — Main project overview, triage methodology, and incident summary table
* [**`INC0010145.png`**](./assets/INC0010145.png) — Multiple Failed Logins ticket screenshot
 * [**`INC0010146.png`**](./assets/INC0010146.png) — Ransomware Mass Encryption ticket screenshot
* [**`INC0010147.png`**](./assets/INC0010147.png) — Malicious IP Outbound Connection ticket screenshot
* [**`INC0010148.png`**](./assets/INC0010148.png) — Unusual Login Time ticket screenshot
 * [**`INC0010149.png`**](./assets/INC0010149.png) — Encoded PowerShell Execution ticket screenshot
---

## 🔄 Triage Methodology

Each incident followed a structured 7-step triage lifecycle:

1. **Understand the Alert:** Review alert metadata, telemetry source, host asset, and user context.
2. **Form a Hypothesis:** Determine whether the activity represents legitimate administrative/business actions, anomalous behavior, or active adversary behavior.
3. **Investigate:** Gather supporting log evidence (authentication events, process execution, network connections, cross-alert correlation).
4. **Reach a Verdict:** Classify the alert (True Positive, Benign True Positive, False Positive, or Insufficient Data).
5. **Assign Severity:** Grade risk level based on asset criticality, potential impact, and confirmed post-exploitation activity.
6. **Close or Escalate:** Close benign alerts with clear rationale, or escalate severe alerts for immediate containment.
7. **Document:** Record full technical findings, timeline, and rationale inside ServiceNow
---

## 📊 Alert Summary Table

| Incident ID | Alert Description | Host / User | Verdict | Severity | Disposition | Evidence / Screenshot |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **INC0010145** | Multiple Failed Logins (Brute Force) | `WKSTN-014` / `jsmith` | True Positive | **Critical** *(Escalated)* | Escalated | [`INC0010145.png`](./INC0010145.png) |
| **INC0010146** | Ransomware Mass Encryption | `FIN-SRV-02` / `rpatel` | True Positive | **Critical** | Escalated | [`INC0010146.png`](./INC0010146.png) |
| **INC0010147** | Outbound Connection to Malicious IP | `WKSTN-027` / `agupta` | True Positive | **High** | Escalated | [`INC0010147.png`](./INC0010147.png) |
| **INC0010148** | Unusual Login Time (02:14 AM) | `LAPTOP-009` / `mlee` | Benign True Positive | **Low** | Closed | [`INC0010148.png`](./INC0010148.png) |
| **INC0010149** | Suspicious Encoded PowerShell | `WKSTN-014` / `jsmith` | True Positive | **Critical** | Escalated | [`INC0010149.png`](./INC0010149.png) |
---

## 🔗 Attack Chain Correlation Note

* **INC0010145 & INC0010149 Correlation:** `INC0010145` (12 failed logins followed by successful authentication) and `INC0010149` (encoded PowerShell execution) occurred on the same host (`WKSTN-014`) and user (`jsmith`). 
* Correlating these alerts revealed a **multi-stage attack chain** (Initial Access via Brute Force ➔ Execution via Malicious Script Download), raising the severity of the initial access alert to **Critical**.

---

## 👤 Author

**Rida**
* **GitHub:** [@ridaabbas000000](https://github.com/ridaabbas000000)
