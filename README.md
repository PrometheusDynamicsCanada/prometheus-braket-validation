# Multi-Window Quantum Execution Validation on Amazon Braket (108-Qubit Rigetti & 256-Atom QuEra Aquila)

*Explore the portfolio: [Prometheus Quantum Overview](https://github.com/PrometheusDynamicsCanada/prometheus-quantum-overview)*

**We tested Prometheus across both superconducting gate-model and neutral-atom analog quantum processors accessed through Amazon Braket, repeating comparisons across separated execution windows.**

- **Superconducting Gate-Model (`108Q` `Rigetti Cepheus-1-108Q`, `10` Tasks, `450` Circuits, `460,800` Shots):** Repeating **18 application-style workloads across three calibration windows** (initial run, `+9.3h` drift, and post-recalibration), live-calibration Prometheus outperformed Qiskit SABRE on **`16 of 18` workloads (`+3.91%` mean output overlap)** and Quantinuum TKET on **`15 of 18` (`+9.03%`)**, widening its lead over SABRE to **`+6.61%`** after recalibration. Supporting suites in Tables 1A-1C report unseen equal-CPU-budget tasks, QAOA optimization trajectories, and diagnostic Clifford mirrors, including regimes where SABRE or TKET led slightly.
- **Neutral-Atom Analog Hamiltonian Simulation (`256`-Atom `QuEra Aquila`, `12` Tasks, `3,000` Rb-87 Shots Across `2` Separated Batches: `+84.9h` Task Submission Span [`Nov 16` vs. `Nov 20`], `+6.2h` Physical QPU Execution Gap on `2026-11-20`):** Round 1 (`6` tasks) was submitted `2026-11-16 21:35 UTC` between scheduled neutral-atom operating windows and physically executed `2026-11-20 04:15-04:28 UTC`; Round 2 (`6` tasks) was submitted `2026-11-20 10:29 UTC` (`+84.9h` later) and physically executed `2026-11-20 10:32-10:43 UTC` (`+6.2h` physical QPU separation). Across `1,500` billed shots and `USD 16.80` per arm (`0` experimental `rydbergLocal` terms, identical `AtomArrangement` registers, `3.0 us` duration, and `15.7 Mrad/s` peak drive), Prometheus outperformed AWS's documented baseline in **both execution windows (`445` vs. `421` in Window 1; `436` vs. `431` in Window 2 = `881` vs. `852` exact optimal answers, `+3.40%` pooled yield, `-3.29%` pooled cost/optimum)**, replicated **`60.00%` (`150/250`) in both windows** on the hardest `12A` topology (`HP = 4.80`: **`300/500` vs. `254/500`, `+18.11%` yield, `-15.35%` cost/optimum, Fisher `p = 0.0042`**), and recorded **`40.34%` fewer suboptimal maximal-independent-set outcomes across `6 of 6` paired tasks (`105` vs. `176`, `p = 1.1e-5`)**.

**[Detailed results](DETAILED_TECHNICAL_REPORT.md) · [Verify the evidence](#verify-the-evidence) · [Discuss a pilot](#discuss-a-pilot)**

![Three-Calibration-Window Replication on 108-Qubit Rigetti Hardware](assets/fig1_rigetti_3window_replication.png)
*Opening summary (`Part I` on `108Q` `Rigetti Cepheus-1-108Q` via AWS Braket): Measured output-distribution overlap across `18` workloads (`4Q-17Q`, `216` circuits) before drift (`Window 1`), after `+9.3h` drift (`Window 2`), and after device recalibration (`Window 3`, `+6.61%` vs. SABRE O3).*

---

## 1. Principal Comparative Benchmark Tables (Separated by Architecture, Workload & Metric Type)

*Combined Repository Scope:* **`22` AWS Braket Tasks** (`10` `ProgramSet` tasks on `108Q` `Rigetti Cepheus-1-108Q` [`450` circuits, `460,800` shots, `USD 198.8400`] + `12` Analog Hamiltonian Simulation tasks on `256`-atom `QuEra Aquila` [`12` global schedules, `3,000` Rb-87 shots, `USD 33.6000`]) = **`462` physical executions and `463,800` physical measurement shots (`USD 232.4400` settled)**.

> [!NOTE]
> **Metric Conventions:** Tables 1A-1D use descriptive columns matched to each architecture and experiment rather than overloading a single schema. Classical Distribution Overlap is $F_B = \sum_x \sqrt{P_{\text{ideal}}(x) P_{\text{meas}}(x)}$ (labeled `"State Fidelity"` in Studio UIs); Squared Hellinger Fidelity is $F_H = F_B^2$; Total Variation Distance is $\text{TVD} = \frac{1}{2}\sum_x |P_{\text{ideal}}(x) - P_{\text{meas}}(x)|$. Direction indicators `(↑)` and `(↓)` denote optimality; **bold** marks cohort winners. All `22` AWS Braket Task ARNs are indexed in [`DETAILED_TECHNICAL_REPORT.md`](DETAILED_TECHNICAL_REPORT.md), [`data/ALL_450_RIGETTI_CIRCUITS_RESULTS.csv`](data/ALL_450_RIGETTI_CIRCUITS_RESULTS.csv), and [`data/ALL_12_QUERA_AQUILA_TASKS_RESULTS.csv`](data/ALL_12_QUERA_AQUILA_TASKS_RESULTS.csv).

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

### Table 1D: Two-Window Neutral-Atom Analog Hamiltonian Simulation (`256`-Atom `QuEra Aquila`, `N = 12` AWS Braket Tasks, `3,000` Physical Rb-87 Shots; `+84.9h` Submit Span / `+6.2h` QPU Execution Gap, `USD 33.6000`)

*Scope, Timestamps & Matched Controls:* `3` development-selected King's-Graph Unit-Disk Graph `MIS` topologies (`11A`, `12A`, `13A`; unique `D_alpha = 1` optimum) $\times$ `2` matched-duration (`3.0 us`, `15.70 Mrad/s` peak Rabi drive, `0` `rydbergLocal` terms, identical `AtomArrangement` coordinates) global `DrivingField` schedules $\times$ `2` interleaved batches (`250` shots/task = `500` shots/arm per instance; `1,500` shots and `USD 16.80` per arm total). **Chronology (`Created at` vs. `Ended at`):** Round 1 tasks were submitted `2026-11-16 21:35 UTC` (while Aquila queued between scheduled operating windows) and physically executed `2026-11-20 04:15-04:28 UTC`; Round 2 tasks were submitted `2026-11-20 10:29 UTC` (`+84.9h` submission separation) and physically executed `2026-11-20 10:32-10:43 UTC` (`+6.2h` physical QPU execution gap).

| Instance / Cohort (`500` Shots/Arm per Instance; `1,500` Shots/Arm Total) | Global Schedule (`T = 3.0 us`) | Valid IS Rate $P_{\text{valid}}$ `(↑)` *(All / Defect-Free)* | Exact Optimum $P_{\text{opt}}$ `(↑)` *(All Billed Shots)* | Exact Optimum $P_{\text{opt}}$ `(↑)` *(Defect-Free Subset)* | Unrepaired Quality $r_{\text{MIS}}$ `(↑)` `*(mean)*` | Suboptimal MIS Outcomes `(↓)` *(All / DF)* | Blockade Viol. \| Pre-Seq Vacancies `(↓)` | Billed `USD / Opt` `(↓)` (`% Delta`, Two-Sided Fisher `p`) |
| :--- | :--- | :---: | :---: | :---: | :---: | :---: | :---: | :--- |
| **`P1_EbadiHard_11A_s7045`** (`11A`, `MIS = 5`, `HP = 3.00`)<br>Tasks `f95ab6...`, `b0aa91...`, `095425...`, `c1b166...` | AWS Documented Baseline<br>**Prometheus Schedule** | **`95.00%` / `94.67%`**<br>`93.60%` / `93.70%` | **`62.20%` (`311/500`)**<br>`60.40%` (`302/500`) | **`63.33%` (`297/469`)**<br>`62.18%` (`296/476`) | **`0.8732`**<br>`0.8564` | `8.80%` (`44`) / `8.10%`<br>**`5.40%` (`27`) / `4.20%`** | **`25`** \| `31`<br>`32` \| **`24`** | **`USD 0.01801`**<br>`USD 0.01854` (`+2.98%`, `p = 0.6035`; subopt. MIS **-38.6%**, `p = 0.0482`) |
| **`P2_EbadiHard_12A_s8024`** (`12A`, `MIS = 5`, `HP = 4.80`)<br>Tasks `7cba59...`, `c2d84a...`, `ce66ea...`, `6d0844...` | AWS Documented Baseline<br>**Prometheus Schedule** | `89.40%` / `89.46%`<br>**`92.40%` / `92.36%`** | `50.80%` (`254/500`)<br>**`60.00%` (`300/500`)** | `51.61%` (`240/465`)<br>**`61.15%` (`288/471`)** | `0.8016`<br>**`0.8464`** | `16.40%` (`82`) / `15.48%`<br>**`9.60%` (`48`) / `7.22%`** | `53` \| `35`<br>**`38` \| `29`** | `USD 0.02205`<br>**`USD 0.01867` (`-15.35%`, `p = 0.0042`; `60.0%` in both R1 & R2)** |
| **`P3_EbadiHard_13A_s9001`** (`13A`, `MIS = 6`, `HP = 3.33`)<br>Tasks `08c026...`, `b48c80...`, `9e5b07...`, `88a26a...` | AWS Documented Baseline<br>**Prometheus Schedule** | `92.00%` / `91.56%`<br>**`92.80%` / `92.55%`** | **`57.40%` (`287/500`)**<br>`55.80%` (`279/500`) | **`60.17%` (`278/462`)**<br>`58.09%` (`273/470`) | `0.8500`<br>**`0.8507`** | `10.00%` (`50`) / `6.93%`<br>**`6.00%` (`30`) / `4.47%`** | `40` \| `38`<br>**`36` \| `30`** | **`USD 0.01951`**<br>`USD 0.02007` (`+2.87%`, `p = 0.6552`; subopt. MIS **-40.0%**, `p = 0.0263`) |
| **6-Task Campaign `*(mean / median)*`**<br>(`250` Shots/Task $\times$ `6` Tasks/Arm) | AWS Documented Baseline<br>**Prometheus Schedule** | `92.13% / 92.00%`<br>**`92.93% / 92.60%`** | `56.80% / 57.40%`<br>**`58.73% / 60.00%`** | `58.40% / 59.22%`<br>**`60.46% / 61.15%`** | `0.8416` / **0.8500**<br>**`0.8512`** / `0.8490` | `11.73% / 10.00%`<br>**`7.00% / 6.80%`** | `19.67` \| `17.33`<br>**`17.67` \| `13.83`** | `USD 0.01988 / USD 0.01955`<br>**`USD 0.01912 / USD 0.01870` (`-3.85%` mean / `-4.35%` med)** |
| **Grand Pooled Totals (`3,000` Shots)**<br>(`1,500` Shots / `USD 16.80` per Arm) | AWS Documented Baseline<br>**Prometheus Schedule** | `1382/1500` (`92.13%`)<br>**`1394/1500` (`92.93%`)** | `852/1500` (`56.80%`)<br>**`881/1500` (`58.73%`)** | `815/1396` (`58.38%`)<br>**`857/1417` (`60.48%`)** | `0.8416`<br>**`0.8512`** | `176/1500` (`11.73%`)<br>**`105/1500` (`7.00%`)** | `118` \| `104`<br>**`106` \| `83`** | `USD 0.01972`<br>**`USD 0.01907` (`-3.29%` pooled; subopt. MIS `-40.34%`, `p = 1.1e-5`)** |

![Two-Window Neutral-Atom Replication on 256-Atom QuEra Aquila](assets/fig5_aquila_2window_neutral_atom_replication.png)
*Part II summary (`256`-atom `QuEra Aquila` via AWS Braket): Separated two-batch replication (`+84.9h` task submission span from `Nov 16 21:35Z` to `Nov 20 10:29Z`; `+6.2h` physical QPU execution gap on `2026-11-20` between `04:15-04:28Z` and `10:32-10:43Z`, `12` AHS tasks, `3,000` physical Rb-87 shots) showing higher overall billed optimal-answer yield in both rounds (`59.3%` vs. `56.1%` in R1; `58.1%` vs. `57.5%` in R2) and repeated `60.0%` optimum probability on the hardest `12A` (`HP = 4.80`) topology (`p = 0.0042`, `-15.35%` cost/optimum).*

---

## Verify the Evidence

**Verification Kind:** Direct **raw-measurement histogram + compiled OpenQASM reconstruction** across all `450` `Rigetti Cepheus-1-108Q` circuits (`10` AWS Braket Task JSONs in `data/jobs/`) **plus raw `pre_sequence`/`post_sequence` neutral-atom shot reconstruction** across all `12` `QuEra Aquila` tasks (`3,000` physical Rb-87 shots in `data/aquila_neutral_atom/tasks/`, zero cloud credentials required; note that local commitment wrapper timestamps on Rigetti Tasks 3-10 precede submission while Tasks 1-2 reflect runner-resume wrapper serialization over unmodified pre-submission caches, as documented in [`PUBLIC_DISCLOSURE.md`](PUBLIC_DISCLOSURE.md)):

```bash
python scripts/verify_braket_campaign.py
```

- **Key files:** [`DETAILED_TECHNICAL_REPORT.md`](DETAILED_TECHNICAL_REPORT.md) · [`data/ALL_450_RIGETTI_CIRCUITS_RESULTS.csv`](data/ALL_450_RIGETTI_CIRCUITS_RESULTS.csv) · [`data/ALL_12_QUERA_AQUILA_TASKS_RESULTS.csv`](data/ALL_12_QUERA_AQUILA_TASKS_RESULTS.csv) · [`PUBLIC_DISCLOSURE.md`](PUBLIC_DISCLOSURE.md) · [`REPOSITORY_SHA256SUMS.txt`](REPOSITORY_SHA256SUMS.txt)

---

## Discuss a Pilot

**Bring a representative workload and an acceptance criterion. We can compare Prometheus with your existing execution approach and measure quality, acceptance rate and charged hardware resources.**

- **Contact:** [william@prometheusdynamics.ca](mailto:william@prometheusdynamics.ca) | [prometheusdynamics.ca](https://prometheusdynamics.ca)
