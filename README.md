# Operating Systems Laboratory – Semester 3 Submissions

**Jain (Deemed-to-be University) · Faculty of Engineering & Technology · Department of Computer Science & Engineering**

## Student and Course Details

| | |
|---|---|
| **Student Name** | Tashvi Adhlakha |
| **USN** | 25BTRCL271 |
| **Program** | B.Tech Computer Science and Engineering (AIML) |
| **Semester / Section** | Semester 3, Section E |
| **Academic Year** | 2026–2027 |
| **Course** | Operating Systems Laboratory |
| **Course Code** | 25PCCS201 |

## Overview

This repository is the consolidated submission for the Operating Systems course. It contains five assessed deliverables, arranged in submission order. Each deliverable lives in its own numbered folder with the report (PDF) and a README that states the question, method, key findings and how the report is organised.

Three of the deliverables study CPU scheduling from different angles: theory and fairness (research), controlled simulation (performance investigation), and fault diagnosis (debugging). One studies process placement on a real Linux system (CPU affinity), and one is the complete laboratory record covering all 21 textbook chapters.

## Repository Structure

```text
Operating-Systems-Sem-3/
├── README.md
├── 01-Research-Writeup/
│   ├── README.md
│   ├── Research_Writeup.pdf
│   └── R3_references.ris
├── 02-Performance-Investigation/
│   ├── README.md
│   └── Performance_Investigation.pdf
├── 03-Design-and-Debugging-Challenge/
│   ├── README.md
│   └── Design_and_Debugging_Challenge.pdf
├── 04-Linux-Systems-Engineering-Challenge/
│   ├── README.md
│   └── Linux_Systems_Engineering_Challenge.pdf
└── 05-Lab-Observation-Report/
    ├── README.md
    └── Lab_Observation_Report.pdf
```

## Submission Summary

| # | Deliverable | Assessment | Focus | Pages |
|---|---|---|---|---|
| 1 | [Research Writeup](01-Research-Writeup) | R3 Research Activity | Fairness vs throughput in CPU scheduling, tested in a Python simulator and in a Rust kernel (Micro-OS) | 12 |
| 2 | [Performance Investigation](02-Performance-Investigation) | CA-2, Experiment 1 | Experimental comparison of FCFS, SJF, SRTF, Priority and Round Robin across three workloads | 21 |
| 3 | [Design & Debugging Challenge](03-Design-and-Debugging-Challenge) | CA-3, Challenge B1 | Root-cause analysis and repair of an incorrect Round Robin scheduler | 9 |
| 4 | [Linux Systems Engineering Challenge](04-Linux-Systems-Engineering-Challenge) | CA-5, Challenge L6 | CPU affinity investigation on Linux (`taskset`, `/proc`) | 9 |
| 5 | [Lab Observation Report](05-Lab-Observation-Report) | Laboratory Record | Experiments from Chapters 1 to 21 with source code and output | 110 |

## Key Results

- **Research Writeup:** maximising throughput does not give fair CPU allocation. SJF and SRTF gave the highest throughput but low Jain's fairness index under overload, while Round Robin stayed near 1 at a cost of 7% to 23% of throughput. The findings held on a real kernel.
- **Performance Investigation:** no scheduler was best on every workload. SRTF and SJF minimised waiting time (68% below FCFS on the mixed workload), and Round Robin with a 10 ms quantum gave the best balance for interactive work.
- **Design & Debugging Challenge:** two independent defects (ready-queue ordering and the waiting-time formula) were isolated, fixed one at a time, and validated against a separate reference simulator. Average waiting time went from 7.60 to the correct 5.80.
- **Linux Systems Engineering Challenge:** pinning all work to one CPU nearly doubled completion time, an unbalanced 3+1 pinning cost about 49%, and balanced pinning matched the kernel's own load balancing with zero migrations.
- **Lab Observation Report:** 21 chapters of experiments, each with aim, source code and execution output.

## Tools and Environment

Python 3.13 (pandas, matplotlib), C (GCC), Rust (Micro-OS kernel), Bash and Linux `taskset` / `/proc` (Ubuntu 24.04). Simulations use fixed random seeds so results can be reproduced.

## How to Evaluate

1. Start with this page for the overall picture, then open each numbered folder in order.
2. Read the folder README for a one-page summary, then open the PDF for the full method, results, source code and references.
3. Reference list for the research write-up: `01-Research-Writeup/R3_references.ris` (importable into Zotero, Mendeley or EndNote).

## Contact

Tashvi Adhlakha · USN 25BTRCL271 · GitHub: [@TashStack-18](https://github.com/TashStack-18)
