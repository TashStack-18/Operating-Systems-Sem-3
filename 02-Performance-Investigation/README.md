# 2. Performance Investigation – CA-2, Experiment 1

**Course:** Operating Systems (25PCCS201) | **Student:** Tashvi Adhlakha (25BTRCL271)
**Submitted:** 15 November 2026 | **Tools:** Python 3.13, pandas, matplotlib

## File
`Performance_Investigation.pdf` (21 pages)

## Performance question
How do FCFS, SJF, SRTF, Priority and Round Robin (quantum 5, 10, 20 ms) differ in waiting time, turnaround time, response time, throughput and context-switch count under CPU-bound, short-burst and mixed workloads, and does the best algorithm change with the workload?

## Method
- Wrote a discrete-event scheduling simulator in Python and validated it against hand-computed textbook cases.
- Ran every algorithm on identical seeded process sets (50 processes per run, 5 repetitions per workload).
- Ran a scaling study from 10 to 200 processes.

## Key findings
- SRTF and SJF had the lowest average waiting time on every workload (68% below FCFS on the Mixed workload).
- Round Robin gave 4 to 25 times better response time than FCFS on CPU-bound and Mixed work, but with 3 to 25 times more context switches and 59% higher waiting time on CPU-bound jobs.
- Priority scheduling with random priorities was no better than FCFS.
- No scheduler was best everywhere; for a mixed interactive workload, Round Robin with a 10 ms quantum gave the best balance.

## Report structure
Summary, question, objective, OS concept, hypothesis, environment, variables, methodology, implementation, workloads, results, analysis, visualization, discussion, engineering decision, limitations, AI disclosure, conclusion. The appendices hold the per-run raw data, the full source code (`sched.py`) and reproduction steps.
