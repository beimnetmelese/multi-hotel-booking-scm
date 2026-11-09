# Software Configuration Item (CI) Naming Conventions and Versioning Standards

**Project Title:** Multi-Hotel Booking and Management Platform  
**Implementation Scope:** React.js Academic Prototype (Login, Hotel Dashboard, Room Booking, Browser LocalStorage)  
**Document Identifier:** DOC-005  
**Document Version:** 1.0.0  
**Baseline Association:** Baseline BL-001 (Initial Configuration Identification Baseline)  
**Date:** November 9, 2026  
**Governing Standard:** IEEE Std 828-2012 / AASTU SCM Week 5 Guidelines  

---

## 1. Introduction and Objectives

In software configuration management (SCM), standardizing the naming and versioning conventions across all project artifacts is essential to establish unambiguous traceability, avoid accidental overwriting, simplify automated build scripts, and facilitate effective surveillance and audits.

This document establishes the formal naming conventions, identifier syntax, file system organizational patterns, semantic versioning guidelines, and Git branch/commit workflows for the **Multi-Hotel Booking and Management Platform** project. All team members must adhere to these conventions throughout the development lifecycle of the React-based academic prototype.

---

## 2. Configuration Item (CI) Identifiers

### 2.1 Identifier Format Structure
Every controlled software configuration item identified in the project inventory must be assigned a unique, immutable identifier conforming to the following two-part alphanumeric schema:

$$\text{CI-ID} = \langle\text{CATEGORY-PREFIX}\rangle\text{-}\langle\text{NUMBER}\rangle$$

Where:
- **`CATEGORY-PREFIX`**: A 2-to-3 character uppercase alphabetic code denoting the functional classification of the artifact.
- **`-`**: A literal hyphen separator.
- **`NUMBER`**: A 3-digit zero-padded sequential integer (e.g., `001`, `002`, `003`).

### 2.2 Standard Category Prefixes
The project defines nine standard category prefixes:

| Category Prefix | Category Description | Scope & Application Examples |
|:---|:---|:---|
| **`REQ`** | Requirements Documents | Functional specifications, user stories, interface requirements (`REQ-001`). |
| **`DES`** | Design Documents & Diagrams | UI wireframes, component interaction diagrams, architecture models (`DES-001`, `DES-002`). |
| **`SRC`** | Source Code Artifacts | React components, application entry points, JSX views, stylesheets (`SRC-001` through `SRC-005`). |
| **`DB`** | Database Schemas & Scripts | SQL schemas, DDL scripts (Evaluated as **Not Applicable** for this client-side prototype; reserved for future scope). |
| **`DAT`** | Data-Related Artifacts | Sample static JSON datasets, browser localStorage schema helpers (`DAT-001`, `DAT-002`). |
| **`TST`** | Test Cases & Reports | Test specifications, manual test execution logs, verification reports (`TST-001`, `TST-002`). |
| **`CFG`** | Configuration Files | Build tool configs, package manifests, lockfiles, git ignore rules (`CFG-001` through `CFG-004`). |
| **`DOC`** | User & Project Documentation | Setup guides, README, user manuals, SCM plans, SCM specifications (`DOC-001` through `DOC-005`). |
| **`REL`** | Release & Baseline Records | Formal baseline audit logs, release notes, master inventory registers (`REL-001`, `REL-002`). |

### 2.3 Identifier Rules and Integrity Constraints
1. **Uniqueness:** A CI identifier is globally unique within the project repository. Under no circumstance may an identifier be assigned to multiple distinct artifacts.
2. **Immutability:** Once a CI identifier is published in an approved baseline, it cannot be modified or reassigned.
3. **Non-Reusability:** If an artifact is retired, deleted, or merged into another item, its identifier is retired and marked *Obsolete* in the CI register; it must never be reassigned to a new artifact.
4. **Stable Traceability:** All cross-references in code comments, test cases, commit messages, and change requests must reference the formal CI ID (e.g., `Refs: REQ-001, SRC-003`).

---

## 3. File and Directory Naming Conventions

To ensure cross-platform compatibility across Windows, Linux, and macOS development environments, file and folder names must strictly avoid whitespace, special characters (`!`, `@`, `#`, `$`, `%`, `^`, `&`, `*`, `?`), and path-length overflows.

### 3.1 Directory (Folder) Naming
- All folder names must be written in **lowercase** using hyphens or underscores to separate multiple words (`kebab-case` or `flatlowercase`).
- Standard top-level and second-level directory structure:
  - `docs/`: All project documentation, SCM specifications, and baseline logs.
  - `docs/design/`: Visual UI wireframes, flowcharts, and architecture diagrams.
  - `src/`: Application source code root.
  - `src/components/`: Reusable React user-interface components.
  - `src/pages/`: Primary route/view-level React components.
  - `src/data/`: Static mock datasets (e.g., `hotels.json`).
  - `src/styles/`: Application stylesheets and theme definitions.
  - `src/utils/`: Reusable JavaScript helper modules (e.g., localStorage utility).
  - `public/`: Static public web assets (HTML shell, icons, favicon).
  - `tests/`: Test plans, test case markdown documents, and test execution reports.

### 3.2 React Source Files (`.jsx`, `.js`)
- **React Components and Pages:** Must use **`PascalCase`** matching the exported component name.
  - *Examples:* `Login.jsx`, `Dashboard.jsx`, `BookingModal.jsx`, `App.jsx`.
- **Application Bootstrap & Utility Modules:** Must use **`camelCase`** or standard lowercase.
  - *Examples:* `main.jsx`, `storage.js`, `formatters.js`.
- **Consistency Rule:** The filename must correspond exactly to the default exported React component name (e.g., `export default function Dashboard()` resides in `Dashboard.jsx`).

### 3.3 Stylesheets (`.css`)
- Global stylesheets must use lowercase descriptive names: `index.css`, `App.css`.
- Component-specific stylesheets must match the component name or use `kebab-case`: `BookingModal.css` or `booking-modal.css`.

### 3.4 Data Artifacts (`.json`)
- Static JSON data files must use **lowercase `kebab-case`** or **lowercase plural nouns**:
  - *Examples:* `hotels.json`, `room-types.json`.

### 3.5 Documentation Files (`.md`, `.docx`, `.pdf`)
- Formal project-level markdown documents must use **`UPPERCASE_SNAKE_CASE`**:
  - *Examples:* `README.md`, `SCMP.md`, `CONFIGURATION_IDENTIFICATION.md`, `CI_NAMING_CONVENTIONS.md`, `INITIAL_CONFIGURATION_BASELINE.md`, `REQUIREMENTS.md`, `USER_GUIDE.md`.
- Secondary topical documents and specifications may use descriptive lowercase with underscores:
  - *Examples:* `hotel_booking_requirements.md`, `test_cases.md`.

### 3.6 Graphical Diagrams and Media (`.png`, `.svg`, `.jpg`)
- Image files and architectural diagrams must use **lowercase snake_case**:
  - *Examples:* `hotel_booking_flow.png`, `ui_wireframe_login.png`, `component_hierarchy.png`.

### 3.7 Configuration Files
- Standard configuration files must retain their canonical, ecosystem-prescribed filenames:
  - *Examples:* `package.json`, `package-lock.json`, `.gitignore`, `vite.config.js`.

---

## 4. Version Identification and Numbering Standards

To maintain configuration status accounting and deliver unambiguous traceability, version numbering applies across document releases, source code baselines, and milestone deliveries.

### 4.1 Semantic Versioning (SemVer 2.0.0)
For source code releases, project packages, and formal deliverables, version numbers follow the standard three-part format:

$$\text{Version} = \langle\text{MAJOR}\rangle.\langle\text{MINOR}\rangle.\langle\text{PATCH}\rangle$$

1. **`MAJOR` (Incompatible Architectural Shifts):**
   - Incremented when fundamental scope changes, major architectural redesigns, or breaking user interface overhauls occur.
   - *Example:* Transitioning from initial static prototype (`1.x.x`) to an external backend architecture (`2.0.0`).
2. **`MINOR` (Added Functionality / Features):**
   - Incremented when new functional capabilities are added in a backward-compatible manner.
   - *Examples:* Adding the hotel catalog dashboard to the login demo (`1.1.0`), adding room booking action (`1.2.0`).
3. **`PATCH` (Bug Fixes & Minor Adjustments):**
   - Incremented when minor bug corrections, documentation updates, or styling refinements are integrated without adding new features.
   - *Example:* Fixing date-validation logic in the room booking modal (`1.2.1`).

### 4.2 Document Versioning Rules
Documents undergo formal versioning documented in an embedded **Revision History Table**:
- **Draft / Pre-Baseline Versions:** `0.1.0`, `0.2.0`, etc.
- **Initial Formally Approved Baseline:** `1.0.0`.
- **Substantive Content Amendments:** Increments minor version (`1.1.0`).
- **Typographical or Formatting Corrections:** Increments patch version (`1.0.1`).

### 4.3 Git Commit Hashes as Physical Version Identifiers
While semantic version numbers represent logical milestone states, Git cryptographic commit hashes (40-character SHA-1 or abbreviated 7-character hashes) serve as the absolute physical version identifiers. Every baseline and change request record must record the specific Git commit hash corresponding to that state.

---

## 5. Git and Version Control Workflow Conventions

### 5.1 Branching Strategy
The project adopts a structured, lightweight Git-flow branching model suited for academic group collaboration:

```text
main (Protected, stable releases, baselines BL-001..BL-005)
  ▲
  │ (Pull Request merge after review)
develop (Active integration branch)
  ▲
  │
  ├── feature/login-page
  ├── feature/hotel-dashboard
  ├── feature/room-booking
  └── docs/ci-identification
```

1. **`main` Branch:**
   - Represents the verified, production-stable academic milestone releases.
   - Direct commits to `main` are strictly forbidden once the repository is initialized and baselined.
   - Only merged via approved Pull Requests from `develop` accompanied by formal baseline audit sign-offs.
2. **`develop` Branch:**
   - Serves as the day-to-day integration branch where completed features converge.
3. **Feature Branches (`feature/<feature-name>`):**
   - Dedicated short-lived branches created off `develop` to isolate specific functional tasks.
   - *Naming convention:* `feature/login-page`, `feature/hotel-dashboard`, `feature/room-booking`, `feature/localstorage-data`.
4. **Documentation Branches (`docs/<topic-name>`):**
   - Used for preparing major SCM or project documentation deliverables.
   - *Naming convention:* `docs/configuration-identification`, `docs/user-guide`.
5. **Hotfix Branches (`hotfix/<issue-name>`):**
   - Used only for urgent, critical fixes to baseline demonstration blockers.

### 5.2 Commit Message Conventions
Commit messages must follow the **Conventional Commits** specification to ensure automated readability, clear repository logs, and seamless traceability:

$$\langle\text{type}\rangle(\langle\text{scope}\rangle): \langle\text{short description}\rangle$$

- **Allowed Types:**
  - `feat`: A new user-facing functional capability (e.g., `feat(booking): implement room selection modal`).
  - `fix`: A bug fix in existing functionality (e.g., `fix(storage): correct JSON parse error on empty booking key`).
  - `docs`: Additions or revisions to documentation (e.g., `docs(scm): complete configuration identification document`).
  - `style`: Formatting, CSS styling, whitespace adjustments (e.g., `style(dashboard): adjust hotel card padding`).
  - `refactor`: Code reorganization that does not alter external behavior (e.g., `refactor(components): extract HotelCard subcomponent`).
  - `test`: Adding or updating test cases and test documentation (e.g., `test(booking): add test cases for date validation`).
  - `chore`: Maintenance tasks, package configuration, gitignore updates (e.g., `chore(npm): initialize package.json scripts`).

- **Commit Message Quality Rules:**
  - Write subject line in imperative mood ("add", not "added" or "adds").
  - Do not end subject line with a period.
  - Limit the subject line to 72 characters.
  - Include optional issue / CI reference in the commit body (e.g., `Implements: SRC-003, Refs: REQ-001`).

### 5.3 Pull Request (PR) and Code Review Expectations
1. **Mandatory Peer Review:** No branch may be merged into `develop` or `main` without at least one approved peer review.
2. **PR Description Requirements:**
   - Summary of changes implemented.
   - Associated CI identifiers affected (e.g., `Affects: SRC-002, TST-001`).
   - Testing verification performed (e.g., manual browser test verification steps).
3. **Merge Strategy:** Squash-and-merge or clean rebase-merge to keep integration history linear and readable.

### 5.4 Baseline and Milestone Tagging Conventions
Git tags are used to designate immutable milestone baselines and formal release states. All tags must be created as **annotated tags** (`git tag -a <tag-name> -m "<annotation>"`) rather than lightweight tags.

Standard tag formats:
- **SCM Identification Baseline:** `ci-baseline-v<M>.<m>` (e.g., `ci-baseline-v1.0`).
- **Requirements Baseline:** `req-baseline-v<M>.<m>`.
- **Design Baseline:** `des-baseline-v<M>.<m>`.
- **Test / Verification Baseline:** `test-baseline-v<M>.<m>`.
- **Final Release Candidate / Product Release:** `v<MAJOR>.<MINOR>.<PATCH>` (e.g., `v1.0.0`).

---

## 6. Summary Compliance Checklist

| Item | Naming Rule | Example |
|:---|:---|:---|
| **Configuration Item ID** | `CATEGORY-NUMBER` (3 digits) | `REQ-001`, `SRC-003`, `CFG-001` |
| **React Component Files** | `PascalCase.jsx` | `Login.jsx`, `Dashboard.jsx`, `BookingModal.jsx` |
| **JavaScript Utility Files** | `camelCase.js` | `storage.js`, `main.jsx` |
| **Folder Names** | `lowercase-hyphen` | `src/components/`, `docs/design/` |
| **Core SCM Documents** | `UPPERCASE_SNAKE_CASE.md` | `CONFIGURATION_IDENTIFICATION.md` |
| **Dataset Files** | `lowercase.json` | `hotels.json` |
| **Git Branches** | `category/short-name` | `feature/hotel-dashboard`, `develop` |
| **Git Commit Subject** | `<type>(<scope>): <message>` | `docs(scm): add configuration identification document` |
| **Baseline Git Tags** | Annotated tag syntax | `ci-baseline-v1.0`, `v1.0.0` |

