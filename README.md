# Multi-Window Quantum Compilation Tests on Amazon Braket (108-Qubit Rigetti)

*Explore the portfolio: [Prometheus Quantum Overview](https://github.com/PrometheusDynamicsCanada/prometheus-quantum-overview)*

**We tested Prometheus on physical quantum processors accessed through Amazon Braket, repeating comparisons across different hardware conditions.**

Modular superconducting processors such as Rigetti's `Cepheus-1-108Q` link smaller qubit tiles across inter-module couplers whose error rates shift over time and after recalibration.

Repeating **18 application-style workloads across three calibration windows** on Amazon Braket (initial run, `9.3` hours later, and after processor recalibration), live-calibration Prometheus outperformed Qiskit SABRE on **`16 of 18` workloads (`+3.91%` mean output overlap)** and Quantinuum TKET on **`15 of 18` (`+9.03%`)**, widening its lead over SABRE to **`+6.61%`** after recalibration. Supporting suites in Tables 1A-1C report unseen equal-CPU-budget tasks, QAOA optimization trajectories, and diagnostic Clifford mirrors, including regimes where SABRE or TKET led slightly.

**[Detailed results](DETAILED_TECHNICAL_REPORT.md) · [Verify the evidence](#verify-the-evidence) · [Discuss a pilot](#discuss-a-pilot)**

![Three-Calibration-Window Replication on 108-Qubit Rigetti Hardware](assets/fig1_rigetti_3window_replication.png)
*Opening summary (`Pillar 1` on `108Q` `Rigetti Cepheus-1-108Q` via AWS Braket): Measured output-distribution overlap across `18` workloads (`4Q-17Q`, `216` circuits) before drift (`Window 1`), after `+9.3h` drift (`Window 2`), and after device recalibration (`Window 3`, `+6.61%` vs. SABRE O3).*

---

## 1. Principal Comparative Benchmark Tables (Separated by Workload & Metric Type)

*Campaign Scope:* `10` AWS Braket `ProgramSet` tasks, `450` verbatim physical circuits, and `460,800` physical shots across `19.1` hours and three calibration windows on 108-qubit `Rigetti Cepheus-1-108Q`.

> [!NOTE]
> **Metric Conventions:** Tables 1A-1C use descriptive columns matched to each experiment rather than overloading a single schema. Classical Distribution Overlap is $F_B = \sum_x \sqrt{P_{\text{ideal}}(x) P_{\text{meas}}(x)}$ (labeled `"State Fidelity"` in Studio UIs); Squared Hellinger Fidelity is $F_H = F_B^2$; Total Variation Distance is $\text{TVD} = \frac{1}{2}\sum_x |P_{\text{ideal}}(x) - P_{\text{meas}}(x)|$. Direction indicators `(↑)` and `(↓)` denote optimality; **bold** marks cohort winners. All `10` AWS Braket Task ARNs (`arn:aws:braket:us-west-1:893688540163:quantum-task/2a6b5957...` through `8e797e69...`) are indexed in [`DETAILED_TECHNICAL_REPORT.md`](DETAILED_TECHNICAL_REPORT.md) and [`data/ALL_450_RIGETTI_CIRCUITS_RESULTS.csv`](data/ALL_450_RIGETTI_CIRCUITS_RESULTS.csv).

### Table 1A: Core Multi-Window Sweep (`Pillar 1`, `N = 18` Workloads, `4Q-17Q`) & Unseen Equal-CPU-Budget Suite (`Pillar 4`, `N = 12`, `6Q-12Q`)

| Cohort & AWS Braket Scope | Execution Strategy | Composite Primary `*(mean)*` `(↑)` | Overlap $F_B$ `*(mean / median)*` `(↑)` | Hellinger $F_H$ `*(mean)*` `(↑)` | $\text{HOP}$ `(↑)` \| $\text{TVD}$ `(↓)` `*(mean)*` | Entropy $H$ `(bits)` `*(mean)*` | Native `CZ` \| Depth `*(mean)*` `(↓)` | Pairwise Wins & Holm-Adjusted $p$-Values |
| :--- | :--- | :---: | :---: | :---: | :---: | :---: | :---: | :--- |
| **Pillar 1 Pooled (`W1+W2+W3`)**<br>`3` Tasks (`2a6b...`, `9d4d...`, `8e79...`), `216` Circs, `221,184` Shots | **Prom. Fresh (Live Cal.)**<br>Prom. Control (Frozen W1)<br>Qiskit SABRE O3<br>Quantinuum TKET O2 | **0.5197**<br>0.5166<br>0.5011<br>0.4801 | **0.5232 / 0.6125**<br>0.5192 / 0.5971<br>0.5035 / 0.5841<br>0.4799 / 0.4941 | **0.3723**<br>0.3691<br>0.3519<br>0.3243 | **0.5770 \| 0.6754**<br>0.5686 \| 0.6775<br>0.5586 \| 0.6916<br>0.5309 \| 0.7196 | 7.8623<br>7.8703<br>7.8846<br>7.9108 | 91.35 \| 148.56<br>**90.63 \| 148.22**<br>105.44 \| 194.35<br>120.44 \| 234.22 | **+3.91% $F_B$ vs. SABRE** (`16W-0T-2L`, `p_Holm = 0.0112`, `-13.4%` CZ)<br>**+9.03% $F_B$ vs. TKET** (`15W-1T-2L`, `p_Holm = 0.000641`, `-24.2%` CZ) |
| **Pillar 1 - Window 3 (`Post-Recal.`)**<br>Task `8e797e69...`, `72` Circs, `73,728` Shots | **Prom. Fresh (Live W3)**<br>Prom. Control (Frozen W1)<br>Qiskit SABRE O3<br>Quantinuum TKET O2 | **0.5383**<br>0.5223<br>0.5045<br>0.4797 | **0.5398 / 0.6365**<br>0.5251 / 0.6207<br>0.5063 / 0.5737<br>0.4808 / 0.4867 | **0.3880**<br>0.3765<br>0.3519<br>0.3244 | **0.5833 \| 0.6634**<br>0.5734 \| 0.6748<br>0.5578 \| 0.6901<br>0.5291 \| 0.7205 | **7.8279**<br>7.8867<br>7.8872<br>7.9122 | **91.11 \| 147.72**<br>91.78 \| 148.78<br>105.44 \| 194.61<br>120.44 \| 234.22 | **+6.61% $F_B$ vs. SABRE** (`11W-0T-7L`, `p_Holm = 0.0379`)<br>**+2.79% $F_B$ vs. Frozen W1** · **+12.27% vs. TKET** (`p_Holm = 0.000938`) |
| **Pillar 4 (`Unseen Equal-CPU`)**<br>Tasks `cc7f...` to `8b34...` (`5` Tasks), `96` Circs, `98,304` Shots | Prom. (Equal CPU)<br>SABRE (Default 1-Seed)<br>**SABRE (Equal CPU)**<br>TKET (Equal CPU) | 0.6150<br>0.5913<br>**0.6174**<br>0.5878 | **0.6344 / 0.6508**<br>0.6090 / 0.6382<br>0.6294 / 0.6329<br>0.6052 / 0.6427 | 0.4448<br>0.4156<br>**0.4465**<br>0.4100 | **0.5982** \| 0.6044<br>0.5595 \| 0.6323<br>0.5948 \| **0.5979**<br>0.5732 \| 0.6316 | 7.9745<br>8.0149<br>**7.9596**<br>8.0042 | 69.83 \| 153.08<br>77.42 \| 183.08<br>**65.17 \| 146.58**<br>71.58 \| 170.08 | **+4.01% Primary (`+4.17%` $F_B$) vs. Default SABRE** (`p_Holm = 0.0337`)<br>**+0.79% $F_B$ (`8W-4L`) vs. Equal-CPU SABRE** (`5W-7L` on composite primary) |

### Table 1B: QAOA MaxCut Optimization Trajectories (`Pillar 3`, Task `c9e0645b...`, `8` Widths `4Q-17Q` x `3` Stages = `72` Circuits, `73,728` Shots)

| Compiler Strategy | Approximation Ratio Across All 24 Stages `*(mean)*` `(↑)` | Final-Stage Approx. Ratio `*(mean)*` `(↑)` | High-Quality Tail Prob. $P(\text{Cut} \ge 0.90\,C_{\max})$ `*(mean / median)*` `(↑)` | Absolute Ratio Error $\|r - r_{\text{ideal}}\|$ `*(mean)*` `(↓)` | Native `CZ` Gates \| Compiled Depth `*(mean)*` `(↓)` | Outcome Summary |
| :--- | :---: | :---: | :---: | :---: | :---: | :--- |
| **Prometheus (Live Cal.)** | 0.5859 | 0.5970 | **0.0680** / 0.0093 | 0.1399 | **102.71 \| 234.75** | **Highest mean top-decile solution probability (`+3.66%` vs. SABRE, `+4.29%` vs. TKET)** & shallowest circuits (`-5.56%` depth vs. SABRE, `-29.45%` vs. TKET) |
| **Qiskit SABRE O3** | 0.5887 | **0.6028** | 0.0656 / 0.0103 | **0.1385** | 106.12 \| 248.58 | Highest final-stage mean approximation ratio (`+0.97%` above Prometheus) |
| **Quantinuum TKET O2** | **0.5971** | 0.5991 | 0.0652 / **0.0142** | 0.1508 | 128.75 \| 332.75 | Highest 3-stage pooled mean ratio despite `+41.7%` deeper circuits |

### Table 1C: Diagnostic Clifford Mirror Scaling (`Pillar 2`, Task `eec556a3...`, `18` Mirrors `4Q-36Q` + `12` SPAM Controls = `66` Circuits, `67,584` Shots)

| Compiler Strategy | Zero-Centered Bit Polarization `*(mean)*` `(↑)` | Per-Bit Return Accuracy `*(mean / median)*` `(↑)` | Exact Full-Bitstring Survival `*(mean)*` `(↑)` | Mean Hamming Distance `(bits)` `*(mean)*` `(↓)` | Native `CZ` Gates \| Compiled Depth `*(mean)*` `(↓)` | Outcome Summary |
| :--- | :---: | :---: | :---: | :---: | :---: | :--- |
| **Prometheus (Live Cal.)** | 0.2277 | 0.6139 / 0.6078 | 0.0904 | 6.0367 | **114.67 \| 111.83** | **+16.91% bit accuracy vs. TKET** (`16W-2L`, `p_Holm = 0.000366`, `-37.0%` CZ); `-1.31%` vs. SABRE (`6W-12L`) |
| **Qiskit SABRE O3** | **0.2442** | **0.6221 / 0.6151** | **0.0907** | **6.0116** | 120.67 \| 119.44 | **Led 4Q-36Q Rigetti mirror suite** despite `5.2%` more CZ gates than Prometheus |
| **Quantinuum TKET O2** | 0.0501 | 0.5251 / 0.5250 | 0.0192 | 7.0173 | 182.00 \| 201.33 | Severe inter-tile SWAP overhead (`+58.7%` more CZ gates than Prometheus) |

---

## Verify the Evidence

**Verification Kind:** Direct **raw-measurement histogram + compiled OpenQASM reconstruction** across all `450` physical circuits (`10` AWS Braket Task JSONs in `data/jobs/`, zero cloud credentials required; note that local commitment wrapper timestamps precede submission on Tasks 3-10 while Tasks 1-2 reflect runner-resume wrapper serialization over unmodified pre-submission caches, as documented in [`PUBLIC_DISCLOSURE.md`](PUBLIC_DISCLOSURE.md)):

```bash
python scripts/verify_braket_campaign.py
```

- **Key files:** [`DETAILED_TECHNICAL_REPORT.md`](DETAILED_TECHNICAL_REPORT.md) · [`data/ALL_450_RIGETTI_CIRCUITS_RESULTS.csv`](data/ALL_450_RIGETTI_CIRCUITS_RESULTS.csv) · [`PUBLIC_DISCLOSURE.md`](PUBLIC_DISCLOSURE.md) · [`REPOSITORY_SHA256SUMS.txt`](REPOSITORY_SHA256SUMS.txt)

---

## Discuss a Pilot

**Bring a representative workload and an acceptance criterion. We can compare Prometheus with your existing execution approach and measure quality, acceptance rate and charged hardware resources.**

- **Contact:** [william@prometheusdynamics.ca](mailto:william@prometheusdynamics.ca) | [prometheusdynamics.ca](https://prometheusdynamics.ca)
