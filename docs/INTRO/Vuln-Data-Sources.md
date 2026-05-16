
# CveToad Vulnerability Management Source Inventory

### A consolidated super-set vulnerability-management source inventory for assessing impact, severity, exploitability, exposure, affectedness, prioritization, & remediation of vulnerabilities in technical systems.


## `License`
>      Copyright Ⓒ 2025 Keerthana Purushotham <keep.consult@proton.me>.
>      Licensed under the GNU AGPL v3. See LICENSE for details.
> [*see license*](https://github.com/keerthanap8898/CveToad/blob/main/LICENSE)

### Note:
> - *Some vendor/security pages change URLs over time, so treat this as a high-coverage baseline rather than a mathematically exhaustive list of every possible vulnerability source.*
> - *Key access assumptions were checked against official/public docs where feasible: NVD is free with stricter unauthenticated rate limits & higher limits with an API key; GitHub Advisory Database is free/open-source for global advisories; CISA KEV is public; FIRST EPSS is freely available via CSV/API.*
> - *Access / Cost labels are best-effort. Many sources are free to read but may require authentication, registration, support entitlement, API keys, paid tiers, or commercial licenses for higher-volume automation, advanced APIs, or complete data. Recheck terms before production ingestion.*
> - *Link-checking note: treat 403, bot-blocked pages, JavaScript-heavy portals, vendor support portals, rate-limited APIs, & authentication-gated consoles as `restricted/manual-review`, not necessarily broken.*

---

### Lifecycle organization:
> - **Chapter A** - CVE record intake, identity, schema & governance.
> - **Chapter B** - CVE enrichment, exploitability, prioritization & data model.
> - **Chapter C** - Weakness taxonomy, attack mapping & AI/ML vulnerability context.
> - **Chapter D** - Affectedness truth across packages, OSes, vendors, cloud, ICS & products.
> - **Chapter E** - Security supply-chain evidence, SBOM, VEX, provenance & malicious package risk.
> - **Chapter F** - Detection, exposure, threat telemetry, validation & remediation operations.
> - **Chapter G** - Governance, compliance, assurance, production baselines & final operating model.

---
## Index


- #### **[A. `CVE Record Intake, Identity, Schema & Program Governance`](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#a-cve-record-intake-identity-schema--program-governance)**

  - **[1. `Corrections & normalization notes`](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#1-corrections--normalization-notes)**

  - **[2. `Canonical vulnerability identifiers, CVE records & schemas`](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#2-canonical-vulnerability-identifiers-cve-records--schemas)**
     - [2.1 CVE Program - canonical CVE identity](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#21-cve-program---canonical-cve-identity)
     - [2.2 NVD - CVE enrichment, CPE matching, CVSS & configurations](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#22-nvd---cve-enrichment-cpe-matching-cvss--configurations)
     - [2.3 Optional CVE meta-mirrors / commercial-community enrichments](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#23-optional-cve-meta-mirrors--commercial-community-enrichments)
     - [2.4 CVE Program governance, project repos, working groups & SADP](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#24-cve-program-governance-project-repos-working-groups--sadp)
     - [2.5 Free CVE lifecycle data feeds, APIs & endpoint references](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#25-free-cve-lifecycle-data-feeds-apis--endpoint-references)

  - **[3. `CVE metadata analytical framework, user-story resources, papers & community governance`](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#3-cve-metadata-analytical-framework-user-story-resources-papers--community-governance)**
     - [3.1 CveToad CVE consumer/user-story resources](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#31-cvetoad-cve-consumeruser-story-resources)
     - [3.2 CVE/CWE working groups, SIGs & community lists](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#32-cvecwe-working-groups-sigs--community-lists)
     - [3.3 Papers, conference programs, talks, training & community material](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#33-papers-conference-programs-talks-training--community-material)


- #### **[B. `CVE Enrichment, Exploitability, Prioritization & Data Model`](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#b-cve-enrichment-exploitability-prioritization--data-model)**

  - **[4. `Exploitation, prioritization, severity & risk scoring`](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#4-exploitation-prioritization-severity--risk-scoring)**
     - [4.1 Known exploited vulnerability sources](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#41-known-exploited-vulnerability-sources)
     - [4.2 Exploit prediction & scoring](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#42-exploit-prediction--scoring)
     - [4.3 Decision-support frameworks](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#43-decision-support-frameworks)
     - [4.4 Public exploit / proof-of-concept / weaponization signals](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#44-public-exploit--proof-of-concept--weaponization-signals)

  - **[5. `Practical priority hierarchy for ingestion`](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#5-practical-priority-hierarchy-for-ingestion)**
     - [5.1 Tier 0 - identifiers & inventory](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#51-tier-0---identifiers--inventory)
     - [5.2 Tier 1 - canonical vulnerability records](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#52-tier-1---canonical-vulnerability-records)
     - [5.3 Tier 2 - package/ecosystem vulnerability records](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#53-tier-2---packageecosystem-vulnerability-records)
     - [5.4 Tier 3 - affectedness, distro & vendor truth](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#54-tier-3---affectedness-distro--vendor-truth)
     - [5.5 Tier 4 - severity & prioritization](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#55-tier-4---severity--prioritization)
     - [5.6 Tier 5 - exploitability & weaponization](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#56-tier-5---exploitability--weaponization)
     - [5.7 Tier 6 - weakness, attack-pattern & AI context](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#57-tier-6---weakness-attack-pattern--ai-context)
     - [5.8 Tier 7 - detection engineering & validation](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#58-tier-7---detection-engineering--validation)

  - **[6. `Recommended canonical data model coverage`](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#6-recommended-canonical-data-model-coverage)**
     - [6.1 Vulnerability identity](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#61-vulnerability-identity)
     - [6.2 Affectedness](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#62-affectedness)
     - [6.3 Severity & exploitability](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#63-severity--exploitability)
     - [6.4 Environmental impact](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#64-environmental-impact)
     - [6.5 Detection & remediation](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#65-detection--remediation)


- #### **[C. `Weakness Taxonomy, Attack Mapping & AI/ML Vulnerability Context`](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#c-weakness-taxonomy-attack-mapping--aiml-vulnerability-context)**

   - **[7. `CWE, CAPEC, ATT&CK, ATLAS & weakness-to-attack mapping`](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#7-cwe-capec-attck-atlas--weakness-to-attack-mapping)**
     - [7.1 CWE - Common Weakness Enumeration](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#71-cwe---common-weakness-enumeration)
     - [7.2 CAPEC - attack patterns](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#72-capec---attack-patterns)
     - [7.3 MITRE ATT&CK](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#73-mitre-attck)
     - [7.4 AI/ML-specific adversary frameworks](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#74-aiml-specific-adversary-frameworks)


- #### **[D. `Affectedness Truth: Package, OS, Vendor, Cloud, ICS & Product Advisories`](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#d-affectedness-truth-package-os-vendor-cloud-ics--product-advisories)**

  - **[8. `Open-source vulnerability databases & package advisory sources`](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#8-open-source-vulnerability-databases--package-advisory-sources)**
     - [8.1 OSV ecosystem](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#81-osv-ecosystem)
     - [8.2 GitHub Advisory Database](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#82-github-advisory-database)
     - [8.3 Language & package ecosystem advisory databases](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#83-language--package-ecosystem-advisory-databases)

  - **[9. `Vendor, OS, distribution, container & package affectedness feeds`](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#9-vendor-os-distribution-container--package-affectedness-feeds)**
     - [9.1 Scanner-oriented aggregators & vulnerability DB builders](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#91-scanner-oriented-aggregators--vulnerability-db-builders)
     - [9.2 Red Hat / RHEL / CentOS Stream](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#92-red-hat--rhel--centos-stream)
     - [9.3 Debian](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#93-debian)
     - [9.4 Ubuntu / Canonical](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#94-ubuntu--canonical)
     - [9.5 Alpine](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#95-alpine)
     - [9.6 SUSE / openSUSE](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#96-suse--opensuse)
     - [9.7 Oracle Linux](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#97-oracle-linux)
     - [9.8 Amazon Linux](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#98-amazon-linux)
     - [9.9 Fedora, AlmaLinux, Rocky, Arch, Gentoo](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#99-fedora-almalinux-rocky-arch-gentoo)
     - [9.10 Wolfi / Chainguard](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#910-wolfi--chainguard)

  - **[10. `Vendor advisories for enterprise impact assessment`](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#10-vendor-advisories-for-enterprise-impact-assessment)**
     - [10.1 Major OS, browser & platform vendors](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#101-major-os-browser--platform-vendors)
     - [10.2 Enterprise infrastructure vendors](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#102-enterprise-infrastructure-vendors)
     - [10.3 Cloud provider security bulletins](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#103-cloud-provider-security-bulletins)

  - **[11. `ICS, OT, IoT, embedded & medical-device sources`](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#11-ics-ot-iot-embedded--medical-device-sources)**
     - [11.1 CISA ICS / medical](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#111-cisa-ics--medical)
     - [11.2 OT / ICS vendor advisories](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#112-ot--ics-vendor-advisories)
     - [11.3 IoT / embedded](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#113-iot--embedded)


- #### **[E. `Security Supply Chain Evidence: SBOM, VEX, Provenance & Malicious Package Risk`](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#e-security-supply-chain-evidence-sbom-vex-provenance--malicious-package-risk)**

  - **[12. `SBOM, package identity, VEX & advisory exchange standards`](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#12-sbom-package-identity-vex--advisory-exchange-standards)**
     - [12.1 SBOM standards](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#121-sbom-standards)
     - [12.2 Package & software identity](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#122-package--software-identity)
     - [12.3 Advisory exchange, CSAF & VEX](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#123-advisory-exchange-csaf--vex)

  - **[13. `Malicious package, supply-chain compromise & package reputation sources`](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#13-malicious-package-supply-chain-compromise--package-reputation-sources)**
     - [13.1 Malicious package databases](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#131-malicious-package-databases)
     - [13.2 Package reputation / dependency health](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#132-package-reputation--dependency-health)

  - **[14. `Source-code, dependency, artifact & build-chain provenance`](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#14-source-code-dependency-artifact--build-chain-provenance)**
     - [14.1 Source & artifact provenance](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#141-source--artifact-provenance)
     - [14.2 Dependency inventory & graphing](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#142-dependency-inventory--graphing)


- #### **[F. `Detection, Exposure, Threat Telemetry, Validation & Remediation Operations`](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#f-detection-exposure-threat-telemetry-validation--remediation-operations)**

  - **[15. `Automated vulnerability detection, static analysis, dynamic analysis & research datasets`](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#15-automated-vulnerability-detection-static-analysis-dynamic-analysis--research-datasets)**
     - [15.1 SAST / code query engines](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#151-sast--code-query-engines)
     - [15.2 DAST, IAST, fuzzing & dynamic test sources](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#152-dast-iast-fuzzing--dynamic-test-sources)
     - [15.3 Vulnerability-detection research datasets](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#153-vulnerability-detection-research-datasets)

  - **[16. `Exposure, internet-facing asset & threat telemetry`](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#16-exposure-internet-facing-asset--threat-telemetry)**
     - [16.1 Internet exposure search engines](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#161-internet-exposure-search-engines)
     - [16.2 Scan/exploitation telemetry](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#162-scanexploitation-telemetry)
     - [16.3 Attack surface management context](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#163-attack-surface-management-context)
      
  - **[17. `Threat intelligence, malware, ransomware & in-the-wild exploitation context`](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#17-threat-intelligence-malware-ransomware--in-the-wild-exploitation-context)**
     - [17.1 Major threat research sources](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#171-major-threat-research-sources)
     - [17.2 Malware & IOC repositories](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#172-malware--ioc-repositories)

      
- #### **[G. `Governance, Compliance, Assurance, Production Baselines & Final Operating Model`](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#g-governance-compliance-assurance-production-baselines--final-operating-model)**
  
  - **[18. `Compliance, baseline configuration, software assurance & exposure severity standards`](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#18-compliance-baseline-configuration-software-assurance--exposure-severity-standards)**
     - [18.1 Security configuration & benchmarks](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#181-security-configuration--benchmarks)
     - [18.2 Cloud configuration posture](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#182-cloud-configuration-posture)
     - [18.3 Software assurance, secure development, acquisition & NIST publication libraries](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#183-software-assurance-secure-development-acquisition--nist-publication-libraries)
      
  - **[19. `Minimal source set for production use`](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#19-minimal-source-set-for-production-use)**
    
  - **[20. `Final structure for all vulnerability management sources & exposure listings`](https://github.com/keerthanap8898/CveToad/blob/main/docs/INTRO/Vuln-Data-Sources.md#20-final-structure-for-all-vulnerability-management-sources--exposure-listings)**

---

## A. CVE Record Intake, Identity, Schema & Program Governance

## 1. Corrections & normalization notes

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **Project Zero issue tracker migration**<br><br>**`Link(s)`:** [bugs.chromium.org/p/project-zero/issues/list](https://bugs.chromium.org/p/project-zero/issues/list), [project-zero.issues.chromium.org/issues](https://project-zero.issues.chromium.org/issues)<br><br>**`Access / Cost`:** Free public web access | **`Relevance`:** Tracks high-quality vulnerability research, root-cause analysis, exploitability notes, & coordinated disclosure. Useful for exploitability context & historical vulnerability behavior.<br><br>**`Notes & POIs`:** Prefer the current tracker for ongoing lookups. Keep the old Monorail-style link for historical references that still appear in older writeups. |
| 2 | **Alpine SecDB mirror normalization**<br><br>**`Link(s)`:** [github.com/alpinelinux/alpine-secdb](https://github.com/alpinelinux/alpine-secdb), [secdb.alpinelinux.org](https://secdb.alpinelinux.org/)<br><br>**`Access / Cost`:** Free / open-source | **`Relevance`:** Provides Alpine package vulnerability affectedness. Important for container images using Alpine as a base.<br><br>**`Notes & POIs`:** The GitHub mirror is deprecated. Use `secdb.alpinelinux.org` as the primary ingestion source. |
| 3 | **Wolfi / Chainguard feed split**<br><br>**`Link(s)`:** [packages.cgr.dev/chainguard/security.json](https://packages.cgr.dev/chainguard/security.json), [packages.wolfi.dev/os/security.json](https://packages.wolfi.dev/os/security.json)<br><br>**`Access / Cost`:** Free public feed for Wolfi; Chainguard feed may depend on product entitlement | **`Relevance`:** Provides secdb-style security feeds for Wolfi & Chainguard images. Key for modern minimal container images.<br><br>**`Notes & POIs`:** The Wolfi feed & Chainguard Enterprise feed represent related but distinct package universes. Avoid treating them as exact duplicates. |
| 4 | **GitHub Advisory APIs**<br><br>**`Link(s)`:** [docs.github.com/en/graphql/reference/objects#securityadvisory](https://docs.github.com/en/graphql/reference/objects#securityadvisory), [docs.github.com/en/rest/security-advisories](https://docs.github.com/en/rest/security-advisories), [docs.github.com/en/rest/security-advisories/global-advisories](https://docs.github.com/en/rest/security-advisories/global-advisories)<br><br>**`Access / Cost`:** Free public global advisories; authenticated API / repository advisories may require GitHub account & permissions | **`Relevance`:** Enables programmatic access to GitHub advisories, including GHSA records, CVE aliases, ecosystems, version ranges, & malware advisories.<br><br>**`Notes & POIs`:** Keep both GraphQL & REST. GraphQL is useful for complex queries; REST is simpler for ingestion & pagination. |
| 5 | **NVD feeds vs APIs**<br><br>**`Link(s)`:** [nvd.nist.gov/developers](https://nvd.nist.gov/developers), [nvd.nist.gov/vuln/data-feeds](https://nvd.nist.gov/vuln/data-feeds)<br><br>**`Access / Cost`:** Free public; optional free API key for higher rate limits | **`Relevance`:** NVD provides CVE enrichment, CPE configurations, CVSS vectors, CWE mappings, references, & change metadata.<br><br>**`Notes & POIs`:** Prefer NVD 2.0 APIs for ongoing sync. Use bulk feeds for bootstrapping, archival snapshots, or local mirroring. |
| 6 | **Link-check allowlist / restricted-source policy**<br><br>**`Link(s)`:** Vendor portals, support portals, API consoles, bot-blocked pages, JavaScript-heavy search pages<br><br>**`Access / Cost`:** Not a data source | **`Relevance`:** Avoids false “broken link” classifications in CI.<br><br>**`Notes & POIs`:** Treat `403`, bot-blocked, JS-only, rate-limited, auth-gated, & support-entitlement pages as `restricted/manual-review`, not automatically dead. |

> 
> #### [*Back to **`Index`***](#index)
> 
> ---

## 2. Canonical vulnerability identifiers, CVE records & schemas

### 2.1 CVE Program - canonical CVE identity

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **CVE.org**<br><br>**`Link(s)`:** [www.cve.org](https://www.cve.org/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Official CVE program portal for CVE IDs, CNA/ADP governance, CVE lookup, & program documentation.<br><br>**`Notes & POIs`:** Canonical governance source, but not always the richest technical source for scoring, affected versions, or exploitability. |
| 2 | **CVE List v5 - official GitHub mirror/cache**<br><br>**`Link(s)`:** [github.com/CVEProject/cvelistV5](https://github.com/CVEProject/cvelistV5)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** Primary public GitHub cache of CVE v5 JSON records. Useful for local mirroring, batch parsing, & canonical CVE field extraction.<br><br>**`Notes & POIs`:** Records may vary in completeness by CNA. Use with NVD, OSV, vendor advisories, & CISA Vulnrichment for enrichment. |
| 3 | **CVE Record Format schema - direct JSON schema**<br><br>**`Link(s)`:** [github.com/CVEProject/cve-schema/blob/main/schema/CVE_Record_Format.json](https://github.com/CVEProject/cve-schema/blob/main/schema/CVE_Record_Format.json)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** Machine-validation schema for CVE v5 records. Required for parser validation & ingestion guardrails.<br><br>**`Notes & POIs`:** Schema correctness does not imply record semantic completeness. Validate schema & still handle missing CNA fields. |
| 4 | **CVE schema repository**<br><br>**`Link(s)`:** [github.com/CVEProject/cve-schema](https://github.com/CVEProject/cve-schema)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** Contains schema versions, tests, examples, release history, & format evolution.<br><br>**`Notes & POIs`:** Track schema version drift when maintaining long-lived ingestion pipelines. |
| 5 | **CVE Services API / CVE Program API**<br><br>**`Link(s)`:** [cveawg.mitre.org/api-docs](https://cveawg.mitre.org/api-docs/)<br><br>**`Access / Cost`:** Free public docs; API workflows may require role/account for CNA functions | **`Relevance`:** Direct CVE lookup & CVE Services API documentation. Useful for targeted lookup workflows.<br><br>**`Notes & POIs`:** API usage may differ from GitHub mirror sync behavior. Use for lookup, not necessarily full mirroring. |
| 6 | **CVE Authorized Data Publishers - ADPs**<br><br>**`Link(s)`:** [www.cve.org/ProgramOrganization/ADPs](https://www.cve.org/ProgramOrganization/ADPs)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Lists ADPs that can enrich CVE records beyond CNA-provided content.<br><br>**`Notes & POIs`:** ADP enrichment can add critical assessment context. Treat ADP data as enrichment layered on top of canonical CNA data. |
| 7 | **CISA Vulnrichment - CVE ADP enrichment**<br><br>**`Link(s)`:** [github.com/cisagov/vulnrichment](https://github.com/cisagov/vulnrichment)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** Provides CISA ADP enrichment of CVE records, including SSVC decision points, & sometimes CWE/CVSS details.<br><br>**`Notes & POIs`:** Useful for prioritization. Coverage may not be universal across all CVEs. Track freshness & missing enrichment states. |

### 2.2 NVD - CVE enrichment, CPE matching, CVSS & configurations

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **NVD home**<br><br>**`Link(s)`:** [nvd.nist.gov](https://nvd.nist.gov/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** U.S. government vulnerability-management repository. Provides vulnerability metadata, scoring, product mapping, & references.<br><br>**`Notes & POIs`:** NVD enrichment may lag behind CVE publication or vendor disclosures. Monitor modified dates. |
| 2 | **NVD CVE API 2.0**<br><br>**`Link(s)`:** [nvd.nist.gov/developers/vulnerabilities](https://nvd.nist.gov/developers/vulnerabilities)<br><br>**`Access / Cost`:** Free public; optional free API key for higher rate limits | **`Relevance`:** Retrieves CVEs with CVSS, weaknesses, references, CPE configurations, & change history.<br><br>**`Notes & POIs`:** Central for CPE-based product matching. Rate limits & API keys may affect ingestion design. |
| 3 | NVD CPE API 2.0 | [nvd.nist.gov/developers/products](https://nvd.nist.gov/developers/products) | Free public; optional free API key for higher rate limits | Provides CPE dictionary & CPE match criteria for product/platform matching. | CPE can be imprecise for packages, forks, backports, & cloud services. Combine with PURL, OSV, & vendor feeds. |
| 4 | NVD Data Feeds | [nvd.nist.gov/vuln/data-feeds](https://nvd.nist.gov/vuln/data-feeds) | Free public | Bulk JSON feeds for CVEs, CPE dictionary, & CPE match feeds. Useful for initial database bootstrapping. | APIs are generally preferred for ongoing updates. Feeds are useful for snapshots & offline ingestion. |
| 5 | NVD CVSS resources | [nvd.nist.gov/vuln-metrics/cvss](https://nvd.nist.gov/vuln-metrics/cvss) | Free public | CVSS calculators, vector definitions, & severity scoring references. | CVSS is severity, not exploit likelihood. Combine with EPSS, KEV, exposure, & asset criticality. |
| 6 | NVD CPE Dictionary | [nvd.nist.gov/products/cpe](https://nvd.nist.gov/products/cpe) | Free public | CPE product naming & matching basis. | CPE coverage & naming consistency vary. False positives are common without vendor/package-specific affectedness. |
| 7 | NVD API documentation root | [nvd.nist.gov/developers](https://nvd.nist.gov/developers) | Free public | API family documentation for NVD data access. | Use this as the stable entry point for NVD API changes. |
| 8 | NVD CVE Change History API | [nvd.nist.gov/developers/vulnerabilities](https://nvd.nist.gov/developers/vulnerabilities) | Free public; optional free API key for higher rate limits | Enables monitoring changes to CVE enrichment, scoring, references, & configurations. | Treat NVD records as mutable. Store ingestion timestamp, source modified timestamp, & prior versions where possible. |

### 2.3 Optional CVE meta-mirrors / commercial-community enrichments
These are useful as secondary sources, not canonical replacements.

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **VulnCheck NVD++**<br><br>**`Link(s)`:** [www.vulncheck.com/nvd2](https://www.vulncheck.com/nvd2)<br><br>**`Access / Cost`:** Commercial; limited free/public info may exist | **`Relevance`:** Aggregated vulnerability intelligence that can supplement CVE/NVD/KEV workflows.<br><br>**`Notes & POIs`:** Commercial/community enrichment. Validate terms, licensing, API access, & provenance before production use. |
| 2 | **Vulners**<br><br>**`Link(s)`:** [vulners.com](https://vulners.com/)<br><br>**`Access / Cost`:** Free web search; API/advanced features may require paid plan | **`Relevance`:** Vulnerability intelligence aggregator across many advisory & exploit sources.<br><br>**`Notes & POIs`:** Useful for broad search & enrichment. Do not treat as canonical without source provenance. |
| 3 | **OpenCVE**<br><br>**`Link(s)`:** [www.opencve.io](https://www.opencve.io/)<br><br>**`Access / Cost`:** Free tier / paid plans | **`Relevance`:** CVE monitoring, subscriptions, change tracking, & alerting workflows.<br><br>**`Notes & POIs`:** Useful for monitoring, but canonical ingestion should still pull from upstream CVE/NVD/vendor feeds. |
| 4 | **CIRCL Vulnerability-Lookup / CVE Search**<br><br>**`Link(s)`:** [cve.circl.lu](https://cve.circl.lu/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** CVE search & enrichment source, historically useful for threat-intel workflows.<br><br>**`Notes & POIs`:** Validate freshness before relying on it. Prefer canonical sources for production scoring. |
| 5 | **Vulnerability-Lookup GitHub repository**<br><br>**`Link(s)`:** [github.com/vulnerability-lookup/vulnerability-lookup](https://github.com/vulnerability-lookup/vulnerability-lookup)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** Correlates vulnerabilities from multiple sources independent of vulnerability IDs & supports coordinated vulnerability disclosure workflows.<br><br>**`Notes & POIs`:** Useful as a CVE/vulnerability correlation platform. Treat as a secondary aggregation/enrichment source, not canonical truth. |

### 2.4 CVE Program governance, project repos, working groups & SADP

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **CVEProject GitHub organization**<br><br>**`Link(s)`:** [github.com/CVEProject](https://github.com/CVEProject)<br><br>**`Access / Cost`:** Free public GitHub org | **`Relevance`:** Source organization for CVE schema, CVE list mirror, automation working group material, & related program repos.<br><br>**`Notes & POIs`:** Useful for tracking official repository structure & project-level changes. |
| 2 | **CVE Program Working Groups**<br><br>**`Link(s)`:** [www.cve.org/programorganization/workinggroups](https://www.cve.org/programorganization/workinggroups)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Official CVE Working Group listing.<br><br>**`Notes & POIs`:** Governance/process context, not a vulnerability feed. |
| 3 | **CVE/CWE Programs groups.io main page**<br><br>**`Link(s)`:** [cve-cwe-programs.groups.io/g/main](https://cve-cwe-programs.groups.io/g/main)<br><br>**`Access / Cost`:** Public/registration may vary by list | **`Relevance`:** Community list hub for CVE/CWE program discussions.<br><br>**`Notes & POIs`:** Use for process context, community discussions, & WG announcements. |
| 4 | **CVE/CWE Programs groups.io subgroups**<br><br>**`Link(s)`:** [cve-cwe-programs.groups.io/g/main/subgroups](https://cve-cwe-programs.groups.io/g/main/subgroups)<br><br>**`Access / Cost`:** Public/registration may vary by list | **`Relevance`:** Subgroup listing for program working groups.<br><br>**`Notes & POIs`:** Useful for discovering WG-specific list URLs. |
| 5 | **CVE Consumer Working Group**<br><br>**`Link(s)`:** [cve-cwe-programs.groups.io/g/ConsumerWG](https://cve-cwe-programs.groups.io/g/ConsumerWG)<br><br>**`Access / Cost`:** Public/registration may vary by list | **`Relevance`:** CVE consumer feedback, use cases, & schema/process discussions.<br><br>**`Notes & POIs`:** Important for consumer-oriented CVE metadata requirements. |
| 6 | **CVE Automation Working Group repo**<br><br>**`Link(s)`:** [github.com/CVEProject/automation-working-group](https://github.com/CVEProject/automation-working-group)<br><br>**`Access / Cost`:** Free public GitHub repo | **`Relevance`:** Automation WG materials, workflows, & implementation discussion artifacts.<br><br>**`Notes & POIs`:** Useful for automation requirements around CVE publication & ingestion. |
| 7 | **CVE Automation Working Group list**<br><br>**`Link(s)`:** [cve-cwe-programs.groups.io/g/AWG](https://cve-cwe-programs.groups.io/g/AWG)<br><br>**`Access / Cost`:** Public/registration may vary by list | **`Relevance`:** Automation WG mailing list.<br><br>**`Notes & POIs`:** Useful for process & tooling evolution tracking. |
| 8 | **CVEProject SADP pilot**<br><br>**`Link(s)`:** [github.com/CVEProject/sadp-pilot](https://github.com/CVEProject/sadp-pilot)<br><br>**`Access / Cost`:** Free public GitHub repo | **`Relevance`:** Supplemental ADP/SADP pilot data & artifacts.<br><br>**`Notes & POIs`:** Useful for tracking supplemental vulnerability enrichment experiments. |
| 9 | **Published SADP Records**<br><br>**`Link(s)`:** [github.com/CVEProject/sadp-pilot/tree/main/Published%20SADP%20Records](https://github.com/CVEProject/sadp-pilot/tree/main/Published%20SADP%20Records)<br><br>**`Access / Cost`:** Free public GitHub repo path | **`Relevance`:** Published SADP record corpus.<br><br>**`Notes & POIs`:** Machine-readable/source-record context should be validated before ingestion. |
| 10 | **RogoLabs SADP Tracker**<br><br>**`Link(s)`:** [rogolabs.github.io/SADP-Tracker](https://rogolabs.github.io/SADP-Tracker)<br><br>**`Access / Cost`:** Public site; manually revalidate | **`Relevance`:** Community tracker for SADP material.<br><br>**`Notes & POIs`:** Add to link-check allowlist until manually verified. |
| 11 | **CWE Working Groups & SIGs**<br><br>**`Link(s)`:** [cwe.mitre.org/community/working_groups.html](https://cwe.mitre.org/community/working_groups.html)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** CWE working group & SIG context.<br><br>**`Notes & POIs`:** Important for weakness taxonomy evolution, including AI/ML-related CWE work. |
| 12 | **CVE Services source repository**<br><br>**`Link(s)`:** [github.com/CVEProject/cve-services](https://github.com/CVEProject/cve-services)<br><br>**`Access / Cost`:** Free public GitHub repo | **`Relevance`:** Source repository for the CVE Services API.<br><br>**`Notes & POIs`:** Useful for understanding CVE API implementation behavior, endpoint evolution, & service-side validation semantics. |

### 2.5 Free CVE lifecycle data feeds, APIs & endpoint references

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **CVE Services API - OpenAPI & public CVE record lookup**<br><br>**`Link(s)`:** [CVE Services API docs](https://cveawg.mitre.org/api-docs/), [OpenAPI JSON](https://cveawg.mitre.org/api-docs/openapi.json), [CVE Services base API](https://cveawg.mitre.org/api)<br><br>**`Access / Cost`:** Free public API docs; most write/assignment endpoints require CVE Services credentials; public record lookup is documented as accessible to all. | **`Relevance`:** Official lifecycle API surface for CVE ID lookup, CVE record retrieval, CVE reservation, submission, updates, & CNA/Secretariat workflows.<br><br>**`Notes & POIs`:** Primary endpoint family to document: `/api/cve/{id}` for CVE record lookup, `/api/cve-id` for CVE ID workflows, & authenticated CNA/Secretariat endpoints for reserve/submit/update operations. |
| 2 | **CVE Partner List - Root CNAs, CNAs & CNA scope discovery**<br><br>**`Link(s)`:** [CVE Partner List](https://www.cve.org/PartnerInformation/ListofPartners)<br><br>**`Access / Cost`:** Free public web listing; JavaScript rendering/manual review may be needed for automation. | **`Relevance`:** Authoritative source for current CVE Program partners, CNA scope boundaries, Root CNAs, & CNA status verification.<br><br>**`Notes & POIs`:** Use to verify CNA status before marking OpenAI, Cloudflare, CrowdStrike, or any vendor as a confirmed CNA. Treat as manual-review source in link-check CI. |
| 3 | **CVE Program CNA Rules & program process resources**<br><br>**`Link(s)`:** [CVE Program CNA Rules](https://www.cve.org/ResourcesSupport/AllResources/CNARules), [CVE Services overview](https://www.cve.org/AllResources/CveServices)<br><br>**`Access / Cost`:** Free public CVE Program documentation. | **`Relevance`:** Defines CNA responsibilities, CVE assignment behavior, record publication expectations, & lifecycle governance rules.<br><br>**`Notes & POIs`:** Use as policy source for CVE reservation, publication, rejection, record updates, scope boundaries, & quality requirements. |
| 4 | **Google Root CNA / Google Bug Hunters VRP**<br><br>**`Link(s)`:** [Google Bug Hunters](https://bughunters.google.com/), [Google Product Security](https://about.google/appsecurity/), [CVE Partner List](https://www.cve.org/PartnerInformation/ListofPartners)<br><br>**`Access / Cost`:** Free public program pages; CNA role should be verified against the live CVE partner list. | **`Relevance`:** Google Root CNA / disclosure path for Google, Android, Chrome, Cloud, AI, & ecosystem issues.<br><br>**`Notes & POIs`:** Keep distinct from Project Zero, Android bulletins, Chrome release posts, Google Cloud bulletins, & OSV. |
| 5 | **INCIBE-CERT Root CNA / Spanish vulnerability coordination**<br><br>**`Link(s)`:** [INCIBE-CERT](https://www.incibe.es/en/incibe-cert), [INCIBE advisories](https://www.incibe.es/en/incibe-cert/early-warning/security-advisories), [CVE Partner List](https://www.cve.org/PartnerInformation/ListofPartners)<br><br>**`Access / Cost`:** Free public web access; some materials may require Spanish/English page handling. | **`Relevance`:** Root CNA / national coordination source relevant to European & Spanish vulnerability coordination.<br><br>**`Notes & POIs`:** Add to CVE governance because CVE Services docs name INCIBE as a Root CNA credential-routing option. |
| 6 | **JPCERT/CC Root CNA, JVN & MyJVN feeds**<br><br>**`Link(s)`:** [JPCERT/CC English](https://www.jpcert.or.jp/english/), [JVN English](https://jvn.jp/en/), [JVN English RSS](https://jvn.jp/en/rss/jvn.rdf), [MyJVN API](https://jvndb.jvn.jp/apis/myjvn/)<br><br>**`Access / Cost`:** Free public web/RSS/API documentation; API query construction requires MyJVN parameters. | **`Relevance`:** Root CNA / Japan vulnerability coordination source, including Japanese Vulnerability Notes & JVN iPedia-style data access.<br><br>**`Notes & POIs`:** Useful for Asia/Japan disclosure context, multi-vendor coordination, JVN identifiers, & CVE cross-reference workflows. |
| 7 | **Linux Kernel CNA & linux-cve-announce archive**<br><br>**`Link(s)`:** [linux-cve-announce archive](https://lore.kernel.org/linux-cve-announce/), [Linux kernel security docs](https://docs.kernel.org/process/security-bugs.html), [kernel.org](https://www.kernel.org/)<br><br>**`Access / Cost`:** Free public mailing-list archive & documentation. | **`Relevance`:** Kernel-specific CVE assignment, disclosure, patch-flow, & affectedness context.<br><br>**`Notes & POIs`:** Track separately from Red Hat, Debian, Ubuntu, SUSE, Amazon Linux, Android, & other downstream distro advisories because distro backports can differ from upstream kernel status. |
| 8 | **CERT/CC Vulnerability Notes & RSS**<br><br>**`Link(s)`:** [CERT/CC VULS](https://www.kb.cert.org/vuls/), [CERT/CC VULS RSS](https://www.kb.cert.org/vuls/rss)<br><br>**`Access / Cost`:** Free public web/RSS access; RSS endpoint should be kept in manual-review allowlist if fetcher blocks it. | **`Relevance`:** CVD coordination, multi-vendor vulnerability notes, affected-vendor status, & remediation guidance.<br><br>**`Notes & POIs`:** Add as CNA/coordinator lifecycle source, not only exploit/disclosure context. |
| 9 | **Microsoft MSRC Security Update Guide / CVRF API**<br><br>**`Link(s)`:** [MSRC Update Guide](https://msrc.microsoft.com/update-guide), [MSRC CVRF updates API](https://api.msrc.microsoft.com/cvrf/v3.0/updates), [MSRC CVRF document example](https://api.msrc.microsoft.com/cvrf/v3.0/cvrf/2025-Mar)<br><br>**`Access / Cost`:** Free public web/API access; rate limits & versioned document IDs should be handled by ingestion jobs. | **`Relevance`:** Microsoft CNA/product-security source for Microsoft CVEs, affected products, KBs, severity, CVRF-style update metadata, & remediation references.<br><br>**`Notes & POIs`:** Use `/updates` to discover release document IDs, then fetch specific CVRF documents such as `/cvrf/{documentId}` for detailed security update metadata. |
| 10 | **Microsoft Defender Vulnerability Management - list vulnerabilities API**<br><br>**`Link(s)`:** [List vulnerabilities docs](https://learn.microsoft.com/en-us/defender-endpoint/api/get-all-vulnerabilities), [Vulnerabilities endpoint](https://api.security.microsoft.com/api/Vulnerabilities)<br><br>**`Access / Cost`:** Requires Microsoft Defender for Endpoint/Defender Vulnerability Management permissions & bearer token. | **`Relevance`:** Asset-aware vulnerability inventory endpoint with CVE ID, CVSS, exploit flags, exposed machines, EPSS, status, & dates.<br><br>**`Notes & POIs`:** Use as enterprise exposure overlay rather than canonical global vulnerability truth. |
| 11 | **Microsoft Defender Vulnerability Management - per-device software vulnerabilities export**<br><br>**`Link(s)`:** [Export software vulnerabilities assessment docs](https://learn.microsoft.com/en-us/defender-endpoint/api/get-assessment-software-vulnerabilities), [SoftwareVulnerabilitiesByMachine endpoint](https://api.security.microsoft.com/api/machines/SoftwareVulnerabilitiesByMachine)<br><br>**`Access / Cost`:** Requires Defender API permissions; supports JSON response & via-file export patterns. | **`Relevance`:** Maps CVEs to device, software vendor/name/version, OS platform, exploitability level, first/last seen timestamps, & available security updates.<br><br>**`Notes & POIs`:** Best for exposure/affectedness correlation inside an organization. Save snapshots for history because current exports may not preserve historical state. |
| 12 | **Cisco PSIRT openVuln API**<br><br>**`Link(s)`:** [Cisco PSIRT openVuln API docs](https://developer.cisco.com/docs/psirt/), [Cisco Security Advisories](https://sec.cloudapps.cisco.com/security/center/publicationListing.x)<br><br>**`Access / Cost`:** Free docs; API use may require Cisco developer/auth workflow depending on endpoint & volume. | **`Relevance`:** Machine-consumable Cisco vulnerability advisories, queryable by advisory ID, CVE ID, bug ID, product type, software version, & timeframe.<br><br>**`Notes & POIs`:** Cisco docs state JSON/XML output & location data for CVRF/CSAF retrieval. Prefer CSAF where available. |
| 13 | **Cloudflare security disclosure, security.txt & public security research feed**<br><br>**`Link(s)`:** [Cloudflare security.txt](https://www.cloudflare.com/.well-known/security.txt), [Cloudflare security policy](https://www.cloudflare.com/disclosure/), [Cloudflare security-tag RSS](https://blog.cloudflare.com/tag/security/rss/)<br><br>**`Access / Cost`:** Free public web/RSS; no dedicated public CVE advisory API confirmed in this pass. | **`Relevance`:** Cloudflare product/security disclosure path & security research stream for edge, WAF, DNS, CDN, Workers, Zero Trust, & cloud/network service vulnerability context.<br><br>**`Notes & POIs`:** Treat as disclosure/research feed, not canonical CVE data unless a Cloudflare CVE/advisory record is explicitly published. |
| 14 | **CrowdStrike public research feed & Falcon Spotlight vulnerability data - restricted**<br><br>**`Link(s)`:** [CrowdStrike blog feed](https://www.crowdstrike.com/en-us/blog/feed/), [CrowdStrike blog](https://www.crowdstrike.com/en-us/blog/), [FalconPy docs](https://falconpy.io/)<br><br>**`Access / Cost`:** Public blog/RSS; Falcon platform vulnerability/Spotlight APIs are authenticated/commercial & not a free public CVE feed. | **`Relevance`:** Threat-intel, exploitability, adversary, & enterprise vulnerability-management context; useful for prioritization & exploitation signals.<br><br>**`Notes & POIs`:** Do not list CrowdStrike as a free canonical CVE data feed unless a specific public API/feed is verified. |
| 15 | **Zero Day Initiative - published & upcoming advisories**<br><br>**`Link(s)`:** [ZDI published advisories](https://www.zerodayinitiative.com/advisories/published/), [ZDI upcoming advisories](https://www.zerodayinitiative.com/advisories/upcoming/), [ZDI published RSS](https://www.zerodayinitiative.com/rss/published/)<br><br>**`Access / Cost`:** Free public web/RSS. | **`Relevance`:** Pre-disclosure & published vulnerability coordination, exploitability context, vendor disclosure timelines, & ZDI identifiers.<br><br>**`Notes & POIs`:** Useful for tracking vulnerabilities before or around CVE publication. Cross-reference with CVE/NVD/vendor records after publication. |
| 16 | **Openwall oss-security mailing list & RSS**<br><br>**`Link(s)`:** [oss-security archive](https://www.openwall.com/lists/oss-security/), [oss-security RSS](https://www.openwall.com/lists/oss-security/rss)<br><br>**`Access / Cost`:** Free public mailing-list archive/RSS. | **`Relevance`:** Open-source vulnerability disclosure, CVE requests, embargo release coordination, & early technical discussion.<br><br>**`Notes & POIs`:** High-signal source for OSS CVE lifecycle events. Requires deduplication & careful parsing of threads. |
| 17 | **Full Disclosure / SecLists CVE-adjacent disclosure feed**<br><br>**`Link(s)`:** [Full Disclosure archive](https://seclists.org/fulldisclosure/), [Full Disclosure RSS](https://seclists.org/rss/fulldisclosure.rss)<br><br>**`Access / Cost`:** Free public mailing-list archive/RSS. | **`Relevance`:** Public vulnerability disclosures, exploit announcements, advisories, & researcher/vendor coordination context.<br><br>**`Notes & POIs`:** Quality varies. Treat as disclosure signal, not canonical source of affectedness or remediation truth. |
| 18 | **HackerOne disclosure platform & disclosed reports**<br><br>**`Link(s)`:** [HackerOne Hacktivity](https://hackerone.com/hacktivity), [HackerOne directory](https://hackerone.com/directory/programs)<br><br>**`Access / Cost`:** Free public disclosed-report browsing; APIs & program details may require account or platform access. | **`Relevance`:** Bug bounty/CVD pipeline source where vulnerabilities can be reported, triaged, disclosed, & sometimes mapped to CVEs.<br><br>**`Notes & POIs`:** Use for lifecycle/disclosure evidence; do not treat every report as CVE-backed or vendor-confirmed without validation. |
| 19 | **Bugcrowd disclosure platform, VRT & program pages**<br><br>**`Link(s)`:** [Bugcrowd vulnerability rating taxonomy](https://bugcrowd.com/vulnerability-rating-taxonomy/), [Bugcrowd programs](https://bugcrowd.com/programs)<br><br>**`Access / Cost`:** Free public taxonomy/program pages; submissions & details may require account or program access. | **`Relevance`:** Bug bounty/CVD triage context & severity normalization for researcher-submitted findings.<br><br>**`Notes & POIs`:** Useful for report-quality & severity context. Not a canonical CVE feed. |
| 20 | **OpenAI security & bug bounty program**<br><br>**`Link(s)`:** [OpenAI security & privacy](https://openai.com/security-and-privacy/), [OpenAI bug bounty announcement](https://openai.com/index/bug-bounty-program/), [OpenAI Bugcrowd program](https://bugcrowd.com/openai)<br><br>**`Access / Cost`:** Free public security page; Bugcrowd submission workflow; bounty scope/rules apply. | **`Relevance`:** AI platform/product vulnerability disclosure path for OpenAI products, APIs, model-serving systems, & AI security issues.<br><br>**`Notes & POIs`:** Add as AI-vendor security/disclosure coverage. Do not mark as confirmed CNA unless verified against the current CVE partner list. |
| 21 | **GitLab Advisory Database & community advisories**<br><br>**`Link(s)`:** [GitLab Advisory Database](https://advisories.gitlab.com/), [GitLab advisories-community repo](https://gitlab.com/gitlab-org/advisories-community)<br><br>**`Access / Cost`:** Free public web/repository access. | **`Relevance`:** Package ecosystem advisories, CVE/GHSA/package aliasing, & GitLab security intelligence data.<br><br>**`Notes & POIs`:** Add as secondary package advisory source. Validate ecosystem/version range semantics before automated use. |
| 22 | **European Union Vulnerability Database - EUVD**<br><br>**`Link(s)`:** [EUVD portal](https://euvd.enisa.europa.eu/), [ENISA](https://www.enisa.europa.eu/)<br><br>**`Access / Cost`:** Free public portal; API/feed endpoint should be verified manually if used for ingestion. | **`Relevance`:** European vulnerability database & CVE/EUVD cross-reference context for EU vulnerability governance.<br><br>**`Notes & POIs`:** Add as manual-review lifecycle source until official API/feed endpoints are documented & tested. |
| 23 | **Open Source Vulnerability Data - VulZoo dataset**<br><br>**`Link(s)`:** [VulZoo GitHub](https://github.com/NUS-Curiosity/VulZoo)<br><br>**`Access / Cost`:** Free public GitHub repository. | **`Relevance`:** Research dataset aggregating multiple vulnerability intelligence sources with scripts for synchronization, cleaning, relationship mining, & statistics.<br><br>**`Notes & POIs`:** Research/supporting dataset, not canonical operational feed. Useful for model development & source-coverage comparison. |
| 24 | **CVEfixes vulnerability-fix dataset**<br><br>**`Link(s)`:** [CVEfixes GitHub](https://github.com/secureIT-project/CVEfixes)<br><br>**`Access / Cost`:** Free public GitHub repository. | **`Relevance`:** Dataset linking CVEs with vulnerable code, fixing commits, repositories, & software metrics.<br><br>**`Notes & POIs`:** Useful for CVE lifecycle work around patch links, vulnerable-code evidence, & ML/research datasets. |

> 
> #### [*Back to **`Index`***](#index)
---

## 3. CVE metadata analytical framework, user-story resources, papers & community governance

### 3.1 CveToad CVE consumer/user-story resources

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **CveToad CVE Consumer User Story**<br><br>**`Link(s)`:** [CVE-Consumer_User-Story.md](https://github.com/keerthanap8898/CveToad/blob/main/CVE-Consumer_User-Story.md)<br><br>**`Access / Cost`:** Free public GitHub repo file | **`Relevance`:** Describes a CVE consumer’s operational pain points around malformed, inconsistent, incomplete, duplicated, or divergent vulnerability metadata.<br><br>**`Notes & POIs`:** Useful as local user-story evidence for field requirements, ingestion guardrails, validation rules, & normalization priorities. |
| 2 | **CVE Metadata Elements, Exploitability, & CWE Analytical Framework**<br><br>**`Link(s)`:** [CVE-user-story_Description.md](https://github.com/keerthanap8898/CveToad/blob/main/CVE-user-story_Description.md)<br><br>**`Access / Cost`:** Free public GitHub repo file | **`Relevance`:** Analytical framework for CVE metadata fields, exploitability metrics, CWE normalization, & CVSS/CWE correlation.<br><br>**`Notes & POIs`:** Good companion to the source inventory; use for implementation requirements & field mapping. |
| 3 | **CVE metadata framework image**<br><br>**`Link(s)`:** [CVE_Meta-data_Framework_Table.jpg](https://github.com/keerthanap8898/CveToad/blob/main/Resources/Images/CVE_Meta-data_Framework_Table.jpg)<br><br>**`Access / Cost`:** Free public GitHub repo file | **`Relevance`:** Visual/table artifact for CVE metadata framework.<br><br>**`Notes & POIs`:** Useful for documentation, diagrams, & explanatory material. |

### 3.2 CVE/CWE working groups, SIGs & community lists

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **CWE Working Groups & SIGs**<br><br>**`Link(s)`:** [cwe.mitre.org/community/working_groups.html](https://cwe.mitre.org/community/working_groups.html)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** CWE taxonomy governance & working-group context.<br><br>**`Notes & POIs`:** Useful for tracking taxonomy evolution, especially AI/ML weakness classification. |
| 2 | **CVE Program Working Groups**<br><br>**`Link(s)`:** [www.cve.org/programorganization/workinggroups](https://www.cve.org/programorganization/workinggroups)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Official CVE WG listing.<br><br>**`Notes & POIs`:** Governance/process source, not vulnerability data. |
| 3 | **CVE/CWE Programs groups.io main page**<br><br>**`Link(s)`:** [cve-cwe-programs.groups.io/g/main](https://cve-cwe-programs.groups.io/g/main)<br><br>**`Access / Cost`:** Public/registration may vary | **`Relevance`:** Main groups.io hub for CVE/CWE program communications.<br><br>**`Notes & POIs`:** Useful for WG discovery & program discussions. |
| 4 | **CVE/CWE Programs groups.io subgroups**<br><br>**`Link(s)`:** [cve-cwe-programs.groups.io/g/main/subgroups](https://cve-cwe-programs.groups.io/g/main/subgroups)<br><br>**`Access / Cost`:** Public/registration may vary | **`Relevance`:** Subgroup directory.<br><br>**`Notes & POIs`:** Useful for finding active CVE/CWE working groups. |
| 5 | **CVE Consumer Working Group**<br><br>**`Link(s)`:** [cve-cwe-programs.groups.io/g/ConsumerWG](https://cve-cwe-programs.groups.io/g/ConsumerWG)<br><br>**`Access / Cost`:** Public/registration may vary | **`Relevance`:** Consumer WG for CVE data consumers.<br><br>**`Notes & POIs`:** Directly relevant to CVE metadata quality, schema usability, & downstream ingestion pain points. |
| 6 | **CVE Automation Working Group repo**<br><br>**`Link(s)`:** [github.com/CVEProject/automation-working-group](https://github.com/CVEProject/automation-working-group)<br><br>**`Access / Cost`:** Free public GitHub repo | **`Relevance`:** Automation WG artifacts & implementation discussion.<br><br>**`Notes & POIs`:** Useful for automated CVE workflows & publication/ingestion changes. |
| 7 | **CVE Automation Working Group list**<br><br>**`Link(s)`:** [cve-cwe-programs.groups.io/g/AWG](https://cve-cwe-programs.groups.io/g/AWG)<br><br>**`Access / Cost`:** Public/registration may vary | **`Relevance`:** AWG mailing list.<br><br>**`Notes & POIs`:** Useful for automation-focused program discussion. |
| 8 | **OpenSSF Vulnerability Disclosures Working Group**<br><br>**`Link(s)`:** [github.com/ossf/wg-vulnerability-disclosures](https://github.com/ossf/wg-vulnerability-disclosures)<br><br>**`Access / Cost`:** Free public GitHub repo | **`Relevance`:** OpenSSF working group focused on improving vulnerability reporting, disclosure, & coordination across open source.<br><br>**`Notes & POIs`:** Useful for disclosure-process guidance, ecosystem governance, & vulnerability-handling best practices. |

### 3.3 Papers, conference programs, talks, training & community material

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **Accuracy Is Not Enough in Cybersecurity**<br><br>**`Link(s)`:** [github.com/keerthanap8898/Accuracy-is-Not-Enough-in-Cybersecurity](https://github.com/keerthanap8898/Accuracy-is-Not-Enough-in-Cybersecurity)<br><br>**`Access / Cost`:** Free public GitHub repo | **`Relevance`:** Blog/article backup focused on cybersecurity prediction, CVE/CVSS/EPSS/user-story context, & VulnCon references.<br><br>**`Notes & POIs`:** Local/reference material, not canonical upstream data. Deduplicate duplicate mentions into one row. |
| 2 | **FIRST VulnCon 2026 program**<br><br>**`Link(s)`:** [first.org/conference/vulncon26/program](https://www.first.org/conference/vulncon26/program)<br><br>**`Access / Cost`:** Free public conference page | **`Relevance`:** Vulnerability management, CVE, PSIRT, & disclosure conference program context.<br><br>**`Notes & POIs`:** Good for community/user-story background. |
| 3 | **FIRST papers - 2026**<br><br>**`Link(s)`:** [www.first.org/resources/papers/2026](https://www.first.org/resources/papers/2026)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** FIRST papers & security response material.<br><br>**`Notes & POIs`:** Useful for research & practitioner references. |
| 4 | **FIRST YouTube channel**<br><br>**`Link(s)`:** [youtube.com/c/FIRSTdotorg](https://www.youtube.com/c/FIRSTdotorg)<br><br>**`Access / Cost`:** Free public video channel | **`Relevance`:** Official FIRST conference/training/media material.<br><br>**`Notes & POIs`:** Training/reference source, not vulnerability feed. |
| 5 | **CISA YouTube channel**<br><br>**`Link(s)`:** [youtube.com/@CISAgov](https://www.youtube.com/@CISAgov)<br><br>**`Access / Cost`:** Free public video channel | **`Relevance`:** Official CISA videos, briefings, guidance, & training material.<br><br>**`Notes & POIs`:** Mark as media/reference source. |
| 6 | **WhiteSec Cyber Security YouTube channel**<br><br>**`Link(s)`:** [youtube.com/@whiteseccybersecurity](https://www.youtube.com/@whiteseccybersecurity)<br><br>**`Access / Cost`:** Free public video channel | **`Relevance`:** Community cybersecurity training/media material.<br><br>**`Notes & POIs`:** Non-authoritative; validate claims against primary sources. |
| 7 | **Breachtrace VulnKeeper docs**<br><br>**`Link(s)`:** [breachtrace.gitbook.io/vulnkeeper](https://breachtrace.gitbook.io/vulnkeeper)<br><br>**`Access / Cost`:** Public docs; manually revalidate | **`Relevance`:** Tool/project documentation for vulnerability tracking workflows.<br><br>**`Notes & POIs`:** Community/tooling source; not canonical vulnerability data. |
| 8 | **LangGuard SCOPE MCP**<br><br>**`Link(s)`:** [scope-mcp.langguard.ai](https://scope-mcp.langguard.ai)<br><br>**`Access / Cost`:** Public web tool/service; terms may apply | **`Relevance`:** AI/agent compliance & risk-evaluation resource.<br><br>**`Notes & POIs`:** Useful for agent/tool-governance notes in AI security sections. |
| 9 | **CVE-MCP**<br><br>**`Link(s)`:** [github.com/jgamblin/CVE-MCP](https://github.com/jgamblin/CVE-MCP)<br><br>**`Access / Cost`:** Free public GitHub repo | **`Relevance`:** MCP server/tooling for CVE data via the CVE.org API.<br><br>**`Notes & POIs`:** Useful as experimental CVE-query tooling, not as a canonical CVE source. Validate API behavior against official CVE Services docs. |

> 
> #### [*Back to **`Index`***](#index)
> 
> ---

## B. CVE Enrichment, Exploitability, Prioritization & Data Model

## 4. Exploitation, prioritization, severity & risk scoring

### 4.1 Known exploited vulnerability sources

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **CISA KEV catalog - web**<br><br>**`Link(s)`:** [www.cisa.gov/known-exploited-vulnerabilities-catalog](https://www.cisa.gov/known-exploited-vulnerabilities-catalog)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Authoritative catalog of known exploited vulnerabilities. Critical for prioritization & remediation urgency.<br><br>**`Notes & POIs`:** KEV is a strong exploitation signal but not a complete list of all exploited vulnerabilities. |
| 2 | **CISA KEV print view**<br><br>**`Link(s)`:** [www.cisa.gov/known-exploited-vulnerabilities-catalog-print](https://www.cisa.gov/known-exploited-vulnerabilities-catalog-print)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Human-readable print-oriented KEV view.<br><br>**`Notes & POIs`:** Useful for documentation & manual review; use JSON for automation. |
| 3 | **CISA KEV JSON feed**<br><br>**`Link(s)`:** [www.cisa.gov/sites/default/files/feeds/known_exploited_vulnerabilities.json](https://www.cisa.gov/sites/default/files/feeds/known_exploited_vulnerabilities.json)<br><br>**`Access / Cost`:** Free public feed | **`Relevance`:** Machine- readable KEV feed.<br><br>**`Notes & POIs`:** Primary automation source for KEV ingestion. Monitor `dateAdded` & due dates. |
| 4 | **CISA KEV JSON schema**<br><br>**`Link(s)`:** [www.cisa.gov/sites/default/files/feeds/known_exploited_vulnerabilities_schema.json](https://www.cisa.gov/sites/default/files/feeds/known_exploited_vulnerabilities_schema.json)<br><br>**`Access / Cost`:** Free public feed | **`Relevance`:** Schema for KEV JSON validation.<br><br>**`Notes & POIs`:** Use for ingestion validation. Schema changes should trigger parser review. |
| 5 | **CISA KEV GitHub mirror**<br><br>**`Link(s)`:** [github.com/cisagov/kev-data](https://github.com/cisagov/kev-data)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** GitHub mirror of KEV data.<br><br>**`Notes & POIs`:** Useful for Git-based diffing & historical tracking. Treat CISA official feed as source of truth. |
| 6 | **VulnCheck KEV**<br><br>**`Link(s)`:** [vulncheck.com/kev](https://vulncheck.com/kev)<br><br>**`Access / Cost`:** Commercial; limited public info may exist | **`Relevance`:** Expanded KEV-like exploitation intelligence.<br><br>**`Notes & POIs`:** Not identical to CISA KEV. Validate definitions, coverage, licensing, & freshness. |
| 7 | **Shadowserver reports**<br><br>**`Link(s)`:** [www.shadowserver.org](https://www.shadowserver.org/)<br><br>**`Access / Cost`:** Free for eligible organizations; access/registration may be required | **`Relevance`:** Internet-scale exploitation & exposure observations.<br><br>**`Notes & POIs`:** Useful for exposure/scan telemetry. Data may be aggregated & require access setup. |
| 8 | **GreyNoise Visualizer**<br><br>**`Link(s)`:** [viz.greynoise.io](https://viz.greynoise.io/)<br><br>**`Access / Cost`:** Free tier / paid plans | **`Relevance`:** Internet scanning/exploitation noise & actor context.<br><br>**`Notes & POIs`:** Helps distinguish benign scanning, mass exploitation, & opportunistic activity. |
| 9 | **GreyNoise API docs**<br><br>**`Link(s)`:** [docs.greynoise.io](https://docs.greynoise.io/)<br><br>**`Access / Cost`:** Free tier / paid plans; API key required | **`Relevance`:** API for IP-based exploitation telemetry enrichment.<br><br>**`Notes & POIs`:** API terms, quotas, & plan level can affect automation. |

### 4.2 Exploit prediction & scoring

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **FIRST EPSS overview**<br><br>**`Link(s)`:** [www.first.org/epss](https://www.first.org/epss/)<br><br>**`Access / Cost`:** Free public / open data | **`Relevance`:** Exploit Prediction Scoring System. Provides probability-style exploit-likelihood signals.<br><br>**`Notes & POIs`:** EPSS predicts exploitation probability, not impact. Use with CVSS, KEV, exposure, & asset criticality. |
| 2 | **FIRST EPSS API**<br><br>**`Link(s)`:** [www.first.org/epss/api](https://www.first.org/epss/api)<br><br>**`Access / Cost`:** Free public API | **`Relevance`:** API endpoint for EPSS scores.<br><br>**`Notes & POIs`:** Useful for daily enrichment. Store score date because EPSS changes over time. |
| 3 | **FIRST EPSS data & CSV downloads**<br><br>**`Link(s)`:** [www.first.org/epss/data_stats](https://www.first.org/epss/data_stats)<br><br>**`Access / Cost`:** Free public data downloads | **`Relevance`:** Current & historical EPSS CSV data reference.<br><br>**`Notes & POIs`:** Historical scores are useful for model training & retrospective analysis. |
| 4 | **Historical EPSS scores GitHub**<br><br>**`Link(s)`:** [github.com/empiricalsec/epss_scores](https://github.com/empiricalsec/epss_scores)<br><br>**`Access / Cost`:** Free public GitHub repo | **`Relevance`:** Daily historical EPSS snapshots.<br><br>**`Notes & POIs`:** Useful for longitudinal training labels. Validate against FIRST releases. |
| 5 | **FIRST CVSS**<br><br>**`Link(s)`:** [www.first.org/cvss](https://www.first.org/cvss/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Official CVSS specification home.<br><br>**`Notes & POIs`:** CVSS severity must not be treated as exploit likelihood. |
| 6 | **FIRST CVSS v4.0**<br><br>**`Link(s)`:** [www.first.org/cvss/v4.0/specification-document](https://www.first.org/cvss/v4.0/specification-document)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** CVSS v4.0 specification.<br><br>**`Notes & POIs`:** Newer scoring semantics may not be universally populated across vulnerability records yet. |
| 7 | **FIRST CVSS v3.1**<br><br>**`Link(s)`:** [www.first.org/cvss/v3.1/specification-document](https://www.first.org/cvss/v3.1/specification-document)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** CVSS v3.1 specification.<br><br>**`Notes & POIs`:** Still widely used across CVE/NVD/vendor data. |
| 8 | **NVD CVSS resources**<br><br>**`Link(s)`:** [nvd.nist.gov/vuln-metrics/cvss](https://nvd.nist.gov/vuln-metrics/cvss)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** CVSS calculators & vector references.<br><br>**`Notes & POIs`:** Useful for parsing & validating NVD scoring data. |

### 4.3 Decision-support frameworks

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **CISA SSVC**<br><br>**`Link(s)`:** [www.cisa.gov/stakeholder-specific-vulnerability-categorization-ssvc](https://www.cisa.gov/stakeholder-specific-vulnerability-categorization-ssvc)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Stakeholder-Specific Vulnerability Categorization for vulnerability response decisions.<br><br>**`Notes & POIs`:** Useful for decision automation beyond raw severity. Depends on environmental & mission context. |
| 2 | **CERT/CC SSVC project**<br><br>**`Link(s)`:** [github.com/CERTCC/SSVC](https://github.com/CERTCC/SSVC)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** SSVC model artifacts, examples, & discussions.<br><br>**`Notes & POIs`:** Useful for implementing SSVC decision trees & decision points. |
| 3 | **CISA Vulnrichment**<br><br>**`Link(s)`:** [github.com/cisagov/vulnrichment](https://github.com/cisagov/vulnrichment)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** CISA ADP enrichment & SSVC decision points.<br><br>**`Notes & POIs`:** Coverage is not universal. Preserve missing/null state distinctly from “low risk.” |
| 4 | **CISA Binding Operational Directive 22-01**<br><br>**`Link(s)`:** [www.cisa.gov/news-events/directives/bod-22-01-reducing- significant-risk-known-exploited-vulnerabilities](https://www.cisa.gov/news-events/directives/bod-22-01-reducing-significant-risk-known-exploited-vulnerabilities)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Operational requirement context for KEV remediation.<br><br>**`Notes & POIs`:** Primarily binding for U.S. federal civilian agencies but useful as industry prioritization guidance. |
| 5 | **CISA Cybersecurity Advisories**<br><br>**`Link(s)`:** [www.cisa.gov/cybersecurity-advisories](https://www.cisa.gov/cybersecurity-advisories)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Broader CISA advisory feed.<br><br>**`Notes & POIs`:** Useful for emergent campaigns, vendor alerts, & remediation guidance. |
| 6 | **CISA Alerts**<br><br>**`Link(s)`:** [www.cisa.gov/news-events/cybersecurity-advisories](https://www.cisa.gov/news-events/cybersecurity-advisories)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** CISA alert/advisory listing.<br><br>**`Notes & POIs`:** May overlap with other CISA pages. Deduplicate by advisory ID/date. |

### 4.4 Public exploit / proof-of-concept / weaponization signals

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **Exploit-DB**<br><br>**`Link(s)`:** [www.exploit-db.com](https://www.exploit-db.com/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Public exploit archive. Strong signal for PoC availability.<br><br>**`Notes & POIs`:** Public PoC does not always mean reliable weaponization; verify exploit quality & target version. |
| 2 | **SearchSploit**<br><br>**`Link(s)`:** [www.exploit-db.com/searchsploit](https://www.exploit-db.com/searchsploit)<br><br>**`Access / Cost`:** Free / open-source tool | **`Relevance`:** CLI interface for Exploit-DB.<br><br>**`Notes & POIs`:** Useful for local workflows & offline search. |
| 3 | **Exploit-DB GitLab mirror**<br><br>**`Link(s)`:** [gitlab.com/exploit-database/exploitdb](https://gitlab.com/exploit-database/exploitdb)<br><br>**`Access / Cost`:** Free public GitLab repo | **`Relevance`:** Git mirror of Exploit-DB content.<br><br>**`Notes & POIs`:** Useful for local indexing & diffing. |
| 4 | **Metasploit Framework**<br><br>**`Link(s)`:** [github.com/rapid7/metasploit-framework](https://github.com/rapid7/metasploit-framework)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo; commercial Rapid7 products separate | **`Relevance`:** Exploit framework containing modules, payloads, & auxiliary checks.<br><br>**`Notes & POIs`:** A Metasploit module is a stronger operationalization signal than a bare PoC. |
| 5 | **Metasploit exploit modules**<br><br>**`Link(s)`:** [github.com/rapid7/metasploit-framework/tree/master/modules/exploits](https://github.com/rapid7/metasploit-framework/tree/master/modules/exploits)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** Practical signal that a vulnerability has weaponized exploit implementation.<br><br>**`Notes & POIs`:** Module maturity, reliability, & target coverage vary. |
| 6 | **Packet Storm Security exploits**<br><br>**`Link(s)`:** [packetstormsecurity.com/files/tags/exploit](https://packetstormsecurity.com/files/tags/exploit/)<br><br>**`Access / Cost`:** Free public; may bot-block automated fetchers | **`Relevance`:** Public exploit & advisory archive.<br><br>**`Notes & POIs`:** Quality & metadata normalization vary; cross-reference CVE IDs. Mark bot-blocked fetches as restricted/manual-review. |
| 7 | **VulnCheck Exploit Database Query Console**<br><br>**`Link(s)`:** [console.vulncheck.com](https://console.vulncheck.com/)<br><br>**`Access / Cost`:** Auth-gated / commercial; limited public access may exist | **`Relevance`:** Exploit intelligence query console.<br><br>**`Notes & POIs`:** Treat as restricted/manual-review in CI. Validate licensing & provenance before production use. |
| 8 | **Vulners Exploit Catalog**<br><br>**`Link(s)`:** [vulners.com/search](https://vulners.com/search)<br><br>**`Access / Cost`:** Free web search; API/advanced features may require paid plan | **`Relevance`:** Broad exploit/advisory search catalog.<br><br>**`Notes & POIs`:** Secondary enrichment. Do not treat as canonical without upstream provenance. |
| 9 | **Project Zero blog**<br><br>**`Link(s)`:** [projectzero.google](https://projectzero.google/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** High-quality root-cause & exploitation writeups.<br><br>**`Notes & POIs`:** Excellent for model features around exploitability primitives & bug classes. |
| 10 | **Project Zero issue tracker - current**<br><br>**`Link(s)`:** [project-zero.issues.chromium.org/issues](https://project-zero.issues.chromium.org/issues)<br><br>**`Access / Cost`:** Free public; some issue details may be restricted before disclosure | **`Relevance`:** Current Project Zero issue tracker.<br><br>**`Notes & POIs`:** Good for disclosure timelines & technical details. |
| 11 | **Project Zero issue tracker - old/historical**<br><br>**`Link(s)`:** [bugs.chromium.org/p/project-zero/issues/list](https://bugs.chromium.org/p/project-zero/issues/list)<br><br>**`Access / Cost`:** Free public historical access where still available | **`Relevance`:** Historical Project Zero issue tracker link.<br><br>**`Notes & POIs`:** Keep for old references; prefer current `/issues` tracker when available. |
| 12 | **CERT/CC Vulnerability Notes Database**<br><br>**`Link(s)`:** [www.kb.cert.org/vuls](https://www.kb.cert.org/vuls/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Coordinated disclosure context, affected vendors, technical notes, & remediation.<br><br>**`Notes & POIs`:** Often useful when multiple vendors/products are affected. |
| 13 | **Rapid7 AttackerKB**<br><br>**`Link(s)`:** [attackerkb.com](https://attackerkb.com/)<br><br>**`Access / Cost`:** Free public content; some Rapid7 ecosystem features may be commercial | **`Relevance`:** Exploitability & attacker-value context.<br><br>**`Notes & POIs`:** Community/commercial signals should be weighted with provenance & recency. |
| 14 | **Nuclei templates**<br><br>**`Link(s)`:** [github.com/projectdiscovery/nuclei-templates](https://github.com/projectdiscovery/nuclei-templates)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** Exposed-condition detection templates. Useful for scanning internet-facing assets.<br><br>**`Notes & POIs`:** Template presence is a practical detection signal, not proof of vulnerability unless executed correctly. |
| 15 | **ProjectDiscovery Nuclei**<br><br>**`Link(s)`:** [github.com/projectdiscovery/nuclei](https://github.com/projectdiscovery/nuclei)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo; commercial ProjectDiscovery offerings separate | **`Relevance`:** Template-based vulnerability & exposure scanner.<br><br>**`Notes & POIs`:** Detection accuracy depends on template quality, target context, & scanner configuration. |
| 16 | **Horizon3.ai research**<br><br>**`Link(s)`:** [horizon3.ai/attack-research](https://horizon3.ai/attack-research/)<br><br>**`Access / Cost`:** Free public research; commercial products separate | **`Relevance`:** PoC & attack-path writeups.<br><br>**`Notes & POIs`:** Useful for exploitability context & reproduction details. |
| 17 | **watchTowr Labs**<br><br>**`Link(s)`:** [labs.watchtowr.com](https://labs.watchtowr.com/)<br><br>**`Access / Cost`:** Free public research; commercial services separate | **`Relevance`:** Vulnerability research & exploitation details.<br><br>**`Notes & POIs`:** Research source; verify exact affected versions & mitigations. |
| 18 | **Assetnote research**<br><br>**`Link(s)`:** [www.assetnote.io/resources/research](https://www.assetnote.io/resources/research)<br><br>**`Access / Cost`:** Free public research; commercial services separate | **`Relevance`:** Exploit research & vulnerability detection signatures.<br><br>**`Notes & POIs`:** Useful for detection engineering & exposed attack surface context. |
| 19 | **Breachtrace VulnKeeper docs**<br><br>**`Link(s)`:** [breachtrace.gitbook.io/vulnkeeper](https://breachtrace.gitbook.io/vulnkeeper)<br><br>**`Access / Cost`:** Public docs; manually revalidate | **`Relevance`:** Community/tooling documentation for vulnerability tracking.<br><br>**`Notes & POIs`:** Treat as non-canonical & keep in manual-review allowlist until verified. |

> 
> #### [*Back to **`Index`***](#index)
---

## 5. Practical priority hierarchy for ingestion

### 5.1 Tier 0 - identifiers & inventory

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **SBOM**<br><br>**`Link(s)`:** [cyclonedx.org/specification/overview](https://cyclonedx.org/specification/overview/), [spdx.dev/specifications](https://spdx.dev/specifications/)<br><br>**`Access / Cost`:** Free / open standards | **`Relevance`:** Inventory foundation for matching components to vulnerabilities.<br><br>**`Notes & POIs`:** Without accurate inventory, vulnerability matching is incomplete or noisy. |
| 2 | **Package identity**<br><br>**`Link(s)`:** [csrc.nist.gov/projects/software-identification-swid](https://csrc.nist.gov/projects/software-identification-swid), [github.com/package-url/purl-spec](https://github.com/package-url/purl-spec), [nvd.nist.gov/products/cpe](https://nvd.nist.gov/products/cpe)<br><br>**`Access / Cost`:** Free public / open standards | **`Relevance`:** Component identity across package, product, & installed software domains.<br><br>**`Notes & POIs`:** Use PURL for packages, CPE for products/platforms, SWID for installed software identity. |
| 3 | **Asset exposure**<br><br>**`Link(s)`:** [search.censys.io](https://search.censys.io/), [www.shodan.io](https://www.shodan.io/)<br><br>**`Access / Cost`:** Free tiers / paid plans | **`Relevance`:** Determines whether vulnerable assets are externally reachable.<br><br>**`Notes & POIs`:** Combine with internal CMDB, cloud inventory, & authenticated scans. |
| 4 | **Artifact provenance**<br><br>**`Link(s)`:** [in-toto.io](https://in-toto.io/), [slsa.dev](https://slsa.dev/), [www.sigstore.dev](https://www.sigstore.dev/)<br><br>**`Access / Cost`:** Free / open-source / open standards | **`Relevance`:** Validates build-chain integrity & artifact authenticity.<br><br>**`Notes & POIs`:** Helps distinguish vulnerable dependency risk from supply-chain tampering risk. |

### 5.2 Tier 1 - canonical vulnerability records

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **CVE List v5**<br><br>**`Link(s)`:** [github.com/CVEProject/cvelistV5](https://github.com/CVEProject/cvelistV5)<br><br>**`Access / Cost`:** Free public GitHub repo | **`Relevance`:** Canonical CVE record mirror.<br><br>**`Notes & POIs`:** Core identity source. |
| 2 | **CVE schema**<br><br>**`Link(s)`:** [github.com/CVEProject/cve-schema](https://github.com/CVEProject/cve-schema)<br><br>**`Access / Cost`:** Free public GitHub repo | **`Relevance`:** Schema validation for CVE records.<br><br>**`Notes & POIs`:** Use for parser correctness. |
| 3 | **CVE Services API**<br><br>**`Link(s)`:** [cveawg.mitre.org/api-docs](https://cveawg.mitre.org/api-docs/)<br><br>**`Access / Cost`:** Free public docs; CNA functions may require role/account | **`Relevance`:** Direct programmatic CVE lookup.<br><br>**`Notes & POIs`:** Useful for targeted CVE access. |
| 4 | **NVD CVE API**<br><br>**`Link(s)`:** [nvd.nist.gov/developers/vulnerabilities](https://nvd.nist.gov/developers/vulnerabilities)<br><br>**`Access / Cost`:** Free public; optional free API key for higher rate limits | **`Relevance`:** CVSS/CPE/CWE/reference enrichment.<br><br>**`Notes & POIs`:** Core enrichment source. |
| 5 | **NVD CPE API**<br><br>**`Link(s)`:** [nvd.nist.gov/developers/products](https://nvd.nist.gov/developers/products)<br><br>**`Access / Cost`:** Free public; optional free API key for higher rate limits | **`Relevance`:** CPE dictionary & product matching.<br><br>**`Notes & POIs`:** Important for product-level mapping. |
| 6 | **NVD data feeds**<br><br>**`Link(s)`:** [nvd.nist.gov/vuln/data-feeds](https://nvd.nist.gov/vuln/data-feeds)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Bulk NVD feed access.<br><br>**`Notes & POIs`:** Useful for bootstrapping. |
| 7 | **CISA Vulnrichment**<br><br>**`Link(s)`:** [github.com/cisagov/vulnrichment](https://github.com/cisagov/vulnrichment)<br><br>**`Access / Cost`:** Free public GitHub repo | **`Relevance`:** CISA ADP enrichment & SSVC data.<br><br>**`Notes & POIs`:** Prioritization enrichment. |

### 5.3 Tier 2 - package/ecosystem vulnerability records

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **OSV full database**<br><br>**`Link(s)`:** [google.github.io/osv.dev/data/#full-database-download](https://google.github.io/osv.dev/data/#full-database-download)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Local mirror of OSS vulnerability records.<br><br>**`Notes & POIs`:** Best for high-volume package matching. |
| 2 | **OSV API**<br><br>**`Link(s)`:** [google.github.io/osv.dev/post-v1-query](https://google.github.io/osv.dev/post-v1-query/)<br><br>**`Access / Cost`:** Free public API | **`Relevance`:** Online vulnerability lookup by package/version/commit/ID.<br><br>**`Notes & POIs`:** Good for targeted lookups. |
| 3 | **GitHub Advisory Database**<br><br>**`Link(s)`:** [github.com/advisories](https://github.com/advisories)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** GHSA/CVE/malware advisory records.<br><br>**`Notes & POIs`:** Preserve aliases. |
| 4 | **GitHub Advisory Database repo**<br><br>**`Link(s)`:** [github.com/github/advisory-database](https://github.com/github/advisory-database)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** Raw advisory data for local ingestion.<br><br>**`Notes & POIs`:** Useful for mirroring. |
| 5 | **Go vuln DB**<br><br>**`Link(s)`:** [vuln.go.dev](https://vuln.go.dev/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Official Go vulnerability database.<br><br>**`Notes & POIs`:** Go- specific affectedness. |
| 6 | **RustSec**<br><br>**`Link(s)`:** [rustsec.org](https://rustsec.org/)<br><br>**`Access / Cost`:** Free public / open-source ecosystem | **`Relevance`:** Rust advisory ecosystem.<br><br>**`Notes & POIs`:** Rust crate-specific advisories. |
| 7 | **PyPA advisory DB**<br><br>**`Link(s)`:** [github.com/pypa/advisory-database](https://github.com/pypa/advisory-database)<br><br>**`Access / Cost`:** Free public GitHub repo | **`Relevance`:** Python advisory source.<br><br>**`Notes & POIs`:** Python/PyPI coverage. |
| 8 | **FriendsOfPHP**<br><br>**`Link(s)`:** [github.com/FriendsOfPHP/security-advisories](https://github.com/FriendsOfPHP/security-advisories)<br><br>**`Access / Cost`:** Free public GitHub repo | **`Relevance`:** PHP Composer advisories.<br><br>**`Notes & POIs`:** Composer-specific. |
| 9 | **RubySec**<br><br>**`Link(s)`:** [github.com/rubysec/ruby-advisory-db](https://github.com/rubysec/ruby-advisory-db)<br><br>**`Access / Cost`:** Free public GitHub repo | **`Relevance`:** RubyGems advisories.<br><br>**`Notes & POIs`:** Ruby ecosystem. |
| 10 | **OSS Index**<br><br>**`Link(s)`:** [ossindex.sonatype.org](https://ossindex.sonatype.org/)<br><br>**`Access / Cost`:** Free tier / API terms; commercial Sonatype products separate | **`Relevance`:** Package vulnerability intelligence.<br><br>**`Notes & POIs`:** Secondary enrichment. |
| 11 | **Packagist API**<br><br>**`Link(s)`:** [packagist.org/apidoc#list-security-advisories](https://packagist.org/apidoc#list-security-advisories)<br><br>**`Access / Cost`:** Free public API docs / public API | **`Relevance`:** Composer advisory API.<br><br>**`Notes & POIs`:** Direct PHP ecosystem source. |

### 5.4 Tier 3 - affectedness, distro & vendor truth

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **Red Hat Security Data**<br><br>**`Link(s)`:** [access.redhat.com/security/data](https://access.redhat.com/security/data)<br><br>**`Access / Cost`:** Free public data; support content may require subscription | **`Relevance`:** RHEL affectedness, CSAF/VEX, OSV, OVAL.<br><br>**`Notes & POIs`:** Backport-aware. |
| 2 | **Debian Security Tracker**<br><br>**`Link(s)`:** [security-tracker.debian.org](https://security-tracker.debian.org/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Debian package affectedness.<br><br>**`Notes & POIs`:** Backport-aware. |
| 3 | **Ubuntu OVAL / OSV / OpenVEX**<br><br>**`Link(s)`:** [github.com/canonical/ubuntu-security-notices](https://github.com/canonical/ubuntu-security-notices), [ubuntu.com/security/oval](https://ubuntu.com/security/oval), [ubuntu.com/security/vex](https://ubuntu.com/security/vex)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Ubuntu package affectedness & VEX status.<br><br>**`Notes & POIs`:** Use release-specific data. |
| 4 | **Alpine SecDB**<br><br>**`Link(s)`:** [secdb.alpinelinux.org](https://secdb.alpinelinux.org/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Alpine package vulnerability data.<br><br>**`Notes & POIs`:** Container-critical. |
| 5 | **SUSE CSAF / OVAL**<br><br>**`Link(s)`:** [www.suse.com/support/security/csaf](https://www.suse.com/support/security/csaf/), [www.suse.com/support/security/oval](https://www.suse.com/support/security/oval/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** SUSE vendor affectedness & scanner data.<br><br>**`Notes & POIs`:** Use machine-readable formats where possible. |
| 6 | **Oracle Linux OVAL / errata**<br><br>**`Link(s)`:** [linux.oracle.com/errata](https://linux.oracle.com/errata/), [linux.oracle.com/security/oval](https://linux.oracle.com/security/oval/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Oracle Linux patch & OVAL data.<br><br>**`Notes & POIs`:** Oracle Linux-specific. |
| 7 | **Amazon Linux ALAS**<br><br>**`Link(s)`:** [alas.aws.amazon.com](https://alas.aws.amazon.com/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Amazon Linux advisories.<br><br>**`Notes & POIs`:** Separate AL2 & AL2023. |
| 8 | **AlmaLinux / Rocky / Fedora / Arch / Gentoo**<br><br>**`Link(s)`:** [bodhi.fedoraproject.org/updates/?type=security](https://bodhi.fedoraproject.org/updates/?type=security), [errata.almalinux.org](https://errata.almalinux.org/), [errata.build.resf.org](https://errata.build.resf.org/), [security.archlinux.org](https://security.archlinux.org/), [security.gentoo.org/glsa](https://security.gentoo.org/glsa/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Additional Linux distribution affectedness sources.<br><br>**`Notes & POIs`:** Distro semantics vary substantially. |
| 9 | **Wolfi / Chainguard**<br><br>**`Link(s)`:** [github.com/wolfi-dev/advisories](https://github.com/wolfi-dev/advisories), [packages.cgr.dev/chainguard/security.json](https://packages.cgr.dev/chainguard/security.json), [packages.wolfi.dev/os/security.json](https://packages.wolfi.dev/os/security.json)<br><br>**`Access / Cost`:** Wolfi free public; Chainguard feed may relate to commercial product scope | **`Relevance`:** Container-first package vulnerability feeds.<br><br>**`Notes & POIs`:** Useful for minimal images. |
| 10 | **Vendor advisories**<br><br>**`Link(s)`:** [helpx.adobe.com/security.html](https://helpx.adobe.com/security.html), [msrc.microsoft.com/update-guide](https://msrc.microsoft.com/update-guide), [security.paloaltonetworks.com](https://security.paloaltonetworks.com/), [sec.cloudapps.cisco.com/security/center/publicationListing.x](https://sec.cloudapps.cisco.com/security/center/publicationListing.x), [support.apple.com/en-us/100100](https://support.apple.com/en-us/100100), [support.broadcom.com/web/ecx/security-advisory](https://support.broadcom.com/web/ecx/security-advisory), [support.citrix.com/securitybulletins](https://support.citrix.com/securitybulletins), [support.sap.com/en/my-support/knowledge-base/security-notes- news.html](https://support.sap.com/en/my-support/knowledge-base/security-notes-news.html), [www.atlassian.com/trust/security/advisories](https://www.atlassian.com/trust/security/advisories), [www.fortiguard.com/psirt](https://www.fortiguard.com/psirt), [forums.ivanti.com/s/security-advisory](https://forums.ivanti.com/s/security-advisory), [www.oracle.com/security-alerts](https://www.oracle.com/security-alerts/)<br><br>**`Access / Cost`:** Mostly free public advisories; some vendors require support accounts/subscriptions for full details or downloads | **`Relevance`:** Vendor truth for affected products, fixed versions, mitigations, & exploitation notes.<br><br>**`Notes & POIs`:** Often most authoritative for product affectedness. Access, formatting, & update latency vary. |

### 5.5 Tier 4 - severity & prioritization

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **CVSS v3.1/v4.0**<br><br>**`Link(s)`:** [www.first.org/cvss/v3.1/specification-document](https://www.first.org/cvss/v3.1/specification-document), [www.first.org/cvss/v4.0/specification-document](https://www.first.org/cvss/v4.0/specification-document)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Standard severity scoring.<br><br>**`Notes & POIs`:** Severity is not exploit likelihood. |
| 2 | **EPSS**<br><br>**`Link(s)`:** [www.first.org/epss](https://www.first.org/epss/)<br><br>**`Access / Cost`:** Free public data/API | **`Relevance`:** Exploit likelihood prediction.<br><br>**`Notes & POIs`:** Temporal; store score date. |
| 3 | **KEV**<br><br>**`Link(s)`:** [www.cisa.gov/sites/default/files/feeds/known_exploited_vulnerabilities.json](https://www.cisa.gov/sites/default/files/feeds/known_exploited_vulnerabilities.json)<br><br>**`Access / Cost`:** Free public feed | **`Relevance`:** Known exploited vulnerability signal.<br><br>**`Notes & POIs`:** Strong but incomplete exploited-in-the-wild signal. |
| 4 | **SSVC**<br><br>**`Link(s)`:** [github.com/CERTCC/SSVC](https://github.com/CERTCC/SSVC), [www.cisa.gov/stakeholder-specific- vulnerability-categorization-ssvc](https://www.cisa.gov/stakeholder-specific-vulnerability-categorization-ssvc)<br><br>**`Access / Cost`:** Free public / open-source | **`Relevance`:** Decision support for remediation urgency.<br><br>**`Notes & POIs`:** Requires environmental/mission context. |
| 5 | **CISA Vulnrichment**<br><br>**`Link(s)`:** [github.com/cisagov/vulnrichment](https://github.com/cisagov/vulnrichment)<br><br>**`Access / Cost`:** Free public GitHub repo | **`Relevance`:** SSVC & enrichment data.<br><br>**`Notes & POIs`:** Coverage varies. |
| 6 | **Vendor exploited-in-the-wild flags**<br><br>**`Link(s)`:** [msrc.microsoft.com/update-guide](https://msrc.microsoft.com/update-guide), [support.apple.com/en-us/100100](https://support.apple.com/en-us/100100), [www.oracle.com/security- alerts](https://www.oracle.com/security-alerts/)<br><br>**`Access / Cost`:** Free public, though product support details may vary | **`Relevance`:** Vendor- provided exploitation status.<br><br>**`Notes & POIs`:** Often product-specific & time-sensitive. |
| 7 | **Patch availability & fixed-version feeds**<br><br>**`Link(s)`:** [access.redhat.com/security/data](https://access.redhat.com/security/data), [github.com/canonical/ubuntu-security-notices](https://github.com/canonical/ubuntu-security-notices), [security-tracker.debian.org/tracker/data/json](https://security-tracker.debian.org/tracker/data/json)<br><br>**`Access / Cost`:** Free public data; some vendor support may require subscription | **`Relevance`:** Determines whether remediation exists.<br><br>**`Notes & POIs`:** Patch availability varies by distro/release/product. |
| 8 | **Environmental context**<br><br>**`Link(s)`:** [docs.greynoise.io](https://docs.greynoise.io/), [search.censys.io](https://search.censys.io/), [www.shodan.io](https://www.shodan.io/)<br><br>**`Access / Cost`:** Free tiers / paid plans | **`Relevance`:** Internet exposure, asset criticality, privilege boundary, & data sensitivity determine real impact.<br><br>**`Notes & POIs`:** Must be joined with internal asset inventory & controls. |

### 5.6 Tier 5 - exploitability & weaponization

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **Exploit-DB**<br><br>**`Link(s)`:** [www.exploit-db.com](https://www.exploit-db.com/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Public exploit availability.<br><br>**`Notes & POIs`:** Verify target versions & exploit reliability. |
| 2 | **Metasploit modules**<br><br>**`Link(s)`:** [github.com/rapid7/metasploit-framework/tree/master/modules/exploits](https://github.com/rapid7/metasploit-framework/tree/master/modules/exploits)<br><br>**`Access / Cost`:** Free / open-source | **`Relevance`:** Weaponized exploit modules.<br><br>**`Notes & POIs`:** Strong operationalization signal. |
| 3 | **Packet Storm**<br><br>**`Link(s)`:** [packetstormsecurity.com/files/tags/exploit](https://packetstormsecurity.com/files/tags/exploit/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Exploit archive.<br><br>**`Notes & POIs`:** Metadata quality varies. |
| 4 | **Project Zero**<br><br>**`Link(s)`:** [projectzero.google](https://projectzero.google/), [project- zero.issues.chromium.org](https://project-zero.issues.chromium.org/issues)<br><br>**`Access / Cost`:** Free public; some issues may be restricted pre-disclosure | **`Relevance`:** Root-cause & exploitability research.<br><br>**`Notes & POIs`:** High-quality technical details. |
| 5 | **CERT/CC VU notes**<br><br>**`Link(s)`:** [www.kb.cert.org/vuls](https://www.kb.cert.org/vuls/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Coordinated disclosure & affected vendor context.<br><br>**`Notes & POIs`:** Useful for ecosystem-wide vulns. |
| 6 | **Rapid7 AttackerKB**<br><br>**`Link(s)`:** [attackerkb.com](https://attackerkb.com/)<br><br>**`Access / Cost`:** Free public content; commercial Rapid7 offerings separate | **`Relevance`:** Attacker value & exploitability context.<br><br>**`Notes & POIs`:** Secondary enrichment. |
| 7 | **GreyNoise**<br><br>**`Link(s)`:** [docs.greynoise.io](https://docs.greynoise.io/), [viz.greynoise.io](https://viz.greynoise.io/)<br><br>**`Access / Cost`:** Free tier / paid plans | **`Relevance`:** Internet exploitation/scanning telemetry.<br><br>**`Notes & POIs`:** Distinguishes noise from activity. |
| 8 | **Shadowserver**<br><br>**`Link(s)`:** [dashboard.shadowserver.org](https://dashboard.shadowserver.org/), [www.shadowserver.org](https://www.shadowserver.org/)<br><br>**`Access / Cost`:** Free for eligible organizations; registration may be required | **`Relevance`:** Exposure & threat telemetry.<br><br>**`Notes & POIs`:** Access & reporting terms vary. |
| 9 | **Nuclei templates**<br><br>**`Link(s)`:** [github.com/projectdiscovery/nuclei-templates](https://github.com/projectdiscovery/nuclei-templates)<br><br>**`Access / Cost`:** Free / open-source | **`Relevance`:** Detection templates for exposed vulnerabilities.<br><br>**`Notes & POIs`:** Template presence is not proof of exposure. |
| 10 | **Vendor emergency advisories**<br><br>**`Link(s)`:** [www.cisa.gov/cybersecurity-advisories](https://www.cisa.gov/cybersecurity-advisories), [www.fortiguard.com/psirt](https://www.fortiguard.com/psirt), [forums.ivanti.com/s/security-advisory](https://forums.ivanti.com/s/security-advisory)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Emergency/active exploitation guidance.<br><br>**`Notes & POIs`:** Highly time-sensitive; monitor frequently. |

### 5.7 Tier 6 - weakness, attack-pattern & AI context

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **CWE**<br><br>**`Link(s)`:** [cwe.mitre.org](https://cwe.mitre.org/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Weakness taxonomy.<br><br>**`Notes & POIs`:** CVE-to-CWE mappings can be broad or missing. |
| 2 | **CAPEC**<br><br>**`Link(s)`:** [capec.mitre.org](https://capec.mitre.org/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Attack-pattern taxonomy.<br><br>**`Notes & POIs`:** Maps weaknesses to attack patterns. |
| 3 | **ATT&CK Enterprise**<br><br>**`Link(s)`:** [attack.mitre.org/matrices/enterprise](https://attack.mitre.org/matrices/enterprise/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Enterprise adversary behavior taxonomy.<br><br>**`Notes & POIs`:** More post-exploitation than CVE-specific. |
| 4 | **ATT&CK STIX**<br><br>**`Link(s)`:** [github.com/mitre-attack/attack-stix-data](https://github.com/mitre-attack/attack-stix-data)<br><br>**`Access / Cost`:** Free public GitHub repo | **`Relevance`:** Machine-readable ATT&CK data.<br><br>**`Notes & POIs`:** Best for ingestion. |
| 5 | **MITRE CTI repo**<br><br>**`Link(s)`:** [github.com/mitre/cti](https://github.com/mitre/cti)<br><br>**`Access / Cost`:** Free public GitHub repo | **`Relevance`:** MITRE STIX data repository.<br><br>**`Notes & POIs`:** Useful for CTI graphing. |
| 6 | **MITRE ATLAS**<br><br>**`Link(s)`:** [atlas.mitre.org](https://atlas.mitre.org/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** AI adversary tactics & techniques.<br><br>**`Notes & POIs`:** Directly relevant to AI/ML systems. |
| 7 | **OWASP LLM Top 10**<br><br>**`Link(s)`:** [owasp.org/www-project-top-10-for-large-language-model-applications](https://owasp.org/www-project-top-10-for-large-language-model-applications/)<br><br>**`Access / Cost`:** Free public / open community | **`Relevance`:** LLM application vulnerability taxonomy.<br><br>**`Notes & POIs`:** Good for AI appsec. |
| 8 | **OWASP ML Security Top 10**<br><br>**`Link(s)`:** [owasp.org/www-project-machine-learning-security-top-10](https://owasp.org/www-project-machine-learning-security-top-10/)<br><br>**`Access / Cost`:** Free public / open community | **`Relevance`:** ML security risk taxonomy.<br><br>**`Notes & POIs`:** Complements ATLAS. |
| 9 | **NIST AI RMF & NIST AI 600-1**<br><br>**`Link(s)`:** [nvlpubs.nist.gov/nistpubs/ai/NIST.AI.100-1.pdf](https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.100-1.pdf), [www.nist.gov/publications/artificial-intelligence-risk- management-framework-generative-artificial-intelligence](https://www.nist.gov/publications/artificial-intelligence-risk-management-framework-generative-artificial-intelligence)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** AI risk management & GenAI risk profile.<br><br>**`Notes & POIs`:** Governance/risk context, not vuln feed. |

### 5.8 Tier 7 - detection engineering & validation

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **CodeQL**<br><br>**`Link(s)`:** [codeql.github.com](https://codeql.github.com/)<br><br>**`Access / Cost`:** Free for many open-source uses; commercial GitHub Advanced Security for many enterprise/private workflows | **`Relevance`:** Semantic code vulnerability detection.<br><br>**`Notes & POIs`:** Strong for variant analysis. |
| 2 | **Semgrep**<br><br>**`Link(s)`:** [semgrep.dev](https://semgrep.dev/)<br><br>**`Access / Cost`:** Free/open-source CLI; commercial products available | **`Relevance`:** Pattern-based static analysis.<br><br>**`Notes & POIs`:** Fast custom rules. |
| 3 | **Joern**<br><br>**`Link(s)`:** [joern.io](https://joern.io/)<br><br>**`Access / Cost`:** Free / open-source | **`Relevance`:** Code property graph analysis.<br><br>**`Notes & POIs`:** Useful for research & advanced detection. |
| 4 | **Infer**<br><br>**`Link(s)`:** [fbinfer.com](https://fbinfer.com/)<br><br>**`Access / Cost`:** Free / open-source | **`Relevance`:** Static analysis engine.<br><br>**`Notes & POIs`:** Good for specific bug classes. |
| 5 | **Sonar rules**<br><br>**`Link(s)`:** [rules.sonarsource.com](https://rules.sonarsource.com/)<br><br>**`Access / Cost`:** Free public catalog; commercial Sonar products available | **`Relevance`:** Security/code quality rule catalog.<br><br>**`Notes & POIs`:** Useful for rule taxonomy mapping. |
| 6 | **Nuclei templates**<br><br>**`Link(s)`:** [github.com/projectdiscovery/nuclei-templates](https://github.com/projectdiscovery/nuclei-templates)<br><br>**`Access / Cost`:** Free / open-source | **`Relevance`:** DAST/exposure templates.<br><br>**`Notes & POIs`:** Template quality varies. |
| 7 | **OSS-Fuzz**<br><br>**`Link(s)`:** [google.github.io/oss-fuzz](https://google.github.io/oss-fuzz/)<br><br>**`Access / Cost`:** Free for eligible open-source projects | **`Relevance`:** Continuous fuzzing.<br><br>**`Notes & POIs`:** Useful for discovery & OSV-linked vulns. |
| 8 | **SARD / Juliet**<br><br>**`Link(s)`:** [samate.nist.gov/SARD](https://samate.nist.gov/SARD/), [samate.nist.gov/SARD/test- suites/112](https://samate.nist.gov/SARD/test-suites/112)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Test suites for vulnerability detection.<br><br>**`Notes & POIs`:** Useful for evaluation; not production vulnerability feed. |
| 9 | **Vulnerability datasets**<br><br>**`Link(s)`:** [github.com/DLVulDet/PrimeVul](https://github.com/DLVulDet/PrimeVul), [github.com/Icyrockton/MegaVul](https://github.com/Icyrockton/MegaVul), [github.com/ZeoVan/MSR_20_Code_vulnerability_CSV_Dataset](https://github.com/ZeoVan/MSR_20_Code_vulnerability_CSV_Dataset), [github.com/secureIT-project/CVEfixes](https://github.com/secureIT-project/CVEfixes), [github.com/tuhh-softsec/vul4j](https://github.com/tuhh-softsec/vul4j), [github.com/wagner-group/diversevul](https://github.com/wagner-group/diversevul), [sites.google.com/view/devign](https://sites.google.com/view/devign)<br><br>**`Access / Cost`:** Mostly free public research datasets; verify license individually | **`Relevance`:** ML/research datasets for vulnerability detection.<br><br>**`Notes & POIs`:** Validate labels, leakage, deduplication, & licensing. |

> 
> #### [*Back to **`Index`***](#index)
---

## 6. Recommended canonical data model coverage
A complete vulnerability impact system should be able to ingest or derive the following fields.

### 6.1 Vulnerability identity

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **CVE ID**<br><br>**`Link(s)`:** [github.com/CVEProject/cvelistV5](https://github.com/CVEProject/cvelistV5), [www.cve.org](https://www.cve.org/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Canonical vulnerability identifier.<br><br>**`Notes & POIs`:** Not all advisories have CVEs immediately. |
| 2 | **GHSA ID**<br><br>**`Link(s)`:** [github.com/advisories](https://github.com/advisories)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** GitHub Security Advisory identifier.<br><br>**`Notes & POIs`:** May exist without CVE. |
| 3 | **OSV ID**<br><br>**`Link(s)`:** [osv.dev](https://osv.dev/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** OSV vulnerability identifier.<br><br>**`Notes & POIs`:** Links package-specific affectedness & aliases. |
| 4 | **Vendor advisory ID**<br><br>**`Link(s)`:** [msrc.microsoft.com/update-guide](https://msrc.microsoft.com/update-guide), [www.oracle.com/security-alerts](https://www.oracle.com/security-alerts/)<br><br>**`Access / Cost`:** Mostly free public; some support details may require entitlement | **`Relevance`:** Vendor-specific advisory identifier.<br><br>**`Notes & POIs`:** Often most authoritative for product-specific truth. |
| 5 | **CWE ID**<br><br>**`Link(s)`:** [cwe.mitre.org](https://cwe.mitre.org/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Weakness class identifier.<br><br>**`Notes & POIs`:** Quality of mapping varies. |
| 6 | **CAPEC ID**<br><br>**`Link(s)`:** [capec.mitre.org](https://capec.mitre.org/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Attack-pattern identifier.<br><br>**`Notes & POIs`:** Useful for attack mechanism mapping. |
| 7 | **ATT&CK technique ID**<br><br>**`Link(s)`:** [attack.mitre.org/matrices/enterprise](https://attack.mitre.org/matrices/enterprise/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Adversary technique identifier.<br><br>**`Notes & POIs`:** Useful for detection/response mapping. |
| 8 | **ATLAS technique ID**<br><br>**`Link(s)`:** [atlas.mitre.org/techniques](https://atlas.mitre.org/techniques)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** AI/ML adversary technique identifier.<br><br>**`Notes & POIs`:** Relevant for AI systems. |
| 9 | **Alias graph**<br><br>**`Link(s)`:** [github.com/CVEProject/cvelistV5](https://github.com/CVEProject/cvelistV5), [github.com/advisories](https://github.com/advisories), [osv.dev](https://osv.dev/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Maps CVE/GHSA/OSV/vendor aliases.<br><br>**`Notes & POIs`:** Crucial for deduplication & correlation. |

### 6.2 Affectedness

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **Product name**<br><br>**`Link(s)`:** [nvd.nist.gov/products/cpe](https://nvd.nist.gov/products/cpe)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Identifies vulnerable products.<br><br>**`Notes & POIs`:** Normalize against CPE/PURL/vendor data. |
| 2 | **Vendor**<br><br>**`Link(s)`:** [www.cve.org](https://www.cve.org/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Vendor/product attribution.<br><br>**`Notes & POIs`:** Vendor naming can differ across sources. |
| 3 | **CPE**<br><br>**`Link(s)`:** [nvd.nist.gov/developers/products](https://nvd.nist.gov/developers/products)<br><br>**`Access / Cost`:** Free public; optional free API key for higher rate limits | **`Relevance`:** Product/platform matching.<br><br>**`Notes & POIs`:** Imprecise for many OSS packages. |
| 4 | **PURL**<br><br>**`Link(s)`:** [github.com/package-url/purl-spec](https://github.com/package-url/purl-spec)<br><br>**`Access / Cost`:** Free / open-source | **`Relevance`:** Package identity.<br><br>**`Notes & POIs`:** Prefer for package ecosystem matching. |
| 5 | **Package ecosystem**<br><br>**`Link(s)`:** [osv.dev/list](https://osv.dev/list)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Defines package namespace & version rules.<br><br>**`Notes & POIs`:** Version semantics are ecosystem-specific. |
| 6 | **Package name**<br><br>**`Link(s)`:** [deps.dev](https://deps.dev/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Dependency identity.<br><br>**`Notes & POIs`:** Normalize casing & namespace rules. |
| 7 | **Affected version range**<br><br>**`Link(s)`:** [ossf.github.io/osv-schema](https://ossf.github.io/osv-schema/)<br><br>**`Access / Cost`:** Free public / open-source | **`Relevance`:** Expresses vulnerable versions.<br><br>**`Notes & POIs`:** Range interpretation must respect ecosystem semantics. |
| 8 | **Fixed version**<br><br>**`Link(s)`:** [github.com/advisories](https://github.com/advisories), [osv.dev](https://osv.dev/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Remediation target.<br><br>**`Notes & POIs`:** Distro fixed versions may differ due to backports. |
| 9 | **Introduced version / commit**<br><br>**`Link(s)`:** [ossf.github.io/osv-schema](https://ossf.github.io/osv-schema/)<br><br>**`Access / Cost`:** Free public / open-source | **`Relevance`:** Determines when vulnerability entered codebase.<br><br>**`Notes & POIs`:** Not always available. |
| 10 | **Last affected version**<br><br>**`Link(s)`:** [ossf.github.io/osv-schema](https://ossf.github.io/osv-schema/)<br><br>**`Access / Cost`:** Free public / open-source | **`Relevance`:** Helps determine affected version bounds.<br><br>**`Notes & POIs`:** Validate with vendor feeds. |
| 11 | **Backport status**<br><br>**`Link(s)`:** [access.redhat.com/security/data](https://access.redhat.com/security/data), [security-tracker.debian.org](https://security-tracker.debian.org/), [ubuntu.com/security/cves](https://ubuntu.com/security/cves)<br><br>**`Access / Cost`:** Mostly free public; some Red Hat support details may require subscription | **`Relevance`:** Determines if a distro package is patched despite upstream version appearing vulnerable.<br><br>**`Notes & POIs`:** Essential for reducing false positives. |
| 12 | **VEX status**<br><br>**`Link(s)`:** [github.com/openvex/spec](https://github.com/openvex/spec), [www.csaf.io](https://www.csaf.io/)<br><br>**`Access / Cost`:** Free / open-source standards | **`Relevance`:** Represents affected, not affected, fixed, or under investigation.<br><br>**`Notes & POIs`:** Preserve justification & author provenance. |
| 13 | **Justification for not affected**<br><br>**`Link(s)`:** [github.com/openvex/spec](https://github.com/openvex/spec)<br><br>**`Access / Cost`:** Free / open-source | **`Relevance`:** Explains why a product is not affected.<br><br>**`Notes & POIs`:** Key for trust & auditability. |
| 14 | **Distro/package release channel**<br><br>**`Link(s)`:** [packages.fedoraproject.org](https://packages.fedoraproject.org/), [pkgs.alpinelinux.org/packages](https://pkgs.alpinelinux.org/packages)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Tracks package release stream.<br><br>**`Notes & POIs`:** Channel differences can affect fix availability. |

### 6.3 Severity & exploitability

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **CVSS v2/v3/v4 vector**<br><br>**`Link(s)`:** [www.first.org/cvss](https://www.first.org/cvss/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Structured severity vector.<br><br>**`Notes & POIs`:** Use vector, not only numeric score. |
| 2 | **CVSS base/temporal/environmental score**<br><br>**`Link(s)`:** [nvd.nist.gov/vuln-metrics/cvss](https://nvd.nist.gov/vuln-metrics/cvss)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Severity scoring.<br><br>**`Notes & POIs`:** Environmental score should be computed with local context. |
| 3 | **EPSS score**<br><br>**`Link(s)`:** [www.first.org/epss](https://www.first.org/epss/)<br><br>**`Access / Cost`:** Free public data/API | **`Relevance`:** Exploit likelihood.<br><br>**`Notes & POIs`:** Temporal; store score date. |
| 4 | **EPSS percentile**<br><br>**`Link(s)`:** [www.first.org/epss/data_stats](https://www.first.org/epss/data_stats)<br><br>**`Access / Cost`:** Free public data downloads | **`Relevance`:** Relative exploit-likelihood ranking.<br><br>**`Notes & POIs`:** Useful for prioritization across backlog. |
| 5 | **KEV membership**<br><br>**`Link(s)`:** [www.cisa.gov/sites/default/files/feeds/known_exploited_vulnerabilities.json](https://www.cisa.gov/sites/default/files/feeds/known_exploited_vulnerabilities.json)<br><br>**`Access / Cost`:** Free public feed | **`Relevance`:** Known exploited vulnerability marker.<br><br>**`Notes & POIs`:** Strong exploitation evidence. |
| 6 | **KEV date added**<br><br>**`Link(s)`:** [www.cisa.gov/sites/default/files/feeds/known_exploited_vulnerabilities.json](https://www.cisa.gov/sites/default/files/feeds/known_exploited_vulnerabilities.json)<br><br>**`Access / Cost`:** Free public feed | **`Relevance`:** Temporal exploitation/prioritization signal.<br><br>**`Notes & POIs`:** Use for SLA & trend analysis. |
| 7 | **Known ransomware usage**<br><br>**`Link(s)`:** [www.ransomware.live](https://www.ransomware.live/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Ransomware exploitation context.<br><br>**`Notes & POIs`:** Attribution & mapping quality vary. |
| 8 | **Public exploit available**<br><br>**`Link(s)`:** [www.exploit-db.com](https://www.exploit-db.com/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** PoC/exploit availability.<br><br>**`Notes & POIs`:** Verify reliability & version applicability. |
| 9 | **Metasploit module available**<br><br>**`Link(s)`:** [github.com/rapid7/metasploit-framework/tree/master/modules/exploits](https://github.com/rapid7/metasploit-framework/tree/master/modules/exploits)<br><br>**`Access / Cost`:** Free / open-source | **`Relevance`:** Weaponized exploit implementation.<br><br>**`Notes & POIs`:** Stronger than generic PoC signal. |
| 10 | **Nuclei template available**<br><br>**`Link(s)`:** [github.com/projectdiscovery/nuclei-templates](https://github.com/projectdiscovery/nuclei-templates)<br><br>**`Access / Cost`:** Free / open-source | **`Relevance`:** Detection template availability.<br><br>**`Notes & POIs`:** Indicates detectable exposure, not confirmed vulnerability. |
| 11 | **GreyNoise observed scanning**<br><br>**`Link(s)`:** [viz.greynoise.io](https://viz.greynoise.io/)<br><br>**`Access / Cost`:** Free tier / paid plans | **`Relevance`:** Internet scanning/exploitation telemetry.<br><br>**`Notes & POIs`:** Helps prioritize exposed services. |
| 12 | **Shadowserver observed exposure**<br><br>**`Link(s)`:** [dashboard.shadowserver.org](https://dashboard.shadowserver.org/)<br><br>**`Access / Cost`:** Free for eligible organizations; registration may be required | **`Relevance`:** Internet-scale exposure telemetry.<br><br>**`Notes & POIs`:** Access may require registration/eligibility. |
| 13 | **CISA SSVC decision points**<br><br>**`Link(s)`:** [github.com/cisagov/vulnrichment](https://github.com/cisagov/vulnrichment)<br><br>**`Access / Cost`:** Free public GitHub repo | **`Relevance`:** Decision support enrichment.<br><br>**`Notes & POIs`:** Useful for prioritization workflows. |
| 14 | **Vendor exploitation status**<br><br>**`Link(s)`:** [msrc.microsoft.com/update-guide](https://msrc.microsoft.com/update-guide), [security.paloaltonetworks.com](https://security.paloaltonetworks.com/), [support.apple.com/en-us/100100](https://support.apple.com/en-us/100100)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Vendor-provided exploitation notes.<br><br>**`Notes & POIs`:** Time-sensitive & product-specific. |
| 15 | **Patch availability**<br><br>**`Link(s)`:** [access.redhat.com/security/data](https://access.redhat.com/security/data), [security-tracker.debian.org](https://security-tracker.debian.org/), [ubuntu.com/security/notices](https://ubuntu.com/security/notices)<br><br>**`Access / Cost`:** Mostly free public; some vendor support details may require subscription | **`Relevance`:** Determines if a fix exists.<br><br>**`Notes & POIs`:** Patch availability varies by release stream. |
| 16 | **Workaround availability**<br><br>**`Link(s)`:** [www.cisa.gov/cybersecurity-advisories](https://www.cisa.gov/cybersecurity-advisories), [www.kb.cert.org/vuls](https://www.kb.cert.org/vuls/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Temporary mitigation when patching is not available.<br><br>**`Notes & POIs`:** Workarounds may reduce but not eliminate risk. |

### 6.4 Environmental impact

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | Asset criticality | [www.cisecurity.org/controls](https://www.cisecurity.org/controls) | Free public | Business/system importance affects risk. | Must come from internal asset inventory. |
| 2 | Internet exposure | [search.censys.io](https://search.censys.io/), [www.shodan.io](https://www.shodan.io/) | Free tiers / paid plans | Determines external exploitability surface. | External scan data may be incomplete or stale. |
| 3 | Network reachability | [nmap.org](https://nmap.org/) | Free / open-source | Determines whether an exploit path exists. | Internal network context required. |
| 4 | Authentication required | [www.first.org/cvss](https://www.first.org/cvss/) | Free public | Impacts exploitability. | CVSS may not capture local compensating controls. |
| 5 | Privilege required | [www.first.org/cvss](https://www.first.org/cvss/) | Free public | Impacts exploitability & blast radius. | Validate with product configuration. |
| 6 | User interaction required | [www.first.org/cvss](https://www.first.org/cvss/) | Free public | Impacts exploitability conditions. | User interaction can be bypassed in some real-world chains. |
| 7 | Exploit preconditions | [projectzero.google](https://projectzero.google/), [www.kb.cert.org/vuls](https://www.kb.cert.org/vuls/) | Free public | Defines required configuration or state. | Crucial for false-positive reduction. |
| 8 | Data sensitivity | [www.cisecurity.org/controls](https://www.cisecurity.org/controls) | Free public | Determines business impact. | Internal classification required. |
| 9 | Compensating controls | [public.cyber.mil/stigs](https://public.cyber.mil/stigs/), [www.cisecurity.org/cis- benchmarks](https://www.cisecurity.org/cis-benchmarks) | Free public; CIS benchmarks may require free registration | Controls can reduce practical exploitability. | Document assumptions & evidence. |
| 10 | Runtime configuration | [docs.dependencytrack.org/datasources/overview](https://docs.dependencytrack.org/datasources/overview/) | Free public docs | Enabled features/modules influence affectedness. | Scanner package matches alone can over-report. |
| 11 | Feature/module enabled | [github.com/openvex/spec](https://github.com/openvex/spec) | Free / open-source | VEX not-affected reasoning may depend on disabled code paths. | Requires product/runtime evidence. |
| 12 | Cloud account/project/environment | [github.com/prowler-cloud/prowler](https://github.com/prowler-cloud/prowler) | Free / open-source core; commercial products separate | Cloud context affects exposure & blast radius. | Join vulnerability data with cloud inventory. |
| 13 | Blast radius | [github.com/salesforce/cloudsplaining](https://github.com/salesforce/cloudsplaining) | Free / open-source | Privilege & dependency spread determine impact. | Requires IAM, network, & data-flow context. |
| 14 | Business process ownership | [www.cisecurity.org/controls](https://www.cisecurity.org/controls) | Free public | Ownership determines remediation accountability. | Internal data source required. |

### 6.5 Detection & remediation

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **Scanner finding ID**<br><br>**`Link(s)`:** [dependencytrack.org](https://dependencytrack.org/), [github.com/anchore/grype](https://github.com/anchore/grype), [trivy.dev/docs/latest/scanner/vulnerability](https://trivy.dev/docs/latest/scanner/vulnerability/)<br><br>**`Access / Cost`:** Free / open-source core tools; commercial support/products may exist | **`Relevance`:** Scanner-specific finding identity.<br><br>**`Notes & POIs`:** Preserve source scanner & version for reproducibility. |
| 2 | **Detection method**<br><br>**`Link(s)`:** [codeql.github.com](https://codeql.github.com/), [github.com/projectdiscovery/nuclei](https://github.com/projectdiscovery/nuclei), [owasp.org/www-project-top-ten](https://owasp.org/www-project-top-ten/)<br><br>**`Access / Cost`:** Mixed: free/open-source, with some commercial tiers | **`Relevance`:** Indicates whether finding came from SBOM, CPE, package manager, SAST, DAST, IaC, or runtime telemetry.<br><br>**`Notes & POIs`:** Different methods have different false-positive characteristics. |
| 3 | **Confidence**<br><br>**`Link(s)`:** [github.com/openvex/spec](https://github.com/openvex/spec)<br><br>**`Access / Cost`:** Free / open-source | **`Relevance`:** Confidence helps rank findings.<br><br>**`Notes & POIs`:** Use evidence & source provenance to compute confidence. |
| 4 | **False-positive reason**<br><br>**`Link(s)`:** [github.com/openvex/spec](https://github.com/openvex/spec)<br><br>**`Access / Cost`:** Free / open-source | **`Relevance`:** Captures why a match is not actually exploitable or affected.<br><br>**`Notes & POIs`:** VEX justification is key for auditability. |
| 5 | **Fix version**<br><br>**`Link(s)`:** [github.com/advisories](https://github.com/advisories), [osv.dev](https://osv.dev/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Remediation target version.<br><br>**`Notes & POIs`:** Distro fixed versions may differ due to backports. |
| 6 | **Patch advisory**<br><br>**`Link(s)`:** [access.redhat.com/security/data](https://access.redhat.com/security/data), [ubuntu.com/security/notices](https://ubuntu.com/security/notices), [www.debian.org/security](https://www.debian.org/security/)<br><br>**`Access / Cost`:** Mostly free public; some Red Hat support details may require subscription | **`Relevance`:** Links vulnerability to vendor patch guidance.<br><br>**`Notes & POIs`:** Use vendor patch source for production remediation. |
| 7 | **Mitigation**<br><br>**`Link(s)`:** [www.cisa.gov/cybersecurity-advisories](https://www.cisa.gov/cybersecurity-advisories), [www.kb.cert.org/vuls](https://www.kb.cert.org/vuls/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Temporary or compensating controls.<br><br>**`Notes & POIs`:** Mitigations may be partial & context-specific. |
| 8 | **Workaround**<br><br>**`Link(s)`:** [www.kb.cert.org/vuls](https://www.kb.cert.org/vuls/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Alternative remediation when patch unavailable.<br><br>**`Notes & POIs`:** Track expiration & replacement by patch. |
| 9 | **Exploit detection signatures**<br><br>**`Link(s)`:** [github.com/SigmaHQ/sigma](https://github.com/SigmaHQ/sigma), [github.com/VirusTotal/yara](https://github.com/VirusTotal/yara), [github.com/projectdiscovery/nuclei-templates](https://github.com/projectdiscovery/nuclei-templates)<br><br>**`Access / Cost`:** Free / open-source public GitHub repos | **`Relevance`:** Detection content for exploit attempts or compromise.<br><br>**`Notes & POIs`:** Validate signatures in environment before high-confidence alerting. |
| 10 | **Regression test**<br><br>**`Link(s)`:** [github.com/google/oss-fuzz](https://github.com/google/oss-fuzz), [google.github.io/oss- fuzz](https://google.github.io/oss-fuzz/)<br><br>**`Access / Cost`:** Free / open-source; OSS-Fuzz service for eligible OSS projects | **`Relevance`:** Tests that a vulnerability class or bug does not reappear.<br><br>**`Notes & POIs`:** Useful for secure SDLC feedback loops. |
| 11 | **Verification command**<br><br>**`Link(s)`:** [github.com/anchore/grype](https://github.com/anchore/grype), [github.com/aquasecurity/trivy-db](https://github.com/aquasecurity/trivy-db), [github.com/projectdiscovery/nuclei](https://github.com/projectdiscovery/nuclei)<br><br>**`Access / Cost`:** Free / open-source | **`Relevance`:** Command/procedure to verify vulnerability or remediation state.<br><br>**`Notes & POIs`:** Required for repeatable remediation closure. |
| 12 | **SLA due date**<br><br>**`Link(s)`:** [www.cisa.gov/news-events/directives/bod-22-01-reducing-significant-risk-known-exploited- vulnerabilities](https://www.cisa.gov/news-events/directives/bod-22-01-reducing-significant-risk-known-exploited-vulnerabilities), [www.cisa.gov/sites/default/files/feeds/known_exploited_vulnerabilities.json](https://www.cisa.gov/sites/default/files/feeds/known_exploited_vulnerabilities.json)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Remediation deadline derived from KEV, severity, exposure, policy, or business context.<br><br>**`Notes & POIs`:** SLA should be policy-driven & context- aware. |

> 
> #### [*Back to **`Index`***](#index)
---

---

## C. Weakness Taxonomy, Attack Mapping & AI/ML Vulnerability Context

## 7. CWE, CAPEC, ATT&CK, ATLAS & weakness-to-attack mapping

### 7.1 CWE - Common Weakness Enumeration

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **CWE home**<br><br>**`Link(s)`:** [cwe.mitre.org](https://cwe.mitre.org/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Common Weakness Enumeration root. Provides standardized weakness taxonomy.<br><br>**`Notes & POIs`:** CVE-to-CWE mappings are sometimes missing, broad, or imprecise. |
| 2 | **CWE downloads**<br><br>**`Link(s)`:** [cwe.mitre.org/data/downloads.html](https://cwe.mitre.org/data/downloads.html)<br><br>**`Access / Cost`:** Free public downloads | **`Relevance`:** XML, CSV, archive bundles, & views for machine ingestion.<br><br>**`Notes & POIs`:** Use downloadable structured data for robust taxonomy ingestion. |
| 3 | **CWE latest PDF**<br><br>**`Link(s)`:** [cwe.mitre.org/data/published/cwe_latest.pdf](https://cwe.mitre.org/data/published/cwe_latest.pdf)<br><br>**`Access / Cost`:** Free public PDF | **`Relevance`:** PDF publication of latest CWE content.<br><br>**`Notes & POIs`:** Better for manual reference than automated ingestion. |
| 4 | **CWE reports**<br><br>**`Link(s)`:** [cwe.mitre.org/data/reports.html](https://cwe.mitre.org/data/reports.html)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Reports & curated views of CWE data.<br><br>**`Notes & POIs`:** Useful for understanding categories, views, & prioritization. |
| 5 | **CWE chains & composites**<br><br>**`Link(s)`:** [cwe.mitre.org/data/reports/chains_and_composites.html](https://cwe.mitre.org/data/reports/chains_and_composites.html)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Describes weakness chains & composite weaknesses.<br><br>**`Notes & POIs`:** Important for modeling multi-step root causes & compound vulnerabilities. |
| 6 | **CWE schema docs**<br><br>**`Link(s)`:** [cwe.mitre.org/documents/schema/index.html](https://cwe.mitre.org/documents/schema/index.html)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Schema documentation for CWE data.<br><br>**`Notes & POIs`:** Use for parser validation & taxonomy consistency. |
| 7 | CWE data definitions | [cwe.mitre.org/data/definitions/1000.html](https://cwe.mitre.org/data/definitions/1000.html) | Free public | CWE views & weakness hierarchy. | Useful for grouping weaknesses into higher-level categories. |
| 8 | CWE Top 25 | [cwe.mitre.org/top25](https://cwe.mitre.org/top25/) | Free public | Most dangerous software weaknesses. | Good for model priors & training labels, but not a substitute for context-specific risk. |
| 9 | CWE AI/ML category - CWE-1448 | [cwe.mitre.org/data/definitions/1448.html](https://cwe.mitre.org/data/definitions/1448.html) | Free public | AI/ML-related weakness category. | Emerging taxonomy area; expect coverage to evolve. |
| 10 | CWE AI Working Group | [cwe.mitre.org/community/working_groups.html](https://cwe.mitre.org/community/working_groups.html) | Free public | CWE/CVE AI Working Group context. | Useful for tracking evolution of AI-related weakness classifications. |

### 7.2 CAPEC - attack patterns

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **CAPEC home**<br><br>**`Link(s)`:** [capec.mitre.org](https://capec.mitre.org/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Catalog of attack patterns used to exploit weaknesses.<br><br>**`Notes & POIs`:** CAPEC bridges weakness taxonomy & attacker behavior patterns. |
| 2 | **CAPEC downloads**<br><br>**`Link(s)`:** [capec.mitre.org/data/downloads.html](https://capec.mitre.org/data/downloads.html)<br><br>**`Access / Cost`:** Free public downloads | **`Relevance`:** XML/CSV attack-pattern bundles.<br><br>**`Notes & POIs`:** Prefer structured downloads for ingestion. |
| 3 | **CAPEC schema docs**<br><br>**`Link(s)`:** [capec.mitre.org/documents/schema/index.html](https://capec.mitre.org/documents/schema/index.html)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Schema docs for CAPEC data.<br><br>**`Notes & POIs`:** Important for parser validation. |
| 4 | **CAPEC data index**<br><br>**`Link(s)`:** [capec.mitre.org/data/index.html](https://capec.mitre.org/data/index.html)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Browsable CAPEC entries & views.<br><br>**`Notes & POIs`:** Useful for manual mapping & explanation. |
| 5 | **MITRE CTI repository - ATT&CK & CAPEC in STIX**<br><br>**`Link(s)`:** [github.com/mitre/cti](https://github.com/mitre/cti)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** MITRE ATT&CK & CAPEC datasets expressed in STIX 2.0.<br><br>**`Notes & POIs`:** Useful for graph-based relationships. May differ from newer ATT&CK-specific STIX repo content. |

### 7.3 MITRE ATT&CK

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **ATT&CK Enterprise Matrix**<br><br>**`Link(s)`:** [attack.mitre.org/matrices/enterprise](https://attack.mitre.org/matrices/enterprise/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Enterprise adversary tactics & techniques.<br><br>**`Notes & POIs`:** More relevant for adversary behavior after exploitation than raw CVE severity. |
| 2 | **ATT&CK Matrices**<br><br>**`Link(s)`:** [attack.mitre.org/matrices](https://attack.mitre.org/matrices/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** ATT&CK matrices across domains.<br><br>**`Notes & POIs`:** Useful for selecting enterprise, mobile, ICS, or other domain views. |
| 3 | **ATT&CK Data & Tools**<br><br>**`Link(s)`:** [attack.mitre.org/resources/attack-data-and-tools](https://attack.mitre.org/resources/attack-data-and-tools/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** ATT&CK Navigator, STIX/TAXII, Workbench, & tooling references.<br><br>**`Notes & POIs`:** Prefer machine-readable STIX/TAXII for ingestion. |
| 4 | **ATT&CK STIX data repo**<br><br>**`Link(s)`:** [github.com/mitre-attack/attack-stix-data](https://github.com/mitre-attack/attack-stix-data)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** Machine-readable ATT&CK STIX data.<br><br>**`Notes & POIs`:** Best source for automated technique/tactic ingestion. |
| 5 | **MITRE CTI repository**<br><br>**`Link(s)`:** [github.com/mitre/cti](https://github.com/mitre/cti)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** MITRE CTI STIX datasets.<br><br>**`Notes & POIs`:** Keep for historical/related STIX content. |
| 6 | **ATT&CK Navigator**<br><br>**`Link(s)`:** [mitre-attack.github.io/attack-navigator](https://mitre-attack.github.io/attack-navigator/)<br><br>**`Access / Cost`:** Free / open-source web tool | **`Relevance`:** Visual mapping of techniques to campaigns, risks, or controls.<br><br>**`Notes & POIs`:** Useful for reporting & matrix visualization, not raw vuln ingestion. |
| 7 | **ATT&CK Workbench**<br><br>**`Link(s)`:** [github.com/center-for-threat-informed-defense/attack-workbench-frontend](https://github.com/center-for-threat-informed-defense/attack-workbench-frontend)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** Tooling for ATT&CK customization & management.<br><br>**`Notes & POIs`:** Useful for internal technique mapping workflows. |
| 8 | **ATT&CK TAXII server docs**<br><br>**`Link(s)`:** [attack.mitre.org/resources/attack-data-and-tools](https://attack.mitre.org/resources/attack-data-and-tools/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** TAXII/STIX access docs.<br><br>**`Notes & POIs`:** Same source as ATT&CK Data & Tools; retained to preserve the explicit TAXII reference. |
| 9 | **ATT&CK Sync**<br><br>**`Link(s)`:** [github.com/center-for-threat-informed-defense/attack-sync](https://github.com/center-for-threat-informed-defense/attack-sync)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** Tooling for consuming MITRE ATT&CK version updates into internal systems & processes.<br><br>**`Notes & POIs`:** Useful for keeping local ATT&CK technique mappings current. |
| 10 | **MITRE ATT&CK Python**<br><br>**`Link(s)`:** [github.com/mitre-attack/mitreattack-python](https://github.com/mitre-attack/mitreattack-python)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** Python module for working with ATT&CK datasets.<br><br>**`Notes & POIs`:** Useful for programmatic ATT&CK ingestion, transformation, & analysis. |
| 11 | **ATT&CK Navigator GitHub repo**<br><br>**`Link(s)`:** [github.com/mitre-attack/attack-navigator](https://github.com/mitre-attack/attack-navigator)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** Source repository for the ATT&CK Navigator web app.<br><br>**`Notes & POIs`:** Complements the hosted Navigator URL; useful for local customization & offline visualization workflows. |

### 7.4 AI/ML-specific adversary frameworks
| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **MITRE ATLAS**<br><br>**`Link(s)`:** [atlas.mitre.org](https://atlas.mitre.org/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Living knowledge base of adversary tactics & techniques against AI-enabled systems.<br><br>**`Notes & POIs`:** More directly relevant to AI systems than ATT&CK Enterprise alone. |
| 2 | **MITRE ATLAS matrix**<br><br>**`Link(s)`:** [atlas.mitre.org/matrices/ATLAS](https://atlas.mitre.org/matrices/ATLAS)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Matrix view of AI adversary tactics & techniques.<br><br>**`Notes & POIs`:** Useful for AI threat modeling & impact mapping. |
| 3 | **MITRE ATLAS techniques**<br><br>**`Link(s)`:** [atlas.mitre.org/techniques](https://atlas.mitre.org/techniques)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Technique-level ATLAS entries.<br><br>**`Notes & POIs`:** Use for structured AI attack technique mapping. |
| 4 | **MITRE ATLAS case studies**<br><br>**`Link(s)`:** [atlas.mitre.org/studies](https://atlas.mitre.org/studies)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Case studies of AI attacks & failures.<br><br>**`Notes & POIs`:** Helpful for real-world analogs & model training examples. |
| 5 | **MITRE ATLAS data repository / case-study data**<br><br>**`Link(s)`:** [github.com/mitre-atlas/atlas-data](https://github.com/mitre-atlas/atlas-data), [case studies](https://github.com/mitre-atlas/atlas-data/tree/main/data/case-studies)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** Structured ATLAS data, including case-study material.<br><br>**`Notes & POIs`:** Prefer this for machine-readable ATLAS case-study ingestion. |
| 6 | **MITRE ATLAS GitHub / Adversarial ML Threat Matrix**<br><br>**`Link(s)`:** [github.com/mitre/advmlthreatmatrix](https://github.com/mitre/advmlthreatmatrix)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** Historical & structured project data for adversarial ML threat matrix.<br><br>**`Notes & POIs`:** May not be the most current ATLAS view; keep for lineage. |
| 7 | **MITRE SAFE-AI report**<br><br>**`Link(s)`:** [atlas.mitre.org/pdf-files/SAFEAI_Full_Report.pdf](https://atlas.mitre.org/pdf-files/SAFEAI_Full_Report.pdf)<br><br>**`Access / Cost`:** Free public PDF | **`Relevance`:** AI system risk mapping across model, data, platform, & environment layers.<br><br>**`Notes & POIs`:** Useful for AI-specific control mapping & architecture risk analysis. |
| 8 | **OWASP Top 10 for LLM Applications**<br><br>**`Link(s)`:** [owasp.org/www-project-top-10-for-large-language-model-applications](https://owasp.org/www-project-top-10-for-large-language-model-applications/)<br><br>**`Access / Cost`:** Free / open-source community project | **`Relevance`:** Practical LLM application vulnerability taxonomy.<br><br>**`Notes & POIs`:** Useful for AI appsec detection categories beyond CVE. |
| 9 | **OWASP Top 10 for Machine Learning Security**<br><br>**`Link(s)`:** [owasp.org/www-project-machine-learning-security-top-10](https://owasp.org/www-project-machine-learning-security-top-10/)<br><br>**`Access / Cost`:** Free / open-source community project | **`Relevance`:** ML-specific application/security risk taxonomy.<br><br>**`Notes & POIs`:** Complements ATLAS with appsec-oriented framing. |
| 10 | **OWASP AI Exchange**<br><br>**`Link(s)`:** [owaspai.org](https://owaspai.org/)<br><br>**`Access / Cost`:** Free public community resource | **`Relevance`:** AI security risks, controls, & threat modeling references.<br><br>**`Notes & POIs`:** Useful for governance & risk mapping. |
| 11 | **NIST AI Risk Management Framework**<br><br>**`Link(s)`:** [www.nist.gov/itl/ai-risk-management-framework](https://www.nist.gov/itl/ai-risk-management-framework)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** AI risk management framework.<br><br>**`Notes & POIs`:** Useful for risk controls, governance, & impact framing. |
| 12 | **NIST AI RMF 1.0 PDF**<br><br>**`Link(s)`:** [nvlpubs.nist.gov/nistpubs/ai/NIST.AI.100-1.pdf](https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.100-1.pdf)<br><br>**`Access / Cost`:** Free public PDF | **`Relevance`:** AI RMF 1.0 document.<br><br>**`Notes & POIs`:** PDF reference; not a vulnerability feed. |
| 13 | **NIST AI 600-1 - Generative AI Profile**<br><br>**`Link(s)`:** [www.nist.gov/publications/artificial-intelligence-risk-management-framework-generative-artificial-intelligence](https://www.nist.gov/publications/artificial-intelligence-risk-management-framework-generative-artificial-intelligence)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** GenAI risk profile companion to AI RMF.<br><br>**`Notes & POIs`:** Useful for LLM/generative AI-specific risk categories. |
| 14 | **NIST adversarial machine learning taxonomy**<br><br>**`Link(s)`:** [www.nist.gov/publications/adversarial-machine-learning-taxonomy-and-terminology-attacks-and-mitigations](https://www.nist.gov/publications/adversarial-machine-learning-taxonomy-and-terminology-attacks-and-mitigations)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Taxonomy & terminology for adversarial ML attacks & mitigations.<br><br>**`Notes & POIs`:** Good for consistent AI vulnerability vocabulary. |
| 15 | **MLCommons AI Safety**<br><br>**`Link(s)`:** [mlcommons.org/working-groups/ai-safety](https://mlcommons.org/working-groups/ai-safety/)<br><br>**`Access / Cost`:** Free public community resource | **`Relevance`:** AI safety benchmarks & working group context.<br><br>**`Notes & POIs`:** Useful for AI system risk evaluation, not direct CVE matching. |
| 16 | **MITRE ATLAS AI Risk Database**<br><br>**`Link(s)`:** [github.com/mitre-atlas/ai-risk-database](https://github.com/mitre-atlas/ai-risk-database)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** AI supply-chain risk database associated with MITRE ATLAS ecosystem work.<br><br>**`Notes & POIs`:** Useful for AI-specific supply-chain risk analysis & case-study style enrichment. |
| 17 | **Cisco AI Defense Skill Scanner**<br><br>**`Link(s)`:** [github.com/cisco-ai-defense/skill-scanner](https://github.com/cisco-ai-defense/skill-scanner)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** Security scanner for agent skills.<br><br>**`Notes & POIs`:** Useful for AI-agent/tooling security review, prompt/tool-surface assessment, & skill-level exposure analysis. |

> 
> #### [*Back to **`Index`***](#index)
---

---

## D. Affectedness Truth: Package, OS, Vendor, Cloud, ICS & Product Advisories

## 8. Open-source vulnerability databases & package advisory sources

### 8.1 OSV ecosystem

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **OSV main site**<br><br>**`Link(s)`:** [osv.dev](https://osv.dev/)<br><br>**`Access / Cost`:** Free public / open data | **`Relevance`:** Aggregates OSS vulnerabilities by package ecosystem, version, commit, & aliases. Key for dependency-based detection.<br><br>**`Notes & POIs`:** OSV is package/version- centric & often better than CPE for OSS packages. Coverage depends on upstream ecosystem feeds. |
| 2 | **OSV vulnerability list**<br><br>**`Link(s)`:** [osv.dev/list](https://osv.dev/list)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Human-browsable OSV records.<br><br>**`Notes & POIs`:** Useful for manual triage & ecosystem browsing. Prefer API/full downloads for automation. |
| 3 | **OSV full database download**<br><br>**`Link(s)`:** [google.github.io/osv.dev/data/#full-database-download](https://google.github.io/osv.dev/data/#full-database-download)<br><br>**`Access / Cost`:** Free public / open data | **`Relevance`:** Full database ZIP, including withdrawn records, via `gs://osv-vulnerabilities/all.zip`.<br><br>**`Notes & POIs`:** Best for local mirroring. Preserve withdrawn records for historical auditability. |
| 4 | **OSV data sources page**<br><br>**`Link(s)`:** [google.github.io/osv.dev/data](https://google.github.io/osv.dev/data/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Per-ecosystem downloads & full-database download.<br><br>**`Notes & POIs`:** Useful for targeted ecosystem ingestion. |
| 5 | OSV schema rendered spec | [ossf.github.io/osv-schema](https://ossf.github.io/osv-schema/) | Free public / open-source | Standard interchange format for OSS vulnerability records. | Handle aliases, affected ranges, fixed versions, withdrawn records, & ecosystem-specific semantics. |
| 6 | OSV schema GitHub repo | [github.com/ossf/osv-schema](https://github.com/ossf/osv-schema) | Free / open-source public GitHub repo | Schema source, releases, bindings, & tooling. | Track schema versions & validation changes over time. |
| 7 | OSV API docs | [google.github.io/osv.dev/post-v1-query](https://google.github.io/osv.dev/post-v1-query/) | Free public API | Query vulnerabilities by package, version, commit, or vulnerability ID. | Good for online lookup. Use full downloads for high-volume local matching. |
| 8 | OSV Scanner | [google.github.io/osv-scanner](https://google.github.io/osv-scanner/) | Free public / open-source | Reference scanner using OSV data. | Useful implementation reference for lockfile parsing & version matching. |
| 9 | OSV Scanner GitHub | [github.com/google/osv-scanner](https://github.com/google/osv-scanner) | Free / open-source public GitHub repo | Scanner implementation, matching logic, & lockfile parsing. | Review for practical matching edge cases. |
| 10 | OSV ecosystem list | [osv.dev/list](https://osv.dev/list) | Free public | Ecosystem browsing for Maven, npm, PyPI, Go, crates.io, Debian, Alpine, Ubuntu, Wolfi, OSS-Fuzz, etc. | Repeats the list URL intentionally because it serves both record browsing & ecosystem discovery. |
| 11 | OSV.dev GitHub repository | [github.com/google/osv.dev](https://github.com/google/osv.dev) | Free / open-source public GitHub repo | Source/infrastructure repo for OSV.dev, API, data dump references, importer/conversion tooling, workers, docs, & service code. | Useful for understanding OSV implementation, feed conversion, API behavior & ecosystem semantics. |

### 8.2 GitHub Advisory Database

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **GitHub Advisory Database - web**<br><br>**`Link(s)`:** [github.com/advisories](https://github.com/advisories)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** GitHub-reviewed, unreviewed, malware, GHSA, & CVE advisory records across ecosystems.<br><br>**`Notes & POIs`:** GHSA records can exist without CVEs. Preserve alias relationships between GHSA, CVE, & OSV. |
| 2 | **GitHub Advisory Database repo**<br><br>**`Link(s)`:** [github.com/github/advisory-database](https://github.com/github/advisory-database)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** Raw advisory data for local ingestion.<br><br>**`Notes & POIs`:** Use for mirroring; validate ecosystem/version range semantics. |
| 3 | **About GitHub Advisory Database**<br><br>**`Link(s)`:** [docs.github.com/en/code-security/concepts/vulnerability-reporting-and- management/about-the-github-advisory-database](https://docs.github.com/en/code-security/concepts/vulnerability-reporting-and-management/about-the-github-advisory-database)<br><br>**`Access / Cost`:** Free public docs | **`Relevance`:** Explains reviewed, unreviewed, & malware advisory model.<br><br>**`Notes & POIs`:** Important for confidence scoring. Reviewed vs unreviewed status affects dependability. |
| 4 | **GitHub Security Advisory GraphQL object**<br><br>**`Link(s)`:** [docs.github.com/en/graphql/reference/objects#securityadvisory](https://docs.github.com/en/graphql/reference/objects#securityadvisory)<br><br>**`Access / Cost`:** Free docs; API usage may require GitHub auth token | **`Relevance`:** Programmatic advisory metadata access via GraphQL.<br><br>**`Notes & POIs`:** Useful for complex filtered queries. Requires API authentication for robust use. |
| 5 | **GitHub REST API - global security advisories**<br><br>**`Link(s)`:** [docs.github.com/en/rest/security-advisories/global-advisories](https://docs.github.com/en/rest/security-advisories/global-advisories)<br><br>**`Access / Cost`:** Free public API; auth recommended for higher rate limits | **`Relevance`:** REST access for listing & retrieving global security advisories.<br><br>**`Notes & POIs`:** Easier to integrate than GraphQL for many ingestion jobs. |
| 6 | **GitHub REST API - security advisories root**<br><br>**`Link(s)`:** [docs.github.com/en/rest/security-advisories](https://docs.github.com/en/rest/security-advisories)<br><br>**`Access / Cost`:** Free public docs; some repository endpoints require permissions | **`Relevance`:** Root documentation for global & repository security advisory endpoints.<br><br>**`Notes & POIs`:** Use to distinguish global advisories from repo-private advisories. |
| 7 | **GitHub Dependabot alerts REST API**<br><br>**`Link(s)`:** [docs.github.com/en/rest/dependabot/alerts](https://docs.github.com/en/rest/dependabot/alerts)<br><br>**`Access / Cost`:** Requires GitHub account, repository access, & relevant permissions | **`Relevance`:** Repository-specific vulnerability exposure from dependency graph.<br><br>**`Notes & POIs`:** Requires repo access. Useful for actual asset exposure, not just global vulnerability existence. |
| 8 | **Dependabot supported ecosystems**<br><br>**`Link(s)`:** [docs.github.com/en/code-security/reference/supply-chain- security/supported-ecosystems-and-repositories](https://docs.github.com/en/code-security/reference/supply-chain-security/supported-ecosystems-and-repositories)<br><br>**`Access / Cost`:** Free public docs | **`Relevance`:** Supported ecosystem list for GitHub dependency graph & alerts.<br><br>**`Notes & POIs`:** Coverage constraints impact blind spots in detection. |
| 9 | GitHub malware advisories | [github.com/advisories?query=type%3Amalware](https://github.com/advisories?query=type%3Amalware) | Free public | Malicious package advisories. | Useful for supply-chain compromise detection beyond CVE-style vulnerabilities. |
| 10 | GitHub npm advisories | [github.com/advisories?query=ecosystem%3Anpm](https://github.com/advisories?query=ecosystem%3Anpm) | Free public | npm ecosystem advisories. | Version ranges & semver semantics are ecosystem-specific. |
| 11 | GitHub pip advisories | [github.com/advisories?query=ecosystem%3Apip](https://github.com/advisories?query=ecosystem%3Apip) | Free public | Python/PyPI advisories. | Cross-check with PyPA advisory DB & OSV. |
| 12 | GitHub Maven advisories | [github.com/advisories?query=ecosystem%3Amaven](https://github.com/advisories?query=ecosystem%3Amaven) | Free public | Maven ecosystem advisories. | Maven coordinates & shaded dependencies can complicate affectedness. |
| 13 | GitHub NuGet advisories | [github.com/advisories?query=ecosystem%3Anuget](https://github.com/advisories?query=ecosystem%3Anuget) | Free public | NuGet ecosystem advisories. | Useful for .NET dependency assessment. |
| 14 | GitHub Go advisories | [github.com/advisories?query=ecosystem%3Ago](https://github.com/advisories?query=ecosystem%3Ago) | Free public | Go ecosystem advisories. | Cross-check with official Go vulnerability DB. |
| 15 | GitHub RubyGems advisories | [github.com/advisories?query=ecosystem%3Arubygems](https://github.com/advisories?query=ecosystem%3Arubygems) | Free public | RubyGems advisories. | Cross-check with RubySec. |
| 16 | GitHub Rust advisories | [github.com/advisories?query=ecosystem%3Arust](https://github.com/advisories?query=ecosystem%3Arust) | Free public | Rust crate advisories. | Cross-check with RustSec. |
| 17 | GitHub Composer advisories | [github.com/advisories?query=ecosystem%3Acomposer](https://github.com/advisories?query=ecosystem%3Acomposer) | Free public | PHP Composer advisories. | Cross-check with FriendsOfPHP & Packagist. |
| 18 | GitHub Pub advisories | [github.com/advisories?query=ecosystem%3Apub](https://github.com/advisories?query=ecosystem%3Apub) | Free public | Dart/Pub advisories. | Coverage may vary by ecosystem maturity. |
| 19 | GitHub Swift advisories | [github.com/advisories?query=ecosystem%3Aswift](https://github.com/advisories?query=ecosystem%3Aswift) | Free public | Swift package advisories. | Useful for Swift Package Manager ecosystems. |
| 20 | GitHub Erlang advisories | [github.com/advisories?query=ecosystem%3Aerlang](https://github.com/advisories?query=ecosystem%3Aerlang) | Free public | Erlang/Hex advisories. | Validate package naming conventions against Hex. |

### 8.3 Language & package ecosystem advisory databases

##### 8.3.1 Go

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **Go Vulnerability Database**<br><br>**`Link(s)`:** [vuln.go.dev](https://vuln.go.dev/)<br><br>**`Access / Cost`:** Free public / open data | **`Relevance`:** Official Go vulnerability database for Go modules.<br><br>**`Notes & POIs`:** Strong source for Go-specific affected symbols, modules, packages, & fixed versions. |
| 2 | **Go vulnerability database docs**<br><br>**`Link(s)`:** [go.dev/doc/security/vuln/database](https://go.dev/doc/security/vuln/database)<br><br>**`Access / Cost`:** Free public docs | **`Relevance`:** Explains Go vulnerability DB data model & OSV usage.<br><br>**`Notes & POIs`:** Important for correct ingestion & symbol/package-level interpretation. |
| 3 | **Go vuln browser**<br><br>**`Link(s)`:** [pkg.go.dev/vuln](https://pkg.go.dev/vuln/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Human-readable curated Go vulnerability reports.<br><br>**`Notes & POIs`:** Useful for triage & manual review. |
| 4 | **Go vuln tooling**<br><br>**`Link(s)`:** [pkg.go.dev/golang.org/x/vuln/cmd/govulncheck](https://pkg.go.dev/golang.org/x/vuln/cmd/govulncheck)<br><br>**`Access / Cost`:** Free / open-source Go module | **`Relevance`:** Go source/binary vulnerability checking.<br><br>**`Notes & POIs`:** Can reduce false positives by analyzing call reachability in Go code. |

##### 8.3.2 Rust

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **RustSec**<br><br>**`Link(s)`:** [rustsec.org](https://rustsec.org/)<br><br>**`Access / Cost`:** Free public / open-source ecosystem | **`Relevance`:** Rust crate advisory ecosystem.<br><br>**`Notes & POIs`:** Often includes Rust-specific unsoundness, yanked crates, & ecosystem-specific risk. |
| 2 | **RustSec advisory DB repo**<br><br>**`Link(s)`:** [github.com/RustSec/advisory-db](https://github.com/RustSec/advisory-db)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** Machine-ingestible Rust advisories.<br><br>**`Notes & POIs`:** Good for local ingestion & cargo-audit compatible workflows. |
| 3 | **RustSec advisories browser**<br><br>**`Link(s)`:** [rustsec.org/advisories](https://rustsec.org/advisories/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Human-browsable Rust advisories.<br><br>**`Notes & POIs`:** Useful for manual triage. |
| 4 | **cargo-audit**<br><br>**`Link(s)`:** [github.com/RustSec/rustsec/tree/main/cargo-audit](https://github.com/RustSec/rustsec/tree/main/cargo-audit)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** RustSec-based vulnerability scanner.<br><br>**`Notes & POIs`:** Reference implementation for Rust dependency scanning. |

##### 8.3.3 Python / PyPI

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **PyPA advisory database**<br><br>**`Link(s)`:** [github.com/pypa/advisory-database](https://github.com/pypa/advisory-database)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** Python/PyPI advisory source.<br><br>**`Notes & POIs`:** Use with OSV & GitHub advisories for better Python coverage. |
| 2 | **PyPI security page**<br><br>**`Link(s)`:** [pypi.org/security](https://pypi.org/security/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** PyPI security reporting & advisory context.<br><br>**`Notes & POIs`:** Useful for process context, not necessarily complete advisory ingestion. |
| 3 | **pip-audit**<br><br>**`Link(s)`:** [github.com/pypa/pip-audit](https://github.com/pypa/pip-audit)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** Python dependency vulnerability scanner.<br><br>**`Notes & POIs`:** Reference implementation for Python dependency assessment. |
| 4 | **Safety DB**<br><br>**`Link(s)`:** [github.com/pyupio/safety-db](https://github.com/pyupio/safety-db)<br><br>**`Access / Cost`:** Free public GitHub repo; related products may be commercial | **`Relevance`:** Historical Python advisory source.<br><br>**`Notes & POIs`:** Validate freshness & licensing before relying on it. |

##### 8.3.4 JavaScript / npm

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **npm advisories via GitHub**<br><br>**`Link(s)`:** [github.com/advisories?query=ecosystem%3Anpm](https://github.com/advisories?query=ecosystem%3Anpm)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** npm ecosystem vulnerability advisories.<br><br>**`Notes & POIs`:** Semver ranges, lockfiles, transitive dependencies, & malicious packages require careful parsing. |
| 2 | **Node.js Security Working Group**<br><br>**`Link(s)`:** [github.com/nodejs/security-wg](https://github.com/nodejs/security-wg)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** Node ecosystem security coordination & historical advisory sources.<br><br>**`Notes & POIs`:** Some historical records may be superseded by GitHub Advisory DB. |
| 3 | **npm audit docs**<br><br>**`Link(s)`:** [docs.npmjs.com/cli/commands/npm-audit](https://docs.npmjs.com/cli/commands/npm-audit)<br><br>**`Access / Cost`:** Free public docs | **`Relevance`:** Documents npm audit behavior.<br><br>**`Notes & POIs`:** Useful to understand scanner behavior, dependency tree handling, & remediation suggestions. |
| 4 | **Socket.dev security research**<br><br>**`Link(s)`:** [socket.dev/blog](https://socket.dev/blog)<br><br>**`Access / Cost`:** Free public blog; product/API features may be commercial | **`Relevance`:** Malicious package & JS supply-chain threat intel.<br><br>**`Notes & POIs`:** Research source. Validate indicators & package claims against primary registries. |

##### 8.3.5 Java / Maven / JVM

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **Sonatype OSS Index**<br><br>**`Link(s)`:** [ossindex.sonatype.org](https://ossindex.sonatype.org/)<br><br>**`Access / Cost`:** Free tier / API terms; Sonatype products may be commercial | **`Relevance`:** OSS vulnerability intelligence commonly used for Maven & other ecosystems.<br><br>**`Notes & POIs`:** Commercial/community source. Validate API terms, limits, & provenance. |
| 2 | **Sonatype vulnerability database**<br><br>**`Link(s)`:** [sonatype.com/resources/vulnerability-database](https://sonatype.com/resources/vulnerability-database)<br><br>**`Access / Cost`:** Free public search / commercial ecosystem | **`Relevance`:** Sonatype vulnerability intelligence database.<br><br>**`Notes & POIs`:** Useful for enrichment & triage, but not canonical. |
| 3 | **Maven Central**<br><br>**`Link(s)`:** [central.sonatype.com](https://central.sonatype.com/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Package identity & metadata for JVM packages.<br><br>**`Notes & POIs`:** Not a vulnerability DB, but essential for coordinate resolution & metadata. |
| 4 | **OSS Index API docs**<br><br>**`Link(s)`:** [ossindex.sonatype.org/doc/rest](https://ossindex.sonatype.org/doc/rest)<br><br>**`Access / Cost`:** Free tier / API terms | **`Relevance`:** REST API access for OSS Index.<br><br>**`Notes & POIs`:** Consider rate limits, authentication, & terms before ingestion. |

##### 8.3.6 PHP / Composer

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **FriendsOfPHP security advisories**<br><br>**`Link(s)`:** [github.com/FriendsOfPHP/security-advisories](https://github.com/FriendsOfPHP/security-advisories)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** PHP Composer package advisories.<br><br>**`Notes & POIs`:** Historical & ecosystem-specific source. Cross-check with Packagist & GHSA. |
| 2 | **Packagist security advisories API**<br><br>**`Link(s)`:** [packagist.org/apidoc#list-security-advisories](https://packagist.org/apidoc#list-security-advisories)<br><br>**`Access / Cost`:** Free public API docs / public API | **`Relevance`:** Composer package advisory API.<br><br>**`Notes & POIs`:** Direct ecosystem source for Composer package advisories. |
| 3 | **Composer audit docs**<br><br>**`Link(s)`:** [getcomposer.org/doc/03-cli.md#audit](https://getcomposer.org/doc/03-cli.md#audit)<br><br>**`Access / Cost`:** Free public docs | **`Relevance`:** Documents Composer audit behavior.<br><br>**`Notes & POIs`:** Useful for implementation parity with Composer-native workflows. |

##### 8.3.7 Ruby

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **RubySec advisory DB**<br><br>**`Link(s)`:** [github.com/rubysec/ruby-advisory-db](https://github.com/rubysec/ruby-advisory-db)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** RubyGems advisories.<br><br>**`Notes & POIs`:** Cross-check with GHSA RubyGems advisories. |
| 2 | **Bundler audit**<br><br>**`Link(s)`:** [github.com/rubysec/bundler-audit](https://github.com/rubysec/bundler-audit)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** Ruby dependency vulnerability scanner.<br><br>**`Notes & POIs`:** Reference implementation for Gemfile.lock scanning. |

##### 8.3.8 .NET / NuGet

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **NuGet advisories via GitHub**<br><br>**`Link(s)`:** [github.com/advisories?query=ecosystem%3Anuget](https://github.com/advisories?query=ecosystem%3Anuget)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** NuGet ecosystem advisories.<br><br>**`Notes & POIs`:** Use with lockfile/project metadata for actual exposure. |
| 2 | **NuGet audit docs**<br><br>**`Link(s)`:** [learn.microsoft.com/en-us/nuget/concepts/auditing-packages](https://learn.microsoft.com/en-us/nuget/concepts/auditing-packages)<br><br>**`Access / Cost`:** Free public docs | **`Relevance`:** Documents NuGet package auditing.<br><br>**`Notes & POIs`:** Useful for Microsoft ecosystem parity & remediation guidance. |

##### 8.3.9 Erlang / Elixir / Hex

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **Erlang advisories via GitHub**<br><br>**`Link(s)`:** [github.com/advisories?query=ecosystem%3Aerlang](https://github.com/advisories?query=ecosystem%3Aerlang)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Erlang/Hex advisories.<br><br>**`Notes & POIs`:** Validate ecosystem naming, package coordinates, & version semantics. |
| 2 | **Hex package manager**<br><br>**`Link(s)`:** [hex.pm](https://hex.pm/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Package registry for Erlang/Elixir packages.<br><br>**`Notes & POIs`:** Registry metadata helps resolve package identity. |
##### 8.3.10 Dart / Flutter / Pub
| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **Pub advisories via GitHub**<br><br>**`Link(s)`:** [github.com/advisories?query=ecosystem%3Apub](https://github.com/advisories?query=ecosystem%3Apub)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Dart/Pub advisories.<br><br>**`Notes & POIs`:** Coverage depends on GitHub advisory ingestion. |
| 2 | **Dart package repository**<br><br>**`Link(s)`:** [pub.dev](https://pub.dev/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Package registry for Dart/Flutter dependencies.<br><br>**`Notes & POIs`:** Useful for package identity & version metadata. |
##### 8.3.11 Swift
| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **Swift advisories via GitHub**<br><br>**`Link(s)`:** [github.com/advisories?query=ecosystem%3Aswift](https://github.com/advisories?query=ecosystem%3Aswift)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Swift ecosystem advisories.<br><br>**`Notes & POIs`:** Coverage depends on GitHub Advisory DB support. |
| 2 | **Swift Package Index**<br><br>**`Link(s)`:** [swiftpackageindex.com](https://swiftpackageindex.com/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Swift package metadata & ecosystem context.<br><br>**`Notes & POIs`:** Not a vulnerability DB, but useful for package discovery & metadata. |

> 
> #### [*Back to **`Index`***](#index)
---

## 9. Vendor, OS, distribution, container & package affectedness feeds

### 9.1 Scanner-oriented aggregators & vulnerability DB builders
| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **NeuVector vul-dbgen**<br><br>**`Link(s)`:** [github.com/neuvector/vul-dbgen](https://github.com/neuvector/vul-dbgen)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** Vulnerability DB generation source originally flagged by this project.<br><br>**`Notes & POIs`:** Useful as a reference for aggregating distro/package vulnerability feeds. |
| 2 | **NeuVector vul-source**<br><br>**`Link(s)`:** [github.com/neuvector/vul-source](https://github.com/neuvector/vul-source)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** Vulnerability source data used by NeuVector workflows.<br><br>**`Notes & POIs`:** Review for source coverage & feed normalization logic. |
| 3 | **Aqua Trivy vulnerability docs**<br><br>**`Link(s)`:** [trivy.dev/docs/latest/scanner/vulnerability](https://trivy.dev/docs/latest/scanner/vulnerability/)<br><br>**`Access / Cost`:** Free public docs | **`Relevance`:** Scanner behavior across OS packages, language packages, misconfig, Kubernetes, etc.<br><br>**`Notes & POIs`:** Useful for scanner semantics & supported target types. |
| 4 | **Trivy DB**<br><br>**`Link(s)`:** [github.com/aquasecurity/trivy-db](https://github.com/aquasecurity/trivy-db)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** Converts raw advisories into Trivy DB format.<br><br>**`Notes & POIs`:** Useful for ingestion architecture & feed normalization patterns. |
| 5 | **Trivy Java DB**<br><br>**`Link(s)`:** [github.com/aquasecurity/trivy-java-db](https://github.com/aquasecurity/trivy-java-db)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** Java-specific vulnerability database used by Trivy.<br><br>**`Notes & POIs`:** Useful for Maven/JAR matching. |
| 6 | **Trivy database configuration docs**<br><br>**`Link(s)`:** [trivy.dev/docs/latest/configuration/db](https://trivy.dev/docs/latest/configuration/db/)<br><br>**`Access / Cost`:** Free public docs | **`Relevance`:** Documents Trivy DB artifacts & configuration.<br><br>**`Notes & POIs`:** Useful for operational scanner deployment. |
| 7 | **Anchore Grype**<br><br>**`Link(s)`:** [github.com/anchore/grype](https://github.com/anchore/grype)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** Vulnerability scanner for container images & filesystems.<br><br>**`Notes & POIs`:** Useful reference for SBOM-to-vuln matching. |
| 8 | **Anchore Grype DB**<br><br>**`Link(s)`:** [github.com/anchore/grype-db](https://github.com/anchore/grype-db)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** Builds Grype vulnerability database from upstream sources.<br><br>**`Notes & POIs`:** Useful for feed normalization & source coverage comparison. |
| 9 | **Anchore Syft**<br><br>**`Link(s)`:** [github.com/anchore/syft](https://github.com/anchore/syft)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** SBOM generation for scanning & exposure matching.<br><br>**`Notes & POIs`:** Pair with Grype for inventory-to-vulnerability workflow. |
| 10 | **Quay ClairCore**<br><br>**`Link(s)`:** [github.com/quay/claircore](https://github.com/quay/claircore)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** Clair vulnerability matching engine core.<br><br>**`Notes & POIs`:** Useful for container security ingestion patterns. |
| 11 | **Clair**<br><br>**`Link(s)`:** [github.com/quay/clair](https://github.com/quay/clair)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** Container vulnerability scanner.<br><br>**`Notes & POIs`:** Compare feed matching behavior with Trivy & Grype. |
| 12 | **VulnerableCode**<br><br>**`Link(s)`:** [github.com/nexB/vulnerablecode](https://github.com/nexB/vulnerablecode)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** Open vulnerability DB aggregator.<br><br>**`Notes & POIs`:** Useful for importer coverage & open-source ingestion architecture. |
| 13 | **VulnerableCode importer docs**<br><br>**`Link(s)`:** [vulnerablecode.readthedocs.io/en/latest/importers_link.html](https://vulnerablecode.readthedocs.io/en/latest/importers_link.html)<br><br>**`Access / Cost`:** Free public docs | **`Relevance`:** Lists supported importer sources.<br><br>**`Notes & POIs`:** Good checklist for source coverage. |
| 14 | **Dependency-Track**<br><br>**`Link(s)`:** [dependencytrack.org](https://dependencytrack.org/)<br><br>**`Access / Cost`:** Free / open-source core project | **`Relevance`:** SBOM-oriented vulnerability management platform.<br><br>**`Notes & POIs`:** Useful reference for BOM ingestion & component risk tracking. |
| 15 | **Dependency-Track data sources**<br><br>**`Link(s)`:** [docs.dependencytrack.org/datasources/overview](https://docs.dependencytrack.org/datasources/overview/)<br><br>**`Access / Cost`:** Free public docs | **`Relevance`:** Documents Dependency-Track data sources.<br><br>**`Notes & POIs`:** Useful for comparing source prioritization. |
| 16 | **Dependency-Track GitHub Advisories datasource**<br><br>**`Link(s)`:** [docs.dependencytrack.org/datasources/github-advisories](https://docs.dependencytrack.org/datasources/github-advisories/)<br><br>**`Access / Cost`:** Free public docs | **`Relevance`:** Mirrors GHSA via GitHub public GraphQL API.<br><br>**`Notes & POIs`:** Useful reference for GHSA ingestion. |
| 17 | **OpenVAS / Greenbone Community Feed**<br><br>**`Link(s)`:** [www.greenbone.net/en/community-feed](https://www.greenbone.net/en/community-feed/)<br><br>**`Access / Cost`:** Free community feed; commercial Greenbone feeds/products available | **`Relevance`:** Network vulnerability test feed.<br><br>**`Notes & POIs`:** Useful for host/network exposure detection, not package-only matching. |
| 18 | **Wazuh vulnerability detector**<br><br>**`Link(s)`:** [documentation.wazuh.com/current/user-manual/capabilities/vulnerability- detection/index.html](https://documentation.wazuh.com/current/user-manual/capabilities/vulnerability-detection/index.html)<br><br>**`Access / Cost`:** Free public docs; Wazuh open-source, commercial support available | **`Relevance`:** Endpoint vulnerability detection capability.<br><br>**`Notes & POIs`:** Useful for host-level package inventory & vuln matching behavior. |
| 19 | **OSV-SCALIBR**<br><br>**`Link(s)`:** [github.com/google/osv-scalibr](https://github.com/google/osv-scalibr)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** Google library for Software Composition Analysis.<br><br>**`Notes & POIs`:** Useful for SCA implementation patterns, package/component extraction, vulnerability matching, & OSV-aligned workflows. |
| 20 | **HarborGuard**<br><br>**`Link(s)`:** [github.com/HarborGuard/HarborGuard](https://github.com/HarborGuard/HarborGuard)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** Image vulnerability scanning & patching platform with multi-tool integration.<br><br>**`Notes & POIs`:** Relevant to container/image vulnerability management, scanner orchestration, & remediation workflow automation. |

### 9.2 Red Hat / RHEL / CentOS Stream

| Sl. # | Source Title | Notes |
|---:|---|---|
| ---: | **---**<br><br>**`Link(s)`:** ---<br><br>**`Access / Cost`:** --- | **`Relevance`:** ---<br><br>**`Notes & POIs`:** --- |
| 1 | **Red Hat Security Data**<br><br>**`Link(s)`:** [access.redhat.com/security/data](https://access.redhat.com/security/data)<br><br>**`Access / Cost`:** Free public data; some product details/support content may require subscription | **`Relevance`:** Red Hat CSAF/VEX, OSV, OVAL, CVE data.<br><br>**`Notes & POIs`:** Essential for RHEL affectedness & backport-aware status. |
| 2 | **Red Hat Security Data API**<br><br>**`Link(s)`:** [docs.redhat.com/en/documentation/red_hat_security_data_api/1.0/html- single/red_hat_security_data_api/index](https://docs.redhat.com/en/documentation/red_hat_security_data_api/1.0/html-single/red_hat_security_data_api/index)<br><br>**`Access / Cost`:** Free public docs/API; support content may require subscription | **`Relevance`:** API retrieves Red Hat CVE/advisory/security data.<br><br>**`Notes & POIs`:** Prefer API for automation; handle auth/rate constraints if applicable. |
| 3 | **Red Hat CVE database**<br><br>**`Link(s)`:** [access.redhat.com/security/security-updates/#/cve](https://access.redhat.com/security/security-updates/#/cve)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Red Hat CVE lookup.<br><br>**`Notes & POIs`:** Human-facing; use data APIs for automation. |
| 4 | **Red Hat OVAL data**<br><br>**`Link(s)`:** [www.redhat.com/security/data/oval](https://www.redhat.com/security/data/oval/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** OVAL definitions for vulnerability assessment.<br><br>**`Notes & POIs`:** Useful for scanner compatibility & package-state evaluation. |
| 5 | **Red Hat CSAF/VEX guidance**<br><br>**`Link(s)`:** [redhatproductsecurity.github.io/security-data-guidelines/csaf-vex](https://redhatproductsecurity.github.io/security-data-guidelines/csaf-vex/)<br><br>**`Access / Cost`:** Free public docs | **`Relevance`:** Explains Red Hat CSAF/VEX & product/package semantics.<br><br>**`Notes & POIs`:** Important for correct interpretation of affected/not-affected states. |
| 6 | **Red Hat security advisories**<br><br>**`Link(s)`:** [access.redhat.com/security/security-updates/#/security-advisories](https://access.redhat.com/security/security-updates/#/security-advisories)<br><br>**`Access / Cost`:** Free public listing; some advisory/product support details may require subscription | **`Relevance`:** Red Hat advisory listing.<br><br>**`Notes & POIs`:** Useful for patch/remediation references. |
| 7 | **CentOS Stream security tracker**<br><br>**`Link(s)`:** [gitlab.com/redhat/centos-stream/rpms](https://gitlab.com/redhat/centos-stream/rpms)<br><br>**`Access / Cost`:** Free public GitLab | **`Relevance`:** CentOS Stream package source context.<br><br>**`Notes & POIs`:** Use carefully; package repo state differs from security advisory truth. |

### 9.3 Debian

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **Debian Security Tracker**<br><br>**`Link(s)`:** [security-tracker.debian.org](https://security-tracker.debian.org/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Debian-specific package vulnerability status.<br><br>**`Notes & POIs`:** Essential for Debian affectedness & backported patches. |
| 2 | **Debian Security Tracker JSON**<br><br>**`Link(s)`:** [security-tracker.debian.org/tracker/data/json](https://security-tracker.debian.org/tracker/data/json)<br><br>**`Access / Cost`:** Free public JSON | **`Relevance`:** Machine-readable Debian vulnerability data.<br><br>**`Notes & POIs`:** Primary automation source for Debian. |
| 3 | **Debian Security Tracker source Git**<br><br>**`Link(s)`:** [salsa.debian.org/security-tracker-team/security-tracker](https://salsa.debian.org/security-tracker-team/security-tracker)<br><br>**`Access / Cost`:** Free / open-source public Git repo | **`Relevance`:** Source repo for tracker data.<br><br>**`Notes & POIs`:** Useful for diffs, auditing, & local mirroring. |
| 4 | **Debian Security Information**<br><br>**`Link(s)`:** [www.debian.org/security](https://www.debian.org/security/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Debian security notices & process context.<br><br>**`Notes & POIs`:** Useful for advisory references & manual review. |
| 5 | **Debian Security Tracker docs**<br><br>**`Link(s)`:** [security-team.debian.org/security_tracker.html](https://security-team.debian.org/security_tracker.html)<br><br>**`Access / Cost`:** Free public docs | **`Relevance`:** Explains Debian tracker semantics.<br><br>**`Notes & POIs`:** Important for interpreting statuses like fixed, vulnerable, ignored, or postponed. |
| 6 | **Debian OVAL**<br><br>**`Link(s)`:** [www.debian.org/security/oval](https://www.debian.org/security/oval/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** OVAL data for Debian vulnerability assessment.<br><br>**`Notes & POIs`:** Useful for scanner integrations. |

### 9.4 Ubuntu / Canonical

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **Ubuntu Security Notices**<br><br>**`Link(s)`:** [ubuntu.com/security/notices](https://ubuntu.com/security/notices)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Ubuntu security notices for fixed packages.<br><br>**`Notes & POIs`:** Useful for patch references & release-specific remediation. |
| 2 | **Ubuntu CVE reports**<br><br>**`Link(s)`:** [ubuntu.com/security/cves](https://ubuntu.com/security/cves)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Ubuntu CVE tracking by package/release.<br><br>**`Notes & POIs`:** Important for Ubuntu affectedness & backport interpretation. |
| 3 | **Ubuntu OVAL**<br><br>**`Link(s)`:** [ubuntu.com/security/oval](https://ubuntu.com/security/oval)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** OVAL data for vulnerability assessment & patch status.<br><br>**`Notes & POIs`:** Useful for scanner compatibility. |
| 4 | **Ubuntu VEX data**<br><br>**`Link(s)`:** [ubuntu.com/security/vex](https://ubuntu.com/security/vex)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Ubuntu VEX data.<br><br>**`Notes & POIs`:** Useful for affected/not-affected status & scanner false-positive reduction. |
| 5 | **Ubuntu VEX docs**<br><br>**`Link(s)`:** [documentation.ubuntu.com/security/security-updates/vex](https://documentation.ubuntu.com/security/security-updates/vex/)<br><br>**`Access / Cost`:** Free public docs | **`Relevance`:** Ubuntu VEX source documentation.<br><br>**`Notes & POIs`:** Important for interpreting Canonical VEX publication model. |
| 6 | **Ubuntu Security Notices GitHub**<br><br>**`Link(s)`:** [github.com/canonical/ubuntu-security-notices](https://github.com/canonical/ubuntu-security-notices)<br><br>**`Access / Cost`:** Free public GitHub repo | **`Relevance`:** USN/LSN JSON, OSV JSON, & OpenVEX JSON formats.<br><br>**`Notes & POIs`:** Strong automation source. Preserve format-specific semantics. |
| 7 | **Ubuntu Security Tracker Git**<br><br>**`Link(s)`:** [git.launchpad.net/ubuntu-cve-tracker](https://git.launchpad.net/ubuntu-cve-tracker)<br><br>**`Access / Cost`:** Free public Git repo | **`Relevance`:** Ubuntu CVE tracker source.<br><br>**`Notes & POIs`:** Useful for local mirroring & historical diffing. |
| 8 | **Ubuntu security updates docs**<br><br>**`Link(s)`:** [documentation.ubuntu.com/security/security-updates](https://documentation.ubuntu.com/security/security-updates/)<br><br>**`Access / Cost`:** Free public docs | **`Relevance`:** Ubuntu security update documentation.<br><br>**`Notes & POIs`:** Useful for process context & VEX/OVAL interpretation. |

### 9.5 Alpine

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **Alpine SecDB**<br><br>**`Link(s)`:** [secdb.alpinelinux.org](https://secdb.alpinelinux.org/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Current Alpine machine-readable security DB.<br><br>**`Notes & POIs`:** Primary Alpine ingestion source. |
| 2 | **Alpine Security Tracker**<br><br>**`Link(s)`:** [security.alpinelinux.org](https://security.alpinelinux.org/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Tracks Alpine security issues.<br><br>**`Notes & POIs`:** Useful for human review & status context. |
| 3 | **Alpine SecDB deprecated GitHub mirror**<br><br>**`Link(s)`:** [github.com/alpinelinux/alpine-secdb](https://github.com/alpinelinux/alpine-secdb)<br><br>**`Access / Cost`:** Free public GitHub repo; deprecated | **`Relevance`:** Historical Alpine SecDB mirror.<br><br>**`Notes & POIs`:** Deprecated; do not rely on it for current ingestion. |
| 4 | **Alpine packages**<br><br>**`Link(s)`:** [pkgs.alpinelinux.org/packages](https://pkgs.alpinelinux.org/packages)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Alpine package metadata.<br><br>**`Notes & POIs`:** Not a vulnerability DB, but helps resolve package names & versions. |

### 9.6 SUSE / openSUSE

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **SUSE CSAF**<br><br>**`Link(s)`:** [www.suse.com/support/security/csaf](https://www.suse.com/support/security/csaf/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** SUSE CSAF advisory data.<br><br>**`Notes & POIs`:** Good for vendor-asserted affectedness & remediation states. |
| 2 | **SUSE CVRF / OVAL security data**<br><br>**`Link(s)`:** [www.suse.com/support/security/oval](https://www.suse.com/support/security/oval/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** SUSE OVAL/CVRF security data.<br><br>**`Notes & POIs`:** Useful for scanner compatibility & package-state evaluation. |
| 3 | **SUSE CVE pages**<br><br>**`Link(s)`:** [www.suse.com/security/cve](https://www.suse.com/security/cve/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** SUSE CVE lookup.<br><br>**`Notes & POIs`:** Human-facing; use machine-readable feeds when available. |
| 4 | **SUSE Security Advisories**<br><br>**`Link(s)`:** [www.suse.com/support/update/announcement](https://www.suse.com/support/update/announcement/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** SUSE security advisory listing.<br><br>**`Notes & POIs`:** Useful for remediation & patch references. |
| 5 | **openSUSE Security Announce**<br><br>**`Link(s)`:** [lists.opensuse.org/archives/list/security-announce@lists.opensuse.org](https://lists.opensuse.org/archives/list/security-announce@lists.opensuse.org/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** openSUSE security announcement mailing list archive.<br><br>**`Notes & POIs`:** Useful for distro-specific disclosure context. |

### 9.7 Oracle Linux

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **Oracle Security Alerts & Critical Patch Updates**<br><br>**`Link(s)`:** [www.oracle.com/security-alerts](https://www.oracle.com/security-alerts/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Oracle CPU, Security Alerts, third-party bulletins, & CVE mappings.<br><br>**`Notes & POIs`:** Oracle products often require vendor advisory interpretation beyond NVD. |
| 2 | **Oracle Linux security data**<br><br>**`Link(s)`:** [linux.oracle.com/security](https://linux.oracle.com/security/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Oracle Linux security data.<br><br>**`Notes & POIs`:** Useful for Oracle Linux affectedness. |
| 3 | **Oracle Linux OVAL**<br><br>**`Link(s)`:** [linux.oracle.com/security/oval](https://linux.oracle.com/security/oval/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Oracle Linux OVAL definitions.<br><br>**`Notes & POIs`:** Useful for scanner compatibility. |

| 4 | Oracle Linux errata | [linux.oracle.com/errata](https://linux.oracle.com/errata/) | Free public | Oracle Linux errata. | Use for patch mapping & fixed versions. |
| 5 | Oracle Linux CVE search | [linux.oracle.com/cve](https://linux.oracle.com/cve/) | Free public | Oracle Linux CVE lookup. | Human lookup source; pair with OVAL/errata for automation. |

### 9.8 Amazon Linux

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **Amazon Linux Security Center**<br><br>**`Link(s)`:** [alas.aws.amazon.com](https://alas.aws.amazon.com/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Amazon Linux security advisory portal.<br><br>**`Notes & POIs`:** Important for Amazon Linux package affectedness. |
| 2 | **Amazon Linux ALAS Explorer**<br><br>**`Link(s)`:** [explore.alas.aws.amazon.com](https://explore.alas.aws.amazon.com/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Search/explore interface for Amazon Linux advisories.<br><br>**`Notes & POIs`:** Useful for manual triage & ALAS advisory lookup. |
| 3 | **Amazon Linux 2 advisories**<br><br>**`Link(s)`:** [alas.aws.amazon.com/alas2.html](https://alas.aws.amazon.com/alas2.html)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Amazon Linux 2 advisories.<br><br>**`Notes & POIs`:** Version-specific advisory stream. |
| 4 | **Amazon Linux 2023 advisories**<br><br>**`Link(s)`:** [alas.aws.amazon.com/AL2023](https://alas.aws.amazon.com/AL2023/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Amazon Linux 2023 advisories.<br><br>**`Notes & POIs`:** Keep AL2 & AL2023 separate because package baselines differ. |
| 5 | **AWS Security Bulletins**<br><br>**`Link(s)`:** [aws.amazon.com/security/security-bulletins](https://aws.amazon.com/security/security-bulletins/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** AWS security bulletins for services & platforms.<br><br>**`Notes & POIs`:** Cloud-service affectedness may not map cleanly to package versions. |
| 6 | **Amazon Linux 2023 GitHub repository**<br><br>**`Link(s)`:** [github.com/amazonlinux/amazon-linux-2023](https://github.com/amazonlinux/amazon-linux-2023)<br><br>**`Access / Cost`:** Free public GitHub repo | **`Relevance`:** Amazon Linux 2023 project repository.<br><br>**`Notes & POIs`:** Useful for Amazon Linux 2023 package context, release notes, source/package metadata references, & distro-specific affectedness workflows. |

### 9.9 Fedora, AlmaLinux, Rocky, Arch, Gentoo

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **Fedora security updates**<br><br>**`Link(s)`:** [bodhi.fedoraproject.org/updates/?type=security](https://bodhi.fedoraproject.org/updates/?type=security)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Fedora security update advisories.<br><br>**`Notes & POIs`:** Useful for Fedora package remediation tracking. |
| 2 | **Fedora packages**<br><br>**`Link(s)`:** [packages.fedoraproject.org](https://packages.fedoraproject.org/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Fedora package metadata.<br><br>**`Notes & POIs`:** Not a vulnerability DB, but useful for package identity & version resolution. |
| 3 | **Fedora packages static - Pagure**<br><br>**`Link(s)`:** [pagure.io/fedora-packages-static](https://pagure.io/fedora-packages-static)<br><br>**`Access / Cost`:** Free public Pagure project; manually revalidate | **`Relevance`:** Fedora package-name & metadata/script reference.<br><br>**`Notes & POIs`:** Keep in link-check allowlist until manually validated; not a primary security advisory source. |
| 4 | **AlmaLinux Errata**<br><br>**`Link(s)`:** [errata.almalinux.org](https://errata.almalinux.org/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** AlmaLinux errata & security advisories.<br><br>**`Notes & POIs`:** Useful for RHEL-compatible distro assessment. |
| 5 | **AlmaLinux OSV data**<br><br>**`Link(s)`:** [github.com/AlmaLinux/osv-database](https://github.com/AlmaLinux/osv-database)<br><br>**`Access / Cost`:** Free public GitHub repo | **`Relevance`:** AlmaLinux OSV-formatted data.<br><br>**`Notes & POIs`:** Good for OSV-based pipelines. |
| 6 | **Rocky Linux security advisories**<br><br>**`Link(s)`:** [errata.build.resf.org](https://errata.build.resf.org/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Rocky Linux errata/security advisories.<br><br>**`Notes & POIs`:** Useful for RHEL-compatible distro assessment. |
| 7 | **Arch Linux Security Tracker**<br><br>**`Link(s)`:** [security.archlinux.org](https://security.archlinux.org/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Arch Linux security tracker.<br><br>**`Notes & POIs`:** Rolling-release semantics differ from fixed-release distros. |
| 8 | **Arch Linux security JSON**<br><br>**`Link(s)`:** [security.archlinux.org/json](https://security.archlinux.org/json)<br><br>**`Access / Cost`:** Free public JSON | **`Relevance`:** Machine-readable Arch security data.<br><br>**`Notes & POIs`:** Useful for automation. |
| 9 | **Gentoo GLSA**<br><br>**`Link(s)`:** [security.gentoo.org/glsa](https://security.gentoo.org/glsa/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Gentoo Linux Security Advisories.<br><br>**`Notes & POIs`:** Useful for Gentoo package affectedness. |
| 10 | **Gentoo GLSA XML**<br><br>**`Link(s)`:** [security.gentoo.org/glsa/feed.rss](https://security.gentoo.org/glsa/feed.rss)<br><br>**`Access / Cost`:** Free public RSS/XML | **`Relevance`:** Gentoo GLSA RSS/XML feed.<br><br>**`Notes & POIs`:** Useful for feed-based monitoring. |

### 9.10 Wolfi / Chainguard

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **Wolfi OS advisories**<br><br>**`Link(s)`:** [github.com/wolfi-dev/advisories](https://github.com/wolfi-dev/advisories)<br><br>**`Access / Cost`:** Free public GitHub repo | **`Relevance`:** Wolfi OS advisory data.<br><br>**`Notes & POIs`:** Important for modern minimal container images. |
| 2 | **Wolfi SecDB generator**<br><br>**`Link(s)`:** [github.com/wolfi-dev/secdb](https://github.com/wolfi-dev/secdb)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** Generates Wolfi security DBs based on Alpine secdb format.<br><br>**`Notes & POIs`:** Useful for understanding feed generation semantics. |
| 3 | **Wolfi OS feed**<br><br>**`Link(s)`:** [packages.wolfi.dev/os/security.json](https://packages.wolfi.dev/os/security.json)<br><br>**`Access / Cost`:** Free public feed | **`Relevance`:** Wolfi package security feed.<br><br>**`Notes & POIs`:** Use this for Wolfi base images. |
| 4 | **Chainguard Enterprise feed**<br><br>**`Link(s)`:** [packages.cgr.dev/chainguard/security.json](https://packages.cgr.dev/chainguard/security.json)<br><br>**`Access / Cost`:** Publicly reachable feed; may relate to commercial Chainguard product scope | **`Relevance`:** Chainguard Enterprise package security feed.<br><br>**`Notes & POIs`:** Separate from Wolfi OS feed. Confirm entitlement/licensing before commercial redistribution. |
| 5 | Chainguard security advisories docs | [edu.chainguard.dev/chainguard/chainguard-images/staying- secure/security-advisories/how-chainguard-issues](https://edu.chainguard.dev/chainguard/chainguard-images/staying-secure/security-advisories/how-chainguard-issues/) | Free public docs | Explains Chainguard advisory publication model. | Important for interpreting feed semantics & OSV/secdb transition. |
| 6 | Wolfi vulnerabilities in OSV | [osv.dev/list?ecosystem=Wolfi](https://osv.dev/list?ecosystem=Wolfi) | Free public | Wolfi ecosystem records in OSV. | Good for OSV-aligned ingestion. |
| 7 | Chainguard OSV advisory feed context | [www.chainguard.dev/unchained/chainguard-enhances-security-with- osv-advisory-feed](https://www.chainguard.dev/unchained/chainguard-enhances-security-with-osv-advisory-feed) | Free public blog | Context on Chainguard OSV advisory feed. | Blog/context source, not primary feed. |

> 
> #### [*Back to **`Index`***](#index)
---

## 10. Vendor advisories for enterprise impact assessment

### 10.1 Major OS, browser & platform vendors

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **Microsoft Security Update Guide**<br><br>**`Link(s)`:** [msrc.microsoft.com/update-guide](https://msrc.microsoft.com/update-guide)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Microsoft vulnerability advisories, CVEs, affected products, & fixes.<br><br>**`Notes & POIs`:** Critical for Windows, Office, Exchange, Azure components, & enterprise Microsoft stack. |
| 2 | **Microsoft MSRC blog**<br><br>**`Link(s)`:** [msrc.microsoft.com/blog](https://msrc.microsoft.com/blog/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Microsoft security research & advisory context.<br><br>**`Notes & POIs`:** Useful for exploitation context & urgent guidance. |
| 3 | **Microsoft Security Response Center**<br><br>**`Link(s)`:** [msrc.microsoft.com](https://msrc.microsoft.com/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Microsoft security response portal.<br><br>**`Notes & POIs`:** Entry point for MSRC resources. |
| 4 | **Apple Security Releases**<br><br>**`Link(s)`:** [support.apple.com/en-us/100100](https://support.apple.com/en-us/100100)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Apple security release index.<br><br>**`Notes & POIs`:** Important for iOS, macOS, Safari, watchOS, tvOS, & ecosystem patch tracking. |
| 5 | **Google Android Security Bulletins**<br><br>**`Link(s)`:** [source.android.com/docs/security/bulletin](https://source.android.com/docs/security/bulletin)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Android platform security bulletins.<br><br>**`Notes & POIs`:** Device/vendor patch latency may differ from bulletin availability. |
| 6 | **Google Chrome Releases**<br><br>**`Link(s)`:** [chromereleases.googleblog.com](https://chromereleases.googleblog.com/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Chrome release announcements.<br><br>**`Notes & POIs`:** Security fixes are often disclosed with delayed details. |
| 7 | **Chrome security advisories**<br><br>**`Link(s)`:** [chromereleases.googleblog.com/search/label/Security](https://chromereleases.googleblog.com/search/label/Security)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Chrome security-specific release posts.<br><br>**`Notes & POIs`:** Good for urgent browser vulnerability tracking. |
| 8 | **Chromium issue tracker**<br><br>**`Link(s)`:** [issues.chromium.org](https://issues.chromium.org/)<br><br>**`Access / Cost`:** Free public for public issues; restricted issues may require access | **`Relevance`:** Chromium issue tracking.<br><br>**`Notes & POIs`:** Security bugs may have restricted visibility until disclosure. |
| 9 | **Mozilla Security Advisories**<br><br>**`Link(s)`:** [www.mozilla.org/en-US/security/advisories](https://www.mozilla.org/en-US/security/advisories/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Mozilla security advisories.<br><br>**`Notes & POIs`:** Important for Firefox, Thunderbird, & related products. |
| 10 | **Mozilla Foundation Security Advisories**<br><br>**`Link(s)`:** [www.mozilla.org/en-US/security/known-vulnerabilities](https://www.mozilla.org/en-US/security/known-vulnerabilities/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Mozilla known vulnerabilities index.<br><br>**`Notes & POIs`:** Useful for historical advisory lookup. |
| 11 | **Google Cloud Security Bulletins**<br><br>**`Link(s)`:** [cloud.google.com/support/bulletins](https://cloud.google.com/support/bulletins)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Google Cloud service/product security bulletins.<br><br>**`Notes & POIs`:** Cloud advisories often require service-specific interpretation. |
| 12 | **Kubernetes Security Announcements**<br><br>**`Link(s)`:** [groups.google.com/g/kubernetes-security-announce](https://groups.google.com/g/kubernetes-security-announce)<br><br>**`Access / Cost`:** Free public Google Group | **`Relevance`:** Kubernetes security announcement mailing list.<br><br>**`Notes & POIs`:** Authoritative operational alerting channel for Kubernetes CVEs. |
| 13 | **Kubernetes official CVE feed**<br><br>**`Link(s)`:** [kubernetes.io/docs/reference/issues-security/official-cve-feed](https://kubernetes.io/docs/reference/issues-security/official-cve-feed/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Official Kubernetes CVE feed reference.<br><br>**`Notes & POIs`:** Useful for automation & Kubernetes-specific CVE tracking. |
| 14 | **Kubernetes security & disclosure**<br><br>**`Link(s)`:** [kubernetes.io/docs/reference/issues-security/security](https://kubernetes.io/docs/reference/issues-security/security/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Kubernetes security disclosure process.<br><br>**`Notes & POIs`:** Useful for understanding embargo, disclosure, & patch handling. |

### 10.2 Enterprise infrastructure vendors

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **Cisco Security Advisories**<br><br>**`Link(s)`:** [sec.cloudapps.cisco.com/security/center/publicationListing.x](https://sec.cloudapps.cisco.com/security/center/publicationListing.x)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Cisco product advisories, affected versions, fixed versions, & workarounds.<br><br>**`Notes & POIs`:** Critical for network infrastructure exposure. |
| 2 | **VMware / Broadcom Security Advisories**<br><br>**`Link(s)`:** [support.broadcom.com/web/ecx/security-advisory](https://support.broadcom.com/web/ecx/security-advisory)<br><br>**`Access / Cost`:** Free public listing; some support downloads may require entitlement | **`Relevance`:** VMware/Broadcom security advisories.<br><br>**`Notes & POIs`:** Important for virtualization, ESXi, vCenter, & enterprise infrastructure. |
| 3 | **Palo Alto Networks Security Advisories**<br><br>**`Link(s)`:** [security.paloaltonetworks.com](https://security.paloaltonetworks.com/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** PAN-OS & Palo Alto product advisories.<br><br>**`Notes & POIs`:** Often includes exploited-in-the-wild notes & mitigation guidance. |
| 4 | **Fortinet PSIRT Advisories**<br><br>**`Link(s)`:** [www.fortiguard.com/psirt](https://www.fortiguard.com/psirt)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Fortinet product advisories.<br><br>**`Notes & POIs`:** Critical for perimeter devices; exploitability can change quickly. |
| 5 | **Ivanti Security Advisories**<br><br>**`Link(s)`:** [forums.ivanti.com/s/security-advisory](https://forums.ivanti.com/s/security-advisory)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Ivanti security advisories.<br><br>**`Notes & POIs`:** Track emergency advisories closely due to recurring exploitation patterns. |
| 6 | **Citrix Security Bulletins**<br><br>**`Link(s)`:** [support.citrix.com/securitybulletins](https://support.citrix.com/securitybulletins)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Citrix product security bulletins.<br><br>**`Notes & POIs`:** Useful for exposed remote access infrastructure. |
| 7 | **F5 Security Advisories**<br><br>**`Link(s)`:** [my.f5.com/manage/s/solutions?series=Security_Advisory](https://my.f5.com/manage/s/solutions?series=Security_Advisory)<br><br>**`Access / Cost`:** Free public listing; some support content may require account | **`Relevance`:** F5 product security advisories.<br><br>**`Notes & POIs`:** Product modules/configuration affect exploitability. |
| 8 | **Juniper Security Advisories**<br><br>**`Link(s)`:** [supportportal.juniper.net/s/global-search/%40uri#sort=relevancy&f:ctype= [Security%20Advisories]](https://supportportal.juniper.net/s/global-search/%40uri#sort=relevancy&f:ctype=%5BSecurity%20Advisories%5D)<br><br>**`Access / Cost`:** Free public listing; support portal may require account for some content | **`Relevance`:** Juniper security advisory listing.<br><br>**`Notes & POIs`:** Useful for network infrastructure patching. |
| 9 | **Dell Security Advisories**<br><br>**`Link(s)`:** [www.dell.com/support/security](https://www.dell.com/support/security)<br><br>**`Access / Cost`:** Free public listing; downloads/support may require entitlement | **`Relevance`:** Dell product security advisories.<br><br>**`Notes & POIs`:** Covers firmware, hardware, drivers, & enterprise products. |
| 10 | **HPE Security Bulletins**<br><br>**`Link(s)`:** [support.hpe.com/connect/s/securitybulletins](https://support.hpe.com/connect/s/securitybulletins)<br><br>**`Access / Cost`:** Free public listing; support portal may require account/entitlement | **`Relevance`:** HPE security bulletins.<br><br>**`Notes & POIs`:** May require product filtering & support portal navigation. |
| 11 | **Lenovo Product Security Advisories**<br><br>**`Link(s)`:** [support.lenovo.com/us/en/product_security/home](https://support.lenovo.com/us/en/product_security/home)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Lenovo product security advisories.<br><br>**`Notes & POIs`:** Useful for firmware & device fleet management. |
| 12 | **IBM PSIRT**<br><br>**`Link(s)`:** [www.ibm.com/support/pages/ibm-psirt](https://www.ibm.com/support/pages/ibm-psirt)<br><br>**`Access / Cost`:** Free public listing; some IBM support docs may require entitlement | **`Relevance`:** IBM product security incident response.<br><br>**`Notes & POIs`:** Useful for IBM software/hardware exposure. |
| 13 | **SAP Security Notes**<br><br>**`Link(s)`:** [support.sap.com/en/my-support/knowledge-base/security-notes-news.html](https://support.sap.com/en/my-support/knowledge-base/security-notes-news.html)<br><br>**`Access / Cost`:** SAP support account / subscription often required for full Security Notes | **`Relevance`:** SAP security notes & patch-day guidance.<br><br>**`Notes & POIs`:** May require SAP support access for full note details. |
| 14 | **Adobe Security Bulletins**<br><br>**`Link(s)`:** [helpx.adobe.com/security.html](https://helpx.adobe.com/security.html)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Adobe security bulletins.<br><br>**`Notes & POIs`:** Important for client-side & enterprise Adobe software. |
| 15 | **Oracle Critical Patch Updates**<br><br>**`Link(s)`:** [www.oracle.com/security-alerts](https://www.oracle.com/security-alerts/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Oracle CPU, Security Alerts, & CVE mappings.<br><br>**`Notes & POIs`:** Oracle advisories often bundle many products; mapping requires product/version context. |
| 16 | Atlassian Security Advisories | [www.atlassian.com/trust/security/advisories](https://www.atlassian.com/trust/security/advisories) | Free public | Atlassian product advisories. | Important for exposed collaboration/dev tooling like Confluence & Jira. |
| 17 | Elastic Security Announcements | [discuss.elastic.co/c/announcements/security-announcements/31](https://discuss.elastic.co/c/announcements/security-announcements/31) | Free public forum | Elastic security announcements. | Useful for Elasticsearch/Kibana stack. |
| 18 | HashiCorp Security | [www.hashicorp.com/security](https://www.hashicorp.com/security) | Free public; enterprise support separate | HashiCorp security advisories & disclosure policy. | Relevant for Terraform, Vault, Consul, Nomad. |
| 19 | GitLab Security Releases | [about.gitlab.com/releases/categories/releases](https://about.gitlab.com/releases/categories/releases/) | Free public | GitLab release posts, including security releases. | Security releases may include multiple CVEs & version-specific patches. |
| 20 | Jenkins Security Advisories | [www.jenkins.io/security/advisories](https://www.jenkins.io/security/advisories/) | Free public | Jenkins core & plugin advisories. | Plugin affectedness is critical; inventory plugin versions. |
| 21 | Apache Security Reports | [www.apache.org/security](https://www.apache.org/security/) | Free public | Apache project security reports & process. | Many Apache projects have project-specific advisory pages. |
| 22 | Eclipse Security Advisories | [www.eclipse.org/security](https://www.eclipse.org/security/) | Free public | Eclipse project security advisories. | Useful for Java tooling & Eclipse projects. |
| 23 | WordPress Security Releases | [wordpress.org/news/category/security](https://wordpress.org/news/category/security/) | Free public | WordPress security release announcements. | Plugin/theme ecosystem needs separate assessment. |
| 24 | Drupal Security Advisories | [www.drupal.org/security](https://www.drupal.org/security) | Free public | Drupal core & contributed project advisories. | Module inventory matters for affectedness. |
| 25 | OpenSSL Vulnerabilities | [www.openssl.org/news/vulnerabilities.html](https://www.openssl.org/news/vulnerabilities.html) | Free public | OpenSSL vulnerability list. | Critical transitive dependency in many systems; patch status depends on bundled library versions. |
| 26 | OpenSSH release notes | [www.openssh.com/releasenotes.html](https://www.openssh.com/releasenotes.html) | Free public | OpenSSH release notes. | Security-relevant changes may appear in release notes. |
| 27 | curl security advisories | [curl.se/docs/security.html](https://curl.se/docs/security.html) | Free public | curl/libcurl security advisories. | Important for widely embedded dependency exposure. |

### 10.3 Cloud provider security bulletins
| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **AWS Security Bulletins**<br><br>**`Link(s)`:** [aws.amazon.com/security/security-bulletins](https://aws.amazon.com/security/security-bulletins/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** AWS service/product security bulletins.<br><br>**`Notes & POIs`:** Cloud provider advisories often require service/configuration context. |
| 2 | **AWS Security Blog**<br><br>**`Link(s)`:** [aws.amazon.com/blogs/security](https://aws.amazon.com/blogs/security/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** AWS security guidance & incident context.<br><br>**`Notes & POIs`:** Good for mitigation patterns, not canonical CVE data. |
| 3 | **Google Cloud Security Bulletins**<br><br>**`Link(s)`:** [cloud.google.com/support/bulletins](https://cloud.google.com/support/bulletins)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Google Cloud security bulletins.<br><br>**`Notes & POIs`:** Use with asset inventory & managed service exposure. |
| 4 | **Google Cloud Security Blog**<br><br>**`Link(s)`:** [cloud.google.com/blog/products/identity-security](https://cloud.google.com/blog/products/identity-security)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Google Cloud identity/security blog.<br><br>**`Notes & POIs`:** Useful for operational context & mitigations. |
| 5 | **Microsoft Azure security / MSRC**<br><br>**`Link(s)`:** [msrc.microsoft.com/update-guide](https://msrc.microsoft.com/update-guide)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Microsoft/Azure-related security updates.<br><br>**`Notes & POIs`:** Azure service advisories may require separate portal/status checks. |
| 6 | **Azure updates**<br><br>**`Link(s)`:** [azure.microsoft.com/en-us/updates](https://azure.microsoft.com/en-us/updates/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Azure product update feed.<br><br>**`Notes & POIs`:** Not purely security-specific; filter carefully. |
| 7 | **Oracle Cloud security**<br><br>**`Link(s)`:** [www.oracle.com/security-alerts](https://www.oracle.com/security-alerts/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Oracle cloud/product security alerts.<br><br>**`Notes & POIs`:** Oracle advisories often span cloud & on-prem products. |
| 8 | IBM Cloud security bulletins | [cloud.ibm.com/status/security](https://cloud.ibm.com/status/security) | Free public | IBM Cloud security bulletins. | Useful for managed service exposure. |

> 
> #### [*Back to **`Index`***](#index)
---

## 11. ICS, OT, IoT, embedded & medical-device sources

### 11.1 CISA ICS / medical

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **CISA ICS Advisories**<br><br>**`Link(s)`:** [www.cisa.gov/news-events/ics-advisories](https://www.cisa.gov/news-events/ics-advisories)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Industrial Control System advisories.<br><br>**`Notes & POIs`:** Critical for OT/ICS environments where patching constraints differ from IT. |
| 2 | **CISA ICS Medical Advisories**<br><br>**`Link(s)`:** [www.cisa.gov/news-events/ics-medical-advisories](https://www.cisa.gov/news-events/ics-medical-advisories)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Medical device security advisories.<br><br>**`Notes & POIs`:** Impact includes patient safety, regulatory, & operational risk. |
| 3 | **CISA cybersecurity advisories**<br><br>**`Link(s)`:** [www.cisa.gov/cybersecurity-advisories](https://www.cisa.gov/cybersecurity-advisories)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** CISA cybersecurity advisory hub.<br><br>**`Notes & POIs`:** Broader than ICS; use for campaigns & emergent threats. |
| 4 | **ICS-CERT advisories archive**<br><br>**`Link(s)`:** [www.cisa.gov/news-events/ics-advisories](https://www.cisa.gov/news-events/ics-advisories)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** ICS-CERT advisory archive path.<br><br>**`Notes & POIs`:** Same URL as ICS advisories, preserved for historical naming. |
| 5 | **CISA ICS recommended practices**<br><br>**`Link(s)`:** [www.cisa.gov/resources-tools/resources/ics-recommended-practices](https://www.cisa.gov/resources-tools/resources/ics-recommended-practices)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Recommended practices for ICS security.<br><br>**`Notes & POIs`:** Useful for mitigation where patching is delayed or impossible. |

### 11.2 OT / ICS vendor advisories

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **Siemens ProductCERT**<br><br>**`Link(s)`:** [cert-portal.siemens.com/productcert](https://cert-portal.siemens.com/productcert/)<br><br>**`Access / Cost`:** Free public advisories; some support downloads may require entitlement | **`Relevance`:** Siemens product security advisories.<br><br>**`Notes & POIs`:** Critical for industrial environments. |
| 2 | **Schneider Electric Security Notifications**<br><br>**`Link(s)`:** [www.se.com/ww/en/work/support/cybersecurity/security- notifications.jsp](https://www.se.com/ww/en/work/support/cybersecurity/security-notifications.jsp)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Schneider Electric security notifications.<br><br>**`Notes & POIs`:** Product model & firmware version matter heavily. |
| 3 | **Rockwell Automation Security Advisories**<br><br>**`Link(s)`:** [www.rockwellautomation.com/en-us/support/product/product- security-advisories.html](https://www.rockwellautomation.com/en-us/support/product/product-security-advisories.html)<br><br>**`Access / Cost`:** Free public listing; support downloads may require entitlement | **`Relevance`:** Rockwell Automation product advisories.<br><br>**`Notes & POIs`:** Operational constraints may affect remediation. |
| 4 | **Honeywell Product Security**<br><br>**`Link(s)`:** [www.honeywell.com/us/en/product-security](https://www.honeywell.com/us/en/product-security)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Honeywell product security advisories.<br><br>**`Notes & POIs`:** Useful for OT product risk. |
| 5 | **Philips Product Security**<br><br>**`Link(s)`:** [www.philips.com/a-w/security/security-advisories.html](https://www.philips.com/a-w/security/security-advisories.html)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Philips medical/product security advisories.<br><br>**`Notes & POIs`:** Patient safety & regulatory implications may affect severity assessment. |
| 6 | **GE Vernova Product Security**<br><br>**`Link(s)`:** [www.gevernova.com/product-security](https://www.gevernova.com/product-security)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** GE Vernova product security.<br><br>**`Notes & POIs`:** Important for energy/industrial systems. |
| 7 | **ABB Cyber Security Alerts**<br><br>**`Link(s)`:** [global.abb/group/en/technology/cyber-security/alerts-and-notifications](https://global.abb/group/en/technology/cyber-security/alerts-and-notifications)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** ABB cyber security alerts & notifications.<br><br>**`Notes & POIs`:** Product-specific affectedness matters. |
| 8 | **Yokogawa Security Advisories**<br><br>**`Link(s)`:** [www.yokogawa.com/library/resources/white-papers/yokogawa-security- advisory-report-list](https://www.yokogawa.com/library/resources/white-papers/yokogawa-security-advisory-report-list/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Yokogawa advisory report list.<br><br>**`Notes & POIs`:** Useful for OT control systems. |
| 9 | **Mitsubishi Electric PSIRT**<br><br>**`Link(s)`:** [www.mitsubishielectric.com/en/psirt/vulnerability](https://www.mitsubishielectric.com/en/psirt/vulnerability/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Mitsubishi Electric vulnerability advisories.<br><br>**`Notes & POIs`:** Important for industrial equipment & automation. |
| 10 | **Johnson Controls Product Security Advisories**<br><br>**`Link(s)`:** [www.johnsoncontrols.com/cyber-solutions/security-advisories](https://www.johnsoncontrols.com/cyber-solutions/security-advisories)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Johnson Controls security advisories.<br><br>**`Notes & POIs`:** Relevant to building management & OT environments. |

### 11.3 IoT / embedded

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **CERT/CC Vulnerability Notes**<br><br>**`Link(s)`:** [www.kb.cert.org/vuls](https://www.kb.cert.org/vuls/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Coordinated disclosure notes, often with embedded/IoT affected vendors.<br><br>**`Notes & POIs`:** Useful when many vendors share a vulnerable component. |
| 2 | **IoT Security Foundation**<br><br>**`Link(s)`:** [www.iotsecurityfoundation.org](https://www.iotsecurityfoundation.org/)<br><br>**`Access / Cost`:** Free public resources; membership options may exist | **`Relevance`:** IoT security guidance & resources.<br><br>**`Notes & POIs`:** Not a vulnerability feed, but useful for control mapping. |
| 3 | **Firmware Analysis and Comparison Tool - FACT**<br><br>**`Link(s)`:** [github.com/fkie-cad/FACT_core](https://github.com/fkie-cad/FACT_core)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** Firmware analysis platform.<br><br>**`Notes & POIs`:** Useful for extracting components & embedded vuln detection. |
| 4 | **EMBA firmware analyzer**<br><br>**`Link(s)`:** [github.com/e-m-b-a/emba](https://github.com/e-m-b-a/emba)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** Firmware analyzer for embedded Linux/IoT.<br><br>**`Notes & POIs`:** Useful for SBOM-like extraction & vulnerability assessment. |
| 5 | **Binwalk**<br><br>**`Link(s)`:** [github.com/ReFirmLabs/binwalk](https://github.com/ReFirmLabs/binwalk)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** Firmware extraction & analysis tool.<br><br>**`Notes & POIs`:** Useful precursor for embedded component discovery. |

> 
> #### [*Back to **`Index`***](#index)
---

---

## E. Security Supply Chain Evidence: SBOM, VEX, Provenance & Malicious Package Risk

## 12. SBOM, package identity, VEX & advisory exchange standards

### 12.1 SBOM standards

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **CycloneDX specification overview**<br><br>**`Link(s)`:** [cyclonedx.org/specification/overview](https://cyclonedx.org/specification/overview/)<br><br>**`Access / Cost`:** Free / open standard | **`Relevance`:** SBOM, SaaSBOM, BOM, VEX, vulnerability & component metadata standard.<br><br>**`Notes & POIs`:** Good fit for vulnerability management workflows due to vulnerability & VEX support. |
| 2 | **CycloneDX GitHub**<br><br>**`Link(s)`:** [github.com/CycloneDX/specification](https://github.com/CycloneDX/specification)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** CycloneDX specification source repository.<br><br>**`Notes & POIs`:** Use for versioned spec tracking. |
| 3 | **CycloneDX VEX**<br><br>**`Link(s)`:** [cyclonedx.org/capabilities/vex](https://cyclonedx.org/capabilities/vex/)<br><br>**`Access / Cost`:** Free public docs | **`Relevance`:** CycloneDX VEX capability documentation.<br><br>**`Notes & POIs`:** Useful for affected/not-affected communication. |
| 4 | **SPDX specifications**<br><br>**`Link(s)`:** [spdx.dev/specifications](https://spdx.dev/specifications/)<br><br>**`Access / Cost`:** Free / open standard | **`Relevance`:** SPDX specifications for software bills of materials & package metadata.<br><br>**`Notes & POIs`:** SPDX is widely used for license/package metadata & supply-chain exchange. |
| 5 | **SPDX 3.0.1 spec**<br><br>**`Link(s)`:** [spdx.github.io/spdx-spec/v3.0.1](https://spdx.github.io/spdx-spec/v3.0.1/)<br><br>**`Access / Cost`:** Free public docs | **`Relevance`:** SPDX 3.0.1 specification.<br><br>**`Notes & POIs`:** Track spec version compatibility in parsers. |
| 6 | **SPDX package URL property**<br><br>**`Link(s)`:** [spdx.github.io/spdx-spec/v3.0.1/model/Software/Properties/packageUrl](https://spdx.github.io/spdx-spec/v3.0.1/model/Software/Properties/packageUrl/)<br><br>**`Access / Cost`:** Free public docs | **`Relevance`:** SPDX support for package URL property.<br><br>**`Notes & POIs`:** Important for PURL-based vulnerability matching. |
| 7 | **SPDX GitHub**<br><br>**`Link(s)`:** [github.com/spdx/spdx-spec](https://github.com/spdx/spdx-spec)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** SPDX specification repository.<br><br>**`Notes & POIs`:** Use for release tracking & schema/source inspection. |
| 8 | **NTIA SBOM resources**<br><br>**`Link(s)`:** [www.ntia.gov/page/software-bill-materials](https://www.ntia.gov/page/software-bill-materials)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** SBOM policy & foundational resources.<br><br>**`Notes & POIs`:** Useful for governance & compliance context. |
| 9 | **CISA SBOM**<br><br>**`Link(s)`:** [www.cisa.gov/sbom](https://www.cisa.gov/sbom)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** CISA SBOM guidance & resources.<br><br>**`Notes & POIs`:** Useful for U.S. public-sector & enterprise SBOM program alignment. |


### 12.2 Package & software identity

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **Package URL - PURL spec**<br><br>**`Link(s)`:** [github.com/package-url/purl-spec](https://github.com/package-url/purl-spec)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** Standard package identifier used in SBOMs & vulnerability DBs.<br><br>**`Notes & POIs`:** Crucial for OSV & package ecosystem matching. |
| 2 | **PURL types**<br><br>**`Link(s)`:** [github.com/package-url/purl-spec/blob/master/PURL-TYPES.rst](https://github.com/package-url/purl-spec/blob/master/PURL-TYPES.rst)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Defines PURL types per ecosystem.<br><br>**`Notes & POIs`:** Helps normalize ecosystem-specific package coordinates. |
| 3 | **CPE specification / dictionary**<br><br>**`Link(s)`:** [nvd.nist.gov/products/cpe](https://nvd.nist.gov/products/cpe)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Product naming & CPE dictionary.<br><br>**`Notes & POIs`:** Useful for product/platform matching, but can be imprecise for packages. |
| 4 | **NVD CPE API**<br><br>**`Link(s)`:** [nvd.nist.gov/developers/products](https://nvd.nist.gov/developers/products)<br><br>**`Access / Cost`:** Free public; optional free API key for higher rate limits | **`Relevance`:** Programmatic CPE dictionary access.<br><br>**`Notes & POIs`:** Required for automated CPE matching workflows. |
| 5 | **SWID tags - NIST**<br><br>**`Link(s)`:** [csrc.nist.gov/projects/software-identification-swid](https://csrc.nist.gov/projects/software-identification-swid)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Software Identification Tags for installed software identity.<br><br>**`Notes & POIs`:** Useful in enterprise asset inventory & compliance. |
| 6 | **GS1 Digital Link / identifiers**<br><br>**`Link(s)`:** [www.gs1.org/standards/gs1-digital-link](https://www.gs1.org/standards/gs1-digital-link)<br><br>**`Access / Cost`:** Free public standard docs; GS1 membership may apply for assigned identifiers | **`Relevance`:** Optional identity standard for physical/embedded supply chains.<br><br>**`Notes & POIs`:** Not a vulnerability standard, but can matter in hardware/product traceability. |
| 7 | **Software Heritage IDs**<br><br>**`Link(s)`:** [www.swhid.org](https://www.swhid.org/)<br><br>**`Access / Cost`:** Free public / open | **`Relevance`:** Persistent source- code artifact identity.<br><br>**`Notes & POIs`:** Useful for source provenance & precise code artifact references. |

### 12.3 Advisory exchange, CSAF & VEX

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **OASIS CSAF 2.0 specification**<br><br>**`Link(s)`:** [docs.oasis-open.org/csaf/csaf/v2.0/os/csaf-v2.0-os.html](https://docs.oasis-open.org/csaf/csaf/v2.0/os/csaf-v2.0-os.html)<br><br>**`Access / Cost`:** Free / open standard | **`Relevance`:** Common Security Advisory Framework for structured advisories.<br><br>**`Notes & POIs`:** CSAF can express product status, remediation, impact, & VEX-like affectedness. |
| 2 | **CSAF home**<br><br>**`Link(s)`:** [www.csaf.io](https://www.csaf.io/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** CSAF ecosystem & tooling hub.<br><br>**`Notes & POIs`:** Good starting point for CSAF adoption. |
| 3 | **OpenVEX specification**<br><br>**`Link(s)`:** [github.com/openvex/spec](https://github.com/openvex/spec)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** Minimal JSON-LD VEX format based on CISA VEX requirements.<br><br>**`Notes & POIs`:** Useful for communicating not- affected/fixed/affected status. |
| 4 | **OpenVEX project page**<br><br>**`Link(s)`:** [openssf.org/projects/openvex](https://openssf.org/projects/openvex/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** OpenSSF project page for OpenVEX.<br><br>**`Notes & POIs`:** Project-level overview. |
| 5 | **CISA Minimum Requirements for VEX**<br><br>**`Link(s)`:** [www.cisa.gov/sites/default/files/2023-04/minimum-requirements-for- vex-508c.pdf](https://www.cisa.gov/sites/default/files/2023-04/minimum-requirements-for-vex-508c.pdf)<br><br>**`Access / Cost`:** Free public PDF | **`Relevance`:** Baseline VEX requirements.<br><br>**`Notes & POIs`:** Useful for evaluating VEX completeness. |
| 6 | **OpenSSF VDR, VEX, OpenVEX & CSAF explainer**<br><br>**`Link(s)`:** [openssf.org/blog/2023/09/07/vdr-vex-openvex-and-csaf](https://openssf.org/blog/2023/09/07/vdr-vex-openvex-and-csaf/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Explains VDR, VEX, OpenVEX, & CSAF.<br><br>**`Notes & POIs`:** Useful for conceptual alignment & terminology. |
| 7 | **Red Hat CSAF/VEX guidance**<br><br>**`Link(s)`:** [redhatproductsecurity.github.io/security-data-guidelines/csaf-vex](https://redhatproductsecurity.github.io/security-data-guidelines/csaf-vex/)<br><br>**`Access / Cost`:** Free public docs | **`Relevance`:** Red Hat CSAF/VEX semantics & usage guidance.<br><br>**`Notes & POIs`:** Important for vendor-specific interpretation. |
| 8 | **Ubuntu VEX**<br><br>**`Link(s)`:** [ubuntu.com/security/vex](https://ubuntu.com/security/vex)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Ubuntu VEX data entry point.<br><br>**`Notes & POIs`:** Useful for Ubuntu affectedness & false-positive reduction. |
| 9 | **Canonical Ubuntu Security Notices repo - OSV & OpenVEX**<br><br>**`Link(s)`:** [github.com/canonical/ubuntu-security-notices](https://github.com/canonical/ubuntu-security-notices)<br><br>**`Access / Cost`:** Free public GitHub repo | **`Relevance`:** Canonical USN/LSN, OSV, & OpenVEX JSON data.<br><br>**`Notes & POIs`:** Strong machine-readable source for Ubuntu security status. |

> 
> #### [*Back to **`Index`***](#index)
---

## 13. Malicious package, supply-chain compromise & package reputation sources

### 13.1 Malicious package databases

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **OpenSSF Malicious Packages repository**<br><br>**`Link(s)`:** [github.com/ossf/malicious-packages](https://github.com/ossf/malicious-packages)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** Public malicious package reports consumable via OSV format.<br><br>**`Notes & POIs`:** Covers malicious packages, which may not be CVEs. |
| 2 | **OpenSSF Malicious Packages announcement**<br><br>**`Link(s)`:** [openssf.org/blog/2023/10/12/introducing-openssfs-malicious- packages-repository](https://openssf.org/blog/2023/10/12/introducing-openssfs-malicious-packages-repository/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Explains the public DB for malicious package reports.<br><br>**`Notes & POIs`:** Context source, not the primary data feed. |
| 3 | **OpenSSF Package Analysis**<br><br>**`Link(s)`:** [openssf.org/package-analysis](https://openssf.org/package-analysis/)<br><br>**`Access / Cost`:** Free public project info | **`Relevance`:** Detects malicious package behavior & informs package consumers.<br><br>**`Notes & POIs`:** Behavioral analysis may surface packages before CVE/advisory assignment. |
| 4 | **OpenSSF Package Analysis GitHub**<br><br>**`Link(s)`:** [github.com/ossf/package-analysis](https://github.com/ossf/package-analysis)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** Open-source package analysis system.<br><br>**`Notes & POIs`:** Useful for detection logic & behavioral signal review. |
| 5 | **OpenSSF Package Feeds**<br><br>**`Link(s)`:** [github.com/ossf/package-feeds](https://github.com/ossf/package-feeds)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** Package ecosystem feed monitoring.<br><br>**`Notes & POIs`:** Useful for observing new packages in ecosystems. |
| 6 | **GitHub malware advisories**<br><br>**`Link(s)`:** [github.com/advisories?query=type%3Amalware](https://github.com/advisories?query=type%3Amalware)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** GitHub malware advisories across ecosystems.<br><br>**`Notes & POIs`:** Treat as supply-chain compromise data, not conventional vuln data. |
| 7 | npm malware advisories via GitHub | [github.com/advisories?query=ecosystem%3Anpm+type%3Amalware](https://github.com/advisories?query=ecosystem%3Anpm+type%3Amalware) | Free public | npm-specific malware advisories. | npm has high malicious package volume; prioritize transitive dependency visibility. |
| 8 | PyPI malware advisories via GitHub | [github.com/advisories?query=ecosystem%3Apip+type%3Amalware](https://github.com/advisories?query=ecosystem%3Apip+type%3Amalware) | Free public | PyPI-specific malware advisories. | Use with lockfiles & package provenance checks. |
| 9 | Socket.dev blog | [socket.dev/blog](https://socket.dev/blog) | Free public blog; product/API features may be commercial | Supply-chain attack research & malicious package analysis. | Research feed; verify indicators before automated blocking. |
| 10 | Snyk vulnerability database | [security.snyk.io](https://security.snyk.io/) | Free public search; commercial plans/API features | Snyk vulnerability & package risk database. | Commercial/community source; validate licensing & provenance. |
| 11 | Sonatype OSS Index | [ossindex.sonatype.org](https://ossindex.sonatype.org/) | Free tier / API terms; commercial Sonatype products separate | OSS vulnerability intelligence. | Useful for package risk enrichment. |
| 12 | Sonatype vulnerability database | [sonatype.com/resources/vulnerability-database](https://sonatype.com/resources/vulnerability-database) | Free public search; commercial ecosystem | Sonatype vulnerability database. | Good secondary enrichment source. |
| 13 | Phylum research | [blog.phylum.io](https://blog.phylum.io/) | Free public blog; commercial products separate | Software supply-chain attack research. | Research source; useful for malicious package trends. |
| 14 | ReversingLabs threat research | [www.reversinglabs.com/blog](https://www.reversinglabs.com/blog) | Free public blog; commercial products separate | Threat research focused on malware & supply-chain compromise. | Use for context, not as canonical package advisory data. |
| 15 | Checkmarx supply-chain research | [checkmarx.com/blog](https://checkmarx.com/blog/) | Free public blog; commercial products separate | Supply-chain & application security research. | Useful for emerging package attack patterns. |

### 13.2 Package reputation / dependency health

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **OpenSSF Scorecard**<br><br>**`Link(s)`:** [github.com/ossf/scorecard](https://github.com/ossf/scorecard)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** Scores open-source project security practices.<br><br>**`Notes & POIs`:** Useful as dependency risk signal, not vulnerability proof. |
| 2 | **OpenSSF Scorecard API**<br><br>**`Link(s)`:** [api.securityscorecards.dev](https://api.securityscorecards.dev/)<br><br>**`Access / Cost`:** Free public API subject to service limits | **`Relevance`:** API for Scorecard results.<br><br>**`Notes & POIs`:** Use with timestamped results because scores change over time. |
| 3 | **OpenSSF Best Practices Badge**<br><br>**`Link(s)`:** [www.bestpractices.dev](https://www.bestpractices.dev/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Project best-practices badge program.<br><br>**`Notes & POIs`:** Useful project maturity signal, not vulnerability evidence. |
| 4 | **deps.dev**<br><br>**`Link(s)`:** [deps.dev](https://deps.dev/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Dependency metadata, transitive dependencies, security signals.<br><br>**`Notes & POIs`:** Useful for dependency graphing & package metadata. |
| 5 | **OpenSSF GUAC**<br><br>**`Link(s)`:** [guac.sh](https://guac.sh/)<br><br>**`Access / Cost`:** Free public / open-source project | **`Relevance`:** Graph for software supply- chain metadata.<br><br>**`Notes & POIs`:** Useful for correlating SBOMs, attestations, vulnerabilities, & provenance. |
| 6 | **GUAC GitHub**<br><br>**`Link(s)`:** [github.com/guacsec/guac](https://github.com/guacsec/guac)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** GUAC implementation repository.<br><br>**`Notes & POIs`:** Reference architecture for supply-chain knowledge graphs. |
| 7 | **Sigstore**<br><br>**`Link(s)`:** [www.sigstore.dev](https://www.sigstore.dev/)<br><br>**`Access / Cost`:** Free / open-source public infrastructure | **`Relevance`:** Signing & verification for software artifacts.<br><br>**`Notes & POIs`:** Helps assess provenance & tamper resistance. |
| 8 | **Rekor transparency log**<br><br>**`Link(s)`:** [docs.sigstore.dev/logging/overview](https://docs.sigstore.dev/logging/overview/)<br><br>**`Access / Cost`:** Free public docs / public transparency log | **`Relevance`:** Transparency log for signed artifacts.<br><br>**`Notes & POIs`:** Useful for provenance verification & audit trails. |
| 9 | **SLSA framework**<br><br>**`Link(s)`:** [slsa.dev](https://slsa.dev/)<br><br>**`Access / Cost`:** Free / open standard | **`Relevance`:** Supply-chain Levels for Software Artifacts.<br><br>**`Notes & POIs`:** Helps assess build integrity & supply-chain hardening. |

> 
> #### [*Back to **`Index`***](#index)
---

## 14. Source-code, dependency, artifact & build-chain provenance

### 14.1 Source & artifact provenance

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **SLSA**<br><br>**`Link(s)`:** [slsa.dev](https://slsa.dev/)<br><br>**`Access / Cost`:** Free / open standard | **`Relevance`:** Supply-chain Levels for Software Artifacts.<br><br>**`Notes & POIs`:** Useful for evaluating build integrity & provenance risk. |
| 2 | **Sigstore**<br><br>**`Link(s)`:** [www.sigstore.dev](https://www.sigstore.dev/)<br><br>**`Access / Cost`:** Free / open-source public infrastructure | **`Relevance`:** Signing & verification for software artifacts.<br><br>**`Notes & POIs`:** Helps verify artifact integrity & publisher identity. |
| 3 | **Cosign**<br><br>**`Link(s)`:** [github.com/sigstore/cosign](https://github.com/sigstore/cosign)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** Container/artifact signing tool.<br><br>**`Notes & POIs`:** Useful for verifying container image provenance. |
| 4 | **Rekor**<br><br>**`Link(s)`:** [docs.sigstore.dev/logging/overview](https://docs.sigstore.dev/logging/overview/)<br><br>**`Access / Cost`:** Free public docs / public transparency log | **`Relevance`:** Transparency log for signed artifacts.<br><br>**`Notes & POIs`:** Useful for auditability & tamper detection. |
| 5 | **in-toto**<br><br>**`Link(s)`:** [in-toto.io](https://in-toto.io/)<br><br>**`Access / Cost`:** Free / open-source | **`Relevance`:** Supply-chain integrity framework.<br><br>**`Notes & POIs`:** Useful for verifying build steps & provenance attestations. |
| 6 | **The Update Framework - TUF**<br><br>**`Link(s)`:** [theupdateframework.io](https://theupdateframework.io/)<br><br>**`Access / Cost`:** Free / open-source | **`Relevance`:** Secure software update framework.<br><br>**`Notes & POIs`:** Useful for update-channel compromise resistance. |
| 7 | **SLSA GitHub generators**<br><br>**`Link(s)`:** [github.com/slsa-framework/slsa-github-generator](https://github.com/slsa-framework/slsa-github-generator)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** GitHub-based SLSA provenance generators.<br><br>**`Notes & POIs`:** Useful for CI/CD provenance generation. |

### 14.2 Dependency inventory & graphing

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | deps.dev | [deps.dev](https://deps.dev/) | Free public | Dependency metadata, transitive dependency graphing, & security signals. | Useful for OSS dependency context. |
| 2 | GUAC | [guac.sh](https://guac.sh/) | Free public / open-source project | Graph for software supply-chain metadata. | Useful for correlating SBOMs, vulnerabilities, provenance, & attestations. |
| 3 | GUAC GitHub | [github.com/guacsec/guac](https://github.com/guacsec/guac) | Free / open-source public GitHub repo | GUAC implementation repository. | Reference architecture for software supply-chain knowledge graphs. |
| 4 | OpenSSF Scorecard | [github.com/ossf/scorecard](https://github.com/ossf/scorecard) | Free / open-source public GitHub repo | Open-source project security practice scoring. | Useful as a dependency risk signal. |
| 5 | OpenSSF Scorecard API | [api.securityscorecards.dev](https://api.securityscorecards.dev/) | Free public API subject to service limits | API for Scorecard results. | Scores are temporal; store retrieval time. |
| 6 | Maven Central | [central.sonatype.com](https://central.sonatype.com/) | Free public | Maven package metadata. | Useful for Java dependency resolution. |
| 7 | npm registry | [registry.npmjs.org](https://registry.npmjs.org/) | Free public registry API | npm package registry API endpoint. | Useful for package metadata & version resolution. |
| 8 | PyPI JSON API | [docs.pypi.org/api/json](https://docs.pypi.org/api/json/) | Free public API docs / public API | PyPI JSON API documentation. | Useful for Python package metadata. |
| 9 | crates.io API | [crates.io/data-access](https://crates.io/data-access) | Free public API subject to policy/rate limits | crates.io data access documentation. | Useful for Rust package metadata. |
| 10 | Go module proxy | [proxy.golang.org](https://proxy.golang.org/) | Free public | Go module proxy. | Useful for Go module version metadata. |

> 
> #### [*Back to **`Index`***](#index)
---

---

## F. Detection, Exposure, Threat Telemetry, Validation & Remediation Operations

## 15. Automated vulnerability detection, static analysis, dynamic analysis & research datasets

### 15.1 SAST / code query engines

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **CodeQL**<br><br>**`Link(s)`:** [codeql.github.com](https://codeql.github.com/)<br><br>**`Access / Cost`:** Free for many open-source uses; GitHub Advanced Security commercial for private enterprise use | **`Relevance`:** Semantic code analysis engine for vulnerability discovery.<br><br>**`Notes & POIs`:** Strong for variant analysis & source-level detection. |
| 2 | **CodeQL GitHub**<br><br>**`Link(s)`:** [github.com/github/codeql](https://github.com/github/codeql)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** CodeQL source & query repository.<br><br>**`Notes & POIs`:** Use query packs for detection logic examples. |
| 3 | **CodeQL query packs**<br><br>**`Link(s)`:** [github.com/github/codeql/tree/main](https://github.com/github/codeql/tree/main)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** Query packs for multiple languages.<br><br>**`Notes & POIs`:** Queries can be adapted for custom vuln detection. |
| 4 | **Semgrep**<br><br>**`Link(s)`:** [semgrep.dev](https://semgrep.dev/)<br><br>**`Access / Cost`:** Free/open-source CLI; commercial Semgrep products available | **`Relevance`:** Pattern-based static analysis.<br><br>**`Notes & POIs`:** Good for fast custom rule writing. |
| 5 | **Semgrep rules**<br><br>**`Link(s)`:** [github.com/semgrep/semgrep-rules](https://github.com/semgrep/semgrep-rules)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** Community/official Semgrep rules.<br><br>**`Notes & POIs`:** Validate rule precision before production blocking. |
| 6 | **Joern**<br><br>**`Link(s)`:** [joern.io](https://joern.io/)<br><br>**`Access / Cost`:** Free / open-source core | **`Relevance`:** Code property graph platform.<br><br>**`Notes & POIs`:** Useful for research-grade vulnerability discovery. |
| 7 | **Joern GitHub**<br><br>**`Link(s)`:** [github.com/joernio/joern](https://github.com/joernio/joern)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** Joern implementation.<br><br>**`Notes & POIs`:** Useful for custom graph queries & ML pipelines. |
| 8 | **Facebook Infer**<br><br>**`Link(s)`:** [fbinfer.com](https://fbinfer.com/)<br><br>**`Access / Cost`:** Free public / open-source | **`Relevance`:** Static analyzer for multiple languages.<br><br>**`Notes & POIs`:** Useful for null deref, resource leaks, concurrency, & related bug classes. |
| 9 | **Infer GitHub**<br><br>**`Link(s)`:** [github.com/facebook/infer](https://github.com/facebook/infer)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** Infer source repository.<br><br>**`Notes & POIs`:** Reference implementation. |
| 10 | **SonarQube rules**<br><br>**`Link(s)`:** [rules.sonarsource.com](https://rules.sonarsource.com/)<br><br>**`Access / Cost`:** Free public rules catalog; Sonar products include free & commercial tiers | **`Relevance`:** SonarSource rule catalog.<br><br>**`Notes & POIs`:** Useful for mapping code quality/security rules to weakness classes. |
| 11 | **Bandit - Python**<br><br>**`Link(s)`:** [github.com/PyCQA/bandit](https://github.com/PyCQA/bandit)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** Python security linter.<br><br>**`Notes & POIs`:** Useful for Python SAST coverage. |
| 12 | **Gosec - Go**<br><br>**`Link(s)`:** [github.com/securego/gosec](https://github.com/securego/gosec)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** Go security checker.<br><br>**`Notes & POIs`:** Useful for Go SAST. |
| 13 | **ESLint security plugin**<br><br>**`Link(s)`:** [github.com/eslint-community/eslint-plugin-security](https://github.com/eslint-community/eslint-plugin-security)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** JavaScript security lint rules.<br><br>**`Notes & POIs`:** Useful for JS static checks. |
| 14 | **SpotBugs**<br><br>**`Link(s)`:** [spotbugs.github.io](https://spotbugs.github.io/)<br><br>**`Access / Cost`:** Free / open-source | **`Relevance`:** Java static analysis.<br><br>**`Notes & POIs`:** General bug detection; pair with FindSecBugs for security. |
| 15 | **FindSecBugs**<br><br>**`Link(s)`:** [find-sec-bugs.github.io](https://find-sec-bugs.github.io/)<br><br>**`Access / Cost`:** Free / open-source | **`Relevance`:** Java security bug detection plugin.<br><br>**`Notes & POIs`:** Useful for Java/JVM SAST. |
| 16 | **Clang Static Analyzer**<br><br>**`Link(s)`:** [clang-analyzer.llvm.org](https://clang-analyzer.llvm.org/)<br><br>**`Access / Cost`:** Free / open-source | **`Relevance`:** C/C++/Objective-C static analyzer.<br><br>**`Notes & POIs`:** Useful for native code vulnerability classes. |
| 17 | **Cppcheck**<br><br>**`Link(s)`:** [cppcheck.sourceforge.io](https://cppcheck.sourceforge.io/)<br><br>**`Access / Cost`:** Free / open-source | **`Relevance`:** C/C++ static analyzer.<br><br>**`Notes & POIs`:** Complements compiler analyzers. |
| 18 | **Flawfinder**<br><br>**`Link(s)`:** [dwheeler.com/flawfinder](https://dwheeler.com/flawfinder/)<br><br>**`Access / Cost`:** Free / open-source | **`Relevance`:** C/C++ security scanner for dangerous functions.<br><br>**`Notes & POIs`:** Fast heuristic scanner with false-positive risk. |
| 19 | **Brakeman - Ruby on Rails**<br><br>**`Link(s)`:** [brakemanscanner.org](https://brakemanscanner.org/)<br><br>**`Access / Cost`:** Free / open-source | **`Relevance`:** Ruby on Rails static security scanner.<br><br>**`Notes & POIs`:** Useful for Rails-specific vulnerability patterns. |
| 20 | **Horusec**<br><br>**`Link(s)`:** [github.com/ZupIT/horusec](https://github.com/ZupIT/horusec)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** Multi-language security scanner.<br><br>**`Notes & POIs`:** Useful for broad SAST coverage. |
| 21 | **Bearer**<br><br>**`Link(s)`:** [github.com/Bearer/bearer](https://github.com/Bearer/bearer)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** Code security/privacy scanner.<br><br>**`Notes & POIs`:** Useful for data-flow & sensitive data exposure detection. |
| 22 | **MobSF**<br><br>**`Link(s)`:** [github.com/MobSF/Mobile-Security-Framework-MobSF](https://github.com/MobSF/Mobile-Security-Framework-MobSF)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** Mobile security testing framework.<br><br>**`Notes & POIs`:** Useful for Android/iOS static & dynamic app analysis. |
| 23 | **zizmor**<br><br>**`Link(s)`:** [github.com/zizmorcore/zizmor](https://github.com/zizmorcore/zizmor)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** Static analysis for GitHub Actions.<br><br>**`Notes & POIs`:** Useful for CI/CD workflow security, GitHub Actions hardening, & supply-chain pipeline risk detection. |
| 24 | **OpenAnt**<br><br>**`Link(s)`:** [github.com/knostic/OpenAnt](https://github.com/knostic/OpenAnt)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** LLM-based vulnerability discovery product focused on verified security flaws & reduced false positives.<br><br>**`Notes & POIs`:** Useful as AI-assisted vulnerability discovery tooling. Validate findings against primary evidence before treating as confirmed vulnerabilities. |

### 15.2 DAST, IAST, fuzzing & dynamic test sources

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **OSS-Fuzz**<br><br>**`Link(s)`:** [google.github.io/oss-fuzz](https://google.github.io/oss-fuzz/)<br><br>**`Access / Cost`:** Free for eligible open-source projects | **`Relevance`:** Continuous fuzzing for open-source projects.<br><br>**`Notes & POIs`:** Useful for vulnerability discovery & bug lifecycle data. |
| 2 | **OSS-Fuzz GitHub**<br><br>**`Link(s)`:** [github.com/google/oss-fuzz](https://github.com/google/oss-fuzz)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** OSS-Fuzz project configuration repository.<br><br>**`Notes & POIs`:** Useful for project fuzzing coverage & harness examples. |
| 3 | **OSS-Fuzz vulnerability data in OSV**<br><br>**`Link(s)`:** [osv.dev/list?ecosystem=OSS-Fuzz](https://osv.dev/list?ecosystem=OSS-Fuzz)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** OSV records from OSS-Fuzz vulnerabilities.<br><br>**`Notes & POIs`:** Good for linking fuzz-discovered vulnerabilities to OSV schema. |
| 4 | **ClusterFuzzLite**<br><br>**`Link(s)`:** [google.github.io/clusterfuzzlite](https://google.github.io/clusterfuzzlite/)<br><br>**`Access / Cost`:** Free / open-source | **`Relevance`:** Lightweight continuous fuzzing for CI/CD.<br><br>**`Notes & POIs`:** Useful for integrating fuzzing into development pipelines. |
| 5 | **AFL++**<br><br>**`Link(s)`:** [github.com/AFLplusplus/AFLplusplus](https://github.com/AFLplusplus/AFLplusplus)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** Coverage-guided fuzzer.<br><br>**`Notes & POIs`:** Good for native code vulnerability discovery. |
| 6 | **libFuzzer**<br><br>**`Link(s)`:** [llvm.org/docs/LibFuzzer.html](https://llvm.org/docs/LibFuzzer.html)<br><br>**`Access / Cost`:** Free / open-source LLVM component | **`Relevance`:** In-process coverage-guided fuzzer.<br><br>**`Notes & POIs`:** Common with LLVM sanitizers. |
| 7 | **Honggfuzz**<br><br>**`Link(s)`:** [github.com/google/honggfuzz](https://github.com/google/honggfuzz)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** Security-oriented fuzzer.<br><br>**`Notes & POIs`:** Useful for native code dynamic testing. |
| 8 | **Jazzer**<br><br>**`Link(s)`:** [github.com/CodeIntelligenceTesting/jazzer](https://github.com/CodeIntelligenceTesting/jazzer)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** JVM fuzzing engine.<br><br>**`Notes & POIs`:** Useful for Java/Kotlin fuzz testing. |
| 9 | **OWASP ZAP**<br><br>**`Link(s)`:** [www.zaproxy.org](https://www.zaproxy.org/)<br><br>**`Access / Cost`:** Free / open-source | **`Relevance`:** Web application dynamic security scanner.<br><br>**`Notes & POIs`:** Useful for DAST & app exposure validation. |
| 10 | **Nuclei**<br><br>**`Link(s)`:** [github.com/projectdiscovery/nuclei](https://github.com/projectdiscovery/nuclei)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo; commercial ecosystem separate | **`Relevance`:** Template-based vulnerability & exposure scanner.<br><br>**`Notes & POIs`:** Useful for automated exposed-service checks. |
| 11 | **Nuclei templates**<br><br>**`Link(s)`:** [github.com/projectdiscovery/nuclei-templates](https://github.com/projectdiscovery/nuclei-templates)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** Community/official detection templates.<br><br>**`Notes & POIs`:** Template quality varies; review false-positive potential. |

### 15.3 Vulnerability-detection research datasets

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **NIST SARD**<br><br>**`Link(s)`:** [samate.nist.gov/SARD](https://samate.nist.gov/SARD/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Software Assurance Reference Dataset.<br><br>**`Notes & POIs`:** Useful for evaluating static analysis tools & ML models. |
| 2 | **Juliet Test Suite - NIST SARD**<br><br>**`Link(s)`:** [samate.nist.gov/SARD/test-suites/112](https://samate.nist.gov/SARD/test-suites/112)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Synthetic test cases for many vulnerability classes.<br><br>**`Notes & POIs`:** Useful for controlled evaluation, but may not reflect real-world code complexity. |
| 3 | **Big-Vul**<br><br>**`Link(s)`:** [github.com/ZeoVan/MSR_20_Code_vulnerability_CSV_Dataset](https://github.com/ZeoVan/MSR_20_Code_vulnerability_CSV_Dataset)<br><br>**`Access / Cost`:** Free public GitHub repo; verify license | **`Relevance`:** Large vulnerability dataset derived from real-world CVE-fix commits.<br><br>**`Notes & POIs`:** Validate deduplication, labels, & train/test leakage. |
| 4 | **Devign**<br><br>**`Link(s)`:** [sites.google.com/view/devign](https://sites.google.com/view/devign)<br><br>**`Access / Cost`:** Free public research page; verify dataset access/license | **`Relevance`:** Vulnerability detection dataset.<br><br>**`Notes & POIs`:** Used in ML vuln detection research. |
| 5 | **Draper VDISC**<br><br>**`Link(s)`:** [osf.io/d45bw](https://osf.io/d45bw/)<br><br>**`Access / Cost`:** Free public OSF dataset; verify license/terms | **`Relevance`:** Vulnerability discovery dataset.<br><br>**`Notes & POIs`:** Useful for ML baselines; inspect labeling quality. |
| 6 | **DiverseVul**<br><br>**`Link(s)`:** [github.com/wagner-group/diversevul](https://github.com/wagner-group/diversevul)<br><br>**`Access / Cost`:** Free public GitHub repo; verify license | **`Relevance`:** Diverse vulnerability dataset.<br><br>**`Notes & POIs`:** Useful for model training/evaluation; check license & label quality. |
| 7 | **PrimeVul**<br><br>**`Link(s)`:** [github.com/DLVulDet/PrimeVul](https://github.com/DLVulDet/PrimeVul)<br><br>**`Access / Cost`:** Free public GitHub repo; verify license | **`Relevance`:** Vulnerability detection benchmark dataset.<br><br>**`Notes & POIs`:** Useful for modern ML vulnerability detection benchmarking. |
| 8 | MegaVul | [github.com/Icyrockton/MegaVul](https://github.com/Icyrockton/MegaVul) | Free public GitHub repo; verify license | Large-scale vulnerability dataset. | Validate methodology before using as labels. |
| 9 | Vul4J | [github.com/tuhh-softsec/vul4j](https://github.com/tuhh-softsec/vul4j) | Free / open-source public GitHub repo | Java vulnerability benchmark. | Useful for Java-focused vulnerability repair/detection. |
| 10 | VulnCode-DB | [github.com/vegardit/vulncode-db](https://github.com/vegardit/vulncode-db) | Free public GitHub repo; verify license | Vulnerable code examples. | Useful for examples & tests. |
| 11 | SecurityEval | [github.com/s2e-lab/SecurityEval](https://github.com/s2e-lab/SecurityEval) | Free public GitHub repo; verify license | Security-focused benchmark. | Useful for evaluating generated code or models. |
| 12 | CVEfixes | [github.com/secureIT-project/CVEfixes](https://github.com/secureIT-project/CVEfixes) | Free public GitHub repo; verify license | Links CVEs to fixing commits. | Useful for root-cause, patch, & ML training pipelines. |
| 13 | Defects4J | [github.com/rjust/defects4j](https://github.com/rjust/defects4j) | Free / open-source public GitHub repo | Java bug dataset. | Not vulnerability-specific, but useful for bug repair baselines. |
| 14 | ManySStuBs4J | [github.com/mast-group/mineSStuBs](https://github.com/mast-group/mineSStuBs) | Free public GitHub repo; verify license | Java simple bug dataset. | Not vulnerability-specific, but useful for bug-fix modeling. |
| 15 | VulDeePecker | [github.com/CGCL-codes/VulDeePecker](https://github.com/CGCL-codes/VulDeePecker) | Free public GitHub repo; verify license | Deep-learning vulnerability detection dataset/tooling. | Older benchmark; inspect for duplication & outdated methodology. |

> 
> #### [*Back to **`Index`***](#index)
---

## 16. Exposure, internet-facing asset & threat telemetry

### 16.1 Internet exposure search engines

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **Censys Search**<br><br>**`Link(s)`:** [search.censys.io](https://search.censys.io/)<br><br>**`Access / Cost`:** Free tier / paid plans | **`Relevance`:** Internet exposure search engine.<br><br>**`Notes & POIs`:** Useful for determining if vulnerable services are internet-facing. |
| 2 | **Censys API**<br><br>**`Link(s)`:** [search.censys.io/api](https://search.censys.io/api)<br><br>**`Access / Cost`:** Free tier / paid plans; API key required | **`Relevance`:** Programmatic Censys access.<br><br>**`Notes & POIs`:** API terms & quotas may apply. |
| 3 | **Shodan**<br><br>**`Link(s)`:** [www.shodan.io](https://www.shodan.io/)<br><br>**`Access / Cost`:** Free limited access / paid plans | **`Relevance`:** Internet-connected device search.<br><br>**`Notes & POIs`:** Useful for exposure discovery & banner-based matching. |
| 4 | **Shodan developer API**<br><br>**`Link(s)`:** [developer.shodan.io](https://developer.shodan.io/)<br><br>**`Access / Cost`:** Paid/API credit model may apply; account required | **`Relevance`:** Shodan API documentation.<br><br>**`Notes & POIs`:** Useful for automation. |
| 5 | ZoomEye | [www.zoomeye.org](https://www.zoomeye.org/) | Free limited access / paid plans | Internet asset search engine. | Useful as additional exposure telemetry. |
| 6 | FOFA | [fofa.info](https://fofa.info/) | Free limited access / paid plans | Internet asset search. | Coverage & access terms vary. |
| 7 | BinaryEdge | [www.binaryedge.io](https://www.binaryedge.io/) | Commercial / limited trial may exist | Internet scanning & threat intelligence. | Useful for external exposure enrichment. |
| 8 | Onyphe | [www.onyphe.io](https://www.onyphe.io/) | Free tier / paid plans | Cyber defense search engine. | Useful for passive/active exposure context. |
| 9 | SecurityTrails | [securitytrails.com](https://securitytrails.com/) | Free limited access / paid plans | DNS & asset intelligence. | Useful for attack surface discovery. |
| 10 | InternetDB by Shodan | [internetdb.shodan.io](https://internetdb.shodan.io/) | Free public API | Lightweight Shodan InternetDB API. | Useful for quick IP exposure enrichment. |

### 16.2 Scan/exploitation telemetry

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **GreyNoise Visualizer**<br><br>**`Link(s)`:** [viz.greynoise.io](https://viz.greynoise.io/)<br><br>**`Access / Cost`:** Free tier / paid plans | **`Relevance`:** Internet scanning/exploitation telemetry.<br><br>**`Notes & POIs`:** Helps separate background scanning from targeted activity. |
| 2 | **GreyNoise API docs**<br><br>**`Link(s)`:** [docs.greynoise.io](https://docs.greynoise.io/)<br><br>**`Access / Cost`:** Free tier / paid plans; API key required | **`Relevance`:** API docs for GreyNoise enrichment.<br><br>**`Notes & POIs`:** Useful for automated telemetry enrichment. |
| 3 | **Shadowserver**<br><br>**`Link(s)`:** [www.shadowserver.org](https://www.shadowserver.org/)<br><br>**`Access / Cost`:** Free for eligible organizations; registration may be required | **`Relevance`:** Internet-scale exposure & threat telemetry.<br><br>**`Notes & POIs`:** Good for population-level exposure signals. |
| 4 | **Shadowserver reports**<br><br>**`Link(s)`:** [dashboard.shadowserver.org](https://dashboard.shadowserver.org/)<br><br>**`Access / Cost`:** Free for eligible organizations; login/registration may be required | **`Relevance`:** Shadowserver reporting dashboard.<br><br>**`Notes & POIs`:** Access/eligibility may vary. |
| 5 | **SANS Internet Storm Center**<br><br>**`Link(s)`:** [isc.sans.edu](https://isc.sans.edu/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Internet threat telemetry & diary reports.<br><br>**`Notes & POIs`:** Useful for emergent exploitation context. |
| 6 | **Honeynet Project**<br><br>**`Link(s)`:** [www.honeynet.org](https://www.honeynet.org/)<br><br>**`Access / Cost`:** Free public / open research | **`Relevance`:** Honeypot & threat research.<br><br>**`Notes & POIs`:** Useful for attacker behavior insight. |
| 7 | **DShield**<br><br>**`Link(s)`:** [www.dshield.org](https://www.dshield.org/)<br><br>**`Access / Cost`:** Free public / community | **`Relevance`:** Distributed intrusion detection & telemetry.<br><br>**`Notes & POIs`:** Useful for broad scanning trend analysis. |
| 8 | **LeakIX**<br><br>**`Link(s)`:** [leakix.net](https://leakix.net/)<br><br>**`Access / Cost`:** Free limited access / paid plans | **`Relevance`:** Exposed service & leak search.<br><br>**`Notes & POIs`:** Useful for exposure assessment. |
| 9 | **urlscan.io**<br><br>**`Link(s)`:** [urlscan.io](https://urlscan.io/)<br><br>**`Access / Cost`:** Free tier / paid plans | **`Relevance`:** URL scanning & web telemetry.<br><br>**`Notes & POIs`:** Useful for phishing, web exposure, & IOC enrichment. |
| 10 | **VirusTotal**<br><br>**`Link(s)`:** [www.virustotal.com](https://www.virustotal.com/)<br><br>**`Access / Cost`:** Free community access / paid enterprise plans | **`Relevance`:** File, URL, domain, & IP reputation.<br><br>**`Notes & POIs`:** Useful for malware/IOC enrichment; licensing constraints apply. |
| 11 | **VirusTotal API**<br><br>**`Link(s)`:** [docs.virustotal.com/reference/overview](https://docs.virustotal.com/reference/overview)<br><br>**`Access / Cost`:** Free community API / paid enterprise API | **`Relevance`:** VirusTotal API documentation.<br><br>**`Notes & POIs`:** API quota & data-sharing policies matter. |

### 16.3 Attack surface management context

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **Amass**<br><br>**`Link(s)`:** [github.com/owasp-amass/amass](https://github.com/owasp-amass/amass)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** Attack surface mapping & DNS enumeration.<br><br>**`Notes & POIs`:** Useful for external asset discovery. |
| 2 | **ProjectDiscovery Subfinder**<br><br>**`Link(s)`:** [github.com/projectdiscovery/subfinder](https://github.com/projectdiscovery/subfinder)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** Subdomain discovery.<br><br>**`Notes & POIs`:** Useful for asset inventory enrichment. |
| 3 | **httpx**<br><br>**`Link(s)`:** [github.com/projectdiscovery/httpx](https://github.com/projectdiscovery/httpx)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** HTTP probing toolkit.<br><br>**`Notes & POIs`:** Useful for validating exposed services. |
| 4 | **Naabu**<br><br>**`Link(s)`:** [github.com/projectdiscovery/naabu](https://github.com/projectdiscovery/naabu)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** Port scanner.<br><br>**`Notes & POIs`:** Useful for fast exposure discovery. |
| 5 | **Nmap**<br><br>**`Link(s)`:** [nmap.org](https://nmap.org/)<br><br>**`Access / Cost`:** Free / open-source | **`Relevance`:** Network discovery & security auditing.<br><br>**`Notes & POIs`:** Mature scanner for service detection & scripts. |
| 6 | **Masscan**<br><br>**`Link(s)`:** [github.com/robertdavidgraham/masscan](https://github.com/robertdavidgraham/masscan)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** High-speed port scanner.<br><br>**`Notes & POIs`:** Use carefully; scan authorization & network impact matter. |

> 
> #### [*Back to **`Index`***](#index)
---

## 17. Threat intelligence, malware, ransomware & in-the-wild exploitation context

### 17.1 Major threat research sources
| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **Mandiant / Google Cloud Threat Intelligence**<br><br>**`Link(s)`:** [cloud.google.com/blog/topics/threat-intelligence](https://cloud.google.com/blog/topics/threat-intelligence)<br><br>**`Access / Cost`:** Free public blog; commercial threat intel products separate | **`Relevance`:** Threat intelligence & exploitation-in-the-wild context.<br><br>**`Notes & POIs`:** Useful for campaign-level vulnerability exploitation context. |
| 2 | **Microsoft Threat Intelligence blog**<br><br>**`Link(s)`:** [www.microsoft.com/en-us/security/blog/topic/threat-intelligence](https://www.microsoft.com/en-us/security/blog/topic/threat-intelligence/)<br><br>**`Access / Cost`:** Free public blog | **`Relevance`:** Microsoft threat intel & exploitation reports.<br><br>**`Notes & POIs`:** Useful for attacker behavior, exploitation campaigns, & mitigations. |
| 3 | **Google Threat Analysis Group**<br><br>**`Link(s)`:** [blog.google/threat-analysis-group](https://blog.google/threat-analysis-group/)<br><br>**`Access / Cost`:** Free public blog | **`Relevance`:** Nation-state & high-end threat research.<br><br>**`Notes & POIs`:** Useful for exploited-in-the-wild context. |
| 4 | **Palo Alto Unit 42**<br><br>**`Link(s)`:** [unit42.paloaltonetworks.com](https://unit42.paloaltonetworks.com/)<br><br>**`Access / Cost`:** Free public blog; commercial threat intel services separate | **`Relevance`:** Threat research & vulnerability exploitation reporting.<br><br>**`Notes & POIs`:** Useful for campaign & malware context. |
| 5 | **Cisco Talos**<br><br>**`Link(s)`:** [blog.talosintelligence.com](https://blog.talosintelligence.com/)<br><br>**`Access / Cost`:** Free public blog; commercial Cisco products separate | **`Relevance`:** Threat intel, malware, & vulnerability research.<br><br>**`Notes & POIs`:** Useful for IOCs & exploit campaigns. |
| 6 | **Rapid7 vulnerability management blog**<br><br>**`Link(s)`:** [www.rapid7.com/blog/tag/vulnerability-management](https://www.rapid7.com/blog/tag/vulnerability-management/)<br><br>**`Access / Cost`:** Free public blog; commercial products separate | **`Relevance`:** Vulnerability management & exploitability commentary.<br><br>**`Notes & POIs`:** Useful for operational triage context. |
| 7 | **Sophos X-Ops**<br><br>**`Link(s)`:** [news.sophos.com/en-us/category/threat-research](https://news.sophos.com/en-us/category/threat-research/)<br><br>**`Access / Cost`:** Free public blog; commercial products separate | **`Relevance`:** Threat research & incident reports.<br><br>**`Notes & POIs`:** Useful for exploitation context & malware behavior. |
| 8 | **CrowdStrike Blog**<br><br>**`Link(s)`:** [www.crowdstrike.com/en-us/blog](https://www.crowdstrike.com/en-us/blog/)<br><br>**`Access / Cost`:** Free public blog; commercial products separate | **`Relevance`:** Threat intelligence & incident research.<br><br>**`Notes & POIs`:** Useful for adversary behavior & vulnerability exploitation context. |
| 9 | **SentinelOne Labs**<br><br>**`Link(s)`:** [www.sentinelone.com/labs](https://www.sentinelone.com/labs/)<br><br>**`Access / Cost`:** Free public blog; commercial products separate | **`Relevance`:** Malware & threat research.<br><br>**`Notes & POIs`:** Useful for exploit chains & malware analysis. |
| 10 | **Kaspersky Securelist**<br><br>**`Link(s)`:** [securelist.com](https://securelist.com/)<br><br>**`Access / Cost`:** Free public blog; commercial products separate | **`Relevance`:** Threat research & malware analysis.<br><br>**`Notes & POIs`:** Useful for campaign-level context. |
| 11 | **ESET WeLiveSecurity**<br><br>**`Link(s)`:** [www.welivesecurity.com](https://www.welivesecurity.com/)<br><br>**`Access / Cost`:** Free public blog; commercial products separate | **`Relevance`:** Threat research & malware analysis.<br><br>**`Notes & POIs`:** Useful for exploitation narratives & IOCs. |
| 12 | **Trend Micro Research**<br><br>**`Link(s)`:** [www.trendmicro.com/en_us/research.html](https://www.trendmicro.com/en_us/research.html)<br><br>**`Access / Cost`:** Free public research; commercial products separate | **`Relevance`:** Threat & vulnerability research.<br><br>**`Notes & POIs`:** Useful for active exploitation context. |
| 13 | **FortiGuard Labs**<br><br>**`Link(s)`:** [www.fortiguard.com/research](https://www.fortiguard.com/research)<br><br>**`Access / Cost`:** Free public research; commercial products separate | **`Relevance`:** Fortinet threat research.<br><br>**`Notes & POIs`:** Useful for attack patterns & indicators. |
| 14 | **Check Point Research**<br><br>**`Link(s)`:** [research.checkpoint.com](https://research.checkpoint.com/)<br><br>**`Access / Cost`:** Free public blog; commercial products separate | **`Relevance`:** Threat research & vulnerability analysis.<br><br>**`Notes & POIs`:** Useful for campaign & exploit analysis. |
| 15 | **Elastic Security Labs**<br><br>**`Link(s)`:** [www.elastic.co/security-labs](https://www.elastic.co/security-labs)<br><br>**`Access / Cost`:** Free public research; commercial products separate | **`Relevance`:** Detection engineering & threat research.<br><br>**`Notes & POIs`:** Useful for detection logic & adversary behavior. |
| 16 | **Sekoia Threat Intelligence**<br><br>**`Link(s)`:** [blog.sekoia.io](https://blog.sekoia.io/)<br><br>**`Access / Cost`:** Free public blog; commercial threat intel separate | **`Relevance`:** Threat intelligence research.<br><br>**`Notes & POIs`:** Useful for IOCs & campaign context. |

### 17.2 Malware & IOC repositories

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **MISP**<br><br>**`Link(s)`:** [www.misp-project.org](https://www.misp-project.org/)<br><br>**`Access / Cost`:** Free / open-source; data sharing depends on communities/instances | **`Relevance`:** Threat intelligence sharing platform.<br><br>**`Notes & POIs`:** Useful for IOC correlation & sharing. |
| 2 | **AlienVault OTX**<br><br>**`Link(s)`:** [otx.alienvault.com](https://otx.alienvault.com/)<br><br>**`Access / Cost`:** Free community access; commercial AT&T Cybersecurity products separate | **`Relevance`:** Open threat exchange for IOCs.<br><br>**`Notes & POIs`:** Quality varies by pulse/source. Validate before enforcement. |
| 3 | **AbuseIPDB**<br><br>**`Link(s)`:** [www.abuseipdb.com](https://www.abuseipdb.com/)<br><br>**`Access / Cost`:** Free tier / paid plans | **`Relevance`:** IP abuse reputation database.<br><br>**`Notes & POIs`:** Useful for IP enrichment; not vulnerability-specific. |
| 4 | **URLhaus**<br><br>**`Link(s)`:** [urlhaus.abuse.ch](https://urlhaus.abuse.ch/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Malware URL tracking.<br><br>**`Notes & POIs`:** Useful for IOC enrichment. |
| 5 | **MalwareBazaar**<br><br>**`Link(s)`:** [bazaar.abuse.ch](https://bazaar.abuse.ch/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Malware sample sharing.<br><br>**`Notes & POIs`:** Useful for malware family & hash enrichment. |
| 6 | **ThreatFox**<br><br>**`Link(s)`:** [threatfox.abuse.ch](https://threatfox.abuse.ch/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Threat intelligence indicators.<br><br>**`Notes & POIs`:** Useful for IOCs. |
| 7 | **Feodo Tracker**<br><br>**`Link(s)`:** [feodotracker.abuse.ch](https://feodotracker.abuse.ch/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Botnet C2 tracking.<br><br>**`Notes & POIs`:** Useful for malware infrastructure context. |
| 8 | **PhishTank**<br><br>**`Link(s)`:** [phishtank.org](https://phishtank.org/)<br><br>**`Access / Cost`:** Free community access; API/account may be required | **`Relevance`:** Phishing URL database.<br><br>**`Notes & POIs`:** Useful for phishing exposure & IOC enrichment. |
| 9 | **OpenPhish**<br><br>**`Link(s)`:** [openphish.com](https://openphish.com/)<br><br>**`Access / Cost`:** Free limited feed / paid premium feeds | **`Relevance`:** Phishing intelligence.<br><br>**`Notes & POIs`:** Commercial/community source; check terms. |
| 10 | **YARA**<br><br>**`Link(s)`:** [github.com/VirusTotal/yara](https://github.com/VirusTotal/yara)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** Malware classification & pattern matching engine.<br><br>**`Notes & POIs`:** Useful for detection signatures. |
| 11 | **YARA-Rules**<br><br>**`Link(s)`:** [github.com/Yara-Rules/rules](https://github.com/Yara-Rules/rules)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** Community YARA rules.<br><br>**`Notes & POIs`:** Validate rule quality before production use. |
| 12 | **SigmaHQ**<br><br>**`Link(s)`:** [github.com/SigmaHQ/sigma](https://github.com/SigmaHQ/sigma)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** Generic SIEM detection rule format.<br><br>**`Notes & POIs`:** Useful for detection engineering. |
| 13 | **LOLBAS**<br><br>**`Link(s)`:** [lolbas-project.github.io](https://lolbas-project.github.io/)<br><br>**`Access / Cost`:** Free public / open-source project | **`Relevance`:** Living-off-the-land binaries/scripts catalog.<br><br>**`Notes & POIs`:** Useful for attack behavior detection. |
| 14 | **GTFOBins**<br><br>**`Link(s)`:** [gtfobins.github.io](https://gtfobins.github.io/)<br><br>**`Access / Cost`:** Free public / open-source project | **`Relevance`:** Unix binary abuse catalog.<br><br>**`Notes & POIs`:** Useful for privilege escalation & post-exploitation detection. |
| 15 | **Ransomware.live**<br><br>**`Link(s)`:** [www.ransomware.live](https://www.ransomware.live/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Ransomware group/leak-site tracking.<br><br>**`Notes & POIs`:** Useful for ransomware exploitation context & trend analysis. |

> 
> #### [*Back to **`Index`***](#index)
---

---

## G. Governance, Compliance, Assurance, Production Baselines & Final Operating Model

## 18. Compliance, baseline configuration, software assurance & exposure severity standards
These are not vulnerability feeds, but they help assess impact, control failure, configuration exposure, & exploitability in a given environment.

### 18.1 Security configuration & benchmarks

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **CIS Benchmarks**<br><br>**`Link(s)`:** [www.cisecurity.org/cis-benchmarks](https://www.cisecurity.org/cis-benchmarks)<br><br>**`Access / Cost`:** Free with registration for many PDFs; commercial CIS tools/membership available | **`Relevance`:** Secure configuration benchmarks.<br><br>**`Notes & POIs`:** Useful for environmental risk scoring & hardening validation. |
| 2 | **CIS Controls**<br><br>**`Link(s)`:** [www.cisecurity.org/controls](https://www.cisecurity.org/controls)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Security control framework.<br><br>**`Notes & POIs`:** Useful for vulnerability management program alignment. |
| 3 | **NIST National Checklist Program**<br><br>**`Link(s)`:** [ncp.nist.gov](https://ncp.nist.gov/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Repository of security configuration checklists.<br><br>**`Notes & POIs`:** Useful for baseline configuration assessment. |
| 4 | **DISA STIGs**<br><br>**`Link(s)`:** [public.cyber.mil/stigs](https://public.cyber.mil/stigs/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Security Technical Implementation Guides.<br><br>**`Notes & POIs`:** Important for government/defense compliance. |
| 5 | **OpenSCAP**<br><br>**`Link(s)`:** [www.open-scap.org](https://www.open-scap.org/)<br><br>**`Access / Cost`:** Free / open-source | **`Relevance`:** SCAP tooling for compliance scanning.<br><br>**`Notes & POIs`:** Useful for host-level configuration scanning. |

| 6 | SCAP Security Guide | [github.com/ComplianceAsCode/content](https://github.com/ComplianceAsCode/content) | Free / open-source public GitHub repo | ComplianceAsCode content for SCAP profiles. | Useful for policy-as-code & baseline validation. |

### 18.2 Cloud configuration posture

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

### 18.3 Software assurance, secure development, acquisition & NIST publication libraries

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

## 19. Minimal source set for production use

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **CVE List v5**<br><br>**`Link(s)`:** [github.com/CVEProject/cvelistV5](https://github.com/CVEProject/cvelistV5)<br><br>**`Access / Cost`:** Free public GitHub repo | **`Relevance`:** Canonical CVE records.<br><br>**`Notes & POIs`:** Start here for CVE identity. |
| 2 | **CVE schema**<br><br>**`Link(s)`:** [github.com/CVEProject/cve-schema](https://github.com/CVEProject/cve-schema)<br><br>**`Access / Cost`:** Free public GitHub repo | **`Relevance`:** CVE schema validation.<br><br>**`Notes & POIs`:** Required for robust parsers. |
| 3 | **NVD CVE API**<br><br>**`Link(s)`:** [nvd.nist.gov/developers/vulnerabilities](https://nvd.nist.gov/developers/vulnerabilities)<br><br>**`Access / Cost`:** Free public; optional free API key for higher rate limits | **`Relevance`:** CVSS/CPE/CWE enrichment.<br><br>**`Notes & POIs`:** Core product matching source. |
| 4 | **NVD CPE API**<br><br>**`Link(s)`:** [nvd.nist.gov/developers/products](https://nvd.nist.gov/developers/products)<br><br>**`Access / Cost`:** Free public; optional free API key for higher rate limits | **`Relevance`:** Product/platform identity matching.<br><br>**`Notes & POIs`:** Combine with PURL. |
| 5 | **OSV full database**<br><br>**`Link(s)`:** [google.github.io/osv.dev/data/#full-database-download](https://google.github.io/osv.dev/data/#full-database-download)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** OSS package vulnerability database.<br><br>**`Notes & POIs`:** Local mirroring recommended. |
| 6 | **OSV schema**<br><br>**`Link(s)`:** [ossf.github.io/osv-schema](https://ossf.github.io/osv-schema/)<br><br>**`Access / Cost`:** Free public / open-source | **`Relevance`:** OSS vulnerability record schema.<br><br>**`Notes & POIs`:** Needed for parsing affected ranges. |
| 7 | **GitHub Advisory Database repo**<br><br>**`Link(s)`:** [github.com/github/advisory-database](https://github.com/github/advisory-database)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** Raw GitHub advisory records.<br><br>**`Notes & POIs`:** Preserve GHSA aliases. |
| 8 | **CISA KEV JSON**<br><br>**`Link(s)`:** [www.cisa.gov/sites/default/files/feeds/known_exploited_vulnerabilities.json](https://www.cisa.gov/sites/default/files/feeds/known_exploited_vulnerabilities.json)<br><br>**`Access / Cost`:** Free public feed | **`Relevance`:** Known exploitation signal.<br><br>**`Notes & POIs`:** High-priority remediation driver. |
| 9 | **CISA Vulnrichment**<br><br>**`Link(s)`:** [github.com/cisagov/vulnrichment](https://github.com/cisagov/vulnrichment)<br><br>**`Access / Cost`:** Free public GitHub repo | **`Relevance`:** CISA ADP & SSVC enrichment.<br><br>**`Notes & POIs`:** Coverage varies. |
| 10 | **FIRST EPSS**<br><br>**`Link(s)`:** [www.first.org/epss](https://www.first.org/epss/)<br><br>**`Access / Cost`:** Free public data/API | **`Relevance`:** Exploit likelihood prediction.<br><br>**`Notes & POIs`:** Store score date. |
| 11 | CWE downloads | [cwe.mitre.org/data/downloads.html](https://cwe.mitre.org/data/downloads.html) | Free public downloads | Weakness taxonomy ingestion. | Useful for classification & grouping. |
| 12 | CAPEC downloads | [capec.mitre.org/data/downloads.html](https://capec.mitre.org/data/downloads.html) | Free public downloads | Attack-pattern taxonomy ingestion. | Useful for weakness-to-attack mapping. |
| 13 | ATT&CK STIX data | [github.com/mitre-attack/attack-stix-data](https://github.com/mitre-attack/attack-stix-data) | Free public GitHub repo | Machine-readable adversary techniques. | Useful for response/detection mapping. |
| 14 | MITRE ATLAS | [atlas.mitre.org](https://atlas.mitre.org/) | Free public | AI/ML adversary framework. | Required for AI system risk mapping. |
| 15 | CycloneDX | [cyclonedx.org/specification/overview](https://cyclonedx.org/specification/overview/) | Free / open standard | SBOM/vulnerability/VEX-capable standard. | Good for inventory ingestion. |
| 16 | SPDX | [spdx.dev/specifications](https://spdx.dev/specifications/) | Free / open standard | SBOM & package metadata standard. | Common in compliance workflows. |
| 17 | PURL | [github.com/package-url/purl-spec](https://github.com/package-url/purl-spec) | Free / open-source | Package identity. | Essential for package vulnerability matching. |
| 18 | CSAF | [docs.oasis-open.org/csaf/csaf/v2.0/os/csaf-v2.0-os.html](https://docs.oasis-open.org/csaf/csaf/v2.0/os/csaf-v2.0-os.html) | Free / open standard | Structured security advisories. | Supports product status & VEX-like workflows. |
| 19 | OpenVEX | [github.com/openvex/spec](https://github.com/openvex/spec) | Free / open-source | Affected/not-affected status communication. | Reduces false positives. |
| 20 | Distro feeds | [access.redhat.com/security/data](https://access.redhat.com/security/data), [alas.aws.amazon.com](https://alas.aws.amazon.com/), [linux.oracle.com/security](https://linux.oracle.com/security/), [packages.cgr.dev/chainguard/security.json](https://packages.cgr.dev/chainguard/security.json), [packages.wolfi.dev/os/security.json](https://packages.wolfi.dev/os/security.json), [secdb.alpinelinux.org](https://secdb.alpinelinux.org/), [security-tracker.debian.org](https://security-tracker.debian.org/), [ubuntu.com/security/oval](https://ubuntu.com/security/oval), [www.suse.com/support/security/csaf](https://www.suse.com/support/security/csaf/) | Mostly free public; some vendor support/subscription details may apply | Distro-specific affectedness & patch status. | Required to avoid backport false positives. |
| 21 | Exploit signal feeds | [docs.greynoise.io](https://docs.greynoise.io/), [github.com/rapid7/metasploit-framework](https://github.com/rapid7/metasploit-framework), [project-zero.issues.chromium.org/issues](https://project-zero.issues.chromium.org/issues), [www.exploit-db.com](https://www.exploit-db.com/), [www.kb.cert.org/vuls](https://www.kb.cert.org/vuls/), [www.shadowserver.org](https://www.shadowserver.org/) | Mixed: free public, open-source, free tiers, paid plans, or registration-based access | Exploitability, weaponization, & exposure enrichment. | Use for prioritization, not canonical vulnerability identity. |

> 
> #### [*Back to **`Index`***](#index)
---

## 20. Final structure for all vulnerability management sources & exposure listings

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **Canonical vulnerability records**<br><br>**`Link(s)`:** [github.com/CVEProject/cvelistV5](https://github.com/CVEProject/cvelistV5), [github.com/cisagov/vulnrichment](https://github.com/cisagov/vulnrichment), [nvd.nist.gov](https://nvd.nist.gov/), [www.cve.org](https://www.cve.org/)<br><br>**`Access / Cost`:** Free public / open-source; NVD optional API key | **`Relevance`:** CVE, NVD, CVE schema, & CISA Vulnrichment provide base vulnerability identity & enrichment.<br><br>**`Notes & POIs`:** Use as foundational sources but enrich with vendor/package-specific affectedness. |
| 2 | **Package & ecosystem advisories**<br><br>**`Link(s)`:** [github.com/advisories](https://github.com/advisories), [github.com/github/advisory-database](https://github.com/github/advisory-database), [osv.dev](https://osv.dev/)<br><br>**`Access / Cost`:** Free public / open-source | **`Relevance`:** OSV, GHSA, & language advisory DBs provide package-level affected version data.<br><br>**`Notes & POIs`:** Prefer PURL/package semantics over CPE for OSS dependencies. |
| 3 | **Vendor & distro affectedness**<br><br>**`Link(s)`:** [access.redhat.com/security/data](https://access.redhat.com/security/data), [secdb.alpinelinux.org](https://secdb.alpinelinux.org/), [security-tracker.debian.org](https://security-tracker.debian.org/), [ubuntu.com/security/oval](https://ubuntu.com/security/oval), [www.suse.com/support/security/csaf](https://www.suse.com/support/security/csaf/)<br><br>**`Access / Cost`:** Mostly free public; some vendor support entitlements may apply | **`Relevance`:** CSAF, VEX, OVAL, secdb, OSV, & vendor advisories identify whether a specific product/package is affected.<br><br>**`Notes & POIs`:** Essential for reducing false positives & handling backports. |
| 4 | **Exploitability & prioritization**<br><br>**`Link(s)`:** [github.com/rapid7/metasploit-framework](https://github.com/rapid7/metasploit-framework), [viz.greynoise.io](https://viz.greynoise.io/), [www.cisa.gov/sites/default/files/feeds/known_exploited_vulnerabilities.json](https://www.cisa.gov/sites/default/files/feeds/known_exploited_vulnerabilities.json), [www.exploit-db.com](https://www.exploit-db.com/), [www.first.org/epss](https://www.first.org/epss/)<br><br>**`Access / Cost`:** Mixed: free public, open-source, free tiers / paid plans | **`Relevance`:** KEV, EPSS, SSVC, CVSS, Exploit-DB, Metasploit, & GreyNoise inform urgency.<br><br>**`Notes & POIs`:** Do not conflate severity with exploitability. |
| 5 | **Weakness & adversary mapping**<br><br>**`Link(s)`:** [attack.mitre.org/matrices/enterprise](https://attack.mitre.org/matrices/enterprise/), [atlas.mitre.org](https://atlas.mitre.org/), [capec.mitre.org](https://capec.mitre.org/), [cwe.mitre.org](https://cwe.mitre.org/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** CWE, CAPEC, ATT&CK, & ATLAS map vulnerabilities to weaknesses & adversary behavior.<br><br>**`Notes & POIs`:** Useful for detection engineering & root-cause analysis. |
| 6 | **AI-specific vulnerability context**<br><br>**`Link(s)`:** [atlas.mitre.org](https://atlas.mitre.org/), [owasp.org/www-project- machine-learning-security-top-10](https://owasp.org/www-project-machine-learning-security-top-10/), [owasp.org/www-project-top-10-for-large-language-model-applications](https://owasp.org/www-project-top-10-for-large-language-model-applications/), [www.nist.gov/itl/ai-risk-management-framework](https://www.nist.gov/itl/ai-risk-management-framework)<br><br>**`Access / Cost`:** Free public / open community | **`Relevance`:** ATLAS, OWASP LLM Top 10, OWASP ML Top 10, & NIST AI RMF frame AI/ML risk.<br><br>**`Notes & POIs`:** AI vulnerabilities often lack CVEs; include threat-model & control frameworks. |
| 7 | **SBOM & identity**<br><br>**`Link(s)`:** [cyclonedx.org/specification/overview](https://cyclonedx.org/specification/overview/), [github.com/package-url/purl-spec](https://github.com/package-url/purl-spec), [nvd.nist.gov/products/cpe](https://nvd.nist.gov/products/cpe), [spdx.dev/specifications](https://spdx.dev/specifications/)<br><br>**`Access / Cost`:** Free public / open standards | **`Relevance`:** CycloneDX, SPDX, PURL, CPE, & SWID identify components for matching.<br><br>**`Notes & POIs`:** Accurate inventory is prerequisite to vulnerability assessment. |
| 8 | **Exposure telemetry**<br><br>**`Link(s)`:** [leakix.net](https://leakix.net/), [search.censys.io](https://search.censys.io/), [viz.greynoise.io](https://viz.greynoise.io/), [www.shadowserver.org](https://www.shadowserver.org/), [www.shodan.io](https://www.shodan.io/)<br><br>**`Access / Cost`:** Mixed: free public, free tiers, paid plans, registration-based access | **`Relevance`:** Censys, Shodan, Shadowserver, GreyNoise, LeakIX, & internal inventory help assess real exposure.<br><br>**`Notes & POIs`:** External scan data can be stale or incomplete; join with internal evidence. |
| 9 | **Malicious package & supply-chain compromise**<br><br>**`Link(s)`:** [github.com/advisories?query=type%3Amalware](https://github.com/advisories?query=type%3Amalware), [github.com/ossf/malicious-packages](https://github.com/ossf/malicious-packages), [github.com/ossf/package-analysis](https://github.com/ossf/package-analysis), [security.snyk.io](https://security.snyk.io/), [socket.dev/blog](https://socket.dev/blog), [sonatype.com/resources/vulnerability-database](https://sonatype.com/resources/vulnerability-database)<br><br>**`Access / Cost`:** Mixed: free public, open-source, free tiers / commercial products | **`Relevance`:** Tracks malicious package risk that may not appear as conventional CVEs.<br><br>**`Notes & POIs`:** Essential for supply-chain defense & dependency risk. |
| 10 | **Detection engineering**<br><br>**`Link(s)`:** [codeql.github.com](https://codeql.github.com/), [github.com/projectdiscovery/nuclei](https://github.com/projectdiscovery/nuclei), [google.github.io/oss-fuzz](https://google.github.io/oss-fuzz/), [joern.io](https://joern.io/), [samate.nist.gov/SARD](https://samate.nist.gov/SARD/), [semgrep.dev](https://semgrep.dev/)<br><br>**`Access / Cost`:** Mixed: free/open-source, free public datasets, commercial tiers for some products | **`Relevance`:** CodeQL, Semgrep, Joern, Infer, Nuclei, OSS-Fuzz, SARD, & vulnerability datasets support detection & validation.<br><br>**`Notes & POIs`:** Detection quality depends on rule precision, context, & evidence quality. |
| 11 | **Threat intelligence**<br><br>**`Link(s)`:** [blog.google/threat-analysis-group](https://blog.google/threat-analysis-group/), [blog.talosintelligence.com](https://blog.talosintelligence.com/), [cloud.google.com/blog/topics/threat-intelligence](https://cloud.google.com/blog/topics/threat-intelligence), [unit42.paloaltonetworks.com](https://unit42.paloaltonetworks.com/), [www.microsoft.com/en-us/security/blog/topic/threat-intelligence](https://www.microsoft.com/en-us/security/blog/topic/threat-intelligence/), [www.rapid7.com/blog/tag/vulnerability-management](https://www.rapid7.com/blog/tag/vulnerability-management/), [www.ransomware.live](https://www.ransomware.live/)<br><br>**`Access / Cost`:** Mostly free public blogs/research; commercial threat intel products separate | **`Relevance`:** Mandiant, Microsoft, Google TAG, Unit 42, Talos, Rapid7, ransomware & IOC feeds provide exploitation-in-the-wild context.<br><br>**`Notes & POIs`:** Research sources vary in timeliness, depth, & attribution confidence. |
| 12 | **Compliance & configuration impact**<br><br>**`Link(s)`:** [github.com/ComplianceAsCode/content](https://github.com/ComplianceAsCode/content), [ncp.nist.gov](https://ncp.nist.gov/), [public.cyber.mil/stigs](https://public.cyber.mil/stigs/), [www.cisecurity.org/cis-benchmarks](https://www.cisecurity.org/cis-benchmarks), [www.open-scap.org](https://www.open-scap.org/)<br><br>**`Access / Cost`:** Mostly free public / open-source; CIS benchmarks may require free registration & commercial tools exist | **`Relevance`:** CIS, STIG, SCAP, cloud posture, & Kubernetes benchmarks help assess environmental control weakness.<br><br>**`Notes & POIs`:** These are not vulnerability feeds but determine practical risk & exploitability. |

> 
> #### [*Back to **`Index`***](#index)


---

### `License`
>   Copyright Ⓒ 2025 Keerthana Purushotham <keep.consult@proton.me>.
>   Licensed under the GNU AGPL v3. See LICENSE for details.
> [*see license*](https://github.com/keerthanap8898/CveToad/blob/main/LICENSE)


##### Note:
> *Some vendor/security pages change URLs over time, so treat this as a high-coverage baseline rather than a
mathematically exhaustive list of every possible vulnerability source.*
