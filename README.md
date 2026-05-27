# Task 3: Secure Coding Review

## 1. Introduction
In modern software engineering, security cannot be handled as a reactive, post-deployment process. 
A **Secure Code Review** is a foundational defensive practice within the software development lifecycle (SDLC) that targets architectural anomalies, functional coding flaws, and systemic misconfigurations before code is compiled or moved to a production release. 

By evaluating the source code directly, developers can locate hidden vulnerabilities that perimeter defenses—like traditional network firewalls—might fail to intercept.This project demonstrates a practical secure code review pipeline, bridging software engineering and application security through static analysis and code hardening.

---

## 2. Project Objectives
The primary technical objectives of this engineering lifecycle lab include:
* **Framework Integration:** Construct a functional web application pipeline using the lightweight Python Flask framework to handle client-side routing.
* **Database Interface Evaluation:** Implement a localized relational database interface using the SQLite database engine to evaluate data-driven interaction pathways.
* **Static Application Security Testing (SAST):** Deploy automated SAST tooling to scan code logic dynamically for software vulnerabilities.
* **Security Hardening & Remediation:** Apply core secure development principles—specifically database query parameterization and server configuration hardening—to entirely eliminate uncovered security risks.

---

## 3. Environment Setup & Tooling

### Prerequisites
* **Python Integrated Environment:** Configured with the **Pylance extension** inside Visual Studio Code to provide intelligent code completion, syntax highlighting, error detection, and enhanced code analysis during manual audits.
***Core Dependencies:** Python Flask framework and SQLite database engine.
* **Automated Guardrails:** Static Application Security Testing (SAST) utilities (such as `Bandit` for Python, `SonarQube`, or `Semgrep`) embedded into the workflow to automatically flag risky methodologies or insecure paths.

### Installation & Initialization
The workspace environment can be verified and prepared using the terminal console:

4. Vulnerability Audit & Secure Remediation ArchitectureDuring the code review process, critical software design vulnerabilities were identified and refactored using defensive programming practices:  
4.1 SQL Injection (SQLi) FlawsThe Vulnerability: Relying on unvalidated or raw user inputs concatenated directly into SQLite database query strings, allowing attackers to bypass authentication or manipulate database logic.  Secure Remediation: Implemented Database Query Parameterization (Prepared Statements). This structures the code so that user inputs are treated strictly as data variables, completely isolating them from executable SQL command syntax.  

4.2 Improper Error Handling & Information DisclosureThe Vulnerability: Allowing the backend to leak verbose debugging data, raw stack traces, or internal system configurations directly to the user interface during application or database exceptions.  Risk Impact: This provides threat actors with an explicit map of the environment infrastructure to craft targeted exploits.  Secure Remediation: Restructured error handling routines using robust error-trapping blocks. The application now suppresses raw traces and returns a user-friendly, generic error message to the client while securely logging detailed technical data to private internal server logs.  

5. Defensive Software Engineering BlueprintTo maintain project integrity and prevent the future introduction of security flaws, the following production rules are established across this workspace:Principle of Least Privilege (Service Privilege Restriction): Ensure database connection accounts or service workers possess only the bare minimum permissions required to execute their specific task. Application-side endpoints should never connect using database root or admin privileges.  Continuous Build Pipeline Integration: Integrate automated SAST linters directly into the continuous integration/continuous deployment (CI/CD) workflows to catch high-risk methodologies before pull requests are permitted to merge.  Software Composition Analysis (SCA): Run automated dependency scanners to parse framework libraries against known CVE catalogs, catching obsolete or unpatched third-party packages before production exposure.
   
6. Deliverables Includedsecure_review_report.md: Deep dive documentation mapping audited scripts, vulnerability severity metrics, and structural code refactoring solutions.  entry_point.py / app.py: Hardened Python Flask script running parameterization and safe exception handling overrides
