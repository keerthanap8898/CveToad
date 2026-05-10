# 16. Recommended canonical data model coverage

A complete vulnerability impact system should be able to ingest or derive the following fields.
### 16.1 Vulnerability identity
| Sl. # | Title | Link(s) | Access / Cost | Relevance | Notes & POIs |
|---:|---|---|---|---|---|
| 1 | CVE ID | [github.com/CVEProject/cvelistV5](https://github.com/CVEProject/cvelistV5), [www.cve.org](https://www.cve.org/) | Free public | Canonical vulnerability identifier. | Not all advisories have CVEs immediately. |
| 2 | GHSA ID | [github.com/advisories](https://github.com/advisories) | Free public | GitHub Security Advisory identifier. | May exist without CVE. |
| 3 | OSV ID | [osv.dev](https://osv.dev/) | Free public | OSV vulnerability identifier. | Links package-specific affectedness & aliases. |
| 4 | Vendor advisory ID | [msrc.microsoft.com/update-guide](https://msrc.microsoft.com/update-guide), [www.oracle.com/security-alerts](https://www.oracle.com/security-alerts/) | Mostly free public; some support details may require entitlement | Vendor-specific advisory identifier. | Often most authoritative for product-specific truth. |
| 5 | CWE ID | [cwe.mitre.org](https://cwe.mitre.org/) | Free public | Weakness class identifier. | Quality of mapping varies. |
| 6 | CAPEC ID | [capec.mitre.org](https://capec.mitre.org/) | Free public | Attack-pattern identifier. | Useful for attack mechanism mapping. |
| 7 | ATT&CK technique ID | [attack.mitre.org/matrices/enterprise](https://attack.mitre.org/matrices/enterprise/) | Free public | Adversary technique identifier. | Useful for detection/response mapping. |
| 8 | ATLAS technique ID | [atlas.mitre.org/techniques](https://atlas.mitre.org/techniques) | Free public | AI/ML adversary technique identifier. | Relevant for AI systems. |
| 9 | Alias graph | [github.com/CVEProject/cvelistV5](https://github.com/CVEProject/cvelistV5), [github.com/advisories](https://github.com/advisories), [osv.dev](https://osv.dev/) | Free public | Maps CVE/GHSA/OSV/vendor aliases. | Crucial for deduplication & correlation. |
### 16.2 Affectedness
| Sl. # | Title | Link(s) | Access / Cost | Relevance | Notes & POIs |
|---:|---|---|---|---|---|
| 1 | Product name | [nvd.nist.gov/products/cpe](https://nvd.nist.gov/products/cpe) | Free public | Identifies vulnerable products. | Normalize against CPE/PURL/vendor data. |
| 2 | Vendor | [www.cve.org](https://www.cve.org/) | Free public | Vendor/product attribution. | Vendor naming can differ across sources. |
| 3 | CPE | [nvd.nist.gov/developers/products](https://nvd.nist.gov/developers/products) | Free public; optional free API key for higher rate limits | Product/platform matching. | Imprecise for many OSS packages. |
| 4 | PURL | [github.com/package-url/purl-spec](https://github.com/package-url/purl-spec) | Free / open-source | Package identity. | Prefer for package ecosystem matching. |
| 5 | Package ecosystem | [osv.dev/list](https://osv.dev/list) | Free public | Defines package namespace & version rules. | Version semantics are ecosystem-specific. |
| 6 | Package name | [deps.dev](https://deps.dev/) | Free public | Dependency identity. | Normalize casing & namespace rules. |
| 7 | Affected version range | [ossf.github.io/osv-schema](https://ossf.github.io/osv-schema/) | Free public / open-source | Expresses vulnerable versions. | Range interpretation must respect ecosystem semantics. |
| 8 | Fixed version | [github.com/advisories](https://github.com/advisories), [osv.dev](https://osv.dev/) | Free public | Remediation target. | Distro fixed versions may differ due to backports. |
| 9 | Introduced version / commit | [ossf.github.io/osv-schema](https://ossf.github.io/osv-schema/) | Free public / open-source | Determines when vulnerability entered codebase. | Not always available. |
| 10 | Last affected version | [ossf.github.io/osv-schema](https://ossf.github.io/osv-schema/) | Free public / open-source | Helps determine affected version bounds. | Validate with vendor feeds. |
| 11 | Backport status | [access.redhat.com/security/data](https://access.redhat.com/security/data), [security-tracker.debian.org](https://security-tracker.debian.org/), [ubuntu.com/security/cves](https://ubuntu.com/security/cves) | Mostly free public; some Red Hat support details may require subscription | Determines if a distro package is patched despite upstream version appearing vulnerable. | Essential for reducing false positives. |
| 12 | VEX status | [github.com/openvex/spec](https://github.com/openvex/spec), [www.csaf.io](https://www.csaf.io/) | Free / open-source standards | Represents affected, not affected, fixed, or under investigation. | Preserve justification & author provenance. |
| 13 | Justification for not affected | [github.com/openvex/spec](https://github.com/openvex/spec) | Free / open-source | Explains why a product is not affected. | Key for trust & auditability. |
| 14 | Distro/package release channel | [packages.fedoraproject.org](https://packages.fedoraproject.org/), [pkgs.alpinelinux.org/packages](https://pkgs.alpinelinux.org/packages) | Free public | Tracks package release stream. | Channel differences can affect fix availability. |
### 16.3 Severity & exploitability
| Sl. # | Title | Link(s) | Access / Cost | Relevance | Notes & POIs |
|---:|---|---|---|---|---|
| 1 | CVSS v2/v3/v4 vector | [www.first.org/cvss](https://www.first.org/cvss/) | Free public | Structured severity vector. | Use vector, not only numeric score. |
| 2 | CVSS base/temporal/environmental score | [nvd.nist.gov/vuln-metrics/cvss](https://nvd.nist.gov/vuln-metrics/cvss) | Free public | Severity scoring. | Environmental score should be computed with local context. |
| 3 | EPSS score | [www.first.org/epss](https://www.first.org/epss/) | Free public data/API | Exploit likelihood. | Temporal; store score date. |
| 4 | EPSS percentile | [www.first.org/epss/data_stats](https://www.first.org/epss/data_stats) | Free public data downloads | Relative exploit-likelihood ranking. | Useful for prioritization across backlog. |
| 5 | KEV membership | [www.cisa.gov/sites/default/files/feeds/known_exploited_vulnerabilities.json](https://www.cisa.gov/sites/default/files/feeds/known_exploited_vulnerabilities.json) | Free public feed | Known exploited vulnerability marker. | Strong exploitation evidence. |
| 6 | KEV date added | [www.cisa.gov/sites/default/files/feeds/known_exploited_vulnerabilities.json](https://www.cisa.gov/sites/default/files/feeds/known_exploited_vulnerabilities.json) | Free public feed | Temporal exploitation/prioritization signal. | Use for SLA & trend analysis. |
| 7 | Known ransomware usage | [www.ransomware.live](https://www.ransomware.live/) | Free public | Ransomware exploitation context. | Attribution & mapping quality vary. |
| 8 | Public exploit available | [www.exploit-db.com](https://www.exploit-db.com/) | Free public | PoC/exploit availability. | Verify reliability & version applicability. |
| 9 | Metasploit module available | [github.com/rapid7/metasploit-framework/tree/master/modules/exploits](https://github.com/rapid7/metasploit-framework/tree/master/modules/exploits) | Free / open-source | Weaponized exploit implementation. | Stronger than generic PoC signal. |
| 10 | Nuclei template available | [github.com/projectdiscovery/nuclei-templates](https://github.com/projectdiscovery/nuclei-templates) | Free / open-source | Detection template availability. | Indicates detectable exposure, not confirmed vulnerability. |
| 11 | GreyNoise observed scanning | [viz.greynoise.io](https://viz.greynoise.io/) | Free tier / paid plans | Internet scanning/exploitation telemetry. | Helps prioritize exposed services. |
| 12 | Shadowserver observed exposure | [dashboard.shadowserver.org](https://dashboard.shadowserver.org/) | Free for eligible organizations; registration may be required | Internet-scale exposure telemetry. | Access may require registration/eligibility. |
| 13 | CISA SSVC decision points | [github.com/cisagov/vulnrichment](https://github.com/cisagov/vulnrichment) | Free public GitHub repo | Decision support enrichment. | Useful for prioritization workflows. |
| 14 | Vendor exploitation status | [msrc.microsoft.com/update-guide](https://msrc.microsoft.com/update-guide), [security.paloaltonetworks.com](https://security.paloaltonetworks.com/), [support.apple.com/en-us/100100](https://support.apple.com/en-us/100100) | Free public | Vendor-provided exploitation notes. | Time-sensitive & product-specific. |
| 15 | Patch availability | [access.redhat.com/security/data](https://access.redhat.com/security/data), [security-tracker.debian.org](https://security-tracker.debian.org/), [ubuntu.com/security/notices](https://ubuntu.com/security/notices) | Mostly free public; some vendor support details may require subscription | Determines if a fix exists. | Patch availability varies by release stream. |
| 16 | Workaround availability | [www.cisa.gov/cybersecurity-advisories](https://www.cisa.gov/cybersecurity-advisories), [www.kb.cert.org/vuls](https://www.kb.cert.org/vuls/) | Free public | Temporary mitigation when patching is not available. | Workarounds may reduce but not eliminate risk. |
### 16.4 Environmental impact
| Sl. # | Title | Link(s) | Access / Cost | Relevance | Notes & POIs |
|---:|---|---|---|---|---|
| 1 | Asset criticality | [www.cisecurity.org/controls](https://www.cisecurity.org/controls) | Free public | Business/system importance affects risk. | Must come from internal asset inventory. |
| 2 | Internet exposure | [search.censys.io](https://search.censys.io/), [www.shodan.io](https://www.shodan.io/) | Free tiers / paid plans | Determines external exploitability surface. | External scan data may be incomplete or stale. |
| 3 | Network reachability | [nmap.org](https://nmap.org/) | Free / open-source | Determines whether an exploit path exists. | Internal network context required. |
| 4 | Authentication required | [www.first.org/cvss](https://www.first.org/cvss/) | Free public | Impacts exploitability. | CVSS may not capture local compensating controls. |
| 5 | Privilege required | [www.first.org/cvss](https://www.first.org/cvss/) | Free public | Impacts exploitability & blast radius. | Validate with product configuration. |
| 6 | User interaction required | [www.first.org/cvss](https://www.first.org/cvss/) | Free public | Impacts exploitability conditions. | User interaction can be bypassed in some real-world chains. |
| 7 | Exploit preconditions | [googleprojectzero.blogspot.com](https://googleprojectzero.blogspot.com/), [www.kb.cert.org/vuls](https://www.kb.cert.org/vuls/) | Free public | Defines required configuration or state. | Crucial for false-positive reduction. |
| 8 | Data sensitivity | [www.cisecurity.org/controls](https://www.cisecurity.org/controls) | Free public | Determines business impact. | Internal classification required. |
| 9 | Compensating controls | [public.cyber.mil/stigs](https://public.cyber.mil/stigs/), [www.cisecurity.org/cis-benchmarks](https://www.cisecurity.org/cis-benchmarks) | Free public; CIS benchmarks may require free registration | Controls can reduce practical exploitability. | Document assumptions & evidence. |
| 10 | Runtime configuration | [docs.dependencytrack.org/datasources/overview](https://docs.dependencytrack.org/datasources/overview/) | Free public docs | Enabled features/modules influence affectedness. | Scanner package matches alone can over-report. |
| 11 | Feature/module enabled | [github.com/openvex/spec](https://github.com/openvex/spec) | Free / open-source | VEX not-affected reasoning may depend on disabled code paths. | Requires product/runtime evidence. |
| 12 | Cloud account/project/environment | [github.com/prowler-cloud/prowler](https://github.com/prowler-cloud/prowler) | Free / open-source core; commercial products separate | Cloud context affects exposure & blast radius. | Join vulnerability data with cloud inventory. |
| 13 | Blast radius | [github.com/salesforce/cloudsplaining](https://github.com/salesforce/cloudsplaining) | Free / open-source | Privilege & dependency spread determine impact. | Requires IAM, network, & data-flow context. |
| 14 | Business process ownership | [www.cisecurity.org/controls](https://www.cisecurity.org/controls) | Free public | Ownership determines remediation accountability. | Internal data source required. |
### 16.5 Detection & remediation
| Sl. # | Title | Link(s) | Access / Cost | Relevance | Notes & POIs |
|---:|---|---|---|---|---|
| 1 | Scanner finding ID | [dependencytrack.org](https://dependencytrack.org/), [github.com/anchore/grype](https://github.com/anchore/grype), [trivy.dev/docs/latest/scanner/vulnerability](https://trivy.dev/docs/latest/scanner/vulnerability/) | Free / open-source core tools; commercial support/products may exist | Scanner-specific finding identity. | Preserve source scanner & version for reproducibility. |
| 2 | Detection method | [codeql.github.com](https://codeql.github.com/), [github.com/projectdiscovery/nuclei](https://github.com/projectdiscovery/nuclei), [owasp.org/www-project-top-ten](https://owasp.org/www-project-top-ten/) | Mixed: free/open-source, with some commercial tiers | Indicates whether finding came from SBOM, CPE, package manager, SAST, DAST, IaC, or runtime telemetry. | Different methods have different false-positive characteristics. |
| 3 | Confidence | [github.com/openvex/spec](https://github.com/openvex/spec) | Free / open-source | Confidence helps rank findings. | Use evidence & source provenance to compute confidence. |
| 4 | False-positive reason | [github.com/openvex/spec](https://github.com/openvex/spec) | Free / open-source | Captures why a match is not actually exploitable or affected. | VEX justification is key for auditability. |
| 5 | Fix version | [github.com/advisories](https://github.com/advisories), [osv.dev](https://osv.dev/) | Free public | Remediation target version. | Distro fixed versions may differ due to backports. |
| 6 | Patch advisory | [access.redhat.com/security/data](https://access.redhat.com/security/data), [ubuntu.com/security/notices](https://ubuntu.com/security/notices), [www.debian.org/security](https://www.debian.org/security/) | Mostly free public; some Red Hat support details may require subscription | Links vulnerability to vendor patch guidance. | Use vendor patch source for production remediation. |
| 7 | Mitigation | [www.cisa.gov/cybersecurity-advisories](https://www.cisa.gov/cybersecurity-advisories), [www.kb.cert.org/vuls](https://www.kb.cert.org/vuls/) | Free public | Temporary or compensating controls. | Mitigations may be partial & context-specific. |
| 8 | Workaround | [www.kb.cert.org/vuls](https://www.kb.cert.org/vuls/) | Free public | Alternative remediation when patch unavailable. | Track expiration & replacement by patch. |
| 9 | Exploit detection signatures | [github.com/SigmaHQ/sigma](https://github.com/SigmaHQ/sigma), [github.com/VirusTotal/yara](https://github.com/VirusTotal/yara), [github.com/projectdiscovery/nuclei-templates](https://github.com/projectdiscovery/nuclei-templates) | Free / open-source public GitHub repos | Detection content for exploit attempts or compromise. | Validate signatures in environment before high-confidence alerting. |
| 10 | Regression test | [github.com/google/oss-fuzz](https://github.com/google/oss-fuzz), [google.github.io/oss-fuzz](https://google.github.io/oss-fuzz/) | Free / open-source; OSS-Fuzz service for eligible OSS projects | Tests that a vulnerability class or bug does not reappear. | Useful for secure SDLC feedback loops. |
| 11 | Verification command | [github.com/anchore/grype](https://github.com/anchore/grype), [github.com/aquasecurity/trivy-db](https://github.com/aquasecurity/trivy-db), [github.com/projectdiscovery/nuclei](https://github.com/projectdiscovery/nuclei) | Free / open-source | Command/procedure to verify vulnerability or remediation state. | Required for repeatable remediation closure. |
| 12 | SLA due date | [www.cisa.gov/news-events/directives/bod-22-01-reducing-significant-risk-known-exploited-vulnerabilities](https://www.cisa.gov/news-events/directives/bod-22-01-reducing-significant-risk-known-exploited-vulnerabilities), [www.cisa.gov/sites/default/files/feeds/known_exploited_vulnerabilities.json](https://www.cisa.gov/sites/default/files/feeds/known_exploited_vulnerabilities.json) | Free public | Remediation deadline derived from KEV, severity, exposure, policy, or business context. | SLA should be policy-driven & context-aware. |
> #### [*Back to **`Index`***](#index)
---
