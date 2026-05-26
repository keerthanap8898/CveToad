# 18. Compliance, baseline configuration, software assurance & exposure severity standards
These are not vulnerability feeds, but they help assess impact, control failure, configuration exposure, & exploitability in a given environment.

## 18.1 Security configuration & benchmarks

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **CIS Benchmarks**<br><br>**`Link(s)`:** [www.cisecurity.org/cis-benchmarks](https://www.cisecurity.org/cis-benchmarks)<br><br>**`Access / Cost`:** Free with registration for many PDFs; commercial CIS tools/membership available | **`Relevance`:** Secure configuration benchmarks.<br><br>**`Notes & POIs`:** Useful for environmental risk scoring & hardening validation. |
| 2 | **CIS Controls**<br><br>**`Link(s)`:** [www.cisecurity.org/controls](https://www.cisecurity.org/controls)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Security control framework.<br><br>**`Notes & POIs`:** Useful for vulnerability management program alignment. |
| 3 | **NIST National Checklist Program**<br><br>**`Link(s)`:** [ncp.nist.gov](https://ncp.nist.gov/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Repository of security configuration checklists.<br><br>**`Notes & POIs`:** Useful for baseline configuration assessment. |
| 4 | **DISA STIGs**<br><br>**`Link(s)`:** [public.cyber.mil/stigs](https://public.cyber.mil/stigs/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Security Technical Implementation Guides.<br><br>**`Notes & POIs`:** Important for government/defense compliance. |
| 5 | **OpenSCAP**<br><br>**`Link(s)`:** [www.open-scap.org](https://www.open-scap.org/)<br><br>**`Access / Cost`:** Free / open-source | **`Relevance`:** SCAP tooling for compliance scanning.<br><br>**`Notes & POIs`:** Useful for host-level configuration scanning. |

| 6 | SCAP Security Guide | [github.com/ComplianceAsCode/content](https://github.com/ComplianceAsCode/content) | Free / open-source public GitHub repo | ComplianceAsCode content for SCAP profiles. | Useful for policy-as-code & baseline validation. |

## 18.2 Cloud configuration posture

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **Prowler - AWS/Azure/GCP/Kubernetes**<br><br>**`Link(s)`:** [github.com/prowler-cloud/prowler](https://github.com/prowler-cloud/prowler)<br><br>**`Access / Cost`:** Free / open-source core; commercial product available | **`Relevance`:** Cloud & Kubernetes security posture scanning.<br><br>**`Notes & POIs`:** Useful for environmental exposure & misconfiguration risk. |
| 2 | **CloudSplaining**<br><br>**`Link(s)`:** [github.com/salesforce/cloudsplaining](https://github.com/salesforce/cloudsplaining)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** AWS IAM policy risk analysis.<br><br>**`Notes & POIs`:** Useful for blast-radius & privilege exposure context. |
| 3 | **ScoutSuite**<br><br>**`Link(s)`:** [github.com/nccgroup/ScoutSuite](https://github.com/nccgroup/ScoutSuite)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** Multi-cloud security auditing.<br><br>**`Notes & POIs`:** Useful for cloud misconfiguration assessment. |
| 4 | **Steampipe mods**<br><br>**`Link(s)`:** [hub.steampipe.io/mods](https://hub.steampipe.io/mods)<br><br>**`Access / Cost`:** Free/open-source mods; commercial Turbot/Steampipe offerings separate | **`Relevance`:** SQL-based cloud/security posture checks.<br><br>**`Notes & POIs`:** Useful for custom exposure queries. |
| 5 | **Cloud Custodian**<br><br>**`Link(s)`:** [cloudcustodian.io](https://cloudcustodian.io/)<br><br>**`Access / Cost`:** Free / open-source | **`Relevance`:** Cloud governance & policy automation.<br><br>**`Notes & POIs`:** Useful for remediation automation. |
| 6 | **Kubernetes CIS benchmark**<br><br>**`Link(s)`:** [www.cisecurity.org/benchmark/kubernetes](https://www.cisecurity.org/benchmark/kubernetes)<br><br>**`Access / Cost`:** Free with registration for benchmark PDFs; commercial CIS tools/membership available | **`Relevance`:** Kubernetes configuration benchmark.<br><br>**`Notes & POIs`:** Useful for cluster hardening & exposure scoring. |
| 7 | **kube-bench**<br><br>**`Link(s)`:** [github.com/aquasecurity/kube-bench](https://github.com/aquasecurity/kube-bench)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** Kubernetes CIS benchmark scanner.<br><br>**`Notes & POIs`:** Useful for automated cluster benchmark checks. |
| 8 | **kube-hunter**<br><br>**`Link(s)`:** [github.com/aquasecurity/kube-hunter](https://github.com/aquasecurity/kube-hunter)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** Kubernetes penetration testing tool.<br><br>**`Notes & POIs`:** Use only in authorized environments. |

## 18.3 Software assurance, secure development, acquisition & NIST publication libraries

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **CISA Software Acquisition Guide**<br><br>**`Link(s)`:** [cisa.gov/resources-tools/resources/software-acquisition-guide-government-enterprise-consumers-software-assurance-cyber-supply-chain](https://www.cisa.gov/resources-tools/resources/software-acquisition-guide-government-enterprise-consumers-software-assurance-cyber-supply-chain)<br><br>**`Access / Cost`:** Free public; CISA pages may bot-block automated fetchers | **`Relevance`:** Software assurance & cyber supply-chain acquisition guidance for enterprise/government consumers.<br><br>**`Notes & POIs`:** Not a vulnerability feed, but useful for procurement, assurance, & supplier-risk context. |
| 2 | **NIST Secure Software Development Framework - SSDF**<br><br>**`Link(s)`:** [csrc.nist.gov/projects/ssdf](https://csrc.nist.gov/projects/ssdf)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Secure development practice framework for reducing software vulnerabilities.<br><br>**`Notes & POIs`:** Useful for SDLC controls, attestation, & vulnerability-prevention context. |
| 3 | **NIST FIPS publications**<br><br>**`Link(s)`:** [csrc.nist.gov/publications/fips](https://csrc.nist.gov/publications/fips)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Federal Information Processing Standards.<br><br>**`Notes & POIs`:** Compliance/standards reference, not vuln feed. |
| 4 | **NIST Special Publications root**<br><br>**`Link(s)`:** [csrc.nist.gov/publications/sp](https://csrc.nist.gov/publications/sp)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** NIST Special Publication library.<br><br>**`Notes & POIs`:** Useful for standards research & compliance mapping. |
| 5 | **NIST SP 800 series**<br><br>**`Link(s)`:** [csrc.nist.gov/publications/sp800](https://csrc.nist.gov/publications/sp800)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Computer/security guidance series.<br><br>**`Notes & POIs`:** High-value for security-control, risk, identity, cryptography, & vulnerability-management context. |
| 6 | **NIST SP 1800 series**<br><br>**`Link(s)`:** [csrc.nist.gov/publications/sp1800](https://csrc.nist.gov/publications/sp1800)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** NIST Cybersecurity Practice Guides.<br><br>**`Notes & POIs`:** Practical implementation patterns & reference architectures. |
| 7 | **NIST SP 500 series**<br><br>**`Link(s)`:** [csrc.nist.gov/publications/sp500](https://csrc.nist.gov/publications/sp500)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Information technology publications.<br><br>**`Notes & POIs`:** Useful for supporting standards & technical guidance. |
| 8 | **NIST AI publication search**<br><br>**`Link(s)`:** [csrc.nist.gov/publications/search?sortBy-lg=relevance&viewMode-lg=brief&ipp-lg=50&status-lg=Final%2CDraft&series-lg=AI](https://csrc.nist.gov/publications/search?sortBy-lg=relevance&viewMode-lg=brief&ipp-lg=50&status-lg=Final%2CDraft&series-lg=AI)<br><br>**`Access / Cost`:** Free public filtered search | **`Relevance`:** NIST AI-series publication discovery.<br><br>**`Notes & POIs`:** Filtered search URL; cite individual publications separately when used for evidence. |
| 9 | **LangGuard SCOPE MCP**<br><br>**`Link(s)`:** [scope-mcp.langguard.ai](https://scope-mcp.langguard.ai)<br><br>**`Access / Cost`:** Public web tool/service; terms may apply | **`Relevance`:** AI/agent compliance & pre-flight risk evaluation for tool use.<br><br>**`Notes & POIs`:** Useful for AI/agent security governance, not vulnerability source ingestion. |
| 10 | **FIRST 2026 papers**<br><br>**`Link(s)`:** [www.first.org/resources/papers/2026](https://www.first.org/resources/papers/2026)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** FIRST papers & security response knowledge base.<br><br>**`Notes & POIs`:** Research/training context, not canonical vulnerability data. |
| 11 | **FIRST VulnCon 2026 program**<br><br>**`Link(s)`:** [first.org/conference/vulncon26/program](https://www.first.org/conference/vulncon26/program)<br><br>**`Access / Cost`:** Free public conference page | **`Relevance`:** Vulnerability management & disclosure conference content.<br><br>**`Notes & POIs`:** Useful for user stories, emerging practices, & CVE/PSIRT ecosystem context. |

> 
> #### [*Back to **`Index`***](#index)
---

## Discussion

This chapter section keeps the latest table structure, source titles, access/cost fields, relevance notes, & operational notes from the source inventory. Review the table entries as ingestion candidates, then validate source freshness, licensing, authentication requirements, & link-check behavior before production use.

---

#### [Back to Index](../../01-index.md)
