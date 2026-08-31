# TrafficMind V5 — Sovereign Multi-Intersection Adaptive Corridor Engine

> **Project Status:** Simulation-Validated Research & Engineering Prototype  
> **Environment:** Eclipse SUMO v1.20+ Microscopic Simulation (`setSpeedMode(31)`)  
> **Core Hypothesis:** Closed-Loop Priority Orchestration without gridlock collapse.

---

## 📌 Key Architectural Pillars
1. **Predict:** Operational Route-Distance ETA & Predictive Pre-Flush (`500m` Emergency Zone).
2. **Protect:** Independent Safety Governor enforcing `3s Yellow + 2s All-Red` and zero conflicting green states (`NS_green ∧ EW_green = False`).
3. **Recover:** Decoupled Intersection Lifecycle with multi-factor Debt Recovery scoring (`Queue + Inflow + Wait`).

---

## 📊 Empirical Validation Summary

* **A/B Counterfactual Benchmark (20 Scenarios):**
  * Emergency Travel Time: `111.55s → 76.15s` (**-31.73%** reduction).
  * EV Stop Waiting Time: `52.35s → 15.00s` (**-71.35%** reduction).
  * Superior Performance: **19 / 20 scenarios (95%)**.
* **120 Deterministic Stress-Test Scenarios:**
  * Mean True Delay (119 completed runs): **42.47 s** (50.44 s including single boundary timeout).
  * Runtime Safety Violations: **0 violations**.
* **2,000 Stochastic Monte Carlo Simulation Runs:**
  * Completed Runs: **1,685 / 2,000** (Mean True Delay: **28.32 s**).
  * Boundary Timeouts: **315 / 2,000** (Counted as strict engineering failures).
  * Strict Acceptance Pass (`Wait ≤ 4s ∧ Delay ≤ 15s`): **469 / 2,000 (23.45%)**.
  * Formal Signal Invariant Violations: **0 across all 2,000 runs**.

---

## 🚀 How to Reproduce
```bash
# 1. Run GUI Demo
python trafficmind_v5_unified.py --gui

# 2. Run 120-Scenario Deterministic Stress-Test
python trafficmind_v5_unified.py --benchmark120

# 3. Run A/B Counterfactual Benchmark (20 runs)
python trafficmind_v5_unified.py --ab_benchmark --scenarios 20

# 4. Run Stochastic Monte Carlo Suite (2,000 runs)
python trafficmind_v5_unified.py --montecarlo --runs 2000
