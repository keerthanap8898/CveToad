# Vuln Data Sources.cleaned

A consolidated super-set vulnerability-management source inventory for assessing impact, severity, exploitability, exposure, affectedness, prioritization, & remediation of vulnerabilities in technical systems.

## License

Copyright Ⓒ 2025 Keerthana Purushotham \<keep.consult@proton.me>.

Licensed under the GNU AGPL v3. See LICENSE for details.

see license (https://github.com/keerthanap8898/CveToad/blob/main/LICENSE)

{% hint style="info" %}
Some vendor/security pages change URLs over time, so treat this as a high-coverage baseline rather than a mathematically exhaustive list of every possible vulnerability source.

Key access assumptions were checked against official/public docs where feasible: NVD is free with stricter unauthenticated rate limits & higher limits with an API key; GitHub Advisory Database is free/open-source for global advisories; CISA KEV is public; FIRST EPSS is freely available via CSV/API.

Access / Cost labels are best-effort. Many sources are free to read but may require authentication, registration, support entitlement, API keys, paid tiers, or commercial licenses for higher-volume automation, advanced APIs, or complete data. Recheck terms before production ingestion.
{% endhint %}

## 0. Corrections & normalization notes

## 1. Canonical vulnerability identifiers, CVE records & schemas

### 1.1 CVE Program - canonical CVE identity

### 1.2 NVD - CVE enrichment, CPE matching, CVSS & configurations

### 1.3 Optional CVE meta-mirrors / commercial-community enrichments

These are useful as secondary sources, not canonical replacements.

## 2. Open-source vulnerability databases & package advisory sources

### 2.1 OSV ecosystem

### 2.2 GitHub Advisory Database

### 2.3 Language & package ecosystem advisory databases

#### 2.3.1 Go

#### 2.3.2 Rust

#### 2.3.3 Python / PyPI

#### 2.3.4 JavaScript / npm

#### 2.3.5 Java / Maven / JVM

#### 2.3.6 PHP / Composer

#### 2.3.7 Ruby

#### 2.3.8 .NET / NuGet

#### 2.3.9 Erlang / Elixir / Hex

#### 2.3.10 Dart / Flutter / Pub

#### 2.3.11 Swift

## 3. Exploitation, prioritization, severity & risk scoring

### 3.1 Known exploited vulnerability sources

### 3.2 Exploit prediction & scoring

### 3.3 Decision-support frameworks

### 3.4 Public exploit / proof-of-concept / weaponization signals

## 4. CWE, CAPEC, ATT\&CK, ATLAS & weakness-to-attack mapping

### 4.1 CWE - Common Weakness Enumeration

### 4.2 CAPEC - attack patterns

### 4.3 MITRE ATT\&CK

### 4.4 AI/ML-specific adversary frameworks

## 5. Vendor, OS, distribution, container & package affectedness feeds

### 5.1 Scanner-oriented aggregators & vulnerability DB builders

### 5.2 Red Hat / RHEL / CentOS Stream

### 5.3 Debian

### 5.4 Ubuntu / Canonical

### 5.5 Alpine

### 5.6 SUSE / openSUSE

### 5.7 Oracle Linux

### 5.8 Amazon Linux

### 5.9 Fedora, AlmaLinux, Rocky, Arch, Gentoo

### 5.10 Wolfi / Chainguard

## 6. Vendor advisories for enterprise impact assessment

### 6.1 Major OS, browser & platform vendors

### 6.2 Enterprise infrastructure vendors

### 6.3 Cloud provider security bulletins

## 7. SBOM, package identity, VEX & advisory exchange standards

### 7.1 SBOM standards

### 7.2 Package & software identity

### 7.3 Advisory exchange, CSAF & VEX

## 8. Malicious package, supply-chain compromise & package reputation sources

### 8.1 Malicious package databases

### 8.2 Package reputation / dependency health

## 9. Automated vulnerability detection, static analysis, dynamic analysis & research datasets

### 9.1 SAST / code query engines

### 9.2 DAST, IAST, fuzzing & dynamic test sources

### 9.3 Vulnerability-detection research datasets

## 10. ICS, OT, IoT, embedded & medical-device sources

### 10.1 CISA ICS / medical

### 10.2 OT / ICS vendor advisories

### 10.3 IoT / embedded

## 11. Exposure, internet-facing asset & threat telemetry

### 11.1 Internet exposure search engines

### 11.2 Scan/exploitation telemetry

### 11.3 Attack surface management context

## 12. Threat intelligence, malware, ransomware & in-the-wild exploitation context

### 12.1 Major threat research sources

### 12.2 Malware & IOC repositories

## 13. Compliance, baseline configuration & exposure severity standards

These are not vulnerability feeds, but they help assess impact, control failure, configuration exposure, & exploitability in a given environment.

### 13.1 Security configuration & benchmarks

### 13.2 Cloud configuration posture

## 14. Source-code, dependency, artifact & build-chain provenance

### 14.1 Source & artifact provenance

### 14.2 Dependency inventory & graphing

## 15. Practical priority hierarchy for ingestion

### 15.1 Tier 0 - identifiers & inventory

### 15.2 Tier 1 - canonical vulnerability records

### 15.3 Tier 2 - package/ecosystem vulnerability records

### 15.4 Tier 3 - affectedness, distro & vendor truth

### 15.5 Tier 4 - severity & prioritization

### 15.6 Tier 5 - exploitability & weaponization

### 15.7 Tier 6 - weakness, attack-pattern & AI context

### 15.8 Tier 7 - detection engineering & validation

## 16. Recommended canonical data model coverage

A complete vulnerability impact system should be able to ingest or derive the following fields.

### 16.1 Vulnerability identity

### 16.2 Affectedness

### 16.3 Severity & exploitability

### 16.4 Environmental impact

### 16.5 Detection & remediation

## 17. Minimal source set for production use

## 18. Final structure for all vulnerability management sources & exposure listings

## License

Copyright Ⓒ 2025 Keerthana Purushotham \<keep.consult@proton.me>.

Licensed under the GNU AGPL v3. See LICENSE for details.

see license (https://github.com/keerthanap8898/CveToad/blob/main/LICENSE)

## Note

Some vendor/security pages change URLs over time, so treat this as a high-coverage baseline rather than a mathematically exhaustive list of every possible vulnerability source.
