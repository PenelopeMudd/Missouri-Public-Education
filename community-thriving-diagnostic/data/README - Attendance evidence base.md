# Attendance evidence base — 11 Jefferson County districts

*What is here, what each field means, and what these numbers cannot be used for.*

All files are **public-source aggregates** at school or district level. **No student-level records.**

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

**Chronic absenteeism = missing 10% or more of enrolled days**, whole-day absence only.

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

## Three cautions — read before computing anything

**1. Denominators can move for reasons that have nothing to do with attendance.**
Grandview R-II's rate falls 19.1% → 4.4% between 2021-22 and 2022-23. No child's attendance changed. Missouri Virtual Academy entered the district's reported enrollment with 1,738 students and 1 chronically absent student. Grandview's brick-and-mortar schools were at **15.9%**, essentially flat against 17.4% the year before.

**Grandview 2022-23 is not usable as reported.** Exclude it from any district comparison or county average. A sweep confirmed Grandview is the **only** one of the eleven with a virtual school.

**2. Whole-day absence undercounts lost instruction.**
Counting part-day absence raises the chronic absenteeism rate from roughly 9% to 24% in studies that have done it. These files count whole days. The rate reflects a fraction of instructional time actually lost.

**3. FRL is a proxy that has been drifting.**
Community Eligibility Provision changes which schools collect individual forms, so FRL counts are not cleanly comparable across schools or years. It remains the best school-level poverty measure available here — treat it as directional.

**Also flagged:** Windsor C-1 reports 0.1% for 2020-2021 (2 students of 2,871). That is out of range against every neighbor and its own later years. Treat as a reporting artifact, not a finding.

---

## What these support

District-level trend, school-level poverty variation, and the residual method — predicting attendance from structural conditions and studying schools that beat their prediction.

**The residual method is not yet runnable.** It needs school-level attendance outcomes for all eleven districts; only Grandview has school-level data here.

When it runs: apply an enrollment floor, exclude school-choice variables, and **never name schools in the low tail.** The method is for finding what works, not for ranking schools.
