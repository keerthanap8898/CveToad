# CveToad Vulnerability Management Source Inventory

#### A consolidated super-set vulnerability-management source inventory for assessing impact, severity, exploitability, exposure, affectedness, prioritization, & remediation of vulnerabilities in technical systems.


### `License`
>     Copyright Ⓒ 2025  Keerthana Purushotham <keep.consult@proton.me>.
>     Licensed under the GNU AGPL v3. See LICENSE for details.
>   [*see license*](https://github.com/keerthanap8898/CveToad/blob/main/LICENSE)

#### Note:
> *Some vendor/security pages change URLs over time, so treat this as a high-coverage baseline rather than a mathematically exhaustive list of every possible vulnerability source.*

---

## Index

- [0. Corrections & normalization notes](#0-corrections--normalization-notes)
- [1. Canonical vulnerability identifiers, CVE records & schemas](#1-canonical-vulnerability-identifiers-cve-records--schemas)
  - [1.1 CVE Program - canonical CVE identity](#11-cve-program---canonical-cve-identity)
  - [1.2 NVD - CVE enrichment, CPE matching, CVSS & configurations](#12-nvd---cve-enrichment-cpe-matching-cvss--configurations)
  - [1.3 Optional CVE meta-mirrors / commercial-community enrichments](#13-optional-cve-meta-mirrors--commercial-community-enrichments)
- [2. Open-source vulnerability databases & package advisory sources](#2-open-source-vulnerability-databases--package-advisory-sources)
  - [2.1 OSV ecosystem](#21-osv-ecosystem)
  - [2.2 GitHub Advisory Database](#22-github-advisory-database)
  - [2.3 Language & package ecosystem advisory databases](#23-language--package-ecosystem-advisory-databases)
- [3. Exploitation, prioritization, severity & risk scoring](#3-exploitation-prioritization-severity--risk-scoring)
  - [3.1 Known exploited vulnerability sources](#31-known-exploited-vulnerability-sources)
  - [3.2 Exploit prediction & scoring](#32-exploit-prediction--scoring)
  - [3.3 Decision-support frameworks](#33-decision-support-frameworks)
  - [3.4 Public exploit / proof-of-concept / weaponization signals](#34-public-exploit--proof-of-concept--weaponization-signals)
- [4. CWE, CAPEC, ATT&CK, ATLAS & weakness-to-attack mapping](#4-cwe-capec-attck-atlas--weakness-to-attack-mapping)
  - [4.1 CWE - Common Weakness Enumeration](#41-cwe---common-weakness-enumeration)
  - [4.2 CAPEC - attack patterns](#42-capec---attack-patterns)
  - [4.3 MITRE ATT&CK](#43-mitre-attck)
  - [4.4 AI/ML-specific adversary frameworks](#44-aiml-specific-adversary-frameworks)
- [5. Vendor, OS, distribution, container & package affectedness feeds](#5-vendor-os-distribution-container--package-affectedness-feeds)
  - [5.1 Scanner-oriented aggregators & vulnerability DB builders](#51-scanner-oriented-aggregators--vulnerability-db-builders)
  - [5.2 Red Hat / RHEL / CentOS Stream](#52-red-hat--rhel--centos-stream)
  - [5.3 Debian](#53-debian)
  - [5.4 Ubuntu / Canonical](#54-ubuntu--canonical)
  - [5.5 Alpine](#55-alpine)
  - [5.6 SUSE / openSUSE](#56-suse--opensuse)
  - [5.7 Oracle Linux](#57-oracle-linux)
  - [5.8 Amazon Linux](#58-amazon-linux)
  - [5.9 Fedora, AlmaLinux, Rocky, Arch, Gentoo](#59-fedora-almalinux-rocky-arch-gentoo)
  - [5.10 Wolfi / Chainguard](#510-wolfi--chainguard)
- [6. Vendor advisories for enterprise impact assessment](#6-vendor-advisories-for-enterprise-impact-assessment)
  - [6.1 Major OS, browser & platform vendors](#61-major-os-browser--platform-vendors)
  - [6.2 Enterprise infrastructure vendors](#62-enterprise-infrastructure-vendors)
  - [6.3 Cloud provider security bulletins](#63-cloud-provider-security-bulletins)
- [7. SBOM, package identity, VEX & advisory exchange standards](#7-sbom-package-identity-vex--advisory-exchange-standards)
  - [7.1 SBOM standards](#71-sbom-standards)
  - [7.2 Package & software identity](#72-package--software-identity)
  - [7.3 Advisory exchange, CSAF & VEX](#73-advisory-exchange-csaf--vex)
- [8. Malicious package, supply-chain compromise & package reputation sources](#8-malicious-package-supply-chain-compromise--package-reputation-sources)
  - [8.1 Malicious package databases](#81-malicious-package-databases)
  - [8.2 Package reputation / dependency health](#82-package-reputation--dependency-health)
- [9. Automated vulnerability detection, static analysis, dynamic analysis & research datasets](#9-automated-vulnerability-detection-static-analysis-dynamic-analysis--research-datasets)
  - [9.1 SAST / code query engines](#91-sast--code-query-engines)
  - [9.2 DAST, IAST, fuzzing & dynamic test sources](#92-dast-iast-fuzzing--dynamic-test-sources)
  - [9.3 Vulnerability-detection research datasets](#93-vulnerability-detection-research-datasets)
- [10. ICS, OT, IoT, embedded & medical-device sources](#10-ics-ot-iot-embedded--medical-device-sources)
  - [10.1 CISA ICS / medical](#101-cisa-ics--medical)
  - [10.2 OT / ICS vendor advisories](#102-ot--ics-vendor-advisories)
  - [10.3 IoT / embedded](#103-iot--embedded)
- [11. Exposure, internet-facing asset & threat telemetry](#11-exposure-internet-facing-asset--threat-telemetry)
  - [11.1 Internet exposure search engines](#111-internet-exposure-search-engines)
  - [11.2 Scan/exploitation telemetry](#112-scanexploitation-telemetry)
  - [11.3 Attack surface management context](#113-attack-surface-management-context)
- [12. Threat intelligence, malware, ransomware & in-the-wild exploitation context](#12-threat-intelligence-malware-ransomware--in-the-wild-exploitation-context)
  - [12.1 Major threat research sources](#121-major-threat-research-sources)
  - [12.2 Malware & IOC repositories](#122-malware--ioc-repositories)
- [13. Compliance, baseline configuration & exposure severity standards](#13-compliance-baseline-configuration--exposure-severity-standards)
  - [13.1 Security configuration & benchmarks](#131-security-configuration--benchmarks)
  - [13.2 Cloud configuration posture](#132-cloud-configuration-posture)
- [14. Source-code, dependency, artifact & build-chain provenance](#14-source-code-dependency-artifact--build-chain-provenance)
  - [14.1 Source & artifact provenance](#141-source--artifact-provenance)
  - [14.2 Dependency inventory & graphing](#142-dependency-inventory--graphing)
- [15. Practical priority hierarchy for ingestion](#15-practical-priority-hierarchy-for-ingestion)
  - [15.1 Tier 0 - identifiers & inventory](#151-tier-0---identifiers--inventory)
  - [15.2 Tier 1 - canonical vulnerability records](#152-tier-1---canonical-vulnerability-records)
  - [15.3 Tier 2 - package/ecosystem vulnerability records](#153-tier-2---packageecosystem-vulnerability-records)
  - [15.4 Tier 3 - affectedness, distro & vendor truth](#154-tier-3---affectedness-distro--vendor-truth)
  - [15.5 Tier 4 - severity & prioritization](#155-tier-4---severity--prioritization)
  - [15.6 Tier 5 - exploitability & weaponization](#156-tier-5---exploitability--weaponization)
  - [15.7 Tier 6 - weakness, attack-pattern & AI context](#157-tier-6---weakness-attack-pattern--ai-context)
  - [15.8 Tier 7 - detection engineering & validation](#158-tier-7---detection-engineering--validation)
- [16. Recommended canonical data model coverage](#16-recommended-canonical-data-model-coverage)
  - [16.1 Vulnerability identity](#161-vulnerability-identity)
  - [16.2 Affectedness](#162-affectedness)
  - [16.3 Severity & exploitability](#163-severity--exploitability)
  - [16.4 Environmental impact](#164-environmental-impact)
  - [16.5 Detection & remediation](#165-detection--remediation)
- [17. Minimal source set for production use](#17-minimal-source-set-for-production-use)
- [18. Final structure for all vulnerability management sources & exposure listings](#18-final-structure-for-all-vulnerability-management-sources--exposure-listings)

---

## 0. Corrections & normalization notes

| Sl. # | Title | Link(s) | Relevance | Notes & POIs |
|---:|---|---|---|---|
| 1 | Project Zero issue tracker migration | [bugs.chromium.org/p/project-zero/issues/list](https://bugs.chromium.org/p/project-zero/issues/list), [project-zero.issues.chromium.org](https://project-zero.issues.chromium.org/) | Tracks high-quality vulnerability research, root-cause analysis, exploitability notes, & coordinated disclosure. Useful for exploitability context & historical vulnerability behavior. | Prefer the current tracker for ongoing lookups. Keep the old Monorail-style link for historical references that still appear in older writeups. |
| 2 | Alpine SecDB mirror normalization | [github.com/alpinelinux/alpine-secdb](https://github.com/alpinelinux/alpine-secdb), [secdb.alpinelinux.org](https://secdb.alpinelinux.org/) | Provides Alpine package vulnerability affectedness. Important for container images using Alpine as a base. | The GitHub mirror is deprecated. Use `secdb.alpinelinux.org` as the primary ingestion source. |
| 3 | Wolfi / Chainguard feed split | [packages.cgr.dev/chainguard/security.json](https://packages.cgr.dev/chainguard/security.json), [packages.wolfi.dev/os/security.json](https://packages.wolfi.dev/os/security.json) | Provides secdb-style security feeds for Wolfi & Chainguard images. Key for modern minimal container images. | The Wolfi feed & Chainguard Enterprise feed represent related but distinct package universes. Avoid treating them as exact duplicates. |
| 4 | GitHub Advisory APIs | [docs.github.com/en/graphql/reference/objects#securityadvisory](https://docs.github.com/en/graphql/reference/objects#securityadvisory), [docs.github.com/en/rest/security-advisories](https://docs.github.com/en/rest/security-advisories), [docs.github.com/en/rest/security-advisories/global-advisories](https://docs.github.com/en/rest/security-advisories/global-advisories) | Enables programmatic access to GitHub advisories, including GHSA records, CVE aliases, ecosystems, version ranges, & malware advisories. | Keep both GraphQL & REST. GraphQL is useful for complex queries; REST is simpler for ingestion & pagination. |
| 5 | NVD feeds vs APIs | [nvd.nist.gov/developers](https://nvd.nist.gov/developers), [nvd.nist.gov/vuln/data-feeds](https://nvd.nist.gov/vuln/data-feeds) | NVD provides CVE enrichment, CPE configurations, CVSS vectors, CWE mappings, references, & change metadata. | Prefer NVD 2.0 APIs for ongoing sync. Use bulk feeds for bootstrapping, archival snapshots, or local mirroring. |

[Back to index](#index)

---

## 1. Canonical vulnerability identifiers, CVE records & schemas

### 1.1 CVE Program - canonical CVE identity

| Sl. # | Title | Link(s) | Relevance | Notes & POIs |
|---:|---|---|---|---|
| 1 | CVE.org | [www.cve.org](https://www.cve.org/) | Official CVE program portal for CVE IDs, CNA/ADP governance, CVE lookup, & program documentation. | Canonical governance source, but not always the richest technical source for scoring, affected versions, or exploitability. |
| 2 | CVE List v5 - official GitHub mirror/cache | [github.com/CVEProject/cvelistV5](https://github.com/CVEProject/cvelistV5) | Primary public GitHub cache of CVE v5 JSON records. Useful for local mirroring, batch parsing, & canonical CVE field extraction. | Records may vary in completeness by CNA. Use with NVD, OSV, vendor advisories, & CISA Vulnrichment for enrichment. |
| 3 | CVE Record Format schema - direct JSON schema | [github.com/CVEProject/cve-schema/blob/main/schema/CVE_Record_Format.json](https://github.com/CVEProject/cve-schema/blob/main/schema/CVE_Record_Format.json) | Machine-validation schema for CVE v5 records. Required for parser validation & ingestion guardrails. | Schema correctness does not imply record semantic completeness. Validate schema & still handle missing CNA fields. |
| 4 | CVE schema repository | [github.com/CVEProject/cve-schema](https://github.com/CVEProject/cve-schema) | Contains schema versions, tests, examples, release history, & format evolution. | Track schema version drift when maintaining long-lived ingestion pipelines. |
| 5 | CVE Services API / CVE Program API | [cveawg.mitre.org/api-docs](https://cveawg.mitre.org/api-docs/) | Direct CVE lookup & CVE Services API documentation. Useful for targeted lookup workflows. | API usage may differ from GitHub mirror sync behavior. Use for lookup, not necessarily full mirroring. |
| 6 | CVE Authorized Data Publishers - ADPs | [www.cve.org/ProgramOrganization/ADPs](https://www.cve.org/ProgramOrganization/ADPs) | Lists ADPs that can enrich CVE records beyond CNA-provided content. | ADP enrichment can add critical assessment context. Treat ADP data as enrichment layered on top of canonical CNA data. |
| 7 | CISA Vulnrichment - CVE ADP enrichment | [github.com/cisagov/vulnrichment](https://github.com/cisagov/vulnrichment) | Provides CISA ADP enrichment of CVE records, including SSVC decision points, & sometimes CWE/CVSS details. | Useful for prioritization. Coverage may not be universal across all CVEs. Track freshness & missing enrichment states. |

### 1.2 NVD - CVE enrichment, CPE matching, CVSS & configurations

| Sl. # | Title | Link(s) | Relevance | Notes & POIs |
|---:|---|---|---|---|
| 1 | NVD home | [nvd.nist.gov](https://nvd.nist.gov/) | U.S. government vulnerability-management repository. Provides vulnerability metadata, scoring, product mapping, & references. | NVD enrichment may lag behind CVE publication or vendor disclosures. Monitor modified dates. |
| 2 | NVD CVE API 2.0 | [nvd.nist.gov/developers/vulnerabilities](https://nvd.nist.gov/developers/vulnerabilities) | Retrieves CVEs with CVSS, weaknesses, references, CPE configurations, & change history. | Central for CPE-based product matching. Rate limits & API keys may affect ingestion design. |
| 3 | NVD CPE API 2.0 | [nvd.nist.gov/developers/products](https://nvd.nist.gov/developers/products) | Provides CPE dictionary & CPE match criteria for product/platform matching. | CPE can be imprecise for packages, forks, backports, & cloud services. Combine with PURL, OSV, & vendor feeds. |
| 4 | NVD Data Feeds | [nvd.nist.gov/vuln/data-feeds](https://nvd.nist.gov/vuln/data-feeds) | Bulk JSON feeds for CVEs, CPE dictionary, & CPE match feeds. Useful for initial database bootstrapping. | APIs are generally preferred for ongoing updates. Feeds are useful for snapshots & offline ingestion. |
| 5 | NVD CVSS resources | [nvd.nist.gov/vuln-metrics/cvss](https://nvd.nist.gov/vuln-metrics/cvss) | CVSS calculators, vector definitions, & severity scoring references. | CVSS is severity, not exploit likelihood. Combine with EPSS, KEV, exposure, & asset criticality. |
| 6 | NVD CPE Dictionary | [nvd.nist.gov/products/cpe](https://nvd.nist.gov/products/cpe) | CPE product naming & matching basis. | CPE coverage & naming consistency vary. False positives are common without vendor/package-specific affectedness. |
| 7 | NVD API documentation root | [nvd.nist.gov/developers](https://nvd.nist.gov/developers) | API family documentation for NVD data access. | Use this as the stable entry point for NVD API changes. |
| 8 | NVD CVE Change History API | [nvd.nist.gov/developers/vulnerabilities](https://nvd.nist.gov/developers/vulnerabilities) | Enables monitoring changes to CVE enrichment, scoring, references, & configurations. | Treat NVD records as mutable. Store ingestion timestamp, source modified timestamp, & prior versions where possible. |

### 1.3 Optional CVE meta-mirrors / commercial-community enrichments

| Sl. # | Title | Link(s) | Relevance | Notes & POIs |
|---:|---|---|---|---|
| 1 | VulnCheck NVD++ | [www.vulncheck.com/nvd2](https://www.vulncheck.com/nvd2) | Aggregated vulnerability intelligence that can supplement CVE/NVD/KEV workflows. | Commercial/community enrichment. Validate terms, licensing, API access, & provenance before production use. |
| 2 | Vulners | [vulners.com](https://vulners.com/) | Vulnerability intelligence aggregator across many advisory & exploit sources. | Useful for broad search & enrichment. Do not treat as canonical without source provenance. |
| 3 | OpenCVE | [www.opencve.io](https://www.opencve.io/) | CVE monitoring, subscriptions, change tracking, & alerting workflows. | Useful for monitoring, but canonical ingestion should still pull from upstream CVE/NVD/vendor feeds. |
| 4 | CIRCL CVE Search | [cve.circl.lu](https://cve.circl.lu/) | CVE search & enrichment source, historically useful for threat-intel workflows. | Validate freshness before relying on it. Prefer canonical sources for production scoring. |

[Back to index](#index)

---

## 2. Open-source vulnerability databases & package advisory sources

### 2.1 OSV ecosystem

| Sl. # | Title | Link(s) | Relevance | Notes & POIs |
|---:|---|---|---|---|
| 1 | OSV main site | [osv.dev](https://osv.dev/) | Aggregates OSS vulnerabilities by package ecosystem, version, commit, & aliases. Key for dependency-based detection. | OSV is package/version-centric & often better than CPE for OSS packages. Coverage depends on upstream ecosystem feeds. |
| 2 | OSV vulnerability list | [osv.dev/list](https://osv.dev/list) | Human-browsable OSV records. | Useful for manual triage & ecosystem browsing. Prefer API/full downloads for automation. |
| 3 | OSV full database download | [google.github.io/osv.dev/data/#full-database-download](https://google.github.io/osv.dev/data/#full-database-download) | Full database ZIP, including withdrawn records, via `gs://osv-vulnerabilities/all.zip`. | Best for local mirroring. Preserve withdrawn records for historical auditability. |
| 4 | OSV data sources page | [google.github.io/osv.dev/data](https://google.github.io/osv.dev/data/) | Per-ecosystem downloads & full-database download. | Useful for targeted ecosystem ingestion. |
| 5 | OSV schema rendered spec | [ossf.github.io/osv-schema](https://ossf.github.io/osv-schema/) | Standard interchange format for OSS vulnerability records. | Handle aliases, affected ranges, fixed versions, withdrawn records, & ecosystem-specific semantics. |
| 6 | OSV schema GitHub repo | [github.com/ossf/osv-schema](https://github.com/ossf/osv-schema) | Schema source, releases, bindings, & tooling. | Track schema versions & validation changes over time. |
| 7 | OSV API docs | [google.github.io/osv.dev/post-v1-query](https://google.github.io/osv.dev/post-v1-query/) | Query vulnerabilities by package, version, commit, or vulnerability ID. | Good for online lookup. Use full downloads for high-volume local matching. |
| 8 | OSV Scanner | [google.github.io/osv-scanner](https://google.github.io/osv-scanner/) | Reference scanner using OSV data. | Useful implementation reference for lockfile parsing & version matching. |
| 9 | OSV Scanner GitHub | [github.com/google/osv-scanner](https://github.com/google/osv-scanner) | Scanner implementation, matching logic, & lockfile parsing. | Review for practical matching edge cases. |
| 10 | OSV ecosystem list | [osv.dev/list](https://osv.dev/list) | Ecosystem browsing for Maven, npm, PyPI, Go, crates.io, Debian, Alpine, Ubuntu, Wolfi, OSS-Fuzz, etc. | Repeats the list URL intentionally because it serves both record browsing & ecosystem discovery. |

### 2.2 GitHub Advisory Database

| Sl. # | Title | Link(s) | Relevance | Notes & POIs |
|---:|---|---|---|---|
| 1 | GitHub Advisory Database - web | [github.com/advisories](https://github.com/advisories) | GitHub-reviewed, unreviewed, malware, GHSA, & CVE advisory records across ecosystems. | GHSA records can exist without CVEs. Preserve alias relationships between GHSA, CVE, & OSV. |
| 2 | GitHub Advisory Database repo | [github.com/github/advisory-database](https://github.com/github/advisory-database) | Raw advisory data for local ingestion. | Use for mirroring; validate ecosystem/version range semantics. |
| 3 | About GitHub Advisory Database | [docs.github.com/en/code-security/concepts/vulnerability-reporting-and-management/about-the-github-advisory-database](https://docs.github.com/en/code-security/concepts/vulnerability-reporting-and-management/about-the-github-advisory-database) | Explains reviewed, unreviewed, & malware advisory model. | Important for confidence scoring. Reviewed vs unreviewed status affects dependability. |
| 4 | GitHub Security Advisory GraphQL object | [docs.github.com/en/graphql/reference/objects#securityadvisory](https://docs.github.com/en/graphql/reference/objects#securityadvisory) | Programmatic advisory metadata access via GraphQL. | Useful for complex filtered queries. Requires API authentication for robust use. |
| 5 | GitHub REST API - global security advisories | [docs.github.com/en/rest/security-advisories/global-advisories](https://docs.github.com/en/rest/security-advisories/global-advisories) | REST access for listing & retrieving global security advisories. | Easier to integrate than GraphQL for many ingestion jobs. |
| 6 | GitHub REST API - security advisories root | [docs.github.com/en/rest/security-advisories](https://docs.github.com/en/rest/security-advisories) | Root documentation for global & repository security advisory endpoints. | Use to distinguish global advisories from repo-private advisories. |
| 7 | GitHub Dependabot alerts REST API | [docs.github.com/en/rest/dependabot/alerts](https://docs.github.com/en/rest/dependabot/alerts) | Repository-specific vulnerability exposure from dependency graph. | Requires repo access. Useful for actual asset exposure, not just global vulnerability existence. |
| 8 | Dependabot supported ecosystems | [docs.github.com/en/code-security/reference/supply-chain-security/supported-ecosystems-and-repositories](https://docs.github.com/en/code-security/reference/supply-chain-security/supported-ecosystems-and-repositories) | Supported ecosystem list for GitHub dependency graph & alerts. | Coverage constraints impact blind spots in detection. |
| 9 | GitHub malware advisories | [github.com/advisories?query=type%3Amalware](https://github.com/advisories?query=type%3Amalware) | Malicious package advisories. | Useful for supply-chain compromise detection beyond CVE-style vulnerabilities. |
| 10 | GitHub npm advisories | [github.com/advisories?query=ecosystem%3Anpm](https://github.com/advisories?query=ecosystem%3Anpm) | npm ecosystem advisories. | Version ranges & semver semantics are ecosystem-specific. |
| 11 | GitHub pip advisories | [github.com/advisories?query=ecosystem%3Apip](https://github.com/advisories?query=ecosystem%3Apip) | Python/PyPI advisories. | Cross-check with PyPA advisory DB & OSV. |
| 12 | GitHub Maven advisories | [github.com/advisories?query=ecosystem%3Amaven](https://github.com/advisories?query=ecosystem%3Amaven) | Maven ecosystem advisories. | Maven coordinates & shaded dependencies can complicate affectedness. |
| 13 | GitHub NuGet advisories | [github.com/advisories?query=ecosystem%3Anuget](https://github.com/advisories?query=ecosystem%3Anuget) | NuGet ecosystem advisories. | Useful for .NET dependency assessment. |
| 14 | GitHub Go advisories | [github.com/advisories?query=ecosystem%3Ago](https://github.com/advisories?query=ecosystem%3Ago) | Go ecosystem advisories. | Cross-check with official Go vulnerability DB. |
| 15 | GitHub RubyGems advisories | [github.com/advisories?query=ecosystem%3Arubygems](https://github.com/advisories?query=ecosystem%3Arubygems) | RubyGems advisories. | Cross-check with RubySec. |
| 16 | GitHub Rust advisories | [github.com/advisories?query=ecosystem%3Arust](https://github.com/advisories?query=ecosystem%3Arust) | Rust crate advisories. | Cross-check with RustSec. |
| 17 | GitHub Composer advisories | [github.com/advisories?query=ecosystem%3Acomposer](https://github.com/advisories?query=ecosystem%3Acomposer) | PHP Composer advisories. | Cross-check with FriendsOfPHP & Packagist. |
| 18 | GitHub Pub advisories | [github.com/advisories?query=ecosystem%3Apub](https://github.com/advisories?query=ecosystem%3Apub) | Dart/Pub advisories. | Coverage may vary by ecosystem maturity. |
| 19 | GitHub Swift advisories | [github.com/advisories?query=ecosystem%3Aswift](https://github.com/advisories?query=ecosystem%3Aswift) | Swift package advisories. | Useful for Swift Package Manager ecosystems. |
| 20 | GitHub Erlang advisories | [github.com/advisories?query=ecosystem%3Aerlang](https://github.com/advisories?query=ecosystem%3Aerlang) | Erlang/Hex advisories. | Validate package naming conventions against Hex. |

### 2.3 Language & package ecosystem advisory databases

#### 2.3.1 Go

| Sl. # | Title | Link(s) | Relevance | Notes & POIs |
|---:|---|---|---|---|
| 1 | Go Vulnerability Database | [vuln.go.dev](https://vuln.go.dev/) | Official Go vulnerability database for Go modules. | Strong source for Go-specific affected symbols, modules, packages, & fixed versions. |
| 2 | Go vulnerability database docs | [go.dev/doc/security/vuln/database](https://go.dev/doc/security/vuln/database) | Explains Go vulnerability DB data model & OSV usage. | Important for correct ingestion & symbol/package-level interpretation. |
| 3 | Go vuln browser | [pkg.go.dev/vuln](https://pkg.go.dev/vuln/) | Human-readable curated Go vulnerability reports. | Useful for triage & manual review. |
| 4 | Go vuln tooling | [pkg.go.dev/golang.org/x/vuln/cmd/govulncheck](https://pkg.go.dev/golang.org/x/vuln/cmd/govulncheck) | Go source/binary vulnerability checking. | Can reduce false positives by analyzing call reachability in Go code. |

#### 2.3.2 Rust

| Sl. # | Title | Link(s) | Relevance | Notes & POIs |
|---:|---|---|---|---|
| 1 | RustSec | [rustsec.org](https://rustsec.org/) | Rust crate advisory ecosystem. | Often includes Rust-specific unsoundness, yanked crates, & ecosystem-specific risk. |
| 2 | RustSec advisory DB repo | [github.com/RustSec/advisory-db](https://github.com/RustSec/advisory-db) | Machine-ingestible Rust advisories. | Good for local ingestion & cargo-audit compatible workflows. |
| 3 | RustSec advisories browser | [rustsec.org/advisories](https://rustsec.org/advisories/) | Human-browsable Rust advisories. | Useful for manual triage. |
| 4 | cargo-audit | [github.com/RustSec/rustsec/tree/main/cargo-audit](https://github.com/RustSec/rustsec/tree/main/cargo-audit) | RustSec-based vulnerability scanner. | Reference implementation for Rust dependency scanning. |

#### 2.3.3 Python / PyPI

| Sl. # | Title | Link(s) | Relevance | Notes & POIs |
|---:|---|---|---|---|
| 1 | PyPA advisory database | [github.com/pypa/advisory-database](https://github.com/pypa/advisory-database) | Python/PyPI advisory source. | Use with OSV & GitHub advisories for better Python coverage. |
| 2 | PyPI security page | [pypi.org/security](https://pypi.org/security/) | PyPI security reporting & advisory context. | Useful for process context, not necessarily complete advisory ingestion. |
| 3 | pip-audit | [github.com/pypa/pip-audit](https://github.com/pypa/pip-audit) | Python dependency vulnerability scanner. | Reference implementation for Python dependency assessment. |
| 4 | Safety DB | [github.com/pyupio/safety-db](https://github.com/pyupio/safety-db) | Historical Python advisory source. | Validate freshness & licensing before relying on it. |

#### 2.3.4 JavaScript / npm

| Sl. # | Title | Link(s) | Relevance | Notes & POIs |
|---:|---|---|---|---|
| 1 | npm advisories via GitHub | [github.com/advisories?query=ecosystem%3Anpm](https://github.com/advisories?query=ecosystem%3Anpm) | npm ecosystem vulnerability advisories. | Semver ranges, lockfiles, transitive dependencies, & malicious packages require careful parsing. |
| 2 | Node.js Security Working Group | [github.com/nodejs/security-wg](https://github.com/nodejs/security-wg) | Node ecosystem security coordination & historical advisory sources. | Some historical records may be superseded by GitHub Advisory DB. |
| 3 | npm audit docs | [docs.npmjs.com/cli/commands/npm-audit](https://docs.npmjs.com/cli/commands/npm-audit) | Documents npm audit behavior. | Useful to understand scanner behavior, dependency tree handling, & remediation suggestions. |
| 4 | Socket.dev security research | [socket.dev/blog](https://socket.dev/blog) | Malicious package & JS supply-chain threat intel. | Research source. Validate indicators & package claims against primary registries. |

#### 2.3.5 Java / Maven / JVM

| Sl. # | Title | Link(s) | Relevance | Notes & POIs |
|---:|---|---|---|---|
| 1 | Sonatype OSS Index | [ossindex.sonatype.org](https://ossindex.sonatype.org/) | OSS vulnerability intelligence commonly used for Maven & other ecosystems. | Commercial/community source. Validate API terms, limits, & provenance. |
| 2 | Sonatype vulnerability database | [sonatype.com/resources/vulnerability-database](https://sonatype.com/resources/vulnerability-database) | Sonatype vulnerability intelligence database. | Useful for enrichment & triage, but not canonical. |
| 3 | Maven Central | [central.sonatype.com](https://central.sonatype.com/) | Package identity & metadata for JVM packages. | Not a vulnerability DB, but essential for coordinate resolution & metadata. |
| 4 | OSS Index API docs | [ossindex.sonatype.org/doc/rest](https://ossindex.sonatype.org/doc/rest) | REST API access for OSS Index. | Consider rate limits, authentication, & terms before ingestion. |

#### 2.3.6 PHP / Composer

| Sl. # | Title | Link(s) | Relevance | Notes & POIs |
|---:|---|---|---|---|
| 1 | FriendsOfPHP security advisories | [github.com/FriendsOfPHP/security-advisories](https://github.com/FriendsOfPHP/security-advisories) | PHP Composer package advisories. | Historical & ecosystem-specific source. Cross-check with Packagist & GHSA. |
| 2 | Packagist security advisories API | [packagist.org/apidoc#list-security-advisories](https://packagist.org/apidoc#list-security-advisories) | Composer package advisory API. | Direct ecosystem source for Composer package advisories. |
| 3 | Composer audit docs | [getcomposer.org/doc/03-cli.md#audit](https://getcomposer.org/doc/03-cli.md#audit) | Documents Composer audit behavior. | Useful for implementation parity with Composer-native workflows. |

#### 2.3.7 Ruby

| Sl. # | Title | Link(s) | Relevance | Notes & POIs |
|---:|---|---|---|---|
| 1 | RubySec advisory DB | [github.com/rubysec/ruby-advisory-db](https://github.com/rubysec/ruby-advisory-db) | RubyGems advisories. | Cross-check with GHSA RubyGems advisories. |
| 2 | Bundler audit | [github.com/rubysec/bundler-audit](https://github.com/rubysec/bundler-audit) | Ruby dependency vulnerability scanner. | Reference implementation for Gemfile.lock scanning. |

#### 2.3.8 .NET / NuGet

| Sl. # | Title | Link(s) | Relevance | Notes & POIs |
|---:|---|---|---|---|
| 1 | NuGet advisories via GitHub | [github.com/advisories?query=ecosystem%3Anuget](https://github.com/advisories?query=ecosystem%3Anuget) | NuGet ecosystem advisories. | Use with lockfile/project metadata for actual exposure. |
| 2 | NuGet audit docs | [learn.microsoft.com/en-us/nuget/concepts/auditing-packages](https://learn.microsoft.com/en-us/nuget/concepts/auditing-packages) | Documents NuGet package auditing. | Useful for Microsoft ecosystem parity & remediation guidance. |

#### 2.3.9 Erlang / Elixir / Hex

| Sl. # | Title | Link(s) | Relevance | Notes & POIs |
|---:|---|---|---|---|
| 1 | Erlang advisories via GitHub | [github.com/advisories?query=ecosystem%3Aerlang](https://github.com/advisories?query=ecosystem%3Aerlang) | Erlang/Hex advisories. | Validate ecosystem naming, package coordinates, & version semantics. |
| 2 | Hex package manager | [hex.pm](https://hex.pm/) | Package registry for Erlang/Elixir packages. | Registry metadata helps resolve package identity. |

#### 2.3.10 Dart / Flutter / Pub

| Sl. # | Title | Link(s) | Relevance | Notes & POIs |
|---:|---|---|---|---|
| 1 | Pub advisories via GitHub | [github.com/advisories?query=ecosystem%3Apub](https://github.com/advisories?query=ecosystem%3Apub) | Dart/Pub advisories. | Coverage depends on GitHub advisory ingestion. |
| 2 | Dart package repository | [pub.dev](https://pub.dev/) | Package registry for Dart/Flutter dependencies. | Useful for package identity & version metadata. |

#### 2.3.11 Swift

| Sl. # | Title | Link(s) | Relevance | Notes & POIs |
|---:|---|---|---|---|
| 1 | Swift advisories via GitHub | [github.com/advisories?query=ecosystem%3Aswift](https://github.com/advisories?query=ecosystem%3Aswift) | Swift ecosystem advisories. | Coverage depends on GitHub Advisory DB support. |
| 2 | Swift Package Index | [swiftpackageindex.com](https://swiftpackageindex.com/) | Swift package metadata & ecosystem context. | Not a vulnerability DB, but useful for package discovery & metadata. |

[Back to index](#index)

---

## 3. Exploitation, prioritization, severity & risk scoring

### 3.1 Known exploited vulnerability sources

| Sl. # | Title | Link(s) | Relevance | Notes & POIs |
|---:|---|---|---|---|
| 1 | CISA KEV catalog - web | [www.cisa.gov/known-exploited-vulnerabilities-catalog](https://www.cisa.gov/known-exploited-vulnerabilities-catalog) | Authoritative catalog of known exploited vulnerabilities. Critical for prioritization & remediation urgency. | KEV is a strong exploitation signal but not a complete list of all exploited vulnerabilities. |
| 2 | CISA KEV print view | [www.cisa.gov/known-exploited-vulnerabilities-catalog-print](https://www.cisa.gov/known-exploited-vulnerabilities-catalog-print) | Human-readable print-oriented KEV view. | Useful for documentation & manual review; use JSON for automation. |
| 3 | CISA KEV JSON feed | [www.cisa.gov/sites/default/files/feeds/known_exploited_vulnerabilities.json](https://www.cisa.gov/sites/default/files/feeds/known_exploited_vulnerabilities.json) | Machine-readable KEV feed. | Primary automation source for KEV ingestion. Monitor `dateAdded` & due dates. |
| 4 | CISA KEV JSON schema | [www.cisa.gov/sites/default/files/feeds/known_exploited_vulnerabilities_schema.json](https://www.cisa.gov/sites/default/files/feeds/known_exploited_vulnerabilities_schema.json) | Schema for KEV JSON validation. | Use for ingestion validation. Schema changes should trigger parser review. |
| 5 | CISA KEV GitHub mirror | [github.com/cisagov/kev-data](https://github.com/cisagov/kev-data) | GitHub mirror of KEV data. | Useful for Git-based diffing & historical tracking. Treat CISA official feed as source of truth. |
| 6 | VulnCheck KEV | [vulncheck.com/kev](https://vulncheck.com/kev) | Expanded KEV-like exploitation intelligence. | Not identical to CISA KEV. Validate definitions, coverage, licensing, & freshness. |
| 7 | Shadowserver reports | [www.shadowserver.org](https://www.shadowserver.org/) | Internet-scale exploitation & exposure observations. | Useful for exposure/scan telemetry. Data may be aggregated & require access setup. |
| 8 | GreyNoise Visualizer | [viz.greynoise.io](https://viz.greynoise.io/) | Internet scanning/exploitation noise & actor context. | Helps distinguish benign scanning, mass exploitation, & opportunistic activity. |
| 9 | GreyNoise API docs | [docs.greynoise.io](https://docs.greynoise.io/) | API for IP-based exploitation telemetry enrichment. | API terms, quotas, & plan level can affect automation. |

### 3.2 Exploit prediction & scoring

| Sl. # | Title | Link(s) | Relevance | Notes & POIs |
|---:|---|---|---|---|
| 1 | FIRST EPSS overview | [www.first.org/epss](https://www.first.org/epss/) | Exploit Prediction Scoring System. Provides probability-style exploit-likelihood signals. | EPSS predicts exploitation probability, not impact. Use with CVSS, KEV, exposure, & asset criticality. |
| 2 | FIRST EPSS API | [www.first.org/epss/api](https://www.first.org/epss/api) | API endpoint for EPSS scores. | Useful for daily enrichment. Store score date because EPSS changes over time. |
| 3 | FIRST EPSS data & CSV downloads | [www.first.org/epss/data_stats](https://www.first.org/epss/data_stats) | Current & historical EPSS CSV data reference. | Historical scores are useful for model training & retrospective analysis. |
| 4 | Historical EPSS scores GitHub | [github.com/empiricalsec/epss_scores](https://github.com/empiricalsec/epss_scores) | Daily historical EPSS snapshots. | Useful for longitudinal training labels. Validate against FIRST releases. |
| 5 | FIRST CVSS | [www.first.org/cvss](https://www.first.org/cvss/) | Official CVSS specification home. | CVSS severity must not be treated as exploit likelihood. |
| 6 | FIRST CVSS v4.0 | [www.first.org/cvss/v4.0/specification-document](https://www.first.org/cvss/v4.0/specification-document) | CVSS v4.0 specification. | Newer scoring semantics may not be universally populated across vulnerability records yet. |
| 7 | FIRST CVSS v3.1 | [www.first.org/cvss/v3.1/specification-document](https://www.first.org/cvss/v3.1/specification-document) | CVSS v3.1 specification. | Still widely used across CVE/NVD/vendor data. |
| 8 | NVD CVSS resources | [nvd.nist.gov/vuln-metrics/cvss](https://nvd.nist.gov/vuln-metrics/cvss) | CVSS calculators & vector references. | Useful for parsing & validating NVD scoring data. |

### 3.3 Decision-support frameworks

| Sl. # | Title | Link(s) | Relevance | Notes & POIs |
|---:|---|---|---|---|
| 1 | CISA SSVC | [www.cisa.gov/stakeholder-specific-vulnerability-categorization-ssvc](https://www.cisa.gov/stakeholder-specific-vulnerability-categorization-ssvc) | Stakeholder-Specific Vulnerability Categorization for vulnerability response decisions. | Useful for decision automation beyond raw severity. Depends on environmental & mission context. |
| 2 | CERT/CC SSVC project | [github.com/CERTCC/SSVC](https://github.com/CERTCC/SSVC) | SSVC model artifacts, examples, & discussions. | Useful for implementing SSVC decision trees & decision points. |
| 3 | CISA Vulnrichment | [github.com/cisagov/vulnrichment](https://github.com/cisagov/vulnrichment) | CISA ADP enrichment & SSVC decision points. | Coverage is not universal. Preserve missing/null state distinctly from “low risk.” |
| 4 | CISA Binding Operational Directive 22-01 | [www.cisa.gov/news-events/directives/bod-22-01-reducing-significant-risk-known-exploited-vulnerabilities](https://www.cisa.gov/news-events/directives/bod-22-01-reducing-significant-risk-known-exploited-vulnerabilities) | Operational requirement context for KEV remediation. | Primarily binding for U.S. federal civilian agencies but useful as industry prioritization guidance. |
| 5 | CISA Cybersecurity Advisories | [www.cisa.gov/cybersecurity-advisories](https://www.cisa.gov/cybersecurity-advisories) | Broader CISA advisory feed. | Useful for emergent campaigns, vendor alerts, & remediation guidance. |
| 6 | CISA Alerts | [www.cisa.gov/news-events/cybersecurity-advisories](https://www.cisa.gov/news-events/cybersecurity-advisories) | CISA alert/advisory listing. | May overlap with other CISA pages. Deduplicate by advisory ID/date. |

### 3.4 Public exploit / proof-of-concept / weaponization signals

| Sl. # | Title | Link(s) | Relevance | Notes & POIs |
|---:|---|---|---|---|
| 1 | Exploit-DB | [www.exploit-db.com](https://www.exploit-db.com/) | Public exploit archive. Strong signal for PoC availability. | Public PoC does not always mean reliable weaponization; verify exploit quality & target version. |
| 2 | SearchSploit | [www.exploit-db.com/searchsploit](https://www.exploit-db.com/searchsploit) | CLI interface for Exploit-DB. | Useful for local workflows & offline search. |
| 3 | Exploit-DB GitLab mirror | [gitlab.com/exploit-database/exploitdb](https://gitlab.com/exploit-database/exploitdb) | Git mirror of Exploit-DB content. | Useful for local indexing & diffing. |
| 4 | Metasploit Framework | [github.com/rapid7/metasploit-framework](https://github.com/rapid7/metasploit-framework) | Exploit framework containing modules, payloads, & auxiliary checks. | A Metasploit module is a stronger operationalization signal than a bare PoC. |
| 5 | Metasploit exploit modules | [github.com/rapid7/metasploit-framework/tree/master/modules/exploits](https://github.com/rapid7/metasploit-framework/tree/master/modules/exploits) | Practical signal that a vulnerability has weaponized exploit implementation. | Module maturity, reliability, & target coverage vary. |
| 6 | Packet Storm Security exploits | [packetstormsecurity.com/files/tags/exploit](https://packetstormsecurity.com/files/tags/exploit/) | Public exploit & advisory archive. | Quality & metadata normalization vary; cross-reference CVE IDs. |
| 7 | 0day.today | [0day.today](https://0day.today/) | Public zero-day/exploit listing. | Use carefully. Legal, provenance, accuracy, & quality may vary substantially. |
| 8 | Project Zero blog | [googleprojectzero.blogspot.com](https://googleprojectzero.blogspot.com/) | High-quality root-cause & exploitation writeups. | Excellent for model features around exploitability primitives & bug classes. |
| 9 | Project Zero issue tracker - current | [project-zero.issues.chromium.org](https://project-zero.issues.chromium.org/) | Current Project Zero issue tracker. | Good for disclosure timelines & technical details. |
| 10 | Project Zero issue tracker - old/historical | [bugs.chromium.org/p/project-zero/issues/list](https://bugs.chromium.org/p/project-zero/issues/list) | Historical Project Zero issue tracker link. | Keep for old references; prefer current tracker when available. |
| 11 | CERT/CC Vulnerability Notes Database | [www.kb.cert.org/vuls](https://www.kb.cert.org/vuls/) | Coordinated disclosure context, affected vendors, technical notes, & remediation. | Often useful when multiple vendors/products are affected. |
| 12 | CERT/CC VINCE public notes | [kb.cert.org/vuls/html](https://kb.cert.org/vuls/html/) | Modern public vulnerability note interface. | Good for public vulnerability notes & coordination context. |
| 13 | Rapid7 AttackerKB | [attackerkb.com](https://attackerkb.com/) | Exploitability & attacker-value context. | Community/commercial signals should be weighted with provenance & recency. |
| 14 | Nuclei templates | [github.com/projectdiscovery/nuclei-templates](https://github.com/projectdiscovery/nuclei-templates) | Exposed-condition detection templates. Useful for scanning internet-facing assets. | Template presence is a practical detection signal, not proof of vulnerability unless executed correctly. |
| 15 | ProjectDiscovery Nuclei | [github.com/projectdiscovery/nuclei](https://github.com/projectdiscovery/nuclei) | Template-based vulnerability & exposure scanner. | Detection accuracy depends on template quality, target context, & scanner configuration. |
| 16 | Horizon3.ai research | [www.horizon3.ai/attack-research](https://www.horizon3.ai/attack-research/) | PoC & attack-path writeups. | Useful for exploitability context & reproduction details. |
| 17 | watchTowr Labs | [labs.watchtowr.com](https://labs.watchtowr.com/) | Vulnerability research & exploitation details. | Research source; verify exact affected versions & mitigations. |
| 18 | Assetnote research | [www.assetnote.io/resources/research](https://www.assetnote.io/resources/research) | Exploit research & vulnerability detection signatures. | Useful for detection engineering & exposed attack surface context. |

[Back to index](#index)

---

## 4. CWE, CAPEC, ATT&CK, ATLAS & weakness-to-attack mapping

### 4.1 CWE - Common Weakness Enumeration

| Sl. # | Title | Link(s) | Relevance | Notes & POIs |
|---:|---|---|---|---|
| 1 | CWE home | [cwe.mitre.org](https://cwe.mitre.org/) | Common Weakness Enumeration root. Provides standardized weakness taxonomy. | CVE-to-CWE mappings are sometimes missing, broad, or imprecise. |
| 2 | CWE downloads | [cwe.mitre.org/data/downloads.html](https://cwe.mitre.org/data/downloads.html) | XML, CSV, archive bundles, & views for machine ingestion. | Use downloadable structured data for robust taxonomy ingestion. |
| 3 | CWE latest PDF | [cwe.mitre.org/data/published/cwe_latest.pdf](https://cwe.mitre.org/data/published/cwe_latest.pdf) | PDF publication of latest CWE content. | Better for manual reference than automated ingestion. |
| 4 | CWE reports | [cwe.mitre.org/data/reports.html](https://cwe.mitre.org/data/reports.html) | Reports & curated views of CWE data. | Useful for understanding categories, views, & prioritization. |
| 5 | CWE chains & composites | [cwe.mitre.org/data/reports/chains_and_composites.html](https://cwe.mitre.org/data/reports/chains_and_composites.html) | Describes weakness chains & composite weaknesses. | Important for modeling multi-step root causes & compound vulnerabilities. |
| 6 | CWE schema docs | [cwe.mitre.org/documents/schema/index.html](https://cwe.mitre.org/documents/schema/index.html) | Schema documentation for CWE data. | Use for parser validation & taxonomy consistency. |
| 7 | CWE data definitions | [cwe.mitre.org/data/definitions/1000.html](https://cwe.mitre.org/data/definitions/1000.html) | CWE views & weakness hierarchy. | Useful for grouping weaknesses into higher-level categories. |
| 8 | CWE Top 25 | [cwe.mitre.org/top25](https://cwe.mitre.org/top25/) | Most dangerous software weaknesses. | Good for model priors & training labels, but not a substitute for context-specific risk. |
| 9 | CWE AI/ML category - CWE-1448 | [cwe.mitre.org/data/definitions/1448.html](https://cwe.mitre.org/data/definitions/1448.html) | AI/ML-related weakness category. | Emerging taxonomy area; expect coverage to evolve. |
| 10 | CWE AI Working Group | [cwe.mitre.org/community/working_groups.html](https://cwe.mitre.org/community/working_groups.html) | CWE/CVE AI Working Group context. | Useful for tracking evolution of AI-related weakness classifications. |

### 4.2 CAPEC - attack patterns

| Sl. # | Title | Link(s) | Relevance | Notes & POIs |
|---:|---|---|---|---|
| 1 | CAPEC home | [capec.mitre.org](https://capec.mitre.org/) | Catalog of attack patterns used to exploit weaknesses. | CAPEC bridges weakness taxonomy & attacker behavior patterns. |
| 2 | CAPEC downloads | [capec.mitre.org/data/downloads.html](https://capec.mitre.org/data/downloads.html) | XML/CSV attack-pattern bundles. | Prefer structured downloads for ingestion. |
| 3 | CAPEC schema docs | [capec.mitre.org/documents/schema/index.html](https://capec.mitre.org/documents/schema/index.html) | Schema docs for CAPEC data. | Important for parser validation. |
| 4 | CAPEC data index | [capec.mitre.org/data/index.html](https://capec.mitre.org/data/index.html) | Browsable CAPEC entries & views. | Useful for manual mapping & explanation. |
| 5 | MITRE CTI repository - ATT&CK & CAPEC in STIX | [github.com/mitre/cti](https://github.com/mitre/cti) | MITRE ATT&CK & CAPEC datasets expressed in STIX 2.0. | Useful for graph-based relationships. May differ from newer ATT&CK-specific STIX repo content. |

### 4.3 MITRE ATT&CK

| Sl. # | Title | Link(s) | Relevance | Notes & POIs |
|---:|---|---|---|---|
| 1 | ATT&CK Enterprise Matrix | [attack.mitre.org/matrices/enterprise](https://attack.mitre.org/matrices/enterprise/) | Enterprise adversary tactics & techniques. | More relevant for adversary behavior after exploitation than raw CVE severity. |
| 2 | ATT&CK Matrices | [attack.mitre.org/matrices](https://attack.mitre.org/matrices/) | ATT&CK matrices across domains. | Useful for selecting enterprise, mobile, ICS, or other domain views. |
| 3 | ATT&CK Data & Tools | [attack.mitre.org/resources/attack-data-and-tools](https://attack.mitre.org/resources/attack-data-and-tools/) | ATT&CK Navigator, STIX/TAXII, Workbench, & tooling references. | Prefer machine-readable STIX/TAXII for ingestion. |
| 4 | ATT&CK STIX data repo | [github.com/mitre-attack/attack-stix-data](https://github.com/mitre-attack/attack-stix-data) | Machine-readable ATT&CK STIX data. | Best source for automated technique/tactic ingestion. |
| 5 | MITRE CTI repository | [github.com/mitre/cti](https://github.com/mitre/cti) | MITRE CTI STIX datasets. | Keep for historical/related STIX content. |
| 6 | ATT&CK Navigator | [mitre-attack.github.io/attack-navigator](https://mitre-attack.github.io/attack-navigator/) | Visual mapping of techniques to campaigns, risks, or controls. | Useful for reporting & matrix visualization, not raw vuln ingestion. |
| 7 | ATT&CK Workbench | [github.com/center-for-threat-informed-defense/attack-workbench-frontend](https://github.com/center-for-threat-informed-defense/attack-workbench-frontend) | Tooling for ATT&CK customization & management. | Useful for internal technique mapping workflows. |
| 8 | ATT&CK TAXII server docs | [attack.mitre.org/resources/attack-data-and-tools](https://attack.mitre.org/resources/attack-data-and-tools/) | TAXII/STIX access docs. | Same source as ATT&CK Data & Tools; retained to preserve the explicit TAXII reference. |

### 4.4 AI/ML-specific adversary frameworks

| Sl. # | Title | Link(s) | Relevance | Notes & POIs |
|---:|---|---|---|---|
| 1 | MITRE ATLAS | [atlas.mitre.org](https://atlas.mitre.org/) | Living knowledge base of adversary tactics & techniques against AI-enabled systems. | More directly relevant to AI systems than ATT&CK Enterprise alone. |
| 2 | MITRE ATLAS matrix | [atlas.mitre.org/matrices/ATLAS](https://atlas.mitre.org/matrices/ATLAS) | Matrix view of AI adversary tactics & techniques. | Useful for AI threat modeling & impact mapping. |
| 3 | MITRE ATLAS techniques | [atlas.mitre.org/techniques](https://atlas.mitre.org/techniques) | Technique-level ATLAS entries. | Use for structured AI attack technique mapping. |
| 4 | MITRE ATLAS case studies | [atlas.mitre.org/studies](https://atlas.mitre.org/studies) | Case studies of AI attacks & failures. | Helpful for real-world analogs & model training examples. |
| 5 | MITRE ATLAS GitHub / Adversarial ML Threat Matrix | [github.com/mitre/advmlthreatmatrix](https://github.com/mitre/advmlthreatmatrix) | Historical & structured project data for adversarial ML threat matrix. | May not be the most current ATLAS view; keep for lineage. |
| 6 | MITRE SAFE-AI report | [atlas.mitre.org/pdf-files/SAFEAI_Full_Report.pdf](https://atlas.mitre.org/pdf-files/SAFEAI_Full_Report.pdf) | AI system risk mapping across model, data, platform, & environment layers. | Useful for AI-specific control mapping & architecture risk analysis. |
| 7 | OWASP Top 10 for LLM Applications | [owasp.org/www-project-top-10-for-large-language-model-applications](https://owasp.org/www-project-top-10-for-large-language-model-applications/) | Practical LLM application vulnerability taxonomy. | Useful for AI appsec detection categories beyond CVE. |
| 8 | OWASP Top 10 for Machine Learning Security | [owasp.org/www-project-machine-learning-security-top-10](https://owasp.org/www-project-machine-learning-security-top-10/) | ML-specific application/security risk taxonomy. | Complements ATLAS with appsec-oriented framing. |
| 9 | OWASP AI Exchange | [owaspai.org](https://owaspai.org/) | AI security risks, controls, & threat modeling references. | Useful for governance & risk mapping. |
| 10 | NIST AI Risk Management Framework | [www.nist.gov/itl/ai-risk-management-framework](https://www.nist.gov/itl/ai-risk-management-framework) | AI risk management framework. | Useful for risk controls, governance, & impact framing. |
| 11 | NIST AI RMF 1.0 PDF | [nvlpubs.nist.gov/nistpubs/ai/NIST.AI.100-1.pdf](https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.100-1.pdf) | AI RMF 1.0 document. | PDF reference; not a vulnerability feed. |
| 12 | NIST AI 600-1 - Generative AI Profile | [www.nist.gov/publications/artificial-intelligence-risk-management-framework-generative-artificial-intelligence](https://www.nist.gov/publications/artificial-intelligence-risk-management-framework-generative-artificial-intelligence) | GenAI risk profile companion to AI RMF. | Useful for LLM/generative AI-specific risk categories. |
| 13 | NIST adversarial machine learning taxonomy | [www.nist.gov/publications/adversarial-machine-learning-taxonomy-and-terminology-attacks-and-mitigations](https://www.nist.gov/publications/adversarial-machine-learning-taxonomy-and-terminology-attacks-and-mitigations) | Taxonomy & terminology for adversarial ML attacks & mitigations. | Good for consistent AI vulnerability vocabulary. |
| 14 | MLCommons AI Safety | [mlcommons.org/working-groups/ai-safety](https://mlcommons.org/working-groups/ai-safety/) | AI safety benchmarks & working group context. | Useful for AI system risk evaluation, not direct CVE matching. |

[Back to index](#index)

---

## 5. Vendor, OS, distribution, container & package affectedness feeds

### 5.1 Scanner-oriented aggregators & vulnerability DB builders

| Sl. # | Title | Link(s) | Relevance | Notes & POIs |
|---:|---|---|---|---|
| 1 | NeuVector vul-dbgen | [github.com/neuvector/vul-dbgen](https://github.com/neuvector/vul-dbgen) | Vulnerability DB generation source originally flagged by this project. | Useful as a reference for aggregating distro/package vulnerability feeds. |
| 2 | NeuVector vul-source | [github.com/neuvector/vul-source](https://github.com/neuvector/vul-source) | Vulnerability source data used by NeuVector workflows. | Review for source coverage & feed normalization logic. |
| 3 | Aqua Trivy vulnerability docs | [trivy.dev/docs/latest/scanner/vulnerability](https://trivy.dev/docs/latest/scanner/vulnerability/) | Scanner behavior across OS packages, language packages, misconfig, Kubernetes, etc. | Useful for scanner semantics & supported target types. |
| 4 | Trivy DB | [github.com/aquasecurity/trivy-db](https://github.com/aquasecurity/trivy-db) | Converts raw advisories into Trivy DB format. | Useful for ingestion architecture & feed normalization patterns. |
| 5 | Trivy Java DB | [github.com/aquasecurity/trivy-java-db](https://github.com/aquasecurity/trivy-java-db) | Java-specific vulnerability database used by Trivy. | Useful for Maven/JAR matching. |
| 6 | Trivy database configuration docs | [trivy.dev/docs/latest/configuration/db](https://trivy.dev/docs/latest/configuration/db/) | Documents Trivy DB artifacts & configuration. | Useful for operational scanner deployment. |
| 7 | Anchore Grype | [github.com/anchore/grype](https://github.com/anchore/grype) | Vulnerability scanner for container images & filesystems. | Useful reference for SBOM-to-vuln matching. |
| 8 | Anchore Grype DB | [github.com/anchore/grype-db](https://github.com/anchore/grype-db) | Builds Grype vulnerability database from upstream sources. | Useful for feed normalization & source coverage comparison. |
| 9 | Anchore Syft | [github.com/anchore/syft](https://github.com/anchore/syft) | SBOM generation for scanning & exposure matching. | Pair with Grype for inventory-to-vulnerability workflow. |
| 10 | Quay ClairCore | [github.com/quay/claircore](https://github.com/quay/claircore) | Clair vulnerability matching engine core. | Useful for container security ingestion patterns. |
| 11 | Clair | [github.com/quay/clair](https://github.com/quay/clair) | Container vulnerability scanner. | Compare feed matching behavior with Trivy & Grype. |
| 12 | VulnerableCode | [github.com/nexB/vulnerablecode](https://github.com/nexB/vulnerablecode) | Open vulnerability DB aggregator. | Useful for importer coverage & open-source ingestion architecture. |
| 13 | VulnerableCode importer docs | [vulnerablecode.readthedocs.io/en/latest/importers_link.html](https://vulnerablecode.readthedocs.io/en/latest/importers_link.html) | Lists supported importer sources. | Good checklist for source coverage. |
| 14 | Dependency-Track | [dependencytrack.org](https://dependencytrack.org/) | SBOM-oriented vulnerability management platform. | Useful reference for BOM ingestion & component risk tracking. |
| 15 | Dependency-Track data sources | [docs.dependencytrack.org/datasources/overview](https://docs.dependencytrack.org/datasources/overview/) | Documents Dependency-Track data sources. | Useful for comparing source prioritization. |
| 16 | Dependency-Track GitHub Advisories datasource | [docs.dependencytrack.org/datasources/github-advisories](https://docs.dependencytrack.org/datasources/github-advisories/) | Mirrors GHSA via GitHub public GraphQL API. | Useful reference for GHSA ingestion. |
| 17 | OpenVAS / Greenbone Community Feed | [www.greenbone.net/en/community-feed](https://www.greenbone.net/en/community-feed/) | Network vulnerability test feed. | Useful for host/network exposure detection, not package-only matching. |
| 18 | Wazuh vulnerability detector | [documentation.wazuh.com/current/user-manual/capabilities/vulnerability-detection/index.html](https://documentation.wazuh.com/current/user-manual/capabilities/vulnerability-detection/index.html) | Endpoint vulnerability detection capability. | Useful for host-level package inventory & vuln matching behavior. |

### 5.2 Red Hat / RHEL / CentOS Stream

| Sl. # | Title | Link(s) | Relevance | Notes & POIs |
|---:|---|---|---|---|
| 1 | Red Hat Security Data | [access.redhat.com/security/data](https://access.redhat.com/security/data) | Red Hat CSAF/VEX, OSV, OVAL, CVE data. | Essential for RHEL affectedness & backport-aware status. |
| 2 | Red Hat Security Data API | [docs.redhat.com/en/documentation/red_hat_security_data_api/1.0/html-single/red_hat_security_data_api/index](https://docs.redhat.com/en/documentation/red_hat_security_data_api/1.0/html-single/red_hat_security_data_api/index) | API retrieves Red Hat CVE/advisory/security data. | Prefer API for automation; handle auth/rate constraints if applicable. |
| 3 | Red Hat CVE database | [access.redhat.com/security/security-updates/#/cve](https://access.redhat.com/security/security-updates/#/cve) | Red Hat CVE lookup. | Human-facing; use data APIs for automation. |
| 4 | Red Hat OVAL data | [www.redhat.com/security/data/oval](https://www.redhat.com/security/data/oval/) | OVAL definitions for vulnerability assessment. | Useful for scanner compatibility & package-state evaluation. |
| 5 | Red Hat CSAF/VEX guidance | [redhatproductsecurity.github.io/security-data-guidelines/csaf-vex](https://redhatproductsecurity.github.io/security-data-guidelines/csaf-vex/) | Explains Red Hat CSAF/VEX & product/package semantics. | Important for correct interpretation of affected/not-affected states. |
| 6 | Red Hat security advisories | [access.redhat.com/security/security-updates/#/security-advisories](https://access.redhat.com/security/security-updates/#/security-advisories) | Red Hat advisory listing. | Useful for patch/remediation references. |
| 7 | CentOS Stream security tracker | [gitlab.com/redhat/centos-stream/rpms](https://gitlab.com/redhat/centos-stream/rpms) | CentOS Stream package source context. | Use carefully; package repo state differs from security advisory truth. |

### 5.3 Debian

| Sl. # | Title | Link(s) | Relevance | Notes & POIs |
|---:|---|---|---|---|
| 1 | Debian Security Tracker | [security-tracker.debian.org](https://security-tracker.debian.org/) | Debian-specific package vulnerability status. | Essential for Debian affectedness & backported patches. |
| 2 | Debian Security Tracker JSON | [security-tracker.debian.org/tracker/data/json](https://security-tracker.debian.org/tracker/data/json) | Machine-readable Debian vulnerability data. | Primary automation source for Debian. |
| 3 | Debian Security Tracker source Git | [salsa.debian.org/security-tracker-team/security-tracker](https://salsa.debian.org/security-tracker-team/security-tracker) | Source repo for tracker data. | Useful for diffs, auditing, & local mirroring. |
| 4 | Debian Security Information | [www.debian.org/security](https://www.debian.org/security/) | Debian security notices & process context. | Useful for advisory references & manual review. |
| 5 | Debian Security Tracker docs | [security-team.debian.org/security_tracker.html](https://security-team.debian.org/security_tracker.html) | Explains Debian tracker semantics. | Important for interpreting statuses like fixed, vulnerable, ignored, or postponed. |
| 6 | Debian OVAL | [www.debian.org/security/oval](https://www.debian.org/security/oval/) | OVAL data for Debian vulnerability assessment. | Useful for scanner integrations. |

### 5.4 Ubuntu / Canonical

| Sl. # | Title | Link(s) | Relevance | Notes & POIs |
|---:|---|---|---|---|
| 1 | Ubuntu Security Notices | [ubuntu.com/security/notices](https://ubuntu.com/security/notices) | Ubuntu security notices for fixed packages. | Useful for patch references & release-specific remediation. |
| 2 | Ubuntu CVE reports | [ubuntu.com/security/cves](https://ubuntu.com/security/cves) | Ubuntu CVE tracking by package/release. | Important for Ubuntu affectedness & backport interpretation. |
| 3 | Ubuntu OVAL | [ubuntu.com/security/oval](https://ubuntu.com/security/oval) | OVAL data for vulnerability assessment & patch status. | Useful for scanner compatibility. |
| 4 | Ubuntu VEX data | [ubuntu.com/security/vex](https://ubuntu.com/security/vex) | Ubuntu VEX data. | Useful for affected/not-affected status & scanner false-positive reduction. |
| 5 | Ubuntu VEX docs | [documentation.ubuntu.com/security/security-updates/vex](https://documentation.ubuntu.com/security/security-updates/vex/) | Ubuntu VEX source documentation. | Important for interpreting Canonical VEX publication model. |
| 6 | Ubuntu Security Notices GitHub | [github.com/canonical/ubuntu-security-notices](https://github.com/canonical/ubuntu-security-notices) | USN/LSN JSON, OSV JSON, & OpenVEX JSON formats. | Strong automation source. Preserve format-specific semantics. |
| 7 | Ubuntu Security Tracker Git | [git.launchpad.net/ubuntu-cve-tracker](https://git.launchpad.net/ubuntu-cve-tracker) | Ubuntu CVE tracker source. | Useful for local mirroring & historical diffing. |
| 8 | Ubuntu security updates docs | [documentation.ubuntu.com/security/security-updates](https://documentation.ubuntu.com/security/security-updates/) | Ubuntu security update documentation. | Useful for process context & VEX/OVAL interpretation. |

### 5.5 Alpine

| Sl. # | Title | Link(s) | Relevance | Notes & POIs |
|---:|---|---|---|---|
| 1 | Alpine SecDB | [secdb.alpinelinux.org](https://secdb.alpinelinux.org/) | Current Alpine machine-readable security DB. | Primary Alpine ingestion source. |
| 2 | Alpine Security Tracker | [security.alpinelinux.org](https://security.alpinelinux.org/) | Tracks Alpine security issues. | Useful for human review & status context. |
| 3 | Alpine SecDB deprecated GitHub mirror | [github.com/alpinelinux/alpine-secdb](https://github.com/alpinelinux/alpine-secdb) | Historical Alpine SecDB mirror. | Deprecated; do not rely on it for current ingestion. |
| 4 | Alpine packages | [pkgs.alpinelinux.org/packages](https://pkgs.alpinelinux.org/packages) | Alpine package metadata. | Not a vulnerability DB, but helps resolve package names & versions. |

### 5.6 SUSE / openSUSE

| Sl. # | Title | Link(s) | Relevance | Notes & POIs |
|---:|---|---|---|---|
| 1 | SUSE CSAF | [www.suse.com/support/security/csaf](https://www.suse.com/support/security/csaf/) | SUSE CSAF advisory data. | Good for vendor-asserted affectedness & remediation states. |
| 2 | SUSE CVRF / OVAL security data | [www.suse.com/support/security/oval](https://www.suse.com/support/security/oval/) | SUSE OVAL/CVRF security data. | Useful for scanner compatibility & package-state evaluation. |
| 3 | SUSE CVE pages | [www.suse.com/security/cve](https://www.suse.com/security/cve/) | SUSE CVE lookup. | Human-facing; use machine-readable feeds when available. |
| 4 | SUSE Security Advisories | [www.suse.com/support/update/announcement](https://www.suse.com/support/update/announcement/) | SUSE security advisory listing. | Useful for remediation & patch references. |
| 5 | openSUSE Security Announce | [lists.opensuse.org/archives/list/security-announce@lists.opensuse.org](https://lists.opensuse.org/archives/list/security-announce@lists.opensuse.org/) | openSUSE security announcement mailing list archive. | Useful for distro-specific disclosure context. |

### 5.7 Oracle Linux

| Sl. # | Title | Link(s) | Relevance | Notes & POIs |
|---:|---|---|---|---|
| 1 | Oracle Security Alerts & Critical Patch Updates | [www.oracle.com/security-alerts](https://www.oracle.com/security-alerts/) | Oracle CPU, Security Alerts, third-party bulletins, & CVE mappings. | Oracle products often require vendor advisory interpretation beyond NVD. |
| 2 | Oracle Linux security data | [linux.oracle.com/security](https://linux.oracle.com/security/) | Oracle Linux security data. | Useful for Oracle Linux affectedness. |
| 3 | Oracle Linux OVAL | [linux.oracle.com/security/oval](https://linux.oracle.com/security/oval/) | Oracle Linux OVAL definitions. | Useful for scanner compatibility. |
| 4 | Oracle Linux errata | [linux.oracle.com/errata](https://linux.oracle.com/errata/) | Oracle Linux errata. | Use for patch mapping & fixed versions. |
| 5 | Oracle Linux CVE search | [linux.oracle.com/cve](https://linux.oracle.com/cve/) | Oracle Linux CVE lookup. | Human lookup source; pair with OVAL/errata for automation. |

### 5.8 Amazon Linux

| Sl. # | Title | Link(s) | Relevance | Notes & POIs |
|---:|---|---|---|---|
| 1 | Amazon Linux Security Center | [alas.aws.amazon.com](https://alas.aws.amazon.com/) | Amazon Linux security advisory portal. | Important for Amazon Linux package affectedness. |
| 2 | Amazon Linux 2 advisories | [alas.aws.amazon.com/alas2.html](https://alas.aws.amazon.com/alas2.html) | Amazon Linux 2 advisories. | Version-specific advisory stream. |
| 3 | Amazon Linux 2023 advisories | [alas.aws.amazon.com/AL2023](https://alas.aws.amazon.com/AL2023/) | Amazon Linux 2023 advisories. | Keep AL2 & AL2023 separate because package baselines differ. |
| 4 | AWS Security Bulletins | [aws.amazon.com/security/security-bulletins](https://aws.amazon.com/security/security-bulletins/) | AWS security bulletins for services & platforms. | Cloud-service affectedness may not map cleanly to package versions. |

### 5.9 Fedora, AlmaLinux, Rocky, Arch, Gentoo

| Sl. # | Title | Link(s) | Relevance | Notes & POIs |
|---:|---|---|---|---|
| 1 | Fedora security updates | [bodhi.fedoraproject.org/updates/?type=security](https://bodhi.fedoraproject.org/updates/?type=security) | Fedora security update advisories. | Useful for Fedora package remediation tracking. |
| 2 | Fedora packages | [packages.fedoraproject.org](https://packages.fedoraproject.org/) | Fedora package metadata. | Not a vulnerability DB, but useful for package identity & version resolution. |
| 3 | AlmaLinux Errata | [errata.almalinux.org](https://errata.almalinux.org/) | AlmaLinux errata & security advisories. | Useful for RHEL-compatible distro assessment. |
| 4 | AlmaLinux OSV data | [github.com/AlmaLinux/osv-database](https://github.com/AlmaLinux/osv-database) | AlmaLinux OSV-formatted data. | Good for OSV-based pipelines. |
| 5 | Rocky Linux security advisories | [errata.build.resf.org](https://errata.build.resf.org/) | Rocky Linux errata/security advisories. | Useful for RHEL-compatible distro assessment. |
| 6 | Arch Linux Security Tracker | [security.archlinux.org](https://security.archlinux.org/) | Arch Linux security tracker. | Rolling-release semantics differ from fixed-release distros. |
| 7 | Arch Linux security JSON | [security.archlinux.org/json](https://security.archlinux.org/json) | Machine-readable Arch security data. | Useful for automation. |
| 8 | Gentoo GLSA | [security.gentoo.org/glsa](https://security.gentoo.org/glsa/) | Gentoo Linux Security Advisories. | Useful for Gentoo package affectedness. |
| 9 | Gentoo GLSA XML | [security.gentoo.org/glsa/feed.rss](https://security.gentoo.org/glsa/feed.rss) | Gentoo GLSA RSS/XML feed. | Useful for feed-based monitoring. |

### 5.10 Wolfi / Chainguard

| Sl. # | Title | Link(s) | Relevance | Notes & POIs |
|---:|---|---|---|---|
| 1 | Wolfi OS advisories | [github.com/wolfi-dev/advisories](https://github.com/wolfi-dev/advisories) | Wolfi OS advisory data. | Important for modern minimal container images. |
| 2 | Wolfi SecDB generator | [github.com/wolfi-dev/secdb](https://github.com/wolfi-dev/secdb) | Generates Wolfi security DBs based on Alpine secdb format. | Useful for understanding feed generation semantics. |
| 3 | Wolfi OS feed | [packages.wolfi.dev/os/security.json](https://packages.wolfi.dev/os/security.json) | Wolfi package security feed. | Use this for Wolfi base images. |
| 4 | Chainguard Enterprise feed | [packages.cgr.dev/chainguard/security.json](https://packages.cgr.dev/chainguard/security.json) | Chainguard Enterprise package security feed. | Separate from Wolfi OS feed. |
| 5 | Chainguard security advisories docs | [edu.chainguard.dev/chainguard/chainguard-images/staying-secure/security-advisories/how-chainguard-issues](https://edu.chainguard.dev/chainguard/chainguard-images/staying-secure/security-advisories/how-chainguard-issues/) | Explains Chainguard advisory publication model. | Important for interpreting feed semantics & OSV/secdb transition. |
| 6 | Wolfi vulnerabilities in OSV | [osv.dev/list?ecosystem=Wolfi](https://osv.dev/list?ecosystem=Wolfi) | Wolfi ecosystem records in OSV. | Good for OSV-aligned ingestion. |
| 7 | Chainguard OSV advisory feed context | [www.chainguard.dev/unchained/chainguard-enhances-security-with-osv-advisory-feed](https://www.chainguard.dev/unchained/chainguard-enhances-security-with-osv-advisory-feed) | Context on Chainguard OSV advisory feed. | Blog/context source, not primary feed. |

[Back to index](#index)

---

## 6. Vendor advisories for enterprise impact assessment

### 6.1 Major OS, browser & platform vendors

| Sl. # | Title | Link(s) | Relevance | Notes & POIs |
|---:|---|---|---|---|
| 1 | Microsoft Security Update Guide | [msrc.microsoft.com/update-guide](https://msrc.microsoft.com/update-guide) | Microsoft vulnerability advisories, CVEs, affected products, & fixes. | Critical for Windows, Office, Exchange, Azure components, & enterprise Microsoft stack. |
| 2 | Microsoft MSRC blog | [msrc.microsoft.com/blog](https://msrc.microsoft.com/blog/) | Microsoft security research & advisory context. | Useful for exploitation context & urgent guidance. |
| 3 | Microsoft Security Response Center | [msrc.microsoft.com](https://msrc.microsoft.com/) | Microsoft security response portal. | Entry point for MSRC resources. |
| 4 | Apple Security Releases | [support.apple.com/en-us/100100](https://support.apple.com/en-us/100100) | Apple security release index. | Important for iOS, macOS, Safari, watchOS, tvOS, & ecosystem patch tracking. |
| 5 | Apple security updates | [support.apple.com/en-us/HT201222](https://support.apple.com/en-us/HT201222) | Apple security update listing. | Keep with newer Apple security release page for compatibility. |
| 6 | Google Android Security Bulletins | [source.android.com/docs/security/bulletin](https://source.android.com/docs/security/bulletin) | Android platform security bulletins. | Device/vendor patch latency may differ from bulletin availability. |
| 7 | Google Chrome Releases | [chromereleases.googleblog.com](https://chromereleases.googleblog.com/) | Chrome release announcements. | Security fixes are often disclosed with delayed details. |
| 8 | Chrome security advisories | [chromereleases.googleblog.com/search/label/Security](https://chromereleases.googleblog.com/search/label/Security) | Chrome security-specific release posts. | Good for urgent browser vulnerability tracking. |
| 9 | Chromium issue tracker | [issues.chromium.org](https://issues.chromium.org/) | Chromium issue tracking. | Security bugs may have restricted visibility until disclosure. |
| 10 | Mozilla Security Advisories | [www.mozilla.org/en-US/security/advisories](https://www.mozilla.org/en-US/security/advisories/) | Mozilla security advisories. | Important for Firefox, Thunderbird, & related products. |
| 11 | Mozilla Foundation Security Advisories | [www.mozilla.org/en-US/security/known-vulnerabilities](https://www.mozilla.org/en-US/security/known-vulnerabilities/) | Mozilla known vulnerabilities index. | Useful for historical advisory lookup. |
| 12 | Google Cloud Security Bulletins | [cloud.google.com/support/bulletins](https://cloud.google.com/support/bulletins) | Google Cloud service/product security bulletins. | Cloud advisories often require service-specific interpretation. |
| 13 | Kubernetes Security Announcements | [groups.google.com/g/kubernetes-security-announce](https://groups.google.com/g/kubernetes-security-announce) | Kubernetes security announcement mailing list. | Authoritative operational alerting channel for Kubernetes CVEs. |
| 14 | Kubernetes official CVE feed | [kubernetes.io/docs/reference/issues-security/official-cve-feed](https://kubernetes.io/docs/reference/issues-security/official-cve-feed/) | Official Kubernetes CVE feed reference. | Useful for automation & Kubernetes-specific CVE tracking. |
| 15 | Kubernetes security & disclosure | [kubernetes.io/docs/reference/issues-security/security](https://kubernetes.io/docs/reference/issues-security/security/) | Kubernetes security disclosure process. | Useful for understanding embargo, disclosure, & patch handling. |

### 6.2 Enterprise infrastructure vendors

| Sl. # | Title | Link(s) | Relevance | Notes & POIs |
|---:|---|---|---|---|
| 1 | Cisco Security Advisories | [sec.cloudapps.cisco.com/security/center/publicationListing.x](https://sec.cloudapps.cisco.com/security/center/publicationListing.x) | Cisco product advisories, affected versions, fixed versions, & workarounds. | Critical for network infrastructure exposure. |
| 2 | VMware / Broadcom Security Advisories | [support.broadcom.com/web/ecx/security-advisory](https://support.broadcom.com/web/ecx/security-advisory) | VMware/Broadcom security advisories. | Important for virtualization, ESXi, vCenter, & enterprise infrastructure. |
| 3 | Palo Alto Networks Security Advisories | [security.paloaltonetworks.com](https://security.paloaltonetworks.com/) | PAN-OS & Palo Alto product advisories. | Often includes exploited-in-the-wild notes & mitigation guidance. |
| 4 | Fortinet PSIRT Advisories | [www.fortiguard.com/psirt](https://www.fortiguard.com/psirt) | Fortinet product advisories. | Critical for perimeter devices; exploitability can change quickly. |
| 5 | Ivanti Security Advisories | [www.ivanti.com/resources/v/doc/ivi/2629/0e3e2be1e66d](https://www.ivanti.com/resources/v/doc/ivi/2629/0e3e2be1e66d) | Ivanti security advisories. | Track emergency advisories closely due to recurring exploitation patterns. |
| 6 | Citrix Security Bulletins | [support.citrix.com/securitybulletins](https://support.citrix.com/securitybulletins) | Citrix product security bulletins. | Useful for exposed remote access infrastructure. |
| 7 | F5 Security Advisories | [my.f5.com/manage/s/solutions?series=Security_Advisory](https://my.f5.com/manage/s/solutions?series=Security_Advisory) | F5 product security advisories. | Product modules/configuration affect exploitability. |
| 8 | Juniper Security Advisories | [supportportal.juniper.net/s/global-search/%40uri#sort=relevancy&f:ctype=[Security%20Advisories]](https://supportportal.juniper.net/s/global-search/%40uri#sort=relevancy&f:ctype=[Security%20Advisories]) | Juniper security advisory listing. | Useful for network infrastructure patching. |
| 9 | Dell Security Advisories | [www.dell.com/support/security](https://www.dell.com/support/security) | Dell product security advisories. | Covers firmware, hardware, drivers, & enterprise products. |
| 10 | HPE Security Bulletins | [support.hpe.com/hpesc/public/home](https://support.hpe.com/hpesc/public/home) | HPE security bulletins. | May require product filtering & support portal navigation. |
| 11 | Lenovo Product Security Advisories | [support.lenovo.com/us/en/product_security/home](https://support.lenovo.com/us/en/product_security/home) | Lenovo product security advisories. | Useful for firmware & device fleet management. |
| 12 | IBM PSIRT | [www.ibm.com/support/pages/ibm-psirt](https://www.ibm.com/support/pages/ibm-psirt) | IBM product security incident response. | Useful for IBM software/hardware exposure. |
| 13 | SAP Security Notes | [support.sap.com/en/my-support/knowledge-base/security-notes-news.html](https://support.sap.com/en/my-support/knowledge-base/security-notes-news.html) | SAP security notes & patch-day guidance. | May require SAP support access for full note details. |
| 14 | Adobe Security Bulletins | [helpx.adobe.com/security.html](https://helpx.adobe.com/security.html) | Adobe security bulletins. | Important for client-side & enterprise Adobe software. |
| 15 | Oracle Critical Patch Updates | [www.oracle.com/security-alerts](https://www.oracle.com/security-alerts/) | Oracle CPU, Security Alerts, & CVE mappings. | Oracle advisories often bundle many products; mapping requires product/version context. |
| 16 | Atlassian Security Advisories | [www.atlassian.com/trust/security/advisories](https://www.atlassian.com/trust/security/advisories) | Atlassian product advisories. | Important for exposed collaboration/dev tooling like Confluence & Jira. |
| 17 | Elastic Security Announcements | [discuss.elastic.co/c/announcements/security-announcements/31](https://discuss.elastic.co/c/announcements/security-announcements/31) | Elastic security announcements. | Useful for Elasticsearch/Kibana stack. |
| 18 | HashiCorp Security | [www.hashicorp.com/security](https://www.hashicorp.com/security) | HashiCorp security advisories & disclosure policy. | Relevant for Terraform, Vault, Consul, Nomad. |
| 19 | GitLab Security Releases | [about.gitlab.com/releases/categories/releases](https://about.gitlab.com/releases/categories/releases/) | GitLab release posts, including security releases. | Security releases may include multiple CVEs & version-specific patches. |
| 20 | Jenkins Security Advisories | [www.jenkins.io/security/advisories](https://www.jenkins.io/security/advisories/) | Jenkins core & plugin advisories. | Plugin affectedness is critical; inventory plugin versions. |
| 21 | Apache Security Reports | [www.apache.org/security](https://www.apache.org/security/) | Apache project security reports & process. | Many Apache projects have project-specific advisory pages. |
| 22 | Eclipse Security Advisories | [www.eclipse.org/security](https://www.eclipse.org/security/) | Eclipse project security advisories. | Useful for Java tooling & Eclipse projects. |
| 23 | WordPress Security Releases | [wordpress.org/news/category/security](https://wordpress.org/news/category/security/) | WordPress security release announcements. | Plugin/theme ecosystem needs separate assessment. |
| 24 | Drupal Security Advisories | [www.drupal.org/security](https://www.drupal.org/security) | Drupal core & contributed project advisories. | Module inventory matters for affectedness. |
| 25 | OpenSSL Vulnerabilities | [www.openssl.org/news/vulnerabilities.html](https://www.openssl.org/news/vulnerabilities.html) | OpenSSL vulnerability list. | Critical transitive dependency in many systems; patch status depends on bundled library versions. |
| 26 | OpenSSH release notes | [www.openssh.com/releasenotes.html](https://www.openssh.com/releasenotes.html) | OpenSSH release notes. | Security-relevant changes may appear in release notes. |
| 27 | curl security advisories | [curl.se/docs/security.html](https://curl.se/docs/security.html) | curl/libcurl security advisories. | Important for widely embedded dependency exposure. |

### 6.3 Cloud provider security bulletins

| Sl. # | Title | Link(s) | Relevance | Notes & POIs |
|---:|---|---|---|---|
| 1 | AWS Security Bulletins | [aws.amazon.com/security/security-bulletins](https://aws.amazon.com/security/security-bulletins/) | AWS service/product security bulletins. | Cloud provider advisories often require service/configuration context. |
| 2 | AWS Security Blog | [aws.amazon.com/blogs/security](https://aws.amazon.com/blogs/security/) | AWS security guidance & incident context. | Good for mitigation patterns, not canonical CVE data. |
| 3 | Google Cloud Security Bulletins | [cloud.google.com/support/bulletins](https://cloud.google.com/support/bulletins) | Google Cloud security bulletins. | Use with asset inventory & managed service exposure. |
| 4 | Google Cloud Security Blog | [cloud.google.com/blog/products/identity-security](https://cloud.google.com/blog/products/identity-security) | Google Cloud identity/security blog. | Useful for operational context & mitigations. |
| 5 | Microsoft Azure security / MSRC | [msrc.microsoft.com/update-guide](https://msrc.microsoft.com/update-guide) | Microsoft/Azure-related security updates. | Azure service advisories may require separate portal/status checks. |
| 6 | Azure updates | [azure.microsoft.com/en-us/updates](https://azure.microsoft.com/en-us/updates/) | Azure product update feed. | Not purely security-specific; filter carefully. |
| 7 | Oracle Cloud security | [www.oracle.com/security-alerts](https://www.oracle.com/security-alerts/) | Oracle cloud/product security alerts. | Oracle advisories often span cloud & on-prem products. |
| 8 | IBM Cloud security bulletins | [cloud.ibm.com/status/security](https://cloud.ibm.com/status/security) | IBM Cloud security bulletins. | Useful for managed service exposure. |

[Back to index](#index)

---

## 7. SBOM, package identity, VEX & advisory exchange standards

### 7.1 SBOM standards

| Sl. # | Title | Link(s) | Relevance | Notes & POIs |
|---:|---|---|---|---|
| 1 | CycloneDX specification overview | [cyclonedx.org/specification/overview](https://cyclonedx.org/specification/overview/) | SBOM, SaaSBOM, BOM, VEX, vulnerability & component metadata standard. | Good fit for vulnerability management workflows due to vulnerability & VEX support. |
| 2 | CycloneDX GitHub | [github.com/CycloneDX/specification](https://github.com/CycloneDX/specification) | CycloneDX specification source repository. | Use for versioned spec tracking. |
| 3 | CycloneDX VEX | [cyclonedx.org/capabilities/vex](https://cyclonedx.org/capabilities/vex/) | CycloneDX VEX capability documentation. | Useful for affected/not-affected communication. |
| 4 | SPDX specifications | [spdx.dev/specifications](https://spdx.dev/specifications/) | SPDX specifications for software bills of materials & package metadata. | SPDX is widely used for license/package metadata & supply-chain exchange. |
| 5 | SPDX 3.0.1 spec | [spdx.github.io/spdx-spec/v3.0.1](https://spdx.github.io/spdx-spec/v3.0.1/) | SPDX 3.0.1 specification. | Track spec version compatibility in parsers. |
| 6 | SPDX package URL property | [spdx.github.io/spdx-spec/v3.0.1/model/Software/Properties/packageUrl](https://spdx.github.io/spdx-spec/v3.0.1/model/Software/Properties/packageUrl/) | SPDX support for package URL property. | Important for PURL-based vulnerability matching. |
| 7 | SPDX GitHub | [github.com/spdx/spdx-spec](https://github.com/spdx/spdx-spec) | SPDX specification repository. | Use for release tracking & schema/source inspection. |
| 8 | NTIA SBOM resources | [www.ntia.gov/page/software-bill-materials](https://www.ntia.gov/page/software-bill-materials) | SBOM policy & foundational resources. | Useful for governance & compliance context. |
| 9 | CISA SBOM | [www.cisa.gov/sbom](https://www.cisa.gov/sbom) | CISA SBOM guidance & resources. | Useful for U.S. public-sector & enterprise SBOM program alignment. |

### 7.2 Package & software identity

| Sl. # | Title | Link(s) | Relevance | Notes & POIs |
|---:|---|---|---|---|
| 1 | Package URL - PURL spec | [github.com/package-url/purl-spec](https://github.com/package-url/purl-spec) | Standard package identifier used in SBOMs & vulnerability DBs. | Crucial for OSV & package ecosystem matching. |
| 2 | PURL types | [github.com/package-url/purl-spec/blob/master/PURL-TYPES.rst](https://github.com/package-url/purl-spec/blob/master/PURL-TYPES.rst) | Defines PURL types per ecosystem. | Helps normalize ecosystem-specific package coordinates. |
| 3 | CPE specification / dictionary | [nvd.nist.gov/products/cpe](https://nvd.nist.gov/products/cpe) | Product naming & CPE dictionary. | Useful for product/platform matching, but can be imprecise for packages. |
| 4 | NVD CPE API | [nvd.nist.gov/developers/products](https://nvd.nist.gov/developers/products) | Programmatic CPE dictionary access. | Required for automated CPE matching workflows. |
| 5 | SWID tags - NIST | [csrc.nist.gov/projects/software-identification-swid](https://csrc.nist.gov/projects/software-identification-swid) | Software Identification Tags for installed software identity. | Useful in enterprise asset inventory & compliance. |
| 6 | GS1 Digital Link / identifiers | [www.gs1.org/standards/gs1-digital-link](https://www.gs1.org/standards/gs1-digital-link) | Optional identity standard for physical/embedded supply chains. | Not a vulnerability standard, but can matter in hardware/product traceability. |
| 7 | Software Heritage IDs | [www.swhid.org](https://www.swhid.org/) | Persistent source-code artifact identity. | Useful for source provenance & precise code artifact references. |

### 7.3 Advisory exchange, CSAF & VEX

| Sl. # | Title | Link(s) | Relevance | Notes & POIs |
|---:|---|---|---|---|
| 1 | OASIS CSAF 2.0 specification | [docs.oasis-open.org/csaf/csaf/v2.0/os/csaf-v2.0-os.html](https://docs.oasis-open.org/csaf/csaf/v2.0/os/csaf-v2.0-os.html) | Common Security Advisory Framework for structured advisories. | CSAF can express product status, remediation, impact, & VEX-like affectedness. |
| 2 | CSAF home | [www.csaf.io](https://www.csaf.io/) | CSAF ecosystem & tooling hub. | Good starting point for CSAF adoption. |
| 3 | OpenVEX specification | [github.com/openvex/spec](https://github.com/openvex/spec) | Minimal JSON-LD VEX format based on CISA VEX requirements. | Useful for communicating not-affected/fixed/affected status. |
| 4 | OpenVEX project page | [openssf.org/projects/openvex](https://openssf.org/projects/openvex/) | OpenSSF project page for OpenVEX. | Project-level overview. |
| 5 | CISA Minimum Requirements for VEX | [www.cisa.gov/sites/default/files/2023-04/minimum-requirements-for-vex-508c.pdf](https://www.cisa.gov/sites/default/files/2023-04/minimum-requirements-for-vex-508c.pdf) | Baseline VEX requirements. | Useful for evaluating VEX completeness. |
| 6 | OpenSSF VDR, VEX, OpenVEX & CSAF explainer | [openssf.org/blog/2023/09/07/vdr-vex-openvex-and-csaf](https://openssf.org/blog/2023/09/07/vdr-vex-openvex-and-csaf/) | Explains VDR, VEX, OpenVEX, & CSAF. | Useful for conceptual alignment & terminology. |
| 7 | Red Hat CSAF/VEX guidance | [redhatproductsecurity.github.io/security-data-guidelines/csaf-vex](https://redhatproductsecurity.github.io/security-data-guidelines/csaf-vex/) | Red Hat CSAF/VEX semantics & usage guidance. | Important for vendor-specific interpretation. |
| 8 | Ubuntu VEX | [ubuntu.com/security/vex](https://ubuntu.com/security/vex) | Ubuntu VEX data entry point. | Useful for Ubuntu affectedness & false-positive reduction. |
| 9 | Canonical Ubuntu Security Notices repo - OSV & OpenVEX | [github.com/canonical/ubuntu-security-notices](https://github.com/canonical/ubuntu-security-notices) | Canonical USN/LSN, OSV, & OpenVEX JSON data. | Strong machine-readable source for Ubuntu security status. |

[Back to index](#index)

---

## 8. Malicious package, supply-chain compromise & package reputation sources

### 8.1 Malicious package databases

| Sl. # | Title | Link(s) | Relevance | Notes & POIs |
|---:|---|---|---|---|
| 1 | OpenSSF Malicious Packages repository | [github.com/ossf/malicious-packages](https://github.com/ossf/malicious-packages) | Public malicious package reports consumable via OSV format. | Covers malicious packages, which may not be CVEs. |
| 2 | OpenSSF Malicious Packages announcement | [openssf.org/blog/2023/10/12/introducing-openssfs-malicious-packages-repository](https://openssf.org/blog/2023/10/12/introducing-openssfs-malicious-packages-repository/) | Explains the public DB for malicious package reports. | Context source, not the primary data feed. |
| 3 | OpenSSF Package Analysis | [openssf.org/package-analysis](https://openssf.org/package-analysis/) | Detects malicious package behavior & informs package consumers. | Behavioral analysis may surface packages before CVE/advisory assignment. |
| 4 | OpenSSF Package Analysis GitHub | [github.com/ossf/package-analysis](https://github.com/ossf/package-analysis) | Open-source package analysis system. | Useful for detection logic & behavioral signal review. |
| 5 | OpenSSF Package Feeds | [github.com/ossf/package-feeds](https://github.com/ossf/package-feeds) | Package ecosystem feed monitoring. | Useful for observing new packages in ecosystems. |
| 6 | GitHub malware advisories | [github.com/advisories?query=type%3Amalware](https://github.com/advisories?query=type%3Amalware) | GitHub malware advisories across ecosystems. | Treat as supply-chain compromise data, not conventional vuln data. |
| 7 | npm malware advisories via GitHub | [github.com/advisories?query=ecosystem%3Anpm+type%3Amalware](https://github.com/advisories?query=ecosystem%3Anpm+type%3Amalware) | npm-specific malware advisories. | npm has high malicious package volume; prioritize transitive dependency visibility. |
| 8 | PyPI malware advisories via GitHub | [github.com/advisories?query=ecosystem%3Apip+type%3Amalware](https://github.com/advisories?query=ecosystem%3Apip+type%3Amalware) | PyPI-specific malware advisories. | Use with lockfiles & package provenance checks. |
| 9 | Socket.dev blog | [socket.dev/blog](https://socket.dev/blog) | Supply-chain attack research & malicious package analysis. | Research feed; verify indicators before automated blocking. |
| 10 | Snyk vulnerability database | [security.snyk.io](https://security.snyk.io/) | Snyk vulnerability & package risk database. | Commercial/community source; validate licensing & provenance. |
| 11 | Sonatype OSS Index | [ossindex.sonatype.org](https://ossindex.sonatype.org/) | OSS vulnerability intelligence. | Useful for package risk enrichment. |
| 12 | Sonatype vulnerability database | [sonatype.com/resources/vulnerability-database](https://sonatype.com/resources/vulnerability-database) | Sonatype vulnerability database. | Good secondary enrichment source. |
| 13 | Phylum research | [blog.phylum.io](https://blog.phylum.io/) | Software supply-chain attack research. | Research source; useful for malicious package trends. |
| 14 | ReversingLabs threat research | [www.reversinglabs.com/blog](https://www.reversinglabs.com/blog) | Threat research focused on malware & supply-chain compromise. | Use for context, not as canonical package advisory data. |
| 15 | Checkmarx supply-chain research | [checkmarx.com/blog](https://checkmarx.com/blog/) | Supply-chain & application security research. | Useful for emerging package attack patterns. |

### 8.2 Package reputation / dependency health

| Sl. # | Title | Link(s) | Relevance | Notes & POIs |
|---:|---|---|---|---|
| 1 | OpenSSF Scorecard | [github.com/ossf/scorecard](https://github.com/ossf/scorecard) | Scores open-source project security practices. | Useful as dependency risk signal, not vulnerability proof. |
| 2 | OpenSSF Scorecard API | [api.securityscorecards.dev](https://api.securityscorecards.dev/) | API for Scorecard results. | Use with timestamped results because scores change over time. |
| 3 | OpenSSF Best Practices Badge | [www.bestpractices.dev](https://www.bestpractices.dev/) | Project best-practices badge program. | Useful project maturity signal, not vulnerability evidence. |
| 4 | deps.dev | [deps.dev](https://deps.dev/) | Dependency metadata, transitive dependencies, security signals. | Useful for dependency graphing & package metadata. |
| 5 | OpenSSF GUAC | [guac.sh](https://guac.sh/) | Graph for software supply-chain metadata. | Useful for correlating SBOMs, attestations, vulnerabilities, & provenance. |
| 6 | GUAC GitHub | [github.com/guacsec/guac](https://github.com/guacsec/guac) | GUAC implementation repository. | Reference architecture for supply-chain knowledge graphs. |
| 7 | Sigstore | [www.sigstore.dev](https://www.sigstore.dev/) | Signing & verification for software artifacts. | Helps assess provenance & tamper resistance. |
| 8 | Rekor transparency log | [docs.sigstore.dev/logging/overview](https://docs.sigstore.dev/logging/overview/) | Transparency log for signed artifacts. | Useful for provenance verification & audit trails. |
| 9 | SLSA framework | [slsa.dev](https://slsa.dev/) | Supply-chain Levels for Software Artifacts. | Helps assess build integrity & supply-chain hardening. |

[Back to index](#index)

---

## 9. Automated vulnerability detection, static analysis, dynamic analysis & research datasets

### 9.1 SAST / code query engines

| Sl. # | Title | Link(s) | Relevance | Notes & POIs |
|---:|---|---|---|---|
| 1 | CodeQL | [codeql.github.com](https://codeql.github.com/) | Semantic code analysis engine for vulnerability discovery. | Strong for variant analysis & source-level detection. |
| 2 | CodeQL GitHub | [github.com/github/codeql](https://github.com/github/codeql) | CodeQL source & query repository. | Use query packs for detection logic examples. |
| 3 | CodeQL query packs | [github.com/github/codeql/tree/main](https://github.com/github/codeql/tree/main) | Query packs for multiple languages. | Queries can be adapted for custom vuln detection. |
| 4 | Semgrep | [semgrep.dev](https://semgrep.dev/) | Pattern-based static analysis. | Good for fast custom rule writing. |
| 5 | Semgrep rules | [github.com/semgrep/semgrep-rules](https://github.com/semgrep/semgrep-rules) | Community/official Semgrep rules. | Validate rule precision before production blocking. |
| 6 | Joern | [joern.io](https://joern.io/) | Code property graph platform. | Useful for research-grade vulnerability discovery. |
| 7 | Joern GitHub | [github.com/joernio/joern](https://github.com/joernio/joern) | Joern implementation. | Useful for custom graph queries & ML pipelines. |
| 8 | Facebook Infer | [fbinfer.com](https://fbinfer.com/) | Static analyzer for multiple languages. | Useful for null deref, resource leaks, concurrency, & related bug classes. |
| 9 | Infer GitHub | [github.com/facebook/infer](https://github.com/facebook/infer) | Infer source repository. | Reference implementation. |
| 10 | SonarQube rules | [rules.sonarsource.com](https://rules.sonarsource.com/) | SonarSource rule catalog. | Useful for mapping code quality/security rules to weakness classes. |
| 11 | Bandit - Python | [github.com/PyCQA/bandit](https://github.com/PyCQA/bandit) | Python security linter. | Useful for Python SAST coverage. |
| 12 | Gosec - Go | [github.com/securego/gosec](https://github.com/securego/gosec) | Go security checker. | Useful for Go SAST. |
| 13 | ESLint security plugin | [github.com/eslint-community/eslint-plugin-security](https://github.com/eslint-community/eslint-plugin-security) | JavaScript security lint rules. | Useful for JS static checks. |
| 14 | SpotBugs | [spotbugs.github.io](https://spotbugs.github.io/) | Java static analysis. | General bug detection; pair with FindSecBugs for security. |
| 15 | FindSecBugs | [find-sec-bugs.github.io](https://find-sec-bugs.github.io/) | Java security bug detection plugin. | Useful for Java/JVM SAST. |
| 16 | Clang Static Analyzer | [clang-analyzer.llvm.org](https://clang-analyzer.llvm.org/) | C/C++/Objective-C static analyzer. | Useful for native code vulnerability classes. |
| 17 | Cppcheck | [cppcheck.sourceforge.io](https://cppcheck.sourceforge.io/) | C/C++ static analyzer. | Complements compiler analyzers. |
| 18 | Flawfinder | [dwheeler.com/flawfinder](https://dwheeler.com/flawfinder/) | C/C++ security scanner for dangerous functions. | Fast heuristic scanner with false-positive risk. |
| 19 | Brakeman - Ruby on Rails | [brakemanscanner.org](https://brakemanscanner.org/) | Ruby on Rails static security scanner. | Useful for Rails-specific vulnerability patterns. |
| 20 | Horusec | [github.com/ZupIT/horusec](https://github.com/ZupIT/horusec) | Multi-language security scanner. | Useful for broad SAST coverage. |
| 21 | Bearer | [github.com/Bearer/bearer](https://github.com/Bearer/bearer) | Code security/privacy scanner. | Useful for data-flow & sensitive data exposure detection. |
| 22 | MobSF | [github.com/MobSF/Mobile-Security-Framework-MobSF](https://github.com/MobSF/Mobile-Security-Framework-MobSF) | Mobile security testing framework. | Useful for Android/iOS static & dynamic app analysis. |

### 9.2 DAST, IAST, fuzzing & dynamic test sources

| Sl. # | Title | Link(s) | Relevance | Notes & POIs |
|---:|---|---|---|---|
| 1 | OSS-Fuzz | [google.github.io/oss-fuzz](https://google.github.io/oss-fuzz/) | Continuous fuzzing for open-source projects. | Useful for vulnerability discovery & bug lifecycle data. |
| 2 | OSS-Fuzz GitHub | [github.com/google/oss-fuzz](https://github.com/google/oss-fuzz) | OSS-Fuzz project configuration repository. | Useful for project fuzzing coverage & harness examples. |
| 3 | OSS-Fuzz vulnerability data in OSV | [osv.dev/list?ecosystem=OSS-Fuzz](https://osv.dev/list?ecosystem=OSS-Fuzz) | OSV records from OSS-Fuzz vulnerabilities. | Good for linking fuzz-discovered vulnerabilities to OSV schema. |
| 4 | ClusterFuzzLite | [google.github.io/clusterfuzzlite](https://google.github.io/clusterfuzzlite/) | Lightweight continuous fuzzing for CI/CD. | Useful for integrating fuzzing into development pipelines. |
| 5 | AFL++ | [github.com/AFLplusplus/AFLplusplus](https://github.com/AFLplusplus/AFLplusplus) | Coverage-guided fuzzer. | Good for native code vulnerability discovery. |
| 6 | libFuzzer | [llvm.org/docs/LibFuzzer.html](https://llvm.org/docs/LibFuzzer.html) | In-process coverage-guided fuzzer. | Common with LLVM sanitizers. |
| 7 | Honggfuzz | [github.com/google/honggfuzz](https://github.com/google/honggfuzz) | Security-oriented fuzzer. | Useful for native code dynamic testing. |
| 8 | Jazzer | [github.com/CodeIntelligenceTesting/jazzer](https://github.com/CodeIntelligenceTesting/jazzer) | JVM fuzzing engine. | Useful for Java/Kotlin fuzz testing. |
| 9 | OWASP ZAP | [www.zaproxy.org](https://www.zaproxy.org/) | Web application dynamic security scanner. | Useful for DAST & app exposure validation. |
| 10 | Nuclei | [github.com/projectdiscovery/nuclei](https://github.com/projectdiscovery/nuclei) | Template-based vulnerability & exposure scanner. | Useful for automated exposed-service checks. |
| 11 | Nuclei templates | [github.com/projectdiscovery/nuclei-templates](https://github.com/projectdiscovery/nuclei-templates) | Community/official detection templates. | Template quality varies; review false-positive potential. |

### 9.3 Vulnerability-detection research datasets

| Sl. # | Title | Link(s) | Relevance | Notes & POIs |
|---:|---|---|---|---|
| 1 | NIST SARD | [samate.nist.gov/SARD](https://samate.nist.gov/SARD/) | Software Assurance Reference Dataset. | Useful for evaluating static analysis tools & ML models. |
| 2 | Juliet Test Suite - NIST SARD | [samate.nist.gov/SARD/test-suites/112](https://samate.nist.gov/SARD/test-suites/112) | Synthetic test cases for many vulnerability classes. | Useful for controlled evaluation, but may not reflect real-world code complexity. |
| 3 | Big-Vul | [github.com/ZeoVan/MSR_20_Code_vulnerability_CSV_Dataset](https://github.com/ZeoVan/MSR_20_Code_vulnerability_CSV_Dataset) | Large vulnerability dataset derived from real-world CVE-fix commits. | Validate deduplication, labels, & train/test leakage. |
| 4 | Devign | [sites.google.com/view/devign](https://sites.google.com/view/devign) | Vulnerability detection dataset. | Used in ML vuln detection research. |
| 5 | Draper VDISC | [osf.io/d45bw](https://osf.io/d45bw/) | Vulnerability discovery dataset. | Useful for ML baselines; inspect labeling quality. |
| 6 | DiverseVul | [github.com/wagner-group/diversevul](https://github.com/wagner-group/diversevul) | Diverse vulnerability dataset. | Useful for model training/evaluation; check license & label quality. |
| 7 | PrimeVul | [github.com/DLVulDet/PrimeVul](https://github.com/DLVulDet/PrimeVul) | Vulnerability detection benchmark dataset. | Useful for modern ML vulnerability detection benchmarking. |
| 8 | MegaVul | [github.com/Icyrockton/MegaVul](https://github.com/Icyrockton/MegaVul) | Large-scale vulnerability dataset. | Validate methodology before using as labels. |
| 9 | Vul4J | [github.com/tuhh-softsec/vul4j](https://github.com/tuhh-softsec/vul4j) | Java vulnerability benchmark. | Useful for Java-focused vulnerability repair/detection. |
| 10 | VulnCode-DB | [github.com/vegardit/vulncode-db](https://github.com/vegardit/vulncode-db) | Vulnerable code examples. | Useful for examples & tests. |
| 11 | SecurityEval | [github.com/s2e-lab/SecurityEval](https://github.com/s2e-lab/SecurityEval) | Security-focused benchmark. | Useful for evaluating generated code or models. |
| 12 | CVEfixes | [github.com/secureIT-project/CVEfixes](https://github.com/secureIT-project/CVEfixes) | Links CVEs to fixing commits. | Useful for root-cause, patch, & ML training pipelines. |
| 13 | Defects4J | [github.com/rjust/defects4j](https://github.com/rjust/defects4j) | Java bug dataset. | Not vulnerability-specific, but useful for bug repair baselines. |
| 14 | ManySStuBs4J | [github.com/mast-group/mineSStuBs](https://github.com/mast-group/mineSStuBs) | Java simple bug dataset. | Not vulnerability-specific, but useful for bug-fix modeling. |
| 15 | VulDeePecker | [github.com/CGCL-codes/VulDeePecker](https://github.com/CGCL-codes/VulDeePecker) | Deep-learning vulnerability detection dataset/tooling. | Older benchmark; inspect for duplication & outdated methodology. |

[Back to index](#index)

---

## 10. ICS, OT, IoT, embedded & medical-device sources

### 10.1 CISA ICS / medical

| Sl. # | Title | Link(s) | Relevance | Notes & POIs |
|---:|---|---|---|---|
| 1 | CISA ICS Advisories | [www.cisa.gov/news-events/ics-advisories](https://www.cisa.gov/news-events/ics-advisories) | Industrial Control System advisories. | Critical for OT/ICS environments where patching constraints differ from IT. |
| 2 | CISA ICS Medical Advisories | [www.cisa.gov/news-events/ics-medical-advisories](https://www.cisa.gov/news-events/ics-medical-advisories) | Medical device security advisories. | Impact includes patient safety, regulatory, & operational risk. |
| 3 | CISA cybersecurity advisories | [www.cisa.gov/cybersecurity-advisories](https://www.cisa.gov/cybersecurity-advisories) | CISA cybersecurity advisory hub. | Broader than ICS; use for campaigns & emergent threats. |
| 4 | ICS-CERT advisories archive | [www.cisa.gov/news-events/ics-advisories](https://www.cisa.gov/news-events/ics-advisories) | ICS-CERT advisory archive path. | Same URL as ICS advisories, preserved for historical naming. |
| 5 | CISA ICS recommended practices | [www.cisa.gov/resources-tools/resources/ics-recommended-practices](https://www.cisa.gov/resources-tools/resources/ics-recommended-practices) | Recommended practices for ICS security. | Useful for mitigation where patching is delayed or impossible. |

### 10.2 OT / ICS vendor advisories

| Sl. # | Title | Link(s) | Relevance | Notes & POIs |
|---:|---|---|---|---|
| 1 | Siemens ProductCERT | [cert-portal.siemens.com/productcert](https://cert-portal.siemens.com/productcert/) | Siemens product security advisories. | Critical for industrial environments. |
| 2 | Schneider Electric Security Notifications | [www.se.com/ww/en/work/support/cybersecurity/security-notifications.jsp](https://www.se.com/ww/en/work/support/cybersecurity/security-notifications.jsp) | Schneider Electric security notifications. | Product model & firmware version matter heavily. |
| 3 | Rockwell Automation Security Advisories | [www.rockwellautomation.com/en-us/support/product/product-security-advisories.html](https://www.rockwellautomation.com/en-us/support/product/product-security-advisories.html) | Rockwell Automation product advisories. | Operational constraints may affect remediation. |
| 4 | Honeywell Product Security | [www.honeywell.com/us/en/product-security](https://www.honeywell.com/us/en/product-security) | Honeywell product security advisories. | Useful for OT product risk. |
| 5 | Philips Product Security | [www.philips.com/a-w/security/security-advisories.html](https://www.philips.com/a-w/security/security-advisories.html) | Philips medical/product security advisories. | Patient safety & regulatory implications may affect severity assessment. |
| 6 | GE Vernova Product Security | [www.gevernova.com/product-security](https://www.gevernova.com/product-security) | GE Vernova product security. | Important for energy/industrial systems. |
| 7 | ABB Cyber Security Alerts | [global.abb/group/en/technology/cyber-security/alerts-and-notifications](https://global.abb/group/en/technology/cyber-security/alerts-and-notifications) | ABB cyber security alerts & notifications. | Product-specific affectedness matters. |
| 8 | Yokogawa Security Advisories | [www.yokogawa.com/library/resources/white-papers/yokogawa-security-advisory-report-list](https://www.yokogawa.com/library/resources/white-papers/yokogawa-security-advisory-report-list/) | Yokogawa advisory report list. | Useful for OT control systems. |
| 9 | Mitsubishi Electric PSIRT | [www.mitsubishielectric.com/en/psirt/vulnerability](https://www.mitsubishielectric.com/en/psirt/vulnerability/) | Mitsubishi Electric vulnerability advisories. | Important for industrial equipment & automation. |
| 10 | Johnson Controls Product Security Advisories | [www.johnsoncontrols.com/cyber-solutions/security-advisories](https://www.johnsoncontrols.com/cyber-solutions/security-advisories) | Johnson Controls security advisories. | Relevant to building management & OT environments. |

### 10.3 IoT / embedded

| Sl. # | Title | Link(s) | Relevance | Notes & POIs |
|---:|---|---|---|---|
| 1 | CERT/CC Vulnerability Notes | [www.kb.cert.org/vuls](https://www.kb.cert.org/vuls/) | Coordinated disclosure notes, often with embedded/IoT affected vendors. | Useful when many vendors share a vulnerable component. |
| 2 | IoT Security Foundation | [www.iotsecurityfoundation.org](https://www.iotsecurityfoundation.org/) | IoT security guidance & resources. | Not a vulnerability feed, but useful for control mapping. |
| 3 | Firmware Analysis and Comparison Tool - FACT | [github.com/fkie-cad/FACT_core](https://github.com/fkie-cad/FACT_core) | Firmware analysis platform. | Useful for extracting components & embedded vuln detection. |
| 4 | EMBA firmware analyzer | [github.com/e-m-b-a/emba](https://github.com/e-m-b-a/emba) | Firmware analyzer for embedded Linux/IoT. | Useful for SBOM-like extraction & vulnerability assessment. |
| 5 | Binwalk | [github.com/ReFirmLabs/binwalk](https://github.com/ReFirmLabs/binwalk) | Firmware extraction & analysis tool. | Useful precursor for embedded component discovery. |

[Back to index](#index)

---

## 11. Exposure, internet-facing asset & threat telemetry

### 11.1 Internet exposure search engines

| Sl. # | Title | Link(s) | Relevance | Notes & POIs |
|---:|---|---|---|---|
| 1 | Censys Search | [search.censys.io](https://search.censys.io/) | Internet exposure search engine. | Useful for determining if vulnerable services are internet-facing. |
| 2 | Censys API | [search.censys.io/api](https://search.censys.io/api) | Programmatic Censys access. | API terms & quotas may apply. |
| 3 | Shodan | [www.shodan.io](https://www.shodan.io/) | Internet-connected device search. | Useful for exposure discovery & banner-based matching. |
| 4 | Shodan developer API | [developer.shodan.io](https://developer.shodan.io/) | Shodan API documentation. | Useful for automation. |
| 5 | ZoomEye | [www.zoomeye.org](https://www.zoomeye.org/) | Internet asset search engine. | Useful as additional exposure telemetry. |
| 6 | FOFA | [fofa.info](https://fofa.info/) | Internet asset search. | Coverage & access terms vary. |
| 7 | BinaryEdge | [www.binaryedge.io](https://www.binaryedge.io/) | Internet scanning & threat intelligence. | Useful for external exposure enrichment. |
| 8 | Onyphe | [www.onyphe.io](https://www.onyphe.io/) | Cyber defense search engine. | Useful for passive/active exposure context. |
| 9 | SecurityTrails | [securitytrails.com](https://securitytrails.com/) | DNS & asset intelligence. | Useful for attack surface discovery. |
| 10 | InternetDB by Shodan | [internetdb.shodan.io](https://internetdb.shodan.io/) | Lightweight Shodan InternetDB API. | Useful for quick IP exposure enrichment. |

### 11.2 Scan/exploitation telemetry

| Sl. # | Title | Link(s) | Relevance | Notes & POIs |
|---:|---|---|---|---|
| 1 | GreyNoise Visualizer | [viz.greynoise.io](https://viz.greynoise.io/) | Internet scanning/exploitation telemetry. | Helps separate background scanning from targeted activity. |
| 2 | GreyNoise API docs | [docs.greynoise.io](https://docs.greynoise.io/) | API docs for GreyNoise enrichment. | Useful for automated telemetry enrichment. |
| 3 | Shadowserver | [www.shadowserver.org](https://www.shadowserver.org/) | Internet-scale exposure & threat telemetry. | Good for population-level exposure signals. |
| 4 | Shadowserver reports | [dashboard.shadowserver.org](https://dashboard.shadowserver.org/) | Shadowserver reporting dashboard. | Access/eligibility may vary. |
| 5 | SANS Internet Storm Center | [isc.sans.edu](https://isc.sans.edu/) | Internet threat telemetry & diary reports. | Useful for emergent exploitation context. |
| 6 | Honeynet Project | [www.honeynet.org](https://www.honeynet.org/) | Honeypot & threat research. | Useful for attacker behavior insight. |
| 7 | DShield | [www.dshield.org](https://www.dshield.org/) | Distributed intrusion detection & telemetry. | Useful for broad scanning trend analysis. |
| 8 | LeakIX | [leakix.net](https://leakix.net/) | Exposed service & leak search. | Useful for exposure assessment. |
| 9 | urlscan.io | [urlscan.io](https://urlscan.io/) | URL scanning & web telemetry. | Useful for phishing, web exposure, & IOC enrichment. |
| 10 | VirusTotal | [www.virustotal.com](https://www.virustotal.com/) | File, URL, domain, & IP reputation. | Useful for malware/IOC enrichment; licensing constraints apply. |
| 11 | VirusTotal API | [docs.virustotal.com/reference/overview](https://docs.virustotal.com/reference/overview) | VirusTotal API documentation. | API quota & data-sharing policies matter. |

### 11.3 Attack surface management context

| Sl. # | Title | Link(s) | Relevance | Notes & POIs |
|---:|---|---|---|---|
| 1 | Amass | [github.com/owasp-amass/amass](https://github.com/owasp-amass/amass) | Attack surface mapping & DNS enumeration. | Useful for external asset discovery. |
| 2 | ProjectDiscovery Subfinder | [github.com/projectdiscovery/subfinder](https://github.com/projectdiscovery/subfinder) | Subdomain discovery. | Useful for asset inventory enrichment. |
| 3 | httpx | [github.com/projectdiscovery/httpx](https://github.com/projectdiscovery/httpx) | HTTP probing toolkit. | Useful for validating exposed services. |
| 4 | Naabu | [github.com/projectdiscovery/naabu](https://github.com/projectdiscovery/naabu) | Port scanner. | Useful for fast exposure discovery. |
| 5 | Nmap | [nmap.org](https://nmap.org/) | Network discovery & security auditing. | Mature scanner for service detection & scripts. |
| 6 | Masscan | [github.com/robertdavidgraham/masscan](https://github.com/robertdavidgraham/masscan) | High-speed port scanner. | Use carefully; scan authorization & network impact matter. |

[Back to index](#index)

---

## 12. Threat intelligence, malware, ransomware & in-the-wild exploitation context

### 12.1 Major threat research sources

| Sl. # | Title | Link(s) | Relevance | Notes & POIs |
|---:|---|---|---|---|
| 1 | Mandiant / Google Cloud Threat Intelligence | [cloud.google.com/blog/topics/threat-intelligence](https://cloud.google.com/blog/topics/threat-intelligence) | Threat intelligence & exploitation-in-the-wild context. | Useful for campaign-level vulnerability exploitation context. |
| 2 | Microsoft Threat Intelligence blog | [www.microsoft.com/en-us/security/blog/topic/threat-intelligence](https://www.microsoft.com/en-us/security/blog/topic/threat-intelligence/) | Microsoft threat intel & exploitation reports. | Useful for attacker behavior, exploitation campaigns, & mitigations. |
| 3 | Google Threat Analysis Group | [blog.google/threat-analysis-group](https://blog.google/threat-analysis-group/) | Nation-state & high-end threat research. | Useful for exploited-in-the-wild context. |
| 4 | Palo Alto Unit 42 | [unit42.paloaltonetworks.com](https://unit42.paloaltonetworks.com/) | Threat research & vulnerability exploitation reporting. | Useful for campaign & malware context. |
| 5 | Cisco Talos | [blog.talosintelligence.com](https://blog.talosintelligence.com/) | Threat intel, malware, & vulnerability research. | Useful for IOCs & exploit campaigns. |
| 6 | Rapid7 vulnerability management blog | [www.rapid7.com/blog/tag/vulnerability-management](https://www.rapid7.com/blog/tag/vulnerability-management/) | Vulnerability management & exploitability commentary. | Useful for operational triage context. |
| 7 | Sophos X-Ops | [news.sophos.com/en-us/category/threat-research](https://news.sophos.com/en-us/category/threat-research/) | Threat research & incident reports. | Useful for exploitation context & malware behavior. |
| 8 | CrowdStrike Blog | [www.crowdstrike.com/en-us/blog](https://www.crowdstrike.com/en-us/blog/) | Threat intelligence & incident research. | Useful for adversary behavior & vulnerability exploitation context. |
| 9 | SentinelOne Labs | [www.sentinelone.com/labs](https://www.sentinelone.com/labs/) | Malware & threat research. | Useful for exploit chains & malware analysis. |
| 10 | Kaspersky Securelist | [securelist.com](https://securelist.com/) | Threat research & malware analysis. | Useful for campaign-level context. |
| 11 | ESET WeLiveSecurity | [www.welivesecurity.com](https://www.welivesecurity.com/) | Threat research & malware analysis. | Useful for exploitation narratives & IOCs. |
| 12 | Trend Micro Research | [www.trendmicro.com/en_us/research.html](https://www.trendmicro.com/en_us/research.html) | Threat & vulnerability research. | Useful for active exploitation context. |
| 13 | FortiGuard Labs | [www.fortiguard.com/research](https://www.fortiguard.com/research) | Fortinet threat research. | Useful for attack patterns & indicators. |
| 14 | Check Point Research | [research.checkpoint.com](https://research.checkpoint.com/) | Threat research & vulnerability analysis. | Useful for campaign & exploit analysis. |
| 15 | Elastic Security Labs | [www.elastic.co/security-labs](https://www.elastic.co/security-labs) | Detection engineering & threat research. | Useful for detection logic & adversary behavior. |
| 16 | Sekoia Threat Intelligence | [blog.sekoia.io](https://blog.sekoia.io/) | Threat intelligence research. | Useful for IOCs & campaign context. |

### 12.2 Malware & IOC repositories

| Sl. # | Title | Link(s) | Relevance | Notes & POIs |
|---:|---|---|---|---|
| 1 | MISP | [www.misp-project.org](https://www.misp-project.org/) | Threat intelligence sharing platform. | Useful for IOC correlation & sharing. |
| 2 | AlienVault OTX | [otx.alienvault.com](https://otx.alienvault.com/) | Open threat exchange for IOCs. | Quality varies by pulse/source. Validate before enforcement. |
| 3 | AbuseIPDB | [www.abuseipdb.com](https://www.abuseipdb.com/) | IP abuse reputation database. | Useful for IP enrichment; not vulnerability-specific. |
| 4 | URLhaus | [urlhaus.abuse.ch](https://urlhaus.abuse.ch/) | Malware URL tracking. | Useful for IOC enrichment. |
| 5 | MalwareBazaar | [bazaar.abuse.ch](https://bazaar.abuse.ch/) | Malware sample sharing. | Useful for malware family & hash enrichment. |
| 6 | ThreatFox | [threatfox.abuse.ch](https://threatfox.abuse.ch/) | Threat intelligence indicators. | Useful for IOCs. |
| 7 | Feodo Tracker | [feodotracker.abuse.ch](https://feodotracker.abuse.ch/) | Botnet C2 tracking. | Useful for malware infrastructure context. |
| 8 | PhishTank | [phishtank.org](https://phishtank.org/) | Phishing URL database. | Useful for phishing exposure & IOC enrichment. |
| 9 | OpenPhish | [openphish.com](https://openphish.com/) | Phishing intelligence. | Commercial/community source; check terms. |
| 10 | YARA | [github.com/VirusTotal/yara](https://github.com/VirusTotal/yara) | Malware classification & pattern matching engine. | Useful for detection signatures. |
| 11 | YARA-Rules | [github.com/Yara-Rules/rules](https://github.com/Yara-Rules/rules) | Community YARA rules. | Validate rule quality before production use. |
| 12 | SigmaHQ | [github.com/SigmaHQ/sigma](https://github.com/SigmaHQ/sigma) | Generic SIEM detection rule format. | Useful for detection engineering. |
| 13 | LOLBAS | [lolbas-project.github.io](https://lolbas-project.github.io/) | Living-off-the-land binaries/scripts catalog. | Useful for attack behavior detection. |
| 14 | GTFOBins | [gtfobins.github.io](https://gtfobins.github.io/) | Unix binary abuse catalog. | Useful for privilege escalation & post-exploitation detection. |
| 15 | Ransomware.live | [www.ransomware.live](https://www.ransomware.live/) | Ransomware group/leak-site tracking. | Useful for ransomware exploitation context & trend analysis. |

[Back to index](#index)

---

## 13. Compliance, baseline configuration & exposure severity standards

These are not vulnerability feeds, but they help assess impact, control failure, configuration exposure, & exploitability in a given environment.

### 13.1 Security configuration & benchmarks

| Sl. # | Title | Link(s) | Relevance | Notes & POIs |
|---:|---|---|---|---|
| 1 | CIS Benchmarks | [www.cisecurity.org/cis-benchmarks](https://www.cisecurity.org/cis-benchmarks) | Secure configuration benchmarks. | Useful for environmental risk scoring & hardening validation. |
| 2 | CIS Controls | [www.cisecurity.org/controls](https://www.cisecurity.org/controls) | Security control framework. | Useful for vulnerability management program alignment. |
| 3 | NIST National Checklist Program | [ncp.nist.gov](https://ncp.nist.gov/) | Repository of security configuration checklists. | Useful for baseline configuration assessment. |
| 4 | DISA STIGs | [public.cyber.mil/stigs](https://public.cyber.mil/stigs/) | Security Technical Implementation Guides. | Important for government/defense compliance. |
| 5 | OpenSCAP | [www.open-scap.org](https://www.open-scap.org/) | SCAP tooling for compliance scanning. | Useful for host-level configuration scanning. |
| 6 | SCAP Security Guide | [github.com/ComplianceAsCode/content](https://github.com/ComplianceAsCode/content) | ComplianceAsCode content for SCAP profiles. | Useful for policy-as-code & baseline validation. |

### 13.2 Cloud configuration posture

| Sl. # | Title | Link(s) | Relevance | Notes & POIs |
|---:|---|---|---|---|
| 1 | Prowler - AWS/Azure/GCP/Kubernetes | [github.com/prowler-cloud/prowler](https://github.com/prowler-cloud/prowler) | Cloud & Kubernetes security posture scanning. | Useful for environmental exposure & misconfiguration risk. |
| 2 | CloudSplaining | [github.com/salesforce/cloudsplaining](https://github.com/salesforce/cloudsplaining) | AWS IAM policy risk analysis. | Useful for blast-radius & privilege exposure context. |
| 3 | ScoutSuite | [github.com/nccgroup/ScoutSuite](https://github.com/nccgroup/ScoutSuite) | Multi-cloud security auditing. | Useful for cloud misconfiguration assessment. |
| 4 | Steampipe mods | [hub.steampipe.io/mods](https://hub.steampipe.io/mods) | SQL-based cloud/security posture checks. | Useful for custom exposure queries. |
| 5 | Cloud Custodian | [cloudcustodian.io](https://cloudcustodian.io/) | Cloud governance & policy automation. | Useful for remediation automation. |
| 6 | Kubernetes CIS benchmark | [www.cisecurity.org/benchmark/kubernetes](https://www.cisecurity.org/benchmark/kubernetes) | Kubernetes configuration benchmark. | Useful for cluster hardening & exposure scoring. |
| 7 | kube-bench | [github.com/aquasecurity/kube-bench](https://github.com/aquasecurity/kube-bench) | Kubernetes CIS benchmark scanner. | Useful for automated cluster benchmark checks. |
| 8 | kube-hunter | [github.com/aquasecurity/kube-hunter](https://github.com/aquasecurity/kube-hunter) | Kubernetes penetration testing tool. | Use only in authorized environments. |

[Back to index](#index)

---

## 14. Source-code, dependency, artifact & build-chain provenance

### 14.1 Source & artifact provenance

| Sl. # | Title | Link(s) | Relevance | Notes & POIs |
|---:|---|---|---|---|
| 1 | SLSA | [slsa.dev](https://slsa.dev/) | Supply-chain Levels for Software Artifacts. | Useful for evaluating build integrity & provenance risk. |
| 2 | Sigstore | [www.sigstore.dev](https://www.sigstore.dev/) | Signing & verification for software artifacts. | Helps verify artifact integrity & publisher identity. |
| 3 | Cosign | [github.com/sigstore/cosign](https://github.com/sigstore/cosign) | Container/artifact signing tool. | Useful for verifying container image provenance. |
| 4 | Rekor | [docs.sigstore.dev/logging/overview](https://docs.sigstore.dev/logging/overview/) | Transparency log for signed artifacts. | Useful for auditability & tamper detection. |
| 5 | in-toto | [in-toto.io](https://in-toto.io/) | Supply-chain integrity framework. | Useful for verifying build steps & provenance attestations. |
| 6 | The Update Framework - TUF | [theupdateframework.io](https://theupdateframework.io/) | Secure software update framework. | Useful for update-channel compromise resistance. |
| 7 | SLSA GitHub generators | [github.com/slsa-framework/slsa-github-generator](https://github.com/slsa-framework/slsa-github-generator) | GitHub-based SLSA provenance generators. | Useful for CI/CD provenance generation. |

### 14.2 Dependency inventory & graphing

| Sl. # | Title | Link(s) | Relevance | Notes & POIs |
|---:|---|---|---|---|
| 1 | deps.dev | [deps.dev](https://deps.dev/) | Dependency metadata, transitive dependency graphing, & security signals. | Useful for OSS dependency context. |
| 2 | GUAC | [guac.sh](https://guac.sh/) | Graph for software supply-chain metadata. | Useful for correlating SBOMs, vulnerabilities, provenance, & attestations. |
| 3 | GUAC GitHub | [github.com/guacsec/guac](https://github.com/guacsec/guac) | GUAC implementation repository. | Reference architecture for software supply-chain knowledge graphs. |
| 4 | OpenSSF Scorecard | [github.com/ossf/scorecard](https://github.com/ossf/scorecard) | Open-source project security practice scoring. | Useful as a dependency risk signal. |
| 5 | OpenSSF Scorecard API | [api.securityscorecards.dev](https://api.securityscorecards.dev/) | API for Scorecard results. | Scores are temporal; store retrieval time. |
| 6 | Maven Central | [central.sonatype.com](https://central.sonatype.com/) | Maven package metadata. | Useful for Java dependency resolution. |
| 7 | npm registry | [registry.npmjs.org](https://registry.npmjs.org/) | npm package registry API endpoint. | Useful for package metadata & version resolution. |
| 8 | PyPI JSON API | [docs.pypi.org/api/json](https://docs.pypi.org/api/json/) | PyPI JSON API documentation. | Useful for Python package metadata. |
| 9 | crates.io API | [crates.io/data-access](https://crates.io/data-access) | crates.io data access documentation. | Useful for Rust package metadata. |
| 10 | Go module proxy | [proxy.golang.org](https://proxy.golang.org/) | Go module proxy. | Useful for Go module version metadata. |

[Back to index](#index)

---

## 15. Practical priority hierarchy for ingestion

### 15.1 Tier 0 - identifiers & inventory

| Sl. # | Title | Link(s) | Relevance | Notes & POIs |
|---:|---|---|---|---|
| 1 | SBOM | [cyclonedx.org/specification/overview](https://cyclonedx.org/specification/overview/), [spdx.dev/specifications](https://spdx.dev/specifications/) | Inventory foundation for matching components to vulnerabilities. | Without accurate inventory, vulnerability matching is incomplete or noisy. |
| 2 | Package identity | [github.com/package-url/purl-spec](https://github.com/package-url/purl-spec), [nvd.nist.gov/products/cpe](https://nvd.nist.gov/products/cpe), [csrc.nist.gov/projects/software-identification-swid](https://csrc.nist.gov/projects/software-identification-swid) | Component identity across package, product, & installed software domains. | Use PURL for packages, CPE for products/platforms, SWID for installed software identity. |
| 3 | Asset exposure | [search.censys.io](https://search.censys.io/), [www.shodan.io](https://www.shodan.io/) | Determines whether vulnerable assets are externally reachable. | Combine with internal CMDB, cloud inventory, & authenticated scans. |
| 4 | Artifact provenance | [slsa.dev](https://slsa.dev/), [www.sigstore.dev](https://www.sigstore.dev/), [in-toto.io](https://in-toto.io/) | Validates build-chain integrity & artifact authenticity. | Helps distinguish vulnerable dependency risk from supply-chain tampering risk. |

### 15.2 Tier 1 - canonical vulnerability records

| Sl. # | Title | Link(s) | Relevance | Notes & POIs |
|---:|---|---|---|---|
| 1 | CVE List v5 | [github.com/CVEProject/cvelistV5](https://github.com/CVEProject/cvelistV5) | Canonical CVE record mirror. | Core identity source. |
| 2 | CVE schema | [github.com/CVEProject/cve-schema](https://github.com/CVEProject/cve-schema) | Schema validation for CVE records. | Use for parser correctness. |
| 3 | CVE Services API | [cveawg.mitre.org/api-docs](https://cveawg.mitre.org/api-docs/) | Direct programmatic CVE lookup. | Useful for targeted CVE access. |
| 4 | NVD CVE API | [nvd.nist.gov/developers/vulnerabilities](https://nvd.nist.gov/developers/vulnerabilities) | CVSS/CPE/CWE/reference enrichment. | Core enrichment source. |
| 5 | NVD CPE API | [nvd.nist.gov/developers/products](https://nvd.nist.gov/developers/products) | CPE dictionary & product matching. | Important for product-level mapping. |
| 6 | NVD data feeds | [nvd.nist.gov/vuln/data-feeds](https://nvd.nist.gov/vuln/data-feeds) | Bulk NVD feed access. | Useful for bootstrapping. |
| 7 | CISA Vulnrichment | [github.com/cisagov/vulnrichment](https://github.com/cisagov/vulnrichment) | CISA ADP enrichment & SSVC data. | Prioritization enrichment. |

### 15.3 Tier 2 - package/ecosystem vulnerability records

| Sl. # | Title | Link(s) | Relevance | Notes & POIs |
|---:|---|---|---|---|
| 1 | OSV full database | [google.github.io/osv.dev/data/#full-database-download](https://google.github.io/osv.dev/data/#full-database-download) | Local mirror of OSS vulnerability records. | Best for high-volume package matching. |
| 2 | OSV API | [google.github.io/osv.dev/post-v1-query](https://google.github.io/osv.dev/post-v1-query/) | Online vulnerability lookup by package/version/commit/ID. | Good for targeted lookups. |
| 3 | GitHub Advisory Database | [github.com/advisories](https://github.com/advisories) | GHSA/CVE/malware advisory records. | Preserve aliases. |
| 4 | GitHub Advisory Database repo | [github.com/github/advisory-database](https://github.com/github/advisory-database) | Raw advisory data for local ingestion. | Useful for mirroring. |
| 5 | Go vuln DB | [vuln.go.dev](https://vuln.go.dev/) | Official Go vulnerability database. | Go-specific affectedness. |
| 6 | RustSec | [rustsec.org](https://rustsec.org/) | Rust advisory ecosystem. | Rust crate-specific advisories. |
| 7 | PyPA advisory DB | [github.com/pypa/advisory-database](https://github.com/pypa/advisory-database) | Python advisory source. | Python/PyPI coverage. |
| 8 | FriendsOfPHP | [github.com/FriendsOfPHP/security-advisories](https://github.com/FriendsOfPHP/security-advisories) | PHP Composer advisories. | Composer-specific. |
| 9 | RubySec | [github.com/rubysec/ruby-advisory-db](https://github.com/rubysec/ruby-advisory-db) | RubyGems advisories. | Ruby ecosystem. |
| 10 | OSS Index | [ossindex.sonatype.org](https://ossindex.sonatype.org/) | Package vulnerability intelligence. | Secondary enrichment. |
| 11 | Packagist API | [packagist.org/apidoc#list-security-advisories](https://packagist.org/apidoc#list-security-advisories) | Composer advisory API. | Direct PHP ecosystem source. |

### 15.4 Tier 3 - affectedness, distro & vendor truth

| Sl. # | Title | Link(s) | Relevance | Notes & POIs |
|---:|---|---|---|---|
| 1 | Red Hat Security Data | [access.redhat.com/security/data](https://access.redhat.com/security/data) | RHEL affectedness, CSAF/VEX, OSV, OVAL. | Backport-aware. |
| 2 | Debian Security Tracker | [security-tracker.debian.org](https://security-tracker.debian.org/) | Debian package affectedness. | Backport-aware. |
| 3 | Ubuntu OVAL / OSV / OpenVEX | [github.com/canonical/ubuntu-security-notices](https://github.com/canonical/ubuntu-security-notices), [ubuntu.com/security/oval](https://ubuntu.com/security/oval), [ubuntu.com/security/vex](https://ubuntu.com/security/vex) | Ubuntu package affectedness & VEX status. | Use release-specific data. |
| 4 | Alpine SecDB | [secdb.alpinelinux.org](https://secdb.alpinelinux.org/) | Alpine package vulnerability data. | Container-critical. |
| 5 | SUSE CSAF / OVAL | [www.suse.com/support/security/csaf](https://www.suse.com/support/security/csaf/), [www.suse.com/support/security/oval](https://www.suse.com/support/security/oval/) | SUSE vendor affectedness & scanner data. | Use machine-readable formats where possible. |
| 6 | Oracle Linux OVAL / errata | [linux.oracle.com/errata](https://linux.oracle.com/errata/), [linux.oracle.com/security/oval](https://linux.oracle.com/security/oval/) | Oracle Linux patch & OVAL data. | Oracle Linux-specific. |
| 7 | Amazon Linux ALAS | [alas.aws.amazon.com](https://alas.aws.amazon.com/) | Amazon Linux advisories. | Separate AL2 & AL2023. |
| 8 | AlmaLinux / Rocky / Fedora / Arch / Gentoo | [bodhi.fedoraproject.org/updates/?type=security](https://bodhi.fedoraproject.org/updates/?type=security), [errata.almalinux.org](https://errata.almalinux.org/), [errata.build.resf.org](https://errata.build.resf.org/), [security.archlinux.org](https://security.archlinux.org/), [security.gentoo.org/glsa](https://security.gentoo.org/glsa/) | Additional Linux distribution affectedness sources. | Distro semantics vary substantially. |
| 9 | Wolfi / Chainguard | [github.com/wolfi-dev/advisories](https://github.com/wolfi-dev/advisories), [packages.cgr.dev/chainguard/security.json](https://packages.cgr.dev/chainguard/security.json), [packages.wolfi.dev/os/security.json](https://packages.wolfi.dev/os/security.json) | Container-first package vulnerability feeds. | Useful for minimal images. |
| 10 | Vendor advisories | [helpx.adobe.com/security.html](https://helpx.adobe.com/security.html), [msrc.microsoft.com/update-guide](https://msrc.microsoft.com/update-guide), [security.paloaltonetworks.com](https://security.paloaltonetworks.com/), [sec.cloudapps.cisco.com/security/center/publicationListing.x](https://sec.cloudapps.cisco.com/security/center/publicationListing.x), [support.apple.com/en-us/100100](https://support.apple.com/en-us/100100), [support.broadcom.com/web/ecx/security-advisory](https://support.broadcom.com/web/ecx/security-advisory), [support.citrix.com/securitybulletins](https://support.citrix.com/securitybulletins), [www.atlassian.com/trust/security/advisories](https://www.atlassian.com/trust/security/advisories), [www.fortiguard.com/psirt](https://www.fortiguard.com/psirt), [www.ivanti.com/resources/v/doc/ivi/2629/0e3e2be1e66d](https://www.ivanti.com/resources/v/doc/ivi/2629/0e3e2be1e66d), [www.oracle.com/security-alerts](https://www.oracle.com/security-alerts/), [www.sap.com](https://support.sap.com/en/my-support/knowledge-base/security-notes-news.html) | Vendor truth for affected products, fixed versions, mitigations, & exploitation notes. | Often most authoritative for product affectedness. Access, formatting, & update latency vary. |

### 15.5 Tier 4 - severity & prioritization

| Sl. # | Title | Link(s) | Relevance | Notes & POIs |
|---:|---|---|---|---|
| 1 | CVSS v3.1/v4.0 | [www.first.org/cvss/v3.1/specification-document](https://www.first.org/cvss/v3.1/specification-document), [www.first.org/cvss/v4.0/specification-document](https://www.first.org/cvss/v4.0/specification-document) | Standard severity scoring. | Severity is not exploit likelihood. |
| 2 | EPSS | [www.first.org/epss](https://www.first.org/epss/) | Exploit likelihood prediction. | Temporal; store score date. |
| 3 | KEV | [www.cisa.gov/sites/default/files/feeds/known_exploited_vulnerabilities.json](https://www.cisa.gov/sites/default/files/feeds/known_exploited_vulnerabilities.json) | Known exploited vulnerability signal. | Strong but incomplete exploited-in-the-wild signal. |
| 4 | SSVC | [github.com/CERTCC/SSVC](https://github.com/CERTCC/SSVC), [www.cisa.gov/stakeholder-specific-vulnerability-categorization-ssvc](https://www.cisa.gov/stakeholder-specific-vulnerability-categorization-ssvc) | Decision support for remediation urgency. | Requires environmental/mission context. |
| 5 | CISA Vulnrichment | [github.com/cisagov/vulnrichment](https://github.com/cisagov/vulnrichment) | SSVC & enrichment data. | Coverage varies. |
| 6 | Vendor exploited-in-the-wild flags | [msrc.microsoft.com/update-guide](https://msrc.microsoft.com/update-guide), [support.apple.com/en-us/100100](https://support.apple.com/en-us/100100), [www.oracle.com/security-alerts](https://www.oracle.com/security-alerts/) | Vendor-provided exploitation status. | Often product-specific & time-sensitive. |
| 7 | Patch availability & fixed-version feeds | [github.com/canonical/ubuntu-security-notices](https://github.com/canonical/ubuntu-security-notices), [security-tracker.debian.org/tracker/data/json](https://security-tracker.debian.org/tracker/data/json), [access.redhat.com/security/data](https://access.redhat.com/security/data) | Determines whether remediation exists. | Patch availability varies by distro/release/product. |
| 8 | Environmental context | [docs.greynoise.io](https://docs.greynoise.io/), [search.censys.io](https://search.censys.io/), [www.shodan.io](https://www.shodan.io/) | Internet exposure, asset criticality, privilege boundary, & data sensitivity determine real impact. | Must be joined with internal asset inventory & controls. |

### 15.6 Tier 5 - exploitability & weaponization

| Sl. # | Title | Link(s) | Relevance | Notes & POIs |
|---:|---|---|---|---|
| 1 | Exploit-DB | [www.exploit-db.com](https://www.exploit-db.com/) | Public exploit availability. | Verify target versions & exploit reliability. |
| 2 | Metasploit modules | [github.com/rapid7/metasploit-framework/tree/master/modules/exploits](https://github.com/rapid7/metasploit-framework/tree/master/modules/exploits) | Weaponized exploit modules. | Strong operationalization signal. |
| 3 | Packet Storm | [packetstormsecurity.com/files/tags/exploit](https://packetstormsecurity.com/files/tags/exploit/) | Exploit archive. | Metadata quality varies. |
| 4 | Project Zero | [googleprojectzero.blogspot.com](https://googleprojectzero.blogspot.com/), [project-zero.issues.chromium.org](https://project-zero.issues.chromium.org/) | Root-cause & exploitability research. | High-quality technical details. |
| 5 | CERT/CC VU notes | [www.kb.cert.org/vuls](https://www.kb.cert.org/vuls/) | Coordinated disclosure & affected vendor context. | Useful for ecosystem-wide vulns. |
| 6 | Rapid7 AttackerKB | [attackerkb.com](https://attackerkb.com/) | Attacker value & exploitability context. | Secondary enrichment. |
| 7 | GreyNoise | [docs.greynoise.io](https://docs.greynoise.io/), [viz.greynoise.io](https://viz.greynoise.io/) | Internet exploitation/scanning telemetry. | Distinguishes noise from activity. |
| 8 | Shadowserver | [dashboard.shadowserver.org](https://dashboard.shadowserver.org/), [www.shadowserver.org](https://www.shadowserver.org/) | Exposure & threat telemetry. | Access & reporting terms vary. |
| 9 | Nuclei templates | [github.com/projectdiscovery/nuclei-templates](https://github.com/projectdiscovery/nuclei-templates) | Detection templates for exposed vulnerabilities. | Template presence is not proof of exposure. |
| 10 | Vendor emergency advisories | [www.cisa.gov/cybersecurity-advisories](https://www.cisa.gov/cybersecurity-advisories), [www.fortiguard.com/psirt](https://www.fortiguard.com/psirt), [www.ivanti.com/resources/v/doc/ivi/2629/0e3e2be1e66d](https://www.ivanti.com/resources/v/doc/ivi/2629/0e3e2be1e66d) | Emergency/active exploitation guidance. | Highly time-sensitive; monitor frequently. |

### 15.7 Tier 6 - weakness, attack-pattern & AI context

| Sl. # | Title | Link(s) | Relevance | Notes & POIs |
|---:|---|---|---|---|
| 1 | CWE | [cwe.mitre.org](https://cwe.mitre.org/) | Weakness taxonomy. | CVE-to-CWE mappings can be broad or missing. |
| 2 | CAPEC | [capec.mitre.org](https://capec.mitre.org/) | Attack-pattern taxonomy. | Maps weaknesses to attack patterns. |
| 3 | ATT&CK Enterprise | [attack.mitre.org/matrices/enterprise](https://attack.mitre.org/matrices/enterprise/) | Enterprise adversary behavior taxonomy. | More post-exploitation than CVE-specific. |
| 4 | ATT&CK STIX | [github.com/mitre-attack/attack-stix-data](https://github.com/mitre-attack/attack-stix-data) | Machine-readable ATT&CK data. | Best for ingestion. |
| 5 | MITRE CTI repo | [github.com/mitre/cti](https://github.com/mitre/cti) | MITRE STIX data repository. | Useful for CTI graphing. |
| 6 | MITRE ATLAS | [atlas.mitre.org](https://atlas.mitre.org/) | AI adversary tactics & techniques. | Directly relevant to AI/ML systems. |
| 7 | OWASP LLM Top 10 | [owasp.org/www-project-top-10-for-large-language-model-applications](https://owasp.org/www-project-top-10-for-large-language-model-applications/) | LLM application vulnerability taxonomy. | Good for AI appsec. |
| 8 | OWASP ML Security Top 10 | [owasp.org/www-project-machine-learning-security-top-10](https://owasp.org/www-project-machine-learning-security-top-10/) | ML security risk taxonomy. | Complements ATLAS. |
| 9 | NIST AI RMF & NIST AI 600-1 | [nvlpubs.nist.gov/nistpubs/ai/NIST.AI.100-1.pdf](https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.100-1.pdf), [www.nist.gov/publications/artificial-intelligence-risk-management-framework-generative-artificial-intelligence](https://www.nist.gov/publications/artificial-intelligence-risk-management-framework-generative-artificial-intelligence) | AI risk management & GenAI risk profile. | Governance/risk context, not vuln feed. |

### 15.8 Tier 7 - detection engineering & validation

| Sl. # | Title | Link(s) | Relevance | Notes & POIs |
|---:|---|---|---|---|
| 1 | CodeQL | [codeql.github.com](https://codeql.github.com/) | Semantic code vulnerability detection. | Strong for variant analysis. |
| 2 | Semgrep | [semgrep.dev](https://semgrep.dev/) | Pattern-based static analysis. | Fast custom rules. |
| 3 | Joern | [joern.io](https://joern.io/) | Code property graph analysis. | Useful for research & advanced detection. |
| 4 | Infer | [fbinfer.com](https://fbinfer.com/) | Static analysis engine. | Good for specific bug classes. |
| 5 | Sonar rules | [rules.sonarsource.com](https://rules.sonarsource.com/) | Security/code quality rule catalog. | Useful for rule taxonomy mapping. |
| 6 | Nuclei templates | [github.com/projectdiscovery/nuclei-templates](https://github.com/projectdiscovery/nuclei-templates) | DAST/exposure templates. | Template quality varies. |
| 7 | OSS-Fuzz | [google.github.io/oss-fuzz](https://google.github.io/oss-fuzz/) | Continuous fuzzing. | Useful for discovery & OSV-linked vulns. |
| 8 | SARD / Juliet | [samate.nist.gov/SARD](https://samate.nist.gov/SARD/), [samate.nist.gov/SARD/test-suites/112](https://samate.nist.gov/SARD/test-suites/112) | Test suites for vulnerability detection. | Useful for evaluation; not production vulnerability feed. |
| 9 | Vulnerability datasets | [github.com/DLVulDet/PrimeVul](https://github.com/DLVulDet/PrimeVul), [github.com/Icyrockton/MegaVul](https://github.com/Icyrockton/MegaVul), [github.com/ZeoVan/MSR_20_Code_vulnerability_CSV_Dataset](https://github.com/ZeoVan/MSR_20_Code_vulnerability_CSV_Dataset), [github.com/secureIT-project/CVEfixes](https://github.com/secureIT-project/CVEfixes), [github.com/tuhh-softsec/vul4j](https://github.com/tuhh-softsec/vul4j), [github.com/wagner-group/diversevul](https://github.com/wagner-group/diversevul), [sites.google.com/view/devign](https://sites.google.com/view/devign) | ML/research datasets for vulnerability detection. | Validate labels, leakage, deduplication, & licensing. |

[Back to index](#index)

---

## 16. Recommended canonical data model coverage

A complete vulnerability impact system should be able to ingest or derive the following fields.

### 16.1 Vulnerability identity

| Sl. # | Title | Link(s) | Relevance | Notes & POIs |
|---:|---|---|---|---|
| 1 | CVE ID | [github.com/CVEProject/cvelistV5](https://github.com/CVEProject/cvelistV5), [www.cve.org](https://www.cve.org/) | Canonical vulnerability identifier. | Not all advisories have CVEs immediately. |
| 2 | GHSA ID | [github.com/advisories](https://github.com/advisories) | GitHub Security Advisory identifier. | May exist without CVE. |
| 3 | OSV ID | [osv.dev](https://osv.dev/) | OSV vulnerability identifier. | Links package-specific affectedness & aliases. |
| 4 | Vendor advisory ID | [msrc.microsoft.com/update-guide](https://msrc.microsoft.com/update-guide), [www.oracle.com/security-alerts](https://www.oracle.com/security-alerts/) | Vendor-specific advisory identifier. | Often most authoritative for product-specific truth. |
| 5 | CWE ID | [cwe.mitre.org](https://cwe.mitre.org/) | Weakness class identifier. | Quality of mapping varies. |
| 6 | CAPEC ID | [capec.mitre.org](https://capec.mitre.org/) | Attack-pattern identifier. | Useful for attack mechanism mapping. |
| 7 | ATT&CK technique ID | [attack.mitre.org/matrices/enterprise](https://attack.mitre.org/matrices/enterprise/) | Adversary technique identifier. | Useful for detection/response mapping. |
| 8 | ATLAS technique ID | [atlas.mitre.org/techniques](https://atlas.mitre.org/techniques) | AI/ML adversary technique identifier. | Relevant for AI systems. |
| 9 | Alias graph | [github.com/advisories](https://github.com/advisories), [osv.dev](https://osv.dev/), [github.com/CVEProject/cvelistV5](https://github.com/CVEProject/cvelistV5) | Maps CVE/GHSA/OSV/vendor aliases. | Crucial for deduplication & correlation. |

### 16.2 Affectedness

| Sl. # | Title | Link(s) | Relevance | Notes & POIs |
|---:|---|---|---|---|
| 1 | Product name | [nvd.nist.gov/products/cpe](https://nvd.nist.gov/products/cpe) | Identifies vulnerable products. | Normalize against CPE/PURL/vendor data. |
| 2 | Vendor | [www.cve.org](https://www.cve.org/) | Vendor/product attribution. | Vendor naming can differ across sources. |
| 3 | CPE | [nvd.nist.gov/developers/products](https://nvd.nist.gov/developers/products) | Product/platform matching. | Imprecise for many OSS packages. |
| 4 | PURL | [github.com/package-url/purl-spec](https://github.com/package-url/purl-spec) | Package identity. | Prefer for package ecosystem matching. |
| 5 | Package ecosystem | [osv.dev/list](https://osv.dev/list) | Defines package namespace & version rules. | Version semantics are ecosystem-specific. |
| 6 | Package name | [deps.dev](https://deps.dev/) | Dependency identity. | Normalize casing & namespace rules. |
| 7 | Affected version range | [ossf.github.io/osv-schema](https://ossf.github.io/osv-schema/) | Expresses vulnerable versions. | Range interpretation must respect ecosystem semantics. |
| 8 | Fixed version | [github.com/advisories](https://github.com/advisories), [osv.dev](https://osv.dev/) | Remediation target. | Fixed package version may differ by distro due to backports. |
| 9 | Introduced version / commit | [ossf.github.io/osv-schema](https://ossf.github.io/osv-schema/) | Determines when vulnerability entered codebase. | Not always available. |
| 10 | Last affected version | [ossf.github.io/osv-schema](https://ossf.github.io/osv-schema/) | Helps determine affected version bounds. | Validate with vendor feeds. |
| 11 | Backport status | [access.redhat.com/security/data](https://access.redhat.com/security/data), [security-tracker.debian.org](https://security-tracker.debian.org/), [ubuntu.com/security/cves](https://ubuntu.com/security/cves) | Determines if a distro package is patched despite upstream version appearing vulnerable. | Essential for reducing false positives. |
| 12 | VEX status | [github.com/openvex/spec](https://github.com/openvex/spec), [www.csaf.io](https://www.csaf.io/) | Represents affected, not affected, fixed, or under investigation. | Preserve justification & author provenance. |
| 13 | Justification for not affected | [github.com/openvex/spec](https://github.com/openvex/spec) | Explains why a product is not affected. | Key for trust & auditability. |
| 14 | Distro/package release channel | [packages.fedoraproject.org](https://packages.fedoraproject.org/), [pkgs.alpinelinux.org/packages](https://pkgs.alpinelinux.org/packages) | Tracks package release stream. | Channel differences can affect fix availability. |

### 16.3 Severity & exploitability

| Sl. # | Title | Link(s) | Relevance | Notes & POIs |
|---:|---|---|---|---|
| 1 | CVSS v2/v3/v4 vector | [www.first.org/cvss](https://www.first.org/cvss/) | Structured severity vector. | Use vector, not only numeric score. |
| 2 | CVSS base/temporal/environmental score | [nvd.nist.gov/vuln-metrics/cvss](https://nvd.nist.gov/vuln-metrics/cvss) | Severity scoring. | Environmental score should be computed with local context. |
| 3 | EPSS score | [www.first.org/epss](https://www.first.org/epss/) | Exploit likelihood. | Temporal; store score date. |
| 4 | EPSS percentile | [www.first.org/epss/data_stats](https://www.first.org/epss/data_stats) | Relative exploit-likelihood ranking. | Useful for prioritization across backlog. |
| 5 | KEV membership | [www.cisa.gov/sites/default/files/feeds/known_exploited_vulnerabilities.json](https://www.cisa.gov/sites/default/files/feeds/known_exploited_vulnerabilities.json) | Known exploited vulnerability marker. | Strong exploitation evidence. |
| 6 | KEV date added | [www.cisa.gov/sites/default/files/feeds/known_exploited_vulnerabilities.json](https://www.cisa.gov/sites/default/files/feeds/known_exploited_vulnerabilities.json) | Temporal exploitation/prioritization signal. | Use for SLA & trend analysis. |
| 7 | Known ransomware usage | [www.ransomware.live](https://www.ransomware.live/) | Ransomware exploitation context. | Attribution & mapping quality vary. |
| 8 | Public exploit available | [www.exploit-db.com](https://www.exploit-db.com/) | PoC/exploit availability. | Verify reliability & version applicability. |
| 9 | Metasploit module available | [github.com/rapid7/metasploit-framework/tree/master/modules/exploits](https://github.com/rapid7/metasploit-framework/tree/master/modules/exploits) | Weaponized exploit implementation. | Stronger than generic PoC signal. |
| 10 | Nuclei template available | [github.com/projectdiscovery/nuclei-templates](https://github.com/projectdiscovery/nuclei-templates) | Detection template availability. | Indicates detectable exposure, not confirmed vulnerability. |
| 11 | GreyNoise observed scanning | [viz.greynoise.io](https://viz.greynoise.io/) | Internet scanning/exploitation telemetry. | Helps prioritize exposed services. |
| 12 | Shadowserver observed exposure | [dashboard.shadowserver.org](https://dashboard.shadowserver.org/) | Internet-scale exposure telemetry. | Access may require registration/eligibility. |
| 13 | CISA SSVC decision points | [github.com/cisagov/vulnrichment](https://github.com/cisagov/vulnrichment) | Decision support enrichment. | Useful for prioritization workflows. |
| 14 | Vendor exploitation status | [msrc.microsoft.com/update-guide](https://msrc.microsoft.com/update-guide), [security.paloaltonetworks.com](https://security.paloaltonetworks.com/), [support.apple.com/en-us/100100](https://support.apple.com/en-us/100100) | Vendor-provided exploitation notes. | Time-sensitive & product-specific. |
| 15 | Patch availability | [access.redhat.com/security/data](https://access.redhat.com/security/data), [security-tracker.debian.org](https://security-tracker.debian.org/), [ubuntu.com/security/notices](https://ubuntu.com/security/notices) | Determines if a fix exists. | Patch availability varies by release stream. |
| 16 | Workaround availability | [www.kb.cert.org/vuls](https://www.kb.cert.org/vuls/), [www.cisa.gov/cybersecurity-advisories](https://www.cisa.gov/cybersecurity-advisories) | Temporary mitigation when patching is not available. | Workarounds may reduce but not eliminate risk. |

### 16.4 Environmental impact

| Sl. # | Title | Link(s) | Relevance | Notes & POIs |
|---:|---|---|---|---|
| 1 | Asset criticality | [www.cisecurity.org/controls](https://www.cisecurity.org/controls) | Business/system importance affects risk. | Must come from internal asset inventory. |
| 2 | Internet exposure | [search.censys.io](https://search.censys.io/), [www.shodan.io](https://www.shodan.io/) | Determines external exploitability surface. | External scan data may be incomplete or stale. |
| 3 | Network reachability | [nmap.org](https://nmap.org/) | Determines whether an exploit path exists. | Internal network context required. |
| 4 | Authentication required | [www.first.org/cvss](https://www.first.org/cvss/) | Impacts exploitability. | CVSS may not capture local compensating controls. |
| 5 | Privilege required | [www.first.org/cvss](https://www.first.org/cvss/) | Impacts exploitability & blast radius. | Validate with product configuration. |
| 6 | User interaction required | [www.first.org/cvss](https://www.first.org/cvss/) | Impacts exploitability conditions. | User interaction can be bypassed in some real-world chains. |
| 7 | Exploit preconditions | [www.kb.cert.org/vuls](https://www.kb.cert.org/vuls/), [googleprojectzero.blogspot.com](https://googleprojectzero.blogspot.com/) | Defines required configuration or state. | Crucial for false-positive reduction. |
| 8 | Data sensitivity | [www.cisecurity.org/controls](https://www.cisecurity.org/controls) | Determines business impact. | Internal classification required. |
| 9 | Compensating controls | [public.cyber.mil/stigs](https://public.cyber.mil/stigs/), [www.cisecurity.org/cis-benchmarks](https://www.cisecurity.org/cis-benchmarks) | Controls can reduce practical exploitability. | Document assumptions & evidence. |
| 10 | Runtime configuration | [docs.dependencytrack.org/datasources/overview](https://docs.dependencytrack.org/datasources/overview/) | Enabled features/modules influence affectedness. | Scanner package matches alone can over-report. |
| 11 | Feature/module enabled | [github.com/openvex/spec](https://github.com/openvex/spec) | VEX not-affected reasoning may depend on disabled code paths. | Requires product/runtime evidence. |
| 12 | Cloud account/project/environment | [github.com/prowler-cloud/prowler](https://github.com/prowler-cloud/prowler) | Cloud context affects exposure & blast radius. | Join vulnerability data with cloud inventory. |
| 13 | Blast radius | [github.com/salesforce/cloudsplaining](https://github.com/salesforce/cloudsplaining) | Privilege & dependency spread determine impact. | Requires IAM, network, & data-flow context. |
| 14 | Business process ownership | [www.cisecurity.org/controls](https://www.cisecurity.org/controls) | Ownership determines remediation accountability. | Internal data source required. |

### 16.5 Detection & remediation

| Sl. # | Title | Link(s) | Relevance | Notes & POIs |
|---:|---|---|---|---|
| 1 | Scanner finding ID | [dependencytrack.org](https://dependencytrack.org/), [github.com/anchore/grype](https://github.com/anchore/grype), [trivy.dev/docs/latest/scanner/vulnerability](https://trivy.dev/docs/latest/scanner/vulnerability/) | Scanner-specific finding identity. | Preserve source scanner & version for reproducibility. |
| 2 | Detection method | [codeql.github.com](https://codeql.github.com/), [github.com/projectdiscovery/nuclei](https://github.com/projectdiscovery/nuclei), [owasp.org/www-project-top-ten](https://owasp.org/www-project-top-ten/) | Indicates whether finding came from SBOM, CPE, package manager, SAST, DAST, IaC, or runtime telemetry. | Different methods have different false-positive characteristics. |
| 3 | Confidence | [github.com/openvex/spec](https://github.com/openvex/spec) | Confidence helps rank findings. | Use evidence & source provenance to compute confidence. |
| 4 | False-positive reason | [github.com/openvex/spec](https://github.com/openvex/spec) | Captures why a match is not actually exploitable or affected. | VEX justification is key for auditability. |
| 5 | Fix version | [osv.dev](https://osv.dev/), [github.com/advisories](https://github.com/advisories) | Remediation target version. | Distro fixed versions may differ due to backports. |
| 6 | Patch advisory | [access.redhat.com/security/data](https://access.redhat.com/security/data), [ubuntu.com/security/notices](https://ubuntu.com/security/notices), [www.debian.org/security](https://www.debian.org/security/) | Links vulnerability to vendor patch guidance. | Use vendor patch source for production remediation. |
| 7 | Mitigation | [www.cisa.gov/cybersecurity-advisories](https://www.cisa.gov/cybersecurity-advisories), [www.kb.cert.org/vuls](https://www.kb.cert.org/vuls/) | Temporary or compensating controls. | Mitigations may be partial & context-specific. |
| 8 | Workaround | [www.kb.cert.org/vuls](https://www.kb.cert.org/vuls/) | Alternative remediation when patch unavailable. | Track expiration & replacement by patch. |
| 9 | Exploit detection signatures | [github.com/SigmaHQ/sigma](https://github.com/SigmaHQ/sigma), [github.com/VirusTotal/yara](https://github.com/VirusTotal/yara), [github.com/projectdiscovery/nuclei-templates](https://github.com/projectdiscovery/nuclei-templates) | Detection content for exploit attempts or compromise. | Validate signatures in environment before high-confidence alerting. |
| 10 | Regression test | [google.github.io/oss-fuzz](https://google.github.io/oss-fuzz/), [github.com/google/oss-fuzz](https://github.com/google/oss-fuzz) | Tests that a vulnerability class or bug does not reappear. | Useful for secure SDLC feedback loops. |
| 11 | Verification command | [github.com/anchore/grype](https://github.com/anchore/grype), [github.com/aquasecurity/trivy-db](https://github.com/aquasecurity/trivy-db), [github.com/projectdiscovery/nuclei](https://github.com/projectdiscovery/nuclei) | Command/procedure to verify vulnerability or remediation state. | Required for repeatable remediation closure. |
| 12 | SLA due date | [www.cisa.gov/sites/default/files/feeds/known_exploited_vulnerabilities.json](https://www.cisa.gov/sites/default/files/feeds/known_exploited_vulnerabilities.json), [www.cisa.gov/news-events/directives/bod-22-01-reducing-significant-risk-known-exploited-vulnerabilities](https://www.cisa.gov/news-events/directives/bod-22-01-reducing-significant-risk-known-exploited-vulnerabilities) | Remediation deadline derived from KEV, severity, exposure, policy, or business context. | SLA should be policy-driven & context-aware. |

[Back to index](#index)

---

## 17. Minimal source set for production use

| Sl. # | Title | Link(s) | Relevance | Notes & POIs |
|---:|---|---|---|---|
| 1 | CVE List v5 | [github.com/CVEProject/cvelistV5](https://github.com/CVEProject/cvelistV5) | Canonical CVE records. | Start here for CVE identity. |
| 2 | CVE schema | [github.com/CVEProject/cve-schema](https://github.com/CVEProject/cve-schema) | CVE schema validation. | Required for robust parsers. |
| 3 | NVD CVE API | [nvd.nist.gov/developers/vulnerabilities](https://nvd.nist.gov/developers/vulnerabilities) | CVSS/CPE/CWE enrichment. | Core product matching source. |
| 4 | NVD CPE API | [nvd.nist.gov/developers/products](https://nvd.nist.gov/developers/products) | Product/platform identity matching. | Combine with PURL. |
| 5 | OSV full database | [google.github.io/osv.dev/data/#full-database-download](https://google.github.io/osv.dev/data/#full-database-download) | OSS package vulnerability database. | Local mirroring recommended. |
| 6 | OSV schema | [ossf.github.io/osv-schema](https://ossf.github.io/osv-schema/) | OSS vulnerability record schema. | Needed for parsing affected ranges. |
| 7 | GitHub Advisory Database repo | [github.com/github/advisory-database](https://github.com/github/advisory-database) | Raw GitHub advisory records. | Preserve GHSA aliases. |
| 8 | CISA KEV JSON | [www.cisa.gov/sites/default/files/feeds/known_exploited_vulnerabilities.json](https://www.cisa.gov/sites/default/files/feeds/known_exploited_vulnerabilities.json) | Known exploitation signal. | High-priority remediation driver. |
| 9 | CISA Vulnrichment | [github.com/cisagov/vulnrichment](https://github.com/cisagov/vulnrichment) | CISA ADP & SSVC enrichment. | Coverage varies. |
| 10 | FIRST EPSS | [www.first.org/epss](https://www.first.org/epss/) | Exploit likelihood prediction. | Store score date. |
| 11 | CWE downloads | [cwe.mitre.org/data/downloads.html](https://cwe.mitre.org/data/downloads.html) | Weakness taxonomy ingestion. | Useful for classification & grouping. |
| 12 | CAPEC downloads | [capec.mitre.org/data/downloads.html](https://capec.mitre.org/data/downloads.html) | Attack-pattern taxonomy ingestion. | Useful for weakness-to-attack mapping. |
| 13 | ATT&CK STIX data | [github.com/mitre-attack/attack-stix-data](https://github.com/mitre-attack/attack-stix-data) | Machine-readable adversary techniques. | Useful for response/detection mapping. |
| 14 | MITRE ATLAS | [atlas.mitre.org](https://atlas.mitre.org/) | AI/ML adversary framework. | Required for AI system risk mapping. |
| 15 | CycloneDX | [cyclonedx.org/specification/overview](https://cyclonedx.org/specification/overview/) | SBOM/vulnerability/VEX-capable standard. | Good for inventory ingestion. |
| 16 | SPDX | [spdx.dev/specifications](https://spdx.dev/specifications/) | SBOM & package metadata standard. | Common in compliance workflows. |
| 17 | PURL | [github.com/package-url/purl-spec](https://github.com/package-url/purl-spec) | Package identity. | Essential for package vulnerability matching. |
| 18 | CSAF | [docs.oasis-open.org/csaf/csaf/v2.0/os/csaf-v2.0-os.html](https://docs.oasis-open.org/csaf/csaf/v2.0/os/csaf-v2.0-os.html) | Structured security advisories. | Supports product status & VEX-like workflows. |
| 19 | OpenVEX | [github.com/openvex/spec](https://github.com/openvex/spec) | Affected/not-affected status communication. | Reduces false positives. |
| 20 | Distro feeds | [access.redhat.com/security/data](https://access.redhat.com/security/data), [alas.aws.amazon.com](https://alas.aws.amazon.com/), [linux.oracle.com/security](https://linux.oracle.com/security/), [packages.cgr.dev/chainguard/security.json](https://packages.cgr.dev/chainguard/security.json), [packages.wolfi.dev/os/security.json](https://packages.wolfi.dev/os/security.json), [secdb.alpinelinux.org](https://secdb.alpinelinux.org/), [security-tracker.debian.org](https://security-tracker.debian.org/), [ubuntu.com/security/oval](https://ubuntu.com/security/oval), [www.suse.com/support/security/csaf](https://www.suse.com/support/security/csaf/) | Distro-specific affectedness & patch status. | Required to avoid backport false positives. |
| 21 | Exploit signal feeds | [docs.greynoise.io](https://docs.greynoise.io/), [github.com/rapid7/metasploit-framework](https://github.com/rapid7/metasploit-framework), [project-zero.issues.chromium.org](https://project-zero.issues.chromium.org/), [www.exploit-db.com](https://www.exploit-db.com/), [www.kb.cert.org/vuls](https://www.kb.cert.org/vuls/), [www.shadowserver.org](https://www.shadowserver.org/) | Exploitability, weaponization, & exposure enrichment. | Use for prioritization, not canonical vulnerability identity. |

[Back to index](#index)

---

## 18. Final structure for all vulnerability management sources & exposure listings

| Sl. # | Title | Link(s) | Relevance | Notes & POIs |
|---:|---|---|---|---|
| 1 | Canonical vulnerability records | [github.com/CVEProject/cvelistV5](https://github.com/CVEProject/cvelistV5), [github.com/cisagov/vulnrichment](https://github.com/cisagov/vulnrichment), [nvd.nist.gov](https://nvd.nist.gov/), [www.cve.org](https://www.cve.org/) | CVE, NVD, CVE schema, & CISA Vulnrichment provide base vulnerability identity & enrichment. | Use as foundational sources but enrich with vendor/package-specific affectedness. |
| 2 | Package & ecosystem advisories | [github.com/advisories](https://github.com/advisories), [github.com/github/advisory-database](https://github.com/github/advisory-database), [osv.dev](https://osv.dev/) | OSV, GHSA, & language advisory DBs provide package-level affected version data. | Prefer PURL/package semantics over CPE for OSS dependencies. |
| 3 | Vendor & distro affectedness | [access.redhat.com/security/data](https://access.redhat.com/security/data), [secdb.alpinelinux.org](https://secdb.alpinelinux.org/), [security-tracker.debian.org](https://security-tracker.debian.org/), [ubuntu.com/security/oval](https://ubuntu.com/security/oval), [www.suse.com/support/security/csaf](https://www.suse.com/support/security/csaf/) | CSAF, VEX, OVAL, secdb, OSV, & vendor advisories identify whether a specific product/package is affected. | Essential for reducing false positives & handling backports. |
| 4 | Exploitability & prioritization | [github.com/rapid7/metasploit-framework](https://github.com/rapid7/metasploit-framework), [viz.greynoise.io](https://viz.greynoise.io/), [www.cisa.gov/sites/default/files/feeds/known_exploited_vulnerabilities.json](https://www.cisa.gov/sites/default/files/feeds/known_exploited_vulnerabilities.json), [www.exploit-db.com](https://www.exploit-db.com/), [www.first.org/epss](https://www.first.org/epss/) | KEV, EPSS, SSVC, CVSS, Exploit-DB, Metasploit, & GreyNoise inform urgency. | Do not conflate severity with exploitability. |
| 5 | Weakness & adversary mapping | [attack.mitre.org/matrices/enterprise](https://attack.mitre.org/matrices/enterprise/), [atlas.mitre.org](https://atlas.mitre.org/), [capec.mitre.org](https://capec.mitre.org/), [cwe.mitre.org](https://cwe.mitre.org/) | CWE, CAPEC, ATT&CK, & ATLAS map vulnerabilities to weaknesses & adversary behavior. | Useful for detection engineering & root-cause analysis. |
| 6 | AI-specific vulnerability context | [atlas.mitre.org](https://atlas.mitre.org/), [owasp.org/www-project-machine-learning-security-top-10](https://owasp.org/www-project-machine-learning-security-top-10/), [owasp.org/www-project-top-10-for-large-language-model-applications](https://owasp.org/www-project-top-10-for-large-language-model-applications/), [www.nist.gov/itl/ai-risk-management-framework](https://www.nist.gov/itl/ai-risk-management-framework) | ATLAS, OWASP LLM Top 10, OWASP ML Top 10, & NIST AI RMF frame AI/ML risk. | AI vulnerabilities often lack CVEs; include threat-model & control frameworks. |
| 7 | SBOM & identity | [cyclonedx.org/specification/overview](https://cyclonedx.org/specification/overview/), [github.com/package-url/purl-spec](https://github.com/package-url/purl-spec), [nvd.nist.gov/products/cpe](https://nvd.nist.gov/products/cpe), [spdx.dev/specifications](https://spdx.dev/specifications/) | CycloneDX, SPDX, PURL, CPE, & SWID identify components for matching. | Accurate inventory is prerequisite to vulnerability assessment. |
| 8 | Exposure telemetry | [leakix.net](https://leakix.net/), [search.censys.io](https://search.censys.io/), [viz.greynoise.io](https://viz.greynoise.io/), [www.shadowserver.org](https://www.shadowserver.org/), [www.shodan.io](https://www.shodan.io/) | Censys, Shodan, Shadowserver, GreyNoise, LeakIX, & internal inventory help assess real exposure. | External scan data can be stale or incomplete; join with internal evidence. |
| 9 | Malicious package & supply-chain compromise | [github.com/ossf/malicious-packages](https://github.com/ossf/malicious-packages), [github.com/ossf/package-analysis](https://github.com/ossf/package-analysis), [github.com/advisories?query=type%3Amalware](https://github.com/advisories?query=type%3Amalware), [security.snyk.io](https://security.snyk.io/), [socket.dev/blog](https://socket.dev/blog), [sonatype.com/resources/vulnerability-database](https://sonatype.com/resources/vulnerability-database) | Tracks malicious package risk that may not appear as conventional CVEs. | Essential for supply-chain defense & dependency risk. |
| 10 | Detection engineering | [codeql.github.com](https://codeql.github.com/), [github.com/projectdiscovery/nuclei](https://github.com/projectdiscovery/nuclei), [google.github.io/oss-fuzz](https://google.github.io/oss-fuzz/), [joern.io](https://joern.io/), [samate.nist.gov/SARD](https://samate.nist.gov/SARD/), [semgrep.dev](https://semgrep.dev/) | CodeQL, Semgrep, Joern, Infer, Nuclei, OSS-Fuzz, SARD, & vulnerability datasets support detection & validation. | Detection quality depends on rule precision, context, & evidence quality. |
| 11 | Threat intelligence | [blog.google/threat-analysis-group](https://blog.google/threat-analysis-group/), [blog.talosintelligence.com](https://blog.talosintelligence.com/), [cloud.google.com/blog/topics/threat-intelligence](https://cloud.google.com/blog/topics/threat-intelligence), [unit42.paloaltonetworks.com](https://unit42.paloaltonetworks.com/), [www.microsoft.com/en-us/security/blog/topic/threat-intelligence](https://www.microsoft.com/en-us/security/blog/topic/threat-intelligence/), [www.rapid7.com/blog/tag/vulnerability-management](https://www.rapid7.com/blog/tag/vulnerability-management/), [www.ransomware.live](https://www.ransomware.live/) | Mandiant, Microsoft, Google TAG, Unit 42, Talos, Rapid7, ransomware & IOC feeds provide exploitation-in-the-wild context. | Research sources vary in timeliness, depth, & attribution confidence. |
| 12 | Compliance & configuration impact | [github.com/ComplianceAsCode/content](https://github.com/ComplianceAsCode/content), [ncp.nist.gov](https://ncp.nist.gov/), [public.cyber.mil/stigs](https://public.cyber.mil/stigs/), [www.cisecurity.org/cis-benchmarks](https://www.cisecurity.org/cis-benchmarks), [www.open-scap.org](https://www.open-scap.org/) | CIS, STIG, SCAP, cloud posture, & Kubernetes benchmarks help assess environmental control weakness. | These are not vulnerability feeds but determine practical risk & exploitability. |

[Back to index](#index)

---

#### `License`
>     Copyright Ⓒ 2025  Keerthana Purushotham <keep.consult@proton.me>.
>     Licensed under the GNU AGPL v3. See LICENSE for details.
>   [*see license*](https://github.com/keerthanap8898/CveToad/blob/main/LICENSE)

##### Note:
> *Some vendor/security pages change URLs over time, so treat this as a high-coverage baseline rather than a mathematically exhaustive list of every possible vulnerability source.*
