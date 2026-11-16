# 3. Design & Debugging Challenge – CA-3, Challenge B1

**Course:** Operating Systems (25PCCS201) | **Student:** Tashvi Adhlakha (25BTRCL271)
**Submitted:** 15 November 2026 | **Tools:** Python 3.13, matplotlib

## File
`Design_and_Debugging_Challenge.pdf` (9 pages)

## Problem
A Python Round Robin scheduler printed wrong waiting times. On the workload P1(0,5), P2(1,3), P3(2,1), P4(3,2), P5(4,3) with q = 2, it reported an average waiting time of 7.60 instead of the correct 5.80.

## Root causes found
| Defect | Cause |
|---|---|
| **D1 – ordering** | The pre-empted process was re-queued before newly arrived processes, breaking the FIFO rule of the ready queue. P1 ran twice in a row while P2 and P3 were waiting. |
| **D2 – metric** | Waiting time was computed as `CT − BT` instead of `CT − AT − BT`, so every late arrival was charged extra waiting time. |

## How I confirmed it
I fixed each defect separately on the same workload. Only the D1 fix gave 5.60 and only the D2 fix gave 7.80; neither matches the reference. With both fixed the result is 5.80, matching an independently written tick-by-tick reference simulation. I also added a regression check, input validation and several test cases.

## Report structure
Problem statement, OS concept, failure reproduction, system model with execution trace, root cause, fix, validation (failure → fix → retest → evidence), regression check, and the source code of the defective, fixed and reference versions.
