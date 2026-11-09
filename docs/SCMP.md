# Software Configuration Management Plan (SCMP)

**Project:** Multi-Hotel Booking and Management Platform  

**Implementation scope:** React-based academic prototype  

**Version:** 1.0  

**Primary reference:** IEEE Std 828-2012


## 1. Introduction


### 1.1 Purpose

This Software Configuration Management Plan (SCMP) defines the practical procedures for identifying, organizing, controlling, tracking, reviewing, and maintaining the software configuration items (CIs) of the Multi-Hotel Booking and Management Platform project. It serves as the project's rulebook and single source of truth for configuration management: it states what is controlled, who is responsible, how changes are handled, when reviews occur, and where records are kept.


### 1.2 Scope

This plan applies to the small React-based demonstration website developed for the project. The implementation scope is limited to a login page, a main dashboard or hotel-list page, and one core room-booking action. The application will use React, JavaScript, CSS, and simple browser-side data storage. It does not include a production backend, database server, payment gateway, external hotel APIs, or a complete commercial booking service.


### 1.3 Organizational relationships and communication

The project team is responsible for following this plan. The Project Manager coordinates project work and approves significant changes. The Configuration Manager maintains this plan, the configuration-item register, baselines, and change records. Developers implement approved changes, while testing personnel verify that changed items work as expected. In a small academic project, one person may perform more than one role. Progress and configuration decisions are communicated through the project GitHub repository and its Issues, Pull Requests, commit history, and project meetings.


### 1.4 References

The primary planning reference is IEEE Std 828-2012, IEEE Standard for Configuration Management in Systems and Software Engineering, as required by the course assignment. The project also uses the official Git, GitHub, and React documentation for tool procedures. The course lecture, Software Configuration Management – Week 5: SCM Plan and Tools (AASTU, October 2025), is used as additional course guidance. This plan is tailored to the size and scope of the project rather than copying an organization-wide plan.


## 2. Project Overview


### 2.1 Project description

The Multi-Hotel Booking and Management Platform is a web application concept that allows users to view hotel information and initiate a room booking. For this assignment, the prototype demonstrates the basic user flow through a login screen, a dashboard showing hotel information, and a booking action. Sample hotel information may be loaded from a static JSON file. Booking records and simple demo state may be stored in browser localStorage.


### 2.2 Project assumptions and limitations

The project is a small academic prototype with a limited team and schedule. The application is expected to run in a modern web browser. Authentication is for demonstration only and must not be represented as secure production authentication. Browser localStorage is suitable for simple demonstration data, but it is not a secure database and should not store passwords or sensitive personal information. A static JSON file can provide initial hotel data; a browser-only React application cannot directly rewrite that local JSON file, so changes such as bookings should be persisted in localStorage for this prototype.


### 2.3 Applicability boundaries

Configuration management covers the source code, interface assets, sample data, project configuration, tests, documentation, and release records produced for this prototype. Supplier-management procedures are not applicable because the current scope does not depend on contracted software suppliers. Formal external-interface management is also not applicable because no external APIs or backend services are included. If either becomes part of the project, the SCMP must be updated before the new dependency is adopted.


## 3. Objectives of Configuration Management


### 3.1 Objectives

The objectives are to: (1) identify and uniquely name the project’s configuration items; (2) establish controlled baselines at important milestones; (3) prevent unauthorized or undocumented changes; (4) maintain traceability between requirements, changes, code, tests, and releases; (5) report the current status of configuration items; (6) verify that approved changes are correctly implemented; and (7) improve the configuration process using review findings and project feedback.


### 3.2 Relationship between the plan and tools

The SCMP defines the strategy, responsibilities, and procedures—what must happen, when, and by whom. Git and GitHub provide the technical capabilities to carry out and record those procedures. Using a tool does not replace the need for a plan; the plan explains how the team will use the tools consistently.


## 4. Configuration Management Organization and Responsibilities


### 4.1 Roles and authorities

Project Manager: coordinates project activities, resolves priority conflicts, and approves significant changes and baseline releases. Configuration Manager: owns and updates this SCMP, maintains the CI register, monitors repository activity, coordinates change control, and prepares status reports. Developer: follows branching and commit rules, implements approved changes, and updates relevant documentation. Testing Personnel: checks changed functionality, records defects, and confirms whether a change is ready to be integrated or released. Stakeholders or the instructor may provide feedback and review deliverables where required by the course.


### 4.2 SCMP approval and distribution

The Configuration Manager prepares and maintains the SCMP. The Project Manager reviews and approves the project version before it is treated as the governing plan. The approved copy is stored in the repository at docs/SCMP.docx, with a Markdown companion at docs/SCMP.md when maintained. The repository is the controlled distribution location; team members should use the latest approved version rather than keeping independent, untracked copies. Any approved revision is announced to the team through the repository or project communication channel.


## 5. Configuration Identification


### 5.1 Identification criteria

An item is treated as a configuration item when changing it could affect project requirements, user-visible behavior, build/run behavior, testing, or the ability to reproduce and review the project. Each CI is given a stable name or identifier and stored in the project repository. File and folder names should be descriptive and consistent.


### 5.2 Configuration-item register

The following items are controlled for this project:


| ID | Configuration item | Location / record |
|---|---|---|

| CI-01 | Project requirements and scope | Requirements document / project notes |

| CI-02 | React application source code | src/ and public/ |

| CI-03 | User interface pages and components | src/pages/ and src/components/ |

| CI-04 | Stylesheets and visual assets | src/styles/ and public/ |

| CI-05 | Sample hotel data and booking data | src/data/hotels.json and browser localStorage behavior |

| CI-06 | Project and dependency configuration | package.json and package-lock.json (or equivalent lockfile) |

| CI-07 | Test cases and test results | tests/ and test records |

| CI-08 | SCMP and other project documentation | docs/ and README.md |

| CI-09 | Baseline, audit, and release records | Git tags, GitHub Issues/PRs, and release notes |


### 5.3 Baselines

A baseline is an agreed, recorded version of selected configuration items that serves as a reference point for later work. The project establishes these baselines: Requirements Baseline after the project scope and core requirements are agreed; Design Baseline after the page structure and basic navigation are agreed; Development Baseline after the login, dashboard, and booking flow are integrated; Test Baseline after test cases and test results are recorded; and Release Baseline when the final demonstration version is approved. Baselines are identified using Git commits and tags, with a short record describing what is included.


## 6. Configuration Management Tools and Resources


### 6.1 Tools

React is used to build the user interface. JavaScript implements application behavior, and CSS controls presentation. Git records source-code and document history. GitHub hosts the repository and supports Issues, Pull Requests, review, and controlled collaboration. Visual Studio Code is the development environment. Browser Developer Tools support debugging and inspection. Static JSON may provide sample hotel data, while localStorage stores simple booking records in the browser for demonstration purposes.


### 6.2 Personnel and other resources

The required resources are the assigned project team members, their computers, a modern browser, internet access for repository collaboration, the Git and GitHub tools, React development dependencies, and project documentation. Team members should understand the agreed repository workflow, basic Git commands, and the process for recording and reviewing changes. No dedicated configuration-management server or paid SCM tool is required for this small project.


## 7. Version Control Strategy


### 7.1 Repository structure

The GitHub repository is the official source repository. A suggested structure is:


```text
multi-hotel-booking/
├── public/
├── src/
│   ├── components/
│   ├── pages/
│   │   ├── Login.jsx
│   │   ├── Dashboard.jsx
│   │   └── Booking.jsx
│   ├── data/
│   │   └── hotels.json
│   ├── styles/
│   ├── App.jsx
│   └── main.jsx
├── tests/
├── docs/
│   ├── SCMP.docx
│   └── SCMP.md
├── package.json
├── package-lock.json
├── README.md
└── .gitignore
```


### 7.2 Branching and commit rules

The main branch contains stable, reviewed project versions. A develop branch may be used to integrate work before release. Each separate task should use a short-lived feature branch, for example feature/login-page, feature/hotel-dashboard, or feature/room-booking. Developers should make focused commits with clear messages, such as “Add hotel list to dashboard” or “Persist booking in localStorage”. Changes are merged into the shared branch only after review and basic testing. Direct changes to main should be avoided except for an agreed urgent correction.


### 7.3 Version identification

Important versions are identified using Git tags. The project may use MAJOR.MINOR.PATCH numbering: MAJOR for incompatible or major scope changes, MINOR for new functionality, and PATCH for small corrections. Example tags include v1.0.0 for the first complete demonstration, v1.1.0 for an additional feature, and v1.1.1 for a small correction. Academic milestone baselines may also use descriptive tags such as requirements-baseline and release-v1.0.


## 8. Configuration Change Control


### 8.1 Change request process

Any proposed change to a controlled item must be recorded before implementation. For this project, GitHub Issues are the primary change-request log. Each request should state the requested change, reason, affected CI(s), expected benefit, possible risks, and priority. Small documentation corrections may be handled directly by the Configuration Manager, but changes affecting requirements, user flow, data handling, or a baseline require Project Manager approval.


### 8.2 Review, approval, and implementation

The Configuration Manager reviews the request and considers its impact on scope, schedule, related files, tests, and existing baselines. The request is approved, rejected, or deferred, and the decision is recorded in the Issue. An approved change is implemented on a separate branch, tested, and submitted for review. After acceptance, it is merged and the related Issue is closed. The CI register, documentation, tests, and baseline records are updated when affected.


### 8.3 Emergency changes

If an urgent correction is needed to make the demonstration usable, the developer may prepare the smallest necessary fix. The change must still be recorded in Git, reviewed as soon as practical, tested, and documented. An emergency change must not become an undocumented permanent exception to the normal process.


## 9. Configuration Status Accounting and Reporting


### 9.1 Records maintained

Configuration status accounting records the current and historical status of controlled items and changes. The project uses the Git commit history, Git tags, GitHub Issues, Pull Requests, the CI register, test records, and release notes. These records should make it possible to determine what changed, who changed it, when it changed, why it changed, and whether it was reviewed and approved.


### 9.2 Reporting frequency and metrics

The Configuration Manager reviews repository activity, open change requests, merged changes, and baseline status at least once each week and at each major project milestone. A brief status update is recorded in the project notes or repository. Useful measures include the number of open and completed change requests, changes awaiting review, unresolved defects, completed CI items, and whether planned baselines were established on schedule. Metrics are used to identify delays or recurring problems, not merely to produce numbers.


### 9.3 Traceability

Where practical, a GitHub Issue should be referenced in the related Pull Request or commit. Test results should identify the feature or change being tested. Baseline tags should point to the exact repository state used for a milestone or release. This creates traceability from a requested change to its implementation, verification, and delivered version.


## 10. Configuration Verification, Surveillance, and Auditing


### 10.1 Surveillance

Surveillance is ongoing monitoring to determine whether the team is following this SCMP. It is different from a formal audit. The Configuration Manager checks repository organization, branch usage, commit messages, change-request records, approval evidence, baseline tags, and documentation updates. Recurring deviations are reported to the Project Manager and corrective actions are agreed.


### 10.2 Verification and audit activities

Verification checks whether configuration items are complete and consistent with approved requirements. Functional checks include opening the login page, using the demonstration login flow, viewing hotel information on the dashboard, selecting a room, submitting a booking, and confirming that the booking record is saved and can be retrieved. Physical/configuration checks confirm that expected source files, styles, sample data, configuration files, tests, and documentation are present in the repository and correspond to the recorded baseline.


### 10.3 Audit schedule and records

A preliminary configuration review is performed at the beginning of Week 7, before final testing is completed. A final functional and physical configuration audit is performed during Week 8 before the release baseline is approved. The Configuration Manager records the audit date, items checked, findings, deviations, responsible person, and corrective action. Any unresolved critical issue must be addressed or explicitly reported before the project is presented as complete.


## 11. Build and Release Management


### 11.1 Build procedure

The developer obtains the approved source from the repository, installs dependencies using the package manager and lockfile where available, and runs the React development or production build command defined in package.json. The application is checked in a modern browser. Build errors, missing dependencies, or configuration problems are corrected and recorded before release.


### 11.2 Release procedure

A release candidate is prepared from the reviewed and tested branch. The team confirms that the login demonstration, hotel dashboard, and booking action work; sample data is available; booking records persist as expected; and no known critical defect prevents the demonstration. The Configuration Manager creates a release tag and updates the release notes. The release record identifies the version, date, included features, known limitations, and relevant baseline commit.


## 12. Configuration Management Schedule


### 12.1 Planned activities and milestones

Configuration-management activities are aligned with the eight-week project schedule:


| Period | Project phase | Configuration-management activities |
|---|---|---|

| Week 1 | Planning | Identify initial CIs; create repository; record initial project scope; prepare SCMP draft. |

| Week 2 | Design | Review page structure; establish Requirements and Design Baselines; record approved design changes. |

| Week 3 | Core setup | Set up React project and repository structure; control dependency/configuration files. |

| Week 4 | Login and dashboard | Develop login and hotel dashboard on feature branches; review and test merged changes. |

| Week 5 | Booking module | Implement the room-booking action; record change requests and related test evidence. |

| Week 6 | Data management | Check sample JSON and localStorage behavior; update CI register and documentation. |

| Week 7 | Testing | Perform preliminary configuration review; verify core functions; record defects and corrections. |

| Week 8 | Release preparation | Perform final audit; resolve or document findings; establish Release Baseline and tag final version. |


### 12.2 Dependencies

The requirements baseline depends on agreement about the project scope. The design baseline depends on the page and navigation design being reviewed. The development baseline depends on integration of the login, dashboard, and booking flow. The test baseline depends on completion of the core implementation and test records. The release baseline depends on successful final checks and closure or documented acceptance of remaining issues.


## 13. SCMP Review, Maintenance, and Continuous Improvement


### 13.1 Review and update frequency

The Configuration Manager reviews this plan at the start of the project and at each major milestone, and at least once every two weeks while development is active. The plan is updated when project scope, roles, tools, CI categories, workflow, schedule, or risks change. Proposed plan changes are reviewed by the Project Manager before the revised version becomes the approved plan.


### 13.2 Revision control and communication

Each SCMP revision is recorded in Git with a meaningful commit message. The document should include a revision history showing version, date, author/owner, and a brief description of the change. The latest approved version remains in the repository's docs folder. The Configuration Manager communicates significant updates to all team members and ensures obsolete local copies are not mistaken for the current plan.


### 13.3 Continuous improvement

Feedback from surveillance, audits, testing, and team experience is used to improve the plan. The team may simplify procedures that are unnecessarily heavy for the project, but must preserve identification, change control, traceability, status reporting, and verification. Lessons learned are recorded so the same configuration problems are less likely to recur.


## 14. Configuration Management Risks


### 14.1 Risks and mitigation

Source-code loss: use a remote GitHub repository and push work regularly. Accidental or unauthorized changes: use branches, Pull Requests, and review. Merge conflicts: keep branches focused and integrate frequently. Incorrect booking behavior or data: test the booking flow and verify localStorage records. Missing or inconsistent documentation: include documentation in the CI register and review it at milestones. Exposure of secrets: do not commit passwords, API keys, or private credentials; use sample/demo data only. Unclear responsibilities: assign role ownership at project start, even if one person holds multiple roles.


## 15. Conclusion


### 15.1 Summary

This SCMP establishes a proportionate configuration-management process for the React-based Multi-Hotel Booking and Management Platform prototype. It identifies the items under control, assigns responsibilities, defines baselines and change procedures, specifies status records and reporting, and schedules surveillance, verification, and audits. Git and GitHub support the process, while this plan defines how they are used. The plan will be reviewed and updated as the project progresses.


## References

1. IEEE. (2012). *IEEE Standard for Configuration Management in Systems and Software Engineering* (IEEE Std 828-2012).
2. Addis Ababa Science and Technology University. (2025, October). *Software Configuration Management: Week 5 – SCM Plan and Tools* [Course lecture slides].
3. Git documentation. https://git-scm.com/doc
4. GitHub documentation. https://docs.github.com/
5. React documentation. https://react.dev/

## Revision History

| Version | Date | Description |
|---|---|---|
| 1.0 | November 2026 | Initial project-specific SCMP |
