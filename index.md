---

layout: col-sidebar
title: OWASP DevGuard
tags: devguard flawfix vulnerability-management sbom cve cwe
level: 2
type: 
pitch: A usable central vulnerability management system for developers and security teams.

---

## Mission

DevGuard is built by developers, for developers, aiming to simplify the complex world of vulnerability management. Our goal is to integrate security seamlessly into the software development lifecycle, ensuring that security practices are accessible and efficient for everyone, regardless of their security expertise.

### The problem we solve

Identifying and managing software vulnerabilities is an increasingly critical challenge. Developers often face security issues without the proper training or tools that fit into their everyday workflows. DevGuard is a developer-centered software designed to provide simple, modern solutions for vulnerability detection and management, compliant with common security frameworks.

In 2023 alone, cyberattacks caused approximately 206 billion euros in damage only in Germany. Many of these attacks exploited software vulnerabilities. With agile and DevOps methodologies becoming standard, the need for integrating security into the development process has never been greater. We aim to fill this gap with DevGuard, offering a seamless integration of vulnerability management into development workflows.

#### Prioritizing Vulnerabilities

Not all vulnerabilities pose the same level of risk to your project. Effective prioritization of vulnerabilities is crucial to ensure that resources are focused on addressing the most critical issues. DevGuard helps you focus on what truly matters by providing risk assessments based on CVSS scores, exploit availability (ExploitDB), and real-world threat data (EPSS). This approach converts a generic `--exit-code 1 --severity CRITICAL` (like trivy has it) to a more practical `--exit-code 1 --risk CRITICAL` strategy, ensuring that you address vulnerabilities that could have the most significant impact on your software.

To further illustrate the importance of prioritizing vulnerabilities, consider our Sankey diagram, which demonstrates how many high CVSS vulnerabilities are reassessed and reprioritized. The diagram shows that a significant portion of these vulnerabilities are mapped to EPSS scores in the 0-10% range, indicating a lower likelihood of exploitation. This visual representation underscores the necessity of a nuanced approach to vulnerability management, where not all "critical" CVEs are treated equally, but rather prioritized based on their actual risk.

<img src="assets/images/sankey.png">
<p>
    <em>Sankey diagram showing the CVSS Base-Score and the adjusted score after applying threat intelligence and the application security requirements to the cvss calculation. The scores then get mapped to their corresponding EPSS (Exploit prediction scoring system).</em>
</p>

## Key Features

1. **Developer-Centric Integration:** DevGuard fits naturally into your existing CI/CD workflows, reducing friction and enhancing productivity. It supports the OWASP DevSecOps pipeline, offering tools (we just reuse open source tools but provide a simplified wrapper cli) for secret scanning (coming soon), SAST (coming soon), SCA, IaC scanning (coming soon), container scanning (coming soon), and DAST (coming soon).
2. **Automated Security Monitoring:** Continuous monitoring using Software Bill of Materials (SBOMs) to keep your projects secure.
3. **Risk Assessment:** Automatically assesses and prioritizes risks to help you address the most critical vulnerabilities first — no really, we do this pragmatically and automate where possible! (Our base: CVSS, exploitdb, EPSS)
4. **Compliance:** Ensures your projects meet security standards like ISO/IEC 27001 and PCI-DSS.
5. **Security and confidentiality:** We prioritize the security of this software! In an expansion stage and in cooperation with research institutions, we want to make confidential data processing usable for the secure handling of sensitive information (confidential computing).

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Understanding the OWASP DevSecOps Pipeline

> DevGuard aims to accompany developers in implementing the OWASP-DevSecOps pipeline in the best way possible, without requiring extensive cybersecurity knowledge. We plan provide a wrapper CLI to a curated list of scanners for different stages and seamless integration with the management backend, ensuring that security is integrated smoothly into the development workflow.

<img src="assets/images/devsecops-pipeline.png">

The OWASP DevSecOps pipeline integrates security practices into the DevOps process, ensuring that security is an integral part of the software development lifecycle. The pipeline includes the following key stages and practices:

### Secret Scanning (Coming Soon)

- Detects and manages sensitive information such as API keys and passwords that may be accidentally committed to the codebase.
- Helps prevent security breaches by identifying secrets early in the development process.

### Software Composition Analysis (SCA)

- Utilizes Software Bill of Materials (SBOMs) to conduct thorough software composition analysis.
- Helps in identifying and managing dependencies and their associated vulnerabilities.
- Prioritizes CVEs using various threat intelligence sources such as EPSS and ExploitDB.
- Focuses on the real risk posed by vulnerabilities, converting "—fail-on-critical" to "—fail-on-real-risk-critical".
- Syncs with the National Vulnerability Database (NVD) to ensure up-to-date information on vulnerabilities.

#### Crowdsourced Vulnerability Management

- Supports a crowdsourced approach to vulnerability management.
- If a dependency (A) has another dependency (B) with a CVE, users can consult A to determine the relevance of B's CVE to their project.
- Allows marking vulnerabilities as false positives, sharing this information across the user community for the same A -> B relationship.

### Static Application Security Testing (SAST) (Coming Soon)

- Analyzes source code to identify security vulnerabilities early in the development process.
- Provides developers with actionable insights to fix vulnerabilities before they become critical issues.


### Infrastructure as Code (IaC) Scanning (Coming Soon)

- Ensures that infrastructure definitions and configurations adhere to security best practices.
- Detects misconfigurations and vulnerabilities in IaC templates early in the development cycle.

### Container Scanning (Coming Soon)

- Scans container images for vulnerabilities, ensuring that the containerized applications are secure.
- Helps maintain the security of containerized environments by identifying and mitigating risks in container images.

### Dynamic Application Security Testing (DAST) (Coming Soon)

- Tests running applications to identify vulnerabilities that may not be visible in the source code.
- Simulates real-world attacks to uncover potential security weaknesses in live environments.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Joint vulnerability management - the strength of exchange

Based on emerging standards such as the Vulnerability Exploitability eXchange (VEX) and our goal of increasing overall software security through the dissemination of DevGuard, we want to make expert information available from the source.  

![Depiction of a dependency graph with vulnerabilities (CVEs) of a software and the integration of VEX and crowd-based information as well as the DevGuard standard management process. The representation is ASCII art.](./assets/images/vex-crowd-ascii.png)

### Vulnerability Exploitability eXchange (VEX) 

> “The goal of Vulnerability Exploitability eXchange (VEX) is to allow a software supplier or other parties to assert the status of specific vulnerabilities in a particular product.” ([CISA](https://www.cisa.gov/sites/default/files/publications/VEX_Use_Cases_Apr22.pdf))

VEX is an advanced form of security advisory that provides several key advantages over conventional methods:

1. Machine Readability
2. Enhanced SBOM Integration
3. Automation Support

For instance, consider an open-source project, “XY-Example,” which detects a vulnerability through a dependency. Upon closer inspection, the developers determine that the specific conditions required to exploit this vulnerability are not present in their software. This expert assessment can be recorded and disseminated through VEX, making it accessible and usable for all users of the “XY-Example” software. This exchange of vulnerability information drastically reduces the effort required for vulnerability management, as users can rely on expert evaluations to determine their exposure to potential threats.

### Crowdsourced

If the VEX is not available and in its addition, we can also use the knowledge of the crowd. If enough users confirm that a vulnerability in a software is not relevant, we can make this information available to others as a preset. In this way, we expand the foundation for joint vulnerability management and make it even easier.
