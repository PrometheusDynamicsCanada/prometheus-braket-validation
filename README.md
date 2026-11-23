# Multi-Window Amazon Braket Validation (`108Q` Rigetti & `256`-Atom QuEra)

*Portfolio Hub: [Prometheus Quantum Overview](https://github.com/PrometheusDynamicsCanada/prometheus-quantum-overview) · [Complexity Atlas (`Cepheus-1` Star)](https://github.com/PrometheusDynamicsCanada/prometheus-circuit-complexity-atlas) · [Detailed Report](DETAILED_TECHNICAL_REPORT.md)*

## Introduction

- **The question:** Do Prometheus's execution gains hold across repeated calibration windows on Amazon Braket - both on a multi-chip superconducting gate processor and on a neutral-atom analog device?
- **The test:** Across `22` AWS Braket tasks (`462` runs, `463,800` physical shots, `$232.44` settled), we ran two distinct hardware studies: (1) `10` gate-model `ProgramSet` tasks (`450` circuits, `460,800` shots) on `108`-qubit `Rigetti Cepheus-1-108Q` across initial, `+9.3h` drift, and post-recalibration windows vs. Qiskit SABRE O3 and Quantinuum TKET O2; and (2) `12` Analog Hamiltonian Simulation (`AHS`) tasks (`3,000` Rb-87 shots across `2` separated windows) on **`11-13`-atom instances** arranged on the **`256`-atom `QuEra Aquila`** neutral-atom device vs. AWS's documented schedule.
- **The finding:** On `Rigetti Cepheus-1`, live-calibration Prometheus beat SABRE O3 on **`16/18` workloads (`+3.91%` 3-window output-distribution agreement, rising to `+6.61%` after recalibration)** and TKET on **`15/18` (`+9.03%`)**. On `256`-atom `QuEra Aquila` (`11-13`-atom instances), Prometheus outperformed AWS's baseline in both execution windows (`881` vs. `852` exact optimal answers), replicated **`60.0%` vs. `50.8%` (`+18.11%` yield, `-15.35%` cost/optimum, `p = 0.0042`)** on the hardest `12`-atom graph, and cut suboptimal maximal-independent-set outcomes by **`-40.34%`** (`p = 1.1e-5`).
- **The significance:** Demonstrates repeatable gains across multi-chip superconducting calibration shifts and global-drive neutral-atom optimization.
- **The boundary:** On Rigetti `4Q-36Q` Clifford mirrors SABRE led slightly (`0.6221` vs. `0.6139` bit accuracy), and on easier `11`-atom and `13`-atom Aquila graphs exact optimum rates were statistically indistinguishable (`p >= 0.60`, though suboptimal MIS fell `-38.6%` to `-40.0%`).
- **The evidence:** Opening 3-window Rigetti chart and two-architecture summary table below, with full Pillar 1-4 and Aquila tables and raw shot verification underneath.

![Three-Calibration-Window Replication on 108-Qubit Rigetti Hardware](assets/fig1_rigetti_3window_replication.png)
*Opening summary: Output-distribution agreement across 18 workloads (`4Q-17Q`, `216` circuits) on 108Q Rigetti Cepheus-1 across 3 calibration windows.*

---

## Executive Summary (`22` AWS Braket Tasks: `10` Rigetti Gate-Model + `12` `256`-Atom QuEra Analog, `463,800` Shots)

*Hardware Task ARNs:* Rigetti `2a6b5957..`..`8b348409..` ([`ALL_450_RIGETTI_CIRCUITS_RESULTS.csv`](data/ALL_450_RIGETTI_CIRCUITS_RESULTS.csv)); QuEra `f95ab6..`..`88a26a..` ([`ALL_12_QUERA_AQUILA_TASKS_RESULTS.csv`](data/ALL_12_QUERA_AQUILA_TASKS_RESULTS.csv)).

| Architecture, Cohort & Strategy | Primary / Optimum `(↑)` | Output Agreement $F_B$ / $P_{\text{valid}}$ `(↑)` | $F_H$ / DF $P_{\text{opt}}$ `(↑)` | `HOP` / `TVD` `*(mean)*` | `CZ` / Depth `(↓)` | Outcome & Statistical Test |
| :--- | :---: | :---: | :---: | :---: | :---: | :--- |
| **Rigetti 3-Window (`216` circs): SABRE O3** | `0.5011` | `0.5035` (`0.5841` med) | `0.3519` | `0.5586` / `0.6916` | `105.4` / `194.4` | `2 / 18` vs. Prom |
| **Rigetti 3-Window (`216` circs): TKET O2** | `0.4801` | `0.4799` (`0.4941` med) | `0.3243` | `0.5309` / `0.7196` | `120.4` / `234.2` | `2 / 18` vs. Prom |
| **Rigetti 3-Window (`216` circs): Prom Fresh** | **`0.5197`** | **`0.5232` (`0.6125` med)** | **`0.3723`** | **`0.5770` / `0.6754`** | **`91.4` / `148.6`** | **`+3.91%` vs. S (`p=0.011`) · `+6.61%` W3** |
| **QuEra `11-13` Atoms (`1,500` shots): AWS Base** | `852 / 1500` (`56.80%`) | `92.13%` valid IS | `58.38%` DF opt | `176` subopt MIS | `3.0 us` (`0` local) | `$16.80` (`1.97c / opt`) |
| **QuEra `11-13` Atoms (`1,500` shots): Prom** | **`881 / 1500` (`58.73%`)** | **`92.93%` valid IS** | **`60.48%` DF opt** | **`105` subopt (`-40.3%`)** | `3.0 us` (`0` local) | **`$16.80` (`1.91c / opt`; `12A` `-15.35%`, `p=0.0042`)** |

*Metric Key:* Rigetti output-distribution agreement is $F_B = \sum_x \sqrt{P_{\text{ideal}}(x)P_{\text{meas}}(x)}$ ($F_H = F_B^2$; Shannon entropy `7.86` Prom vs. `7.88` S / `7.91` T). QuEra runs tested `11-13`-atom registers on the `256`-atom `Aquila` device (`3.0 us` duration, `15.7 Mrad/s` peak drive, `0` local detuning terms).

---

## Inspect the Evidence & Reproduce Supported Checks Offline

- **Command:** `python scripts/verify_braket_campaign.py`
- **Dependencies & measured runtime:** Python 3 + `numpy` + `scipy` (`0` cloud credentials, **`~1.34 s`** measured runtime; reconstructs all `450` Rigetti circuits and `3,000` raw `pre`/`post_sequence` Rb-87 neutral-atom shots).
- **Start a pilot:** [william@prometheusdynamics.ca](mailto:william@prometheusdynamics.ca) | [prometheusdynamics.ca](https://prometheusdynamics.ca)

---

## Full Rigetti Pillars 1-4 & QuEra Per-Topology Tables

<details>
<summary><strong>1. Complete Rigetti Pillars 1-4 (Window 3, Equal-CPU, QAOA, Mirrors) & QuEra 11-13 Atom Tables - Click to expand</strong></summary>

- **Window 3 Post-Recalibration (`8e797e69..`, `72` circs):** Prom Fresh **`0.5398`** $F_B$ (`0.3880` $F_H$, `91.1 CZ / 147.7 depth`) vs. Frozen W1 `0.5251`, SABRE `0.5063` (**`+6.61%`**, `p_Holm = 0.0379`), and TKET `0.4808` (**`+12.27%`**, `p_Holm = 0.00094`).
- **Pillar 4 Unseen Equal-CPU (`5` tasks `cc7f..8b34`, `96` circs):** Prom **`0.6344`** $F_B$ (`8W-4L`) vs. Default SABRE `0.6090` (`+4.17%`), Equal-CPU SABRE `0.6294`, and Equal-CPU TKET `0.6052`.
- **Pillar 3 QAOA Trajectories (`c9e0645b..`, `72` circs):** Prom highest top-decile cut probability (**`0.0680`** vs. `0.0656` S / `0.0652` T); SABRE led final-stage mean ratio (`0.6028` vs. `0.5970`).
- **Pillar 2 `4Q-36Q` Clifford Mirrors (`eec556a3..`, `66` circs):** Prom beat TKET `+16.91%` bit accuracy (`0.6139` vs. `0.5251`); SABRE led Prom slightly (`0.6221` vs. `0.6139`).

| Topology (`500` Shots/Arm, `$5.60`/Arm on `256`-Atom Aquila) | Schedule | Valid IS `(↑)` | Exact Opt (`All` / `DF`) `(↑)` | Subopt MIS `(↓)` | `Cents / Opt` `(↓)` & Fisher `p` |
| :--- | :--- | :---: | :---: | :---: | :--- |
| **`11`-Atom (`11A`, `HP = 3.00`)** | AWS Base / **Prom** | **`95.0%`** / `93.6%` | **`62.2%`** / `60.4%` (`63.3%` / `62.2%` DF) | `44` / **`27` (`-38.6%`)** | **`1.80c`** / `1.85c` (`p = 0.60`; subopt `p = 0.048`) |
| **`12`-Atom (`12A`, `HP = 4.80`, Hardest)** | AWS Base / **Prom** | `89.4%` / **`92.4%`** | `50.8%` / **`60.0%`** (`51.6%` / **`61.2%`** DF) | `82` / **`48` (`-41.5%`)** | `2.21c` / **`1.87c` (`-15.35%`, `p = 0.0042`)** |
| **`13`-Atom (`13A`, `HP = 3.33`)** | AWS Base / **Prom** | `92.0%` / **`92.8%`** | **`57.4%`** / `55.8%` (`60.2%` / `58.1%` DF) | `50` / **`30` (`-40.0%`)** | **`1.95c`** / `2.01c` (`p = 0.66`; subopt `p = 0.026`) |

</details>

<details>
<summary><strong>2. QuEra Aquila Two-Window Neutral-Atom Replication Figure - Click to expand</strong></summary>

![Two-Window Neutral-Atom Replication on 256-Atom QuEra Aquila](assets/fig5_aquila_2window_neutral_atom_replication.png)

</details>
