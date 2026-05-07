# CveToad Vulnerability Management Source Inventory

A consolidated super-set vulnerability-management source inventory for assessing impact, severity, exploitability, exposure, affectedness, prioritization, & remediation of vulnerabilities in technical systems.

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

1. **Project Zero issue tracker**
   - Old: <https://bugs.chromium.org/p/project-zero/issues/list>
   - Current preferred: <https://project-zero.issues.chromium.org/>
   - Note: Google/Chromium issue tracking migrated away from Monorail-style `bugs.chromium.org`; the Project Zero issue tracker is now hosted under `project-zero.issues.chromium.org`.

2. **Alpine SecDB GitHub mirror**
   - Deprecated mirror: <https://github.com/alpinelinux/alpine-secdb>
   - Preferred: <https://secdb.alpinelinux.org/>
   - Note: Keep both for historical compatibility, but ingest from `secdb.alpinelinux.org`.

3. **Wolfi / Chainguard feed duplicate**
   - Previously duplicated: <https://packages.wolfi.dev/os/security.json>
   - Correct split:
     - Wolfi OS feed: <https://packages.wolfi.dev/os/security.json>
     - Chainguard Enterprise feed: <https://packages.cgr.dev/chainguard/security.json>

4. **GitHub advisories APIs**
   - Keep GraphQL `SecurityAdvisory`.
   - Add REST global security advisory endpoints.
   - GraphQL object: <https://docs.github.com/en/graphql/reference/objects#securityadvisory>
   - REST global advisories: <https://docs.github.com/en/rest/security-advisories/global-advisories>
   - REST advisories root: <https://docs.github.com/en/rest/security-advisories>

5. **NVD feeds vs APIs**
   - Keep both.
   - Prefer NVD 2.0 APIs for ongoing sync.
   - Use feeds for bootstrapping or mirroring.
   - NVD API docs: <https://nvd.nist.gov/developers>
   - NVD data feeds: <https://nvd.nist.gov/vuln/data-feeds>

[Back to index](#index)

---

## 1. Canonical vulnerability identifiers, CVE records & schemas

### 1.1 CVE Program - canonical CVE identity

1. **CVE.org**
   - Link: <https://www.cve.org/>
   - Purpose: CVE program portal, CNA/ADP governance, CVE ID lookup, program documentation.

2. **CVE List v5 - official GitHub mirror/cache**
   - Link: <https://github.com/CVEProject/cvelistV5>
   - Purpose: primary public GitHub cache of CVE v5 JSON records.

3. **CVE Record Format schema - direct JSON schema**
   - Link: <https://github.com/CVEProject/cve-schema/blob/main/schema/CVE_Record_Format.json>
   - Purpose: machine-validation schema for CVE v5 records.

4. **CVE schema repository**
   - Link: <https://github.com/CVEProject/cve-schema>
   - Purpose: schema versions, tests, examples, release history.

5. **CVE Services API / CVE Program API**
   - Link: <https://cveawg.mitre.org/api-docs/>
   - Purpose: direct CVE lookup, CNA workflows, CVE Services API documentation.

6. **CVE Authorized Data Publishers - ADPs**
   - Link: <https://www.cve.org/ProgramOrganization/ADPs>
   - Purpose: list of ADPs that can enrich CVE records beyond CNA-provided content.

7. **CISA Vulnrichment - CVE ADP enrichment**
   - Link: <https://github.com/cisagov/vulnrichment>
   - Purpose: CISA ADP enrichment of CVE records, including SSVC decision points, & sometimes CWE/CVSS enrichment.

### 1.2 NVD - CVE enrichment, CPE matching, CVSS & configurations

1. **NVD home**
   - Link: <https://nvd.nist.gov/>
   - Purpose: U.S. government vulnerability-management repository.

2. **NVD CVE API 2.0**
   - Link: <https://nvd.nist.gov/developers/vulnerabilities>
   - Purpose: CVE retrieval, CVSS, weaknesses, references, CPE configurations, change history.

3. **NVD CPE API 2.0**
   - Link: <https://nvd.nist.gov/developers/products>
   - Purpose: CPE dictionary & CPE match criteria for product/platform matching.

4. **NVD Data Feeds**
   - Link: <https://nvd.nist.gov/vuln/data-feeds>
   - Purpose: bulk JSON feeds for CVEs, CPE dictionary, & CPE match feeds.

5. **NVD CVSS resources**
   - Link: <https://nvd.nist.gov/vuln-metrics/cvss>
   - Purpose: CVSS calculators, vector definitions, severity scoring references.

6. **NVD CPE Dictionary**
   - Link: <https://nvd.nist.gov/products/cpe>
   - Purpose: CPE product naming, product identifiers, & matching basis.

7. **NVD API documentation root**
   - Link: <https://nvd.nist.gov/developers>
   - Purpose: NVD API family documentation.

8. **NVD CVE Change History API**
   - Link: <https://nvd.nist.gov/developers/vulnerabilities>
   - Purpose: monitor changes to CVE enrichment, scoring, references, configurations.

### 1.3 Optional CVE meta-mirrors / commercial-community enrichments

These are useful as secondary sources, not canonical replacements.

1. **VulnCheck NVD++**
   - Link: <https://www.vulncheck.com/nvd2>
   - Purpose: community/commercial aggregated access to CVE List, NVD, & KEV-like data.

2. **Vulners**
   - Link: <https://vulners.com/>
   - Purpose: vulnerability intelligence aggregator.

3. **OpenCVE**
   - Link: <https://www.opencve.io/>
   - Purpose: CVE monitoring, subscriptions, change tracking.

4. **CIRCL CVE Search**
   - Link: <https://cve.circl.lu/>
   - Purpose: CVE search & enrichment, useful historically.

[Back to index](#index)

---

## 2. Open-source vulnerability databases & package advisory sources

### 2.1 OSV ecosystem

1. **OSV main site**
   - Link: <https://osv.dev/>
   - Purpose: OSS vulnerability aggregation by package ecosystem, version, commit, & alias.

2. **OSV vulnerability list**
   - Link: <https://osv.dev/list>
   - Purpose: human-browsable OSV records.

3. **OSV full database download**
   - Link: <https://google.github.io/osv.dev/data/#full-database-download>
   - Purpose: full database ZIP, including withdrawn records, via `gs://osv-vulnerabilities/all.zip`.

4. **OSV data sources page**
   - Link: <https://google.github.io/osv.dev/data/>
   - Purpose: per-ecosystem downloads & full-database download.

5. **OSV schema rendered spec**
   - Link: <https://ossf.github.io/osv-schema/>
   - Purpose: standard interchange format for OSS vulnerability records.

6. **OSV schema GitHub repo**
   - Link: <https://github.com/ossf/osv-schema>
   - Purpose: schema source, releases, bindings, tooling.

7. **OSV API docs**
   - Link: <https://google.github.io/osv.dev/post-v1-query/>
   - Purpose: query by package, version, commit, or vulnerability ID.

8. **OSV Scanner**
   - Link: <https://google.github.io/osv-scanner/>
   - Purpose: reference scanner using OSV data.

9. **OSV Scanner GitHub**
   - Link: <https://github.com/google/osv-scanner>
   - Purpose: scanner implementation, matching logic, lockfile parsing.

10. **OSV ecosystem list**
    - Link: <https://osv.dev/list>
    - Purpose: ecosystem browsing, including Maven, npm, PyPI, Go, crates.io, Debian, Alpine, Ubuntu, Wolfi, OSS-Fuzz, etc.

### 2.2 GitHub Advisory Database

1. **GitHub Advisory Database - web**
   - Link: <https://github.com/advisories>
   - Purpose: GitHub-reviewed, unreviewed, malware & GHSA/CVE advisory records.

2. **GitHub Advisory Database repo**
   - Link: <https://github.com/github/advisory-database>
   - Purpose: raw advisory data for local ingestion.

3. **About GitHub Advisory Database**
   - Link: <https://docs.github.com/en/code-security/concepts/vulnerability-reporting-and-management/about-the-github-advisory-database>
   - Purpose: reviewed/unreviewed/malware advisory model.

4. **GitHub Security Advisory GraphQL object**
   - Link: <https://docs.github.com/en/graphql/reference/objects#securityadvisory>
   - Purpose: GraphQL advisory metadata access.

5. **GitHub REST API - global security advisories**
   - Link: <https://docs.github.com/en/rest/security-advisories/global-advisories>
   - Purpose: list & get global security advisories.

6. **GitHub REST API - security advisories root**
   - Link: <https://docs.github.com/en/rest/security-advisories>
   - Purpose: global & repository advisory endpoints.

7. **GitHub Dependabot alerts REST API**
   - Link: <https://docs.github.com/en/rest/dependabot/alerts>
   - Purpose: repository-specific vulnerability exposure from dependency graph.

8. **Dependabot supported ecosystems**
   - Link: <https://docs.github.com/en/code-security/reference/supply-chain-security/supported-ecosystems-and-repositories>
   - Purpose: supported ecosystem list for GitHub dependency graph & alerts.

9. **GitHub malware advisories**
   - Link: <https://github.com/advisories?query=type%3Amalware>
   - Purpose: malicious package advisories.

10. **GitHub npm advisories**
    - Link: <https://github.com/advisories?query=ecosystem%3Anpm>

11. **GitHub pip advisories**
    - Link: <https://github.com/advisories?query=ecosystem%3Apip>

12. **GitHub Maven advisories**
    - Link: <https://github.com/advisories?query=ecosystem%3Amaven>

13. **GitHub NuGet advisories**
    - Link: <https://github.com/advisories?query=ecosystem%3Anuget>

14. **GitHub Go advisories**
    - Link: <https://github.com/advisories?query=ecosystem%3Ago>

15. **GitHub RubyGems advisories**
    - Link: <https://github.com/advisories?query=ecosystem%3Arubygems>

16. **GitHub Rust advisories**
    - Link: <https://github.com/advisories?query=ecosystem%3Arust>

17. **GitHub Composer advisories**
    - Link: <https://github.com/advisories?query=ecosystem%3Acomposer>

18. **GitHub Pub advisories**
    - Link: <https://github.com/advisories?query=ecosystem%3Apub>

19. **GitHub Swift advisories**
    - Link: <https://github.com/advisories?query=ecosystem%3Aswift>

20. **GitHub Erlang advisories**
    - Link: <https://github.com/advisories?query=ecosystem%3Aerlang>

### 2.3 Language & package ecosystem advisory databases

#### 2.3.1 Go

1. **Go Vulnerability Database**
   - Link: <https://vuln.go.dev/>
   - Purpose: official Go vulnerability database.

2. **Go vulnerability database docs**
   - Link: <https://go.dev/doc/security/vuln/database>
   - Purpose: Go vulnerability DB data model & OSV usage.

3. **Go vuln browser**
   - Link: <https://pkg.go.dev/vuln/>
   - Purpose: human-readable Go vulnerability reports.

4. **Go vuln tooling**
   - Link: <https://pkg.go.dev/golang.org/x/vuln/cmd/govulncheck>
   - Purpose: Go source/binary vulnerability checking.

#### 2.3.2 Rust

1. **RustSec**
   - Link: <https://rustsec.org/>
   - Purpose: Rust crate advisories.

2. **RustSec advisory DB repo**
   - Link: <https://github.com/RustSec/advisory-db>
   - Purpose: machine-ingestible Rust advisories.

3. **RustSec advisories browser**
   - Link: <https://rustsec.org/advisories/>

4. **cargo-audit**
   - Link: <https://github.com/RustSec/rustsec/tree/main/cargo-audit>
   - Purpose: RustSec-based vulnerability scanner.

#### 2.3.3 Python / PyPI

1. **PyPA advisory database**
   - Link: <https://github.com/pypa/advisory-database>
   - Purpose: Python/PyPI advisory source.

2. **PyPI security page**
   - Link: <https://pypi.org/security/>
   - Purpose: PyPI security reporting & advisory context.

3. **pip-audit**
   - Link: <https://github.com/pypa/pip-audit>
   - Purpose: Python dependency vulnerability scanning.

4. **Safety DB**
   - Link: <https://github.com/pyupio/safety-db>
   - Purpose: historical Python advisory source.

#### 2.3.4 JavaScript / npm

1. **npm advisories via GitHub**
   - Link: <https://github.com/advisories?query=ecosystem%3Anpm>

2. **Node.js Security Working Group**
   - Link: <https://github.com/nodejs/security-wg>
   - Purpose: Node ecosystem security coordination & historical advisory sources.

3. **npm audit docs**
   - Link: <https://docs.npmjs.com/cli/commands/npm-audit>
   - Purpose: npm ecosystem audit behavior.

4. **Socket.dev security research**
   - Link: <https://socket.dev/blog>
   - Purpose: malicious package & JS supply-chain threat intel.

#### 2.3.5 Java / Maven / JVM

1. **Sonatype OSS Index**
   - Link: <https://ossindex.sonatype.org/>
   - Purpose: OSS vulnerability intelligence, commonly used for Maven & other ecosystems.

2. **Sonatype vulnerability database**
   - Link: <https://sonatype.com/resources/vulnerability-database>

3. **Maven Central**
   - Link: <https://central.sonatype.com/>
   - Purpose: package identity & metadata, useful for resolution.

4. **OSS Index API docs**
   - Link: <https://ossindex.sonatype.org/doc/rest>

#### 2.3.6 PHP / Composer

1. **FriendsOfPHP security advisories**
   - Link: <https://github.com/FriendsOfPHP/security-advisories>

2. **Packagist security advisories API**
   - Link: <https://packagist.org/apidoc#list-security-advisories>

3. **Composer audit docs**
   - Link: <https://getcomposer.org/doc/03-cli.md#audit>

#### 2.3.7 Ruby

1. **RubySec advisory DB**
   - Link: <https://github.com/rubysec/ruby-advisory-db>

2. **Bundler audit**
   - Link: <https://github.com/rubysec/bundler-audit>

#### 2.3.8 .NET / NuGet

1. **NuGet advisories via GitHub**
   - Link: <https://github.com/advisories?query=ecosystem%3Anuget>

2. **NuGet audit docs**
   - Link: <https://learn.microsoft.com/en-us/nuget/concepts/auditing-packages>

#### 2.3.9 Erlang / Elixir / Hex

1. **Erlang advisories via GitHub**
   - Link: <https://github.com/advisories?query=ecosystem%3Aerlang>

2. **Hex package manager**
   - Link: <https://hex.pm/>

#### 2.3.10 Dart / Flutter / Pub

1. **Pub advisories via GitHub**
   - Link: <https://github.com/advisories?query=ecosystem%3Apub>

2. **Dart package repository**
   - Link: <https://pub.dev/>

#### 2.3.11 Swift

1. **Swift advisories via GitHub**
   - Link: <https://github.com/advisories?query=ecosystem%3Aswift>

2. **Swift Package Index**
   - Link: <https://swiftpackageindex.com/>

[Back to index](#index)

---

## 3. Exploitation, prioritization, severity & risk scoring

### 3.1 Known exploited vulnerability sources

1. **CISA KEV catalog - web**
   - Link: <https://www.cisa.gov/known-exploited-vulnerabilities-catalog>
   - Purpose: authoritative known exploited vulnerability catalog.

2. **CISA KEV print view**
   - Link: <https://www.cisa.gov/known-exploited-vulnerabilities-catalog-print>

3. **CISA KEV JSON feed**
   - Link: <https://www.cisa.gov/sites/default/files/feeds/known_exploited_vulnerabilities.json>

4. **CISA KEV JSON schema**
   - Link: <https://www.cisa.gov/sites/default/files/feeds/known_exploited_vulnerabilities_schema.json>

5. **CISA KEV GitHub mirror**
   - Link: <https://github.com/cisagov/kev-data>
   - Purpose: GitHub mirror of KEV data.

6. **VulnCheck KEV**
   - Link: <https://vulncheck.com/kev>
   - Purpose: expanded KEV-like exploitation intelligence.

7. **Shadowserver reports**
   - Link: <https://www.shadowserver.org/>
   - Purpose: internet-scale exploitation & exposure observations.

8. **GreyNoise Visualizer**
   - Link: <https://viz.greynoise.io/>
   - Purpose: internet scanning/exploitation noise & actor context.

9. **GreyNoise API docs**
   - Link: <https://docs.greynoise.io/>
   - Purpose: enrichment API for IP-based exploitation telemetry.

### 3.2 Exploit prediction & scoring

1. **FIRST EPSS overview**
   - Link: <https://www.first.org/epss/>
   - Purpose: Exploit Prediction Scoring System.

2. **FIRST EPSS API**
   - Link: <https://www.first.org/epss/api>

3. **FIRST EPSS data & CSV downloads**
   - Link: <https://www.first.org/epss/data_stats>

4. **Historical EPSS scores GitHub**
   - Link: <https://github.com/empiricalsec/epss_scores>

5. **FIRST CVSS**
   - Link: <https://www.first.org/cvss/>
   - Purpose: official CVSS specification home.

6. **FIRST CVSS v4.0**
   - Link: <https://www.first.org/cvss/v4.0/specification-document>

7. **FIRST CVSS v3.1**
   - Link: <https://www.first.org/cvss/v3.1/specification-document>

8. **NVD CVSS resources**
   - Link: <https://nvd.nist.gov/vuln-metrics/cvss>

### 3.3 Decision-support frameworks

1. **CISA SSVC**
   - Link: <https://www.cisa.gov/stakeholder-specific-vulnerability-categorization-ssvc>
   - Purpose: decision framework for vulnerability response.

2. **CERT/CC SSVC project**
   - Link: <https://github.com/CERTCC/SSVC>

3. **CISA Vulnrichment**
   - Link: <https://github.com/cisagov/vulnrichment>
   - Purpose: CISA ADP enrichment & SSVC decision points.

4. **CISA Binding Operational Directive 22-01**
   - Link: <https://www.cisa.gov/news-events/directives/bod-22-01-reducing-significant-risk-known-exploited-vulnerabilities>
   - Purpose: operational requirement context for KEV remediation.

5. **CISA Cybersecurity Advisories**
   - Link: <https://www.cisa.gov/cybersecurity-advisories>
   - Purpose: broader CISA advisory feed.

6. **CISA Alerts**
   - Link: <https://www.cisa.gov/news-events/cybersecurity-advisories>

### 3.4 Public exploit / proof-of-concept / weaponization signals

1. **Exploit-DB**
   - Link: <https://www.exploit-db.com/>
   - Purpose: public exploit archive.

2. **SearchSploit**
   - Link: <https://www.exploit-db.com/searchsploit>

3. **Exploit-DB GitLab mirror**
   - Link: <https://gitlab.com/exploit-database/exploitdb>

4. **Metasploit Framework**
   - Link: <https://github.com/rapid7/metasploit-framework>

5. **Metasploit exploit modules**
   - Link: <https://github.com/rapid7/metasploit-framework/tree/master/modules/exploits>

6. **Packet Storm Security exploits**
   - Link: <https://packetstormsecurity.com/files/tags/exploit/>

7. **0day.today**
   - Link: <https://0day.today/>
   - Note: Use carefully - quality, legality & attribution vary.

8. **Project Zero blog**
   - Link: <https://googleprojectzero.blogspot.com/>

9. **Project Zero issue tracker - current**
   - Link: <https://project-zero.issues.chromium.org/>

10. **Project Zero issue tracker - old/historical**
    - Link: <https://bugs.chromium.org/p/project-zero/issues/list>

11. **CERT/CC Vulnerability Notes Database**
    - Link: <https://www.kb.cert.org/vuls/>

12. **CERT/CC VINCE public notes**
    - Link: <https://kb.cert.org/vuls/html/>

13. **Rapid7 AttackerKB**
    - Link: <https://attackerkb.com/>
    - Purpose: exploitability & attacker-value context.

14. **Nuclei templates**
    - Link: <https://github.com/projectdiscovery/nuclei-templates>
    - Purpose: exploitable-condition detection templates.

15. **ProjectDiscovery Nuclei**
    - Link: <https://github.com/projectdiscovery/nuclei>

16. **Horizon3.ai research**
    - Link: <https://www.horizon3.ai/attack-research/>
    - Purpose: PoC & attack-path writeups.

17. **watchTowr Labs**
    - Link: <https://labs.watchtowr.com/>
    - Purpose: vulnerability research & exploitation details.

18. **Assetnote research**
    - Link: <https://www.assetnote.io/resources/research>
    - Purpose: exploit research & vulnerability detection signatures.

[Back to index](#index)

---

## 4. CWE, CAPEC, ATT&CK, ATLAS & weakness-to-attack mapping

### 4.1 CWE - Common Weakness Enumeration

1. **CWE home**
   - Link: <https://cwe.mitre.org/>

2. **CWE downloads**
   - Link: <https://cwe.mitre.org/data/downloads.html>
   - Purpose: XML, CSV, archive bundles, views.

3. **CWE latest PDF**
   - Link: <https://cwe.mitre.org/data/published/cwe_latest.pdf>

4. **CWE reports**
   - Link: <https://cwe.mitre.org/data/reports.html>

5. **CWE chains & composites**
   - Link: <https://cwe.mitre.org/data/reports/chains_and_composites.html>

6. **CWE schema docs**
   - Link: <https://cwe.mitre.org/documents/schema/index.html>

7. **CWE data definitions**
   - Link: <https://cwe.mitre.org/data/definitions/1000.html>
   - Purpose: CWE views & weakness hierarchy.

8. **CWE Top 25**
   - Link: <https://cwe.mitre.org/top25/>
   - Purpose: most dangerous software weaknesses.

9. **CWE AI/ML category - CWE-1448**
   - Link: <https://cwe.mitre.org/data/definitions/1448.html>
   - Purpose: AI/ML-related weakness category.

10. **CWE AI Working Group**
    - Link: <https://cwe.mitre.org/community/working_groups.html>
    - Purpose: CWE/CVE AI WG context.

### 4.2 CAPEC - attack patterns

1. **CAPEC home**
   - Link: <https://capec.mitre.org/>
   - Purpose: catalog of attack patterns.

2. **CAPEC downloads**
   - Link: <https://capec.mitre.org/data/downloads.html>
   - Purpose: XML/CSV attack-pattern bundles.

3. **CAPEC schema docs**
   - Link: <https://capec.mitre.org/documents/schema/index.html>

4. **CAPEC data index**
   - Link: <https://capec.mitre.org/data/index.html>

5. **MITRE CTI repository - ATT&CK & CAPEC in STIX**
   - Link: <https://github.com/mitre/cti>
   - Purpose: MITRE ATT&CK & CAPEC datasets expressed in STIX 2.0.

### 4.3 MITRE ATT&CK

1. **ATT&CK Enterprise Matrix**
   - Link: <https://attack.mitre.org/matrices/enterprise/>

2. **ATT&CK Matrices**
   - Link: <https://attack.mitre.org/matrices/>

3. **ATT&CK Data & Tools**
   - Link: <https://attack.mitre.org/resources/attack-data-and-tools/>
   - Purpose: ATT&CK Navigator, STIX/TAXII, Workbench, & tooling references.

4. **ATT&CK STIX data repo**
   - Link: <https://github.com/mitre-attack/attack-stix-data>

5. **MITRE CTI repository**
   - Link: <https://github.com/mitre/cti>

6. **ATT&CK Navigator**
   - Link: <https://mitre-attack.github.io/attack-navigator/>

7. **ATT&CK Workbench**
   - Link: <https://github.com/center-for-threat-informed-defense/attack-workbench-frontend>

8. **ATT&CK TAXII server docs**
   - Link: <https://attack.mitre.org/resources/attack-data-and-tools/>

### 4.4 AI/ML-specific adversary frameworks

1. **MITRE ATLAS**
   - Link: <https://atlas.mitre.org/>
   - Purpose: living knowledge base of adversary tactics & techniques against AI-enabled systems.

2. **MITRE ATLAS matrix**
   - Link: <https://atlas.mitre.org/matrices/ATLAS>

3. **MITRE ATLAS techniques**
   - Link: <https://atlas.mitre.org/techniques>

4. **MITRE ATLAS case studies**
   - Link: <https://atlas.mitre.org/studies>

5. **MITRE ATLAS GitHub / Adversarial ML Threat Matrix**
   - Link: <https://github.com/mitre/advmlthreatmatrix>

6. **MITRE SAFE-AI report**
   - Link: <https://atlas.mitre.org/pdf-files/SAFEAI_Full_Report.pdf>

7. **OWASP Top 10 for LLM Applications**
   - Link: <https://owasp.org/www-project-top-10-for-large-language-model-applications/>

8. **OWASP Top 10 for Machine Learning Security**
   - Link: <https://owasp.org/www-project-machine-learning-security-top-10/>

9. **OWASP AI Exchange**
   - Link: <https://owaspai.org/>

10. **NIST AI Risk Management Framework**
    - Link: <https://www.nist.gov/itl/ai-risk-management-framework>

11. **NIST AI RMF 1.0 PDF**
    - Link: <https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.100-1.pdf>

12. **NIST AI 600-1 - Generative AI Profile**
    - Link: <https://www.nist.gov/publications/artificial-intelligence-risk-management-framework-generative-artificial-intelligence>

13. **NIST adversarial machine learning taxonomy**
    - Link: <https://www.nist.gov/publications/adversarial-machine-learning-taxonomy-and-terminology-attacks-and-mitigations>

14. **MLCommons AI Safety**
    - Link: <https://mlcommons.org/working-groups/ai-safety/>

[Back to index](#index)

---

## 5. Vendor, OS, distribution, container & package affectedness feeds

### 5.1 Scanner-oriented aggregators & vulnerability DB builders

1. **NeuVector vul-dbgen**
   - Link: <https://github.com/neuvector/vul-dbgen>
   - Purpose: vulnerability DB generation source originally flagged by you.

2. **NeuVector vul-source**
   - Link: <https://github.com/neuvector/vul-source>
   - Purpose: vulnerability source data used by NeuVector workflows.

3. **Aqua Trivy vulnerability docs**
   - Link: <https://trivy.dev/docs/latest/scanner/vulnerability/>
   - Purpose: scanner behavior across OS packages, language packages, misconfig, Kubernetes, etc.

4. **Trivy DB**
   - Link: <https://github.com/aquasecurity/trivy-db>
   - Purpose: transforms raw advisories into Trivy DB format.

5. **Trivy Java DB**
   - Link: <https://github.com/aquasecurity/trivy-java-db>

6. **Trivy database configuration docs**
   - Link: <https://trivy.dev/docs/latest/configuration/db/>
   - Purpose: Trivy DB artifacts & purposes.

7. **Anchore Grype**
   - Link: <https://github.com/anchore/grype>

8. **Anchore Grype DB**
   - Link: <https://github.com/anchore/grype-db>
   - Purpose: builds Grype vulnerability database from upstream sources.

9. **Anchore Syft**
   - Link: <https://github.com/anchore/syft>
   - Purpose: SBOM generation for scanning & exposure matching.

10. **Quay ClairCore**
    - Link: <https://github.com/quay/claircore>

11. **Clair**
    - Link: <https://github.com/quay/clair>

12. **VulnerableCode**
    - Link: <https://github.com/nexB/vulnerablecode>
    - Purpose: open vulnerability DB aggregator.

13. **VulnerableCode importer docs**
    - Link: <https://vulnerablecode.readthedocs.io/en/latest/importers_link.html>
    - Purpose: list of supported importer sources.

14. **Dependency-Track**
    - Link: <https://dependencytrack.org/>

15. **Dependency-Track data sources**
    - Link: <https://docs.dependencytrack.org/datasources/overview/>

16. **Dependency-Track GitHub Advisories datasource**
    - Link: <https://docs.dependencytrack.org/datasources/github-advisories/>
    - Purpose: mirrors GHSA via GitHub public GraphQL API.

17. **OpenVAS / Greenbone Community Feed**
    - Link: <https://www.greenbone.net/en/community-feed/>

18. **Wazuh vulnerability detector**
    - Link: <https://documentation.wazuh.com/current/user-manual/capabilities/vulnerability-detection/index.html>

### 5.2 Red Hat / RHEL / CentOS Stream

1. **Red Hat Security Data**
   - Link: <https://access.redhat.com/security/data>
   - Purpose: Red Hat CSAF/VEX, OSV, OVAL, CVE data.

2. **Red Hat Security Data API**
   - Link: <https://docs.redhat.com/en/documentation/red_hat_security_data_api/1.0/html-single/red_hat_security_data_api/index>

3. **Red Hat CVE database**
   - Link: <https://access.redhat.com/security/security-updates/#/cve>

4. **Red Hat OVAL data**
   - Link: <https://www.redhat.com/security/data/oval/>

5. **Red Hat CSAF/VEX guidance**
   - Link: <https://redhatproductsecurity.github.io/security-data-guidelines/csaf-vex/>

6. **Red Hat security advisories**
   - Link: <https://access.redhat.com/security/security-updates/#/security-advisories>

7. **CentOS Stream security tracker**
   - Link: <https://gitlab.com/redhat/centos-stream/rpms>

### 5.3 Debian

1. **Debian Security Tracker**
   - Link: <https://security-tracker.debian.org/>

2. **Debian Security Tracker JSON**
   - Link: <https://security-tracker.debian.org/tracker/data/json>

3. **Debian Security Tracker source Git**
   - Link: <https://salsa.debian.org/security-tracker-team/security-tracker>

4. **Debian Security Information**
   - Link: <https://www.debian.org/security/>

5. **Debian Security Tracker docs**
   - Link: <https://security-team.debian.org/security_tracker.html>

6. **Debian OVAL**
   - Link: <https://www.debian.org/security/oval/>

### 5.4 Ubuntu / Canonical

1. **Ubuntu Security Notices**
   - Link: <https://ubuntu.com/security/notices>

2. **Ubuntu CVE reports**
   - Link: <https://ubuntu.com/security/cves>

3. **Ubuntu OVAL**
   - Link: <https://ubuntu.com/security/oval>

4. **Ubuntu VEX data**
   - Link: <https://ubuntu.com/security/vex>

5. **Ubuntu VEX docs**
   - Link: <https://documentation.ubuntu.com/security/security-updates/vex/>
   - Purpose: Ubuntu VEX sources.

6. **Ubuntu Security Notices GitHub**
   - Link: <https://github.com/canonical/ubuntu-security-notices>
   - Purpose: USN/LSN JSON, OSV JSON, & OpenVEX JSON formats.

7. **Ubuntu Security Tracker Git**
   - Link: <https://git.launchpad.net/ubuntu-cve-tracker>

8. **Ubuntu security updates docs**
   - Link: <https://documentation.ubuntu.com/security/security-updates/>

### 5.5 Alpine

1. **Alpine SecDB**
   - Link: <https://secdb.alpinelinux.org/>
   - Purpose: current Alpine machine-readable security DB.

2. **Alpine Security Tracker**
   - Link: <https://security.alpinelinux.org/>

3. **Alpine SecDB deprecated GitHub mirror**
   - Link: <https://github.com/alpinelinux/alpine-secdb>
   - Purpose: historical compatibility only.

4. **Alpine packages**
   - Link: <https://pkgs.alpinelinux.org/packages>

### 5.6 SUSE / openSUSE

1. **SUSE CSAF**
   - Link: <https://www.suse.com/support/security/csaf/>

2. **SUSE CVRF / OVAL security data**
   - Link: <https://www.suse.com/support/security/oval/>

3. **SUSE CVE pages**
   - Link: <https://www.suse.com/security/cve/>

4. **SUSE Security Advisories**
   - Link: <https://www.suse.com/support/update/announcement/>

5. **openSUSE Security Announce**
   - Link: <https://lists.opensuse.org/archives/list/security-announce@lists.opensuse.org/>

### 5.7 Oracle Linux

1. **Oracle Security Alerts & Critical Patch Updates**
   - Link: <https://www.oracle.com/security-alerts/>

2. **Oracle Linux security data**
   - Link: <https://linux.oracle.com/security/>

3. **Oracle Linux OVAL**
   - Link: <https://linux.oracle.com/security/oval/>

4. **Oracle Linux errata**
   - Link: <https://linux.oracle.com/errata/>

5. **Oracle Linux CVE search**
   - Link: <https://linux.oracle.com/cve/>

### 5.8 Amazon Linux

1. **Amazon Linux Security Center**
   - Link: <https://alas.aws.amazon.com/>

2. **Amazon Linux 2 advisories**
   - Link: <https://alas.aws.amazon.com/alas2.html>

3. **Amazon Linux 2023 advisories**
   - Link: <https://alas.aws.amazon.com/AL2023/>

4. **AWS Security Bulletins**
   - Link: <https://aws.amazon.com/security/security-bulletins/>

### 5.9 Fedora, AlmaLinux, Rocky, Arch, Gentoo

1. **Fedora security updates**
   - Link: <https://bodhi.fedoraproject.org/updates/?type=security>

2. **Fedora packages**
   - Link: <https://packages.fedoraproject.org/>

3. **AlmaLinux Errata**
   - Link: <https://errata.almalinux.org/>

4. **AlmaLinux OSV data**
   - Link: <https://github.com/AlmaLinux/osv-database>

5. **Rocky Linux security advisories**
   - Link: <https://errata.build.resf.org/>

6. **Arch Linux Security Tracker**
   - Link: <https://security.archlinux.org/>

7. **Arch Linux security JSON**
   - Link: <https://security.archlinux.org/json>

8. **Gentoo GLSA**
   - Link: <https://security.gentoo.org/glsa/>

9. **Gentoo GLSA XML**
   - Link: <https://security.gentoo.org/glsa/feed.rss>

### 5.10 Wolfi / Chainguard

1. **Wolfi OS advisories**
   - Link: <https://github.com/wolfi-dev/advisories>

2. **Wolfi SecDB generator**
   - Link: <https://github.com/wolfi-dev/secdb>
   - Purpose: generates Wolfi security DBs based on Alpine secdb format.

3. **Wolfi OS feed**
   - Link: <https://packages.wolfi.dev/os/security.json>

4. **Chainguard Enterprise feed**
   - Link: <https://packages.cgr.dev/chainguard/security.json>

5. **Chainguard security advisories docs**
   - Link: <https://edu.chainguard.dev/chainguard/chainguard-images/staying-secure/security-advisories/how-chainguard-issues/>

6. **Wolfi vulnerabilities in OSV**
   - Link: <https://osv.dev/list?ecosystem=Wolfi>

7. **Chainguard OSV advisory feed context**
   - Link: <https://www.chainguard.dev/unchained/chainguard-enhances-security-with-osv-advisory-feed>

[Back to index](#index)

---

## 6. Vendor advisories for enterprise impact assessment

### 6.1 Major OS, browser & platform vendors

1. **Microsoft Security Update Guide**
   - Link: <https://msrc.microsoft.com/update-guide>

2. **Microsoft MSRC blog**
   - Link: <https://msrc.microsoft.com/blog/>

3. **Microsoft Security Response Center**
   - Link: <https://msrc.microsoft.com/>

4. **Apple Security Releases**
   - Link: <https://support.apple.com/en-us/100100>

5. **Apple security updates**
   - Link: <https://support.apple.com/en-us/HT201222>

6. **Google Android Security Bulletins**
   - Link: <https://source.android.com/docs/security/bulletin>

7. **Google Chrome Releases**
   - Link: <https://chromereleases.googleblog.com/>

8. **Chrome security advisories**
   - Link: <https://chromereleases.googleblog.com/search/label/Security>

9. **Chromium issue tracker**
   - Link: <https://issues.chromium.org/>

10. **Mozilla Security Advisories**
    - Link: <https://www.mozilla.org/en-US/security/advisories/>

11. **Mozilla Foundation Security Advisories**
    - Link: <https://www.mozilla.org/en-US/security/known-vulnerabilities/>

12. **Google Cloud Security Bulletins**
    - Link: <https://cloud.google.com/support/bulletins>

13. **Kubernetes Security Announcements**
    - Link: <https://groups.google.com/g/kubernetes-security-announce>

14. **Kubernetes official CVE feed**
    - Link: <https://kubernetes.io/docs/reference/issues-security/official-cve-feed/>

15. **Kubernetes security & disclosure**
    - Link: <https://kubernetes.io/docs/reference/issues-security/security/>

### 6.2 Enterprise infrastructure vendors

1. **Cisco Security Advisories**
   - Link: <https://sec.cloudapps.cisco.com/security/center/publicationListing.x>

2. **VMware / Broadcom Security Advisories**
   - Link: <https://support.broadcom.com/web/ecx/security-advisory>

3. **Palo Alto Networks Security Advisories**
   - Link: <https://security.paloaltonetworks.com/>

4. **Fortinet PSIRT Advisories**
   - Link: <https://www.fortiguard.com/psirt>

5. **Ivanti Security Advisories**
   - Link: <https://www.ivanti.com/resources/v/doc/ivi/2629/0e3e2be1e66d>

6. **Citrix Security Bulletins**
   - Link: <https://support.citrix.com/securitybulletins>

7. **F5 Security Advisories**
   - Link: <https://my.f5.com/manage/s/solutions?series=Security_Advisory>

8. **Juniper Security Advisories**
   - Link: <https://supportportal.juniper.net/s/global-search/%40uri#sort=relevancy&f:ctype=[Security%20Advisories]>

9. **Dell Security Advisories**
   - Link: <https://www.dell.com/support/security>

10. **HPE Security Bulletins**
    - Link: <https://support.hpe.com/hpesc/public/home>

11. **Lenovo Product Security Advisories**
    - Link: <https://support.lenovo.com/us/en/product_security/home>

12. **IBM PSIRT**
    - Link: <https://www.ibm.com/support/pages/ibm-psirt>

13. **SAP Security Notes**
    - Link: <https://support.sap.com/en/my-support/knowledge-base/security-notes-news.html>

14. **Adobe Security Bulletins**
    - Link: <https://helpx.adobe.com/security.html>

15. **Oracle Critical Patch Updates**
    - Link: <https://www.oracle.com/security-alerts/>

16. **Atlassian Security Advisories**
    - Link: <https://www.atlassian.com/trust/security/advisories>

17. **Elastic Security Announcements**
    - Link: <https://discuss.elastic.co/c/announcements/security-announcements/31>

18. **HashiCorp Security**
    - Link: <https://www.hashicorp.com/security>

19. **GitLab Security Releases**
    - Link: <https://about.gitlab.com/releases/categories/releases/>

20. **Jenkins Security Advisories**
    - Link: <https://www.jenkins.io/security/advisories/>

21. **Apache Security Reports**
    - Link: <https://www.apache.org/security/>

22. **Eclipse Security Advisories**
    - Link: <https://www.eclipse.org/security/>

23. **WordPress Security Releases**
    - Link: <https://wordpress.org/news/category/security/>

24. **Drupal Security Advisories**
    - Link: <https://www.drupal.org/security>

25. **OpenSSL Vulnerabilities**
    - Link: <https://www.openssl.org/news/vulnerabilities.html>

26. **OpenSSH release notes**
    - Link: <https://www.openssh.com/releasenotes.html>

27. **curl security advisories**
    - Link: <https://curl.se/docs/security.html>

### 6.3 Cloud provider security bulletins

1. **AWS Security Bulletins**
   - Link: <https://aws.amazon.com/security/security-bulletins/>

2. **AWS Security Blog**
   - Link: <https://aws.amazon.com/blogs/security/>

3. **Google Cloud Security Bulletins**
   - Link: <https://cloud.google.com/support/bulletins>

4. **Google Cloud Security Blog**
   - Link: <https://cloud.google.com/blog/products/identity-security>

5. **Microsoft Azure security / MSRC**
   - Link: <https://msrc.microsoft.com/update-guide>

6. **Azure updates**
   - Link: <https://azure.microsoft.com/en-us/updates/>

7. **Oracle Cloud security**
   - Link: <https://www.oracle.com/security-alerts/>

8. **IBM Cloud security bulletins**
   - Link: <https://cloud.ibm.com/status/security>

[Back to index](#index)

---

## 7. SBOM, package identity, VEX & advisory exchange standards

### 7.1 SBOM standards

1. **CycloneDX specification overview**
   - Link: <https://cyclonedx.org/specification/overview/>
   - Purpose: SBOM, SaaSBOM, BOM, VEX, vulnerability & component metadata.

2. **CycloneDX GitHub**
   - Link: <https://github.com/CycloneDX/specification>

3. **CycloneDX VEX**
   - Link: <https://cyclonedx.org/capabilities/vex/>

4. **SPDX specifications**
   - Link: <https://spdx.dev/specifications/>

5. **SPDX 3.0.1 spec**
   - Link: <https://spdx.github.io/spdx-spec/v3.0.1/>

6. **SPDX package URL property**
   - Link: <https://spdx.github.io/spdx-spec/v3.0.1/model/Software/Properties/packageUrl/>

7. **SPDX GitHub**
   - Link: <https://github.com/spdx/spdx-spec>

8. **NTIA SBOM resources**
   - Link: <https://www.ntia.gov/page/software-bill-materials>

9. **CISA SBOM**
   - Link: <https://www.cisa.gov/sbom>

### 7.2 Package & software identity

1. **Package URL - PURL spec**
   - Link: <https://github.com/package-url/purl-spec>
   - Purpose: standard package identifier used in SBOMs & vulnerability DBs.

2. **PURL types**
   - Link: <https://github.com/package-url/purl-spec/blob/master/PURL-TYPES.rst>

3. **CPE specification / dictionary**
   - Link: <https://nvd.nist.gov/products/cpe>

4. **NVD CPE API**
   - Link: <https://nvd.nist.gov/developers/products>

5. **SWID tags - NIST**
   - Link: <https://csrc.nist.gov/projects/software-identification-swid>

6. **GS1 Digital Link / identifiers**
   - Link: <https://www.gs1.org/standards/gs1-digital-link>
   - Purpose: optional for product identity in physical/embedded supply chains.

7. **Software Heritage IDs**
   - Link: <https://www.swhid.org/>
   - Purpose: source-code artifact identity.

### 7.3 Advisory exchange, CSAF & VEX

1. **OASIS CSAF 2.0 specification**
   - Link: <https://docs.oasis-open.org/csaf/csaf/v2.0/os/csaf-v2.0-os.html>
   - Purpose: Common Security Advisory Framework.

2. **CSAF home**
   - Link: <https://www.csaf.io/>

3. **OpenVEX specification**
   - Link: <https://github.com/openvex/spec>
   - Purpose: minimal JSON-LD VEX format based on CISA VEX minimum requirements.

4. **OpenVEX project page**
   - Link: <https://openssf.org/projects/openvex/>

5. **CISA Minimum Requirements for VEX**
   - Link: <https://www.cisa.gov/sites/default/files/2023-04/minimum-requirements-for-vex-508c.pdf>
   - Purpose: baseline VEX requirements.

6. **OpenSSF VDR, VEX, OpenVEX & CSAF explainer**
   - Link: <https://openssf.org/blog/2023/09/07/vdr-vex-openvex-and-csaf/>

7. **Red Hat CSAF/VEX guidance**
   - Link: <https://redhatproductsecurity.github.io/security-data-guidelines/csaf-vex/>

8. **Ubuntu VEX**
   - Link: <https://ubuntu.com/security/vex>

9. **Canonical Ubuntu Security Notices repo - OSV & OpenVEX**
   - Link: <https://github.com/canonical/ubuntu-security-notices>

[Back to index](#index)

---

## 8. Malicious package, supply-chain compromise & package reputation sources

### 8.1 Malicious package databases

1. **OpenSSF Malicious Packages repository**
   - Link: <https://github.com/ossf/malicious-packages>
   - Purpose: malicious package reports consumable via OSV format.

2. **OpenSSF Malicious Packages announcement**
   - Link: <https://openssf.org/blog/2023/10/12/introducing-openssfs-malicious-packages-repository/>
   - Purpose: explains public DB for malicious package reports.

3. **OpenSSF Package Analysis**
   - Link: <https://openssf.org/package-analysis/>
   - Purpose: detects malicious package behavior & informs package consumers.

4. **OpenSSF Package Analysis GitHub**
   - Link: <https://github.com/ossf/package-analysis>

5. **OpenSSF Package Feeds**
   - Link: <https://github.com/ossf/package-feeds>

6. **GitHub malware advisories**
   - Link: <https://github.com/advisories?query=type%3Amalware>

7. **npm malware advisories via GitHub**
   - Link: <https://github.com/advisories?query=ecosystem%3Anpm+type%3Amalware>

8. **PyPI malware advisories via GitHub**
   - Link: <https://github.com/advisories?query=ecosystem%3Apip+type%3Amalware>

9. **Socket.dev blog**
   - Link: <https://socket.dev/blog>

10. **Snyk vulnerability database**
    - Link: <https://security.snyk.io/>

11. **Sonatype OSS Index**
    - Link: <https://ossindex.sonatype.org/>

12. **Sonatype vulnerability database**
    - Link: <https://sonatype.com/resources/vulnerability-database>

13. **Phylum research**
    - Link: <https://blog.phylum.io/>

14. **ReversingLabs threat research**
    - Link: <https://www.reversinglabs.com/blog>

15. **Checkmarx supply-chain research**
    - Link: <https://checkmarx.com/blog/>

### 8.2 Package reputation / dependency health

1. **OpenSSF Scorecard**
   - Link: <https://github.com/ossf/scorecard>

2. **OpenSSF Scorecard API**
   - Link: <https://api.securityscorecards.dev/>

3. **OpenSSF Best Practices Badge**
   - Link: <https://www.bestpractices.dev/>

4. **deps.dev**
   - Link: <https://deps.dev/>
   - Purpose: dependency metadata, transitive dependencies, security signals.

5. **OpenSSF GUAC**
   - Link: <https://guac.sh/>
   - Purpose: graph for software supply-chain metadata.

6. **GUAC GitHub**
   - Link: <https://github.com/guacsec/guac>

7. **Sigstore**
   - Link: <https://www.sigstore.dev/>

8. **Rekor transparency log**
   - Link: <https://docs.sigstore.dev/logging/overview/>

9. **SLSA framework**
   - Link: <https://slsa.dev/>

[Back to index](#index)

---

## 9. Automated vulnerability detection, static analysis, dynamic analysis & research datasets

### 9.1 SAST / code query engines

1. **CodeQL**
   - Link: <https://codeql.github.com/>

2. **CodeQL GitHub**
   - Link: <https://github.com/github/codeql>

3. **CodeQL query packs**
   - Link: <https://github.com/github/codeql/tree/main>

4. **Semgrep**
   - Link: <https://semgrep.dev/>

5. **Semgrep rules**
   - Link: <https://github.com/semgrep/semgrep-rules>

6. **Joern**
   - Link: <https://joern.io/>

7. **Joern GitHub**
   - Link: <https://github.com/joernio/joern>

8. **Facebook Infer**
   - Link: <https://fbinfer.com/>

9. **Infer GitHub**
   - Link: <https://github.com/facebook/infer>

10. **SonarQube rules**
    - Link: <https://rules.sonarsource.com/>

11. **Bandit - Python**
    - Link: <https://github.com/PyCQA/bandit>

12. **Gosec - Go**
    - Link: <https://github.com/securego/gosec>

13. **ESLint security plugin**
    - Link: <https://github.com/eslint-community/eslint-plugin-security>

14. **SpotBugs**
    - Link: <https://spotbugs.github.io/>

15. **FindSecBugs**
    - Link: <https://find-sec-bugs.github.io/>

16. **Clang Static Analyzer**
    - Link: <https://clang-analyzer.llvm.org/>

17. **Cppcheck**
    - Link: <https://cppcheck.sourceforge.io/>

18. **Flawfinder**
    - Link: <https://dwheeler.com/flawfinder/>

19. **Brakeman - Ruby on Rails**
    - Link: <https://brakemanscanner.org/>

20. **Horusec**
    - Link: <https://github.com/ZupIT/horusec>

21. **Bearer**
    - Link: <https://github.com/Bearer/bearer>

22. **MobSF**
    - Link: <https://github.com/MobSF/Mobile-Security-Framework-MobSF>

### 9.2 DAST, IAST, fuzzing & dynamic test sources

1. **OSS-Fuzz**
   - Link: <https://google.github.io/oss-fuzz/>

2. **OSS-Fuzz GitHub**
   - Link: <https://github.com/google/oss-fuzz>

3. **OSS-Fuzz vulnerability data in OSV**
   - Link: <https://osv.dev/list?ecosystem=OSS-Fuzz>

4. **ClusterFuzzLite**
   - Link: <https://google.github.io/clusterfuzzlite/>

5. **AFL++**
   - Link: <https://github.com/AFLplusplus/AFLplusplus>

6. **libFuzzer**
   - Link: <https://llvm.org/docs/LibFuzzer.html>

7. **Honggfuzz**
   - Link: <https://github.com/google/honggfuzz>

8. **Jazzer**
   - Link: <https://github.com/CodeIntelligenceTesting/jazzer>

9. **OWASP ZAP**
   - Link: <https://www.zaproxy.org/>

10. **Nuclei**
    - Link: <https://github.com/projectdiscovery/nuclei>

11. **Nuclei templates**
    - Link: <https://github.com/projectdiscovery/nuclei-templates>

### 9.3 Vulnerability-detection research datasets

1. **NIST SARD**
   - Link: <https://samate.nist.gov/SARD/>

2. **Juliet Test Suite - NIST SARD**
   - Link: <https://samate.nist.gov/SARD/test-suites/112>

3. **Big-Vul**
   - Link: <https://github.com/ZeoVan/MSR_20_Code_vulnerability_CSV_Dataset>

4. **Devign**
   - Link: <https://sites.google.com/view/devign>

5. **Draper VDISC**
   - Link: <https://osf.io/d45bw/>

6. **DiverseVul**
   - Link: <https://github.com/wagner-group/diversevul>

7. **PrimeVul**
   - Link: <https://github.com/DLVulDet/PrimeVul>

8. **MegaVul**
   - Link: <https://github.com/Icyrockton/MegaVul>

9. **Vul4J**
   - Link: <https://github.com/tuhh-softsec/vul4j>

10. **VulnCode-DB**
    - Link: <https://github.com/vegardit/vulncode-db>

11. **SecurityEval**
    - Link: <https://github.com/s2e-lab/SecurityEval>

12. **CVEfixes**
    - Link: <https://github.com/secureIT-project/CVEfixes>

13. **Defects4J**
    - Link: <https://github.com/rjust/defects4j>

14. **ManySStuBs4J**
    - Link: <https://github.com/mast-group/mineSStuBs>

15. **VulDeePecker**
    - Link: <https://github.com/CGCL-codes/VulDeePecker>

[Back to index](#index)

---

## 10. ICS, OT, IoT, embedded & medical-device sources

### 10.1 CISA ICS / medical

1. **CISA ICS Advisories**
   - Link: <https://www.cisa.gov/news-events/ics-advisories>

2. **CISA ICS Medical Advisories**
   - Link: <https://www.cisa.gov/news-events/ics-medical-advisories>

3. **CISA cybersecurity advisories**
   - Link: <https://www.cisa.gov/cybersecurity-advisories>

4. **ICS-CERT advisories archive**
   - Link: <https://www.cisa.gov/news-events/ics-advisories>

5. **CISA ICS recommended practices**
   - Link: <https://www.cisa.gov/resources-tools/resources/ics-recommended-practices>

### 10.2 OT / ICS vendor advisories

1. **Siemens ProductCERT**
   - Link: <https://cert-portal.siemens.com/productcert/>

2. **Schneider Electric Security Notifications**
   - Link: <https://www.se.com/ww/en/work/support/cybersecurity/security-notifications.jsp>

3. **Rockwell Automation Security Advisories**
   - Link: <https://www.rockwellautomation.com/en-us/support/product/product-security-advisories.html>

4. **Honeywell Product Security**
   - Link: <https://www.honeywell.com/us/en/product-security>

5. **Philips Product Security**
   - Link: <https://www.philips.com/a-w/security/security-advisories.html>

6. **GE Vernova Product Security**
   - Link: <https://www.gevernova.com/product-security>

7. **ABB Cyber Security Alerts**
   - Link: <https://global.abb/group/en/technology/cyber-security/alerts-and-notifications>

8. **Yokogawa Security Advisories**
   - Link: <https://www.yokogawa.com/library/resources/white-papers/yokogawa-security-advisory-report-list/>

9. **Mitsubishi Electric PSIRT**
   - Link: <https://www.mitsubishielectric.com/en/psirt/vulnerability/>

10. **Johnson Controls Product Security Advisories**
    - Link: <https://www.johnsoncontrols.com/cyber-solutions/security-advisories>

### 10.3 IoT / embedded

1. **CERT/CC Vulnerability Notes**
   - Link: <https://www.kb.cert.org/vuls/>

2. **IoT Security Foundation**
   - Link: <https://www.iotsecurityfoundation.org/>

3. **Firmware Analysis and Comparison Tool - FACT**
   - Link: <https://github.com/fkie-cad/FACT_core>

4. **EMBA firmware analyzer**
   - Link: <https://github.com/e-m-b-a/emba>

5. **Binwalk**
   - Link: <https://github.com/ReFirmLabs/binwalk>

[Back to index](#index)

---

## 11. Exposure, internet-facing asset & threat telemetry

### 11.1 Internet exposure search engines

1. **Censys Search**
   - Link: <https://search.censys.io/>

2. **Censys API**
   - Link: <https://search.censys.io/api>

3. **Shodan**
   - Link: <https://www.shodan.io/>

4. **Shodan developer API**
   - Link: <https://developer.shodan.io/>

5. **ZoomEye**
   - Link: <https://www.zoomeye.org/>

6. **FOFA**
   - Link: <https://fofa.info/>

7. **BinaryEdge**
   - Link: <https://www.binaryedge.io/>

8. **Onyphe**
   - Link: <https://www.onyphe.io/>

9. **SecurityTrails**
   - Link: <https://securitytrails.com/>

10. **InternetDB by Shodan**
    - Link: <https://internetdb.shodan.io/>

### 11.2 Scan/exploitation telemetry

1. **GreyNoise Visualizer**
   - Link: <https://viz.greynoise.io/>

2. **GreyNoise API docs**
   - Link: <https://docs.greynoise.io/>

3. **Shadowserver**
   - Link: <https://www.shadowserver.org/>

4. **Shadowserver reports**
   - Link: <https://dashboard.shadowserver.org/>

5. **SANS Internet Storm Center**
   - Link: <https://isc.sans.edu/>

6. **Honeynet Project**
   - Link: <https://www.honeynet.org/>

7. **DShield**
   - Link: <https://www.dshield.org/>

8. **LeakIX**
   - Link: <https://leakix.net/>

9. **urlscan.io**
   - Link: <https://urlscan.io/>

10. **VirusTotal**
    - Link: <https://www.virustotal.com/>

11. **VirusTotal API**
    - Link: <https://docs.virustotal.com/reference/overview>

### 11.3 Attack surface management context

1. **Amass**
   - Link: <https://github.com/owasp-amass/amass>

2. **ProjectDiscovery Subfinder**
   - Link: <https://github.com/projectdiscovery/subfinder>

3. **httpx**
   - Link: <https://github.com/projectdiscovery/httpx>

4. **Naabu**
   - Link: <https://github.com/projectdiscovery/naabu>

5. **Nmap**
   - Link: <https://nmap.org/>

6. **Masscan**
   - Link: <https://github.com/robertdavidgraham/masscan>

[Back to index](#index)

---

## 12. Threat intelligence, malware, ransomware & in-the-wild exploitation context

### 12.1 Major threat research sources

1. **Mandiant / Google Cloud Threat Intelligence**
   - Link: <https://cloud.google.com/blog/topics/threat-intelligence>

2. **Microsoft Threat Intelligence blog**
   - Link: <https://www.microsoft.com/en-us/security/blog/topic/threat-intelligence/>

3. **Google Threat Analysis Group**
   - Link: <https://blog.google/threat-analysis-group/>

4. **Palo Alto Unit 42**
   - Link: <https://unit42.paloaltonetworks.com/>

5. **Cisco Talos**
   - Link: <https://blog.talosintelligence.com/>

6. **Rapid7 vulnerability management blog**
   - Link: <https://www.rapid7.com/blog/tag/vulnerability-management/>

7. **Sophos X-Ops**
   - Link: <https://news.sophos.com/en-us/category/threat-research/>

8. **CrowdStrike Blog**
   - Link: <https://www.crowdstrike.com/en-us/blog/>

9. **SentinelOne Labs**
   - Link: <https://www.sentinelone.com/labs/>

10. **Kaspersky Securelist**
    - Link: <https://securelist.com/>

11. **ESET WeLiveSecurity**
    - Link: <https://www.welivesecurity.com/>

12. **Trend Micro Research**
    - Link: <https://www.trendmicro.com/en_us/research.html>

13. **FortiGuard Labs**
    - Link: <https://www.fortiguard.com/research>

14. **Check Point Research**
    - Link: <https://research.checkpoint.com/>

15. **Elastic Security Labs**
    - Link: <https://www.elastic.co/security-labs>

16. **Sekoia Threat Intelligence**
    - Link: <https://blog.sekoia.io/>

### 12.2 Malware & IOC repositories

1. **MISP**
   - Link: <https://www.misp-project.org/>

2. **AlienVault OTX**
   - Link: <https://otx.alienvault.com/>

3. **AbuseIPDB**
   - Link: <https://www.abuseipdb.com/>

4. **URLhaus**
   - Link: <https://urlhaus.abuse.ch/>

5. **MalwareBazaar**
   - Link: <https://bazaar.abuse.ch/>

6. **ThreatFox**
   - Link: <https://threatfox.abuse.ch/>

7. **Feodo Tracker**
   - Link: <https://feodotracker.abuse.ch/>

8. **PhishTank**
   - Link: <https://phishtank.org/>

9. **OpenPhish**
   - Link: <https://openphish.com/>

10. **YARA**
    - Link: <https://github.com/VirusTotal/yara>

11. **YARA-Rules**
    - Link: <https://github.com/Yara-Rules/rules>

12. **SigmaHQ**
    - Link: <https://github.com/SigmaHQ/sigma>

13. **LOLBAS**
    - Link: <https://lolbas-project.github.io/>

14. **GTFOBins**
    - Link: <https://gtfobins.github.io/>

15. **Ransomware.live**
    - Link: <https://www.ransomware.live/>

[Back to index](#index)

---

## 13. Compliance, baseline configuration & exposure severity standards

These are not vulnerability feeds, but they help assess impact, control failure, configuration exposure, & exploitability in a given environment.

### 13.1 Security configuration & benchmarks

1. **CIS Benchmarks**
   - Link: <https://www.cisecurity.org/cis-benchmarks>

2. **CIS Controls**
   - Link: <https://www.cisecurity.org/controls>

3. **NIST National Checklist Program**
   - Link: <https://ncp.nist.gov/>

4. **DISA STIGs**
   - Link: <https://public.cyber.mil/stigs/>

5. **OpenSCAP**
   - Link: <https://www.open-scap.org/>

6. **SCAP Security Guide**
   - Link: <https://github.com/ComplianceAsCode/content>

### 13.2 Cloud configuration posture

1. **Prowler - AWS/Azure/GCP/Kubernetes**
   - Link: <https://github.com/prowler-cloud/prowler>

2. **CloudSplaining**
   - Link: <https://github.com/salesforce/cloudsplaining>

3. **ScoutSuite**
   - Link: <https://github.com/nccgroup/ScoutSuite>

4. **Steampipe mods**
   - Link: <https://hub.steampipe.io/mods>

5. **Cloud Custodian**
   - Link: <https://cloudcustodian.io/>

6. **Kubernetes CIS benchmark**
   - Link: <https://www.cisecurity.org/benchmark/kubernetes>

7. **kube-bench**
   - Link: <https://github.com/aquasecurity/kube-bench>

8. **kube-hunter**
   - Link: <https://github.com/aquasecurity/kube-hunter>

[Back to index](#index)

---

## 14. Source-code, dependency, artifact & build-chain provenance

### 14.1 Source & artifact provenance

1. **SLSA**
   - Link: <https://slsa.dev/>

2. **Sigstore**
   - Link: <https://www.sigstore.dev/>

3. **Cosign**
   - Link: <https://github.com/sigstore/cosign>

4. **Rekor**
   - Link: <https://docs.sigstore.dev/logging/overview/>

5. **in-toto**
   - Link: <https://in-toto.io/>

6. **The Update Framework - TUF**
   - Link: <https://theupdateframework.io/>

7. **SLSA GitHub generators**
   - Link: <https://github.com/slsa-framework/slsa-github-generator>

### 14.2 Dependency inventory & graphing

1. **deps.dev**
   - Link: <https://deps.dev/>

2. **GUAC**
   - Link: <https://guac.sh/>

3. **GUAC GitHub**
   - Link: <https://github.com/guacsec/guac>

4. **OpenSSF Scorecard**
   - Link: <https://github.com/ossf/scorecard>

5. **OpenSSF Scorecard API**
   - Link: <https://api.securityscorecards.dev/>

6. **Maven Central**
   - Link: <https://central.sonatype.com/>

7. **npm registry**
   - Link: <https://registry.npmjs.org/>

8. **PyPI JSON API**
   - Link: <https://docs.pypi.org/api/json/>

9. **crates.io API**
   - Link: <https://crates.io/data-access>

10. **Go module proxy**
    - Link: <https://proxy.golang.org/>

[Back to index](#index)

---

## 15. Practical priority hierarchy for ingestion

### 15.1 Tier 0 - identifiers & inventory

1. **SBOM**
   - Sources: CycloneDX, SPDX.

2. **Package identity**
   - Sources: PURL, CPE, SWID.

3. **Asset exposure**
   - Sources: CMDB/cloud inventory, Censys/Shodan, internal scanning.

4. **Artifact provenance**
   - Sources: SLSA, Sigstore, in-toto.

### 15.2 Tier 1 - canonical vulnerability records

1. CVE List v5.
2. CVE schema.
3. CVE Services API.
4. NVD CVE API.
5. NVD CPE API.
6. NVD data feeds.
7. CISA Vulnrichment.

### 15.3 Tier 2 - package/ecosystem vulnerability records

1. OSV full database.
2. OSV API.
3. GitHub Advisory Database.
4. GitHub Advisory Database repo.
5. Go vuln DB.
6. RustSec.
7. PyPA advisory DB.
8. FriendsOfPHP.
9. RubySec.
10. OSS Index.
11. Packagist API.

### 15.4 Tier 3 - affectedness, distro & vendor truth

1. Red Hat Security Data.
2. Debian Security Tracker.
3. Ubuntu OVAL / OSV / OpenVEX.
4. Alpine SecDB.
5. SUSE CSAF / OVAL.
6. Oracle Linux OVAL / errata.
7. Amazon Linux ALAS.
8. AlmaLinux / Rocky / Fedora / Arch / Gentoo.
9. Wolfi / Chainguard.
10. Vendor advisories: Microsoft, Apple, Cisco, VMware/Broadcom, Fortinet, Palo Alto, Ivanti, Adobe, Oracle, SAP, Atlassian, F5, Citrix.

### 15.5 Tier 4 - severity & prioritization

1. CVSS v3.1/v4.0.
2. EPSS.
3. KEV.
4. SSVC.
5. CISA Vulnrichment.
6. Vendor “exploited in the wild” flags.
7. Patch availability & fixed-version feeds.
8. Environmental context - internet exposure, asset criticality, privilege boundary, data sensitivity.

### 15.6 Tier 5 - exploitability & weaponization

1. Exploit-DB.
2. Metasploit modules.
3. Packet Storm.
4. Project Zero.
5. CERT/CC VU notes.
6. Rapid7 AttackerKB.
7. GreyNoise.
8. Shadowserver.
9. Nuclei templates.
10. Vendor emergency advisories.

### 15.7 Tier 6 - weakness, attack-pattern & AI context

1. CWE.
2. CAPEC.
3. ATT&CK Enterprise.
4. ATT&CK STIX.
5. MITRE CTI repo.
6. MITRE ATLAS.
7. OWASP LLM Top 10.
8. OWASP ML Security Top 10.
9. NIST AI RMF & NIST AI 600-1.

### 15.8 Tier 7 - detection engineering & validation

1. CodeQL.
2. Semgrep.
3. Joern.
4. Infer.
5. Sonar rules.
6. Nuclei templates.
7. OSS-Fuzz.
8. SARD / Juliet.
9. Big-Vul, Devign, DiverseVul, PrimeVul, MegaVul, CVEfixes, Vul4J.

[Back to index](#index)

---

## 16. Recommended canonical data model coverage

A complete vulnerability impact system should be able to ingest or derive these fields.

### 16.1 Vulnerability identity

1. CVE ID.
2. GHSA ID.
3. OSV ID.
4. Vendor advisory ID.
5. CWE ID.
6. CAPEC ID.
7. ATT&CK technique ID.
8. ATLAS technique ID.
9. Alias graph across CVE/GHSA/OSV/vendor IDs.

### 16.2 Affectedness

1. Product name.
2. Vendor.
3. CPE.
4. PURL.
5. Package ecosystem.
6. Package name.
7. Affected version range.
8. Fixed version.
9. Introduced version / commit.
10. Last affected version.
11. Backport status.
12. VEX status:
    - affected
    - not affected
    - fixed
    - under investigation
13. Justification for not affected.
14. Distro/package release channel.

### 16.3 Severity & exploitability

1. CVSS v2/v3/v4 vector.
2. CVSS base/temporal/environmental score.
3. EPSS score.
4. EPSS percentile.
5. KEV membership.
6. KEV date added.
7. Known ransomware usage.
8. Public exploit available.
9. Metasploit module available.
10. Nuclei template available.
11. GreyNoise observed scanning.
12. Shadowserver observed exposure.
13. CISA SSVC decision points.
14. Vendor exploitation status.
15. Patch availability.
16. Workaround availability.

### 16.4 Environmental impact

1. Asset criticality.
2. Internet exposure.
3. Network reachability.
4. Authentication required.
5. Privilege required.
6. User interaction required.
7. Exploit preconditions.
8. Data sensitivity.
9. Compensating controls.
10. Runtime configuration.
11. Feature/module enabled.
12. Cloud account/project/environment.
13. Blast radius.
14. Business process ownership.

### 16.5 Detection & remediation

1. Scanner finding ID.
2. Detection method:
   - SBOM match
   - CPE match
   - package-manager match
   - SAST
   - DAST
   - IaC
   - runtime telemetry
3. Confidence.
4. False-positive reason.
5. Fix version.
6. Patch advisory.
7. Mitigation.
8. Workaround.
9. Exploit detection signatures.
10. Regression test.
11. Verification command.
12. SLA due date.

[Back to index](#index)

---

## 17. Minimal source set for production use

For a first production-grade ingestion system, start with:

1. **CVE List v5**
   - Link: <https://github.com/CVEProject/cvelistV5>

2. **CVE schema**
   - Link: <https://github.com/CVEProject/cve-schema>

3. **NVD CVE API**
   - Link: <https://nvd.nist.gov/developers/vulnerabilities>

4. **NVD CPE API**
   - Link: <https://nvd.nist.gov/developers/products>

5. **OSV full database**
   - Link: <https://google.github.io/osv.dev/data/#full-database-download>

6. **OSV schema**
   - Link: <https://ossf.github.io/osv-schema/>

7. **GitHub Advisory Database repo**
   - Link: <https://github.com/github/advisory-database>

8. **CISA KEV JSON**
   - Link: <https://www.cisa.gov/sites/default/files/feeds/known_exploited_vulnerabilities.json>

9. **CISA Vulnrichment**
   - Link: <https://github.com/cisagov/vulnrichment>

10. **FIRST EPSS**
    - Link: <https://www.first.org/epss/>

11. **CWE downloads**
    - Link: <https://cwe.mitre.org/data/downloads.html>

12. **CAPEC downloads**
    - Link: <https://capec.mitre.org/data/downloads.html>

13. **ATT&CK STIX data**
    - Link: <https://github.com/mitre-attack/attack-stix-data>

14. **MITRE ATLAS**
    - Link: <https://atlas.mitre.org/>

15. **CycloneDX**
    - Link: <https://cyclonedx.org/specification/overview/>

16. **SPDX**
    - Link: <https://spdx.dev/specifications/>

17. **PURL**
    - Link: <https://github.com/package-url/purl-spec>

18. **CSAF**
    - Link: <https://docs.oasis-open.org/csaf/csaf/v2.0/os/csaf-v2.0-os.html>

19. **OpenVEX**
    - Link: <https://github.com/openvex/spec>

20. **Distro feeds**
    - Red Hat, Debian, Ubuntu, Alpine, SUSE, Oracle, Amazon Linux, Wolfi/Chainguard.

21. **Exploit signal feeds**
    - Exploit-DB, Metasploit, CERT/CC, Project Zero, GreyNoise, Shadowserver.

[Back to index](#index)

---

## 18. Final structure for all vulnerability management sources & exposure listings

Use this top-level taxonomy in your system:

1. **Canonical vulnerability records**
   - CVE, NVD, CVE schema, Vulnrichment.

2. **Package & ecosystem advisories**
   - OSV, GHSA, language advisory DBs.

3. **Vendor & distro affectedness**
   - CSAF, VEX, OVAL, secdb, OSV, vendor advisories.

4. **Exploitability & prioritization**
   - KEV, EPSS, SSVC, CVSS, Exploit-DB, Metasploit, GreyNoise.

5. **Weakness & adversary mapping**
   - CWE, CAPEC, ATT&CK, ATLAS.

6. **AI-specific vulnerability context**
   - ATLAS, OWASP LLM Top 10, OWASP ML Top 10, NIST AI RMF.

7. **SBOM & identity**
   - CycloneDX, SPDX, PURL, CPE, SWID.

8. **Exposure telemetry**
   - Censys, Shodan, Shadowserver, GreyNoise, LeakIX, internal asset inventory.

9. **Malicious package & supply-chain compromise**
   - OpenSSF malicious packages, Package Analysis, Socket, Snyk, Sonatype, GitHub malware advisories.

10. **Detection engineering**
    - CodeQL, Semgrep, Joern, Infer, Nuclei, OSS-Fuzz, SARD, vulnerability datasets.

11. **Threat intelligence**
    - Mandiant, Microsoft, Google TAG, Unit 42, Talos, Rapid7, ransomware & IOC feeds.

12. **Compliance & configuration impact**
    - CIS, STIG, SCAP, cloud posture, Kubernetes benchmarks.

[Back to index](#index)
