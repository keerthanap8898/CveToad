# Vuln Data Sources

## CveToad Vulnerability Management Source Inventory

### TO-DO

Add prior known(to myself) sources, package lists, pagure, env specifications, hardware specs, OS specific plug ins, Paywalls section/column, super-set schemas, universal pkg-tree in merkle-DAG format,

Remediation sources, SIG Forums and sources, Well-know exploit Blogs, books, papers, course material, youtube videos, tutorials, social media articles, etc. idk lol.

## CveToad Vulnerability Management Source Inventory

A consolidated super-set vulnerability-management source inventory for assessing impact, severity, exploitability, exposure, affectedness, prioritization, & remediation of vulnerabilities in technical systems.

### License

Copyright ■ 2025 Keerthana Purushotham [keep.consult@proton.me](mailto:keep.consult@proton.me).

Licensed under the GNU AGPL v3. See LICENSE for details.

see license (https://github.com/keerthanap8898/CveToad/blob/main/LICENSE)

### Note

* Some vendor/security pages change URLs over time, so treat this as a high-coverage baseline rather than a mathematically exhaustive list of every possible vulnerability source.
* Key access assumptions were checked against official/public docs where feasible: NVD is free with stricter unauthenticated rate limits & higher limits with an API key; GitHub Advisory Database is free/open-source for global advisories; CISA KEV is public; FIRST EPSS is freely available via CSV/API.
* Access / Cost labels are best-effort. Many sources are free to read but may require authentication, registration, support entitlement, API keys, paid tiers, or commercial licenses for higher-volume automation, advanced APIs, or complete data. Recheck terms before production ingestion.

### 0. Corrections & normalization notes

| Sl. # | Title                                     | Link(s)                                                                                                                                                              | Access / Cost                                                                                   | Relevance Notes & POIs                                                                                                                                                                                                      |
| ----- | ----------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1     | Project Zero issue tracker migration bugs | chromium.org/p/project-zero/issues/list, project-zero.issues.chromium.org                                                                                            | Free public web access                                                                          | Tracks high-quality vulnerability research, root-cause analysis, exploitability notes, & coordinated disclosure. Useful for exploitability context & historical vulnerability behavior.                                     |
| 2     | Alpine SecDB mirror normalization         | github.com/alpinelinux/alpine-secdb, secdb.alpinelinux.org                                                                                                           | Free / open-source                                                                              | Provides Alpine package vulnerability affectedness. Important for container images using Alpine as a base.                                                                                                                  |
| 3     | Wolfi / Chainguard feed split             | cgr.dev/chainguard/security.json, packages.wolfi.dev/os/security.json                                                                                                | Free public feed for Wolfi; Chainguard may depend on product entitlement                        | Provides secdb-style security feeds for Wolfi & Chainguard images. Key for modern minimal container images.                                                                                                                 |
| 4     | GitHub Advisory APIs docs                 | github.com/en/graphql/reference/objects#securityadvisory, docs.github.com/en/rest/security-advisories, docs.github.com/en/rest/security-advisories/global-advisories | Free public; authenticated API / repository advisories may require GitHub account & permissions | Enables programmatic access to GitHub advisories, including GHSA records, CVE aliases, ecosystems, version ranges, & malware advisories. Keep both GraphQL & REST.                                                          |
| 5     | NVD feeds vs APIs                         | nvd.nist.gov/developers, nvd.nist.gov/vuln/data-feeds                                                                                                                | Free public; optional free API key for higher rate limits                                       | NVD provides CVE enrichment, CPE configurations, CVSS vectors, CWE mappings, references, & change metadata. Prefer NVD 2.0 APIs for ongoing sync. Use bulk feeds for bootstrapping, archival snapshots, or local mirroring. |

### 1. Canonical vulnerability identifiers, CVE records & schemas

#### 1.1 CVE Program - canonical CVE identity

| Sl. # | Title                                         | Link(s)                                                                    | Access / Cost                                                              | Relevance Notes & POIs                                                                                                           |
| ----- | --------------------------------------------- | -------------------------------------------------------------------------- | -------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------- |
| 1     | CVE.org                                       | www.cve.org                                                                | Free public                                                                | Official CVE program portal for CVE IDs, CNA/ADP governance, CVE lookup, & program documentation.                                |
| 2     | CVE List v5 - official GitHub mirror/cache    | github.com/CVEProject/cvelistV5                                            | Free / open-source public GitHub repo                                      | Primary public GitHub cache of CVE v5 JSON records. Useful for local mirroring, batch parsing, & canonical CVE field extraction. |
| 3     | CVE Record Format schema - direct JSON schema | github.com/CVEProject/cve-schema/blob/main/schema/CVE\_Record\_Format.json | Free / open-source public GitHub repo                                      | Machine-validation schema for CVE v5 records. Required for parser validation & ingestion guardrails.                             |
| 4     | CVE schema repository                         | github.com/CVEProject/cve-schema                                           | Free / open-source public GitHub repo                                      | Contains schema versions, tests, examples, release history, & format evolution.                                                  |
| 5     | CVE Services API / CVE Program API            | cveawg.mitre.org/api-docs                                                  | Free public docs; API workflows may require role/account for CNA functions | Direct CVE lookup & CVE Services API documentation.                                                                              |
| 6     | CVE Authorized Data Publishers - ADPs         | www.cve.org/ProgramOrganization/ADPs                                       | Free public                                                                | Lists ADPs that can enrich CVE records beyond CNA-provided content.                                                              |
| 7     | CISA Vulnrichment - CVE ADP enrichment        | github.com/cisagov/vulnrichment                                            | Free / open-source public GitHub repo                                      | Provides CISA ADP enrichment of CVE records, including SSVC decision points, & sometimes CWE/CVSS details.                       |

#### 1.2 NVD - CVE enrichment, CPE matching, CVSS & configurations

| Sl. # | Title                      | Link(s)                                 | Access / Cost                                             | Relevance Notes & POIs                                                                  |
| ----- | -------------------------- | --------------------------------------- | --------------------------------------------------------- | --------------------------------------------------------------------------------------- |
| 1     | NVD home                   | nvd.nist.gov                            | Free public                                               | U.S. government vulnerability-management repository.                                    |
| 2     | NVD CVE API 2.0            | nvd.nist.gov/developers/vulnerabilities | Free public; optional free API key for higher rate limits | Retrieves CVEs with CVSS, weaknesses, references, CPE configurations, & change history. |
| 3     | NVD CPE API 2.0            | nvd.nist.gov/developers/products        | Free public; optional free API key for higher rate limits | Provides CPE dictionary & CPE match criteria for product/platform matching.             |
| 4     | NVD Data Feeds             | nvd.nist.gov/vuln/data-feeds            | Free public                                               | Bulk JSON feeds for CVEs, CPE dictionary, & CPE match feeds.                            |
| 5     | NVD CVSS resources         | nvd.nist.gov/vuln-metrics/cvss          | Free public                                               | CVSS calculators, vector definitions, & severity scoring references.                    |
| 6     | NVD CPE Dictionary         | nvd.nist.gov/products/cpe               | Free public                                               | CPE product naming & matching basis.                                                    |
| 7     | NVD API documentation root | nvd.nist.gov/developers                 | Free public                                               | API family documentation for NVD data access.                                           |
| 8     | NVD CVE Change History API | nvd.nist.gov/developers/vulnerabilities | Free public; optional free API key for higher rate limits | Enables monitoring changes to CVE enrichment, scoring, references, & configurations.    |

#### 1.3 Optional CVE meta-mirrors / commercial-community enrichments

These are useful as secondary sources, not canonical replacements.

| Sl. # | Title            | Link(s)                | Access / Cost                                                | Relevance Notes & POIs                                                           |
| ----- | ---------------- | ---------------------- | ------------------------------------------------------------ | -------------------------------------------------------------------------------- |
| 1     | VulnCheck NVD++  | www.vulncheck.com/nvd2 | Commercial                                                   | Aggregated vulnerability intelligence that can supplement CVE/NVD/KEV workflows. |
| 2     | Vulners          | vulners.com            | Free web search; API/advanced features may require paid plan | Vulnerability intelligence aggregator across many advisory & exploit sources.    |
| 3     | OpenCVE          | www.opencve.io         | Free tier / paid plans                                       | CVE monitoring, subscriptions, change tracking, & alerting workflows.            |
| 4     | CIRCL CVE Search | cve.circl.lu           | Free public                                                  | CVE search & enrichment source, historically useful for threat-intel workflows.  |

### 2. Open-source vulnerability databases & package advisory sources

#### 2.1 OSV ecosystem

| Sl. # | Title                      | Link(s)                                               | Access / Cost                         | Relevance Notes & POIs                                                                                |
| ----- | -------------------------- | ----------------------------------------------------- | ------------------------------------- | ----------------------------------------------------------------------------------------------------- |
| 1     | OSV main site              | osv.dev                                               | Free public / open data               | Aggregates OSS vulnerabilities by package ecosystem, version, commit, & aliases.                      |
| 2     | OSV vulnerability list     | osv.dev/list                                          | Free public                           | Human-browsable OSV records.                                                                          |
| 3     | OSV full database download | google.github.io/osv.dev/data/#full-database-download | Free public / open data               | Full database ZIP, including withdrawn records, via gs://osv-vulnerabilities/all.                     |
| 4     | OSV data sources page      | google.github.io/osv.dev/data                         | Free public                           | Per-ecosystem downloads & full-database download.                                                     |
| 5     | OSV schema rendered spec   | ossf.github.io/osv-schema                             | Free public / open-source             | Standard interchange format for OSS vulnerability records.                                            |
| 6     | OSV schema GitHub repo     | github.com/ossf/osv-schema                            | Free / open-source public GitHub repo | Schema source, releases, bindings, & tooling.                                                         |
| 7     | OSV API docs               | google.github.io/osv.dev/post-v1-query/               | Free public API                       | Query vulnerabilities by package, version, commit, or vulnerability ID.                               |
| 8     | OSV Scanner                | google.github.io/osv-scanner                          | Free public / open-source             | Reference scanner using OSV data.                                                                     |
| 9     | OSV Scanner GitHub         | github.com/google/osv-scanner                         | Free / open-source public GitHub repo | Scanner implementation, matching logic, & lockfile parsing.                                           |
| 10    | OSV ecosystem list         | osv.dev/list                                          | Free public                           | Ecosystem browsing for Maven, npm, PyPI, Go, crates.io, Debian, Alpine, Ubuntu, Wolfi, OSS-Fuzz, etc. |

#### 2.2 GitHub Advisory Database

| Sl. # | Title                                        | Link(s)                                                                                                             | Access / Cost                                                      | Relevance Notes & POIs                                                                |
| ----- | -------------------------------------------- | ------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------ | ------------------------------------------------------------------------------------- |
| 1     | GitHub Advisory Database - web               | github.com/advisories                                                                                               | Free public                                                        | GitHub-reviewed, unreviewed, malware, GHSA, & CVE advisory records across ecosystems. |
| 2     | GitHub Advisory Database repo                | github.com/github/advisory-database                                                                                 | Free / open-source public GitHub repo                              | Raw advisory data for local ingestion.                                                |
| 3     | About GitHub Advisory Database               | docs.github.com/en/code-security/concepts/vulnerability-reporting-and-management/about-the-github-advisory-database | Free public docs                                                   | Explains reviewed, unreviewed, & malware advisory model.                              |
| 4     | GitHub Security Advisory GraphQL             | docs.github.com/en/graphql/reference/objects#objectsecurityadvisory                                                 | Free docs; API usage may require GitHub auth token                 | Programmatic advisory metadata access via GraphQL.                                    |
| 5     | GitHub REST API - global security advisories | docs.github.com/en/rest/security-advisories/global-advisories                                                       | Free public API; auth recommended for higher rate limits           | Listing & retrieving global security advisories.                                      |
| 6     | GitHub REST API - security advisories root   | docs.github.com/en/rest/security-advisories                                                                         | Free public docs; some repository endpoints require permissions    | Root documentation for global & repository security advisory endpoints.               |
| 7     | GitHub Dependabot alerts REST API            | docs.github.com/en/rest/dependabot/alerts                                                                           | Requires GitHub account, repository access, & relevant permissions | Repository-specific vulnerability exposure from dependency graph.                     |
| 8     | Dependabot supported ecosystems              | docs.github.com/en/code-security/reference/supply-chain-security/supported-ecosystems-and-repositories              | Free public docs                                                   | Supported ecosystem list for GitHub dependency graph & alerts.                        |
| 9     | GitHub malware advisories                    | github.com/advisories?query=type%3Amalware                                                                          | Free public                                                        | Malicious package advisories.                                                         |
| 10    | GitHub npm advisories                        | github.com/advisories?query=ecosystem%3Anpm                                                                         | Free public                                                        | npm ecosystem advisories.                                                             |
| 11    | GitHub pip advisories                        | github.com/advisories?query=ecosystem%3Apip                                                                         | Free public                                                        | Python/PyPI advisories.                                                               |
| 12    | GitHub Maven advisories                      | github.com/advisories?query=ecosystem%3Amaven                                                                       | Free public                                                        | Maven ecosystem advisories.                                                           |
| 13    | GitHub NuGet advisories                      | github.com/advisories?query=ecosystem%3Anuget                                                                       | Free public                                                        | NuGet ecosystem advisories.                                                           |
| 14    | GitHub Go advisories                         | github.com/advisories?query=ecosystem%3Ago                                                                          | Free public                                                        | Go ecosystem advisories.                                                              |
| 15    | GitHub RubyGems advisories                   | github.com/advisories?query=ecosystem%3Arubygems                                                                    | Free public                                                        | RubyGems advisories.                                                                  |
| 16    | GitHub Rust advisories                       | github.com/advisories?query=ecosystem%3Arust                                                                        | Free public                                                        | Rust crate advisories.                                                                |
| 17    | GitHub Composer advisories                   | github.com/advisories?query=ecosystem%3Acomposer                                                                    | Free public                                                        | PHP Composer advisories.                                                              |
| 18    | GitHub Pub advisories                        | github.com/advisories?query=ecosystem%3Apub                                                                         | Free public                                                        | Dart/Pub advisories.                                                                  |
| 19    | GitHub Swift advisories                      | github.com/advisories?query=ecosystem%3Aswift                                                                       | Free public                                                        | Swift package advisories.                                                             |
| 20    | GitHub Erlang advisories                     | github.com/advisories?query=ecosystem%3Aerlang                                                                      | Free public                                                        | Erlang/Hex advisories.                                                                |

#### 2.3 Language & package ecosystem advisory databases

**2.3.1 Go**

| Sl. # | Title                          | Link(s)                                      | Access / Cost                | Relevance Notes & POIs                               |
| ----- | ------------------------------ | -------------------------------------------- | ---------------------------- | ---------------------------------------------------- |
| 1     | Go Vulnerability Database      | vuln.go.dev                                  | Free public / open data      | Official Go vulnerability database for Go modules.   |
| 2     | Go vulnerability database docs | go.dev/doc/security/vuln/database            | Free public docs             | Explains Go vulnerability DB data model & OSV usage. |
| 3     | Go vuln browser                | pkg.go.dev/vuln                              | Free public                  | Human-readable curated Go vulnerability reports.     |
| 4     | Go vuln tooling                | pkg.go.dev/golang.org/x/vuln/cmd/govulncheck | Free / open-source Go module | Go source/binary vulnerability checking.             |

**2.3.2 Rust**

| Sl. # | Title                      | Link(s)                                          | Access / Cost                         | Relevance Notes & POIs               |
| ----- | -------------------------- | ------------------------------------------------ | ------------------------------------- | ------------------------------------ |
| 1     | RustSec                    | rustsec.org                                      | Free public / open-source ecosystem   | Rust crate advisory ecosystem.       |
| 2     | RustSec advisory DB repo   | github.com/RustSec/advisory-db                   | Free / open-source public GitHub repo | Machine-ingestible Rust advisories.  |
| 3     | RustSec advisories browser | rustsec.org/advisories                           | Free public                           | Human-browsable Rust advisories.     |
| 4     | cargo-audit                | github.com/RustSec/rustsec/tree/main/cargo-audit | Free / open-source public GitHub repo | RustSec-based vulnerability scanner. |

**2.3.3 Python / PyPI**

| Sl. # | Title                  | Link(s)                           | Access / Cost                                               | Relevance Notes & POIs                      |
| ----- | ---------------------- | --------------------------------- | ----------------------------------------------------------- | ------------------------------------------- |
| 1     | PyPA advisory database | github.com/pypa/advisory-database | Free / open-source public GitHub repo                       | Python/PyPI advisory source.                |
| 2     | PyPI security page     | pypi.org/security                 | Free public                                                 | PyPI security reporting & advisory context. |
| 3     | pip-audit              | github.com/pypa/pip-audit         | Free / open-source public GitHub repo                       | Python dependency vulnerability scanner.    |
| 4     | Safety DB              | github.com/pyupio/safety-db       | Free public GitHub repo; related products may be commercial | Historical Python advisory source.          |

**2.3.4 JavaScript / npm**

| Sl. # | Title                          | Link(s)                                     | Access / Cost                                            | Relevance Notes & POIs                                              |
| ----- | ------------------------------ | ------------------------------------------- | -------------------------------------------------------- | ------------------------------------------------------------------- |
| 1     | npm advisories via GitHub      | github.com/advisories?query=ecosystem%3Anpm | Free public                                              | npm ecosystem vulnerability advisories.                             |
| 2     | Node.js Security Working Group | github.com/nodejs/security-wg               | Free / open-source public GitHub repo                    | Node ecosystem security coordination & historical advisory sources. |
| 3     | npm audit docs                 | docs.npmjs.com/cli/commands/npm-audit       | Free public docs                                         | Documents npm audit behavior.                                       |
| 4     | Socket.dev security research   | socket.dev/blog                             | Free public blog; product/API features may be commercial | Malicious package & JS supply-chain threat intel.                   |

**2.3.5 Java / Maven / JVM**

| Sl. # | Title                           | Link(s)                                       | Access / Cost                                              | Relevance Notes & POIs                                                     |
| ----- | ------------------------------- | --------------------------------------------- | ---------------------------------------------------------- | -------------------------------------------------------------------------- |
| 1     | Sonatype OSS Index              | ossindex.sonatype.org                         | Free tier / API terms; Sonatype products may be commercial | OSS vulnerability intelligence commonly used for Maven & other ecosystems. |
| 2     | Sonatype vulnerability database | sonatype.com/resources/vulnerability-database | Free public search / commercial ecosystem                  | Sonatype vulnerability intelligence database.                              |
| 3     | Maven Central                   | central.sonatype.com                          | Free public                                                | Package identity & metadata for JVM packages.                              |
| 4     | OSS Index API docs              | ossindex.sonatype.org/doc/rest                | Free tier / API terms                                      | REST API access for OSS Index.                                             |

**2.3.6 PHP / Composer**

| Sl. # | Title                             | Link(s)                                       | Access / Cost                         | Relevance Notes & POIs             |
| ----- | --------------------------------- | --------------------------------------------- | ------------------------------------- | ---------------------------------- |
| 1     | FriendsOfPHP security advisories  | github.com/FriendsOfPHP/security-advisories   | Free / open-source public GitHub repo | PHP Composer package advisories.   |
| 2     | Packagist security advisories API | packagist.org/apidoc#list-security-advisories | Free public API docs / public API     | Composer package advisory API.     |
| 3     | Composer audit docs               | getcomposer.org/doc/03-cli.md#audit           | Free public docs                      | Documents Composer audit behavior. |

**2.3.7 Ruby**

| Sl. # | Title               | Link(s)                             | Access / Cost                         | Relevance Notes & POIs                 |
| ----- | ------------------- | ----------------------------------- | ------------------------------------- | -------------------------------------- |
| 1     | RubySec advisory DB | github.com/rubysec/ruby-advisory-db | Free / open-source public GitHub repo | RubyGems advisories.                   |
| 2     | Bundler audit       | github.com/rubysec/bundler-audit    | Free / open-source public GitHub repo | Ruby dependency vulnerability scanner. |

**2.3.8 .NET / NuGet**

| Sl. # | Title                       | Link(s)                                                    | Access / Cost    | Relevance Notes & POIs            |
| ----- | --------------------------- | ---------------------------------------------------------- | ---------------- | --------------------------------- |
| 1     | NuGet advisories via GitHub | github.com/advisories?query=ecosystem%3Anuget              | Free public      | NuGet ecosystem advisories.       |
| 2     | NuGet audit docs            | learn.microsoft.com/en-us/nuget/concepts/auditing-packages | Free public docs | Documents NuGet package auditing. |

**2.3.9 Erlang / Elixir / Hex**

| Sl. # | Title                        | Link(s)                                        | Access / Cost | Relevance Notes & POIs                       |
| ----- | ---------------------------- | ---------------------------------------------- | ------------- | -------------------------------------------- |
| 1     | Erlang advisories via GitHub | github.com/advisories?query=ecosystem%3Aerlang | Free public   | Erlang/Hex advisories.                       |
| 2     | Hex package manager          | hex.pm                                         | Free public   | Package registry for Erlang/Elixir packages. |

**2.3.10 Dart / Flutter / Pub**

| Sl. # | Title                     | Link(s)                                     | Access / Cost | Relevance Notes & POIs                          |
| ----- | ------------------------- | ------------------------------------------- | ------------- | ----------------------------------------------- |
| 1     | Pub advisories via GitHub | github.com/advisories?query=ecosystem%3Apub | Free public   | Dart/Pub advisories.                            |
| 2     | Dart package repository   | pub.dev                                     | Free public   | Package registry for Dart/Flutter dependencies. |

**2.3.11 Swift**

| Sl. # | Title                       | Link(s)                                       | Access / Cost | Relevance Notes & POIs                      |
| ----- | --------------------------- | --------------------------------------------- | ------------- | ------------------------------------------- |
| 1     | Swift advisories via GitHub | github.com/advisories?query=ecosystem%3Aswift | Free public   | Swift ecosystem advisories.                 |
| 2     | Swift Package Index         | swiftpackageindex.com                         | Free public   | Swift package metadata & ecosystem context. |

### 3. Exploitation, prioritization, severity & risk scoring

#### 3.1 Known exploited vulnerability sources

| Sl. # | Title                  | Link(s)                                                                               | Access / Cost                                                        | Relevance Notes & POIs                                    |
| ----- | ---------------------- | ------------------------------------------------------------------------------------- | -------------------------------------------------------------------- | --------------------------------------------------------- |
| 1     | CISA KEV catalog - web | www.cisa.gov/known-exploited-vulnerabilities-catalog                                  | Free public                                                          | Authoritative catalog of known exploited vulnerabilities. |
| 2     | CISA KEV print view    | www.cisa.gov/known-exploited-vulnerabilities-catalog-print                            | Free public                                                          | Human-readable print-oriented KEV view.                   |
| 3     | CISA KEV JSON feed     | www.cisa.gov/sites/default/files/feeds/known\_exploited\_vulnerabilities.json         | Free public feed                                                     | Machine-readable KEV feed.                                |
| 4     | CISA KEV JSON schema   | www.cisa.gov/sites/default/files/feeds/known\_exploited\_vulnerabilities\_schema.json | Free public feed                                                     | Schema for KEV JSON validation.                           |
| 5     | CISA KEV GitHub mirror | github.com/cisagov/kev-data                                                           | Free / open-source public GitHub repo                                | GitHub mirror of KEV data.                                |
| 6     | VulnCheck KEV          | vulncheck.com/kev                                                                     | Commercial                                                           | Expanded KEV-like exploitation intelligence.              |
| 7     | Shadowserver reports   | www.shadowserver.org                                                                  | Free for eligible organizations; access/registration may be required | Internet-scale exploitation & exposure observations.      |
| 8     | GreyNoise Visualizer   | viz.greynoise.io                                                                      | Free tier / paid plans                                               | Internet scanning/exploitation noise & actor context.     |
| 9     | GreyNoise API docs     | docs.greynoise.io                                                                     | Free tier / paid plans; API key required                             | API for IP-based exploitation telemetry enrichment.       |

#### 3.2 Exploit prediction & scoring

| Sl. # | Title                           | Link(s)                                        | Access / Cost              | Relevance Notes & POIs                        |
| ----- | ------------------------------- | ---------------------------------------------- | -------------------------- | --------------------------------------------- |
| 1     | FIRST EPSS overview             | www.first.org/epss                             | Free public / open data    | Exploit Prediction Scoring System.            |
| 2     | FIRST EPSS API                  | www.first.org/epss/api                         | Free public API            | Endpoint for EPSS scores.                     |
| 3     | FIRST EPSS data & CSV downloads | www.first.org/epss/data\_stats                 | Free public data downloads | Current & historical EPSS CSV data reference. |
| 4     | Historical EPSS scores GitHub   | github.com/empiricalsec/epss\_scores           | Free public GitHub repo    | Daily historical EPSS snapshots.              |
| 5     | FIRST CVSS                      | www.first.org/cvss                             | Free public                | Official CVSS specification home.             |
| 6     | FIRST CVSS v4.0                 | www.first.org/cvss/v4.0/specification-document | Free public                | CVSS v4.0 specification.                      |
| 7     | FIRST CVSS v3.1                 | www.first.org/cvss/v3.1/specification-document | Free public                | CVSS v3.1 specification.                      |
| 8     | NVD CVSS resources              | nvd.nist.gov/vuln-metrics/cvss                 | Free public                | CVSS calculators & vector references.         |

#### 3.3 Decision-support frameworks

| Sl. # | Title                                    | Link(s)                                                                                                 | Access / Cost                         | Relevance Notes & POIs                                                                  |
| ----- | ---------------------------------------- | ------------------------------------------------------------------------------------------------------- | ------------------------------------- | --------------------------------------------------------------------------------------- |
| 1     | CISA SSVC                                | www.cisa.gov/stakeholder-specific-vulnerability-categorization-ssvc                                     | Free public                           | Stakeholder-Specific Vulnerability Categorization for vulnerability response decisions. |
| 2     | CERT/CC SSVC project                     | github.com/CERTCC/SSVC                                                                                  | Free / open-source public GitHub repo | SSVC model artifacts, examples, & discussions.                                          |
| 3     | CISA Vulnrichment                        | github.com/cisagov/vulnrichment                                                                         | Free / open-source public GitHub repo | CISA ADP enrichment & SSVC decision points.                                             |
| 4     | CISA Binding Operational Directive 22-01 | www.cisa.gov/news-events/directives/bod-22-01-reducing-significant-risk-known-exploited-vulnerabilities | Free public                           | Operational requirement context for KEV remediation.                                    |
| 5     | CISA Cybersecurity Advisories            | www.cisa.gov/cybersecurity-advisories                                                                   | Free public                           | Broader CISA advisory feed.                                                             |
| 6     | CISA Alerts                              | www.cisa.gov/news-events/cybersecurity-advisories                                                       | Free public                           | CISA alert/advisory listing.                                                            |

#### 3.4 Public exploit / proof-of-concept / weaponization signals

| Sl. # | Title                                       | Link(s)                                                             | Access / Cost                                                                         | Relevance Notes & POIs                                                            |
| ----- | ------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- |
| 1     | Exploit-DB                                  | www.exploit-db.com                                                  | Free public                                                                           | Public exploit archive.                                                           |
| 2     | SearchSploit                                | www.exploit-db.com/searchsploit                                     | Free / open-source tool                                                               | CLI interface for Exploit-DB.                                                     |
| 3     | Exploit-DB GitLab mirror                    | gitlab.com/exploit-database/exploitdb                               | Free public GitLab repo                                                               | Git mirror of Exploit-DB content.                                                 |
| 4     | Metasploit Framework                        | github.com/rapid7/metasploit-framework                              | Free / open-source public GitHub repo                                                 | Exploit framework containing modules, payloads, & auxiliary checks.               |
| 5     | Metasploit exploit modules                  | github.com/rapid7/metasploit-framework/tree/master/modules/exploits | Free / open-source public GitHub repo                                                 | Practical signal that a vulnerability has weaponized exploit implementation.      |
| 6     | Packet Storm Security exploits              | packetstormsecurity.com/files/tags/exploit/                         | Free public                                                                           | Public exploit & advisory archive.                                                |
| 7     | 0day.today                                  | 0day.today                                                          | Mixed                                                                                 | Public zero-day/exploit listing.                                                  |
| 8     | Project Zero blog                           | googleprojectzero.blogspot.com                                      | Free public                                                                           | High-quality root-cause & exploitation writeups.                                  |
| 9     | Project Zero issue tracker - current        | project-zero.issues.chromium.org                                    | Free public; some issue details may be restricted before disclosure                   | Current Project Zero issue tracker.                                               |
| 10    | Project Zero issue tracker - old/historical | bugs.chromium.org/p/project-zero/issues/list                        | Free public historical access where still available                                   | Historical Project Zero issue tracker link.                                       |
| 11    | CERT/CC Vulnerability Notes Database        | www.kb.cert.org/vuls                                                | Free public                                                                           | Coordinated disclosure context, affected vendors, technical notes, & remediation. |
| 12    | CERT/CC VINCE public notes                  | kb.cert.org/vuls/html                                               | Free public                                                                           | Modern public vulnerability note interface.                                       |
| 13    | Rapid7 AttackerKB                           | attackerkb.com                                                      | Free public content; some Rapid7 ecosystem features may be commercial                 | Exploitability & attacker-value context.                                          |
| 14    | Nuclei templates                            | github.com/projectdiscovery/nuclei-templates                        | Free / open-source public GitHub repo                                                 | Exposed-condition detection templates.                                            |
| 15    | ProjectDiscovery Nuclei                     | github.com/projectdiscovery/nuclei                                  | Free / open-source public GitHub repo; commercial ProjectDiscovery offerings separate | Template-based vulnerability & exposure scanner.                                  |
| 16    | Horizon3.ai research                        | www.horizon3.ai/attack-research                                     | Free public research; commercial products separate                                    | PoC & attack-path writeups.                                                       |
| 17    | watchTowr Labs                              | labs.watchtowr.com                                                  | Free public research; commercial services separate                                    | Vulnerability research & exploitation details.                                    |
| 18    | Assetnote research                          | www.assetnote.io/resources/research                                 | Free public research; commercial services separate                                    | Exploit research & vulnerability detection signatures.                            |

### 4. CWE, CAPEC, ATT\&CK, ATLAS & weakness-to-attack mapping

#### 4.1 CWE - Common Weakness Enumeration

| Sl. # | Title                         | Link(s)                                                 | Access / Cost | Relevance Notes & POIs                                    |
| ----- | ----------------------------- | ------------------------------------------------------- | ------------- | --------------------------------------------------------- |
| 1     | CWE home                      | cwe.mitre.org                                           | Free public   | Common Weakness Enumeration root.                         |
| 2     | CWE downloads                 | cwe.mitre.org/data/downloads.html                       | Free public   | XML, CSV, archive bundles, & views for machine ingestion. |
| 3     | CWE latest PDF                | cwe.mitre.org/data/published/cwe\_latest.pdf            | Free public   | PDF publication of latest CWE content.                    |
| 4     | CWE reports                   | cwe.mitre.org/data/reports.html                         | Free public   | Reports & curated views of CWE data.                      |
| 5     | CWE chains & composites       | cwe.mitre.org/data/reports/chains\_and\_composites.html | Free public   | Describes weakness chains & composite weaknesses.         |
| 6     | CWE schema docs               | cwe.mitre.org/documents/schema/index.html               | Free public   | Schema documentation for CWE data.                        |
| 7     | CWE data definitions          | cwe.mitre.org/data/definitions/1000.html                | Free public   | CWE views & weakness hierarchy.                           |
| 8     | CWE Top 25                    | cwe.mitre.org/top25                                     | Free public   | Most dangerous software weaknesses.                       |
| 9     | CWE AI/ML category - CWE-1448 | cwe.mitre.org/data/definitions/1448.html                | Free public   | AI/ML-related weakness category.                          |
| 10    | CWE AI Working Group          | cwe.mitre.org/community/working\_groups.html            | Free public   | CWE/CVE AI Working Group context.                         |

#### 4.2 CAPEC - attack patterns

| Sl. # | Title                                          | Link(s)                                     | Access / Cost                         | Relevance Notes & POIs                                 |
| ----- | ---------------------------------------------- | ------------------------------------------- | ------------------------------------- | ------------------------------------------------------ |
| 1     | CAPEC home                                     | capec.mitre.org                             | Free public                           | Catalog of attack patterns used to exploit weaknesses. |
| 2     | CAPEC downloads                                | capec.mitre.org/data/downloads.html         | Free public                           | XML/CSV attack-pattern bundles.                        |
| 3     | CAPEC schema docs                              | capec.mitre.org/documents/schema/index.html | Free public                           | Schema docs for CAPEC data.                            |
| 4     | CAPEC data index                               | capec.mitre.org/data/index.html             | Free public                           | Browsable CAPEC entries & views.                       |
| 5     | MITRE CTI repository - ATT\&CK & CAPEC in STIX | github.com/mitre/cti                        | Free / open-source public GitHub repo | MITRE ATT\&CK & CAPEC datasets expressed in STIX 2.0.  |

#### 4.3 MITRE ATT\&CK

| Sl. # | Title                     | Link(s)                                                                 | Access / Cost                         | Relevance Notes & POIs                                          |
| ----- | ------------------------- | ----------------------------------------------------------------------- | ------------------------------------- | --------------------------------------------------------------- |
| 1     | ATT\&CK Enterprise Matrix | attack.mitre.org/matrices/enterprise                                    | Free public                           | Enterprise adversary tactics & techniques.                      |
| 2     | ATT\&CK Matrices          | attack.mitre.org/matrices                                               | Free public                           | ATT\&CK matrices across domains.                                |
| 3     | ATT\&CK Data & Tools      | attack.mitre.org/resources/attack-data-and-tools                        | Free public                           | ATT\&CK Navigator, STIX/TAXII, Workbench, & tooling references. |
| 4     | ATT\&CK STIX data repo    | github.com/mitre-attack/attack-stix-data                                | Free / open-source public GitHub repo | Machine-readable ATT\&CK STIX data.                             |
| 5     | MITRE CTI repository      | github.com/mitre/cti                                                    | Free / open-source public GitHub repo | MITRE CTI STIX datasets.                                        |
| 6     | ATT\&CK Navigator         | mitre-attack.github.io/attack-navigator                                 | Free / open-source web tool           | Visual mapping of techniques to campaigns, risks, or controls.  |
| 7     | ATT\&CK Workbench         | github.com/center-for-threat-informed-defense/attack-workbench-frontend | Free / open-source public GitHub repo | Tooling for ATT\&CK customization & management.                 |
| 8     | ATT\&CK TAXII server docs | attack.mitre.org/resources/attack-data-and-tools                        | Free public                           | TAXII/STIX access docs.                                         |

#### 4.4 AI/ML-specific adversary frameworks

| Sl. # | Title                                             | Link(s)                                                                                                        | Access / Cost                         | Relevance Notes & POIs                                                              |
| ----- | ------------------------------------------------- | -------------------------------------------------------------------------------------------------------------- | ------------------------------------- | ----------------------------------------------------------------------------------- |
| 1     | MITRE ATLAS                                       | atlas.mitre.org                                                                                                | Free public                           | Living knowledge base of adversary tactics & techniques against AI-enabled systems. |
| 2     | MITRE ATLAS matrix                                | atlas.mitre.org/matrices/ATLAS                                                                                 | Free public                           | Matrix view of AI adversary tactics & techniques.                                   |
| 3     | MITRE ATLAS techniques                            | atlas.mitre.org/techniques                                                                                     | Free public                           | Technique-level ATLAS entries.                                                      |
| 4     | MITRE ATLAS case studies                          | atlas.mitre.org/studies                                                                                        | Free public                           | Case studies of AI attacks & failures.                                              |
| 5     | MITRE ATLAS GitHub / Adversarial ML Threat Matrix | github.com/mitre/advmlthreatmatrix                                                                             | Free / open-source public GitHub repo | Historical & structured project data for adversarial ML threat matrix.              |
| 6     | MITRE SAFE-AI report                              | atlas.mitre.org/pdf-files/SAFEAI\_Full\_Report.pdf                                                             | Free public PDF                       | AI system risk mapping across model, data, platform, & environment layers.          |
| 7     | OWASP Top 10 for LLM Applications                 | owasp.org/www-project-top-10-for-large-language-model-applications                                             | Free / open-source community project  | Practical LLM application vulnerability taxonomy.                                   |
| 8     | OWASP Top 10 for Machine Learning Security        | owasp.org/www-project-machine-learning-security-top-10                                                         | Free / open-source community project  | ML-specific application/security risk taxonomy.                                     |
| 9     | OWASP AI Exchange                                 | owaspai.org                                                                                                    | Free public                           | AI security risks, controls, & threat modeling references.                          |
| 10    | NIST AI Risk Management Framework                 | www.nist.gov/itl/ai-risk-management-framework                                                                  | Free public                           | AI risk management framework.                                                       |
| 11    | NIST AI RMF 1.0 PDF                               | nvlpubs.nist.gov/nistpubs/ai/NIST.AI.100-1.pdf                                                                 | Free public PDF                       | AI RMF 1.0 document.                                                                |
| 12    | NIST AI 600-1 - Generative AI Profile             | www.nist.gov/publications/artificial-intelligence-risk-management-framework-generative-artificial-intelligence | Free public                           | GenAI risk profile companion to AI RMF.                                             |
| 13    | NIST adversarial machine learning taxonomy        | www.nist.gov/publications/adversarial-machine-learning-taxonomy-and-terminology-attacks-and-mitigations        | Free public                           | Taxonomy & terminology for adversarial ML attacks & mitigations.                    |
| 14    | MLCommons AI Safety                               | mlcommons.org/working-groups/ai-safety                                                                         | Free public community resource        | AI safety benchmarks & working group context.                                       |

### 5. Vendor, OS, distribution, container & package affectedness feeds

#### 5.1 Scanner-oriented aggregators & vulnerability DB builders

| Sl. # | Title                              | Link(s)                                                                                     | Access / Cost                                                      | Relevance Notes & POIs                                                              |
| ----- | ---------------------------------- | ------------------------------------------------------------------------------------------- | ------------------------------------------------------------------ | ----------------------------------------------------------------------------------- |
| 1     | NeuVector vul-dbgen                | github.com/neuvector/vul-dbgen                                                              | Free / open-source public GitHub repo                              | Vulnerability DB generation source.                                                 |
| 2     | NeuVector vul-source               | github.com/neuvector/vul-source                                                             | Free / open-source public GitHub repo                              | Vulnerability source data used by NeuVector workflows.                              |
| 3     | Aqua Trivy vulnerability docs      | trivy.dev/docs/latest/scanner/vulnerability/                                                | Free public docs                                                   | Scanner behavior across OS packages, language packages, misconfig, Kubernetes, etc. |
| 4     | Trivy DB                           | github.com/aquasecurity/trivy-db                                                            | Free / open-source public GitHub repo                              | Converts raw advisories into Trivy DB format.                                       |
| 5     | Trivy Java DB                      | github.com/aquasecurity/trivy-java-db                                                       | Free / open-source public GitHub repo                              | Java-specific vulnerability database used by Trivy.                                 |
| 6     | Trivy database configuration docs  | trivy.dev/docs/latest/configuration/db/                                                     | Free public docs                                                   | Documents Trivy DB artifacts & configuration.                                       |
| 7     | Anchore Grype                      | github.com/anchore/grype                                                                    | Free / open-source public GitHub repo                              | Vulnerability scanner for container images & filesystems.                           |
| 8     | Anchore Grype DB                   | github.com/anchore/grype-db                                                                 | Free / open-source public GitHub repo                              | Builds Grype vulnerability database from upstream sources.                          |
| 9     | Anchore Syft                       | github.com/anchore/syft                                                                     | Free / open-source public GitHub repo                              | SBOM generation for scanning & exposure matching.                                   |
| 10    | Quay ClairCore                     | github.com/quay/claircore                                                                   | Free / open-source public GitHub repo                              | Clair vulnerability matching engine core.                                           |
| 11    | Clair                              | github.com/quay/clair                                                                       | Free / open-source public GitHub repo                              | Container vulnerability scanner.                                                    |
| 12    | VulnerableCode                     | github.com/nexB/vulnerablecode                                                              | Free / open-source public GitHub repo                              | Open vulnerability DB aggregator.                                                   |
| 13    | VulnerableCode importer docs       | vulnerablecode.readthedocs.io/en/latest/importers\_link.html                                | Free public docs                                                   | Lists supported importer sources.                                                   |
| 14    | Dependency-Track                   | dependencytrack.org                                                                         | Free / open-source core project                                    | SBOM-oriented vulnerability management platform.                                    |
| 15    | Dependency-Track data sources docs | docs.dependencytrack.org/datasources/overview/                                              | Free public docs                                                   | Documents Dependency-Track data sources.                                            |
| 16    | Dependency-Track GitHub Advisories | docs.dependencytrack.org/datasources/github-advisories/                                     | Free public docs                                                   | Mirrors GHSA via GitHub public GraphQL API.                                         |
| 17    | OpenVAS / Greenbone Community Feed | www.greenbone.net/en/community-feed/                                                        | Free community feed; commercial Greenbone feeds/products available | Network vulnerability test feed.                                                    |
| 18    | Wazuh vulnerability detector       | documentation.wazuh.com/current/user-manual/capabilities/vulnerability-detection/index.html | Free public docs; Wazuh open-source, commercial support available  | Endpoint vulnerability detection capability.                                        |

#### 5.2 Red Hat / RHEL / CentOS Stream

| Sl. # | Title                          | Link(s)                                                                                                            | Access / Cost                                                                   | Relevance Notes & POIs                                 |
| ----- | ------------------------------ | ------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------- | ------------------------------------------------------ |
| 1     | Red Hat Security Data          | access.redhat.com/security/data                                                                                    | Free public data; some product details/support content may require subscription | Red Hat CSAF/VEX, OSV, OVAL, CVE data.                 |
| 2     | Red Hat Security Data API docs | docs.redhat.com/en/documentation/red\_hat\_security\_data\_api/1.0/html-single/red\_hat\_security\_data\_api/index | Free public docs/API; support content may require subscription                  | Retrieves Red Hat CVE/advisory/security data.          |
| 3     | Red Hat CVE database           | access.redhat.com/security/security-updates/#/cve                                                                  | Free public                                                                     | Red Hat CVE lookup.                                    |
| 4     | Red Hat OVAL data              | www.redhat.com/security/data/oval                                                                                  | Free public                                                                     | OVAL definitions for vulnerability assessment.         |
| 5     | Red Hat CSAF/VEX guidance      | redhatproductsecurity.github.io/security-data-guidelines/csaf-vex                                                  | Free public docs                                                                | Explains Red Hat CSAF/VEX & product/package semantics. |
| 6     | Red Hat security advisories    | access.redhat.com/security/security-updates/#/security-advisories                                                  | Free public listing                                                             | Red Hat advisory listing.                              |
| 7     | CentOS Stream security tracker | gitlab.com/redhat/centos-stream/rpms                                                                               | Free public GitLab                                                              | CentOS Stream package source context.                  |

#### 5.3 Debian

| Sl. # | Title                              | Link(s)                                                 | Access / Cost                      | Relevance Notes & POIs                         |
| ----- | ---------------------------------- | ------------------------------------------------------- | ---------------------------------- | ---------------------------------------------- |
| 1     | Debian Security Tracker            | security-tracker.debian.org                             | Free public                        | Debian-specific package vulnerability status.  |
| 2     | Debian Security Tracker JSON       | security-tracker.debian.org/tracker/data/json           | Free public JSON                   | Machine-readable Debian vulnerability data.    |
| 3     | Debian Security Tracker source Git | salsa.debian.org/security-tracker-team/security-tracker | Free / open-source public Git repo | Source repo for tracker data.                  |
| 4     | Debian Security Information        | www.debian.org/security                                 | Free public                        | Debian security notices & process context.     |
| 5     | Debian Security Tracker docs       | security-team.debian.org/security\_tracker.html         | Free public docs                   | Explains Debian tracker semantics.             |
| 6     | Debian OVAL                        | www.debian.org/security/oval                            | Free public                        | OVAL data for Debian vulnerability assessment. |

#### 5.4 Ubuntu / Canonical

| Sl. # | Title                          | Link(s)                                                 | Access / Cost           | Relevance Notes & POIs                                 |
| ----- | ------------------------------ | ------------------------------------------------------- | ----------------------- | ------------------------------------------------------ |
| 1     | Ubuntu Security Notices        | ubuntu.com/security/notices                             | Free public             | Ubuntu security notices for fixed packages.            |
| 2     | Ubuntu CVE reports             | ubuntu.com/security/cves                                | Free public             | Ubuntu CVE tracking by package/release.                |
| 3     | Ubuntu OVAL                    | ubuntu.com/security/oval                                | Free public             | OVAL data for vulnerability assessment & patch status. |
| 4     | Ubuntu VEX data                | ubuntu.com/security/vex                                 | Free public             | Ubuntu VEX data.                                       |
| 5     | Ubuntu VEX docs                | documentation.ubuntu.com/security/security-updates/vex/ | Free public docs        | Ubuntu VEX source documentation.                       |
| 6     | Ubuntu Security Notices GitHub | github.com/canonical/ubuntu-security-notices            | Free public GitHub repo | USN/LSN JSON, OSV JSON, & OpenVEX JSON formats.        |
| 7     | Ubuntu Security Tracker Git    | git.launchpad.net/ubuntu-cve-tracker                    | Free public Git repo    | Ubuntu CVE tracker source.                             |
| 8     | Ubuntu security updates docs   | documentation.ubuntu.com/security/security-updates/     | Free public docs        | Process context & VEX/OVAL interpretation.             |

#### 5.5 Alpine

| Sl. # | Title                                 | Link(s)                             | Access / Cost                       | Relevance Notes & POIs                       |
| ----- | ------------------------------------- | ----------------------------------- | ----------------------------------- | -------------------------------------------- |
| 1     | Alpine SecDB                          | secdb.alpinelinux.org               | Free public                         | Current Alpine machine-readable security DB. |
| 2     | Alpine Security Tracker               | security.alpinelinux.org            | Free public                         | Tracks Alpine security issues.               |
| 3     | Alpine SecDB deprecated GitHub mirror | github.com/alpinelinux/alpine-secdb | Free public GitHub repo; deprecated | Historical Alpine SecDB mirror.              |
| 4     | Alpine packages                       | pkgs.alpinelinux.org/packages       | Free public                         | Alpine package metadata.                     |

#### 5.6 SUSE / openSUSE

| Sl. # | Title                          | Link(s)                                                               | Access / Cost | Relevance Notes & POIs                               |
| ----- | ------------------------------ | --------------------------------------------------------------------- | ------------- | ---------------------------------------------------- |
| 1     | SUSE CSAF                      | www.suse.com/support/security/csaf/                                   | Free public   | SUSE CSAF advisory data.                             |
| 2     | SUSE CVRF / OVAL security data | www.suse.com/support/security/oval/                                   | Free public   | SUSE OVAL/CVRF security data.                        |
| 3     | SUSE CVE pages                 | www.suse.com/security/cve/                                            | Free public   | SUSE CVE lookup.                                     |
| 4     | SUSE Security Advisories       | www.suse.com/support/update/announcement/                             | Free public   | SUSE security advisory listing.                      |
| 5     | openSUSE Security Announce     | lists.opensuse.org/archives/list/security-announce@lists.opensuse.org | Free public   | openSUSE security announcement mailing list archive. |

#### 5.7 Oracle Linux

| Sl. # | Title                                           | Link(s)                         | Access / Cost | Relevance Notes & POIs                                              |
| ----- | ----------------------------------------------- | ------------------------------- | ------------- | ------------------------------------------------------------------- |
| 1     | Oracle Security Alerts & Critical Patch Updates | www.oracle.com/security-alerts/ | Free public   | Oracle CPU, Security Alerts, third-party bulletins, & CVE mappings. |
| 2     | Oracle Linux security data                      | linux.oracle.com/security/      | Free public   | Oracle Linux security data.                                         |
| 3     | Oracle Linux OVAL                               | linux.oracle.com/security/oval/ | Free public   | Oracle Linux OVAL definitions.                                      |
| 4     | Oracle Linux errata                             | linux.oracle.com/errata/        | Free public   | Oracle Linux errata.                                                |
| 5     | Oracle Linux CVE search                         | linux.oracle.com/cve/           | Free public   | Oracle Linux CVE lookup.                                            |

#### 5.8 Amazon Linux

| Sl. # | Title                        | Link(s)                                     | Access / Cost | Relevance Notes & POIs                           |
| ----- | ---------------------------- | ------------------------------------------- | ------------- | ------------------------------------------------ |
| 1     | Amazon Linux Security Center | alas.aws.amazon.com                         | Free public   | Amazon Linux security advisory portal.           |
| 2     | Amazon Linux 2 advisories    | alas.aws.amazon.com/alas2.html              | Free public   | Amazon Linux 2 advisories.                       |
| 3     | Amazon Linux 2023 advisories | alas.aws.amazon.com/AL2023/                 | Free public   | Amazon Linux 2023 advisories.                    |
| 4     | AWS Security Bulletins       | aws.amazon.com/security/security-bulletins/ | Free public   | AWS security bulletins for services & platforms. |

#### 5.9 Fedora, AlmaLinux, Rocky, Arch, Gentoo

| Sl. # | Title                           | Link(s)                                        | Access / Cost           | Relevance Notes & POIs                  |
| ----- | ------------------------------- | ---------------------------------------------- | ----------------------- | --------------------------------------- |
| 1     | Fedora security updates         | bodhi.fedoraproject.org/updates/?type=security | Free public             | Fedora security update advisories.      |
| 2     | Fedora packages                 | packages.fedoraproject.org                     | Free public             | Fedora package metadata.                |
| 3     | AlmaLinux Errata                | errata.almalinux.org                           | Free public             | AlmaLinux errata & security advisories. |
| 4     | AlmaLinux OSV data              | github.com/AlmaLinux/osv-database              | Free public GitHub repo | AlmaLinux OSV-formatted data.           |
| 5     | Rocky Linux security advisories | errata.build.resf.org                          | Free public             | Rocky Linux errata/security advisories. |
| 6     | Arch Linux Security Tracker     | security.archlinux.org                         | Free public             | Arch Linux security tracker.            |
| 7     | Arch Linux security JSON        | security.archlinux.org/json                    | Free public JSON        | Machine-readable Arch security data.    |
| 8     | Gentoo GLSA                     | security.gentoo.org/glsa/                      | Free public             | Gentoo Linux Security Advisories.       |
| 9     | Gentoo GLSA XML                 | security.gentoo.org/glsa/feed.rss              | Free public RSS/XML     | Gentoo GLSA RSS/XML feed.               |

#### 5.10 Wolfi / Chainguard

| Sl. # | Title                                | Link(s)                                                                                                  | Access / Cost                                                              | Relevance Notes & POIs                                     |
| ----- | ------------------------------------ | -------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------- | ---------------------------------------------------------- |
| 1     | Wolfi OS advisories                  | github.com/wolfi-dev/advisories                                                                          | Free public GitHub repo                                                    | Wolfi OS advisory data.                                    |
| 2     | Wolfi SecDB generator                | github.com/wolfi-dev/secdb                                                                               | Free / open-source public GitHub repo                                      | Generates Wolfi security DBs based on Alpine secdb format. |
| 3     | Wolfi OS feed                        | packages.wolfi.dev/os/security.json                                                                      | Free public feed                                                           | Wolfi package security feed.                               |
| 4     | Chainguard Enterprise feed           | packages.cgr.dev/chainguard/security.json                                                                | Publicly reachable feed; may relate to commercial Chainguard product scope | Separate from Wolfi OS feed.                               |
| 5     | Chainguard security advisories docs  | edu.chainguard.dev/chainguard/chainguard-images/staying-secure/security-advisories/how-chainguard-issues | Free public docs                                                           | Explains Chainguard advisory publication model.            |
| 6     | Wolfi vulnerabilities in OSV         | osv.dev/list?ecosystem=Wolfi                                                                             | Free public                                                                | Wolfi ecosystem records in OSV.                            |
| 7     | Chainguard OSV advisory feed context | www.chainguard.dev/unchained/chainguard-enhances-security-with-osv-advisory-feed                         | Free public blog                                                           | Context on Chainguard OSV advisory feed.                   |

### 6. Vendor advisories for enterprise impact assessment

#### 6.1 Major OS, browser & platform vendors

| Sl. # | Title                                  | Link(s)                                                         | Access / Cost                                                       | Relevance Notes & POIs                                                |
| ----- | -------------------------------------- | --------------------------------------------------------------- | ------------------------------------------------------------------- | --------------------------------------------------------------------- |
| 1     | Microsoft Security Update Guide        | msrc.microsoft.com/update-guide                                 | Free public                                                         | Microsoft vulnerability advisories, CVEs, affected products, & fixes. |
| 2     | Microsoft MSRC blog                    | msrc.microsoft.com/blog/                                        | Free public                                                         | Microsoft security research & advisory context.                       |
| 3     | Microsoft Security Response Center     | msrc.microsoft.com                                              | Free public                                                         | Entry point for MSRC resources.                                       |
| 4     | Apple Security Releases                | support.apple.com/en-us/100100                                  | Free public                                                         | Apple security release index.                                         |
| 5     | Apple security updates                 | support.apple.com/en-us/HT201222                                | Free public                                                         | Apple security update listing.                                        |
| 6     | Google Android Security Bulletins      | source.android.com/docs/security/bulletin                       | Free public                                                         | Android platform security bulletins.                                  |
| 7     | Google Chrome Releases                 | chromereleases.googleblog.com                                   | Free public                                                         | Chrome release announcements.                                         |
| 8     | Chrome security advisories             | chromereleases.googleblog.com/search/label/Security             | Free public                                                         | Chrome security-specific release posts.                               |
| 9     | Chromium issue tracker                 | issues.chromium.org                                             | Free public for public issues; restricted issues may require access | Chromium issue tracking.                                              |
| 10    | Mozilla Security Advisories            | www.mozilla.org/en-US/security/advisories/                      | Free public                                                         | Mozilla security advisories.                                          |
| 11    | Mozilla Foundation Security Advisories | www.mozilla.org/en-US/security/known-vulnerabilities/           | Free public                                                         | Mozilla known vulnerabilities index.                                  |
| 12    | Google Cloud Security Bulletins        | cloud.google.com/support/bulletins                              | Free public                                                         | Google Cloud service/product security bulletins.                      |
| 13    | Kubernetes Security Announcements      | groups.google.com/g/kubernetes-security-announce                | Free public                                                         | Google Group Kubernetes security announcement mailing list.           |
| 14    | Kubernetes official CVE feed           | kubernetes.io/docs/reference/issues-security/official-cve-feed/ | Free public                                                         | Official Kubernetes CVE feed reference.                               |
| 15    | Kubernetes security & disclosure       | kubernetes.io/docs/reference/issues-security/security/          | Free public                                                         | Kubernetes security disclosure process.                               |

#### 6.2 Enterprise infrastructure vendors

| Sl. # | Title                                  | Link(s)                                                                                           | Access / Cost                                                    | Relevance Notes & POIs                                                      |
| ----- | -------------------------------------- | ------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------- | --------------------------------------------------------------------------- |
| 1     | Cisco Security Advisories              | sec.cloudapps.cisco.com/security/center/publicationListing.x                                      | Free public                                                      | Cisco product advisories, affected versions, fixed versions, & workarounds. |
| 2     | VMware / Broadcom Security Advisories  | support.broadcom.com/web/ecx/security-advisory                                                    | Free public; some support downloads may require entitlement      | VMware/Broadcom security advisories.                                        |
| 3     | Palo Alto Networks Security Advisories | security.paloaltonetworks.com                                                                     | Free public                                                      | PAN-OS & Palo Alto product advisories.                                      |
| 4     | Fortinet PSIRT Advisories              | www.fortiguard.com/psirt                                                                          | Free public                                                      | Fortinet product advisories.                                                |
| 5     | Ivanti Security Advisories             | www.ivanti.com/resources/v/doc/ivi/2629/0e3e2be1e66d                                              | Free public                                                      | Ivanti security advisories.                                                 |
| 6     | Citrix Security Bulletins              | support.citrix.com/securitybulletins                                                              | Free public                                                      | Citrix product security bulletins.                                          |
| 7     | F5 Security Advisories                 | my.f5.com/manage/s/solutions?series=Security\_Advisory                                            | Free public; some support content may require account            | F5 product security advisories.                                             |
| 8     | Juniper Security Advisories            | supportportal.juniper.net/s/global-search/%40uri#sort=relevancy\&f:ctype=\[Security%20Advisories] | Free public; support portal may require account for some content | Juniper security advisory listing.                                          |
| 9     | Dell Security Advisories               | www.dell.com/support/security                                                                     | Free public; downloads/support may require entitlement           | Dell product security advisories.                                           |
| 10    | HPE Security Bulletins                 | support.hpe.com/hpesc/public/home                                                                 | Free public; support portal may require account/entitlement      | HPE security bulletins.                                                     |
| 11    | Lenovo Product Security Advisories     | support.lenovo.com/us/en/product\_security/home                                                   | Free public                                                      | Lenovo product security advisories.                                         |
| 12    | IBM PSIRT                              | www.ibm.com/support/pages/ibm-psirt                                                               | Free public; some support docs may require entitlement           | IBM product security incident response.                                     |
| 13    | SAP Security Notes                     | support.sap.com/en/my-support/knowledge-base/security-notes-news.html                             | SAP support account/subscription often required                  | SAP security notes & patch-day guidance.                                    |
| 14    | Adobe Security Bulletins               | helpx.adobe.com/security.html                                                                     | Free public                                                      | Adobe security bulletins.                                                   |
| 15    | Oracle Critical Patch Updates          | www.oracle.com/security-alerts/                                                                   | Free public                                                      | Oracle CPU, Security Alerts, & CVE mappings.                                |
| 16    | Atlassian Security Advisories          | www.atlassian.com/trust/security/advisories                                                       | Free public                                                      | Atlassian product advisories.                                               |
| 17    | Elastic Security Announcements         | discuss.elastic.co/c/announcements/security-announcements/31                                      | Free public forum                                                | Elastic security announcements.                                             |
| 18    | HashiCorp Security                     | www.hashicorp.com/security                                                                        | Free public; enterprise support separate                         | HashiCorp security advisories & disclosure policy.                          |
| 19    | GitLab Security Releases               | about.gitlab.com/releases/categories/releases/                                                    | Free public                                                      | GitLab release posts, including security releases.                          |
| 20    | Jenkins Security Advisories            | www.jenkins.io/security/advisories/                                                               | Free public                                                      | Jenkins core & plugin advisories.                                           |
| 21    | Apache Security Reports                | www.apache.org/security/                                                                          | Free public                                                      | Apache project security reports & process.                                  |
| 22    | Eclipse Security Advisories            | www.eclipse.org/security/                                                                         | Free public                                                      | Eclipse project security advisories.                                        |
| 23    | WordPress Security Releases            | wordpress.org/news/category/security/                                                             | Free public                                                      | WordPress security release announcements.                                   |
| 24    | Drupal Security Advisories             | www.drupal.org/security                                                                           | Free public                                                      | Drupal core & contributed project advisories.                               |
| 25    | OpenSSL Vulnerabilities                | www.openssl.org/news/vulnerabilities.html                                                         | Free public                                                      | OpenSSL vulnerability list.                                                 |
| 26    | OpenSSH release notes                  | www.openssh.com/releasenotes.html                                                                 | Free public                                                      | OpenSSH release notes.                                                      |
| 27    | curl security advisories               | curl.se/docs/security.html                                                                        | Free public                                                      | curl/libcurl security advisories.                                           |

#### 6.3 Cloud provider security bulletins

| Sl. # | Title                           | Link(s)                                          | Access / Cost | Relevance Notes & POIs                    |
| ----- | ------------------------------- | ------------------------------------------------ | ------------- | ----------------------------------------- |
| 1     | AWS Security Bulletins          | aws.amazon.com/security/security-bulletins/      | Free public   | AWS service/product security bulletins.   |
| 2     | AWS Security Blog               | aws.amazon.com/blogs/security/                   | Free public   | AWS security guidance & incident context. |
| 3     | Google Cloud Security Bulletins | cloud.google.com/support/bulletins               | Free public   | Google Cloud security bulletins.          |
| 4     | Google Cloud Security Blog      | cloud.google.com/blog/products/identity-security | Free public   | Google Cloud identity/security blog.      |
| 5     | Microsoft Azure security / MSRC | msrc.microsoft.com/update-guide                  | Free public   | Microsoft/Azure-related security updates. |
| 6     | Azure updates                   | azure.microsoft.com/en-us/updates/               | Free public   | Azure product update feed.                |
| 7     | Oracle Cloud security           | www.oracle.com/security-alerts/                  | Free public   | Oracle cloud/product security alerts.     |
| 8     | IBM Cloud security bulletins    | cloud.ibm.com/status/security                    | Free public   | IBM Cloud security bulletins.             |

### 7. SBOM, package identity, VEX & advisory exchange standards

#### 7.1 SBOM standards

| Sl. # | Title                            | Link(s)                                                               | Access / Cost                         | Relevance Notes & POIs                                                  |
| ----- | -------------------------------- | --------------------------------------------------------------------- | ------------------------------------- | ----------------------------------------------------------------------- |
| 1     | CycloneDX specification overview | cyclonedx.org/specification/overview/                                 | Free / open standard                  | SBOM, SaaSBOM, BOM, VEX, vulnerability & component metadata standard.   |
| 2     | CycloneDX GitHub                 | github.com/CycloneDX/specification                                    | Free / open-source public GitHub repo | CycloneDX specification source repository.                              |
| 3     | CycloneDX VEX                    | cyclonedx.org/capabilities/vex/                                       | Free public docs                      | CycloneDX VEX capability documentation.                                 |
| 4     | SPDX specifications              | spdx.dev/specifications/                                              | Free / open standard                  | SPDX specifications for software bills of materials & package metadata. |
| 5     | SPDX 3.0.1 spec                  | spdx.github.io/spdx-spec/v3.0.1/                                      | Free public docs                      | SPDX 3.0.1 specification.                                               |
| 6     | SPDX package URL property        | spdx.github.io/spdx-spec/v3.0.1/model/Software/Properties/packageUrl/ | Free public docs                      | SPDX support for package URL property.                                  |
| 7     | SPDX GitHub                      | github.com/spdx/spdx-spec                                             | Free / open-source public GitHub repo | SPDX specification repository.                                          |
| 8     | NTIA SBOM resources              | www.ntia.gov/page/software-bill-materials                             | Free public                           | SBOM policy & foundational resources.                                   |
| 9     | CISA SBOM                        | www.cisa.gov/sbom                                                     | Free public                           | CISA SBOM guidance & resources.                                         |

#### 7.2 Package & software identity

| Sl. # | Title                          | Link(s)                                                     | Access / Cost                                                                         | Relevance Notes & POIs                                          |
| ----- | ------------------------------ | ----------------------------------------------------------- | ------------------------------------------------------------------------------------- | --------------------------------------------------------------- |
| 1     | Package URL - PURL spec        | github.com/package-url/purl-spec                            | Free / open-source public GitHub repo                                                 | Standard package identifier used in SBOMs & vulnerability DBs.  |
| 2     | PURL types                     | github.com/package-url/purl-spec/blob/master/PURL-TYPES.rst | Free public                                                                           | Defines PURL types per ecosystem.                               |
| 3     | CPE specification / dictionary | nvd.nist.gov/products/cpe                                   | Free public                                                                           | Product naming & CPE dictionary.                                |
| 4     | NVD CPE API                    | nvd.nist.gov/developers/products                            | Free public; optional free API key for higher rate limits                             | Programmatic CPE dictionary access.                             |
| 5     | SWID tags - NIST               | csrc.nist.gov/projects/software-identification-swid         | Free public                                                                           | Software Identification Tags for installed software identity.   |
| 6     | GS1 Digital Link / identifiers | www.gs1.org/standards/gs1-digital-link                      | Free public standard docs; membership may apply for assigned traceability identifiers | Optional identity standard for physical/embedded supply chains. |
| 7     | Software Heritage IDs          | www.swhid.org                                               | Free public / open                                                                    | Persistent source-code artifact identity.                       |

#### 7.3 Advisory exchange, CSAF & VEX

| Sl. # | Title                                                  | Link(s)                                                                        | Access / Cost                         | Relevance Notes & POIs                                        |
| ----- | ------------------------------------------------------ | ------------------------------------------------------------------------------ | ------------------------------------- | ------------------------------------------------------------- |
| 1     | OASIS CSAF 2.0 specification                           | docs.oasis-open.org/csaf/csaf/v2.0/os/csaf-v2.0-os.html                        | Free / open standard                  | Common Security Advisory Framework for structured advisories. |
| 2     | CSAF home                                              | www.csaf.io                                                                    | Free public                           | CSAF ecosystem & tooling hub.                                 |
| 3     | OpenVEX specification                                  | github.com/openvex/spec                                                        | Free / open-source public GitHub repo | Minimal JSON-LD VEX format.                                   |
| 4     | OpenVEX project page                                   | openssf.org/projects/openvex/                                                  | Free public                           | OpenSSF project page for OpenVEX.                             |
| 5     | CISA Minimum Requirements for VEX                      | www.cisa.gov/sites/default/files/2023-04/minimum-requirements-for-vex-508c.pdf | Free public PDF                       | Baseline VEX requirements.                                    |
| 6     | OpenSSF VDR, VEX, OpenVEX & CSAF explainer             | openssf.org/blog/2023/09/07/vdr-vex-openvex-and-csaf/                          | Free public                           | Explains VDR, VEX, OpenVEX, & CSAF.                           |
| 7     | Red Hat CSAF/VEX guidance                              | redhatproductsecurity.github.io/security-data-guidelines/csaf-vex              | Free public docs                      | Red Hat CSAF/VEX semantics & usage guidance.                  |
| 8     | Ubuntu VEX                                             | ubuntu.com/security/vex                                                        | Free public                           | Ubuntu VEX data entry point.                                  |
| 9     | Canonical Ubuntu Security Notices repo - OSV & OpenVEX | github.com/canonical/ubuntu-security-notices                                   | Free public GitHub repo               | Canonical USN/LSN, OSV, & OpenVEX JSON data.                  |

### 8. Malicious package, supply-chain compromise & package reputation sources

#### 8.1 Malicious package databases

| Sl. # | Title                                   | Link(s)                                                                         | Access / Cost                                                | Relevance Notes & POIs                                          |
| ----- | --------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------ | --------------------------------------------------------------- |
| 1     | OpenSSF Malicious Packages repository   | github.com/ossf/malicious-packages                                              | Free / open-source public GitHub repo                        | Public malicious package reports consumable via OSV format.     |
| 2     | OpenSSF Malicious Packages announcement | openssf.org/blog/2023/10/12/introducing-openssfs-malicious-packages-repository/ | Free public                                                  | Explains the public DB for malicious package reports.           |
| 3     | OpenSSF Package Analysis                | openssf.org/package-analysis/                                                   | Free public project info                                     | Detects malicious package behavior & informs package consumers. |
| 4     | OpenSSF Package Analysis GitHub         | github.com/ossf/package-analysis                                                | Free / open-source public GitHub repo                        | Open-source package analysis system.                            |
| 5     | OpenSSF Package Feeds                   | github.com/ossf/package-feeds                                                   | Free / open-source public GitHub repo                        | Package ecosystem feed monitoring.                              |
| 6     | GitHub malware advisories               | github.com/advisories?query=type%3Amalware                                      | Free public                                                  | GitHub malware advisories across ecosystems.                    |
| 7     | npm malware advisories via GitHub       | github.com/advisories?query=ecosystem%3Anpm+type%3Amalware                      | Free public                                                  | npm-specific malware advisories.                                |
| 8     | PyPI malware advisories via GitHub      | github.com/advisories?query=ecosystem%3Apip+type%3Amalware                      | Free public                                                  | PyPI-specific malware advisories.                               |
| 9     | Socket.dev blog                         | socket.dev/blog                                                                 | Free public blog; product/API features may be commercial     | Supply-chain attack research & malicious package analysis.      |
| 10    | Snyk vulnerability database             | security.snyk.io                                                                | Free public search; commercial plans/API features            | Snyk vulnerability & package risk database.                     |
| 11    | Sonatype OSS Index                      | ossindex.sonatype.org                                                           | Free tier / API terms; commercial Sonatype products separate | OSS vulnerability intelligence.                                 |
| 12    | Sonatype vulnerability database         | sonatype.com/resources/vulnerability-database                                   | Free public search; commercial ecosystem                     | Sonatype vulnerability database.                                |
| 13    | Phylum research                         | blog.phylum.io                                                                  | Free public blog; commercial products separate               | Software supply-chain attack research.                          |
| 14    | ReversingLabs threat research           | www.reversinglabs.com/blog                                                      | Free public blog; commercial products separate               | Threat research focused on malware & supply-chain compromise.   |
| 15    | Checkmarx supply-chain research         | checkmarx.com/blog                                                              | Free public blog; commercial products separate               | Supply-chain & application security research.                   |

#### 8.2 Package reputation / dependency health

| Sl. # | Title                        | Link(s)                            | Access / Cost                              | Relevance Notes & POIs                                          |
| ----- | ---------------------------- | ---------------------------------- | ------------------------------------------ | --------------------------------------------------------------- |
| 1     | OpenSSF Scorecard            | github.com/ossf/scorecard          | Free / open-source public GitHub repo      | Scores open-source project security practices.                  |
| 2     | OpenSSF Scorecard API        | api.securityscorecards.dev         | Free public API subject to service limits  | API for Scorecard results.                                      |
| 3     | OpenSSF Best Practices Badge | www.bestpractices.dev              | Free public                                | Project best-practices badge program.                           |
| 4     | deps.dev                     | deps.dev                           | Free public                                | Dependency metadata, transitive dependencies, security signals. |
| 5     | OpenSSF GUAC                 | guac.sh                            | Free public / open-source project          | Graph for software supply-chain metadata.                       |
| 6     | GUAC GitHub                  | github.com/guacsec/guac            | Free / open-source public GitHub repo      | GUAC implementation repository.                                 |
| 7     | Sigstore                     | www.sigstore.dev                   | Free / open-source public infrastructure   | Signing & verification for software artifacts.                  |
| 8     | Rekor transparency log       | docs.sigstore.dev/logging/overview | Free public docs / public transparency log | Transparency log for signed artifacts.                          |
| 9     | SLSA framework               | slsa.dev                           | Free / open standard                       | Supply-chain Levels for Software Artifacts.                     |

### 9. Automated vulnerability detection, static analysis, dynamic analysis & research datasets

#### 9.1 SAST / code query engines

| Sl. # | Title                    | Link(s)                                            | Access / Cost                                                                                  | Relevance Notes & POIs                                     |
| ----- | ------------------------ | -------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------- |
| 1     | CodeQL                   | codeql.github.com                                  | Free for many open-source uses; GitHub Advanced Security commercial for private enterprise use | Semantic code analysis engine for vulnerability discovery. |
| 2     | CodeQL GitHub            | github.com/github/codeql                           | Free / open-source public GitHub repo                                                          | CodeQL source & query repository.                          |
| 3     | CodeQL query packs       | github.com/github/codeql/tree/main                 | Free / open-source public GitHub repo                                                          | Query packs for multiple languages.                        |
| 4     | Semgrep                  | semgrep.dev                                        | Free/open-source CLI; commercial products available                                            | Pattern-based static analysis.                             |
| 5     | Semgrep rules            | github.com/semgrep/semgrep-rules                   | Free / open-source public GitHub repo                                                          | Community/official Semgrep rules.                          |
| 6     | Joern                    | joern.io                                           | Free / open-source core                                                                        | Code property graph platform.                              |
| 7     | Joern GitHub             | github.com/joernio/joern                           | Free / open-source public GitHub repo                                                          | Joern implementation.                                      |
| 8     | Facebook Infer           | fbinfer.com                                        | Free public / open-source                                                                      | Static analyzer for multiple languages.                    |
| 9     | Infer GitHub             | github.com/facebook/infer                          | Free / open-source public GitHub repo                                                          | Infer source repository.                                   |
| 10    | SonarQube rules          | rules.sonarsource.com                              | Free public rules catalog; commercial products include free & commercial tiers                 | SonarSource rule catalog.                                  |
| 11    | Bandit - Python          | github.com/PyCQA/bandit                            | Free / open-source public GitHub repo                                                          | Python security linter.                                    |
| 12    | Gosec - Go               | github.com/securego/gosec                          | Free / open-source public GitHub repo                                                          | Go security checker.                                       |
| 13    | ESLint security plugin   | github.com/eslint-community/eslint-plugin-security | Free / open-source public GitHub repo                                                          | JavaScript security lint rules.                            |
| 14    | SpotBugs                 | spotbugs.github.io                                 | Free / open-source                                                                             | Java static analysis.                                      |
| 15    | FindSecBugs              | find-sec-bugs.github.io                            | Free / open-source                                                                             | Java security bug detection plugin.                        |
| 16    | Clang Static Analyzer    | clang-analyzer.llvm.org                            | Free / open-source                                                                             | C/C++/Objective-C static analyzer.                         |
| 17    | Cppcheck                 | cppcheck.sourceforge.io                            | Free / open-source                                                                             | C/C++ static analyzer.                                     |
| 18    | Flawfinder               | dwheeler.com/flawfinder                            | Free / open-source                                                                             | C/C++ security scanner for dangerous functions.            |
| 19    | Brakeman - Ruby on Rails | brakemanscanner.org                                | Free / open-source                                                                             | Ruby on Rails static security scanner.                     |
| 20    | Horusec                  | github.com/ZupIT/horusec                           | Free / open-source public GitHub repo                                                          | Multi-language security scanner.                           |
| 21    | Bearer                   | github.com/Bearer/bearer                           | Free / open-source public GitHub repo                                                          | Code security/privacy scanner.                             |
| 22    | MobSF                    | github.com/MobSF/Mobile-Security-Framework-MobSF   | Free / open-source public GitHub repo                                                          | Mobile security testing framework.                         |

#### 9.2 DAST, IAST, fuzzing & dynamic test sources

| Sl. # | Title                              | Link(s)                                      | Access / Cost                                                        | Relevance Notes & POIs                           |
| ----- | ---------------------------------- | -------------------------------------------- | -------------------------------------------------------------------- | ------------------------------------------------ |
| 1     | OSS-Fuzz                           | google.github.io/oss-fuzz                    | Free for eligible open-source projects                               | Continuous fuzzing for open-source projects.     |
| 2     | OSS-Fuzz GitHub                    | github.com/google/oss-fuzz                   | Free / open-source public GitHub repo                                | OSS-Fuzz project configuration repository.       |
| 3     | OSS-Fuzz vulnerability data in OSV | osv.dev/list?ecosystem=OSS-Fuzz              | Free public                                                          | OSV records from OSS-Fuzz vulnerabilities.       |
| 4     | ClusterFuzzLite                    | google.github.io/clusterfuzzlite             | Free / open-source                                                   | Lightweight continuous fuzzing for CI/CD.        |
| 5     | AFL++                              | github.com/AFLplusplus/AFLplusplus           | Free / open-source public GitHub repo                                | Coverage-guided fuzzer.                          |
| 6     | libFuzzer                          | llvm.org/docs/LibFuzzer.html                 | Free / open-source LLVM component                                    | In-process coverage-guided fuzzer.               |
| 7     | Honggfuzz                          | github.com/google/honggfuzz                  | Free / open-source public GitHub repo                                | Security-oriented fuzzer.                        |
| 8     | Jazzer                             | github.com/CodeIntelligenceTesting/jazzer    | Free / open-source public GitHub repo                                | JVM fuzzing engine.                              |
| 9     | OWASP ZAP                          | www.zaproxy.org                              | Free / open-source                                                   | Web application dynamic security scanner.        |
| 10    | Nuclei                             | github.com/projectdiscovery/nuclei           | Free / open-source public GitHub repo; commercial ecosystem separate | Template-based vulnerability & exposure scanner. |
| 11    | Nuclei templates                   | github.com/projectdiscovery/nuclei-templates | Free / open-source public GitHub repo                                | Community/official detection templates.          |

#### 9.3 Vulnerability-detection research datasets

| Sl. # | Title                         | Link(s)                                                      | Access / Cost                                            | Relevance Notes & POIs                                               |
| ----- | ----------------------------- | ------------------------------------------------------------ | -------------------------------------------------------- | -------------------------------------------------------------------- |
| 1     | NIST SARD                     | samate.nist.gov/SARD/                                        | Free public                                              | Software Assurance Reference Dataset.                                |
| 2     | Juliet Test Suite - NIST SARD | samate.nist.gov/SARD/test-suites/112                         | Free public                                              | Synthetic test cases for many vulnerability classes.                 |
| 3     | Big-Vul                       | github.com/ZeoVan/MSR\_20\_Code\_vulnerability\_CSV\_Dataset | Free public GitHub repo; verify license                  | Large vulnerability dataset derived from real-world CVE-fix commits. |
| 4     | Devign                        | sites.google.com/view/devign                                 | Free public research page; verify dataset access/license | Vulnerability detection dataset.                                     |
| 5     | Draper VDISC                  | osf.io/d45bw                                                 | Free public OSF dataset; verify license/terms            | Vulnerability discovery dataset.                                     |
| 6     | DiverseVul                    | github.com/wagner-group/diversevul                           | Free public GitHub repo; verify license                  | Diverse vulnerability dataset.                                       |
| 7     | PrimeVul                      | github.com/DLVulDet/PrimeVul                                 | Free public GitHub repo; verify license                  | Vulnerability detection benchmark dataset.                           |
| 8     | MegaVul                       | github.com/Icyrockton/MegaVul                                | Free public GitHub repo; verify license                  | Large-scale vulnerability dataset.                                   |
| 9     | Vul4J                         | github.com/tuhh-softsec/vul4j                                | Free / open-source public GitHub repo                    | Java vulnerability benchmark.                                        |
| 10    | VulnCode-DB                   | github.com/vegardit/vulncode-db                              | Free public GitHub repo; verify license                  | Vulnerable code examples.                                            |
| 11    | SecurityEval                  | github.com/s2e-lab/SecurityEval                              | Free public GitHub repo; verify license                  | Security-focused benchmark.                                          |
| 12    | CVEfixes                      | github.com/secureIT-project/CVEfixes                         | Free public GitHub repo; verify license                  | Links CVEs to fixing commits.                                        |
| 13    | Defects4J                     | github.com/rjust/defects4j                                   | Free / open-source public GitHub repo                    | Java bug dataset.                                                    |
| 14    | ManySStuBs4J                  | github.com/mast-group/mineSStuBs                             | Free public GitHub repo; verify license                  | Java simple bug dataset.                                             |
| 15    | VulDeePecker                  | github.com/CGCL-codes/VulDeePecker                           | Free public GitHub repo; verify license                  | Deep-learning vulnerability detection dataset/tooling.               |

### 10. ICS, OT, IoT, embedded & medical-device sources

#### 10.1 CISA ICS / medical

| Sl. # | Title                          | Link(s)                                                          | Access / Cost | Relevance Notes & POIs                  |
| ----- | ------------------------------ | ---------------------------------------------------------------- | ------------- | --------------------------------------- |
| 1     | CISA ICS Advisories            | www.cisa.gov/news-events/ics-advisories                          | Free public   | Industrial Control System advisories.   |
| 2     | CISA ICS Medical Advisories    | www.cisa.gov/news-events/ics-medical-advisories                  | Free public   | Medical device security advisories.     |
| 3     | CISA cybersecurity advisories  | www.cisa.gov/cybersecurity-advisories                            | Free public   | CISA cybersecurity advisory hub.        |
| 4     | ICS-CERT advisories archive    | www.cisa.gov/news-events/ics-advisories                          | Free public   | ICS-CERT advisory archive path.         |
| 5     | CISA ICS recommended practices | www.cisa.gov/resources-tools/resources/ics-recommended-practices | Free public   | Recommended practices for ICS security. |

#### 10.2 OT / ICS vendor advisories

| Sl. # | Title                                        | Link(s)                                                                                | Access / Cost                                                  | Relevance Notes & POIs                        |
| ----- | -------------------------------------------- | -------------------------------------------------------------------------------------- | -------------------------------------------------------------- | --------------------------------------------- |
| 1     | Siemens ProductCERT                          | cert-portal.siemens.com/productcert/                                                   | Free public; some support downloads may require entitlement    | Siemens product security advisories.          |
| 2     | Schneider Electric Security Notifications    | www.se.com/ww/en/work/support/cybersecurity/security-notifications.jsp                 | Free public                                                    | Schneider Electric security notifications.    |
| 3     | Rockwell Automation Security Advisories      | www.rockwellautomation.com/en-us/support/product/product-security-advisories.html      | Free public listing; support downloads may require entitlement | Rockwell Automation product advisories.       |
| 4     | Honeywell Product Security                   | www.honeywell.com/us/en/product-security                                               | Free public                                                    | Honeywell product security advisories.        |
| 5     | Philips Product Security                     | www.philips.com/a-w/security/security-advisories.html                                  | Free public                                                    | Philips medical/product security advisories.  |
| 6     | GE Vernova Product Security                  | www.gevernova.com/product-security                                                     | Free public                                                    | GE Vernova product security.                  |
| 7     | ABB Cyber Security Alerts                    | global.abb/group/en/technology/cyber-security/alerts-and-notifications                 | Free public                                                    | ABB cyber security alerts & notifications.    |
| 8     | Yokogawa Security Advisories                 | www.yokogawa.com/library/resources/white-papers/yokogawa-security-advisory-report-list | Free public                                                    | Yokogawa advisory report list.                |
| 9     | Mitsubishi Electric PSIRT                    | www.mitsubishielectric.com/en/psirt/vulnerability                                      | Free public                                                    | Mitsubishi Electric vulnerability advisories. |
| 10    | Johnson Controls Product Security Advisories | www.johnsoncontrols.com/cyber-solutions/security-advisories                            | Free public                                                    | Johnson Controls security advisories.         |

#### 10.3 IoT / embedded

| Sl. # | Title                                        | Link(s)                        | Access / Cost                                       | Relevance Notes & POIs                                                  |
| ----- | -------------------------------------------- | ------------------------------ | --------------------------------------------------- | ----------------------------------------------------------------------- |
| 1     | CERT/CC Vulnerability Notes                  | www.kb.cert.org/vuls           | Free public                                         | Coordinated disclosure notes, often with embedded/IoT affected vendors. |
| 2     | IoT Security Foundation                      | www.iotsecurityfoundation.org  | Free public resources; membership options may exist | IoT security guidance & resources.                                      |
| 3     | FACT - Firmware Analysis and Comparison Tool | github.com/fkie-cad/FACT\_core | Free / open-source public GitHub repo               | Firmware analysis platform.                                             |
| 4     | EMBA firmware analyzer                       | github.com/e-m-b-a/emba        | Free / open-source public GitHub repo               | Firmware analyzer for embedded Linux/IoT.                               |
| 5     | Binwalk                                      | github.com/ReFirmLabs/binwalk  | Free / open-source public GitHub repo               | Firmware extraction & analysis tool.                                    |

### 11. Exposure, internet-facing asset & threat telemetry

#### 11.1 Internet exposure search engines

| Sl. # | Title                | Link(s)              | Access / Cost                                     | Relevance Notes & POIs                   |
| ----- | -------------------- | -------------------- | ------------------------------------------------- | ---------------------------------------- |
| 1     | Censys Search        | search.censys.io     | Free tier / paid plans                            | Internet exposure search engine.         |
| 2     | Censys API           | search.censys.io/api | Free tier / paid plans; API key required          | Programmatic Censys access.              |
| 3     | Shodan               | www.shodan.io        | Free limited access / paid plans                  | Internet-connected device search.        |
| 4     | Shodan developer API | developer.shodan.io  | Paid/API credit model may apply; account required | Shodan API documentation.                |
| 5     | ZoomEye              | www.zoomeye.org      | Free limited access / paid plans                  | Internet asset search engine.            |
| 6     | FOFA                 | fofa.info            | Free limited access / paid plans                  | Internet asset search.                   |
| 7     | BinaryEdge           | www.binaryedge.io    | Commercial / limited trial may exist              | Internet scanning & threat intelligence. |
| 8     | Onyphe               | www.onyphe.io        | Free tier / paid plans                            | Cyber defense search engine.             |
| 9     | SecurityTrails       | securitytrails.com   | Free limited access / paid plans                  | DNS & asset intelligence.                |
| 10    | InternetDB by Shodan | internetdb.shodan.io | Free public API                                   | Lightweight Shodan InternetDB API.       |

#### 11.2 Scan/exploitation telemetry

| Sl. # | Title                          | Link(s)                                | Access / Cost                                                       | Relevance Notes & POIs                       |
| ----- | ------------------------------ | -------------------------------------- | ------------------------------------------------------------------- | -------------------------------------------- |
| 1     | GreyNoise Visualizer           | viz.greynoise.io                       | Free tier / paid plans                                              | Internet scanning/exploitation telemetry.    |
| 2     | GreyNoise API docs             | docs.greynoise.io                      | Free tier / paid plans; API key required                            | API docs for GreyNoise enrichment.           |
| 3     | Shadowserver                   | www.shadowserver.org                   | Free for eligible organizations; registration may be required       | Internet-scale exposure & threat telemetry.  |
| 4     | Shadowserver reports dashboard | dashboard.shadowserver.org             | Free for eligible organizations; login/registration may be required | Shadowserver reporting dashboard.            |
| 5     | SANS Internet Storm Center     | isc.sans.edu                           | Free public                                                         | Internet threat telemetry & diary reports.   |
| 6     | Honeynet Project               | www.honeynet.org                       | Free public / open research                                         | Honeypot & threat research.                  |
| 7     | DShield                        | www.dshield.org                        | Free public / community                                             | Distributed intrusion detection & telemetry. |
| 8     | LeakIX                         | leakix.net                             | Free limited access / paid plans                                    | Exposed service & leak search.               |
| 9     | urlscan.io                     | urlscan.io                             | Free tier / paid plans                                              | URL scanning & web telemetry.                |
| 10    | VirusTotal                     | www.virustotal.com                     | Free community access / paid enterprise plans                       | File, URL, domain, & IP reputation.          |
| 11    | VirusTotal API                 | docs.virustotal.com/reference/overview | Free community API / paid enterprise API                            | VirusTotal API documentation.                |

#### 11.3 Attack surface management context

| Sl. # | Title                      | Link(s)                               | Access / Cost                         | Relevance Notes & POIs                    |
| ----- | -------------------------- | ------------------------------------- | ------------------------------------- | ----------------------------------------- |
| 1     | Amass                      | github.com/owasp-amass/amass          | Free / open-source public GitHub repo | Attack surface mapping & DNS enumeration. |
| 2     | ProjectDiscovery Subfinder | github.com/projectdiscovery/subfinder | Free / open-source public GitHub repo | Subdomain discovery.                      |
| 3     | httpx                      | github.com/projectdiscovery/httpx     | Free / open-source public GitHub repo | HTTP probing toolkit.                     |
| 4     | Naabu                      | github.com/projectdiscovery/naabu     | Free / open-source public GitHub repo | Port scanner.                             |
| 5     | Nmap                       | nmap.org                              | Free / open-source                    | Network discovery & security auditing.    |
| 6     | Masscan                    | github.com/robertdavidgraham/masscan  | Free / open-source public GitHub repo | High-speed port scanner.                  |

### 12. Threat intelligence, malware, ransomware & in-the-wild exploitation context

#### 12.1 Major threat research sources

| Sl. # | Title                                       | Link(s)                                                         | Access / Cost                                               | Relevance Notes & POIs                                  |
| ----- | ------------------------------------------- | --------------------------------------------------------------- | ----------------------------------------------------------- | ------------------------------------------------------- |
| 1     | Mandiant / Google Cloud Threat Intelligence | cloud.google.com/blog/topics/threat-intelligence                | Free public blog; commercial threat intel products separate | Threat intelligence & exploitation-in-the-wild context. |
| 2     | Microsoft Threat Intelligence blog          | www.microsoft.com/en-us/security/blog/topic/threat-intelligence | Free public blog                                            | Microsoft threat intel & exploitation reports.          |
| 3     | Google Threat Analysis Group                | blog.google/threat-analysis-group                               | Free public blog                                            | Nation-state & high-end threat research.                |
| 4     | Palo Alto Unit 42                           | unit42.paloaltonetworks.com                                     | Free public blog; commercial threat intel services separate | Threat research & vulnerability exploitation reporting. |
| 5     | Cisco Talos                                 | blog.talosintelligence.com                                      | Free public blog; commercial Cisco products separate        | Threat intel, malware, & vulnerability research.        |
| 6     | Rapid7 vulnerability management blog        | www.rapid7.com/blog/tag/vulnerability-management/               | Free public blog; commercial products separate              | Vulnerability management & exploitability commentary.   |
| 7     | Sophos X-Ops                                | news.sophos.com/en-us/category/threat-research/                 | Free public blog; commercial products separate              | Threat research & incident reports.                     |
| 8     | CrowdStrike Blog                            | www.crowdstrike.com/en-us/blog/                                 | Free public blog; commercial products separate              | Threat intelligence & incident research.                |
| 9     | SentinelOne Labs                            | www.sentinelone.com/labs/                                       | Free public blog; commercial products separate              | Malware & threat research.                              |
| 10    | Kaspersky Securelist                        | securelist.com                                                  | Free public blog; commercial products separate              | Threat research & malware analysis.                     |
| 11    | ESET WeLiveSecurity                         | www.welivesecurity.com                                          | Free public blog; commercial products separate              | Threat research & malware analysis.                     |
| 12    | Trend Micro Research                        | www.trendmicro.com/en\_us/research.html                         | Free public research; commercial products separate          | Threat & vulnerability research.                        |
| 13    | FortiGuard Labs                             | www.fortiguard.com/research                                     | Free public research; commercial products separate          | Fortinet threat research.                               |
| 14    | Check Point Research                        | research.checkpoint.com                                         | Free public blog; commercial products separate              | Threat research & vulnerability analysis.               |
| 15    | Elastic Security Labs                       | www.elastic.co/security-labs                                    | Free public research; commercial products separate          | Detection engineering & threat research.                |
| 16    | Sekoia Threat Intelligence                  | blog.sekoia.io                                                  | Free public blog; commercial threat intel products separate | Threat intelligence research.                           |

#### 12.2 Malware & IOC repositories

| Sl. # | Title           | Link(s)                     | Access / Cost                                                           | Relevance Notes & POIs                            |
| ----- | --------------- | --------------------------- | ----------------------------------------------------------------------- | ------------------------------------------------- |
| 1     | MISP            | www.misp-project.org        | Free / open-source; data sharing depends on communities/instances       | Threat intelligence sharing platform.             |
| 2     | AlienVault OTX  | otx.alienvault.com          | Free community access; commercial AT\&T Cybersecurity products separate | Open threat exchange for IOCs.                    |
| 3     | AbuseIPDB       | www.abuseipdb.com           | Free tier / paid plans                                                  | IP abuse reputation database.                     |
| 4     | URLhaus         | urlhaus.abuse.ch            | Free public                                                             | Malware URL tracking.                             |
| 5     | MalwareBazaar   | bazaar.abuse.ch             | Free public                                                             | Malware sample sharing.                           |
| 6     | ThreatFox       | threatfox.abuse.ch          | Free public                                                             | Threat intelligence indicators.                   |
| 7     | Feodo Tracker   | feodotracker.abuse.ch       | Free public                                                             | Botnet C2 tracking.                               |
| 8     | PhishTank       | phishtank.org               | Free community access; API/account may be required                      | Phishing URL database.                            |
| 9     | OpenPhish       | openphish.com               | Free limited feed / paid premium feeds                                  | Phishing intelligence.                            |
| 10    | YARA            | github.com/VirusTotal/yara  | Free / open-source public GitHub repo                                   | Malware classification & pattern matching engine. |
| 11    | YARA-Rules      | github.com/Yara-Rules/rules | Free / open-source public GitHub repo                                   | Community YARA rules.                             |
| 12    | SigmaHQ         | github.com/SigmaHQ/sigma    | Free / open-source public GitHub repo                                   | Generic SIEM detection rule format.               |
| 13    | LOLBAS          | lolbas-project.github.io    | Free public / open-source project                                       | Living-off-the-land binaries/scripts catalog.     |
| 14    | GTFOBins        | gtfobins.github.io          | Free public / open-source project                                       | Unix binary abuse catalog.                        |
| 15    | Ransomware.live | www.ransomware.live         | Free public                                                             | Ransomware group/leak-site tracking.              |

### 13. Compliance, baseline configuration & exposure severity standards

These are not vulnerability feeds, but they help assess impact, control failure, configuration exposure, & exploitability in a given environment.

#### 13.1 Security configuration & benchmarks

| Sl. # | Title                           | Link(s)                             | Access / Cost                                                                   | Relevance Notes & POIs                           |
| ----- | ------------------------------- | ----------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------ |
| 1     | CIS Benchmarks                  | www.cisecurity.org/cis-benchmarks   | Free with registration for many PDFs; commercial CIS tools/membership available | Secure configuration benchmarks.                 |
| 2     | CIS Controls                    | www.cisecurity.org/controls         | Free public                                                                     | Security control framework.                      |
| 3     | NIST National Checklist Program | ncp.nist.gov                        | Free public                                                                     | Repository of security configuration checklists. |
| 4     | DISA STIGs                      | public.cyber.mil/stigs              | Free public                                                                     | Security Technical Implementation Guides.        |
| 5     | OpenSCAP                        | www.open-scap.org                   | Free / open-source                                                              | SCAP tooling for compliance scanning.            |
| 6     | SCAP Security Guide             | github.com/ComplianceAsCode/content | Free / open-source public GitHub repo                                           | ComplianceAsCode content for SCAP profiles.      |

#### 13.2 Cloud configuration posture

| Sl. # | Title                                    | Link(s)                                 | Access / Cost                                                                        | Relevance Notes & POIs                        |
| ----- | ---------------------------------------- | --------------------------------------- | ------------------------------------------------------------------------------------ | --------------------------------------------- |
| 1     | Prowler - AWS / Azure / GCP / Kubernetes | github.com/prowler-cloud/prowler        | Free / open-source core; commercial product available                                | Cloud & Kubernetes security posture scanning. |
| 2     | CloudSplaining                           | github.com/salesforce/cloudsplaining    | Free / open-source public GitHub repo                                                | AWS IAM policy risk analysis.                 |
| 3     | ScoutSuite                               | github.com/nccgroup/ScoutSuite          | Free / open-source public GitHub repo                                                | Multi-cloud security auditing.                |
| 4     | Steampipe mods                           | hub.steampipe.io/mods                   | Free/open-source mods; commercial Turbot/Steampipe offerings separate                | SQL-based cloud/security posture checks.      |
| 5     | Cloud Custodian                          | cloudcustodian.io                       | Free / open-source                                                                   | Cloud governance & policy automation.         |
| 6     | Kubernetes CIS benchmark                 | www.cisecurity.org/benchmark/kubernetes | Free with registration for benchmark PDFs; commercial CIS tools/membership available | Kubernetes configuration benchmark.           |
| 7     | kube-bench                               | github.com/aquasecurity/kube-bench      | Free / open-source public GitHub repo                                                | Kubernetes CIS benchmark scanner.             |
| 8     | kube-hunter                              | github.com/aquasecurity/kube-hunter     | Free / open-source public GitHub repo                                                | Kubernetes penetration testing tool.          |

### 14. Source-code, dependency, artifact & build-chain provenance

#### 14.1 Source & artifact provenance

| Sl. # | Title                      | Link(s)                                         | Access / Cost                              | Relevance Notes & POIs                         |
| ----- | -------------------------- | ----------------------------------------------- | ------------------------------------------ | ---------------------------------------------- |
| 1     | SLSA                       | slsa.dev                                        | Free / open standard                       | Supply-chain Levels for Software Artifacts.    |
| 2     | Sigstore                   | www.sigstore.dev                                | Free / open-source public infrastructure   | Signing & verification for software artifacts. |
| 3     | Cosign                     | github.com/sigstore/cosign                      | Free / open-source public GitHub repo      | Container/artifact signing tool.               |
| 4     | Rekor                      | docs.sigstore.dev/logging/overview              | Free public docs / public transparency log | Transparency log for signed artifacts.         |
| 5     | in-toto                    | in-toto.io                                      | Free / open-source                         | Supply-chain integrity framework.              |
| 6     | The Update Framework - TUF | theupdateframework.io                           | Free / open-source                         | Secure software update framework.              |
| 7     | SLSA GitHub generators     | github.com/slsa-framework/slsa-github-generator | Free / open-source public GitHub repo      | GitHub-based SLSA provenance generators.       |

#### 14.2 Dependency inventory & graphing

| Sl. # | Title                 | Link(s)                    | Access / Cost                             | Relevance Notes & POIs                                                   |
| ----- | --------------------- | -------------------------- | ----------------------------------------- | ------------------------------------------------------------------------ |
| 1     | deps.dev              | deps.dev                   | Free public                               | Dependency metadata, transitive dependency graphing, & security signals. |
| 2     | GUAC                  | guac.sh                    | Free public / open-source project         | Graph for software supply-chain metadata.                                |
| 3     | GUAC GitHub           | github.com/guacsec/guac    | Free / open-source public GitHub repo     | GUAC implementation repository.                                          |
| 4     | OpenSSF Scorecard     | github.com/ossf/scorecard  | Free / open-source public GitHub repo     | Open-source project security practice scoring.                           |
| 5     | OpenSSF Scorecard API | api.securityscorecards.dev | Free public API subject to service limits | API for Scorecard results.                                               |
| 6     | Maven Central         | central.sonatype.com       | Free public                               | Maven package metadata.                                                  |
| 7     | npm registry          | registry.npmjs.org         | Free public                               | npm package registry API endpoint.                                       |
| 8     | PyPI JSON API         | docs.pypi.org/api/json/    | Free public API docs / public API         | PyPI JSON API documentation.                                             |
| 9     | crates.io API         | crates.io/data-access      | Free public                               | crates.io data access documentation.                                     |
| 10    | Go module proxy       | proxy.golang.org           | Free public                               | Go module proxy.                                                         |

### 15. Practical priority hierarchy for ingestion

#### 15.1 Tier 0 - identifiers & inventory

| Sl. # | Title               | Link(s)                                                                                                          | Access / Cost                       | Relevance Notes & POIs                                                    |
| ----- | ------------------- | ---------------------------------------------------------------------------------------------------------------- | ----------------------------------- | ------------------------------------------------------------------------- |
| 1     | SBOM                | cyclonedx.org/specification/overview/, spdx.dev/specifications/                                                  | Free / open standards               | Inventory foundation for matching components to vulnerabilities.          |
| 2     | Package identity    | csrc.nist.gov/projects/software-identification-swid, github.com/package-url/purl-spec, nvd.nist.gov/products/cpe | Free public / open standards        | Component identity across package, product, & installed software domains. |
| 3     | Asset exposure      | search.censys.io, www.shodan.io                                                                                  | Free tiers / paid plans             | Determines whether vulnerable assets are externally reachable.            |
| 4     | Artifact provenance | in-toto.io, slsa.dev, www.sigstore.dev                                                                           | Free / open-source / open standards | Validates build-chain integrity & artifact authenticity.                  |

#### 15.2 Tier 1 - canonical vulnerability records

| Sl. # | Title             | Link(s)                                 | Access / Cost                                             | Relevance Notes & POIs              |
| ----- | ----------------- | --------------------------------------- | --------------------------------------------------------- | ----------------------------------- |
| 1     | CVE List v5       | github.com/CVEProject/cvelistV5         | Free public GitHub repo                                   | Canonical CVE record mirror.        |
| 2     | CVE schema        | github.com/CVEProject/cve-schema        | Free public GitHub repo                                   | Schema validation for CVE records.  |
| 3     | CVE Services API  | cveawg.mitre.org/api-docs               | Free public docs; CNA functions may require role/account  | Direct programmatic CVE lookup.     |
| 4     | NVD CVE API       | nvd.nist.gov/developers/vulnerabilities | Free public; optional free API key for higher rate limits | CVSS/CPE/CWE/reference enrichment.  |
| 5     | NVD CPE API       | nvd.nist.gov/developers/products        | Free public; optional free API key for higher rate limits | Product/platform identity matching. |
| 6     | NVD data feeds    | nvd.nist.gov/vuln/data-feeds            | Free public                                               | Bulk NVD feed access.               |
| 7     | CISA Vulnrichment | github.com/cisagov/vulnrichment         | Free public GitHub repo                                   | CISA ADP enrichment & SSVC data.    |

#### 15.3 Tier 2 - package/ecosystem vulnerability records

| Sl. # | Title                         | Link(s)                                               | Access / Cost                                                | Relevance Notes & POIs                                    |
| ----- | ----------------------------- | ----------------------------------------------------- | ------------------------------------------------------------ | --------------------------------------------------------- |
| 1     | OSV full database             | google.github.io/osv.dev/data/#full-database-download | Free public                                                  | Local mirror of OSS vulnerability records.                |
| 2     | OSV API                       | google.github.io/osv.dev/post-v1-query/               | Free public API                                              | Online vulnerability lookup by package/version/commit/ID. |
| 3     | GitHub Advisory Database      | github.com/advisories                                 | Free public                                                  | GHSA/CVE/malware advisory records.                        |
| 4     | GitHub Advisory Database repo | github.com/github/advisory-database                   | Free / open-source public GitHub repo                        | Raw advisory data for local ingestion.                    |
| 5     | Go vuln DB                    | vuln.go.dev                                           | Free public                                                  | Go-specific affectedness.                                 |
| 6     | RustSec                       | rustsec.org                                           | Free public / open-source ecosystem                          | Rust crate-specific advisories.                           |
| 7     | PyPA advisory DB              | github.com/pypa/advisory-database                     | Free public GitHub repo                                      | Python advisory source.                                   |
| 8     | FriendsOfPHP                  | github.com/FriendsOfPHP/security-advisories           | Free public GitHub repo                                      | Composer-specific advisories.                             |
| 9     | RubySec                       | github.com/rubysec/ruby-advisory-db                   | Free public GitHub repo                                      | Ruby ecosystem advisories.                                |
| 10    | OSS Index                     | ossindex.sonatype.org                                 | Free tier / API terms; commercial Sonatype products separate | Package vulnerability intelligence.                       |
| 11    | Packagist API                 | packagist.org/apidoc#list-security-advisories         | Free public API docs / public API                            | Direct PHP ecosystem source.                              |

#### 15.4 Tier 3 - affectedness, distro & vendor truth

| Sl. # | Title                                      | Link(s)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                | Access / Cost                                                                  | Relevance Notes & POIs                                                                 |
| ----- | ------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------- |
| 1     | Red Hat Security Data                      | access.redhat.com/security/data                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        | Free public data; support content may require subscription                     | RHEL affectedness, CSAF/VEX, OSV, OVAL.                                                |
| 2     | Debian Security Tracker                    | security-tracker.debian.org                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            | Free public                                                                    | Debian package affectedness.                                                           |
| 3     | Ubuntu OVAL / OSV / OpenVEX                | github.com/canonical/ubuntu-security-notices, ubuntu.com/security/oval, ubuntu.com/security/vex                                                                                                                                                                                                                                                                                                                                                                                                                        | Free public                                                                    | Ubuntu package affectedness & VEX status.                                              |
| 4     | Alpine SecDB                               | secdb.alpinelinux.org                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  | Free public                                                                    | Alpine package vulnerability data.                                                     |
| 5     | SUSE CSAF / OVAL                           | www.suse.com/support/security/csaf/, www.suse.com/support/security/oval                                                                                                                                                                                                                                                                                                                                                                                                                                                | Free public                                                                    | SUSE vendor affectedness & scanner data.                                               |
| 6     | Oracle Linux OVAL / errata                 | linux.oracle.com/errata/, linux.oracle.com/security/oval                                                                                                                                                                                                                                                                                                                                                                                                                                                               | Free public                                                                    | Oracle Linux-specific patch & OVAL data.                                               |
| 7     | Amazon Linux ALAS                          | alas.aws.amazon.com                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    | Free public                                                                    | Amazon Linux advisories.                                                               |
| 8     | AlmaLinux / Rocky / Fedora / Arch / Gentoo | bodhi.fedoraproject.org/updates/?type=security, errata.almalinux.org, errata.build.resf.org, security.archlinux.org, security.gentoo.org/glsa/                                                                                                                                                                                                                                                                                                                                                                         | Free public                                                                    | Additional Linux distribution affectedness sources.                                    |
| 9     | Wolfi / Chainguard                         | github.com/wolfi-dev/advisories, packages.cgr.dev/chainguard/security.json, packages.wolfi.dev/os/security.json                                                                                                                                                                                                                                                                                                                                                                                                        | Wolfi free public; Chainguard feed may relate to commercial product scope      | Container-first package vulnerability feeds.                                           |
| 10    | Vendor advisories                          | helpx.adobe.com/security.html, msrc.microsoft.com/update-guide, security.paloaltonetworks.com, sec.cloudapps.cisco.com/security/center/publicationListing.x, support.apple.com/en-us/100100, support.broadcom.com/web/ecx/security-advisory, support.citrix.com/securitybulletins, support.sap.com/en/my-support/knowledge-base/security-notes-news.html, www.atlassian.com/trust/security/advisories, www.fortiguard.com/psirt, www.ivanti.com/resources/v/doc/ivi/2629/0e3e2be1e66d, www.oracle.com/security-alerts/ | Mostly free public; some vendor subscriptions/support accounts may be required | Vendor truth for affected products, fixed versions, mitigations, & exploitation notes. |

#### 15.5 Tier 4 - severity & prioritization

| Sl. # | Title                                    | Link(s)                                                                                                                      | Access / Cost                                                  | Relevance Notes & POIs                                                                              |
| ----- | ---------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- |
| 1     | CVSS v3.1/v4.0                           | www.first.org/cvss/v3.1/specification-document, www.first.org/cvss/v4.0/specification-document                               | Free public                                                    | Standard severity scoring.                                                                          |
| 2     | EPSS                                     | www.first.org/epss/                                                                                                          | Free public data/API                                           | Exploit likelihood prediction.                                                                      |
| 3     | KEV                                      | www.cisa.gov/sites/default/files/feeds/known\_exploited\_vulnerabilities.json                                                | Free public feed                                               | Known exploited vulnerability signal.                                                               |
| 4     | SSVC                                     | github.com/CERTCC/SSVC, www.cisa.gov/stakeholder-specific-vulnerability-categorization-ssvc                                  | Free public / open-source                                      | Decision support for remediation urgency.                                                           |
| 5     | CISA Vulnrichment                        | github.com/cisagov/vulnrichment                                                                                              | Free public GitHub repo                                        | SSVC & enrichment data.                                                                             |
| 6     | Vendor exploited-in-the-wild flags       | msrc.microsoft.com/update-guide, support.apple.com/en-us/100100, www.oracle.com/security-alerts/                             | Free public, though product support details may vary           | Vendor-provided exploitation status.                                                                |
| 7     | Patch availability & fixed-version feeds | access.redhat.com/security/data, github.com/canonical/ubuntu-security-notices, security-tracker.debian.org/tracker/data/json | Free public data; some vendor support may require subscription | Determines whether remediation exists.                                                              |
| 8     | Environmental context                    | docs.greynoise.io, search.censys.io, www.shodan.io                                                                           | Free tiers / paid plans                                        | Internet exposure, asset criticality, privilege boundary, & data sensitivity determine real impact. |

#### 15.6 Tier 5 - exploitability & weaponization

| Sl. # | Title                       | Link(s)                                                                                                               | Access / Cost                                                 | Relevance Notes & POIs                            |
| ----- | --------------------------- | --------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------- | ------------------------------------------------- |
| 1     | Exploit-DB                  | www.exploit-db.com                                                                                                    | Free public                                                   | Public exploit availability.                      |
| 2     | Metasploit modules          | github.com/rapid7/metasploit-framework/tree/master/modules/exploits                                                   | Free / open-source                                            | Weaponized exploit modules.                       |
| 3     | Packet Storm                | packetstormsecurity.com/files/tags/exploit/                                                                           | Free public                                                   | Exploit archive.                                  |
| 4     | Project Zero                | googleprojectzero.blogspot.com, project-zero.issues.chromium.org                                                      | Free public; some issues may be restricted pre-disclosure     | Root-cause & exploitability research.             |
| 5     | CERT/CC VU notes            | www.kb.cert.org/vuls                                                                                                  | Free public                                                   | Coordinated disclosure & affected vendor context. |
| 6     | Rapid7 AttackerKB           | attackerkb.com                                                                                                        | Free public content; commercial offerings separate            | Attacker value & exploitability context.          |
| 7     | GreyNoise                   | docs.greynoise.io, viz.greynoise.io                                                                                   | Free tier / paid plans                                        | Internet exploitation/scanning telemetry.         |
| 8     | Shadowserver                | dashboard.shadowserver.org, www.shadowserver.org                                                                      | Free for eligible organizations; registration may be required | Exposure & threat telemetry.                      |
| 9     | Nuclei templates            | github.com/projectdiscovery/nuclei-templates                                                                          | Free / open-source                                            | Detection templates for exposed vulnerabilities.  |
| 10    | Vendor emergency advisories | www.cisa.gov/cybersecurity-advisories, www.fortiguard.com/psirt, www.ivanti.com/resources/v/doc/ivi/2629/0e3e2be1e66d | Free public                                                   | Emergency/active exploitation guidance.           |

#### 15.7 Tier 6 - weakness, attack-pattern & AI context

| Sl. # | Title                       | Link(s)                                                                                                                                                        | Access / Cost                | Relevance Notes & POIs                   |
| ----- | --------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------- | ---------------------------------------- |
| 1     | CWE                         | cwe.mitre.org                                                                                                                                                  | Free public                  | Weakness taxonomy.                       |
| 2     | CAPEC                       | capec.mitre.org                                                                                                                                                | Free public                  | Attack-pattern taxonomy.                 |
| 3     | ATT\&CK Enterprise          | attack.mitre.org/matrices/enterprise/                                                                                                                          | Free public                  | Enterprise adversary behavior taxonomy.  |
| 4     | ATT\&CK STIX                | github.com/mitre-attack/attack-stix-data                                                                                                                       | Free public GitHub repo      | Machine-readable ATT\&CK data.           |
| 5     | MITRE CTI repo              | github.com/mitre/cti                                                                                                                                           | Free public GitHub repo      | MITRE STIX data repository.              |
| 6     | MITRE ATLAS                 | atlas.mitre.org                                                                                                                                                | Free public                  | AI adversary tactics & techniques.       |
| 7     | OWASP LLM Top 10            | owasp.org/www-project-top-10-for-large-language-model-applications                                                                                             | Free public / open community | LLM application vulnerability taxonomy.  |
| 8     | OWASP ML Security Top 10    | owasp.org/www-project-machine-learning-security-top-10                                                                                                         | Free public / open community | ML security risk taxonomy.               |
| 9     | NIST AI RMF & NIST AI 600-1 | nvlpubs.nist.gov/nistpubs/ai/NIST.AI.100-1.pdf, www.nist.gov/publications/artificial-intelligence-risk-management-framework-generative-artificial-intelligence | Free public                  | AI risk management & GenAI risk profile. |

#### 15.8 Tier 7 - detection engineering & validation

| Sl. # | Title                  | Link(s)                                                                                                                                                                                                                                                          | Access / Cost                                                                                             | Relevance Notes & POIs                            |
| ----- | ---------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------- | ------------------------------------------------- |
| 1     | CodeQL                 | codeql.github.com                                                                                                                                                                                                                                                | Free for many open-source uses; commercial GitHub Advanced Security for many enterprise/private workflows | Semantic code vulnerability detection.            |
| 2     | Semgrep                | semgrep.dev                                                                                                                                                                                                                                                      | Free/open-source CLI; commercial products available                                                       | Pattern-based static analysis.                    |
| 3     | Joern                  | joern.io                                                                                                                                                                                                                                                         | Free / open-source                                                                                        | Code property graph analysis.                     |
| 4     | Infer                  | fbinfer.com                                                                                                                                                                                                                                                      | Free / open-source                                                                                        | Static analysis engine.                           |
| 5     | Sonar rules            | rules.sonarsource.com                                                                                                                                                                                                                                            | Free public catalog; commercial products available                                                        | Sonar Security/code quality rule catalog.         |
| 6     | Nuclei templates       | github.com/projectdiscovery/nuclei-templates                                                                                                                                                                                                                     | Free / open-source                                                                                        | DAST/exposure templates.                          |
| 7     | OSS-Fuzz               | google.github.io/oss-fuzz                                                                                                                                                                                                                                        | Free for eligible open-source projects                                                                    | Continuous fuzzing.                               |
| 8     | SARD / Juliet          | samate.nist.gov/SARD/, samate.nist.gov/SARD/test-suites/112                                                                                                                                                                                                      | Free public                                                                                               | Test suites for vulnerability detection.          |
| 9     | Vulnerability datasets | github.com/DLVulDet/PrimeVul, github.com/Icyrockton/MegaVul, github.com/ZeoVan/MSR\_20\_Code\_vulnerability\_CSV\_Dataset, github.com/secureIT-project/CVEfixes, github.com/tuhh-softsec/vul4j, github.com/wagner-group/diversevul, sites.google.com/view/devign | Mostly free public research datasets; verify license individually                                         | ML/research datasets for vulnerability detection. |

### 16. Recommended canonical data model coverage

A complete vulnerability impact system should be able to ingest or derive the following fields.

#### 16.1 Vulnerability identity

| Sl. # | Title                | Link(s)                                                          | Access / Cost                                                    | Relevance Notes & POIs                |
| ----- | -------------------- | ---------------------------------------------------------------- | ---------------------------------------------------------------- | ------------------------------------- |
| 1     | CVE ID               | github.com/CVEProject/cvelistV5, www.cve.org                     | Free public                                                      | Canonical vulnerability identifier.   |
| 2     | GHSA ID              | github.com/advisories                                            | Free public                                                      | GitHub Security Advisory identifier.  |
| 3     | OSV ID               | osv.dev                                                          | Free public                                                      | OSV vulnerability identifier.         |
| 4     | Vendor advisory ID   | msrc.microsoft.com/update-guide, www.oracle.com/security-alerts/ | Mostly free public; some support details may require entitlement | Vendor-specific advisory identifier.  |
| 5     | CWE ID               | cwe.mitre.org                                                    | Free public                                                      | Weakness class identifier.            |
| 6     | CAPEC ID             | capec.mitre.org                                                  | Free public                                                      | Attack-pattern identifier.            |
| 7     | ATT\&CK technique ID | attack.mitre.org/matrices/enterprise                             | Free public                                                      | Adversary technique identifier.       |
| 8     | ATLAS technique ID   | atlas.mitre.org/techniques                                       | Free public                                                      | AI/ML adversary technique identifier. |
| 9     | Alias graph          | github.com/CVEProject/cvelistV5, github.com/advisories, osv.dev  | Free public                                                      | Maps CVE/GHSA/OSV/vendor aliases.     |

#### 16.2 Affectedness

| Sl. # | Title                          | Link(s)                                                                                | Access / Cost                                                     | Relevance Notes & POIs                                                                   |
| ----- | ------------------------------ | -------------------------------------------------------------------------------------- | ----------------------------------------------------------------- | ---------------------------------------------------------------------------------------- |
| 1     | Product name                   | nvd.nist.gov/products/cpe                                                              | Free public                                                       | Identifies vulnerable products.                                                          |
| 2     | Vendor                         | www.cve.org                                                                            | Free public                                                       | Vendor/product attribution.                                                              |
| 3     | CPE                            | nvd.nist.gov/developers/products                                                       | Free public; optional free API key for higher rate limits         | Product/platform matching.                                                               |
| 4     | PURL                           | github.com/package-url/purl-spec                                                       | Free / open-source                                                | Package identity.                                                                        |
| 5     | Package ecosystem              | osv.dev/list                                                                           | Free public                                                       | Defines package namespace & version rules.                                               |
| 6     | Package name                   | deps.dev                                                                               | Free public                                                       | Dependency identity.                                                                     |
| 7     | Affected version range         | ossf.github.io/osv-schema                                                              | Free / open-source                                                | Expresses vulnerable versions.                                                           |
| 8     | Fixed version                  | github.com/advisories, osv.dev                                                         | Free public                                                       | Remediation target.                                                                      |
| 9     | Introduced version / commit    | ossf.github.io/osv-schema                                                              | Free / open-source                                                | Determines when vulnerability entered codebase.                                          |
| 10    | Last affected version          | ossf.github.io/osv-schema                                                              | Free / open-source                                                | Helps determine affected version bounds.                                                 |
| 11    | Backport status                | access.redhat.com/security/data, security-tracker.debian.org, ubuntu.com/security/cves | Mostly free public; some support details may require subscription | Determines if a distro package is patched despite upstream version appearing vulnerable. |
| 12    | VEX status                     | github.com/openvex/spec, www.csaf.io                                                   | Free / open-source standards                                      | Represents affected, not affected, fixed, or under investigation.                        |
| 13    | Justification for not affected | github.com/openvex/spec                                                                | Free / open-source                                                | Explains why a product is not affected.                                                  |
| 14    | Distro/package release channel | packages.fedoraproject.org, pkgs.alpinelinux.org/packages                              | Free public                                                       | Tracks package release stream.                                                           |

#### 16.3 Severity & exploitability

| Sl. # | Title                                  | Link(s)                                                                                        | Access / Cost                                                            | Relevance Notes & POIs                               |
| ----- | -------------------------------------- | ---------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------ | ---------------------------------------------------- |
| 1     | CVSS v2/v3/v4 vector                   | www.first.org/cvss                                                                             | Free public                                                              | Structured severity vector.                          |
| 2     | CVSS base/temporal/environmental score | nvd.nist.gov/vuln-metrics/cvss                                                                 | Free public                                                              | Severity scoring.                                    |
| 3     | EPSS score                             | www.first.org/epss                                                                             | Free public data/API                                                     | Exploit likelihood.                                  |
| 4     | EPSS percentile                        | www.first.org/epss/data\_stats                                                                 | Free public data downloads                                               | Relative exploit-likelihood ranking.                 |
| 5     | KEV membership                         | www.cisa.gov/sites/default/files/feeds/known\_exploited\_vulnerabilities.json                  | Free public feed                                                         | Known exploited vulnerability marker.                |
| 6     | KEV date added                         | www.cisa.gov/sites/default/files/feeds/known\_exploited\_vulnerabilities.json                  | Free public feed                                                         | Temporal exploitation/prioritization signal.         |
| 7     | Known ransomware usage                 | www.ransomware.live                                                                            | Free public                                                              | Ransomware exploitation context.                     |
| 8     | Public exploit available               | www.exploit-db.com                                                                             | Free public                                                              | PoC/exploit availability.                            |
| 9     | Metasploit module available            | github.com/rapid7/metasploit-framework/tree/master/modules/exploits                            | Free / open-source                                                       | Weaponized exploit implementation.                   |
| 10    | Nuclei template available              | github.com/projectdiscovery/nuclei-templates                                                   | Free / open-source                                                       | Detection template availability.                     |
| 11    | GreyNoise observed scanning            | viz.greynoise.io                                                                               | Free tier / paid plans                                                   | Internet scanning/exploitation telemetry.            |
| 12    | Shadowserver observed exposure         | dashboard.shadowserver.org                                                                     | Free for eligible organizations; registration may be required            | Internet-scale exposure telemetry.                   |
| 13    | CISA SSVC decision points              | github.com/cisagov/vulnrichment                                                                | Free public GitHub repo                                                  | Decision support enrichment.                         |
| 14    | Vendor exploitation status             | msrc.microsoft.com/update-guide, security.paloaltonetworks.com, support.apple.com/en-us/100100 | Free public                                                              | Vendor-provided exploitation notes.                  |
| 15    | Patch availability                     | access.redhat.com/security/data, security-tracker.debian.org, ubuntu.com/security/notices      | Mostly free public; some vendor support details may require subscription | Determines if a fix exists.                          |
| 16    | Workaround availability                | www.cisa.gov/cybersecurity-advisories, www.kb.cert.org/vuls                                    | Free public                                                              | Temporary mitigation when patching is not available. |

#### 16.4 Environmental impact

| Sl. # | Title                             | Link(s)                                                   | Access / Cost                                             | Relevance Notes & POIs                                        |
| ----- | --------------------------------- | --------------------------------------------------------- | --------------------------------------------------------- | ------------------------------------------------------------- |
| 1     | Asset criticality                 | www.cisecurity.org/controls                               | Free public                                               | Business/system importance affects risk.                      |
| 2     | Internet exposure                 | search.censys.io, www.shodan.io                           | Free tiers / paid plans                                   | Determines external exploitability surface.                   |
| 3     | Network reachability              | nmap.org                                                  | Free / open-source                                        | Determines whether an exploit path exists.                    |
| 4     | Authentication required           | www.first.org/cvss                                        | Free public                                               | Impacts exploitability.                                       |
| 5     | Privilege required                | www.first.org/cvss                                        | Free public                                               | Impacts exploitability & blast radius.                        |
| 6     | User interaction required         | www.first.org/cvss                                        | Free public                                               | Impacts exploitability conditions.                            |
| 7     | Exploit preconditions             | googleprojectzero.blogspot.com, www.kb.cert.org/vuls      | Free public                                               | Defines required configuration or state.                      |
| 8     | Data sensitivity                  | www.cisecurity.org/controls                               | Free public                                               | Determines business impact.                                   |
| 9     | Compensating controls             | public.cyber.mil/stigs, www.cisecurity.org/cis-benchmarks | Free public; CIS benchmarks may require free registration | Controls can reduce practical exploitability.                 |
| 10    | Runtime configuration             | docs.dependencytrack.org/datasources/overview/            | Free public docs                                          | Enabled features/modules influence affectedness.              |
| 11    | Feature/module enabled            | github.com/openvex/spec                                   | Free / open-source                                        | VEX not-affected reasoning may depend on disabled code paths. |
| 12    | Cloud account/project/environment | github.com/prowler-cloud/prowler                          | Free / open-source core; commercial products separate     | Cloud context affects exposure & blast radius.                |
| 13    | Blast radius                      | github.com/salesforce/cloudsplaining                      | Free / open-source                                        | Privilege & dependency spread determine impact.               |
| 14    | Business process ownership        | www.cisecurity.org/controls                               | Free public                                               | Ownership determines remediation accountability.              |

#### 16.5 Detection & remediation

| Sl. # | Title                        | Link(s)                                                                                                                                                                                | Access / Cost                                                            | Relevance Notes & POIs                                                                                 |
| ----- | ---------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------ |
| 1     | Scanner finding ID           | dependencytrack.org, github.com/anchore/grype, trivy.dev/docs/latest/scanner/vulnerability/                                                                                            | Free / open-source core tools; commercial support/products may exist     | Scanner-specific finding identity.                                                                     |
| 2     | Detection method             | codeql.github.com, github.com/projectdiscovery/nuclei, owasp.org/www-project-top-ten/                                                                                                  | Mixed                                                                    | Indicates whether finding came from SBOM, CPE, package manager, SAST, DAST, IaC, or runtime telemetry. |
| 3     | Confidence                   | github.com/openvex/spec                                                                                                                                                                | Free / open-source                                                       | Confidence helps rank findings.                                                                        |
| 4     | False-positive reason        | github.com/openvex/spec                                                                                                                                                                | Free / open-source                                                       | Captures why a match is not actually exploitable or affected.                                          |
| 5     | Fix version                  | github.com/advisories, osv.dev                                                                                                                                                         | Free public                                                              | Remediation target version.                                                                            |
| 6     | Patch advisory               | access.redhat.com/security/data, ubuntu.com/security/notices, www.debian.org/security                                                                                                  | Mostly free public; some vendor support details may require subscription | Links vulnerability to vendor patch guidance.                                                          |
| 7     | Mitigation                   | www.cisa.gov/cybersecurity-advisories, www.kb.cert.org/vuls                                                                                                                            | Free public                                                              | Temporary or compensating controls.                                                                    |
| 8     | Workaround                   | www.kb.cert.org/vuls                                                                                                                                                                   | Free public                                                              | Alternative remediation when patch unavailable.                                                        |
| 9     | Exploit detection signatures | github.com/SigmaHQ/sigma, github.com/VirusTotal/yara, github.com/projectdiscovery/nuclei-templates                                                                                     | Free / open-source public GitHub repos                                   | Detection content for exploit attempts or compromise.                                                  |
| 10    | Regression test              | github.com/google/oss-fuzz, google.github.io/oss-fuzz                                                                                                                                  | Free / open-source; OSS-Fuzz service for eligible OSS projects           | Tests that a vulnerability class or bug does not reappear.                                             |
| 11    | Verification command         | github.com/anchore/grype, github.com/aquasecurity/trivy-db, github.com/projectdiscovery/nuclei                                                                                         | Free / open-source                                                       | Command/procedure to verify vulnerability or remediation state.                                        |
| 12    | SLA due date                 | www.cisa.gov/news-events/directives/bod-22-01-reducing-significant-risk-known-exploited-vulnerabilities, www.cisa.gov/sites/default/files/feeds/known\_exploited\_vulnerabilities.json | Free public                                                              | Remediation deadline derived from KEV, severity, exposure, policy, or business context.                |

### 17. Minimal source set for production use

| Sl. # | Title                         | Link(s)                                                                                                                                                                                                                                                                             | Access / Cost                                                          | Relevance Notes & POIs                                |
| ----- | ----------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------- | ----------------------------------------------------- |
| 1     | CVE List v5                   | github.com/CVEProject/cvelistV5                                                                                                                                                                                                                                                     | Free public GitHub repo                                                | Canonical CVE records.                                |
| 2     | CVE schema                    | github.com/CVEProject/cve-schema                                                                                                                                                                                                                                                    | Free public GitHub repo                                                | CVE schema validation.                                |
| 3     | NVD CVE API                   | nvd.nist.gov/developers/vulnerabilities                                                                                                                                                                                                                                             | Free public; optional free API key for higher rate limits              | CVSS/CPE/CWE enrichment.                              |
| 4     | NVD CPE API                   | nvd.nist.gov/developers/products                                                                                                                                                                                                                                                    | Free public; optional free API key for higher rate limits              | Product/platform identity matching.                   |
| 5     | OSV full database             | google.github.io/osv.dev/data/#full-database-download                                                                                                                                                                                                                               | Free public                                                            | OSS package vulnerability database.                   |
| 6     | OSV schema                    | ossf.github.io/osv-schema                                                                                                                                                                                                                                                           | Free / open-source                                                     | OSS vulnerability record schema.                      |
| 7     | GitHub Advisory Database repo | github.com/github/advisory-database                                                                                                                                                                                                                                                 | Free / open-source public GitHub repo                                  | Raw GitHub advisory records.                          |
| 8     | CISA KEV JSON                 | www.cisa.gov/sites/default/files/feeds/known\_exploited\_vulnerabilities.json                                                                                                                                                                                                       | Free public feed                                                       | Known exploitation signal.                            |
| 9     | CISA Vulnrichment             | github.com/cisagov/vulnrichment                                                                                                                                                                                                                                                     | Free public GitHub repo                                                | CISA ADP & SSVC enrichment.                           |
| 10    | FIRST EPSS                    | www.first.org/epss/                                                                                                                                                                                                                                                                 | Free public data/API                                                   | Exploit likelihood prediction.                        |
| 11    | CWE downloads                 | cwe.mitre.org/data/downloads.html                                                                                                                                                                                                                                                   | Free public downloads                                                  | Weakness taxonomy ingestion.                          |
| 12    | CAPEC downloads               | capec.mitre.org/data/downloads.html                                                                                                                                                                                                                                                 | Free public downloads                                                  | Attack-pattern taxonomy ingestion.                    |
| 13    | ATT\&CK STIX data             | github.com/mitre-attack/attack-stix-data                                                                                                                                                                                                                                            | Free public GitHub repo                                                | Machine-readable adversary techniques.                |
| 14    | MITRE ATLAS                   | atlas.mitre.org                                                                                                                                                                                                                                                                     | Free public                                                            | AI/ML adversary framework.                            |
| 15    | CycloneDX                     | cyclonedx.org/specification/overview/                                                                                                                                                                                                                                               | Free / open standard                                                   | SBOM/vulnerability/VEX-capable standard.              |
| 16    | SPDX                          | spdx.dev/specifications/                                                                                                                                                                                                                                                            | Free / open standard                                                   | SBOM & package metadata standard.                     |
| 17    | PURL                          | github.com/package-url/purl-spec                                                                                                                                                                                                                                                    | Free / open-source                                                     | Package identity.                                     |
| 18    | CSAF                          | docs.oasis-open.org/csaf/csaf/v2.0/os/csaf-v2.0-os.html                                                                                                                                                                                                                             | Free / open standard                                                   | Structured security advisories.                       |
| 19    | OpenVEX                       | github.com/openvex/spec                                                                                                                                                                                                                                                             | Free / open-source                                                     | Affected/not-affected status communication.           |
| 20    | Distro feeds                  | access.redhat.com/security/data, alas.aws.amazon.com, linux.oracle.com/security/, packages.cgr.dev/chainguard/security.json, packages.wolfi.dev/os/security.json, secdb.alpinelinux.org, security-tracker.debian.org, ubuntu.com/security/oval, www.suse.com/support/security/csaf/ | Mostly free public; some vendor support/subscription details may apply | Distro-specific affectedness & patch status.          |
| 21    | Exploit signal feeds          | docs.greynoise.io, github.com/rapid7/metasploit-framework, project-zero.issues.chromium.org, www.exploit-db.com, www.kb.cert.org/vuls, www.shadowserver.org                                                                                                                         | Mixed                                                                  | Exploitability, weaponization, & exposure enrichment. |

### 18. Final structure for all vulnerability management sources & exposure listings

| Sl. # | Title                                       | Link(s)                                                                                                                                                                                                                                                                                   | Access / Cost                                                                                                | Relevance Notes & POIs                                                                                    |
| ----- | ------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------- |
| 1     | Canonical vulnerability records             | github.com/CVEProject/cvelistV5, github.com/cisagov/vulnrichment, nvd.nist.gov/, www.cve.org                                                                                                                                                                                              | Free public / open-source; NVD optional API key & enrichment                                                 | CVE, NVD, CVE schema, & CISA Vulnrichment provide base vulnerability identity & enrichment.               |
| 2     | Package & ecosystem advisories              | github.com/advisories, github.com/github/advisory-database, osv.dev                                                                                                                                                                                                                       | Free public / open-source                                                                                    | OSV, GHSA, & language advisory DBs provide package-level affected version data.                           |
| 3     | Vendor & distro affectedness                | access.redhat.com/security/data, secdb.alpinelinux.org, security-tracker.debian.org, ubuntu.com/security/oval, www.suse.com/support/security/csaf/                                                                                                                                        | Mostly free public; some vendor support entitlements may apply                                               | CSAF, VEX, OVAL, secdb, OSV, & vendor advisories identify whether a specific product/package is affected. |
| 4     | Exploitability & prioritization             | github.com/rapid7/metasploit-framework, viz.greynoise.io, www.cisa.gov/sites/default/files/feeds/known\_exploited\_vulnerabilities.json, www.exploit-db.com, www.first.org/epss/                                                                                                          | Mixed: free public, open-source, free tiers / paid plans                                                     | KEV, EPSS, SSVC, CVSS, Exploit-DB, Metasploit, & GreyNoise inform urgency.                                |
| 5     | Weakness & adversary mapping                | attack.mitre.org/matrices/enterprise/, atlas.mitre.org/, capec.mitre.org/, cwe.mitre.org/                                                                                                                                                                                                 | Free public                                                                                                  | CWE, CAPEC, ATT\&CK, & ATLAS map vulnerabilities to weaknesses & adversary behavior.                      |
| 6     | AI-specific vulnerability context           | atlas.mitre.org/, owasp.org/www-project-machine-learning-security-top-10/, owasp.org/www-project-top-10-for-large-language-model-applications/, www.nist.gov/itl/ai-risk-management-framework                                                                                             | Free public / open community                                                                                 | ATLAS, OWASP LLM Top 10, OWASP ML Top 10, & NIST AI RMF frame AI/ML risk.                                 |
| 7     | SBOM & identity                             | cyclonedx.org/specification/overview/, github.com/package-url/purl-spec, nvd.nist.gov/products/cpe, spdx.dev/specifications/                                                                                                                                                              | Free public / open standards                                                                                 | CycloneDX, SPDX, PURL, CPE, & SWID identify components for matching.                                      |
| 8     | Exposure telemetry                          | leakix.net/, search.censys.io/, viz.greynoise.io/, www.shadowserver.org/, www.shodan.io/                                                                                                                                                                                                  | Mixed: free public, free tiers, paid plans, registration-based access                                        | Censys, Shodan, Shadowserver, GreyNoise, LeakIX, & internal inventory help assess real exposure.          |
| 9     | Malicious package & supply-chain compromise | github.com/advisories?query=type%3Amalware, github.com/ossf/malicious-packages, github.com/ossf/package-analysis, security.snyk.io, socket.dev/blog, sonatype.com/resources/vulnerability-database                                                                                        | Mixed: free public, open-source, free tiers / commercial products                                            | Tracks malicious package risk that may not appear as conventional CVEs.                                   |
| 10    | Detection engineering                       | codeql.github.com/, github.com/projectdiscovery/nuclei, google.github.io/oss-fuzz/, joern.io/, samate.nist.gov/SARD/, semgrep.dev/                                                                                                                                                        | Mixed: free/open-source, free public datasets, commercial tiers for some support products                    | Detection quality depends on rule precision, context, & evidence quality.                                 |
| 11    | Threat intelligence, ransomware & IOC       | blog.google/threat-analysis-group/, blog.talosintelligence.com/, cloud.google.com/blog/topics/threat-intelligence, unit42.paloaltonetworks.com/, www.microsoft.com/en-us/security/blog/topic/threat-intelligence/, www.rapid7.com/blog/tag/vulnerability-management/, www.ransomware.live | Mostly free public blogs/research; commercial threat intel products provide exploitation-in-the-wild context | Research sources vary in timeliness, depth, & attribution confidence.                                     |
| 12    | Compliance & configuration impact           | github.com/ComplianceAsCode/content, ncp.nist.gov, public.cyber.mil/stigs, www.cisecurity.org/cis-benchmarks, www.open-scap.org                                                                                                                                                           | Mostly free public / open-source; CIS benchmarks may require free registration; commercial tools exist       | These are not vulnerability feeds but determine practical risk & exploitability.                          |

### License

Copyright ■ 2025 Keerthana Purushotham [keep.consult@proton.me](mailto:keep.consult@proton.me).

Licensed under the GNU AGPL v3. See LICENSE for details.

see license (https://github.com/keerthanap8898/CveToad/blob/main/LICENSE)

### Note

Some vendor/security pages change URLs over time, so treat this as a high-coverage baseline rather than a mathematically exhaustive list of every possible vulnerability source.
