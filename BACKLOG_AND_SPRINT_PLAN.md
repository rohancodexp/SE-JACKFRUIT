# StudentRMS - Product Backlog & Two-Sprint Plan
## Deliverables Part-2: Agile Planning & GitHub Project Specification
**Project:** Student Record Management System (StudentRMS)  
**Team 4:**
- **M1 (Leader):** Samiksha Jayanth (`PES1UG24CS414`)
- **M2:** Rohan M (`PES1UG24CS381`)
- **M3:** Saksham Bajpayi (`PES1UG24CS404`)
- **M4:** Riddhi Mundada (`PES1UG24CS372`)
**Course:** Software Engineering (`UE24CS341A`), Semester 5 | PES University

---

## 1. Sprint Strategy & Velocity Overview

In compliance with **Deliverables Part-2 (Item 1.c, 1.d, 1.e)**:
- **Sprint 1 (19th Oct to 23rd Oct 2026):**
  - **Goal:** Core foundation, secure authentication gate, student record addition with strict validation, automatic CGPA computation engine, high-performance search & sorting module, and automated GitHub Actions CI pipeline.
  - **Sprint 1 Velocity:** **24 Story Points** (100% Completed & Verified).
  - **Outcome:** Working Product (`studentrms.exe`), 28 headless tests passed, 1-minute video demo, and PR #1.
- **Sprint 2 (26th Oct to 30th Oct 2026):**
  - **Goal:** Complete record lifecycle (update, confirmed deletion), atomic binary persistence (`students.dat`), text reporting (`reports.txt`), final UI polish, and development freeze.
  - **Sprint 2 Velocity:** **16 Story Points** (Planned).
  - **Outcome:** Complete Product Freeze + 2-Minute Demo Video + Final Report.

---

## 2. Team Member Sprint Allocation Matrix

| Team Member | Work Package | Sprint 1 Stories (SP) | Sprint 1 Focus & Deliverable | Sprint 2 Stories (SP) | Sprint 2 Focus & Deliverable | Total SP |
| :--- | :---: | :--- | :--- | :--- | :--- | :---: |
| **Samiksha Jayanth**<br>*(PES1UG24CS414, M1)* | **WP3** | **US-01 (5 SP)**<br>**US-02 (3 SP)**<br>**US-10 (2 SP)** | Admin Authentication Gate, Credentials Separation (`SEC-001`), Failed-login Audit Log (`login.log`), CI/CD Pipeline. | **US-15 (3 SP)** | Console UI Refinement, Usability review ($\le 3$ clicks), Code Quality Freeze. | **13 SP** |
| **Rohan M**<br>*(PES1UG24CS381, M2)* | **WP4** | **US-05 (3 SP)**<br>**US-06 (3 SP)**<br>**US-07 (2 SP)** | Roll Number & Substring Name Search (`FR-004`), 6-Mode Sorting (`FR-007`), 1,000-Record SLA Benchmark (`NFR-001`). | **US-16 (2 SP)** | Search & Filter Integration for Text Reports, Regression Review. | **10 SP** |
| **Saksham Bajpayi**<br>*(PES1UG24CS404, M3)* | **WP5** | **US-03 (5 SP)**<br>**US-04 (3 SP)** | Add Student Record (`FR-002`), Unique Roll Number Check (`FR-003`), Marks Boundary ($0-100$) Validation (`FR-012`). | **US-11 (3 SP)**<br>**US-12 (3 SP)** | Update Student Records (`FR-005`), Delete Student Record with explicit confirmation (`FR-006`). | **14 SP** |
| **Riddhi Mundada**<br>*(PES1UG24CS372, M4)* | **WP6** | **US-08 (3 SP)**<br>**US-09 (3 SP)** | Automatic Percentage & CGPA Engine (`FR-008`), Merit Rank List Generation (`FR-009`). | **US-13 (4 SP)**<br>**US-14 (3 SP)** | Atomic Binary File Persistence (`students.dat`), Export Reports to Text File (`reports.txt`). | **13 SP** |
| **Team Velocity Total** | | **24 SP (Sprint 1)** | **Working Core Product Delivered** | **16 SP (Sprint 2)** | **Complete System Freeze** | **50 SP** |

---

## 3. Specific Sprint Breakdown by Team Member

### 3.1 Member 1: Samiksha Jayanth (`PES1UG24CS414`) - Team Lead & WP3 Owner

#### Sprint 1 Responsibilities (Total: 10 Story Points) - COMPLETED
- **US-01: Administrator Authentication & Credentials Gatekeeper**
  - **Story Points:** 5 | **Priority:** Critical | **Sprint:** Sprint 1
  - **Mapped Requirements:** `FR-001`, `SEC-001`, `UC-01`
  - **Test Cases:** `TC-AUTH-01`, `TC-AUTH-02`, `TC-SEC-01`
  - **Description:** Implement `auth_login()`, `auth_logout()`, and `auth_is_authenticated()`. Ensure credentials are not hardcoded in plaintext business logic and session state gates all operational functions.
- **US-02: Session Gating & Timestamped Security Audit Log**
  - **Story Points:** 3 | **Priority:** High | **Sprint:** Sprint 1
  - **Mapped Requirements:** `SEC-002`, `SEC-005`
  - **Test Cases:** `TC-AUTH-03`
  - **Description:** Implement `log_auth_event()` appending ISO timestamped entries (`[YYYY-MM-DD HH:MM:SS] User: 'admin' - Status: FAILED_LOGIN`) to `login.log`. Block unauthorized access attempts.
- **US-10: Automated CI/CD Pipeline Configuration**
  - **Story Points:** 2 | **Priority:** High | **Sprint:** Sprint 1
  - **Mapped Requirements:** `NFR-005`, `NFR-006`
  - **Test Cases:** `TC-PORT-01`
  - **Description:** Configure `.github/workflows/ci.yml` to trigger on every push and pull request, building under GCC on Ubuntu and validating that all test suites pass before merge.

#### Sprint 2 Responsibilities (Total: 3 Story Points) - PLANNED
- **US-15: Console UX Polish, Usability Rule & Code Review**
  - **Story Points:** 3 | **Priority:** Medium | **Sprint:** Sprint 2
  - **Mapped Requirements:** `NFR-003`, `NFR-004`
  - **Description:** Verify that every core administrative task is reachable within 3 menu selections (`NFR-003`). Conduct code quality review ensuring no function exceeds ~60 lines (`NFR-004`).

---

### 3.2 Member 2: Rohan M (`PES1UG24CS381`) - WP4 Owner

#### Sprint 1 Responsibilities (Total: 8 Story Points) - COMPLETED
- **US-05: Record Search by Roll Number & Substring Name**
  - **Story Points:** 3 | **Priority:** Critical | **Sprint:** Sprint 1
  - **Mapped Requirements:** `FR-004`, `UC-03`, `SEC-003`
  - **Test Cases:** `TC-SEARCH-01`, `TC-SEARCH-02`
  - **Description:** Implement `search_by_roll_no()` with exact case-insensitive lookup, and `search_by_name()` supporting partial substring queries with bounded `max_results` buffer protection.
- **US-06: Multi-Attribute Student Sorting & Formatting Engine**
  - **Story Points:** 3 | **Priority:** High | **Sprint:** Sprint 1
  - **Mapped Requirements:** `FR-007`, `UC-06`
  - **Test Cases:** `TC-LIST-01`
  - **Description:** Implement `sort_students()` using standard library `qsort` with 6 dedicated comparator functions (`cmp_roll_asc`, `cmp_roll_desc`, `cmp_name_asc`, `cmp_name_desc`, `cmp_cgpa_asc`, `cmp_cgpa_desc`) and formatted table renderers.
- **US-07: Sub-2.0s Performance SLA Benchmark on 1,000 Records**
  - **Story Points:** 2 | **Priority:** High | **Sprint:** Sprint 1
  - **Mapped Requirements:** `NFR-001`
  - **Test Cases:** `TC-PERF-01`
  - **Description:** Author `tests/test_perf.c` synthesizing 1,000 realistic student records and benchmark 1,000 roll lookups, substring queries, and dual sorts. Prove execution within 2.0s (achieved **0.047s**).

#### Sprint 2 Responsibilities (Total: 2 Story Points) - PLANNED
- **US-16: Search & Filter Integration for Exported Reports**
  - **Story Points:** 2 | **Priority:** Medium | **Sprint:** Sprint 2
  - **Mapped Requirements:** `FR-011`, `UC-06`
  - **Description:** Integrate WP4 search and filter routines with Riddhi's WP6 report generator to allow exporting specific filtered sub-lists to `reports.txt`.

---

### 3.3 Member 3: Saksham Bajpayi (`PES1UG24CS404`) - WP5 Owner

#### Sprint 1 Responsibilities (Total: 8 Story Points) - COMPLETED
- **US-03: Add Student Record & Duplicate Roll Prevention**
  - **Story Points:** 5 | **Priority:** Critical | **Sprint:** Sprint 1
  - **Mapped Requirements:** `FR-002`, `FR-003`, `UC-02`
  - **Test Cases:** `TC-ADD-01`, `TC-ADD-02`
  - **Description:** Implement `add_student_record()` and `find_student_by_roll()`. Ensure new records can be inserted into the system and reject any roll number that already exists (`MGMT_ERR_DUPLICATE`).
- **US-04: Mandatory Field Validation & Marks Boundary Checking**
  - **Story Points:** 3 | **Priority:** High | **Sprint:** Sprint 1
  - **Mapped Requirements:** `FR-012`, `SEC-003`
  - **Test Cases:** `TC-VAL-01`, `TC-SEC-02`
  - **Description:** Implement `validate_marks()` and `validate_student_fields()`. Strictly enforce semester range ($1-8$), non-empty strings, and marks bounds ($0.0 \le 	ext{mark} \le 100.0$).

#### Sprint 2 Responsibilities (Total: 6 Story Points) - PLANNED
- **US-11: Update Student Record Details**
  - **Story Points:** 3 | **Priority:** High | **Sprint:** Sprint 2
  - **Mapped Requirements:** `FR-005`, `UC-04`
  - **Test Cases:** `TC-UPD-01`
  - **Description:** Allow updating student department, semester, and individual subject marks for an existing record, automatically triggering CGPA recalculation.
- **US-12: Delete Student Record with Explicit Confirmation**
  - **Story Points:** 3 | **Priority:** High | **Sprint:** Sprint 2
  - **Mapped Requirements:** `FR-006`, `UC-05`
  - **Test Cases:** `TC-DEL-01`, `TC-DEL-02`
  - **Description:** Implement safe record deletion requiring a mandatory `[Y/N]` confirmation step to prevent accidental loss of academic data.

---

### 3.4 Member 4: Riddhi Mundada (`PES1UG24CS372`) - WP6 Owner

#### Sprint 1 Responsibilities (Total: 6 Story Points) - COMPLETED
- **US-08: Automatic Percentage & CGPA Computation Engine**
  - **Story Points:** 3 | **Priority:** Critical | **Sprint:** Sprint 1
  - **Mapped Requirements:** `FR-008`, `UC-07`
  - **Test Cases:** `TC-CGPA-01`
  - **Description:** Implement `compute_percentage()`, `compute_cgpa()`, and `update_student_academics()`. Ensure Percentage and CGPA are always calculated automatically from the 6 subject marks and capped at 10.0.
- **US-09: Academic Merit Rank List Generation**
  - **Story Points:** 3 | **Priority:** High | **Sprint:** Sprint 1
  - **Mapped Requirements:** `FR-009`, `UC-07`
  - **Test Cases:** `TC-RANK-01`
  - **Description:** Generate class rank listings sorted in descending order of CGPA with ordinal rank numbers assigned for academic reporting.

#### Sprint 2 Responsibilities (Total: 7 Story Points) - PLANNED
- **US-13: Persistent Binary File Storage (`students.dat`) & Crash Resilience**
  - **Story Points:** 4 | **Priority:** Critical | **Sprint:** Sprint 2
  - **Mapped Requirements:** `FR-010`, `NFR-002`, `SEC-004`
  - **Test Cases:** `TC-PERSIST-01`, `TC-REL-01`
  - **Description:** Implement atomic binary serialization to `students.dat`. Check file return values and ensure sudden termination during write does not corrupt existing data.
- **US-14: Export Student Records & Rank Reports to Text File**
  - **Story Points:** 3 | **Priority:** Medium | **Sprint:** Sprint 2
  - **Mapped Requirements:** `FR-011`, `UC-08`
  - **Test Cases:** `TC-EXPORT-01`
  - **Description:** Implement formatted text report generation saving complete record tables and rank summaries to `reports.txt`.

---

## 4. GitHub Projects Board Configuration Guide

To reflect this setup in **GitHub Projects**:
1. Open the repository: `https://github.com/samikshajayanth/SE-JACKFRUIT`
2. Go to **Projects** $ightarrow$ Open **"StudentRMS Sprint Board"**.
3. Create custom fields:
   - **Sprint:** Single select (`Sprint 1`, `Sprint 2`).
   - **Story Points:** Number field ($1, 2, 3, 5$).
   - **Assignee:** GitHub username of the member.
   - **Work Package:** Single select (`WP3`, `WP4`, `WP5`, `WP6`, `WP7`).
4. Move all **Sprint 1 User Stories (US-01 through US-10)** to **Done**.
5. Keep **Sprint 2 User Stories (US-11 through US-16)** in **Todo / Sprint Backlog**.
