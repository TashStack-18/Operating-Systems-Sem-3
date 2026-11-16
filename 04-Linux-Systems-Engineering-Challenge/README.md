# 4. Linux Systems Engineering Challenge – CA-5, Challenge L6

**Course:** Operating Systems (25PCCS201) | **Student:** Tashvi Adhlakha (25BTRCL271)
**Submitted:** 16 November 2026 | **Tools:** Python 3.13, Bash, `taskset`, `/proc`, pandas, matplotlib

## File
`Linux_Systems_Engineering_Challenge.pdf` (9 pages)

## Question
How much does restricting a CPU-bound workload to a subset of CPUs change makespan, utilization, throughput and variability, and can deliberate pinning match the kernel's own load balancing?

## Method
- Ran 4 identical CPU-bound workers under four affinity policies: unrestricted, all pinned to one CPU, balanced pinning (2+2) and imbalanced pinning (3+1).
- 10 repetitions per policy with a fixed seed, on Ubuntu 24.04 (kernel 6.18) in a 2-vCPU KVM guest.
- Measured completion time, CPU utilization, throughput, variability, context switches and CPU migrations (sampled from `/proc/<pid>/stat` every 5 ms).

## Key findings
- Pinning everything to one CPU halved utilization and nearly doubled completion time.
- Imbalanced pinning (3+1) left a CPU idle and cost about 49%.
- Balanced pinning matched the kernel's load balancing with zero migrations, but gave no speed-up for this workload.
- Affinity is a tool for predictability, cache/NUMA locality and isolation, not a default performance win.

## Report structure
Problem, OS concept, question, hypothesis, environment, tools, experimental design, results, analysis, conclusion, textbook-model comparison, limitations and the full source code.
