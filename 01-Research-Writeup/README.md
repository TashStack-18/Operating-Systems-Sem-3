# 1. Research Writeup – R3: Fairness vs Throughput in CPU Scheduling

**Course:** Operating Systems (25PCCS201) | **Student:** Tashvi Adhlakha (25BTRCL271)

## Files
| File | Description |
|---|---|
| `Research_Writeup.pdf` | The 12-page research write-up |
| `R3_references.ris` | Reference list (8 entries) in RIS format; imports into Zotero, Mendeley or EndNote |

## Research question
Does maximizing throughput necessarily produce fair CPU allocation?

## What I did
- Compared six policies: FCFS, SJF, SRTF, HRRN and Round Robin with two quantum values.
- Measured throughput, CPU utilization, waiting-time variance and Jain's fairness index.
- Used two workload mixes and three load levels (underloaded ρ = 0.7 up to overloaded ρ = 1.1), with a fixed context-switch cost.
- Built a discrete-event simulator in Python, then implemented the same policies in my own Rust kernel (the Micro-OS from CA-6) and repeated the experiments there (440 kernel runs).

## Key findings
- Under overload, SJF and SRTF gave the highest throughput but low fairness (about 0.12 to 0.28 in the simulator, 0.18 to 0.46 on the kernel).
- Round Robin stayed close to a fairness index of 1, at a cost of 7% to 23% of throughput depending on quantum and workload.
- Underloaded, all policies were within about 1% of each other, so the trade-off shows up only under overload.
- Throughput peaked at an 8 ms quantum while fairness was still about 0.93.
- The simulator's conclusions held on the real kernel, with absolute numbers shifting by a few percent.

## Sources
The references cited in the write-up (Silberschatz et al., Stallings, Schrage, Bansal and Harchol-Balter, Wierman and Harchol-Balter, Jain et al., OSTEP, Waldspurger and Weihl, Linux kernel CFS docs) are in `R3_references.ris`.
