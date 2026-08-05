# Attendance evidence base — 11 Jefferson County districts

*What is here, what each field means, and what these numbers cannot be used for.*

All files are **public-source aggregates** at school or district level. **No student-level records.**

---

## Two different measures — read this first

Missouri produces **two** attendance statistics. They are built differently and are not interchangeable.

| | **EDFacts DG814 / DG814PCT** | **Missouri PAR** |
|---|---|---|
| Unit | whole days | **hours** |
| Formula | days absent ≥ 10% of days enrolled | hours attended ÷ hours enrolled |
| Threshold | chronically absent at ≥10% | proportional attendance at ≥90% |
| Used for | federal reporting | MSIP 6 |
| In this folder | yes, the CSVs below | no — PAR-derived values live in the research notes |

**The files in this folder are EDFacts — day-based.** Any PAR-derived figure (100 − PAR) appearing in the research notes is a different measure and **must not be compared to these rates or mixed into the same series.**

The common phrasing *"missing 10% of school days, about 18 days"* is shorthand for a 180-day calendar. Missouri's own calculation is a percentage of scheduled hours, submitted through Core Data / MOSIS.

---

## The files

### `raw/attendance/EDFacts DG814PCT LEA - Eleven District Extract 2020-2023.csv`
District-level chronic absenteeism, three years, all eleven districts.

| field | meaning |
|---|---|
| `DENOMINATOR` | students enrolled |
| `NUMERATOR` | students chronically absent |
| `NUMERIC_VALUE` | chronic absenteeism rate, percent |
| `SUBGROUP` | `ALLLEA` — all students, no breakdowns available |

### `raw/attendance/EDFacts DG814 School - Grandview R-II Extract 2020-2023.csv`
School-level counts, Grandview only. `NUMERIC_VALUE` is a **count**, not a rate — pair it with membership to get a rate.

### `raw/frl/CCD School FRL + Virtual - 11 Districts 2022 (Urban-CCD).csv`
**64 schools, all eleven districts.** Free/reduced lunch, the poverty proxy.

| field | meaning |
|---|---|
| `frl_count` | free + reduced, as published |
| `frl_rate_calc` | `frl_count / enrollment` — **calculated here, not published** |
| `virtual` | `1` = virtual school |
| `school_level` | 0 pre-K · 1 primary · 2 middle · 3 high · 4 other |

Retrieved via the Urban Institute Education Data Portal, a mirror of NCES CCD, used because Missouri's MCDS portal blocks automated access.

---

## Four cautions — read before computing anything

**1. Denominators can move for reasons that have nothing to do with attendance.**
Grandview R-II's rate falls 19.1% → 4.4% between 2021-22 and 2022-23. No child's attendance changed. Missouri Virtual Academy entered the district's reported enrollment with 1,738 students and 1 chronically absent student. Grandview's brick-and-mortar schools were at **15.9%**, essentially flat against 17.4% the year before.

**Grandview 2022-23 is not usable as reported.** Exclude it from any district comparison or county average. A sweep confirmed Grandview is the **only** one of the eleven with a virtual school.

**2. Both measures collapse to one annual figure and a binary threshold.**
A student at 89% and a student at 50% appear the same in the statistic. The pattern — consecutive days, every Monday, first period only — stays inside the district. Districts hold the granular hour-level data that produces the state figure; what gets published is the summary.

**3. Part-day capture depends on local practice.**
Hours only reach the state if schools mark absences by period and their student information system passes them through. Practice varies by district. Studies that count part-day absence report rates roughly 9% → 24% against whole-day counting — an indication of how much a day-based measure leaves out, and a reason the two measures above should never be blended.

**4. FRL is a proxy that has been drifting.**
Community Eligibility Provision changes which schools collect individual forms, so FRL counts are not cleanly comparable across schools or years. It remains the best school-level poverty measure available here — treat it as directional.

**Also flagged:** Windsor C-1 reports 0.1% for 2020-2021 (2 students of 2,871). That is out of range against every neighbor and its own later years. Treat as a reporting artifact, not a finding.

---

## What these support

District-level trend, school-level poverty variation, and the residual method — predicting attendance from structural conditions and studying schools that beat their prediction.

**The residual method is not yet runnable.** It needs school-level attendance outcomes for all eleven districts; only Grandview has school-level data here.

When it runs: apply an enrollment floor, exclude school-choice variables, and **never name schools in the low tail.** The method is for finding what works, not for ranking schools.
