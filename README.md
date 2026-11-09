# ADDIS ABABA SCIENCE AND TECHNOLOGY UNIVERSITY
## COLLEGE OF ENGINEERING
### Course: Software Configuration Management (SCM)
### PROJECT TITLE: DESIGN AND DEVELOPMENT OF A MULTI-HOTEL BOOKING AND MANAGEMENT PLATFORM
### GROUP: 7

---

## Group Members

| No. | Full Name | Student ID |
|:---:|:---|:---:|
| 1 | **BASLIEL MESFIN AMARE** | ETS0200/15 |
| 2 | **BEAMLAK DEREJE MANDEFRO** | ETS0204/15 |
| 3 | **BETELHEM WONDALE** | ETS0261/15 |
| 4 | **BEIMNET MELESE KEBEDE** | ETS0219/15 |

---

## Project Overview

The **Multi-Hotel Booking and Management Platform** is a web-based platform designed to enable prospective guests to explore multiple hotels, check room availability and amenities, and initiate room reservations.

### Academic Implementation Scope
For the current course project milestones, the implementation scope is deliberately focused on a lightweight, modular **React.js academic prototype** comprising:
1. **Login & Authentication Demonstration Page:** A mock authentication screen demonstrating credential input, basic validation, and login state toggling.
2. **Main Hotel Catalog Dashboard:** A responsive hotel list view displaying hotel descriptions, amenity badges, room types, and availability statuses.
3. **Core Room Booking Action:** An interactive modal/form enabling guests to choose room categories, specify dates, enter contact information, and submit a booking.
4. **Browser-Side Data Persistence:** Utilizing browser `localStorage` for demonstration booking records and state management (no production backend or database server is utilized in this prototype scope).

---

## Software Configuration Management (SCM) Deliverables

This repository is governed by formal Software Configuration Management processes conforming to **IEEE Std 828-2012** and the AASTU SCM curriculum guidelines. All core SCM documentation and baseline records are maintained in the [`docs/`](docs/) directory:

| Document | CI ID | Description |
|:---|:---:|:---|
| [**Software Configuration Management Plan (SCMP)**](docs/SCMP.md) | `DOC-003` | Primary SCM governing standard defining CM organization, procedures, baseline schedules, change control, surveillance, and audits. |
| [**Configuration Identification Document**](docs/CONFIGURATION_IDENTIFICATION.md) | `DOC-004` | Complete CI identification specification detailing criteria, taxonomy, storage layout, change tracking, versioning rules, and the master inventory table. |
| [**Configuration Item Inventory (CSV)**](docs/CI_INVENTORY.csv) | `REL-002` | Machine-readable master inventory register tracking all 24 identified configuration items, locations, versions, statuses, and baseline associations. |
| [**CI Naming & Versioning Conventions**](docs/CI_NAMING_CONVENTIONS.md) | `DOC-005` | Formal standards for CI identifiers (`CATEGORY-NUMBER`), file/folder naming, SemVer 2.0.0, Git branch conventions, and Conventional Commits. |
| [**Initial Configuration Baseline Record**](docs/INITIAL_CONFIGURATION_BASELINE.md) | `REL-001` | Formal record establishing **Baseline BL-001** (Initial Configuration Identification Baseline), including Git commit reference and baseline freeze sign-off. |

---

## Repository Structure

```text
multi-hotel-booking-scm/
├── README.md                           # Project overview, team members, and repository guide
├── docs/                               # SCM Governance & Documentation
│   ├── SCMP.md                         # Software Configuration Management Plan
│   ├── CONFIGURATION_IDENTIFICATION.md # Configuration Identification Document
│   ├── CI_INVENTORY.csv                # Master Configuration Item Inventory Register
│   ├── CI_NAMING_CONVENTIONS.md        # Naming & Versioning Standards
│   └── INITIAL_CONFIGURATION_BASELINE.md # Baseline BL-001 Record
├── src/                                # (Planned) React application source code
│   ├── components/                     # Reusable React UI components
│   ├── pages/                          # View pages (Login, Dashboard, Booking)
│   ├── data/                           # Static sample datasets (hotels.json)
│   ├── styles/                         # CSS stylesheets
│   └── utils/                          # Helper utilities (localStorage wrapper)
├── tests/                              # (Planned) Test cases and verification reports
└── package.json                        # (Planned) Node.js manifest and build scripts
```

---

## Git Workflow and Branching Strategy

The repository follows a structured Git workflow:
- **`main`:** Contains stable, verified, and baseline-tagged milestone releases. Direct commits are restricted.
- **`develop`:** Active day-to-day integration branch for merging completed features and documentation.
- **`feature/<name>`:** Short-lived feature branches for isolated development tasks (e.g., `feature/login-page`, `feature/hotel-dashboard`).
- **`docs/<name>`:** Branches dedicated to SCM documentation deliverables.

### Baseline Tags
- **`ci-baseline-v1.0`:** Initial Configuration Identification Baseline (BL-001).

---

## Academic Notice
This repository is developed for educational purposes as part of the **Software Configuration Management (SCM)** course at Addis Ababa Science and Technology University (AASTU), Academic Year 2026.
