# 🚨 MedFlow: Enterprise Emergency Triage Operations Engine

> **Live Production Deployment:** [https://gleeful-beignet-e2c0ce.netlify.app](https://gleeful-beignet-e2c0ce.netlify.app)

MedFlow is a high-performance, real-time hospital triage simulation and emergency resource management engine built for the **Hack-a-Matics 2026** hackathon (**VECTOR** theme). It replaces traditional, inefficient first-come-first-served queues with a dynamic, mathematically bounded priority scheduling algorithm designed to maximize critical care throughput and completely eliminate patient starvation during high-stress clinical surges.

---

## ⚡ The Core Problem & Engineering Challenge

Traditional hospital emergency departments (EDs) suffer from severe queuing bottlenecks during mass-casualty events, accidents, or weekend surge conditions. Standard FIFO (First-In, First-Out) queues fail because they completely ignore clinical urgency, while naive priority queues lead directly to **patient starvation**—where lower-acuity patients wait indefinitely while continuous high-acuity arrivals bypass them.

**MedFlow solves this via algorithmic scheduling control:** balancing clinical severity against waiting duration using a deterministic quadratic aging function.

---

## 🧮 The Mathematics Behind MedFlow

Unlike static dashboard mockups, MedFlow's core simulation engine recomputes every simulated minute using rigorous priority and penalty metrics:

### 1. Dynamic Priority Score (with Quadratic Aging)
To ensure no patient is neglected indefinitely under sustained high-pressure conditions, the scheduling weight scales quadratically with wait time:
$$P(\text{patient}) = 8 \cdot \text{urgency}^2 + 1.5 \cdot \text{waitMinutes}$$
* **Result:** Even a lower-urgency patient's priority score grows robustly over time, guaranteeing they will eventually bubble to the top of the queue without getting starved out.

### 2. Weighted Wait-Time Penalty Matrix
System degradation and delay costs are continuously quantified across active queues:
$$\text{Penalty}(p) = \text{urgency} \times \text{waitMinutes}$$
$$\text{SystemPenalty} = \sum \text{Penalty}(p)$$

### 3. Triage Efficiency Ratio (TER)
Real-time tracking of clinical performance against golden-window medical targets:
$$\text{TER} = \left( \frac{\text{Stabilized Critical Cases}}{\text{Total Critical Influx}} \right) \times 100$$

---

## 🚀 Key Technical Features

* **Binary-Heap Priority Scheduling:** Efficient underlying data structure handling dynamic insertions and extractions under high-frequency event ticks.
* **Role-Based Access Control (RBAC):** Secure demonstration authentication layering distinct views for administrators, triage nurses, and attending physicians.
* **Real-Time Operations Audit Log:** Live event streaming tracking patient arrivals, ambulance offload delays, bed allocations, and critical interventions down to the second.
* **Dynamic Risk Monitoring:** Automated system-health diagnostics that trigger actionable recommendations when critical-case thresholds drop below safety margins.

---

## 💻 Tech Stack

* **Frontend & Engine:** Single-file architecture utilizing semantic HTML5, custom CSS Grid/Flexbox design systems, and optimized Vanilla JavaScript.
* **State Management:** Reactive simulation loop driving continuous queue re-indexing, memory-efficient DOM updates, and live metrics telemetry.
* **Deployment:** Continuous delivery pipeline hosted live on Netlify.

---

## 🛠️ Local Development & Quick Start

To run the MedFlow simulation engine locally on your machine:

1. Clone the repository:
   ```bash
   git clone [https://github.com/kratikasrivastavacs26-ops/hack-a-matics-2026.git](https://github.com/kratikasrivastavacs26-ops/hack-a-matics-2026.git)
