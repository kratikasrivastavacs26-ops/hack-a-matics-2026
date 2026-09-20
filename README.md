# 🚨 MedFlow: Enterprise Emergency Triage Operations Engine

> **Live Production Deployment:** [https://harmonious-elf-4ce3a1.netlify.app](https://harmonious-elf-4ce3a1.netlify.app)[cite: 9]

MedFlow is a high-performance, real-time hospital triage simulation and emergency resource management engine. Built for high-stress clinical environments, it replaces static first-come-first-served queues with a dynamic, mathematically bounded priority scheduling algorithm to optimize critical care throughput and prevent patient starvation under severe capacity crunches.

---

## ⚡ The Core Problem & Engineering Challenge

Traditional hospital emergency departments (EDs) suffer from severe queuing bottlenecks during mass-casualty events or surge conditions. Standard FIFO (First-In, First-Out) queues fail because they ignore clinical urgency, while naive priority queues lead to **patient starvation**—where lower-urgency patients wait indefinitely while continuous high-urgency arrivals bypass them.

**MedFlow solves this via algorithmic scheduling control:** balancing clinical severity against waiting duration using a deterministic aging function.

---

## 🧮 The Mathematics Behind MedFlow

Unlike static dashboard mockups, MedFlow's engine recomputes every simulated minute using rigorous priority metrics:

### 1. Dynamic Priority Score (with Quadratic Aging)
To ensure no patient is neglected indefinitely under sustained Level-5 pressure, the scheduling weight scales quadratically with wait time:
$$P(\text{patient}) = 8 \cdot \text{urgency}^2 + 1.5 \cdot \text{waitMinutes}$$
* *Result:* Even a lower-urgency patient's priority score grows robustly over time, guaranteeing they will eventually bubble to the top of the queue.

### 2. Weighted Wait-Time Penalty Matrix
System degradation is continuously quantified across active queues:
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
* **Deployment:** Continuous delivery pipeline hosted on Netlify[cite: 9].

---

## 🛠️ Local Development & Quick Start

To run the MedFlow simulation engine locally on your machine:

1. Clone the repository:
   ```bash
   git clone [https://github.com/kratikasrivastavacs26-ops/hack-a-matics-2026.git](https://github.com/kratikasrivastavacs26-ops/hack-a-matics-2026.git)
