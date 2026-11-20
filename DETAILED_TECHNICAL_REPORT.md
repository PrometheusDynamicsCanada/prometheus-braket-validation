# Detailed 10-Task AWS Braket Ledger & Per-Workload Results (`prometheus-braket-validation`)

*Companion technical report to [`README.md`](README.md) · Part of the [Prometheus quantum execution portfolio](https://github.com/PrometheusDynamicsCanada/prometheus-quantum-overview)*

---

<details>
<summary><strong>Expand Table 1B: Complete 10-Task AWS Braket Hardware Ledger & Commitment Timestamp Notes (USD 198.8400)</strong></summary>

| Task # | Batch & Validation Pillar | Window & Task Timestamps (`data/jobs/*.json`) | AWS Braket Quantum Task ARN (`us-west-1`) | Commitment SHA-256 & JSON Timestamp (`data/commitments/*.json`) | Calibration Snapshot SHA-256 | Circuits \| Shots | Turnaround \| Cost |
| :---: | :--- | :---: | :--- | :--- | :---: | :---: | :---: |
| **1** | `Rigetti_Batch1_P1_W1_72circs`<br>(Pillar 1 Core Sweep - Window 1) | Window 1<br>Sub: `2026-11-01T00:07:49.173806Z`<br>Comp: `2026-11-01T00:08:34.294836Z` | `arn:aws:braket:us-west-1:893688540163:quantum-task/2a6b5957-bbf1-43a5-9194-c87da64399bf` | `6a162ea426172daa...`<br>(`2026-11-01T00:56:22.599515Z` *(resume re-serialized)*) | `e1b24e8dc46002d7...` | 72 \| 73,728 | 45.12s \| USD 31.6344 |
| **2** | `Rigetti_Batch2_P2_Mirrors66`<br>(Pillar 2 4Q-36Q Mirrors + SPAM) | Window 1<br>Sub: `2026-11-01T00:11:06.678697Z`<br>Comp: `2026-11-01T00:11:43.753910Z` | `arn:aws:braket:us-west-1:893688540163:quantum-task/eec556a3-2cd0-4eba-8791-4737cee60aa9` | `0dc5881254c1e873...`<br>(`2026-11-01T00:56:23.836577Z` *(resume re-serialized)*) | `e1b24e8dc46002d7...` | 66 \| 67,584 | 37.08s \| USD 29.0232 |
| **3** | `Rigetti_Batch3_P3_QAOA72`<br>(Pillar 3 4Q-17Q QAOA Trajectories) | Window 1<br>Sub: `2026-11-01T00:58:22.948258Z`<br>Comp: `2026-11-01T00:59:07.891070Z` | `arn:aws:braket:us-west-1:893688540163:quantum-task/c9e0645b-739d-4c3c-aee1-739dcbcf48c5` | `658ed6c8e47d3cac...`<br>(`2026-11-01T00:58:22.899503Z`) | `e1b24e8dc46002d7...` | 72 \| 73,728 | 44.94s \| USD 31.6344 |
| **4** | `Rigetti_Batch4_P4_Block1_Packed48`<br>(Pillar 4 Equal-Budget Packed Block 1) | Window 1<br>Sub: `2026-11-01T01:01:50.931473Z`<br>Comp: `2026-11-01T01:02:12.923326Z` | `arn:aws:braket:us-west-1:893688540163:quantum-task/cc7fe5bb-71ac-4d1c-9b2d-02f544ec917b` | `7e4a89d9881decba...`<br>(`2026-11-01T01:01:50.904771Z`) | `e1b24e8dc46002d7...` | 48 \| 49,152 | 21.99s \| USD 21.1896 |
| **5** | `Rigetti_Batch4_P4_Block2_Isolated_sabre_o3_default` | Window 1<br>Sub: `2026-11-01T01:02:50.617613Z`<br>Comp: `2026-11-01T01:02:58.473605Z` | `arn:aws:braket:us-west-1:893688540163:quantum-task/d1caac13-a61b-4c97-862c-f5e0480772cb` | `7e4a89d9881decba...`<br>(`2026-11-01T01:01:50.904771Z`) | `e1b24e8dc46002d7...` | 12 \| 12,288 | 7.86s \| USD 5.5224 |
| **6** | `Rigetti_Batch4_P4_Block2_Isolated_sabre_o3_matched_budget` | Window 1<br>Sub: `2026-11-01T01:03:10.422394Z`<br>Comp: `2026-11-01T01:03:18.630632Z` | `arn:aws:braket:us-west-1:893688540163:quantum-task/bad64742-ead7-49d1-b1de-cf9d47328981` | `7e4a89d9881decba...`<br>(`2026-11-01T01:01:50.904771Z`) | `e1b24e8dc46002d7...` | 12 \| 12,288 | 8.21s \| USD 5.5224 |
| **7** | `Rigetti_Batch4_P4_Block2_Isolated_tket_matched_budget` | Window 1<br>Sub: `2026-11-01T01:03:30.588240Z`<br>Comp: `2026-11-01T01:03:38.930636Z` | `arn:aws:braket:us-west-1:893688540163:quantum-task/92672c37-8631-4e85-ac99-fa95715de8a6` | `7e4a89d9881decba...`<br>(`2026-11-01T01:01:50.904771Z`) | `e1b24e8dc46002d7...` | 12 \| 12,288 | 8.34s \| USD 5.5224 |
| **8** | `Rigetti_Batch4_P4_Block2_Isolated_prometheus_candidate` | Window 1<br>Sub: `2026-11-01T01:03:50.620575Z`<br>Comp: `2026-11-01T01:03:58.401720Z` | `arn:aws:braket:us-west-1:893688540163:quantum-task/8b348409-6ac6-4762-b6b1-7b9fb279ed5f` | `7e4a89d9881decba...`<br>(`2026-11-01T01:01:50.904771Z`) | `e1b24e8dc46002d7...` | 12 \| 12,288 | 7.78s \| USD 5.5224 |
| **9** | `Rigetti_Batch1_P1_W2_72circs`<br>(Pillar 1 Drift Replication - Window 2) | Window 2<br>Sub: `2026-11-01T09:24:21.065270Z`<br>Comp: `2026-11-01T09:25:05.516169Z` | `arn:aws:braket:us-west-1:893688540163:quantum-task/9d4d452d-9e02-4176-a05c-fd06e78237ac` | `2b7eef3352fafbad...`<br>(`2026-11-01T09:24:21.015843Z`) | `4284e80eb3eb5e3e...` | 72 \| 73,728 | 44.45s \| USD 31.6344 |
| **10** | `Rigetti_Batch1_P1_W3_72circs`<br>(Pillar 1 Post-Recalibration - Window 3) | Window 3<br>Sub: `2026-11-01T19:12:22.391992Z`<br>Comp: `2026-11-01T19:13:02.349031Z` | `arn:aws:braket:us-west-1:893688540163:quantum-task/8e797e69-0955-4129-abd0-43997896fcae` | `66983d6dd653072d...`<br>(`2026-11-01T19:12:22.342659Z`) | `bed37417162b375d...` | 72 \| 73,728 | 39.96s \| USD 31.6344 |
| **Total** | **All 4 Pillars & 3 Calibration Windows** | **W1 + W2 + W3** | **10 Verifiable AWS Braket Task ARNs** | **6 Commitment Ledgers** | **3 Snapshots** | **450 \| 460,800** | **265.73s \| USD 198.8400** |

- **Commitment-Timestamp Chronology Note (Tasks 1-2 vs. Tasks 3-10):** For Tasks 3-10 (312 of 450 circuits, including Window 2, Window 3, and all 96 Pillar 4 unseen circuits), `commitment_timestamp_utc` in `data/commitments/*.json` strictly precedes `submission_timestamp_utc` in `data/jobs/*.json`. For Tasks 1 and 2 (`2a6b5957...` submitted at `00:07:49Z` after locking `rigetti_p1_w1_compiled.pkl` at `00:07:49.124Z`, and `eec556a3...` submitted at `00:11:06Z` after locking `rigetti_p2_mirrors_compiled.pkl` at `00:11:06.595Z`), resuming the Window 1 runner at `00:56:22Z` (`--phase w1_all`) loaded the unmodified `00:07Z`/`00:11Z` compiled caches and re-serialized the JSON wrapper timestamps (`00:56:22Z` / `00:56:23Z`) before hitting the completed-task checkpoint skip. Both JSON files are retained unmodified so their SHA-256 digests remain intact.

</details>

---

## 2. Visual Summary & Detailed Per-Workload Ledgers

![Figure 1: 3-Calibration-Window Hardware Replication on Rigetti Cepheus-1-108Q](assets/fig1_rigetti_3window_replication.png)

<details>
<summary><strong>Expand Table 2: Complete Per-Workload 3-Window Mean Ledger Across All 18 Pillar 1 Workloads (4Q-17Q, 216 Circuits, 221,184 Shots)</strong></summary>

| Workload ID | Family (Width) | SABRE O3 F_B (↑) | TKET F_B (↑) | Prom Control F_B (↑) | Prom Fresh F_B (↑) | Prom Fresh F_H = F_B² (↑) | Prom Fresh HOP \| TVD | Prom Fresh H (bits) | Native 2Q (S / T / P) (↓) | Depth (S / T / P) (↓) | % Δ F_B (Prom Fresh vs. SABRE) (↑) |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| `bipartite_6q_s260126` | bipartite (6Q) | 0.8044 | 0.7740 | **0.8132** | 0.8098 | 0.6561 | 0.5579 \| 0.4850 | 5.8548 | **36.0 / 36.0 / 36.0** | 82.0 / 81.0 / **51.7** | **+0.67%** |
| `bipartite_9q_s260127` | bipartite (9Q) | 0.7232 | **0.7367** | 0.7256 | 0.7257 | 0.5267 | 0.5329 \| 0.5463 | 8.5089 | **84.0** / 101.0 / 87.0 | 122.3 / 182.0 / **111.3** | **+0.33%** |
| `bipartite_12q_s260128` | bipartite (12Q) | 0.3068 | 0.3327 | 0.3177 | **0.3333** | 0.1113 | 0.5072 \| 0.8330 | 9.7423 | 159.0 / 250.0 / **153.0** | 171.0 / 357.0 / **155.3** | **+8.64%** |
| `bipartite_15q_s260131` | bipartite (15Q) | 0.1420 | 0.1368 | 0.1453 | **0.1485** | 0.0220 | 0.5592 \| 0.9633 | 9.9574 | 121.0 / 155.0 / **117.3** | **141.7** / 242.0 / 148.7 | **+4.57%** |
| `dense_4q_s260024` | dense (4Q) | **0.9553** | 0.8845 | 0.9421 | 0.9178 | 0.8430 | 0.6660 \| 0.2894 | 3.7842 | 12.0 / 12.0 / **11.3** | 46.0 / 47.0 / **32.3** | -3.92% |
| `dense_5q_s260025` | dense (5Q) | 0.8992 | 0.8683 | 0.9277 | **0.9308** | 0.8663 | 0.7500 \| 0.2821 | 4.6009 | 18.0 / 19.0 / **17.3** | 50.0 / 50.0 / **44.7** | **+3.51%** |
| `dense_6q_s260026` | dense (6Q) | 0.8423 | 0.8231 | 0.8689 | **0.8735** | 0.7635 | 0.6006 \| 0.3837 | 5.8162 | 64.0 / 69.0 / **44.0** | 150.0 / 133.0 / **78.0** | **+3.70%** |
| `dense_8q_s260028b` | dense (8Q) | 0.7730 | 0.7667 | **0.8218** | 0.8092 | 0.6557 | 0.5518 \| 0.4747 | 7.6803 | 58.0 / 67.0 / **53.3** | **93.0** / 128.0 / 117.0 | **+4.69%** |
| `dense_9q_s260027` | dense (9Q) | 0.5993 | **0.6202** | 0.6191 | 0.6173 | 0.3812 | 0.4906 \| 0.6542 | 8.4806 | 166.0 / 184.0 / **129.0** | 270.0 / 293.0 / **167.0** | **+3.01%** |
| `dense_10q_s260030` | dense (10Q) | 0.5906 | 0.5501 | 0.5989 | **0.6077** | 0.3701 | 0.5299 \| 0.6379 | 9.0553 | 97.0 / 105.0 / **67.0** | 178.3 / 172.0 / **105.0** | **+2.90%** |
| `dense_12q_s260028` | dense (12Q) | 0.2959 | 0.2876 | **0.3269** | 0.3169 | 0.1008 | 0.4974 \| 0.8422 | 9.7513 | 308.0 / 367.0 / **194.0** | 414.0 / 451.0 / **156.3** | **+7.11%** |
| `ising_17q_s260333` | ising (17Q) | 0.0343 | 0.0359 | 0.0355 | **0.0385** | 0.0016 | 0.6182 \| 0.9910 | 9.9857 | **111.0** / 138.0 / 114.3 | **403.0** / 559.0 / 403.3 | **+12.09%** |
| `qaoa_8q_s260428b` | qaoa (8Q) | 0.8330 | 0.8092 | 0.8310 | **0.8389** | 0.7039 | 0.5332 \| 0.4347 | 7.7234 | **59.0** / 69.0 / 61.7 | **154.3** / 208.0 / 160.3 | **+0.71%** |
| `qaoa_12q_s260428` | qaoa (12Q) | 0.3620 | 0.3308 | 0.3760 | **0.3819** | 0.1462 | 0.5426 \| 0.8195 | 9.7111 | 99.0 / 105.0 / **96.0** | 198.7 / 169.0 / **115.7** | **+5.50%** |
| `qft_phase_6q_s260526` | qft_phase (6Q) | 0.2230 | 0.1794 | 0.2973 | **0.3174** | 0.1204 | 0.6702 \| 0.8796 | 5.3643 | 53.0 / **48.0** / 53.7 | 123.0 / 146.0 / **122.0** | **+42.34%** |
| `qft_phase_8q_s260528b` | qft_phase (8Q) | 0.5776 | 0.4381 | 0.5953 | **0.6489** | 0.4240 | 0.7087 \| 0.6486 | 7.3004 | 64.0 / 77.0 / **60.0** | 177.0 / 221.0 / **138.3** | **+12.34%** |
| `qft_phase_9q_s260527` | qft_phase (9Q) | **0.1020** | 0.0536 | 0.0778 | 0.0919 | 0.0085 | 0.5544 \| 0.9915 | 8.4759 | **125.0** / 129.0 / **125.0** | **248.0** / 317.0 / **248.0** | -9.90% |
| `qft_phase_12q_s260528` | qft_phase (12Q) | 0.0000 | 0.0104 | **0.0251** | 0.0104 | 0.0003 | 0.5153 \| 0.9997 | 9.7288 | 264.0 / 237.0 / **224.3** | 476.0 / 460.0 / **319.0** | +0.00% |
| **18-Workload Pooled Mean** | **All 5 Families (4Q-17Q)** | **0.5035** | **0.4799** | **0.5192** | **0.5232** | **0.3723** | **0.5770 \| 0.6754** | **7.8623** | 105.44 / 120.44 / **91.35** | 194.35 / 234.22 / **148.56** | **+3.91%** (16W-0T-2L, p_perm,Holm = **0.0112**) |

</details>

![Figure 2: 4Q to 36Q Clifford Mirror Scaling on Rigetti Cepheus-1-108Q](assets/fig2_clifford_mirrors_4q_to_36q.png)

![Figure 3: Pillar 4 Equal-Budget Challenge and Pillar 3 QAOA Trajectories](assets/fig3_pillar4_equal_budget_and_qaoa.png)

<details>
<summary><strong>Expand Table 3: Pillar 4 Unseen Workload Generalization Ledger (Block 1 + Block 2 Combined, 12 Workloads, 6Q-12Q, 96 Circuits)</strong></summary>

| Unseen Workload ID | Family (Width) | CPU Budget | SABRE Def Primary / F_B (↑) | SABRE Bud Primary / F_B (↑) | TKET Bud Primary / F_B (↑) | Prometheus Primary / F_B (↑) | Prom F_H \| HOP \| TVD \| H | Native 2Q (S_Def / S_Bud / T_Bud / Prom) (↓) | Depth (S_Def / S_Bud / T_Bud / Prom) (↓) |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| `fresh_bipartite_8q_s20261440` | bipartite (8Q) | 1.95s | 0.8303 / 0.8303 | **0.8641 / 0.8641** | 0.7669 / 0.7669 | 0.8617 / 0.8617 | 0.7425 \| 0.6621 \| 0.3827 \| 7.3620 | 28 / **22** / 32 / **22** | 56 / **41** / 76 / **41** |
| `fresh_bipartite_12q_s20261506` | bipartite (12Q) | 3.33s | 0.4001 / 0.4001 | 0.4262 / 0.4262 | 0.4259 / 0.4259 | **0.4289 / 0.4289** | 0.1840 \| 0.5684 \| 0.7574 \| 9.6870 | 79 / **52** / 91 / **52** | 112 / **65** / 168 / **65** |
| `fresh_dense_6q_s20261407` | dense (6Q) | 1.79s | 0.8211 / 0.8211 | **0.9470 / 0.9470** | 0.8997 / 0.8997 | 0.9011 / 0.9011 | 0.8120 \| 0.6216 \| 0.3324 \| 5.7694 | 28 / **23** / 27 / 27 | 64 / **55** / 78 / 73 |
| `fresh_dense_10q_s20261473` | dense (10Q) | 4.87s | 0.6423 / 0.6423 | 0.6468 / 0.6468 | **0.6575 / 0.6575** | 0.6559 / 0.6559 | 0.4304 \| 0.5659 \| 0.5791 \| 9.0128 | 97 / **67 / 67 / 67** | 175 / 100 / **97** / 104 |
| `fresh_qaoa_6q_s20261207` | qaoa (6Q) | 1.95s | 0.6700 / **0.9044** | **0.6909** / 0.8927 | 0.6853 / 0.8951 | 0.6842 / 0.8838 | 0.7812 \| 0.4980 \| 0.3804 \| 5.8597 | 52 / **50 / 50 / 50** | 145 / **143** / 144 / 149 |
| `fresh_qaoa_8q_s20261226` | qaoa (8Q) | 2.46s | 0.6145 / 0.7944 | **0.6258** / 0.7764 | 0.6180 / 0.8057 | 0.6153 / **0.8144** | 0.6632 \| 0.5522 \| 0.4684 \| 7.7354 | 83 / **77** / 78 / 83 | 203 / 178 / **171** / 177 |
| `fresh_qaoa_10q_s20261245` | qaoa (10Q) | 3.12s | 0.6010 / 0.6341 | **0.6011** / 0.6191 | 0.5941 / 0.6280 | 0.5893 / **0.6456** | 0.4170 \| 0.5347 \| 0.5940 \| 9.1224 | 106 / **99 / 99** / 102 | 287 / 263 / 264 / **254** |
| `fresh_qaoa_12q_s20261264` | qaoa (12Q) | 3.70s | **0.6102** / 0.3756 | 0.6079 / 0.3816 | 0.6054 / 0.3829 | 0.6051 / **0.3835** | 0.1473 \| 0.5151 \| 0.8019 \| 9.6967 | 135 / **119** / 127 / 137 | 335 / **284** / 307 / 301 |
| `fresh_qft_6q_s20261307` | qft (6Q) | 1.80s | 0.7215 / 0.7215 | **0.8041 / 0.8041** | 0.6659 / 0.6659 | 0.7205 / 0.7205 | 0.5194 \| 0.7197 \| 0.5971 \| 5.5436 | 41 / **36** / 39 / 41 | 97 / **89** / 109 / 97 |
| `fresh_qft_8q_s20261332` | qft (8Q) | 2.52s | 0.5994 / 0.5994 | 0.5883 / 0.5883 | 0.4733 / 0.4733 | **0.6256 / 0.6256** | 0.3914 \| 0.7007 \| 0.6601 \| 7.2380 | 64 / **56** / 61 / 60 | 179 / **130** / 161 / 139 |
| `fresh_qft_10q_s20261357` | qft (10Q) | 3.56s | 0.3568 / 0.3568 | 0.3660 / 0.3660 | **0.4518 / 0.4518** | 0.4166 / 0.4166 | 0.1736 \| 0.6196 \| 0.8204 \| 9.0102 | 94 / **78** / 80 / 90 | 237 / **183** / 199 / 202 |
| `fresh_qft_12q_s20261382` | qft (12Q) | 3.89s | 0.2281 / 0.2281 | 0.2404 / 0.2404 | 0.2098 / 0.2098 | **0.2755 / 0.2755** | 0.0759 \| 0.6201 \| 0.8790 \| 9.6564 | 122 / **103** / 108 / 107 | 307 / **228** / 267 / 235 |
| **12-Workload Mean** | **All 3 Families (6Q-12Q)** | **2.91s** | 0.5913 / 0.6090 | **0.6174** / 0.6294 | 0.5878 / 0.6052 | 0.6150 / **0.6344** | 0.4448 \| **0.5982** \| 0.6044 \| 7.9745 | 77.42 / **65.17** / 71.58 / 69.83 | 183.08 / **146.58** / 170.08 / 153.08 |

</details>

---

## 3. Cross-Provider Architectural Comparison: Rigetti Cepheus-1-108Q vs. IBM Quantum Heron (10 Identical Workloads)

![Figure 4: Cross-Provider Architectural Comparison Between Rigetti Cepheus-1-108Q and IBM Heron](assets/fig4_cross_provider_rigetti_vs_ibm_heron.png)

| Shared Workload ID | Family (Width) | Rigetti 3W F_B SABRE (↑) | Rigetti 3W F_B TKET (↑) | Rigetti 3W F_B Prom Fresh (↑) | IBM Heron 3-QPU F_B SABRE (↑) | IBM Heron 3-QPU F_B TKET (↑) | IBM Heron 3-QPU F_B Prometheus (↑) | Rigetti 2Q (S / T / P) (↓) | IBM Heron 2Q (S / T / P) (↓) |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| `dense_6q_s260026` | dense (6Q) | 0.8423 | 0.8231 | **0.8735** | 0.9577 | 0.8559 | **0.9668** | 64.0 / 69.0 / **44.0** | 79.0 / 94.0 / **68.0** |
| `dense_9q_s260027` | dense (9Q) | 0.5993 | **0.6202** | 0.6173 | 0.8339 | 0.8130 | **0.8647** | 166.0 / 184.0 / **129.0** | 210.0 / 252.0 / **173.0** |
| `dense_12q_s260028` | dense (12Q) | 0.2959 | 0.2876 | **0.3169** | 0.5454 | 0.3164 | **0.5700** | 308.0 / 367.0 / **194.0** | 339.0 / 619.0 / **291.7** |
| `bipartite_6q_s260126` | bipartite (6Q) | 0.8044 | 0.7740 | **0.8098** | 0.9647 | 0.9385 | **0.9722** | **36.0 / 36.0 / 36.0** | 48.0 / 54.0 / **46.0** |
| `bipartite_9q_s260127` | bipartite (9Q) | 0.7232 | **0.7367** | 0.7257 | 0.8680 | 0.7818 | **0.8894** | **84.0** / 101.0 / 87.0 | 141.0 / 227.0 / **116.0** |
| `bipartite_12q_s260128` | bipartite (12Q) | 0.3068 | 0.3327 | **0.3333** | **0.5920** | 0.4459 | 0.5896 | 159.0 / 250.0 / **153.0** | **142.0** / 355.0 / 142.7 |
| `qft_phase_6q_s260526` | qft_phase (6Q) | 0.2230 | 0.1794 | **0.3174** | 0.7544 | 0.4746 | **0.7897** | 53.0 / **48.0** / 53.7 | 58.0 / 57.0 / **46.0** |
| `qft_phase_9q_s260527` | qft_phase (9Q) | **0.1020** | 0.0536 | 0.0919 | 0.4927 | 0.3330 | **0.6236** | **125.0** / 129.0 / **125.0** | 175.0 / 171.0 / **145.0** |
| `qft_phase_12q_s260528` | qft_phase (12Q) | 0.0000 | **0.0104** | **0.0104** | 0.3309 | 0.1031 | **0.4067** | 264.0 / 237.0 / **224.3** | 312.0 / 405.0 / **235.0** |
| `qaoa_12q_s260428` | qaoa (12Q) | 0.3620 | 0.3308 | **0.3819** | **0.5842** | 0.5281 | 0.5785 | 99.0 / 105.0 / **96.0** | **138.0** / 198.0 / **138.0** |
| **10-Workload Mean** | **4 Families (6Q-12Q)** | **0.4259** | **0.4149** | **0.4478** | **0.6924** | **0.5590** | **0.7251** | 135.80 / 152.60 / **114.20** | 164.20 / 243.20 / **140.14** |

---

## 4. Two-Window Neutral-Atom Ledger on `256`-Atom `QuEra Aquila` (`12` AWS Braket Tasks, `3,000` Rb-87 Shots, `USD 33.6000`)

![Figure 5: Two-Window Neutral-Atom Replication on 256-Atom QuEra Aquila](assets/fig5_aquila_2window_neutral_atom_replication.png)

| Round & Queue Pos | Instance (`Atoms`, `HP`) | Pipeline (`T = 3.0 us`) | Ended (`UTC`) | Valid IS `(↑)` | Exact Opt `(↑)` *(All)* | Exact Opt `(↑)` *(DF)* | Subopt. MIS `(↓)` | Viol. \| Vac. `(↓)` | Quality $r_{\text{MIS}}$ `(↑)` | Entropy `(bits)` `(↓)` | `USD/Opt` `(↓)` | AWS Braket Task ARN (`us-east-1`) |
| :---: | :--- | :--- | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :--- |
| `R1 #1` | `P3` (`13A`, `3.33`) | **Prometheus** | `2026-11-20T04:15:56Z` | **230 (`92.0%`)** | **145 (`58.0%`)** | **142/239 (`59.41%`)** | **10 (`4.0%`)** | **20 \| 11** | **0.8467** | **3.0183** | **`USD 0.0193`** | `arn:aws:braket:us-east-1:893688540163:quantum-task/b48c8077-1bde-4200-b43d-7e00b1f67730` |
| `R1 #2` | `P3` (`13A`, `3.33`) | AWS Baseline | `2026-11-20T04:18:05Z` | 228 (`91.2%`) | 138 (`55.2%`) | 134/235 (`57.02%`) | 24 (`9.6%`) | 22 \| 15 | 0.8420 | 3.1366 | `USD 0.0203` | `arn:aws:braket:us-east-1:893688540163:quantum-task/08c02636-aa6b-43d9-ad4f-02c3645f52b3` |
| `R1 #3` | `P2` (`12A`, `4.80`) | AWS Baseline | `2026-11-20T04:21:18Z` | 224 (`89.6%`) | 131 (`52.4%`) | 127/237 (`53.59%`) | 37 (`14.8%`) | 26 \| 13 | 0.8064 | 3.3446 | `USD 0.0214` | `arn:aws:braket:us-east-1:893688540163:quantum-task/7cba59c1-a937-4501-ad49-d68c9fdabc3b` |
| `R1 #4` | `P2` (`12A`, `4.80`) | **Prometheus** | `2026-11-20T04:23:26Z` | **233 (`93.2%`)** | **150 (`60.0%`)** | **145/238 (`60.92%`)** | **24 (`9.6%`)** | **17 \| 12** | **0.8512** | **2.9126** | **`USD 0.0187`** | `arn:aws:braket:us-east-1:893688540163:quantum-task/c2d84a13-cba2-49ef-920c-90f9b94986d8` |
| `R1 #5` | `P1` (`11A`, `3.00`) | **Prometheus** | `2026-11-20T04:26:40Z` | 230 (`92.0%`) | 150 (`60.0%`) | **146/235 (`62.13%`)** | **13 (`5.2%`)** | 20 \| 15 | 0.8408 | 2.8706 | `USD 0.0187` | `arn:aws:braket:us-east-1:893688540163:quantum-task/b0aa917c-caa3-4164-a526-77ff21db97f3` |
| `R1 #6` | `P1` (`11A`, `3.00`) | AWS Baseline | `2026-11-20T04:28:48Z` | **239 (`95.6%`)** | **152 (`60.8%`)** | 148/241 (`61.41%`) | 24 (`9.6%`) | **11 \| 9** | **0.8736** | **2.6347** | **`USD 0.0184`** | `arn:aws:braket:us-east-1:893688540163:quantum-task/f95ab630-d0e2-4a2b-bab8-1fe83c9b2797` |
| `R2 #1` | `P1` (`11A`, `3.00`) | AWS Baseline | `2026-11-20T10:32:29Z` | 236 (`94.4%`) | **159 (`63.6%`)** | **149/228 (`65.35%`)** | 20 (`8.0%`) | 14 \| 22 | **0.8728** | **2.5260** | **`USD 0.0176`** | `arn:aws:braket:us-east-1:893688540163:quantum-task/09542580-f2cd-4099-83b3-2376693b2830` |
| `R2 #2` | `P1` (`11A`, `3.00`) | **Prometheus** | `2026-11-20T10:34:38Z` | **238 (`95.2%`)** | 152 (`60.8%`) | 150/241 (`62.24%`) | **14 (`5.6%`)** | **12 \| 9** | 0.8720 | 2.6018 | `USD 0.0184` | `arn:aws:braket:us-east-1:893688540163:quantum-task/c1b16629-3e8e-416d-bdde-0070f29edf50` |
| `R2 #3` | `P3` (`13A`, `3.33`) | **Prometheus** | `2026-11-20T10:36:43Z` | **234 (`93.6%`)** | 134 (`53.6%`) | 131/231 (`56.71%`) | **20 (`8.0%`)** | **16 \| 19** | 0.8547 | 3.1124 | `USD 0.0209` | `arn:aws:braket:us-east-1:893688540163:quantum-task/88a26a0b-91b0-4727-ac41-80795a0a0f7f` |
| `R2 #4` | `P3` (`13A`, `3.33`) | AWS Baseline | `2026-11-20T10:38:52Z` | 232 (`92.8%`) | **149 (`59.6%`)** | **144/227 (`63.44%`)** | 26 (`10.4%`) | 18 \| 23 | **0.8580** | **2.9796** | **`USD 0.0188`** | `arn:aws:braket:us-east-1:893688540163:quantum-task/9e5b0732-f4c5-4abe-836e-a0ccdb742a7b` |
| `R2 #5` | `P2` (`12A`, `4.80`) | AWS Baseline | `2026-11-20T10:41:01Z` | 223 (`89.2%`) | 123 (`49.2%`) | 113/228 (`49.56%`) | 45 (`18.0%`) | 27 \| 22 | 0.7968 | 3.3645 | `USD 0.0228` | `arn:aws:braket:us-east-1:893688540163:quantum-task/ce66eabb-117e-40ec-8244-f9a48952a0bc` |
| `R2 #6` | `P2` (`12A`, `4.80`) | **Prometheus** | `2026-11-20T10:43:10Z` | **229 (`91.6%`)** | **150 (`60.0%`)** | **143/233 (`61.37%`)** | **24 (`9.6%`)** | **21 \| 17** | **0.8416** | **2.8904** | **`USD 0.0187`** | `arn:aws:braket:us-east-1:893688540163:quantum-task/6d0844a8-e60c-410c-8da5-016fad5b908b` |

---

## 5. Verification Protocol & Repository Structure

- **Pre-Dispatch Equivalence Verification:** All non-Clifford gate-model circuits traversing <= 20 active physical wires were verified before dispatch for exact statevector equivalence (max_x |P_ideal(x) - P_compiled(x)| < 1e-6 under physical measurement wire remapping); larger 14Q-17Q instances traversing > 20 active physical wires enforced 1-to-1 measurement bijection, zero post-measurement ops, and native basis-gate compliance (`rx`, `rz`, `cz`, `measure`). All 66 Clifford mirror and SPAM circuits (4Q-36Q) were verified via exact `StabilizerState` simulation. All 3 `QuEra Aquila` King's-Graph UDG configurations verified exact Rydberg ground-state equivalence with the unique classical `MIS` optimum (`0` `rydbergLocal` terms).
- **One-Command Raw-Measurement Audit (`450/450` Rigetti Circuits + `12/12` QuEra Aquila Tasks):** [`scripts/verify_braket_campaign.py`](scripts/verify_braket_campaign.py) verifies all file checksums in [`REPOSITORY_SHA256SUMS.txt`](REPOSITORY_SHA256SUMS.txt) and [`REPO_SHA256_MANIFEST.json`](REPO_SHA256_MANIFEST.json), audits all `22` AWS Braket Task ARNs, and recomputes every Rigetti circuit and QuEra Aquila shot directly from raw measurements (`463,800` physical shots total):

```bash
python scripts/verify_braket_campaign.py
```

```text
prometheus-braket-validation/
├── README.md                                               # Executive summary, benchmark tables, and visual plots
├── PUBLIC_DISCLOSURE.md                                    # IP protection boundary & empirical provenance statement
├── DATA_DICTIONARY.md                                      # Complete column-by-column schema reference
├── REPOSITORY_SHA256SUMS.txt                               # LF-normalized SHA-256 manifest of all tracked files
├── REPO_SHA256_MANIFEST.json                               # Structured JSON SHA-256 manifest
├── assets/                                                 # 300-DPI PNG and vector PDF visualizations
├── data/
│   ├── ALL_450_RIGETTI_CIRCUITS_RESULTS.csv                # Master 450-row Rigetti circuit ledger (zero placeholder cells)
│   ├── ALL_12_QUERA_AQUILA_TASKS_RESULTS.csv               # Master 12-row QuEra Aquila neutral-atom ledger (3,000 Rb-87 shots)
│   ├── CROSS_PROVIDER_RIGETTI_VS_IBM_HERON_10WORKLOADS.csv # 10-workload Rigetti vs. IBM Heron comparison table
│   ├── aquila_neutral_atom/                                # UDG register specs & 12 raw pre/post_sequence Braket task JSONs
│   ├── calibration_snapshots/                              # Live Rigetti Cepheus-1-108Q calibration snapshots (W1, W2, W3)
│   ├── commitments/                                        # Pre-execution SHA-256 commitment ledgers (6 batches)
│   ├── jobs/                                               # Raw AWS Braket Rigetti ProgramSet payloads (10 tasks)
│   ├── logical_circuits/                                   # Unrouted .qasm circuits, .npz ideal distributions, & target specs
│   └── results/                                            # Scored JSON ledgers & 3-window statistical summary
└── scripts/
    └── verify_braket_campaign.py                           # Standalone raw-measurement & statistical audit script (numpy + scipy)
```
