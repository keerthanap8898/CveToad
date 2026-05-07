# Vuln Data Sources.original

A consolidated super-set vulnerability-management source inventory for assessing impact, severity, exploitability, exposure, affectedness, prioritization, and remediation of vulnerabilities in technical systems.

## TO-DO

* Add prior known(to myself) sources, package lists, pagure, env specifications, hardware specs, OS specific plug ins, Paywalls section/column, super-set schemas, universal pkg-tree in merkle-DAG format,
* Remediation sources, SIG Forums and sources, Well-know exploit Blogs, books, papers, course material, youtube videos, tutorials, social media articles, etc. idk lol.

## License

* Copyright ■ 2025 Keerthana Purushotham `<keep.consult@proton.me>`.
* Licensed under the GNU AGPL v3. See LICENSE for details.
* see license (https://github.com/keerthanap8898/CveToad/blob/main/LICENSE)

## Note

* Some vendor/security pages change URLs over time, so treat this as a high-coverage baseline rather than a mathematically exhaustive list of every possible vulnerability source.
* Key access assumptions were checked against official/public docs where feasible: NVD is free with stricter unauthenticated rate limits and higher limits with an API key; GitHub Advisory Database is free/open-source for global advisories; CISA KEV is public; FIRST EPSS is freely available via CSV/API.
* Access / Cost labels are best-effort. Many sources are free to read but may require authentication, registration, support entitlement, API keys, paid tiers, or commercial licenses for higher-volume automation, advanced APIs, or complete data. Recheck terms before production ingestion.

## 0. Corrections & normalization notes

1. **Project Zero issue tracker migration**
   * Link(s): bugs.chromium.org/p/project-zero/issues/list (https: / / bugs. chromium. org/ p/ project- zero/ issues/ list), project-zero.issues.chromium.org (https: / / project- zero. issues. chromium. org/ )
   * Access / Cost: Free public web access
   * Relevance: Tracks high-quality vulnerability research, root-cause analysis, exploitability notes, and coordinated disclosure. Useful for exploitability context and historical vulnerability behavior.
   * Notes: Prefer the current tracker for ongoing lookups. Keep the old Monorail-style link for historical references that still appear in older writeups.
2. **Alpine SecDB mirror normalization**
   * Link(s): github.com/alpinelinux/alpine-secdb (https: / / github. com/ alpinelinux/ alpine- secdb), secdb.alpinelinux.org (https: / / secdb. alpinelinux. org/ )
   * Access / Cost: Free / open-source
   * Relevance: Provides Alpine package vulnerability affectedness. Important for container images using Alpine as a base.
   * Notes: The GitHub mirror is deprecated. Use secdb.alpinelinux.org as the primary ingestion source.
3. **Wolfi / Chainguard feed split**
   * Link(s): packages.cgr.dev/chainguard/security.json (https: / / packages. cgr. dev/ chainguard/ security. json), packages.wolfi.dev/os/security.json (https: / / packages. wolfi. dev/ os/ security. json)
   * Access / Cost: Free public feed for Wolfi; Chainguard feed may depend on product entitlement
   * Relevance: Provides secdb-style security feeds for Wolfi and Chainguard images. Key for modern minimal container images.
   * Notes: The Wolfi feed and Chainguard Enterprise feed represent related but distinct package universes. Avoid treating them as exact duplicates.
4. **GitHub Advisory APIs**
   * Link(s): docs.github.com/en/graphql/reference/objects#securityadvisory (https: / / docs. github. com/ en/ graphql/ reference/ objects# securityadvisory), docs.github.com/en/rest/security-advisories (https: / / docs. github. com/ en/ rest/ security- advisories), docs.github.com/en/rest/security-advisories/global-advisories (https: / / docs. github. com/ en/ rest/ security- advisories/ global- advisories)
   * Access / Cost: Free public global advisories; authenticated API / repository advisories may require GitHub account and permissions
   * Relevance: Enables programmatic access to GitHub advisories, including GHSA records, CVE aliases, ecosystems, version ranges, and malware advisories.
   * Notes: Keep both GraphQL and REST. GraphQL is useful for complex queries; REST is simpler for ingestion and pagination.
5. **NVD feeds vs APIs**
   * Link(s): nvd.nist.gov/developers (https: / / nvd. nist. gov/ developers), nvd.nist.gov/vuln/data-feeds (https: / / nvd. nist. gov/ vuln/ data- feeds)
   * Access / Cost: Free public; optional free API key for higher rate limits
   * Relevance: NVD provides CVE enrichment, CPE configurations, CVSS vectors, CWE mappings, references, and change metadata.
   * Notes: Prefer NVD 2.0 APIs for ongoing sync. Use bulk feeds for bootstrapping, archival snapshots, or local mirroring.

## 1. Canonical vulnerability identifiers, CVE records & schemas

### 1.1 CVE Program - canonical CVE identity

1. **CVE.org**
   * Link(s): www.cve.org (https: / / www. cve. org/ )
   * Access / Cost: Free public
   * Relevance: Official CVE program portal for CVE IDs, CNA/ADP governance, CVE lookup, and program documentation.
   * Notes: Canonical governance source, but not always the richest technical source for scoring, affected versions, or exploitability.
2. **CVE List v5 - official GitHub mirror/cache**
   * Link(s): github.com/CVEProject/cvelistV5 (https: / / github. com/ CVEProject/ cvelistV5)
   * Access / Cost: Free / open-source public GitHub repo
   * Relevance: Primary public GitHub cache of CVE v5 JSON records. Useful for local mirroring, batch parsing, and canonical CVE field extraction.
   * Notes: Records may vary in completeness by CNA. Use with NVD, OSV, and vendor advisories for enrichment.
3. **CVE Record Format schema - direct JSON schema**
   * Link(s): github.com/CVEProject/cve-schema/blob/main/schema/CVE\_Record\_Format.json (https: / / github. com/ CVEProject/ cve- schema/ blob/ main/ schema/ CVE\_ Record\_ Format. json)
   * Access / Cost: Free / open-source public GitHub repo
   * Relevance: Machine-validation schema for CVE v5 records. Required for parser validation and ingestion guardrails.
   * Notes: Schema correctness does not imply record semantic completeness. Validate schema and still handle missing CNA fields.
4. **CVE schema repository**
   * Link(s): github.com/CVEProject/cve-schema (https: / / github. com/ CVEProject/ cve- schema)
   * Access / Cost: Free / open-source public GitHub repo
   * Relevance: Contains schema versions, tests, examples, release history, and format evolution.
   * Notes: Track schema version drift when maintaining long-lived ingestion pipelines.
5. **CVE Services API / CVE Program API**
   * Link(s): cveawg.mitre.org/api-docs (https: / / cveawg. mitre. org/ api- docs/ )
   * Access / Cost: Free public docs; API workflows may require role/account for CNA functions
   * Relevance: Direct CVE lookup and CVE Services API documentation. Useful for targeted lookup workflows.
   * Notes: API usage may differ from GitHub mirror sync behavior. Use for lookup, not necessarily full mirroring.
6. **CVE Authorized Data Publishers - ADPs**
   * Link(s): www.cve.org/ProgramOrganization/ADPs (https: / / www. cve. org/ ProgramOrganizatio n/ ADPs)
   * Access / Cost: Free public
   * Relevance: Lists ADPs that can enrich CVE records beyond CNA-provided content.
   * Notes: ADP enrichment can add critical assessment context. Treat ADP data as enrichment layered on top of canonical CNA data.
7. **CISA Vulnrichment - CVE ADP enrichment**
   * Link(s): github.com/cisagov/vulnrichment (https: / / github. com/ cisagov/ vulnrichment)
   * Access / Cost: Free / open-source public GitHub repo
   * Relevance: Provides CISA ADP enrichment of CVE records, including SSVC decision points, and sometimes CWE/CVSS details.
   * Notes: Useful for prioritization. Coverage may not be universal across all CVEs. Track freshness and missing enrichment states.

### 1.2 NVD - CVE enrichment, CPE matching, CVSS & configurations

1. **NVD home**
   * Link(s): nvd.nist.gov (https: / / nvd. nist. gov/ )
   * Access / Cost: Free public
   * Relevance: U.S. government vulnerability-management repository. Provides vulnerability metadata, scoring, product mapping, and references.
   * Notes: NVD enrichment may lag behind CVE publication or vendor disclosures. Monitor modified dates.
2. **NVD CVE API 2.0**
   * Link(s): nvd.nist.gov/developers/vulnerabilities (https: / / nvd. nist. gov/ developers/ vulnerabilities)
   * Access / Cost: Free public; optional free API key for higher rate limits
   * Relevance: Retrieves CVEs with CVSS, weaknesses, references, CPE configurations, and change history.
   * Notes: Central for CPE-based product matching. Rate limits and API keys may affect ingestion design.
3. **NVD CPE API 2.0**
   * Link(s): nvd.nist.gov/developers/products (https: / / nvd. nist. gov/ developers/ products)
   * Access / Cost: Free public; optional free API key for higher rate limits
   * Relevance: Provides CPE dictionary and CPE match criteria for product/platform matching.
   * Notes: CPE can be imprecise for packages, forks, backports, and cloud services. Combine with PURL, OSV, and vendor feeds.
4. **NVD Data Feeds**
   * Link(s): nvd.nist.gov/vuln/data-feeds (https: / / nvd. nist. gov/ vuln/ data- feeds)
   * Access / Cost: Free public
   * Relevance: Bulk JSON feeds for CVEs, CPE dictionary, and CPE match feeds. Useful for initial database bootstrapping.
   * Notes: APIs are generally preferred for ongoing updates. Feeds are useful for snapshots and offline ingestion.
5. **NVD CVSS resources**
   * Link(s): nvd.nist.gov/vuln-metrics/cvss (https: / / nvd. nist. gov/ vuln- metrics/ cvss)
   * Access / Cost: Free public
   * Relevance: CVSS calculators, vector definitions, and severity scoring references.
   * Notes: CVSS is severity, not exploit likelihood. Combine with EPSS, KEV, exposure, and asset criticality.
6. **NVD CPE Dictionary**
   * Link(s): nvd.nist.gov/products/cpe (https: / / nvd. nist. gov/ products/ cpe)
   * Access / Cost: Free public
   * Relevance: CPE product naming and matching basis.
   * Notes: CPE coverage and naming consistency vary. False positives are common without vendor/package-specific affectedness.
7. **NVD API documentation root**
   * Link(s): nvd.nist.gov/developers (https: / / nvd. nist. gov/ developers)
   * Access / Cost: Free public
   * Relevance: API family documentation for NVD data access.
   * Notes: Use this as the stable entry point for NVD API changes.
8. **NVD CVE Change History API**
   * Link(s): nvd.nist.gov/developers/vulnerabilities (https: / / nvd. nist. gov/ developers/ vulnerabilities)
   * Access / Cost: Free public; optional free API key for higher rate limits
   * Relevance: Enables monitoring changes to CVE enrichment, scoring, references, and configurations.
   * Notes: Treat NVD records as mutable. Store ingestion timestamp, source modified timestamp, and prior versions where possible.

### 1.3 Optional CVE meta-mirrors / commercial-community enrichments

These are useful as secondary sources, not canonical replacements.

1. **VulnCheck NVD++**
   * Link(s): www.vulncheck.com/nvd2 (https: / / www. vulncheck. com/ nvd2)
   * Access / Cost: Commercial; limited free/public info may exist
   * Relevance: Aggregated vulnerability intelligence that can supplement CVE/NVD/KEV workflows.
   * Notes: Commercial/community enrichment. Validate terms, licensing, API access, and provenance before production use.
2. **Vulners**
   * Link(s): vulners.com (https: / / vulners. com/ )
   * Access / Cost: Free web search; API/advanced features may require paid plan
   * Relevance: Vulnerability intelligence aggregator across many advisory and exploit sources.
   * Notes: Useful for broad search and enrichment. Do not treat as canonical without source provenance.
3. **OpenCVE**
   * Link(s): www.opencve.io (https: / / www. opencve. io/ )
   * Access / Cost: Free tier / paid plans
   * Relevance: CVE monitoring, subscriptions, change tracking, and alerting workflows.
   * Notes: Useful for monitoring, but canonical ingestion should still pull from upstream CVE/NVD/vendor feeds.
4. **CIRCL CVE Search**
   * Link(s): cve.circl.lu (https: / / cve. circl. lu/ )
   * Access / Cost: Free public
   * Relevance: CVE search and enrichment source, historically useful for threat-intel workflows.
   * Notes: Validate freshness before relying on it. Prefer canonical sources for production scoring.

## 2. Open-source vulnerability databases & package advisory sources

### 2.1 OSV ecosystem

1. **OSV main site**
   * Link(s): osv.dev (https://osv.dev/)
   * Access / Cost: Free public / open data
   * Relevance: Aggregates OSS vulnerabilities by package ecosystem, version, commit, and aliases.
   * Notes: OSV is package/version-centric and often better than CPE for OSS packages. Coverage depends on upstream ecosystem feeds.
2. **OSV vulnerability list**
   * Link(s): osv.dev/list (https: / / osv. dev/ list)
   * Access / Cost: Free public
   * Relevance: Human-browsable OSV records.
   * Notes: Useful for manual triage and ecosystem browsing. Prefer API/full downloads for automation.
3. **OSV full database download**
   * Link(s): google.github.io/osv.dev/data/#full-database-download (https: / / google. github. io/ osv. dev/ data/ # full- database- download)
   * Access / Cost: Free public / open data
   * Relevance: Full database ZIP, including withdrawn records, via gs://osv-vulnerabilities/all.zip.
   * Notes: Best for local mirroring. Preserve withdrawn records for historical auditability.
4. **OSV data sources page**
   * Link(s): google.github.io/osv.dev/data (https: / / google. github. io/ osv. dev/ data)
   * Access / Cost: Free public
   * Relevance: Per-ecosystem downloads and full-database download.
   * Notes: Useful for targeted ecosystem ingestion.
5. **OSV schema rendered spec**
   * Link(s): ossf.github.io/osv-schema (https: / / ossf. github. io/ osv- schema/ )
   * Access / Cost: Free public / open-source
   * Relevance: Standard interchange format for OSS vulnerability records.
   * Notes: Handle aliases, affected ranges, fixed versions, withdrawn records, and ecosystem-specific semantics.
6. **OSV schema GitHub repo**
   * Link(s): github.com/ossf/osv-schema (https: / / github. com/ ossf/ osv- schema)
   * Access / Cost: Free / open-source public GitHub repo
   * Relevance: Schema source, releases, bindings, and tooling.
   * Notes: Track schema versions and validation changes over time.
7. **OSV API docs**
   * Link(s): google.github.io/osv.dev/post-v1-query (https: / / google. github. io/ osv. dev/ post- v1- query/ )
   * Access / Cost: Free public API
   * Relevance: Query vulnerabilities by package, version, commit, or vulnerability ID.
   * Notes: Good for online lookup. Use full downloads for high-volume local matching.
8. **OSV Scanner**
   * Link(s): google.github.io/osv-scanner (https: / / google. github. io/ osv- scanner/ )
   * Access / Cost: Free public / open-source
   * Relevance: Reference scanner using OSV data.
   * Notes: Useful implementation reference for lockfile parsing and version matching.
9. **OSV Scanner GitHub**
   * Link(s): github.com/google/osv-scanner (https: / / github. com/ google/ osv- scanner)
   * Access / Cost: Free / open-source public GitHub repo
   * Relevance: Scanner implementation, matching logic, and lockfile parsing.
   * Notes: Review for practical matching edge cases.
10. **OSV ecosystem list**
    * Link(s): osv.dev/list (https: / / osv. dev/ list)
    * Access / Cost: Free public
    * Relevance: Ecosystem browsing for Maven, npm, PyPI, Go, crates.io, Debian, Alpine, Ubuntu, Wolfi, OSS-Fuzz, etc.
    * Notes: Repeats the list URL intentionally because it serves both record browsing and ecosystem discovery.

### 2.2 GitHub Advisory Database

1. **GitHub Advisory Database - web**
   * Link(s): github.com/advisories (https: / / github. com/ advisories)
   * Access / Cost: Free public
   * Relevance: GitHub-reviewed, unreviewed, malware, GHSA, and CVE advisory records across ecosystems.
   * Notes: GHSA records can exist without CVEs. Preserve alias relationships between GHSA, CVE, and OSV.
2. **GitHub Advisory Database repo**
   * Link(s): github.com/github/advisory-database (https: / / github. com/ github/ advisory- database)
   * Access / Cost: Free / open-source public GitHub repo
   * Relevance: Raw advisory data for local ingestion.
   * Notes: Use for mirroring; validate ecosystem/version range semantics.
3. **About GitHub Advisory Database**
   * Link(s): docs.github.com/en/code-security/concepts/vulnerability-reporting-and-management/about-the-github-advisory-database (https: / / docs. github. com/ en/ code- security/ concepts/ vulnerability- reporting- and- management/ about- the- github- advisory- database)
   * Access / Cost: Free public docs
   * Relevance: Explains reviewed, unreviewed, and malware advisory model.
   * Notes: Important for confidence scoring. Reviewed vs unreviewed status affects dependability.
4. **GitHub Security Advisory GraphQL**
   * Link(s): docs.github.com/en/graphql/reference/objects#securityadvisory (https: / / docs. github. com/ en/ graphql/ reference/ objects# securityadvisory)
   * Access / Cost: Free docs; API usage may require GitHub auth token
   * Relevance: Programmatic advisory metadata access via GraphQL.
   * Notes: Useful for complex filtered queries. Requires API authentication for robust use.
5. **GitHub REST API - global security advisories**
   * Link(s): docs.github.com/en/rest/security-advisories/global-advisories (https: / / docs. github. com/ en/ rest/ security- advisories/ global- advisories)
   * Access / Cost: Free public API; auth recommended for higher rate limits
   * Relevance: REST access for listing and retrieving global security advisories.
   * Notes: Easier to integrate than GraphQL for many ingestion jobs.
6. **GitHub REST API - security advisories root**
   * Link(s): docs.github.com/en/rest/security-advisories (https: / / docs. github. com/ en/ rest/ security- advisories)
   * Access / Cost: Free public docs; some repository endpoints require permissions
   * Relevance: Root documentation for global and repository security advisory endpoints.
   * Notes: Use to distinguish global advisories from repo-private advisories.
7. **GitHub Dependabot alerts REST API**
   * Link(s): docs.github.com/en/rest/dependabot/alerts (https: / / docs. github. com/ en/ rest/ dependabot/ alerts)
   * Access / Cost: Requires GitHub account, repository access, and relevant permissions
   * Relevance: Repository-specific vulnerability exposure from dependency graph.
   * Notes: Requires repo access. Useful for actual asset exposure, not just global vulnerability existence.
8. **Dependabot supported ecosystems**
   * Link(s): docs.github.com/en/code-security/reference/supply-chain-security/supported-ecosystems-and-repositories (https: / / docs. github. com/ en/ code- security/ reference/ supply- chain- security/ supported- ecosystems- and- repositories)
   * Access / Cost: Free public docs
   * Relevance: Supported ecosystem list for GitHub dependency graph and alerts.
   * Notes: Coverage constraints impact blind spots in detection.
9. **GitHub malware advisories**
   * Link(s): github.com/advisories?query=type%3Amalware (https: / / github. com/ advisories? query= type% 3Amalware)
   * Access / Cost: Free public
   * Relevance: Malicious package advisories.
   * Notes: Useful for supply-chain compromise detection beyond CVE-style vulnerabilities.
10. **GitHub npm advisories**
    * Link(s): github.com/advisories?query=ecosystem%3Anpm (https: / / github. com/ advisories? query= ecosystem% 3Anpm)
    * Access / Cost: Free public
    * Relevance: npm ecosystem advisories.
    * Notes: Version ranges and semver semantics are ecosystem-specific.
11. **GitHub pip advisories**
    * Link(s): github.com/advisories?query=ecosystem%3Apip (https: / / github. com/ advisories? query= ecosystem% 3Apip)
    * Access / Cost: Free public
    * Relevance: Python/PyPI advisories.
    * Notes: Cross-check with PyPA advisory DB and OSV.
12. **GitHub Maven advisories**
    * Link(s): github.com/advisories?query=ecosystem%3Amaven (https: / / github. com/ advisories? query= ecosystem% 3Amaven)
    * Access / Cost: Free public
    * Relevance: Maven ecosystem advisories.
    * Notes: Maven coordinates and shaded dependencies can complicate affectedness.
13. **GitHub NuGet advisories**
    * Link(s): github.com/advisories?query=ecosystem%3Anuget (https: / / github. com/ advisories? query= ecosystem% 3Anuget)
    * Access / Cost: Free public
    * Relevance: NuGet ecosystem advisories.
    * Notes: Useful for .NET dependency assessment.
14. **GitHub Go advisories**
    * Link(s): github.com/advisories?query=ecosystem%3Ago (https: / / github. com/ advisories? query= ecosystem% 3Ago)
    * Access / Cost: Free public
    * Relevance: Go ecosystem advisories.
    * Notes: Cross-check with official Go vulnerability DB.
15. **GitHub RubyGems advisories**
    * Link(s): github.com/advisories?query=ecosystem%3Arubygems (https: / / github. com/ advisories? query= ecosystem% 3Arubygems)
    * Access / Cost: Free public
    * Relevance: RubyGems advisories.
    * Notes: Cross-check with RubySec.
16. **GitHub Rust advisories**
    * Link(s): github.com/advisories?query=ecosystem%3Arust (https: / / github. com/ advisories? query= ecosystem% 3Arust)
    * Access / Cost: Free public
    * Relevance: Rust crate advisories.
    * Notes: Cross-check with RustSec.
17. **GitHub Composer advisories**
    * Link(s): github.com/advisories?query=ecosystem%3Acomposer (https: / / github. com/ advisories? query= ecosystem% 3Acomposer)
    * Access / Cost: Free public
    * Relevance: PHP Composer advisories.
    * Notes: Cross-check with FriendsOfPHP and Packagist.
18. **GitHub Pub advisories**
    * Link(s): github.com/advisories?query=ecosystem%3Apub (https: / / github. com/ advisories? query= ecosystem% 3Apub)
    * Access / Cost: Free public
    * Relevance: Dart/Pub advisories.
    * Notes: Coverage may vary by ecosystem maturity.
19. **GitHub Swift advisories**
    * Link(s): github.com/advisories?query=ecosystem%3Aswift (https: / / github. com/ advisories? query= ecosystem% 3Aswift)
    * Access / Cost: Free public
    * Relevance: Swift package advisories.
    * Notes: Useful for Swift Package Manager ecosystems.
20. **GitHub Erlang advisories**
    * Link(s): github.com/advisories?query=ecosystem%3Aerlang (https: / / github. com/ advisories? query= ecosystem% 3Aerlang)
    * Access / Cost: Free public
    * Relevance: Erlang/Hex advisories.
    * Notes: Validate package naming conventions against Hex.

### 2.3 Language & package ecosystem advisory databases

#### 2.3.1 Go

1. **Go Vulnerability Database**
   * Link(s): vuln.go.dev (https: / / vuln. go. dev/ )
   * Access / Cost: Free public / open data
   * Relevance: Official Go vulnerability database for Go modules.
   * Notes: Strong source for Go-specific affected symbols, modules, packages, and fixed versions.
2. **Go vulnerability database docs**
   * Link(s): go.dev/doc/security/vuln/database (https: / / go. dev/ doc/ security/ vuln/ database)
   * Access / Cost: Free public docs
   * Relevance: Explains Go vulnerability DB data model and OSV usage.
   * Notes: Important for correct ingestion and symbol/package-level interpretation.
3. **Go vuln browser**
   * Link(s): pkg.go.dev/vuln (https: / / pkg. go. dev/ vuln/ )
   * Access / Cost: Free public
   * Relevance: Human-readable curated Go vulnerability reports.
   * Notes: Useful for triage and manual review.
4. **Go vuln tooling**
   * Link(s): pkg.go.dev/golang.org/x/vuln/cmd/govulncheck (https: / / pkg. go. dev/ golang. org/ x/ vuln/ cmd/ govulncheck)
   * Access / Cost: Free / open-source Go module
   * Relevance: Go source/binary vulnerability checking.
   * Notes: Can reduce false positives by analyzing call reachability in Go code.

#### 2.3.2 Rust

1. **RustSec**
   * Link(s): rustsec.org (https: / / rustsec. org/ )
   * Access / Cost: Free public / open-source ecosystem
   * Relevance: Rust crate advisory ecosystem.
   * Notes: Often includes Rust-specific unsoundness, yanked crates, and ecosystem-specific risk.
2. **RustSec advisory DB repo**
   * Link(s): github.com/RustSec/advisory-db (https: / / github. com/ RustSec/ advisory- db)
   * Access / Cost: Free / open-source public GitHub repo
   * Relevance: Machine-ingestible Rust advisories.
   * Notes: Good for local ingestion and cargo-audit compatible workflows.
3. **RustSec advisories browser**
   * Link(s): rustsec.org/advisories (https: / / rustsec. org/ advisories/ )
   * Access / Cost: Free public
   * Relevance: Human-browsable Rust advisories.
   * Notes: Useful for manual triage.
4. **cargo-audit**
   * Link(s): github.com/RustSec/rustsec/tree/main/cargo-audit (https: / / github. com/ RustSec/ rustsec/ tree/ main/ cargo- audit)
   * Access / Cost: Free / open-source public GitHub repo
   * Relevance: RustSec-based vulnerability scanner.
   * Notes: Reference implementation for Rust dependency scanning.

#### 2.3.3 Python / PyPI

1. **PyPA advisory database**
   * Link(s): github.com/pypa/advisory-database (https: / / github. com/ pypa/ advisory- database)
   * Access / Cost: Free / open-source public GitHub repo
   * Relevance: Python/PyPI advisory source.
   * Notes: Use with OSV and GitHub advisories for better Python coverage.
2. **PyPI security page**
   * Link(s): pypi.org/security (https: / / pypi. org/ security/ )
   * Access / Cost: Free public
   * Relevance: PyPI security reporting and advisory context.
   * Notes: Useful for process context, not necessarily complete advisory ingestion.
3. **pip-audit**
   * Link(s): github.com/pypa/pip-audit (https: / / github. com/ pypa/ pip- audit)
   * Access / Cost: Free / open-source public GitHub repo
   * Relevance: Python dependency vulnerability scanner.
   * Notes: Reference implementation for Python dependency assessment.
4. **Safety DB**
   * Link(s): github.com/pyupio/safety-db (https: / / github. com/ pyupio/ safety- db)
   * Access / Cost: Free public GitHub repo; related products may be commercial
   * Relevance: Historical Python advisory source.
   * Notes: Validate freshness and licensing before relying on it.

#### 2.3.4 JavaScript / npm

1. **npm advisories via GitHub**
   * Link(s): github.com/advisories?query=ecosystem%3Anpm (https: / / github. com/ advisories? query= ecosystem% 3Anpm)
   * Access / Cost: Free public
   * Relevance: npm ecosystem vulnerability advisories.
   * Notes: Semver ranges, lockfiles, transitive dependencies, and malicious packages require careful parsing.
2. **Node.js Security Working Group**
   * Link(s): github.com/nodejs/security-wg (https: / / github. com/ nodejs/ security- wg)
   * Access / Cost: Free / open-source public GitHub repo
   * Relevance: Node ecosystem security coordination and historical advisory sources.
   * Notes: Some historical records may be superseded by GitHub Advisory DB.
3. **npm audit docs**
   * Link(s): docs.npmjs.com/cli/commands/npm-audit (https: / / docs. npmjs. com/ cli/ commands/ npm- audit)
   * Access / Cost: Free public docs
   * Relevance: Documents npm audit behavior.
   * Notes: Useful to understand scanner behavior, dependency tree handling, and remediation suggestions.
4. **Socket.dev security research**
   * Link(s): socket.dev/blog (https: / / socket. dev/ blog)
   * Access / Cost: Free public blog; product/API features may be commercial
   * Relevance: Malicious package and JS supply-chain threat intel.
   * Notes: Research source. Validate indicators and package claims against primary registries.

#### 2.3.5 Java / Maven / JVM

1. **Sonatype OSS Index**
   * Link(s): ossindex.sonatype.org (https: / / ossindex. sonatype. org/ )
   * Access / Cost: Free tier / API terms; Sonatype products may be commercial
   * Relevance: OSS vulnerability intelligence commonly used for Maven and other ecosystems.
   * Notes: Commercial/community source. Validate API terms, limits, and provenance.
2. **Sonatype vulnerability database**
   * Link(s): sonatype.com/resources/vulnerability-database (https: / / sonatype. com/ resources/ vulnerability- database)
   * Access / Cost: Free public search / commercial ecosystem
   * Relevance: Sonatype vulnerability intelligence database.
   * Notes: Useful for enrichment and triage, but not canonical.
3. **Maven Central**
   * Link(s): central.sonatype.com (https: / / central. sonatype. com/ )
   * Access / Cost: Free public
   * Relevance: Package identity and metadata for JVM packages.
   * Notes: Not a vulnerability DB, but essential for coordinate resolution and metadata.
4. **OSS Index API docs**
   * Link(s): ossindex.sonatype.org/doc/rest (https: / / ossindex. sonatype. org/ doc/ rest)
   * Access / Cost: Free tier / API terms
   * Relevance: REST API access for OSS Index.
   * Notes: Consider rate limits, authentication, and terms before ingestion.

#### 2.3.6 PHP / Composer

1. **FriendsOfPHP security advisories**
   * Link(s): github.com/FriendsOfPHP/security-advisories (https: / / github. com/ FriendsOfPHP/ security- advisories)
   * Access / Cost: Free / open-source public GitHub repo
   * Relevance: PHP Composer package advisories.
   * Notes: Historical and ecosystem-specific source. Cross-check with Packagist and GHSA.
2. **Packagist security advisories API**
   * Link(s): packagist.org/apidoc#list-security-advisories (https: / / packagist. org/ apidoc# list- security- advisories)
   * Access / Cost: Free public API docs / public API
   * Relevance: Composer package advisory API.
   * Notes: Direct ecosystem source for Composer package advisories.
3. **Composer audit docs**
   * Link(s): getcomposer.org/doc/03-cli.md#audit (https: / / getcomposer. org/ doc/ 03- cli. md# audit)
   * Access / Cost: Free public docs
   * Relevance: Documents Composer audit behavior.
   * Notes: Useful for implementation parity with Composer-native workflows.

#### 2.3.7 Ruby

1. **RubySec advisory DB**
   * Link(s): github.com/rubysec/ruby-advisory-db (https: / / github. com/ rubysec/ ruby- advisory- db)
   * Access / Cost: Free / open-source public GitHub repo
   * Relevance: RubyGems advisories.
   * Notes: Cross-check with GHSA RubyGems advisories.
2. **Bundler audit**
   * Link(s): github.com/rubysec/bundler-audit (https: / / github. com/ rubysec/ bundler- audit)
   * Access / Cost: Free / open-source public GitHub repo
   * Relevance: Ruby dependency vulnerability scanner.
   * Notes: Reference implementation for Gemfile.lock scanning.

#### 2.3.8 .NET / NuGet

1. **NuGet advisories via GitHub**
   * Link(s): github.com/advisories?query=ecosystem%3Anuget (https: / / github. com/ advisories? query= ecosystem% 3Anuget)
   * Access / Cost: Free public
   * Relevance: NuGet ecosystem advisories.
   * Notes: Use with lockfile/project metadata for actual exposure.
2. **NuGet audit docs**
   * Link(s): learn.microsoft.com/en-us/nuget/concepts/auditing-packages (https: / / learn. microsoft. com/ en- us/ nuget/ concepts/ auditing- packages)
   * Access / Cost: Free public docs
   * Relevance: Documents NuGet package auditing.
   * Notes: Useful for Microsoft ecosystem parity and remediation guidance.

#### 2.3.9 Erlang / Elixir / Hex

1. **Erlang advisories via GitHub**
   * Link(s): github.com/advisories?query=ecosystem%3Aerlang (https: / / github. com/ advisories? query= ecosystem% 3Aerlang)
   * Access / Cost: Free public
   * Relevance: Erlang/Hex advisories.
   * Notes: Validate ecosystem naming, package coordinates, and version semantics.
2. **Hex package manager**
   * Link(s): hex.pm (https://hex.pm/)
   * Access / Cost: Free public
   * Relevance: Package registry for Erlang/Elixir packages.
   * Notes: Registry metadata helps resolve package identity.

#### 2.3.10 Dart / Flutter / Pub

1. **Pub advisories via GitHub**
   * Link(s): github.com/advisories?query=ecosystem%3Apub (https: / / github. com/ advisories? query= ecosystem% 3Apub)
   * Access / Cost: Free public
   * Relevance: Dart/Pub advisories.
   * Notes: Coverage depends on GitHub advisory ingestion.
2. **Dart package repository**
   * Link(s): pub.dev (https://pub.dev/)
   * Access / Cost: Free public
   * Relevance: Package registry for Dart/Flutter dependencies.
   * Notes: Useful for package identity and version metadata.

#### 2.3.11 Swift

1. **Swift advisories via GitHub**
   * Link(s): github.com/advisories?query=ecosystem%3Aswift (https: / / github. com/ advisories? query= ecosystem% 3Aswift)
   * Access / Cost: Free public
   * Relevance: Swift ecosystem advisories.
   * Notes: Coverage depends on GitHub Advisory DB support.
2. **Swift Package Index**
   * Link(s): swiftpackageindex.com (https: / / swiftpackageindex. com/ )
   * Access / Cost: Free public
   * Relevance: Swift package metadata and ecosystem context.
   * Notes: Not a vulnerability DB, but useful for package discovery and metadata.

## 3. Exploitation, prioritization, severity & risk scoring

### 3.1 Known exploited vulnerability sources

1. **CISA KEV catalog - web**
   * Link(s): www.cisa.gov/known-exploited-vulnerabilities-catalog (https: / / www. cisa. gov/ known- exploited- vulnerabilities- catalog)
   * Access / Cost: Free public
   * Relevance: Authoritative catalog of known exploited vulnerabilities. Critical for prioritization and remediation urgency.
   * Notes: KEV is a strong exploitation signal but not a complete list of all exploited vulnerabilities.
2. **CISA KEV print view**
   * Link(s): www.cisa.gov/known-exploited-vulnerabilities-catalog-print (https: / / www. cisa. gov/ known- exploited- vulnerabilities- catalog- print)
   * Access / Cost: Free public
   * Relevance: Human-readable print-oriented KEV view.
   * Notes: Useful for documentation and manual review; use JSON for automation.
3. **CISA KEV JSON feed**
   * Link(s): www.cisa.gov/sites/default/files/feeds/known\_exploited\_vulnerabilities.json (https: / / www. cisa. gov/ sites/ default/ files/ feeds/ known\_ exploited\_ vulnerabilities. json)
   * Access / Cost: Free public feed
   * Relevance: Machine-readable KEV feed.
   * Notes: Primary automation source for KEV ingestion. Monitor dateAdded and due dates.
4. **CISA KEV JSON schema**
   * Link(s): www.cisa.gov/sites/default/files/feeds/known\_exploited\_vulnerabilities\_schema.json (https: / / www. cisa. gov/ sites/ default/ files/ feeds/ known\_ exploited\_ vulnerabilities\_ schema. json)
   * Access / Cost: Free public feed
   * Relevance: Schema for KEV JSON validation.
   * Notes: Use for ingestion validation. Schema changes should trigger parser review.
5. **CISA KEV GitHub mirror**
   * Link(s): github.com/cisagov/kev-data (https: / / github. com/ cisagov/ kev- data)
   * Access / Cost: Free / open-source public GitHub repo
   * Relevance: GitHub mirror of KEV data.
   * Notes: Useful for Git-based diffing and historical tracking. Treat CISA official feed as source of truth.
6. **VulnCheck KEV**
   * Link(s): vulncheck.com/kev (https: / / vulncheck. com/ kev)
   * Access / Cost: Commercial; limited public info may exist
   * Relevance: Expanded KEV-like exploitation intelligence.
   * Notes: Not identical to CISA KEV. Validate definitions, coverage, licensing, and freshness.
7. **Shadowserver reports**
   * Link(s): www.shadowserver.org (https: / / www. shadowserver. org/ )
   * Access / Cost: Free for eligible organizations; access/registration may be required
   * Relevance: Internet-scale exploitation and exposure observations.
   * Notes: Useful for exposure/scan telemetry. Data may be aggregated and require access setup.
8. **GreyNoise Visualizer**
   * Link(s): viz.greynoise.io (https: / / viz. greynoise. io/ )
   * Access / Cost: Free tier / paid plans
   * Relevance: Internet scanning/exploitation noise and actor context.
   * Notes: Helps distinguish benign scanning, mass exploitation, and opportunistic activity.
9. **GreyNoise API docs**
   * Link(s): docs.greynoise.io (https: / / docs. greynoise. io/ )
   * Access / Cost: Free tier / paid plans; API key required
   * Relevance: API for IP-based exploitation telemetry enrichment.
   * Notes: API terms, quotas, and plan level can affect automation.

### 3.2 Exploit prediction & scoring

1. **FIRST EPSS overview**
   * Link(s): www.first.org/epss (https: / / www. first. org/ epss/ )
   * Access / Cost: Free public / open data
   * Relevance: Exploit Prediction Scoring System. Provides probability-style exploit-likelihood signals.
   * Notes: EPSS predicts exploitation probability, not impact. Use with CVSS, KEV, exposure, and asset criticality.
2. **FIRST EPSS API**
   * Link(s): www.first.org/epss/api (https: / / www. first. org/ epss/ api)
   * Access / Cost: Free public API
   * Relevance: API endpoint for EPSS scores.
   * Notes: Useful for daily enrichment. Store score date because EPSS changes over time.
3. **FIRST EPSS data & CSV downloads**
   * Link(s): www.first.org/epss/data\_stats (https: / / www. first. org/ epss/ data\_ stats)
   * Access / Cost: Free public data downloads
   * Relevance: Current and historical EPSS CSV data reference.
   * Notes: Historical scores are useful for model training and retrospective analysis.
4. **Historical EPSS scores GitHub**
   * Link(s): github.com/empiricalsec/epss\_scores (https: / / github. com/ empiricalsec/ epss\_ scores)
   * Access / Cost: Free public GitHub repo
   * Relevance: Daily historical EPSS snapshots.
   * Notes: Useful for longitudinal training labels. Validate against FIRST releases.
5. **FIRST CVSS**
   * Link(s): www.first.org/cvss (https: / / www. first. org/ cvss/ )
   * Access / Cost: Free public
   * Relevance: Official CVSS specification home.
   * Notes: CVSS severity must not be treated as exploit likelihood.
6. **FIRST CVSS v4.0**
   * Link(s): www.first.org/cvss/v4.0/specification-document (https: / / www. first. org/ cvss/ v4. 0/ specification- document)
   * Access / Cost: Free public
   * Relevance: CVSS v4.0 specification.
   * Notes: Newer scoring semantics may not be universally populated across vulnerability records yet.
7. **FIRST CVSS v3.1**
   * Link(s): www.first.org/cvss/v3.1/specification-document (https: / / www. first. org/ cvss/ v3. 1/ specification- document)
   * Access / Cost: Free public
   * Relevance: CVSS v3.1 specification.
   * Notes: Still widely used across CVE/NVD/vendor data.
8. **NVD CVSS resources**
   * Link(s): nvd.nist.gov/vuln-metrics/cvss (https: / / nvd. nist. gov/ vuln- metrics/ cvss)
   * Access / Cost: Free public
   * Relevance: CVSS calculators and vector references.
   * Notes: Useful for parsing and validating NVD scoring data.

### 3.3 Decision-support frameworks

1. **CISA SSVC**
   * Link(s): www.cisa.gov/stakeholder-specific-vulnerability-categorization-ssvc (https: / / www. cisa. gov/ stakeholder- specific- vulnerability- categorization- ssvc)
   * Access / Cost: Free public
   * Relevance: Stakeholder-Specific Vulnerability Categorization for vulnerability response decisions.
   * Notes: Useful for decision automation beyond raw severity. Depends on environmental and mission context.
2. **CERT/CC SSVC project**
   * Link(s): github.com/CERTCC/SSVC (https: / / github. com/ CERTCC/ SSVC)
   * Access / Cost: Free / open-source public GitHub repo
   * Relevance: SSVC model artifacts, examples, and discussions.
   * Notes: Useful for implementing SSVC decision trees and decision points.
3. **CISA Vulnrichment**
   * Link(s): github.com/cisagov/vulnrichment (https: / / github. com/ cisagov/ vulnrichment)
   * Access / Cost: Free / open-source public GitHub repo
   * Relevance: CISA ADP enrichment and SSVC decision points.
   * Notes: Coverage is not universal. Preserve missing/null state distinctly from "low risk."
4. **CISA Binding Operational Directive 22-01**
   * Link(s): www.cisa.gov/news-events/directives/bod-22-01-reducing-significant-risk-known-exploited-vulnerabilities (https: / / www. cisa. gov/ news- events/ directives/ bod- 22- 01- reducing- significant- risk- known- exploited- vulnerabilities)
   * Access / Cost: Free public
   * Relevance: Operational requirement context for KEV remediation.
   * Notes: Primarily binding for U.S. federal civilian agencies but useful as industry prioritization guidance.
5. **CISA Cybersecurity Advisories**
   * Link(s): www.cisa.gov/cybersecurity-advisories (https: / / www. cisa. gov/ cybersecurity- advisories)
   * Access / Cost: Free public
   * Relevance: Broader CISA advisory feed.
   * Notes: Useful for emergent campaigns, vendor alerts, and remediation guidance.
6. **CISA Alerts**
   * Link(s): www.cisa.gov/news-events/cybersecurity-advisories (https: / / www. cisa. gov/ news- events/ cybersecurity- advisories)
   * Access / Cost: Free public
   * Relevance: CISA alert/advisory listing.
   * Notes: May overlap with other CISA pages. Deduplicate by advisory ID/date.

### 3.4 Public exploit / proof-of-concept / weaponization signals

1. **Exploit-DB**
   * Link(s): www.exploit-db.com (https: / / www. exploit- db. com/ )
   * Access / Cost: Free public
   * Relevance: Public exploit archive. Strong signal for PoC availability.
   * Notes: Public PoC does not always mean reliable weaponization; verify exploit quality and target version.
2. **SearchSploit**
   * Link(s): www.exploit-db.com/searchsploit (https: / / www. exploit- db. com/ searchsploit)
   * Access / Cost: Free / open-source tool
   * Relevance: CLI interface for Exploit-DB.
   * Notes: Useful for local workflows and offline search.
3. **Exploit-DB GitLab mirror**
   * Link(s): gitlab.com/exploit-database/exploitdb (https: / / gitlab. com/ exploit- database/ exploitdb)
   * Access / Cost: Free public GitLab repo
   * Relevance: Git mirror of Exploit-DB content.
   * Notes: Useful for local indexing and diffing.
4. **Metasploit Framework**
   * Link(s): github.com/rapid7/metasploit-framework (https: / / github. com/ rapid7/ metasploit- framework)
   * Access / Cost: Free / open-source public GitHub repo; commercial Rapid7 products separate
   * Relevance: Exploit framework containing modules, payloads, and auxiliary checks.
   * Notes: A Metasploit module is a stronger operationalization signal than a bare PoC.
5. **Metasploit exploit modules**
   * Link(s): github.com/rapid7/metasploit-framework/tree/master/modules/exploits (https: / / github. com/ rapid7/ metasploit- framework/ tree/ master/ modules/ exploits)
   * Access / Cost: Free / open-source public GitHub repo
   * Relevance: Practical signal that a vulnerability has weaponized exploit implementation.
   * Notes: Module maturity, reliability, and target coverage vary.
6. **Packet Storm Security exploits**
   * Link(s): packetstormsecurity.com/files/tags/exploit/ (https: / / packetstormsecurit y. com/ files/ tags/ exploit/ )
   * Access / Cost: Free public
   * Relevance: Public exploit and advisory archive.
   * Notes: Quality and metadata normalization vary; cross-reference CVE IDs.
7. **0day.today**
   * Link(s): 0day.today (https: / / 0day. today/ )
   * Access / Cost: Mixed; some access may require account/payment
   * Relevance: Public zero-day/exploit listing.
   * Notes: Use carefully. Legal, provenance, accuracy, and quality may vary substantially.
8. **Project Zero blog**
   * Link(s): googleprojectzero.blogspot.com (https: / / googleprojectzero. blogspot. com/ )
   * Access / Cost: Free public
   * Relevance: High-quality root-cause and exploitation writeups.
   * Notes: Excellent for model features around exploitability primitives and bug classes.
9. **Project Zero issue tracker - current**
   * Link(s): project-zero.issues.chromium.org (https: / / project- zero. issues. chromium. org/ )
   * Access / Cost: Free public; some issue details may be restricted before disclosure
   * Relevance: Current Project Zero issue tracker.
   * Notes: Good for disclosure timelines and technical details.
10. **Project Zero issue tracker - old/historical**
    * Link(s): bugs.chromium.org/p/project-zero/issues/list (https: / / bugs. chromium. org/ p/ project- zero/ issues/ list)
    * Access / Cost: Free public historical access where still available
    * Relevance: Historical Project Zero issue tracker link.
    * Notes: Keep for old references; prefer current tracker when available.
11. **CERT/CC Vulnerability Notes Database**
    * Link(s): www.kb.cert.org/vuls (https: / / www. kb. cert. org/ vuls/ )
    * Access / Cost: Free public
    * Relevance: Coordinated disclosure context, affected vendors, technical notes, and remediation.
    * Notes: Often useful when multiple vendors/products are affected.
12. **CERT/CC VINCE public notes**
    * Link(s): kb.cert.org/vuls/html (https: / / kb. cert. org/ vuls/ html/ )
    * Access / Cost: Free public
    * Relevance: Modern public vulnerability note interface.
    * Notes: Good for public vulnerability notes and coordination context.
13. **Rapid7 AttackerKB**
    * Link(s): attackerkb.com (https: / / attackerkb. com/ )
    * Access / Cost: Free public content; some Rapid7 ecosystem features may be commercial
    * Relevance: Exploitability and attacker-value context.
    * Notes: Community/commercial signals should be weighted with provenance and recency.
14. **Nuclei templates**
    * Link(s): github.com/projectdiscovery/nuclei-templates (https: / / github. com/ projectdiscovery/ nuclei- templates)
    * Access / Cost: Free / open-source public GitHub repo
    * Relevance: Exposed-condition detection templates. Useful for scanning internet-facing assets.
    * Notes: Template presence is a practical detection signal, not proof of vulnerability unless executed correctly.
15. **ProjectDiscovery Nuclei**
    * Link(s): github.com/projectdiscovery/nuclei (https: / / github. com/ projectdiscovery/ nuclei)
    * Access / Cost: Free / open-source public GitHub repo; commercial ProjectDiscovery offerings separate
    * Relevance: Template-based vulnerability and exposure scanner.
    * Notes: Detection accuracy depends on template quality, target context, and scanner configuration.
16. **Horizon3.ai research**
    * Link(s): www.horizon3.ai/attack-research (https: / / www. horizon3. ai/ attack- research/ )
    * Access / Cost: Free public research; commercial products separate
    * Relevance: PoC and attack-path writeups.
    * Notes: Useful for exploitability context and reproduction details.
17. **watchTowr Labs**
    * Link(s): labs.watchtowr.com (https: / / labs. watchtowr. com/ )
    * Access / Cost: Free public research; commercial services separate
    * Relevance: Vulnerability research and exploitation details.
    * Notes: Research source; verify exact affected versions and mitigations.
18. **Assetnote research**
    * Link(s): www.assetnote.io/resources/research (https: / / www. assetnote. io/ resources/ research)
    * Access / Cost: Free public research; commercial services separate
    * Relevance: Exploit research and vulnerability detection signatures.
    * Notes: Useful for detection engineering and exposed attack surface context.

## 4. CWE, CAPEC, ATT\&CK, ATLAS & weakness-to-attack mapping

### 4.1 CWE - Common Weakness Enumeration

1. **CWE home**
   * Link(s): cwe.mitre.org (https: / / cwe. mitre. org/ )
   * Access / Cost: Free public
   * Relevance: Common Weakness Enumeration root. Provides standardized weakness taxonomy.
   * Notes: CVE-to-CWE mappings are sometimes missing, broad, or imprecise.
2. **CWE downloads**
   * Link(s): cwe.mitre.org/data/downloads.html (https: / / cwe. mitre. org/ data/ downloads. html)
   * Access / Cost: Free public downloads
   * Relevance: XML, CSV, archive bundles, and views for machine ingestion.
   * Notes: Use downloadable structured data for robust taxonomy ingestion.
3. **CWE latest PDF**
   * Link(s): cwe.mitre.org/data/published/cwe\_latest.pdf (https: / / cwe. mitre. org/ data/ published/ cwe\_ latest. pdf)
   * Access / Cost: Free public PDF
   * Relevance: PDF publication of latest CWE content.
   * Notes: Better for manual reference than automated ingestion.
4. **CWE reports**
   * Link(s): cwe.mitre.org/data/reports.html (https: / / cwe. mitre. org/ data/ reports. html)
   * Access / Cost: Free public
   * Relevance: Reports and curated views of CWE data.
   * Notes: Useful for understanding categories, views, and prioritization.
5. **CWE chains & composites**
   * Link(s): cwe.mitre.org/data/reports/chains\_and\_composites.html (https: / / cwe. mitre. org/ data/ reports/ chains\_ and\_ composites. html)
   * Access / Cost: Free public
   * Relevance: Describes weakness chains and composite weaknesses.
   * Notes: Important for modeling multi-step root causes and compound vulnerabilities.
6. **CWE schema docs**
   * Link(s): cwe.mitre.org/documents/schema/index.html (https: / / cwe. mitre. org/ documents/ schema/ index. html)
   * Access / Cost: Free public
   * Relevance: Schema documentation for CWE data.
   * Notes: Use for parser validation and taxonomy consistency.
7. **CWE data definitions**
   * Link(s): cwe.mitre.org/data/definitions/1000.html (https: / / cwe. mitre. org/ data/ definitions/ 1000. html)
   * Access / Cost: Free public
   * Relevance: CWE views and weakness hierarchy.
   * Notes: Useful for grouping weaknesses into higher-level categories.
8. **CWE Top 25**
   * Link(s): cwe.mitre.org/top25 (https: / / cwe. mitre. org/ top25/ )
   * Access / Cost: Free public
   * Relevance: Most dangerous software weaknesses.
   * Notes: Good for model priors and training labels, but not a substitute for context-specific risk.
9. **CWE AI/ML category - CWE-1448**
   * Link(s): cwe.mitre.org/data/definitions/1448.html (https: / / cwe. mitre. org/ data/ definitions/ 1448. html)
   * Access / Cost: Free public
   * Relevance: AI/ML-related weakness category.
   * Notes: Emerging taxonomy area; expect coverage to evolve.
10. **CWE AI Working Group**
    * Link(s): cwe.mitre.org/community/working\_groups.html (https: / / cwe. mitre. org/ community/ working\_ groups. html)
    * Access / Cost: Free public
    * Relevance: CWE/CVE AI Working Group context.
    * Notes: Useful for tracking evolution of AI-related weakness classifications.

### 4.2 CAPEC - attack patterns

1. **CAPEC home**
   * Link(s): capec.mitre.org (https: / / capec. mitre. org/ )
   * Access / Cost: Free public
   * Relevance: Catalog of attack patterns used to exploit weaknesses.
   * Notes: CAPEC bridges weakness taxonomy and attacker behavior patterns.
2. **CAPEC downloads**
   * Link(s): capec.mitre.org/data/downloads.html (https: / / capec. mitre. org/ data/ downloads. html)
   * Access / Cost: Free public downloads
   * Relevance: XML/CSV attack-pattern bundles.
   * Notes: Prefer structured downloads for ingestion.
3. **CAPEC schema docs**
   * Link(s): capec.mitre.org/documents/schema/index.html (https: / / capec. mitre. org/ documents/ schema/ index. html)
   * Access / Cost: Free public
   * Relevance: Schema docs for CAPEC data.
   * Notes: Important for parser validation.
4. **CAPEC data index**
   * Link(s): capec.mitre.org/data/index.html (https: / / capec. mitre. org/ data/ index. html)
   * Access / Cost: Free public
   * Relevance: Browsable CAPEC entries and views.
   * Notes: Useful for manual mapping and explanation.
5. **MITRE CTI repository - ATT\&CK & CAPEC in STIX**
   * Link(s): github.com/mitre/cti (https: / / github. com/ mitre/ cti)
   * Access / Cost: Free / open-source public GitHub repo
   * Relevance: MITRE ATT\&CK and CAPEC datasets expressed in STIX 2.0.
   * Notes: Useful for graph-based relationships. May differ from newer ATT\&CK-specific STIX repo content.

### 4.3 MITRE ATT\&CK

1. **ATT\&CK Enterprise Matrix**
   * Link(s): attack.mitre.org/matrices/enterprise (https: / / attack. mitre. org/ matrices/ enterprise/ )
   * Access / Cost: Free public
   * Relevance: Enterprise adversary tactics and techniques.
   * Notes: More relevant for adversary behavior after exploitation than raw CVE severity.
2. **ATT\&CK Matrices**
   * Link(s): attack.mitre.org/matrices (https: / / attack. mitre. org/ matrices/ )
   * Access / Cost: Free public
   * Relevance: ATT\&CK matrices across domains.
   * Notes: Useful for selecting enterprise, mobile, ICS, or other domain views.
3. **ATT\&CK Data & Tools**
   * Link(s): attack.mitre.org/resources/attack-data-and-tools (https: / / attack. mitre. org/ resources/ attack- data- and- tools/ )
   * Access / Cost: Free public
   * Relevance: ATT\&CK Navigator, STIX/TAXII, Workbench, and tooling references.
   * Notes: Prefer machine-readable STIX/TAXII for ingestion.
4. **ATT\&CK STIX data repo**
   * Link(s): github.com/mitre-attack/attack-stix-data (https: / / github. com/ mitre- attack/ attack- stix- data)
   * Access / Cost: Free / open-source public GitHub repo
   * Relevance: Machine-readable ATT\&CK STIX data.
   * Notes: Best source for automated technique/tactic ingestion.
5. **MITRE CTI repository**
   * Link(s): github.com/mitre/cti (https: / / github. com/ mitre/ cti)
   * Access / Cost: Free / open-source public GitHub repo
   * Relevance: MITRE CTI STIX datasets.
   * Notes: Keep for historical/related STIX content.
6. **ATT\&CK Navigator**
   * Link(s): mitre-attack.github.io/attack-navigator (https: / / mitre- attack. github. io/ attack- navigator/ )
   * Access / Cost: Free / open-source web tool
   * Relevance: Visual mapping of techniques to campaigns, risks, or controls.
   * Notes: Useful for reporting and matrix visualization, not raw vuln ingestion.
7. **ATT\&CK Workbench**
   * Link(s): github.com/center-for-threat-informed-defense/attack-workbench-frontend (https: / / github. com/ center- for- threat- informed- defense/ attack- workbench- frontend)
   * Access / Cost: Free / open-source public GitHub repo
   * Relevance: Tooling for ATT\&CK customization and management.
   * Notes: Useful for internal technique mapping workflows.
8. **ATT\&CK TAXII server docs**
   * Link(s): attack.mitre.org/resources/attack-data-and-tools (https: / / attack. mitre. org/ resources/ attack- data- and- tools/ )
   * Access / Cost: Free public
   * Relevance: TAXII/STIX access docs.
   * Notes: Same source as ATT\&CK Data & Tools; retained to preserve the explicit TAXII reference.

### 4.4 AI/ML-specific adversary frameworks

1. **MITRE ATLAS**
   * Link(s): atlas.mitre.org (https: / / atlas. mitre. org/ )
   * Access / Cost: Free public
   * Relevance: Living knowledge base of adversary tactics and techniques against AI-enabled systems.
   * Notes: More directly relevant to AI systems than ATT\&CK Enterprise alone.
2. **MITRE ATLAS matrix**
   * Link(s): atlas.mitre.org/matrices/ATLAS (https: / / atlas. mitre. org/ matrices/ ATLAS)
   * Access / Cost: Free public
   * Relevance: Matrix view of AI adversary tactics and techniques.
   * Notes: Useful for AI threat modeling and impact mapping.
3. **MITRE ATLAS techniques**
   * Link(s): atlas.mitre.org/techniques (https: / / atlas. mitre. org/ techniques)
   * Access / Cost: Free public
   * Relevance: Technique-level ATLAS entries.
   * Notes: Use for structured AI attack technique mapping.
4. **MITRE ATLAS case studies**
   * Link(s): atlas.mitre.org/studies (https: / / atlas. mitre. org/ studies)
   * Access / Cost: Free public
   * Relevance: Case studies of AI attacks and failures.
   * Notes: Helpful for real-world analogs and model training examples.
5. **MITRE ATLAS GitHub / Adversarial ML Threat Matrix**
   * Link(s): github.com/mitre/advmlthreatmatrix (https: / / github. com/ mitre/ advmlthreatmatrix)
   * Access / Cost: Free / open-source public GitHub repo
   * Relevance: Historical and structured project data for adversarial ML threat matrix.
   * Notes: May not be the most current ATLAS view; keep for lineage.
6. **MITRE SAFE-AI report**
   * Link(s): atlas.mitre.org/pdf-files/SAFEAI\_Full\_Report.pdf (https: / / atlas. mitre. org/ pdf- files/ SAFEAI\_ Full\_ Report. pdf)
   * Access / Cost: Free public PDF
   * Relevance: AI system risk mapping across model, data, platform, and environment layers.
   * Notes: Useful for AI-specific control mapping and architecture risk analysis.
7. **OWASP Top 10 for LLM Applications**
   * Link(s): owasp.org/www-project-top-10-for-large-language-model-applications (https: / / owasp. org/ www- project- top- 10- for- large- language- model- applications/ )
   * Access / Cost: Free / open-source community project
   * Relevance: Practical LLM application vulnerability taxonomy.
   * Notes: Useful for AI appsec detection categories beyond CVE.
8. **OWASP Top 10 for Machine Learning Security**
   * Link(s): owasp.org/www-project-machine-learning-security-top-10 (https: / / owasp. org/ www- project- machine- learning- security- top- 10/ )
   * Access / Cost: Free / open-source community project
   * Relevance: ML-specific application/security risk taxonomy.
   * Notes: Complements ATLAS with appsec-oriented framing.
9. **OWASP AI Exchange**
   * Link(s): owaspai.org (https: / / owaspai. org/ )
   * Access / Cost: Free public community resource
   * Relevance: AI security risks, controls, and threat modeling references.
   * Notes: Useful for governance and risk mapping.
10. **NIST AI Risk Management Framework**
    * Link(s): www.nist.gov/itl/ai-risk-management-framework (https: / / www. nist. gov/ itl/ ai- risk- management- framework)
    * Access / Cost: Free public
    * Relevance: AI risk management framework.
    * Notes: Useful for risk controls, governance, and impact framing.
11. **NIST AI RMF 1.0 PDF**
    * Link(s): nvlpubs.nist.gov/nistpubs/ai/NIST.AI.100-1.pdf (https: / / nvlpubs. nist. gov/ nistpubs/ ai/ NIST. AI. 100- 1. pdf)
    * Access / Cost: Free public PDF
    * Relevance: AI RMF 1.0 document.
    * Notes: PDF reference; not a vulnerability feed.
12. **NIST AI 600-1 - Generative AI Profile**
    * Link(s): www.nist.gov/publications/artificial-intelligence-risk-management-framework-generative-artificial-intelligence (https: / / www. nist. gov/ publications/ artificial- intelligence- risk- management- framework- generative- artificial- intelligence)
    * Access / Cost: Free public
    * Relevance: GenAI risk profile companion to AI RMF.
    * Notes: Useful for LLM/generative AI-specific risk categories.
13. **NIST adversarial machine learning taxonomy**
    * Link(s): www.nist.gov/publications/adversarial-machine-learning-taxonomy-and-terminology-attacks-and-mitigations (https: / / www. nist. gov/ publications/ adversarial- machine- learning- taxonomy- and- terminology- attacks- and- mitigations)
    * Access / Cost: Free public
    * Relevance: Taxonomy and terminology for adversarial ML attacks and mitigations.
    * Notes: Good for consistent AI vulnerability vocabulary.
14. **MLCommons AI Safety**
    * Link(s): mlcommons.org/working-groups/ai-safety (https: / / mlcommons. org/ working- groups/ ai- safety/ )
    * Access / Cost: Free public community resource
    * Relevance: AI safety benchmarks and working group context.
    * Notes: Useful for AI system risk evaluation, not direct CVE matching.

## 5. Vendor, OS, distribution, container & package affectedness feeds

### 5.1 Scanner-oriented aggregators & vulnerability DB builders

1. **NeuVector vul-dbgen**
   * Link(s): github.com/neuvector/vul-dbgen (https: / / github. com/ neuvector/ vul- dbgen)
   * Access / Cost: Free / open-source public GitHub repo
   * Relevance: Vulnerability DB generation source originally flagged by this project.
   * Notes: Useful as a reference for aggregating distro/package vulnerability feeds.
2. **NeuVector vul-source**
   * Link(s): github.com/neuvector/vul-source (https: / / github. com/ neuvector/ vul- source)
   * Access / Cost: Free / open-source public GitHub repo
   * Relevance: Vulnerability source data used by NeuVector workflows.
   * Notes: Review for source coverage and feed normalization logic.
3. **Aqua Trivy vulnerability docs**
   * Link(s): trivy.dev/docs/latest/scanner/vulnerability (https: / / trivy. dev/ docs/ latest/ scanner/ vulnerability/ )
   * Access / Cost: Free public docs
   * Relevance: Scanner behavior across OS packages, language packages, misconfig, Kubernetes, etc.
   * Notes: Useful for scanner semantics and supported target types.
4. **Trivy DB**
   * Link(s): github.com/aquasecurity/trivy-db (https: / / github. com/ aquasecurity/ trivy- db)
   * Access / Cost: Free / open-source public GitHub repo
   * Relevance: Converts raw advisories into Trivy DB format.
   * Notes: Useful for ingestion architecture and feed normalization patterns.
5. **Trivy Java DB**
   * Link(s): github.com/aquasecurity/trivy-java-db (https: / / github. com/ aquasecurity/ trivy- java- db)
   * Access / Cost: Free / open-source public GitHub repo
   * Relevance: Java-specific vulnerability database used by Trivy.
   * Notes: Useful for Maven/JAR matching.
6. **Trivy database configuration docs**
   * Link(s): trivy.dev/docs/latest/configuration/db (https: / / trivy. dev/ docs/ latest/ configuration/ db/ )
   * Access / Cost: Free public docs
   * Relevance: Documents Trivy DB artifacts and configuration.
   * Notes: Useful for operational scanner deployment.
7. **Anchore Grype**
   * Link(s): github.com/anchore/grype (https: / / github. com/ anchore/ grype)
   * Access / Cost: Free / open-source public GitHub repo
   * Relevance: Vulnerability scanner for container images and filesystems.
   * Notes: Useful reference for SBOM-to-vuln matching.
8. **Anchore Grype DB**
   * Link(s): github.com/anchore/grype-db (https: / / github. com/ anchore/ grype- db)
   * Access / Cost: Free / open-source public GitHub repo
   * Relevance: Builds Grype vulnerability database from upstream sources.
   * Notes: Useful for feed normalization and source coverage comparison.
9. **Anchore Syft**
   * Link(s): github.com/anchore/syft (https: / / github. com/ anchore/ syft)
   * Access / Cost: Free / open-source public GitHub repo
   * Relevance: SBOM generation for scanning and exposure matching.
   * Notes: Pair with Grype for inventory-to-vulnerability workflow.
10. **Quay ClairCore**
    * Link(s): github.com/quay/claircore (https: / / github. com/ quay/ claircore)
    * Access / Cost: Free / open-source public GitHub repo
    * Relevance: Clair vulnerability matching engine core.
    * Notes: Useful for container security ingestion patterns.
11. **Clair**
    * Link(s): github.com/quay/clair (https: / / github. com/ quay/ clair)
    * Access / Cost: Free / open-source public GitHub repo
    * Relevance: Container vulnerability scanner.
    * Notes: Compare feed matching behavior with Trivy and Grype.
12. **VulnerableCode**
    * Link(s): github.com/nexB/vulnerablecode (https: / / github. com/ nexB/ vulnerablecode)
    * Access / Cost: Free / open-source public GitHub repo
    * Relevance: Open vulnerability DB aggregator.
    * Notes: Useful for importer coverage and open-source ingestion architecture.
13. **VulnerableCode importer docs**
    * Link(s): vulnerablecode.readthedocs.io/en/latest/importers\_link.html (https: / / vulnerablecode. readthedocs. io/ en/ latest/ importers\_ link. html)
    * Access / Cost: Free public docs
    * Relevance: Lists supported importer sources.
    * Notes: Good checklist for source coverage.
14. **Dependency-Track**
    * Link(s): dependencytrack.org (https: / / dependencytrack. org/ )
    * Access / Cost: Free / open-source core project
    * Relevance: SBOM-oriented vulnerability management platform.
    * Notes: Useful reference for BOM ingestion and component risk tracking.
15. **Dependency-Track data sources**
    * Link(s): docs.dependencytrack.org/datasources/overview (https: / / docs. dependencytrack. org/ datasources/ overview/ )
    * Access / Cost: Free public docs
    * Relevance: Documents Dependency-Track data sources.
    * Notes: Useful for comparing source prioritization.
16. **Dependency-Track GitHub Advisories datasource**
    * Link(s): docs.dependencytrack.org/datasources/github-advisories (https: / / docs. dependencytrack. org/ datasources/ github- advisories/ )
    * Access / Cost: Free public docs
    * Relevance: Mirrors GHSA via GitHub public GraphQL API.
    * Notes: Useful reference for GHSA ingestion.
17. **OpenVAS / Greenbone Community Feed**
    * Link(s): www.greenbone.net/en/community-feed (https: / / www. greenbone. net/ en/ community- feed/ )
    * Access / Cost: Free community feed; commercial Greenbone feeds/products available
    * Relevance: Network vulnerability test feed.
    * Notes: Useful for host/network exposure detection, not package-only matching.
18. **Wazuh vulnerability detector**
    * Link(s): documentation.wazuh.com/current/user-manual/capabilities/vulnerability-detection/index.html (https: / / documentation. wazuh. com/ current/ user- manual/ capabilities/ vulnerability- detection/ index. html)
    * Access / Cost: Free public docs; Wazuh open-source, commercial support available
    * Relevance: Endpoint vulnerability detection capability.
    * Notes: Useful for host-level package inventory and vuln matching behavior.

### 5.2 Red Hat / RHEL / CentOS Stream

1. **Red Hat Security Data**
   * Link(s): access.redhat.com/security/data (https: / / access. redhat. com/ security/ data)
   * Access / Cost: Free public data; some product details/support content may require subscription
   * Relevance: Red Hat CSAF/VEX, OSV, OVAL, CVE data.
   * Notes: Essential for RHEL affectedness and backport-aware status.
2. **Red Hat Security Data API**
   * Link(s): docs.redhat.com/en/documentation/red\_hat\_security\_data\_api/1.0/html-single/red\_hat\_security\_data\_api/index (https: / / docs. redhat. com/ en/ documentation/ red\_ hat\_ security\_ data\_ api/ 1.0/ html- single/ red\_ hat\_ security\_ data\_ api/ index)
   * Access / Cost: Free public docs/API; support content may require subscription
   * Relevance: API retrieves Red Hat CVE/advisory/security data.
   * Notes: Prefer API for automation; handle auth/rate constraints if applicable.
3. **Red Hat CVE database**
   * Link(s): access.redhat.com/security/security-updates/#/cve (https: / / access. redhat. com/ security/ security- updates/ # / cve)
   * Access / Cost: Free public
   * Relevance: Red Hat CVE lookup.
   * Notes: Human-facing; use data APIs for automation.
4. **Red Hat OVAL data**
   * Link(s): www.redhat.com/security/data/oval (https: / / www. redhat. com/ security/ data/ oval/ )
   * Access / Cost: Free public
   * Relevance: OVAL definitions for vulnerability assessment.
   * Notes: Useful for scanner compatibility and package-state evaluation.
5. **Red Hat CSAF/VEX guidance**
   * Link(s): redhatproductsecurity.github.io/security-data-guidelines/csaf-vex (https: / / redhatproductsecur ity. github. io/ security- data- guidelines/ csaf- vex/ )
   * Access / Cost: Free public docs
   * Relevance: Explains Red Hat CSAF/VEX and product/package semantics.
   * Notes: Important for correct interpretation of affected/not-affected states.
6. **Red Hat security advisories**
   * Link(s): access.redhat.com/security/security-updates/#/security-advisories (https: / / access. redhat. com/ security/ security- updates/ # / security- advisories)
   * Access / Cost: Free public listing; some product support details may require subscription
   * Relevance: Red Hat advisory listing.
   * Notes: Useful for patch/remediation references.
7. **CentOS Stream security tracker**
   * Link(s): gitlab.com/redhat/centos-stream/rpms (https: / / gitlab. com/ redhat/ centos- stream/ rpms)
   * Access / Cost: Free public GitLab
   * Relevance: CentOS Stream package source context.
   * Notes: Use carefully; package repo state differs from security advisory truth.

### 5.3 Debian

1. **Debian Security Tracker**
   * Link(s): security-tracker.debian.org (https: / / security- tracker. debian. org/ )
   * Access / Cost: Free public
   * Relevance: Debian-specific package vulnerability status.
   * Notes: Essential for Debian affectedness and backported patches.
2. **Debian Security Tracker JSON**
   * Link(s): security-tracker.debian.org/tracker/data/json (https: / / security- tracker. debian. org/ tracker/ data/ json)
   * Access / Cost: Free public JSON
   * Relevance: Machine-readable Debian vulnerability data.
   * Notes: Primary automation source for Debian.
3. **Debian Security Tracker source Git**
   * Link(s): salsa.debian.org/security-tracker-team/security-tracker (https: / / salsa. debian. org/ security- tracker- team/ security- tracker)
   * Access / Cost: Free / open-source public Git repo
   * Relevance: Source repo for tracker data.
   * Notes: Useful for diffs, auditing, and local mirroring.
4. **Debian Security Information**
   * Link(s): www.debian.org/security (https: / / www. debian. org/ security/ )
   * Access / Cost: Free public
   * Relevance: Debian security notices and process context.
   * Notes: Useful for advisory references and manual review.
5. **Debian Security Tracker docs**
   * Link(s): security-team.debian.org/security\_tracker.html (https: / / security- team. debian. org/ security\_ tracker. html)
   * Access / Cost: Free public docs
   * Relevance: Explains Debian tracker semantics.
   * Notes: Important for interpreting statuses like fixed, vulnerable, ignored, or postponed.
6. **Debian OVAL**
   * Link(s): www.debian.org/security/oval (https: / / www. debian. org/ security/ oval/ )
   * Access / Cost: Free public
   * Relevance: OVAL data for Debian vulnerability assessment.
   * Notes: Useful for scanner integrations.

### 5.4 Ubuntu / Canonical

1. **Ubuntu Security Notices**
   * Link(s): ubuntu.com/security/notices (https: / / ubuntu. com/ security/ notices)
   * Access / Cost: Free public
   * Relevance: Ubuntu security notices for fixed packages.
   * Notes: Useful for patch references and release-specific remediation.
2. **Ubuntu CVE reports**
   * Link(s): ubuntu.com/security/cves (https: / / ubuntu. com/ security/ cves)
   * Access / Cost: Free public
   * Relevance: Ubuntu CVE tracking by package/release.
   * Notes: Important for Ubuntu affectedness and backport interpretation.
3. **Ubuntu OVAL**
   * Link(s): ubuntu.com/security/oval (https: / / ubuntu. com/ security/ oval)
   * Access / Cost: Free public
   * Relevance: OVAL data for vulnerability assessment and patch status.
   * Notes: Useful for scanner compatibility.
4. **Ubuntu VEX data**
   * Link(s): ubuntu.com/security/vex (https: / / ubuntu. com/ security/ vex)
   * Access / Cost: Free public
   * Relevance: Ubuntu VEX data.
   * Notes: Useful for affected/not-affected status and scanner false-positive reduction.
5. **Ubuntu VEX docs**
   * Link(s): documentation.ubuntu.com/security/security-updates/vex (https: / / documentation. ubuntu. com/ security/ security- updates/ vex/ )
   * Access / Cost: Free public docs
   * Relevance: Ubuntu VEX source documentation.
   * Notes: Important for interpreting Canonical VEX publication model.
6. **Ubuntu Security Notices GitHub**
   * Link(s): github.com/canonical/ubuntu-security-notices (https: / / github. com/ canonical/ ubuntu- security- notices)
   * Access / Cost: Free public GitHub repo
   * Relevance: USN/LSN JSON, OSV JSON, and OpenVEX JSON formats.
   * Notes: Strong automation source. Preserve format-specific semantics.
7. **Ubuntu Security Tracker Git**
   * Link(s): git.launchpad.net/ubuntu-cve-tracker (https: / / git. launchpad. net/ ubuntu- cve- tracker)
   * Access / Cost: Free public Git repo
   * Relevance: Ubuntu CVE tracker source.
   * Notes: Useful for local mirroring and historical diffing.
8. **Ubuntu security updates docs**
   * Link(s): documentation.ubuntu.com/security/security-updates (https: / / documentation. ubuntu. com/ security/ security- updates/ )
   * Access / Cost: Free public docs
   * Relevance: Ubuntu security update documentation.
   * Notes: Useful for process context and VEX/OVAL interpretation.

### 5.5 Alpine

1. **Alpine SecDB**
   * Link(s): secdb.alpinelinux.org (https: / / secdb. alpinelinux. org/ )
   * Access / Cost: Free public
   * Relevance: Current Alpine machine-readable security DB.
   * Notes: Primary Alpine ingestion source.
2. **Alpine Security Tracker**
   * Link(s): security.alpinelinux.org (https: / / security. alpinelinux. org/ )
   * Access / Cost: Free public
   * Relevance: Tracks Alpine security issues.
   * Notes: Useful for human review and status context.
3. **Alpine SecDB deprecated GitHub mirror**
   * Link(s): github.com/alpinelinux/alpine-secdb (https: / / github. com/ alpinelinux/ alpine- secdb)
   * Access / Cost: Free public GitHub repo; deprecated
   * Relevance: Historical Alpine SecDB mirror.
   * Notes: Deprecated; do not rely on it for current ingestion.
4. **Alpine packages**
   * Link(s): pkgs.alpinelinux.org/packages (https: / / pkgs. alpinelinux. org/ packages)
   * Access / Cost: Free public
   * Relevance: Alpine package metadata.
   * Notes: Not a vulnerability DB, but helps resolve package names and versions.

### 5.6 SUSE / openSUSE

1. **SUSE CSAF**
   * Link(s): www.suse.com/support/security/csaf (https: / / www. suse. com/ support/ security/ csaf/ )
   * Access / Cost: Free public
   * Relevance: SUSE CSAF advisory data.
   * Notes: Good for vendor-asserted affectedness and remediation states.
2. **SUSE CVRF / OVAL security data**
   * Link(s): www.suse.com/support/security/oval (https: / / www. suse. com/ support/ security/ oval/ )
   * Access / Cost: Free public
   * Relevance: SUSE OVAL/CVRF security data.
   * Notes: Useful for scanner compatibility and package-state evaluation.
3. **SUSE CVE pages**
   * Link(s): www.suse.com/security/cve (https: / / www. suse. com/ security/ cve/ )
   * Access / Cost: Free public
   * Relevance: SUSE CVE lookup.
   * Notes: Human-facing; use machine-readable feeds when available.
4. **SUSE Security Advisories**
   * Link(s): www.suse.com/support/update/announcement (https: / / www. suse. com/ support/ update/ announcement/ )
   * Access / Cost: Free public
   * Relevance: SUSE security advisory listing.
   * Notes: Useful for remediation and patch references.
5. **openSUSE Security Announce**
   * Link(s): lists.opensuse.org/archives/list/security-announce@lists.opensuse.org (https: / / lists. opensuse. org/ archives/ list/ security- announce@lists. opensuse. org/ )
   * Access / Cost: Free public
   * Relevance: openSUSE security announcement mailing list archive.
   * Notes: Useful for distro-specific disclosure context.

### 5.7 Oracle Linux

1. **Oracle Security Alerts & Critical Patch Updates**
   * Link(s): www.oracle.com/security-alerts (https: / / www. oracle. com/ security- alerts/ )
   * Access / Cost: Free public
   * Relevance: Oracle CPU, Security Alerts, third-party bulletins, and CVE mappings.
   * Notes: Oracle products often require vendor advisory interpretation beyond NVD.
2. **Oracle Linux security data**
   * Link(s): linux.oracle.com/security (https: / / linux. oracle. com/ security/ )
   * Access / Cost: Free public
   * Relevance: Oracle Linux security data.
   * Notes: Useful for Oracle Linux affectedness.
3. **Oracle Linux OVAL**
   * Link(s): linux.oracle.com/security/oval (https: / / linux. oracle. com/ security/ oval/ )
   * Access / Cost: Free public
   * Relevance: Oracle Linux OVAL definitions.
   * Notes: Useful for scanner compatibility.
4. **Oracle Linux errata**
   * Link(s): linux.oracle.com/errata (https: / / linux. oracle. com/ errata/ )
   * Access / Cost: Free public
   * Relevance: Oracle Linux errata.
   * Notes: Use for patch mapping and fixed versions.
5. **Oracle Linux CVE search**
   * Link(s): linux.oracle.com/cve (https: / / linux. oracle. com/ cve/ )
   * Access / Cost: Free public
   * Relevance: Oracle Linux CVE lookup.
   * Notes: Human lookup source; pair with OVAL/errata for automation.

### 5.8 Amazon Linux

1. **Amazon Linux Security Center**
   * Link(s): alas.aws.amazon.com (https: / / alas. aws. amazon. com/ )
   * Access / Cost: Free public
   * Relevance: Amazon Linux security advisory portal.
   * Notes: Important for Amazon Linux package affectedness.
2. **Amazon Linux 2 advisories**
   * Link(s): alas.aws.amazon.com/alas2.html (https: / / alas. aws. amazon. com/ alas2. html)
   * Access / Cost: Free public
   * Relevance: Amazon Linux 2 advisories.
   * Notes: Version-specific advisory stream.
3. **Amazon Linux 2023 advisories**
   * Link(s): alas.aws.amazon.com/AL2023 (https: / / alas. aws. amazon. com/ AL2023/ )
   * Access / Cost: Free public
   * Relevance: Amazon Linux 2023 advisories.
   * Notes: Keep AL2 and AL2023 separate because package baselines differ.
4. **AWS Security Bulletins**
   * Link(s): aws.amazon.com/security/security-bulletins (https: / / aws. amazon. com/ security/ security- bulletins/ )
   * Access / Cost: Free public
   * Relevance: AWS security bulletins for services and platforms.
   * Notes: Cloud-service affectedness may not map cleanly to package versions.

### 5.9 Fedora, AlmaLinux, Rocky, Arch, Gentoo

1. **Fedora security updates**
   * Link(s): bodhi.fedoraproject.org/updates/?type=security (https: / / bodhi. fedoraproject. org/ updates/ ? type= security)
   * Access / Cost: Free public
   * Relevance: Fedora security update advisories.
   * Notes: Useful for Fedora package remediation tracking.
2. **Fedora packages**
   * Link(s): packages.fedoraproject.org (https: / / packages. fedoraproject. org/ )
   * Access / Cost: Free public
   * Relevance: Fedora package metadata.
   * Notes: Not a vulnerability DB, but useful for package identity and version resolution.
3. **AlmaLinux Errata**
   * Link(s): errata.almalinux.org (https: / / errata. almalinux. org/ )
   * Access / Cost: Free public
   * Relevance: AlmaLinux errata and security advisories.
   * Notes: Useful for RHEL-compatible distro assessment.
4. **AlmaLinux OSV data**
   * Link(s): github.com/AlmaLinux/osv-database (https: / / github. com/ AlmaLinux/ osv- database)
   * Access / Cost: Free public GitHub repo
   * Relevance: AlmaLinux OSV-formatted data.
   * Notes: Good for OSV-based pipelines.
5. **Rocky Linux security advisories**
   * Link(s): errata.build.resf.org (https: / / errata. build. resf. org/ )
   * Access / Cost: Free public
   * Relevance: Rocky Linux errata/security advisories.
   * Notes: Useful for RHEL-compatible distro assessment.
6. **Arch Linux Security Tracker**
   * Link(s): security.archlinux.org (https: / / security. archlinux. org/ )
   * Access / Cost: Free public
   * Relevance: Arch Linux security tracker.
   * Notes: Rolling-release semantics differ from fixed-release distros.
7. **Arch Linux security JSON**
   * Link(s): security.archlinux.org/json (https: / / security. archlinux. org/ json)
   * Access / Cost: Free public JSON
   * Relevance: Machine-readable Arch security data.
   * Notes: Useful for automation.
8. **Gentoo GLSA**
   * Link(s): security.gentoo.org/glsa (https: / / security. gentoo. org/ glsa/ )
   * Access / Cost: Free public
   * Relevance: Gentoo Linux Security Advisories.
   * Notes: Useful for Gentoo package affectedness.
9. **Gentoo GLSA XML**
   * Link(s): security.gentoo.org/glsa/feed.rss (https: / / security. gentoo. org/ glsa/ feed. rss)
   * Access / Cost: Free public RSS/XML
   * Relevance: Gentoo GLSA RSS/XML feed.
   * Notes: Useful for feed-based monitoring.

### 5.10 Wolfi / Chainguard

1. **Wolfi OS advisories**
   * Link(s): github.com/wolfi-dev/advisories (https: / / github. com/ wolfi- dev/ advisories)
   * Access / Cost: Free public GitHub repo
   * Relevance: Wolfi OS advisory data.
   * Notes: Important for modern minimal container images.
2. **Wolfi SecDB generator**
   * Link(s): github.com/wolfi-dev/secdb (https: / / github. com/ wolfi- dev/ secdb)
   * Access / Cost: Free / open-source public GitHub repo
   * Relevance: Generates Wolfi security DBs based on Alpine secdb format.
   * Notes: Useful for understanding feed generation semantics.
3. **Wolfi OS feed**
   * Link(s): packages.wolfi.dev/os/security.json (https: / / packages. wolfi. dev/ os/ security. json)
   * Access / Cost: Free public feed
   * Relevance: Wolfi package security feed.
   * Notes: Use this for Wolfi base images.
4. **Chainguard Enterprise feed**
   * Link(s): packages.cgr.dev/chainguard/security.json (https: / / packages. cgr. dev/ chainguard/ security. json)
   * Access / Cost: Publicly reachable feed; may relate to commercial Chainguard product scope
   * Relevance: Chainguard Enterprise package security feed.
   * Notes: Separate from Wolfi OS feed. Confirm entitlement/licensing before commercial redistribution.
5. **Chainguard security advisories docs**
   * Link(s): edu.chainguard.dev/chainguard/chainguard-images/staying-secure/security-advisories/how-chainguard-issues (https: / / edu. chainguard. dev/ chainguard/ chainguard- images/ staying- secure/ security- advisories/ how- chainguard- issues/ )
   * Access / Cost: Free public docs
   * Relevance: Explains Chainguard advisory publication model.
   * Notes: Important for interpreting feed semantics and OSV/secdb transition.
6. **Wolfi vulnerabilities in OSV**
   * Link(s): osv.dev/list?ecosystem=Wolfi (https: / / osv. dev/ list? ecosystem= Wolfi)
   * Access / Cost: Free public
   * Relevance: Wolfi ecosystem records in OSV.
   * Notes: Good for OSV-aligned ingestion.
7. **Chainguard OSV advisory feed context**
   * Link(s): www.chainguard.dev/unchained/chainguard-enhances-security-with-osv-advisory-feed (https: / / www. chainguard. dev/ unchained/ chainguard- enhances- security- with- osv- advisory- feed)
   * Access / Cost: Free public blog
   * Relevance: Context on Chainguard OSV advisory feed.
   * Notes: Blog/context source, not primary feed.

## 6. Vendor advisories for enterprise impact assessment

### 6.1 Major OS, browser & platform vendors

1. **Microsoft Security Update Guide**
   * Link(s): msrc.microsoft.com/update-guide (https: / / msrc. microsoft. com/ update- guide)
   * Access / Cost: Free public
   * Relevance: Microsoft vulnerability advisories, CVEs, affected products, and fixes.
   * Notes: Critical for Windows, Office, Exchange, Azure components, and enterprise Microsoft stack.
2. **Microsoft MSRC blog**
   * Link(s): msrc.microsoft.com/blog (https: / / msrc. microsoft. com/ blog/ )
   * Access / Cost: Free public
   * Relevance: Microsoft security research and advisory context.
   * Notes: Useful for exploitation context and urgent guidance.
3. **Microsoft Security Response Center**
   * Link(s): msrc.microsoft.com (https: / / msrc. microsoft. com/ )
   * Access / Cost: Free public
   * Relevance: Microsoft security response portal.
   * Notes: Entry point for MSRC resources.
4. **Apple Security Releases**
   * Link(s): support.apple.com/en-us/100100 (https: / / support. apple. com/ en- us/ 100100)
   * Access / Cost: Free public
   * Relevance: Apple security release index.
   * Notes: Important for iOS, macOS, Safari, watchOS, tvOS, and ecosystem patch tracking.
5. **Apple security updates**
   * Link(s): support.apple.com/en-us/HT201222 (https: / / support. apple. com/ en- us/ HT201222)
   * Access / Cost: Free public
   * Relevance: Apple security update listing.
   * Notes: Keep with newer Apple security release page for compatibility.
6. **Google Android Security Bulletins**
   * Link(s): source.android.com/docs/security/bulletin (https: / / source. android. com/ docs/ security/ bulletin)
   * Access / Cost: Free public
   * Relevance: Android platform security bulletins.
   * Notes: Device/vendor patch latency may differ from bulletin availability.
7. **Google Chrome Releases**
   * Link(s): chromereleases.googleblog.com (https: / / chromereleases. googleblog. com/ )
   * Access / Cost: Free public
   * Relevance: Chrome release announcements.
   * Notes: Security fixes are often disclosed with delayed details.
8. **Chrome security advisories**
   * Link(s): chromereleases.googleblog.com/search/label/Security (https: / / chromereleases. googleblog. com/ search/ label/ Security)
   * Access / Cost: Free public
   * Relevance: Chrome security-specific release posts.
   * Notes: Good for urgent browser vulnerability tracking.
9. **Chromium issue tracker**
   * Link(s): issues.chromium.org (https: / / issues. chromium. org/ )
   * Access / Cost: Free public for public issues; restricted issues may require access
   * Relevance: Chromium issue tracking.
   * Notes: Security bugs may have restricted visibility until disclosure.
10. **Mozilla Security Advisories**
    * Link(s): www.mozilla.org/en-US/security/advisories (https: / / www. mozilla. org/ en- US/ security/ advisories/ )
    * Access / Cost: Free public
    * Relevance: Mozilla security advisories.
    * Notes: Important for Firefox, Thunderbird, and related products.
11. **Mozilla Foundation Security Advisories**
    * Link(s): www.mozilla.org/en-US/security/known-vulnerabilities (https: / / www. mozilla. org/ en- US/ security/ known- vulnerabilities/ )
    * Access / Cost: Free public
    * Relevance: Mozilla known vulnerabilities index.
    * Notes: Useful for historical advisory lookup.
12. **Google Cloud Security Bulletins**
    * Link(s): cloud.google.com/support/bulletins (https: / / cloud. google. com/ support/ bulletins)
    * Access / Cost: Free public
    * Relevance: Google Cloud service/product security bulletins.
    * Notes: Cloud advisories often require service-specific interpretation.
13. **Kubernetes Security Announcements**
    * Link(s): groups.google.com/g/kubernetes-security-announce (https: / / groups. google. com/ g/ kubernetes- security- announce)
    * Access / Cost: Free public Google Group
    * Relevance: Kubernetes security announcement mailing list.
    * Notes: Authoritative operational alerting channel for Kubernetes CVEs.
14. **Kubernetes official CVE feed**
    * Link(s): kubernetes.io/docs/reference/issues-security/official-cve-feed (https: / / kubernetes. io/ docs/ reference/ issues- security/ official- cve- feed/ )
    * Access / Cost: Free public
    * Relevance: Official Kubernetes CVE feed reference.
    * Notes: Useful for automation and Kubernetes-specific CVE tracking.
15. **Kubernetes security & disclosure**
    * Link(s): kubernetes.io/docs/reference/issues-security/security (https: / / kubernetes. io/ docs/ reference/ issues- security/ security/ )
    * Access / Cost: Free public
    * Relevance: Kubernetes security disclosure process.
    * Notes: Useful for understanding embargo, disclosure, and patch handling.

### 6.2 Enterprise infrastructure vendors

1. **Cisco Security Advisories**
   * Link(s): sec.cloudapps.cisco.com/security/center/publicationListing.x (https: / / sec. cloudapps. cisco. com/ security/ center/ publicationListing . x)
   * Access / Cost: Free public
   * Relevance: Cisco product advisories, affected versions, fixed versions, and workarounds.
   * Notes: Critical for network infrastructure exposure.
2. **VMware / Broadcom Security Advisories**
   * Link(s): support.broadcom.com/web/ecx/security-advisory (https: / / support. broadcom. com/ web/ ecx/ security- advisory)
   * Access / Cost: Free public listing; some support downloads may require entitlement
   * Relevance: VMware/Broadcom security advisories.
   * Notes: Important for virtualization, ESXi, vCenter, and enterprise infrastructure.
3. **Palo Alto Networks Security Advisories**
   * Link(s): security.paloaltonetworks.com (https: / / security. paloaltonetworks. com/ )
   * Access / Cost: Free public
   * Relevance: PAN-OS and Palo Alto product advisories.
   * Notes: Often includes exploited-in-the-wild notes and mitigation guidance.
4. **Fortinet PSIRT Advisories**
   * Link(s): www.fortiguard.com/psirt (https: / / www. fortiguard. com/ psirt)
   * Access / Cost: Free public
   * Relevance: Fortinet product advisories.
   * Notes: Critical for perimeter devices; exploitability can change quickly.
5. **Ivanti Security Advisories**
   * Link(s): www.ivanti.com/resources/v/doc/ivi/2629/0e3e2be1e66d (https: / / www. ivanti. com/ resources/ v/ doc/ ivi/ 2629/ 0e3e2be1e66d)
   * Access / Cost: Free public
   * Relevance: Ivanti security advisories.
   * Notes: Track emergency advisories closely due to recurring exploitation patterns.
6. **Citrix Security Bulletins**
   * Link(s): support.citrix.com/securitybulletins (https: / / support. citrix. com/ securitybulletins)
   * Access / Cost: Free public
   * Relevance: Citrix product security bulletins.
   * Notes: Useful for exposed remote access infrastructure.
7. **F5 Security Advisories**
   * Link(s): my.f5.com/manage/s/solutions?series=Security\_Advisory (https: / / my. f5. com/ manage/ s/ solutions? series= Security\_Advisory)
   * Access / Cost: Free public listing; some support content may require account
   * Relevance: F5 product security advisories.
   * Notes: Product modules/configuration affect exploitability.
8. **Juniper Security Advisories**
   * Link(s): supportportal.juniper.net/s/global-search/%40uri#sort=relevancy\&f:ctype=\[Security%20Advisories] (https: / / supportportal. juniper. net/ s/ global- search/ % 40uri# sort= relevancy& f: ctype= \[Security% 20Advisories])
   * Access / Cost: Free public listing; support portal may require account for some content
   * Relevance: Juniper security advisory listing.
   * Notes: Useful for network infrastructure patching.
9. **Dell Security Advisories**
   * Link(s): www.dell.com/support/security (https: / / www. dell. com/ support/ security)
   * Access / Cost: Free public listing; downloads/support may require entitlement
   * Relevance: Dell product security advisories.
   * Notes: Covers firmware, hardware, drivers, and enterprise products.
10. **HPE Security Bulletins**
    * Link(s): support.hpe.com/hpesc/public/home (https: / / support. hpe. com/ hpesc/ public/ home)
    * Access / Cost: Free public listing; support portal may require account/entitlement
    * Relevance: HPE security bulletins.
    * Notes: May require product filtering and support portal navigation.
11. **Lenovo Product Security Advisories**
    * Link(s): support.lenovo.com/us/en/product\_security/home (https: / / support. lenovo. com/ us/ en/ product\_ security/ home)
    * Access / Cost: Free public
    * Relevance: Lenovo product security advisories.
    * Notes: Useful for firmware and device fleet management.
12. **IBM PSIRT**
    * Link(s): www.ibm.com/support/pages/ibm-psirt (https: / / www. ibm. com/ support/ pages/ ibm- psirt)
    * Access / Cost: Free public listing; some IBM support docs may require entitlement
    * Relevance: IBM product security incident response.
    * Notes: Useful for IBM software/hardware exposure.
13. **SAP Security Notes**
    * Link(s): support.sap.com/en/my-support/knowledge-base/security-notes-news.html (https: / / support. sap. com/ en/ my- support/ knowledge- base/ security- notes- news. html)
    * Access / Cost: SAP support account / subscription often required for full Security Notes
    * Relevance: SAP security notes and patch-day guidance.
    * Notes: May require SAP support access for full note details.
14. **Adobe Security Bulletins**
    * Link(s): helpx.adobe.com/security.html (https: / / helpx. adobe. com/ security. html)
    * Access / Cost: Free public
    * Relevance: Adobe security bulletins.
    * Notes: Important for client-side and enterprise Adobe software.
15. **Oracle Critical Patch Updates**
    * Link(s): www.oracle.com/security-alerts (https: / / www. oracle. com/ security- alerts/ )
    * Access / Cost: Free public
    * Relevance: Oracle CPU, Security Alerts, and CVE mappings.
    * Notes: Oracle advisories often bundle many products; mapping requires product/version context.
16. **Atlassian Security Advisories**
    * Link(s): www.atlassian.com/trust/security/advisories (https: / / www. atlassian. com/ trust/ security/ advisories)
    * Access / Cost: Free public
    * Relevance: Atlassian product advisories.
    * Notes: Important for exposed collaboration/dev tooling like Confluence and Jira.
17. **Elastic Security Announcements**
    * Link(s): discuss.elastic.co/c/announcements/security-announcements/31 (https: / / discuss. elastic. co/ c/ announcements/ security- announcements/ 31)
    * Access / Cost: Free public forum
    * Relevance: Elastic security announcements.
    * Notes: Useful for Elasticsearch/Kibana stack.
18. **HashiCorp Security**
    * Link(s): www.hashicorp.com/security (https: / / www. hashicorp. com/ security)
    * Access / Cost: Free public; enterprise support separate
    * Relevance: HashiCorp security advisories and disclosure policy.
    * Notes: Relevant for Terraform, Vault, Consul, Nomad.
19. **GitLab Security Releases**
    * Link(s): about.gitlab.com/releases/categories/releases (https: / / about. gitlab. com/ releases/ categories/ releases/ )
    * Access / Cost: Free public
    * Relevance: GitLab release posts, including security releases.
    * Notes: Security releases may include multiple CVEs and version-specific patches.
20. **Jenkins Security Advisories**
    * Link(s): www.jenkins.io/security/advisories (https: / / www. jenkins. io/ security/ advisories/ )
    * Access / Cost: Free public
    * Relevance: Jenkins core and plugin advisories.
    * Notes: Plugin affectedness is critical; inventory plugin versions.
21. **Apache Security Reports**
    * Link(s): www.apache.org/security (https: / / www. apache. org/ security/ )
    * Access / Cost: Free public
    * Relevance: Apache project security reports and process.
    * Notes: Many Apache projects have project-specific advisory pages.
22. **Eclipse Security Advisories**
    * Link(s): www.eclipse.org/security (https: / / www. eclipse. org/ security/ )
    * Access / Cost: Free public
    * Relevance: Eclipse project security advisories.
    * Notes: Useful for Java tooling and Eclipse projects.
23. **WordPress Security Releases**
    * Link(s): wordpress.org/news/category/security (https: / / wordpress. org/ news/ category/ security/ )
    * Access / Cost: Free public
    * Relevance: WordPress security release announcements.
    * Notes: Plugin/theme ecosystem needs separate assessment.
24. **Drupal Security Advisories**
    * Link(s): www.drupal.org/security (https: / / www. drupal. org/ security)
    * Access / Cost: Free public
    * Relevance: Drupal core and contributed project advisories.
    * Notes: Module inventory matters for affectedness.
25. **OpenSSL Vulnerabilities**
    * Link(s): www.openssl.org/news/vulnerabilities.html (https: / / www. openssl. org/ news/ vulnerabilities. html)
    * Access / Cost: Free public
    * Relevance: OpenSSL vulnerability list.
    * Notes: Critical transitive dependency in many systems; patch status depends on bundled library versions.
26. **OpenSSH release notes**
    * Link(s): www.openssh.com/releasenotes.html (https: / / www. openssh. com/ releasenotes. html)
    * Access / Cost: Free public
    * Relevance: OpenSSH release notes.
    * Notes: Security-relevant changes may appear in release notes.
27. **curl security advisories**
    * Link(s): curl.se/docs/security.html (https: / / curl. se/ docs/ security. html)
    * Access / Cost: Free public
    * Relevance: curl/libcurl security advisories.
    * Notes: Important for widely embedded dependency exposure.

### 6.3 Cloud provider security bulletins

1. **AWS Security Bulletins**
   * Link(s): aws.amazon.com/security/security-bulletins (https: / / aws. amazon. com/ security/ security- bulletins/ )
   * Access / Cost: Free public
   * Relevance: AWS service/product security bulletins.
   * Notes: Cloud provider advisories often require service/configuration context.
2. **AWS Security Blog**
   * Link(s): aws.amazon.com/blogs/security (https: / / aws. amazon. com/ blogs/ security/ )
   * Access / Cost: Free public
   * Relevance: AWS security guidance and incident context.
   * Notes: Good for mitigation patterns, not canonical CVE data.
3. **Google Cloud Security Bulletins**
   * Link(s): cloud.google.com/support/bulletins (https: / / cloud. google. com/ support/ bulletins)
   * Access / Cost: Free public
   * Relevance: Google Cloud security bulletins.
   * Notes: Use with asset inventory and managed service exposure.
4. **Google Cloud Security Blog**
   * Link(s): cloud.google.com/blog/products/identity-security (https: / / cloud. google. com/ blog/ products/ identity- security)
   * Access / Cost: Free public
   * Relevance: Google Cloud identity/security blog.
   * Notes: Useful for operational context and mitigations.
5. **Microsoft Azure security / MSRC**
   * Link(s): msrc.microsoft.com/update-guide (https: / / msrc. microsoft. com/ update- guide)
   * Access / Cost: Free public
   * Relevance: Microsoft/Azure-related security updates.
   * Notes: Azure service advisories may require separate portal/status checks.
6. **Azure updates**
   * Link(s): azure.microsoft.com/en-us/updates (https: / / azure. microsoft. com/ en- us/ updates/ )
   * Access / Cost: Free public
   * Relevance: Azure product update feed.
   * Notes: Not purely security-specific; filter carefully.
7. **Oracle Cloud security**
   * Link(s): www.oracle.com/security-alerts (https: / / www. oracle. com/ security- alerts/ )
   * Access / Cost: Free public
   * Relevance: Oracle cloud/product security alerts.
   * Notes: Oracle advisories often span cloud and on-prem products.
8. **IBM Cloud security bulletins**
   * Link(s): cloud.ibm.com/status/security (https: / / cloud. ibm. com/ status/ security)
   * Access / Cost: Free public
   * Relevance: IBM Cloud security bulletins.
   * Notes: Useful for managed service exposure.

## 7. SBOM, package identity, VEX & advisory exchange standards

### 7.1 SBOM standards

1. **CycloneDX specification overview**
   * Link(s): cyclonedx.org/specification/overview (https: / / cyclonedx. org/ specification/ overview/ )
   * Access / Cost: Free / open standard
   * Relevance: SBOM, SaaSBOM, BOM, VEX, vulnerability, and component metadata standard.
   * Notes: Good fit for vulnerability management workflows due to vulnerability and VEX support.
2. **CycloneDX GitHub**
   * Link(s): github.com/CycloneDX/specification (https: / / github. com/ CycloneDX/ specification)
   * Access / Cost: Free / open-source public GitHub repo
   * Relevance: CycloneDX specification source repository.
   * Notes: Use for versioned spec tracking.
3. **CycloneDX VEX**
   * Link(s): cyclonedx.org/capabilities/vex (https: / / cyclonedx. org/ capabilities/ vex/ )
   * Access / Cost: Free public docs
   * Relevance: CycloneDX VEX capability documentation.
   * Notes: Useful for affected/not-affected communication.
4. **SPDX specifications**
   * Link(s): spdx.dev/specifications (https: / / spdx. dev/ specifications/ )
   * Access / Cost: Free / open standard
   * Relevance: SPDX specifications for software bills of materials and package metadata.
   * Notes: SPDX is widely used for license/package metadata and supply-chain exchange.
5. **SPDX 3.0.1 spec**
   * Link(s): spdx.github.io/spdx-spec/v3.0.1 (https: / / spdx. github. io/ spdx- spec/ v3. 0. 1/ )
   * Access / Cost: Free public docs
   * Relevance: SPDX 3.0.1 specification.
   * Notes: Track spec version compatibility in parsers.
6. **SPDX package URL property**
   * Link(s): spdx.github.io/spdx-spec/v3.0.1/model/Software/Properties/packageUrl (https: / / spdx. github. io/ spdx- spec/ v3. 0. 1/ model/ Software/ Properties/ packageUrl/ )
   * Access / Cost: Free public docs
   * Relevance: SPDX support for package URL property.
   * Notes: Important for PURL-based vulnerability matching.
7. **SPDX GitHub**
   * Link(s): github.com/spdx/spdx-spec (https: / / github. com/ spdx/ spdx- spec)
   * Access / Cost: Free / open-source public GitHub repo
   * Relevance: SPDX specification repository.
   * Notes: Use for release tracking and schema/source inspection.
8. **NTIA SBOM resources**
   * Link(s): www.ntia.gov/page/software-bill-materials (https: / / www. ntia. gov/ page/ software- bill- materials)
   * Access / Cost: Free public
   * Relevance: SBOM policy and foundational resources.
   * Notes: Useful for governance and compliance context.
9. **CISA SBOM**
   * Link(s): www.cisa.gov/sbom (https: / / www. cisa. gov/ sbom)
   * Access / Cost: Free public
   * Relevance: CISA SBOM guidance and resources.
   * Notes: Useful for U.S. public-sector and enterprise SBOM program alignment.

### 7.2 Package & software identity

1. **Package URL - PURL spec**
   * Link(s): github.com/package-url/purl-spec (https: / / github. com/ package- url/ purl- spec)
   * Access / Cost: Free / open-source public GitHub repo
   * Relevance: Standard package identifier used in SBOMs and vulnerability DBs.
   * Notes: Crucial for OSV and package ecosystem matching.
2. **PURL types**
   * Link(s): github.com/package-url/purl-spec/blob/master/PURL-TYPES.rst (https: / / github. com/ package- url/ purl- spec/ blob/ master/ PURL- TYPES. rst)
   * Access / Cost: Free public
   * Relevance: Defines PURL types per ecosystem.
   * Notes: Helps normalize ecosystem-specific package coordinates.
3. **CPE specification / dictionary**
   * Link(s): nvd.nist.gov/products/cpe (https: / / nvd. nist. gov/ products/ cpe)
   * Access / Cost: Free public
   * Relevance: Product naming and CPE dictionary.
   * Notes: Useful for product/platform matching, but can be imprecise for packages.
4. **NVD CPE API**
   * Link(s): nvd.nist.gov/developers/products (https: / / nvd. nist. gov/ developers/ products)
   * Access / Cost: Free public; optional free API key for higher rate limits
   * Relevance: Programmatic CPE dictionary access.
   * Notes: Required for automated CPE matching workflows.
5. **SWID tags - NIST**
   * Link(s): csrc.nist.gov/projects/software-identification-swid (https: / / csrc. nist. gov/ projects/ software- identification- swid)
   * Access / Cost: Free public
   * Relevance: Software Identification Tags for installed software identity.
   * Notes: Useful in enterprise asset inventory and compliance.
6. **GS1 Digital Link / identifiers**
   * Link(s): www.gs1.org/standards/gs1-digital-link (https: / / www. gs1. org/ standards/ gs1- digital- link)
   * Access / Cost: Free public standard docs; GS1 membership may apply for assigned identifiers
   * Relevance: Optional identity standard for physical/embedded supply chains.
   * Notes: Not a vulnerability standard, but can matter in hardware/product traceability.
7. **Software Heritage IDs**
   * Link(s): www.swhid.org (https: / / www. swhid. org/ )
   * Access / Cost: Free public / open
   * Relevance: Persistent source-code artifact identity.
   * Notes: Useful for source provenance and precise code artifact references.

### 7.3 Advisory exchange, CSAF & VEX

1. **OASIS CSAF 2.0 specification**
   * Link(s): docs.oasis-open.org/csaf/csaf/v2.0/os/csaf-v2.0-os.html (https: / / docs. oasis- open. org/ csaf/ csaf/ v2. 0/ os/ csaf- v2. 0- os. html)
   * Access / Cost: Free / open standard
   * Relevance: Common Security Advisory Framework for structured advisories.
   * Notes: CSAF can express product status, remediation, impact, and VEX-like affectedness.
2. **CSAF home**
   * Link(s): www.csaf.io (https: / / www. csaf. io/ )
   * Access / Cost: Free public
   * Relevance: CSAF ecosystem and tooling hub.
   * Notes: Good starting point for CSAF adoption.
3. **OpenVEX specification**
   * Link(s): github.com/openvex/spec (https: / / github. com/ openvex/ spec)
   * Access / Cost: Free / open-source public GitHub repo
   * Relevance: Minimal JSON-LD VEX format based on CISA VEX requirements.
   * Notes: Useful for communicating not-affected/fixed/affected status.
4. **OpenVEX project page**
   * Link(s): openssf.org/projects/openvex (https: / / openssf. org/ projects/ openvex/ )
   * Access / Cost: Free public
   * Relevance: OpenSSF project page for OpenVEX.
   * Notes: Project-level overview.
5. **CISA Minimum Requirements for VEX**
   * Link(s): www.cisa.gov/sites/default/files/2023-04/minimum-requirements-for-vex-508c.pdf (https: / / www. cisa. gov/ sites/ default/ files/ 2023- 04/ minimum- requirements- for- vex- 508c. pdf)
   * Access / Cost: Free public PDF
   * Relevance: Baseline VEX requirements.
   * Notes: Useful for evaluating VEX completeness.
6. **OpenSSF VDR, VEX, OpenVEX & CSAF explainer**
   * Link(s): openssf.org/blog/2023/09/07/vdr-vex-openvex-and-csaf (https: / / openssf. org/ blog/ 2023/ 09/ 07/ vdr- vex- openvex- and- csaf/ )
   * Access / Cost: Free public
   * Relevance: Explains VDR, VEX, OpenVEX, and CSAF.
   * Notes: Useful for conceptual alignment and terminology.
7. **Red Hat CSAF/VEX guidance**
   * Link(s): redhatproductsecurity.github.io/security-data-guidelines/csaf-vex (https: / / redhatproductsecur ity. github. io/ security- data- guidelines/ csaf- vex/ )
   * Access / Cost: Free public docs
   * Relevance: Red Hat CSAF/VEX semantics and usage guidance.
   * Notes: Important for vendor-specific interpretation.
8. **Ubuntu VEX**
   * Link(s): ubuntu.com/security/vex (https: / / ubuntu. com/ security/ vex)
   * Access / Cost: Free public
   * Relevance: Ubuntu VEX data entry point.
   * Notes: Useful for Ubuntu affectedness and false-positive reduction.
9. **Canonical Ubuntu Security Notices repo - OSV & OpenVEX**
   * Link(s): github.com/canonical/ubuntu-security-notices (https: / / github. com/ canonical/ ubuntu- security- notices)
   * Access / Cost: Free public GitHub repo
   * Relevance: Canonical USN/LSN, OSV, and OpenVEX JSON data.
   * Notes: Strong machine-readable source for Ubuntu security status.

## 8. Malicious package, supply-chain compromise & package reputation sources

### 8.1 Malicious package databases

1. **OpenSSF Malicious Packages repository**
   * Link(s): github.com/ossf/malicious-packages (https: / / github. com/ ossf/ malicious- packages)
   * Access / Cost: Free / open-source public GitHub repo
   * Relevance: Public malicious package reports consumable via OSV format.
   * Notes: Covers malicious packages, which may not be CVEs.
2. **OpenSSF Malicious Packages announcement**
   * Link(s): openssf.org/blog/2023/10/12/introducing-openssfs-malicious-packages-repository (https: / / openssf. org/ blog/ 2023/ 10/ 12/ introducing- openssfs- malicious- packages- repository/ )
   * Access / Cost: Free public
   * Relevance: Explains the public DB for malicious package reports.
   * Notes: Context source, not the primary data feed.
3. **OpenSSF Package Analysis**
   * Link(s): openssf.org/package-analysis (https: / / openssf. org/ package- analysis/ )
   * Access / Cost: Free public project info
   * Relevance: Detects malicious package behavior and informs package consumers.
   * Notes: Behavioral analysis may surface packages before CVE/advisory assignment.
4. **OpenSSF Package Analysis GitHub**
   * Link(s): github.com/ossf/package-analysis (https: / / github. com/ ossf/ package- analysis)
   * Access / Cost: Free / open-source public GitHub repo
   * Relevance: Open-source package analysis system.
   * Notes: Useful for detection logic and behavioral signal review.
5. **OpenSSF Package Feeds**
   * Link(s): github.com/ossf/package-feeds (https: / / github. com/ ossf/ package- feeds)
   * Access / Cost: Free / open-source public GitHub repo
   * Relevance: Package ecosystem feed monitoring.
   * Notes: Useful for observing new packages in ecosystems.
6. **GitHub malware advisories**
   * Link(s): github.com/advisories?query=type%3Amalware (https: / / github. com/ advisories? query= type% 3Amalware)
   * Access / Cost: Free public
   * Relevance: GitHub malware advisories across ecosystems.
   * Notes: Treat as supply-chain compromise data, not conventional vuln data.
7. **npm malware advisories via GitHub**
   * Link(s): github.com/advisories?query=ecosystem%3Anpm+type%3Amalware (https: / / github. com/ advisories? query= ecosystem% 3Anpm+type% 3Amalware)
   * Access / Cost: Free public
   * Relevance: npm-specific malware advisories.
   * Notes: npm has high malicious package volume; prioritize transitive dependency visibility.
8. **PyPI malware advisories via GitHub**
   * Link(s): github.com/advisories?query=ecosystem%3Apip+type%3Amalware (https: / / github. com/ advisories? query= ecosystem% 3Apip+type% 3Amalware)
   * Access / Cost: Free public
   * Relevance: PyPI-specific malware advisories.
   * Notes: Use with lockfiles and package provenance checks.
9. **Socket.dev blog**
   * Link(s): socket.dev/blog (https: / / socket. dev/ blog)
   * Access / Cost: Free public blog; product/API features may be commercial
   * Relevance: Supply-chain attack research and malicious package analysis.
   * Notes: Research feed; verify indicators before automated blocking.
10. **Snyk vulnerability database**
    * Link(s): security.snyk.io (https: / / security. snyk. io/ )
    * Access / Cost: Free public search; commercial plans/API features
    * Relevance: Snyk vulnerability and package risk database.
    * Notes: Commercial/community source; validate licensing and provenance.
11. **Sonatype OSS Index**
    * Link(s): ossindex.sonatype.org (https: / / ossindex. sonatype. org/ )
    * Access / Cost: Free tier / API terms; commercial Sonatype products separate
    * Relevance: OSS vulnerability intelligence.
    * Notes: Useful for package risk enrichment.
12. **Sonatype vulnerability database**
    * Link(s): sonatype.com/resources/vulnerability-database (https: / / sonatype. com/ resources/ vulnerability- database)
    * Access / Cost: Free public search; commercial ecosystem
    * Relevance: Sonatype vulnerability database.
    * Notes: Good secondary enrichment source.
13. **Phylum research**
    * Link(s): blog.phylum.io (https: / / blog. phylum. io/ )
    * Access / Cost: Free public blog; commercial products separate
    * Relevance: Software supply-chain attack research.
    * Notes: Research source; useful for malicious package trends.
14. **ReversingLabs threat research**
    * Link(s): www.reversinglabs.com/blog (https: / / www. reversinglabs. com/ blog)
    * Access / Cost: Free public blog; commercial products separate
    * Relevance: Threat research focused on malware and supply-chain compromise.
    * Notes: Use for context, not as canonical package advisory data.
15. **Checkmarx supply-chain research**
    * Link(s): checkmarx.com/blog (https: / / checkmarx. com/ blog/ )
    * Access / Cost: Free public blog; commercial products separate
    * Relevance: Supply-chain and application security research.
    * Notes: Useful for emerging package attack patterns.

### 8.2 Package reputation / dependency health

1. **OpenSSF Scorecard**
   * Link(s): github.com/ossf/scorecard (https: / / github. com/ ossf/ scorecard)
   * Access / Cost: Free / open-source public GitHub repo
   * Relevance: Scores open-source project security practices.
   * Notes: Useful as dependency risk signal, not vulnerability proof.
2. **OpenSSF Scorecard API**
   * Link(s): api.securityscorecards.dev (https: / / api. securityscorecards . dev/ )
   * Access / Cost: Free public API subject to service limits
   * Relevance: API for Scorecard results.
   * Notes: Use with timestamped results because scores change over time.
3. **OpenSSF Best Practices Badge**
   * Link(s): www.bestpractices.dev (https: / / www. bestpractices. dev/ )
   * Access / Cost: Free public
   * Relevance: Project best-practices badge program.
   * Notes: Useful project maturity signal, not vulnerability evidence.
4. **deps.dev**
   * Link(s): deps.dev (https://deps.dev/)
   * Access / Cost: Free public
   * Relevance: Dependency metadata, transitive dependencies, security signals.
   * Notes: Useful for dependency graphing and package metadata.
5. **OpenSSF GUAC**
   * Link(s): guac.sh (https://guac.sh/)
   * Access / Cost: Free public / open-source project
   * Relevance: Graph for software supply-chain metadata.
   * Notes: Useful for correlating SBOMs, attestations, vulnerabilities, and provenance.
6. **GUAC GitHub**
   * Link(s): github.com/guacsec/guac (https: / / github. com/ guacsec/ guac)
   * Access / Cost: Free / open-source public GitHub repo
   * Relevance: GUAC implementation repository.
   * Notes: Reference architecture for supply-chain knowledge graphs.
7. **Sigstore**
   * Link(s): www.sigstore.dev (https: / / www. sigstore. dev/ )
   * Access / Cost: Free / open-source public infrastructure
   * Relevance: Signing and verification for software artifacts.
   * Notes: Helps assess provenance and tamper resistance.
8. **Rekor transparency log**
   * Link(s): docs.sigstore.dev/logging/overview (https: / / docs. sigstore. dev/ logging/ overview/ )
   * Access / Cost: Free public docs / public transparency log
   * Relevance: Transparency log for signed artifacts.
   * Notes: Useful for provenance verification and audit trails.
9. **SLSA framework**
   * Link(s): slsa.dev (https://slsa.dev/)
   * Access / Cost: Free / open standard
   * Relevance: Supply-chain Levels for Software Artifacts.
   * Notes: Helps assess build integrity and supply-chain hardening.

## 9. Automated vulnerability detection, static analysis, dynamic analysis & research datasets

### 9.1 SAST / code query engines

1. **CodeQL**
   * Link(s): codeql.github.com (https: / / codeql. github. com/ )
   * Access / Cost: Free for many open-source uses; GitHub Advanced Security commercial for private enterprise use
   * Relevance: Semantic code analysis engine for vulnerability discovery.
   * Notes: Strong for variant analysis and source-level detection.
2. **CodeQL GitHub**
   * Link(s): github.com/github/codeql (https: / / github. com/ github/ codeql)
   * Access / Cost: Free / open-source public GitHub repo
   * Relevance: CodeQL source and query repository.
   * Notes: Use query packs for detection logic examples.
3. **CodeQL query packs**
   * Link(s): github.com/github/codeql/tree/main (https: / / github. com/ github/ codeql/ tree/ main)
   * Access / Cost: Free / open-source public GitHub repo
   * Relevance: Query packs for multiple languages.
   * Notes: Queries can be adapted for custom vuln detection.
4. **Semgrep**
   * Link(s): semgrep.dev (https://semgrep.dev/)
   * Access / Cost: Free/open-source CLI; commercial products available
   * Relevance: Pattern-based static analysis.
   * Notes: Good for fast custom rule writing.
5. **Semgrep rules**
   * Link(s): github.com/semgrep/semgrep-rules (https: / / github. com/ semgrep/ semgrep- rules)
   * Access / Cost: Free / open-source public GitHub repo
   * Relevance: Community/official Semgrep rules.
   * Notes: Validate rule precision before production blocking.
6. **Joern**
   * Link(s): joern.io (https://joern.io/)
   * Access / Cost: Free / open-source core
   * Relevance: Code property graph platform.
   * Notes: Useful for research-grade vulnerability discovery.
7. **Joern GitHub**
   * Link(s): github.com/joernio/joern (https: / / github. com/ joernio/ joern)
   * Access / Cost: Free / open-source public GitHub repo
   * Relevance: Joern implementation.
   * Notes: Useful for custom graph queries and ML pipelines.
8. **Facebook Infer**
   * Link(s): fbinfer.com (https://fbinfer.com/ )
   * Access / Cost: Free public / open-source
   * Relevance: Static analyzer for multiple languages.
   * Notes: Useful for null deref, resource leaks, concurrency, and related bug classes.
9. **Infer GitHub**
   * Link(s): github.com/facebook/infer (https: / / github. com/ facebook/ infer)
   * Access / Cost: Free / open-source public GitHub repo
   * Relevance: Infer source repository.
   * Notes: Reference implementation.
10. **SonarQube rules**
    * Link(s): rules.sonarsource.com (https: / / rules. sonarsource. com/ )
    * Access / Cost: Free public rules catalog; Sonar products include free and commercial tiers
    * Relevance: SonarSource rule catalog.
    * Notes: Useful for mapping code quality/security rules to weakness classes.
11. **Bandit - Python**
    * Link(s): github.com/PyCQA/bandit (https: / / github. com/ PyCQA/ bandit)
    * Access / Cost: Free / open-source public GitHub repo
    * Relevance: Python security linter.
    * Notes: Useful for Python SAST coverage.
12. **Gosec - Go**
    * Link(s): github.com/securego/gosec (https: / / github. com/ securego/ gosec)
    * Access / Cost: Free / open-source public GitHub repo
    * Relevance: Go security checker.
    * Notes: Useful for Go SAST.
13. **ESLint security plugin**
    * Link(s): github.com/eslint-community/eslint-plugin-security (https: / / github. com/ eslint- community/ eslint- plugin- security)
    * Access / Cost: Free / open-source public GitHub repo
    * Relevance: JavaScript security lint rules.
    * Notes: Useful for JS static checks.
14. **SpotBugs**
    * Link(s): spotbugs.github.io (https: / / spotbugs. github. io/ )
    * Access / Cost: Free / open-source
    * Relevance: Java static analysis.
    * Notes: General bug detection; pair with FindSecBugs for security.
15. **FindSecBugs**
    * Link(s): find-sec-bugs.github.io (https: / / find- sec- bugs. github. io/ )
    * Access / Cost: Free / open-source
    * Relevance: Java security bug detection plugin.
    * Notes: Useful for Java/JVM SAST.
16. **Clang Static Analyzer**
    * Link(s): clang-analyzer.llvm.org (https: / / clang- analyzer. llvm. org/ )
    * Access / Cost: Free / open-source
    * Relevance: C/C++/Objective-C static analyzer.
    * Notes: Useful for native code vulnerability classes.
17. **Cppcheck**
    * Link(s): cppcheck.sourceforge.io (https: / / cppcheck. sourceforge. io/ )
    * Access / Cost: Free / open-source
    * Relevance: C/C++ static analyzer.
    * Notes: Complements compiler analyzers.
18. **Flawfinder**
    * Link(s): dwheeler.com/flawfinder (https: / / dwheeler. com/ flawfinder/ )
    * Access / Cost: Free / open-source
    * Relevance: C/C++ security scanner for dangerous functions.
    * Notes: Fast heuristic scanner with false-positive risk.
19. **Brakeman - Ruby on Rails**
    * Link(s): brakemanscanner.org (https: / / brakemanscanner. org/ )
    * Access / Cost: Free / open-source
    * Relevance: Ruby on Rails static security scanner.
    * Notes: Useful for Rails-specific vulnerability patterns.
20. **Horusec**
    * Link(s): github.com/ZupIT/horusec (https: / / github. com/ ZupIT/ horusec)
    * Access / Cost: Free / open-source public GitHub repo
    * Relevance: Multi-language security scanner.
    * Notes: Useful for broad SAST coverage.
21. **Bearer**
    * Link(s): github.com/Bearer/bearer (https: / / github. com/ Bearer/ bearer)
    * Access / Cost: Free / open-source public GitHub repo
    * Relevance: Code security/privacy scanner.
    * Notes: Useful for data-flow and sensitive data exposure detection.
22. **MobSF**
    * Link(s): github.com/MobSF/Mobile-Security-Framework-MobSF (https: / / github. com/ MobSF/ Mobile- Security- Framework- MobSF)
    * Access / Cost: Free / open-source public GitHub repo
    * Relevance: Mobile security testing framework.
    * Notes: Useful for Android/iOS static and dynamic app analysis.

### 9.2 DAST, IAST, fuzzing & dynamic test sources

1. **OSS-Fuzz**
   * Link(s): google.github.io/oss-fuzz (https: / / google. github. io/ oss- fuzz/ )
   * Access / Cost: Free for eligible open-source projects
   * Relevance: Continuous fuzzing for open-source projects.
   * Notes: Useful for vulnerability discovery and bug lifecycle data.
2. **OSS-Fuzz GitHub**
   * Link(s): github.com/google/oss-fuzz (https: / / github. com/ google/ oss- fuzz)
   * Access / Cost: Free / open-source public GitHub repo
   * Relevance: OSS-Fuzz project configuration repository.
   * Notes: Useful for project fuzzing coverage and harness examples.
3. **OSS-Fuzz vulnerability data in OSV**
   * Link(s): osv.dev/list?ecosystem=OSS-Fuzz (https: / / osv. dev/ list? ecosystem= OSS- Fuzz)
   * Access / Cost: Free public
   * Relevance: OSV records from OSS-Fuzz vulnerabilities.
   * Notes: Good for linking fuzz-discovered vulnerabilities to OSV schema.
4. **ClusterFuzzLite**
   * Link(s): google.github.io/clusterfuzzlite (https: / / google. github. io/ clusterfuzzlite/ )
   * Access / Cost: Free / open-source
   * Relevance: Lightweight continuous fuzzing for CI/CD.
   * Notes: Useful for integrating fuzzing into development pipelines.
5. **AFL++**
   * Link(s): github.com/AFLplusplus/AFLplusplus (https: / / github. com/ AFLplusplus/ AFLplusplus)
   * Access / Cost: Free / open-source public GitHub repo
   * Relevance: Coverage-guided fuzzer.
   * Notes: Good for native code vulnerability discovery.
6. **libFuzzer**
   * Link(s): llvm.org/docs/LibFuzzer.html (https: / / llvm. org/ docs/ LibFuzzer. html)
   * Access / Cost: Free / open-source LLVM component
   * Relevance: In-process coverage-guided fuzzer.
   * Notes: Common with LLVM sanitizers.
7. **Honggfuzz**
   * Link(s): github.com/google/honggfuzz (https: / / github. com/ google/ honggfuzz)
   * Access / Cost: Free / open-source public GitHub repo
   * Relevance: Security-oriented fuzzer.
   * Notes: Useful for native code dynamic testing.
8. **Jazzer**
   * Link(s): github.com/CodeIntelligenceTesting/jazzer (https: / / github. com/ CodeIntelligenceTe sting/ jazzer)
   * Access / Cost: Free / open-source public GitHub repo
   * Relevance: JVM fuzzing engine.
   * Notes: Useful for Java/Kotlin fuzz testing.
9. **OWASP ZAP**
   * Link(s): www.zaproxy.org (https: / / www. zaproxy. org/ )
   * Access / Cost: Free / open-source
   * Relevance: Web application dynamic security scanner.
   * Notes: Useful for DAST and app exposure validation.
10. **Nuclei**
    * Link(s): github.com/projectdiscovery/nuclei (https: / / github. com/ projectdiscovery/ nuclei)
    * Access / Cost: Free / open-source public GitHub repo; commercial ecosystem separate
    * Relevance: Template-based vulnerability and exposure scanner.
    * Notes: Useful for automated exposed-service checks.
11. **Nuclei templates**
    * Link(s): github.com/projectdiscovery/nuclei-templates (https: / / github. com/ projectdiscovery/ nuclei- templates)
    * Access / Cost: Free / open-source public GitHub repo
    * Relevance: Community/official detection templates.
    * Notes: Template quality varies; review false-positive potential.

### 9.3 Vulnerability-detection research datasets

1. **NIST SARD**
   * Link(s): samate.nist.gov/SARD (https: / / samate. nist. gov/ SARD/ )
   * Access / Cost: Free public
   * Relevance: Software Assurance Reference Dataset.
   * Notes: Useful for evaluating static analysis tools and ML models.
2. **Juliet Test Suite - NIST SARD**
   * Link(s): samate.nist.gov/SARD/test-suites/112 (https: / / samate. nist. gov/ SARD/ test- suites/ 112)
   * Access / Cost: Free public
   * Relevance: Synthetic test cases for many vulnerability classes.
   * Notes: Useful for controlled evaluation, but may not reflect real-world code complexity.
3. **Big-Vul**
   * Link(s): github.com/ZeoVan/MSR\_20\_Code\_vulnerability\_CSV\_Dataset (https: / / github. com/ ZeoVan/ MSR\_ 20\_ Code\_ vulnerability\_ CSV\_ Dataset)
   * Access / Cost: Free public GitHub repo; verify license
   * Relevance: Large vulnerability dataset derived from real-world CVE-fix commits.
   * Notes: Validate deduplication, labels, and train/test leakage.
4. **Devign**
   * Link(s): sites.google.com/view/devign (https: / / sites. google. com/ view/ devign)
   * Access / Cost: Free public research page; verify dataset access/license
   * Relevance: Vulnerability detection dataset.
   * Notes: Used in ML vuln detection research.
5. **Draper VDISC**
   * Link(s): osf.io/d45bw (https: / / osf. io/ d45bw/ )
   * Access / Cost: Free public OSF dataset; verify license/terms
   * Relevance: Vulnerability discovery dataset.
   * Notes: Useful for ML baselines; inspect labeling quality.
6. **DiverseVul**
   * Link(s): github.com/wagner-group/diversevul (https: / / github. com/ wagner- group/ diversevul)
   * Access / Cost: Free public GitHub repo; verify license
   * Relevance: Diverse vulnerability dataset.
   * Notes: Useful for model training/evaluation; check license and label quality.
7. **PrimeVul**
   * Link(s): github.com/DLVulDet/PrimeVul (https: / / github. com/ DLVulDet/ PrimeVul)
   * Access / Cost: Free public GitHub repo; verify license
   * Relevance: Vulnerability detection benchmark dataset.
   * Notes: Useful for modern ML vulnerability detection benchmarking.
8. **MegaVul**
   * Link(s): github.com/Icyrockton/MegaVul (https: / / github. com/ Icyrockton/ MegaVul)
   * Access / Cost: Free public GitHub repo; verify license
   * Relevance: Large-scale vulnerability dataset.
   * Notes: Validate methodology before using as labels.
9. **Vul4J**
   * Link(s): github.com/tuhh-softsec/vul4j (https: / / github. com/ tuhh- softsec/ vul4j)
   * Access / Cost: Free / open-source public GitHub repo
   * Relevance: Java vulnerability benchmark.
   * Notes: Useful for Java-focused vulnerability repair/detection.
10. **VulnCode-DB**
    * Link(s): github.com/vegardit/vulncode-db (https: / / github. com/ vegardit/ vulncode- db)
    * Access / Cost: Free public GitHub repo; verify license
    * Relevance: Vulnerable code examples.
    * Notes: Useful for examples and tests.
11. **SecurityEval**
    * Link(s): github.com/s2e-lab/SecurityEval (https: / / github. com/ s2e- lab/ SecurityEval)
    * Access / Cost: Free public GitHub repo; verify license
    * Relevance: Security-focused benchmark.
    * Notes: Useful for evaluating generated code or models.
12. **CVEfixes**
    * Link(s): github.com/secureIT-project/CVEfixes (https: / / github. com/ secureIT- project/ CVEfixes)
    * Access / Cost: Free public GitHub repo; verify license
    * Relevance: Links CVEs to fixing commits.
    * Notes: Useful for root-cause, patch, and ML training pipelines.
13. **Defects4J**
    * Link(s): github.com/rjust/defects4j (https: / / github. com/ rjust/ defects4j)
    * Access / Cost: Free / open-source public GitHub repo
    * Relevance: Java bug dataset.
    * Notes: Not vulnerability-specific, but useful for bug repair baselines.
14. **ManySStuBs4J**
    * Link(s): github.com/mast-group/mineSStuBs (https: / / github. com/ mast- group/ mineSStuBs)
    * Access / Cost: Free public GitHub repo; verify license
    * Relevance: Java simple bug dataset.
    * Notes: Not vulnerability-specific, but useful for bug-fix modeling.
15. **VulDeePecker**
    * Link(s): github.com/CGCL-codes/VulDeePecker (https: / / github. com/ CGCL- codes/ VulDeePecker)
    * Access / Cost: Free public GitHub repo; verify license
    * Relevance: Deep-learning vulnerability detection dataset/tooling.
    * Notes: Older benchmark; inspect for duplication and outdated methodology.

## 10. ICS, OT, IoT, embedded & medical-device sources

### 10.1 CISA ICS / medical

1. **CISA ICS Advisories**
   * Link(s): www.cisa.gov/news-events/ics-advisories (https: / / www. cisa. gov/ news- events/ ics- advisories)
   * Access / Cost: Free public
   * Relevance: Industrial Control System advisories.
   * Notes: Critical for OT/ICS environments where patching constraints differ from IT.
2. **CISA ICS Medical Advisories**
   * Link(s): www.cisa.gov/news-events/ics-medical-advisories (https: / / www. cisa. gov/ news- events/ ics- medical- advisories)
   * Access / Cost: Free public
   * Relevance: Medical device security advisories.
   * Notes: Impact includes patient safety, regulatory, and operational risk.
3. **CISA cybersecurity advisories**
   * Link(s): www.cisa.gov/cybersecurity-advisories (https: / / www. cisa. gov/ cybersecurity- advisories)
   * Access / Cost: Free public
   * Relevance: CISA cybersecurity advisory hub.
   * Notes: Broader than ICS; use for campaigns and emergent threats.
4. **ICS-CERT advisories archive**
   * Link(s): www.cisa.gov/news-events/ics-advisories (https: / / www. cisa. gov/ news- events/ ics- advisories)
   * Access / Cost: Free public
   * Relevance: ICS-CERT advisory archive path.
   * Notes: Same URL as ICS advisories, preserved for historical naming.
5. **CISA ICS recommended practices**
   * Link(s): www.cisa.gov/resources-tools/resources/ics-recommended-practices (https: / / www. cisa. gov/ resources- tools/ resources/ ics- recommended- practices)
   * Access / Cost: Free public
   * Relevance: Recommended practices for ICS security.
   * Notes: Useful for mitigation where patching is delayed or impossible.

### 10.2 OT / ICS vendor advisories

1. **Siemens ProductCERT**
   * Link(s): cert-portal.siemens.com/productcert (https: / / cert- portal. siemens. com/ productcert/ )
   * Access / Cost: Free public advisories; some support downloads may require entitlement
   * Relevance: Siemens product security advisories.
   * Notes: Critical for industrial environments.
2. **Schneider Electric Security Notifications**
   * Link(s): www.se.com/ww/en/work/support/cybersecurity/security-notifications.jsp (https: / / www. se. com/ ww/ en/ work/ support/ cybersecurity/ security- notifications. jsp)
   * Access / Cost: Free public
   * Relevance: Schneider Electric security notifications.
   * Notes: Product model and firmware version matter heavily.
3. **Rockwell Automation Security Advisories**
   * Link(s): www.rockwellautomation.com/en-us/support/product/product-security-advisories.html (https: / / www. rockwellautomation . com/ en- us/ support/ product/ product- security- advisories. html)
   * Access / Cost: Free public listing; support downloads may require entitlement
   * Relevance: Rockwell Automation product advisories.
   * Notes: Operational constraints may affect remediation.
4. **Honeywell Product Security**
   * Link(s): www.honeywell.com/us/en/product-security (https: / / www. honeywell. com/ us/ en/ product- security)
   * Access / Cost: Free public
   * Relevance: Honeywell product security advisories.
   * Notes: Useful for OT product risk.
5. **Philips Product Security**
   * Link(s): www.philips.com/a-w/security/security-advisories.html (https: / / www. philips. com/ a- w/ security/ security- advisories. html)
   * Access / Cost: Free public
   * Relevance: Philips medical/product security advisories.
   * Notes: Patient safety and regulatory implications may affect severity assessment.
6. **GE Vernova Product Security**
   * Link(s): www.gevernova.com/product-security (https: / / www. gevernova. com/ product- security)
   * Access / Cost: Free public
   * Relevance: GE Vernova product security.
   * Notes: Important for energy/industrial systems.
7. **ABB Cyber Security Alerts**
   * Link(s): global.abb/group/en/technology/cyber-security/alerts-and-notifications (https: / / global. abb/ group/ en/ technology/ cyber- security/ alerts- and- notifications)
   * Access / Cost: Free public
   * Relevance: ABB cyber security alerts and notifications.
   * Notes: Product-specific affectedness matters.
8. **Yokogawa Security Advisories**
   * Link(s): www.yokogawa.com/library/resources/white-papers/yokogawa-security-advisory-report-list (https: / / www. yokogawa. com/ library/ resources/ white- papers/ yokogawa- security- advisory- report- list/ )
   * Access / Cost: Free public
   * Relevance: Yokogawa advisory report list.
   * Notes: Useful for OT control systems.
9. **Mitsubishi Electric PSIRT**
   * Link(s): www.mitsubishielectric.com/en/psirt/vulnerability (https: / / www. mitsubishielectric . com/ en/ psirt/ vulnerability/ )
   * Access / Cost: Free public
   * Relevance: Mitsubishi Electric vulnerability advisories.
   * Notes: Important for industrial equipment and automation.
10. **Johnson Controls Product Security Advisories**
    * Link(s): www.johnsoncontrols.com/cyber-solutions/security-advisories (https: / / www. johnsoncontrols. com/ cyber- solutions/ security- advisories)
    * Access / Cost: Free public
    * Relevance: Johnson Controls security advisories.
    * Notes: Relevant to building management and OT environments.

### 10.3 IoT / embedded

1. **CERT/CC Vulnerability Notes**
   * Link(s): www.kb.cert.org/vuls (https: / / www. kb. cert. org/ vuls/ )
   * Access / Cost: Free public
   * Relevance: Coordinated disclosure notes, often with embedded/IoT affected vendors.
   * Notes: Useful when many vendors share a vulnerable component.
2. **IoT Security Foundation**
   * Link(s): www.iotsecurityfoundation.org (https: / / www. iotsecurityfoundat ion. org/ )
   * Access / Cost: Free public resources; membership options may exist
   * Relevance: IoT security guidance and resources.
   * Notes: Not a vulnerability feed, but useful for control mapping.
3. **Firmware Analysis and Comparison Tool - FACT**
   * Link(s): github.com/fkie-cad/FACT\_core (https: / / github. com/ fkie- cad/ FACT\_ core)
   * Access / Cost: Free / open-source public GitHub repo
   * Relevance: Firmware analysis platform.
   * Notes: Useful for extracting components and embedded vuln detection.
4. **EMBA firmware analyzer**
   * Link(s): github.com/e-m-b-a/emba (https: / / github. com/ e- m- b- a/ emba)
   * Access / Cost: Free / open-source public GitHub repo
   * Relevance: Firmware analyzer for embedded Linux/IoT.
   * Notes: Useful for SBOM-like extraction and vulnerability assessment.
5. **Binwalk**
   * Link(s): github.com/ReFirmLabs/binwalk (https: / / github. com/ ReFirmLabs/ binwalk)
   * Access / Cost: Free / open-source public GitHub repo
   * Relevance: Firmware extraction and analysis tool.
   * Notes: Useful precursor for embedded component discovery.

## 11. Exposure, internet-facing asset & threat telemetry

### 11.1 Internet exposure search engines

1. **Censys Search**
   * Link(s): search.censys.io (https: / / search. censys. io/ )
   * Access / Cost: Free tier / paid plans
   * Relevance: Internet exposure search engine.
   * Notes: Useful for determining if vulnerable services are internet-facing.
2. **Censys API**
   * Link(s): search.censys.io/api (https: / / search. censys. io/ api)
   * Access / Cost: Free tier / paid plans; API key required
   * Relevance: Programmatic Censys access.
   * Notes: API terms and quotas may apply.
3. **Shodan**
   * Link(s): www.shodan.io (https: / / www. shodan. io/ )
   * Access / Cost: Free limited access / paid plans
   * Relevance: Internet-connected device search.
   * Notes: Useful for exposure discovery and banner-based matching.
4. **Shodan developer API**
   * Link(s): developer.shodan.io (https: / / developer. shodan. io/ )
   * Access / Cost: Paid/API credit model may apply; account required
   * Relevance: Shodan API documentation.
   * Notes: Useful for automation.
5. **ZoomEye**
   * Link(s): www.zoomeye.org (https: / / www. zoomeye. org/ )
   * Access / Cost: Free limited access / paid plans
   * Relevance: Internet asset search engine.
   * Notes: Useful as additional exposure telemetry.
6. **FOFA**
   * Link(s): fofa.info (https://fofa.info/)
   * Access / Cost: Free limited access / paid plans
   * Relevance: Internet asset search.
   * Notes: Coverage and access terms vary.
7. **BinaryEdge**
   * Link(s): www.binaryedge.io (https: / / www. binaryedge. io/ )
   * Access / Cost: Commercial / limited trial may exist
   * Relevance: Internet scanning and threat intelligence.
   * Notes: Useful for external exposure enrichment.
8. **Onyphe**
   * Link(s): www.onyphe.io (https: / / www. onyphe. io/ )
   * Access / Cost: Free tier / paid plans
   * Relevance: Cyber defense search engine.
   * Notes: Useful for passive/active exposure context.
9. **SecurityTrails**
   * Link(s): securitytrails.com (https: / / securitytrails. com/ )
   * Access / Cost: Free limited access / paid plans
   * Relevance: DNS and asset intelligence.
   * Notes: Useful for attack surface discovery.
10. **InternetDB by Shodan**
    * Link(s): internetdb.shodan.io (https: / / internetdb. shodan. io/ )
    * Access / Cost: Free public API
    * Relevance: Lightweight Shodan InternetDB API.
    * Notes: Useful for quick IP exposure enrichment.

### 11.2 Scan/exploitation telemetry

1. **GreyNoise Visualizer**
   * Link(s): viz.greynoise.io (https: / / viz. greynoise. io/ )
   * Access / Cost: Free tier / paid plans
   * Relevance: Internet scanning/exploitation telemetry.
   * Notes: Helps separate background scanning from targeted activity.
2. **GreyNoise API docs**
   * Link(s): docs.greynoise.io (https: / / docs. greynoise. io/ )
   * Access / Cost: Free tier / paid plans; API key required
   * Relevance: API docs for GreyNoise enrichment.
   * Notes: Useful for automated telemetry enrichment.
3. **Shadowserver**
   * Link(s): www.shadowserver.org (https: / / www. shadowserver. org/ )
   * Access / Cost: Free for eligible organizations; registration may be required
   * Relevance: Internet-scale exposure and threat telemetry.
   * Notes: Good for population-level exposure signals.
4. **Shadowserver reports**
   * Link(s): dashboard.shadowserver.org (https: / / dashboard. shadowserver. org/ )
   * Access / Cost: Free for eligible organizations; login/registration may be required
   * Relevance: Shadowserver reporting dashboard.
   * Notes: Access/eligibility may vary.
5. **SANS Internet Storm Center**
   * Link(s): isc.sans.edu (https: / / isc. sans. edu/ )
   * Access / Cost: Free public
   * Relevance: Internet threat telemetry and diary reports.
   * Notes: Useful for emergent exploitation context.
6. **Honeynet Project**
   * Link(s): www.honeynet.org (https: / / www. honeynet. org/ )
   * Access / Cost: Free public / open research
   * Relevance: Honeypot and threat research.
   * Notes: Useful for attacker behavior insight.
7. **DShield**
   * Link(s): www.dshield.org (https: / / www. dshield. org/ )
   * Access / Cost: Free public / community
   * Relevance: Distributed intrusion detection and telemetry.
   * Notes: Useful for broad scanning trend analysis.
8. **LeakIX**
   * Link(s): leakix.net (https: / / leakix. net/ )
   * Access / Cost: Free limited access / paid plans
   * Relevance: Exposed service and leak search.
   * Notes: Useful for exposure assessment.
9. **urlscan.io**
   * Link(s): urlscan.io (https: / / urlscan. io/ )
   * Access / Cost: Free tier / paid plans
   * Relevance: URL scanning and web telemetry.
   * Notes: Useful for phishing, web exposure, and IOC enrichment.
10. **VirusTotal**
    * Link(s): www.virustotal.com (https: / / www. virustotal. com/ )
    * Access / Cost: Free community access / paid enterprise plans
    * Relevance: File, URL, domain, and IP reputation.
    * Notes: Useful for malware/IOC enrichment; licensing constraints apply.
11. **VirusTotal API**
    * Link(s): docs.virustotal.com/reference/overview (https: / / docs. virustotal. com/ reference/ overview)
    * Access / Cost: Free community API / paid enterprise API
    * Relevance: VirusTotal API documentation.
    * Notes: API quota and data-sharing policies matter.

### 11.3 Attack surface management context

1. **Amass**
   * Link(s): github.com/owasp-amass/amass (https: / / github. com/ owasp- amass/ amass)
   * Access / Cost: Free / open-source public GitHub repo
   * Relevance: Attack surface mapping and DNS enumeration.
   * Notes: Useful for external asset discovery.
2. **ProjectDiscovery Subfinder**
   * Link(s): github.com/projectdiscovery/subfinder (https: / / github. com/ projectdiscovery/ subfinder)
   * Access / Cost: Free / open-source public GitHub repo
   * Relevance: Subdomain discovery.
   * Notes: Useful for asset inventory enrichment.
3. **httpx**
   * Link(s): github.com/projectdiscovery/httpx (https: / / github. com/ projectdiscovery/ httpx)
   * Access / Cost: Free / open-source public GitHub repo
   * Relevance: HTTP probing toolkit.
   * Notes: Useful for validating exposed services.
4. **Naabu**
   * Link(s): github.com/projectdiscovery/naabu (https: / / github. com/ projectdiscovery/ naabu)
   * Access / Cost: Free / open-source public GitHub repo
   * Relevance: Port scanner.
   * Notes: Useful for fast exposure discovery.
5. **Nmap**
   * Link(s): nmap.org (https://nmap.org/)
   * Access / Cost: Free / open-source
   * Relevance: Network discovery and security auditing.
   * Notes: Mature scanner for service detection and scripts.
6. **Masscan**
   * Link(s): github.com/robertdavidgraham/masscan (https: / / github. com/ robertdavidgraham/ masscan)
   * Access / Cost: Free / open-source public GitHub repo
   * Relevance: High-speed port scanner.
   * Notes: Use carefully; scan authorization and network impact matter.

## 12. Threat intelligence, malware, ransomware & in-the-wild exploitation context

### 12.1 Major threat research sources

1. **Mandiant / Google Cloud Threat Intelligence**
   * Link(s): cloud.google.com/blog/topics/threat-intelligence (https: / / cloud. google. com/ blog/ topics/ threat- intelligence)
   * Access / Cost: Free public blog; commercial threat intel products separate
   * Relevance: Threat intelligence and exploitation-in-the-wild context.
   * Notes: Useful for campaign-level vulnerability exploitation context.
2. **Microsoft Threat Intelligence blog**
   * Link(s): www.microsoft.com/en-us/security/blog/topic/threat-intelligence (https: / / www. microsoft. com/ en- us/ security/ blog/ topic/ threat- intelligence/ )
   * Access / Cost: Free public blog
   * Relevance: Microsoft threat intel and exploitation reports.
   * Notes: Useful for attacker behavior, exploitation campaigns, and mitigations.
3. **Google Threat Analysis Group**
   * Link(s): blog.google/threat-analysis-group (https: / / blog. google/ threat- analysis- group/ )
   * Access / Cost: Free public blog
   * Relevance: Nation-state and high-end threat research.
   * Notes: Useful for exploited-in-the-wild context.
4. **Palo Alto Unit 42**
   * Link(s): unit42.paloaltonetworks.com (https: / / unit42. paloaltonetworks. com/ )
   * Access / Cost: Free public blog; commercial threat intel services separate
   * Relevance: Threat research and vulnerability exploitation reporting.
   * Notes: Useful for campaign and malware context.
5. **Cisco Talos**
   * Link(s): blog.talosintelligence.com (https: / / blog. talosintelligence. com/ )
   * Access / Cost: Free public blog; commercial Cisco products separate
   * Relevance: Threat intel, malware, and vulnerability research.
   * Notes: Useful for IOCs and exploit campaigns.
6. **Rapid7 vulnerability management blog**
   * Link(s): www.rapid7.com/blog/tag/vulnerability-management (https: / / www. rapid7. com/ blog/ tag/ vulnerability- management/ )
   * Access / Cost: Free public blog; commercial products separate
   * Relevance: Vulnerability management and exploitability commentary.
   * Notes: Useful for operational triage context.
7. **Sophos X-Ops**
   * Link(s): news.sophos.com/en-us/category/threat-research (https: / / news. sophos. com/ en- us/ category/ threat- research/ )
   * Access / Cost: Free public blog; commercial products separate
   * Relevance: Threat research and incident reports.
   * Notes: Useful for exploitation context and malware behavior.
8. **CrowdStrike Blog**
   * Link(s): www.crowdstrike.com/en-us/blog (https: / / www. crowdstrike. com/ en- us/ blog/ )
   * Access / Cost: Free public blog; commercial products separate
   * Relevance: Threat intelligence and incident research.
   * Notes: Useful for adversary behavior and vulnerability exploitation context.
9. **SentinelOne Labs**
   * Link(s): www.sentinelone.com/labs (https: / / www. sentinelone. com/ labs/ )
   * Access / Cost: Free public blog; commercial products separate
   * Relevance: Malware and threat research.
   * Notes: Useful for exploit chains and malware analysis.
10. **Kaspersky Securelist**
    * Link(s): securelist.com (https: / / securelist. com/ )
    * Access / Cost: Free public blog; commercial products separate
    * Relevance: Threat research and malware analysis.
    * Notes: Useful for campaign-level context.
11. **ESET WeLiveSecurity**
    * Link(s): www.welivesecurity.com (https: / / www. welivesecurity. com/ )
    * Access / Cost: Free public blog; commercial products separate
    * Relevance: Threat research and malware analysis.
    * Notes: Useful for exploitation narratives and IOCs.
12. **Trend Micro Research**
    * Link(s): www.trendmicro.com/en\_us/research.html (https: / / www. trendmicro. com/ en\_ us/ research. html)
    * Access / Cost: Free public research; commercial products separate
    * Relevance: Threat and vulnerability research.
    * Notes: Useful for active exploitation context.
13. **FortiGuard Labs**
    * Link(s): www.fortiguard.com/research (https: / / www. fortiguard. com/ research)
    * Access / Cost: Free public research; commercial products separate
    * Relevance: Fortinet threat research.
    * Notes: Useful for attack patterns and indicators.
14. **Check Point Research**
    * Link(s): research.checkpoint.com (https: / / research. checkpoint. com/ )
    * Access / Cost: Free public blog; commercial products separate
    * Relevance: Threat research and vulnerability analysis.
    * Notes: Useful for campaign and exploit analysis.
15. **Elastic Security Labs**
    * Link(s): www.elastic.co/security-labs (https: / / www. elastic. co/ security- labs)
    * Access / Cost: Free public research; commercial products separate
    * Relevance: Detection engineering and threat research.
    * Notes: Useful for detection logic and adversary behavior.
16. **Sekoia Threat Intelligence**
    * Link(s): blog.sekoia.io (https: / / blog. sekoia. io/ )
    * Access / Cost: Free public blog; commercial threat intel products separate
    * Relevance: Threat intelligence research.
    * Notes: Useful for IOCs and campaign context.

### 12.2 Malware & IOC repositories

1. **MISP**
   * Link(s): www.misp-project.org (https: / / www. misp- project. org/ )
   * Access / Cost: Free / open-source; data sharing depends on communities/instances
   * Relevance: Threat intelligence sharing platform.
   * Notes: Useful for IOC correlation and sharing.
2. **AlienVault OTX**
   * Link(s): otx.alienvault.com (https: / / otx. alienvault. com/ )
   * Access / Cost: Free community access; commercial AT\&T Cybersecurity products separate
   * Relevance: Open threat exchange for IOCs.
   * Notes: Quality varies by pulse/source. Validate before enforcement.
3. **AbuseIPDB**
   * Link(s): www.abuseipdb.com (https: / / www. abuseipdb. com/ )
   * Access / Cost: Free tier / paid plans
   * Relevance: IP abuse reputation database.
   * Notes: Useful for IP enrichment; not vulnerability-specific.
4. **URLhaus**
   * Link(s): urlhaus.abuse.ch (https: / / urlhaus. abuse. ch/ )
   * Access / Cost: Free public
   * Relevance: Malware URL tracking.
   * Notes: Useful for IOC enrichment.
5. **MalwareBazaar**
   * Link(s): bazaar.abuse.ch (https: / / bazaar. abuse. ch/ )
   * Access / Cost: Free public
   * Relevance: Malware sample sharing.
   * Notes: Useful for malware family and hash enrichment.
6. **ThreatFox**
   * Link(s): threatfox.abuse.ch (https: / / threatfox. abuse. ch/ )
   * Access / Cost: Free public
   * Relevance: Threat intelligence indicators.
   * Notes: Useful for IOCs.
7. **Feodo Tracker**
   * Link(s): feodotracker.abuse.ch (https: / / feodotracker. abuse. ch/ )
   * Access / Cost: Free public
   * Relevance: Botnet C2 tracking.
   * Notes: Useful for malware infrastructure context.
8. **PhishTank**
   * Link(s): phishtank.org (https://phishtank.org/)
   * Access / Cost: Free community access; API/account may be required
   * Relevance: Phishing URL database.
   * Notes: Useful for phishing exposure and IOC enrichment.
9. **OpenPhish**
   * Link(s): openphish.com (https://openphish.com/)
   * Access / Cost: Free limited feed / paid premium feeds
   * Relevance: Phishing intelligence.
   * Notes: Commercial/community source; check terms.
10. **YARA**
    * Link(s): github.com/VirusTotal/yara (https: / / github. com/ VirusTotal/ yara)
    * Access / Cost: Free / open-source public GitHub repo
    * Relevance: Malware classification and pattern matching engine.
    * Notes: Useful for detection signatures.
11. **YARA-Rules**
    * Link(s): github.com/Yara-Rules/rules (https: / / github. com/ Yara- Rules/ rules)
    * Access / Cost: Free / open-source public GitHub repo
    * Relevance: Community YARA rules.
    * Notes: Validate rule quality before production use.
12. **SigmaHQ**
    * Link(s): github.com/SigmaHQ/sigma (https: / / github. com/ SigmaHQ/ sigma)
    * Access / Cost: Free / open-source public GitHub repo
    * Relevance: Generic SIEM detection rule format.
    * Notes: Useful for detection engineering.
13. **LOLBAS**
    * Link(s): lolbas-project.github.io (https: / / lolbas- project. github. io/ )
    * Access / Cost: Free public / open-source project
    * Relevance: Living-off-the-land binaries/scripts catalog.
    * Notes: Useful for attack behavior detection.
14. **GTFOBins**
    * Link(s): gtfobins.github.io (https: / / gtfobins. github. io/ )
    * Access / Cost: Free public / open-source project
    * Relevance: Unix binary abuse catalog.
    * Notes: Useful for privilege escalation and post-exploitation detection.
15. **Ransomware.live**
    * Link(s): www.ransomware.live (https: / / www. ransomware. live/ )
    * Access / Cost: Free public
    * Relevance: Ransomware group/leak-site tracking.
    * Notes: Useful for ransomware exploitation context and trend analysis.

## 13. Compliance, baseline configuration & exposure severity standards

These are not vulnerability feeds, but they help assess impact, control failure, configuration exposure, and exploitability in a given environment.

### 13.1 Security configuration & benchmarks

1. **CIS Benchmarks**
   * Link(s): www.cisecurity.org/cis-benchmarks (https: / / www. cisecurity. org/ cis- benchmarks)
   * Access / Cost: Free with registration for many PDFs; commercial CIS tools/membership available
   * Relevance: Secure configuration benchmarks.
   * Notes: Useful for environmental risk scoring and hardening validation.
2. **CIS Controls**
   * Link(s): www.cisecurity.org/controls (https: / / www. cisecurity. org/ controls)
   * Access / Cost: Free public
   * Relevance: Security control framework.
   * Notes: Useful for vulnerability management program alignment.
3. **NIST National Checklist Program**
   * Link(s): ncp.nist.gov (https: / / ncp. nist. gov/ )
   * Access / Cost: Free public
   * Relevance: Repository of security configuration checklists.
   * Notes: Useful for baseline configuration assessment.
4. **DISA STIGs**
   * Link(s): public.cyber.mil/stigs (https: / / public. cyber. mil/ stigs/ )
   * Access / Cost: Free public
   * Relevance: Security Technical Implementation Guides.
   * Notes: Important for government/defense compliance.
5. **OpenSCAP**
   * Link(s): www.open-scap.org (https: / / www. open- scap. org/ )
   * Access / Cost: Free / open-source
   * Relevance: SCAP tooling for compliance scanning.
   * Notes: Useful for host-level configuration scanning.
6. **SCAP Security Guide**
   * Link(s): github.com/ComplianceAsCode/content (https: / / github. com/ ComplianceAsCode/ content)
   * Access / Cost: Free / open-source public GitHub repo
   * Relevance: ComplianceAsCode content for SCAP profiles.
   * Notes: Useful for policy-as-code and baseline validation.

### 13.2 Cloud configuration posture

1. **Prowler - AWS / Azure / GCP / Kubernetes**
   * Link(s): github.com/prowler-cloud/prowler (https: / / github. com/ prowler- cloud/ prowler)
   * Access / Cost: Free / open-source core; commercial product available
   * Relevance: Cloud and Kubernetes security posture scanning.
   * Notes: Useful for environmental exposure and misconfiguration risk.
2. **CloudSplaining**
   * Link(s): github.com/salesforce/cloudsplaining (https: / / github. com/ salesforce/ cloudsplaining)
   * Access / Cost: Free / open-source public GitHub repo
   * Relevance: AWS IAM policy risk analysis.
   * Notes: Useful for blast-radius and privilege exposure context.
3. **ScoutSuite**
   * Link(s): github.com/nccgroup/ScoutSuite (https: / / github. com/ nccgroup/ ScoutSuite)
   * Access / Cost: Free / open-source public GitHub repo
   * Relevance: Multi-cloud security auditing.
   * Notes: Useful for cloud misconfiguration assessment.
4. **Steampipe mods**
   * Link(s): hub.steampipe.io/mods (https: / / hub. steampipe. io/ mods)
   * Access / Cost: Free/open-source mods; commercial Turbot/Steampipe offerings separate
   * Relevance: SQL-based cloud/security posture checks.
   * Notes: Useful for custom exposure queries.
5. **Cloud Custodian**
   * Link(s): cloudcustodian.io (https: / / cloudcustodian. io/ )
   * Access / Cost: Free / open-source
   * Relevance: Cloud governance and policy automation.
   * Notes: Useful for remediation automation.
6. **Kubernetes CIS benchmark**
   * Link(s): www.cisecurity.org/benchmark/kubernetes (https: / / www. cisecurity. org/ benchmark/ kubernetes)
   * Access / Cost: Free with registration for benchmark PDFs; commercial CIS tools/membership available
   * Relevance: Kubernetes configuration benchmark.
   * Notes: Useful for cluster hardening and exposure scoring.
7. **kube-bench**
   * Link(s): github.com/aquasecurity/kube-bench (https: / / github. com/ aquasecurity/ kube- bench)
   * Access / Cost: Free / open-source public GitHub repo
   * Relevance: Kubernetes CIS benchmark scanner.
   * Notes: Useful for automated cluster benchmark checks.
8. **kube-hunter**
   * Link(s): github.com/aquasecurity/kube-hunter (https: / / github. com/ aquasecurity/ kube- hunter)
   * Access / Cost: Free / open-source public GitHub repo
   * Relevance: Kubernetes penetration testing tool.
   * Notes: Use only in authorized environments.

## 14. Source-code, dependency, artifact & build-chain provenance

### 14.1 Source & artifact provenance

1. **SLSA**
   * Link(s): slsa.dev (https://slsa.dev/)
   * Access / Cost: Free / open standard
   * Relevance: Supply-chain Levels for Software Artifacts.
   * Notes: Useful for evaluating build integrity and provenance risk.
2. **Sigstore**
   * Link(s): www.sigstore.dev (https: / / www. sigstore. dev/ )
   * Access / Cost: Free / open-source public infrastructure
   * Relevance: Signing and verification for software artifacts.
   * Notes: Helps verify artifact integrity and publisher identity.
3. **Cosign**
   * Link(s): github.com/sigstore/cosign (https: / / github. com/ sigstore/ cosign)
   * Access / Cost: Free / open-source public GitHub repo
   * Relevance: Container/artifact signing tool.
   * Notes: Useful for verifying container image provenance.
4. **Rekor**
   * Link(s): docs.sigstore.dev/logging/overview (https: / / docs. sigstore. dev/ logging/ overview/ )
   * Access / Cost: Free public docs / public transparency log
   * Relevance: Transparency log for signed artifacts.
   * Notes: Useful for auditability and tamper detection.
5. **in-toto**
   * Link(s): in-toto.io (https: / / in- toto. io/ )
   * Access / Cost: Free / open-source
   * Relevance: Supply-chain integrity framework.
   * Notes: Useful for verifying build steps and provenance attestations.
6. **The Update Framework - TUF**
   * Link(s): theupdateframework.io (https: / / theupdateframework . io/ )
   * Access / Cost: Free / open-source
   * Relevance: Secure software update framework.
   * Notes: Useful for update-channel compromise resistance.
7. **SLSA GitHub generators**
   * Link(s): github.com/slsa-framework/slsa-github-generator (https: / / github. com/ slsa- framework/ slsa- github- generator)
   * Access / Cost: Free / open-source public GitHub repo
   * Relevance: GitHub-based SLSA provenance generators.
   * Notes: Useful for CI/CD provenance generation.

### 14.2 Dependency inventory & graphing

1. **deps.dev**
   * Link(s): deps.dev (https://deps.dev/)
   * Access / Cost: Free public
   * Relevance: Dependency metadata, transitive dependency graphing, and security signals.
   * Notes: Useful for OSS dependency context.
2. **GUAC**
   * Link(s): guac.sh (https://guac.sh/)
   * Access / Cost: Free public / open-source project
   * Relevance: Graph for software supply-chain metadata.
   * Notes: Useful for correlating SBOMs, vulnerabilities, provenance, and attestations.
3. **GUAC GitHub**
   * Link(s): github.com/guacsec/guac (https: / / github. com/ guacsec/ guac)
   * Access / Cost: Free / open-source public GitHub repo
   * Relevance: GUAC implementation repository.
   * Notes: Reference architecture for software supply-chain knowledge graphs.
4. **OpenSSF Scorecard**
   * Link(s): github.com/ossf/scorecard (https: / / github. com/ ossf/ scorecard)
   * Access / Cost: Free / open-source public GitHub repo
   * Relevance: Open-source project security practice scoring.
   * Notes: Useful as a dependency risk signal.
5. **OpenSSF Scorecard API**
   * Link(s): api.securityscorecards.dev (https: / / api. securityscorecards . dev/ )
   * Access / Cost: Free public API subject to service limits
   * Relevance: API for Scorecard results.
   * Notes: Scores are temporal; store retrieval time.
6. **Maven Central**
   * Link(s): central.sonatype.com (https: / / central. sonatype. com/ )
   * Access / Cost: Free public
   * Relevance: Maven package metadata.
   * Notes: Useful for Java dependency resolution.
7. **npm registry**
   * Link(s): registry.npmjs.org (https: / / registry. npmjs. org/ )
   * Access / Cost: Free public registry API
   * Relevance: npm package registry API endpoint.
   * Notes: Useful for package metadata and version resolution.
8. **PyPI JSON API**
   * Link(s): docs.pypi.org/api/json (https: / / docs. pypi. org/ api/ json/ )
   * Access / Cost: Free public API docs / public API
   * Relevance: PyPI JSON API documentation.
   * Notes: Useful for Python package metadata.
9. **crates.io API**
   * Link(s): crates.io/data-access (https: / / crates. io/ data- access)
   * Access / Cost: Free public API subject to policy/rate limits
   * Relevance: crates.io data access documentation.
   * Notes: Useful for Rust package metadata.
10. **Go module proxy**
    * Link(s): proxy.golang.org (https: / / proxy. golang. org/ )
    * Access / Cost: Free public
    * Relevance: Go module proxy.
    * Notes: Useful for Go module version metadata.

## 15. Practical priority hierarchy for ingestion

### 15.1 Tier 0 - identifiers & inventory

1. **SBOM**
   * Link(s): cyclonedx.org/specification/overview (https: / / cyclonedx. org/ specification/ overview/ ), spdx.dev/specifications (https: / / spdx. dev/ specifications/ )
   * Access / Cost: Free / open standards
   * Relevance: Inventory foundation for matching components to vulnerabilities.
   * Notes: Without accurate inventory, vulnerability matching is incomplete or noisy.
2. **Package identity**
   * Link(s): csrc.nist.gov/projects/software-identification-swid (https: / / csrc. nist. gov/ projects/ software- identification- swid), github.com/package-url/purl-spec (https: / / github. com/ package- url/ purl- spec), nvd.nist.gov/products/cpe (https: / / nvd. nist. gov/ products/ cpe)
   * Access / Cost: Free public / open standards
   * Relevance: Component identity across package, product, and installed software domains.
   * Notes: Use PURL for packages, CPE for products/platforms, SWID for installed software identity.
3. **Asset exposure**
   * Link(s): search.censys.io (https: / / search. censys. io/ ), www.shodan.io (https: / / www. shodan. io/ )
   * Access / Cost: Free tiers / paid plans
   * Relevance: Determines whether vulnerable assets are externally reachable.
   * Notes: Combine with internal CMDB, cloud inventory, and authenticated scans.
4. **Artifact provenance**
   * Link(s): in-toto.io (https: / / in- toto. io/ ), slsa.dev (https://slsa.dev/), www.sigstore.dev (https: / / www. sigstore. dev/ )
   * Access / Cost: Free / open-source / open standards
   * Relevance: Validates build-chain integrity and artifact authenticity.
   * Notes: Helps distinguish vulnerable dependency risk from supply-chain tampering risk.

### 15.2 Tier 1 - canonical vulnerability records

1. **CVE List v5**
   * Link(s): github.com/CVEProject/cvelistV5 (https: / / github. com/ CVEProject/ cvelistV5)
   * Access / Cost: Free public GitHub repo
   * Relevance: Canonical CVE record mirror.
   * Notes: Core identity source.
2. **CVE schema**
   * Link(s): github.com/CVEProject/cve-schema (https: / / github. com/ CVEProject/ cve- schema)
   * Access / Cost: Free public GitHub repo
   * Relevance: Schema validation for CVE records.
   * Notes: Use for parser correctness.
3. **CVE Services API**
   * Link(s): cveawg.mitre.org/api-docs (https: / / cveawg. mitre. org/ api- docs/ )
   * Access / Cost: Free public docs; CNA functions may require role/account
   * Relevance: Direct programmatic CVE lookup.
   * Notes: Useful for targeted CVE access.
4. **NVD CVE API**
   * Link(s): nvd.nist.gov/developers/vulnerabilities (https: / / nvd. nist. gov/ developers/ vulnerabilities)
   * Access / Cost: Free public; optional free API key for higher rate limits
   * Relevance: CVSS/CPE/CWE/reference enrichment.
   * Notes: Core product matching source.
5. **NVD CPE API**
   * Link(s): nvd.nist.gov/developers/products (https: / / nvd. nist. gov/ developers/ products)
   * Access / Cost: Free public; optional free API key for higher rate limits
   * Relevance: CPE dictionary and product/platform matching.
   * Notes: Important for product-level mapping.
6. **NVD data feeds**
   * Link(s): nvd.nist.gov/vuln/data-feeds (https: / / nvd. nist. gov/ vuln/ data- feeds)
   * Access / Cost: Free public
   * Relevance: Bulk NVD feed access.
   * Notes: Useful for bootstrapping.
7. **CISA Vulnrichment**
   * Link(s): github.com/cisagov/vulnrichment (https: / / github. com/ cisagov/ vulnrichment)
   * Access / Cost: Free public GitHub repo
   * Relevance: CISA ADP enrichment and SSVC data.
   * Notes: Prioritization enrichment.

### 15.3 Tier 2 - package/ecosystem vulnerability records

1. **OSV full database**
   * Link(s): google.github.io/osv.dev/data/#full-database-download (https: / / google. github. io/ osv. dev/ data/ # full- database- download)
   * Access / Cost: Free public
   * Relevance: Local mirror of OSS vulnerability records.
   * Notes: Best for high-volume package matching.
2. **OSV API**
   * Link(s): google.github.io/osv.dev/post-v1-query (https: / / google. github. io/ osv. dev/ post- v1- query/ )
   * Access / Cost: Free public API
   * Relevance: Online vulnerability lookup by package/version/commit/ID.
   * Notes: Good for targeted lookups.
3. **GitHub Advisory Database**
   * Link(s): github.com/advisories (https: / / github. com/ advisories)
   * Access / Cost: Free public
   * Relevance: GHSA/CVE/malware advisory records.
   * Notes: Preserve aliases.
4. **GitHub Advisory Database repo**
   * Link(s): github.com/github/advisory-database (https: / / github. com/ github/ advisory- database)
   * Access / Cost: Free / open-source public GitHub repo
   * Relevance: Raw advisory data for local ingestion.
   * Notes: Useful for mirroring.
5. **Go vuln DB**
   * Link(s): vuln.go.dev (https: / / vuln. go. dev/ )
   * Access / Cost: Free public
   * Relevance: Official Go vulnerability database.
   * Notes: Go-specific affectedness.
6. **RustSec**
   * Link(s): rustsec.org (https: / / rustsec. org/ )
   * Access / Cost: Free public / open-source ecosystem
   * Relevance: Rust advisory ecosystem.
   * Notes: Rust crate-specific advisories.
7. **PyPA advisory DB**
   * Link(s): github.com/pypa/advisory-database (https: / / github. com/ pypa/ advisory- database)
   * Access / Cost: Free public GitHub repo
   * Relevance: Python advisory source.
   * Notes: Python/PyPI coverage.
8. **FriendsOfPHP**
   * Link(s): github.com/FriendsOfPHP/security-advisories (https: / / github. com/ FriendsOfPHP/ security- advisories)
   * Access / Cost: Free public GitHub repo
   * Relevance: PHP Composer advisories.
   * Notes: Composer-specific.
9. **RubySec**
   * Link(s): github.com/rubysec/ruby-advisory-db (https: / / github. com/ rubysec/ ruby- advisory- db)
   * Access / Cost: Free public GitHub repo
   * Relevance: RubyGems advisories.
   * Notes: Ruby ecosystem.
10. **OSS Index**
    * Link(s): ossindex.sonatype.org (https: / / ossindex. sonatype. org/ )
    * Access / Cost: Free tier / API terms; commercial Sonatype products separate
    * Relevance: Package vulnerability intelligence.
    * Notes: Secondary enrichment.
11. **Packagist API**
    * Link(s): packagist.org/apidoc#list-security-advisories (https: / / packagist. org/ apidoc# list- security- advisories)
    * Access / Cost: Free public API docs / public API
    * Relevance: Composer advisory API.
    * Notes: Direct PHP ecosystem source.

### 15.4 Tier 3 - affectedness, distro & vendor truth

1. **Red Hat Security Data**
   * Link(s): access.redhat.com/security/data (https: / / access. redhat. com/ security/ data)
   * Access / Cost: Free public data; support content may require subscription
   * Relevance: RHEL affectedness, CSAF/VEX, OSV, OVAL.
   * Notes: Backport-aware.
2. **Debian Security Tracker**
   * Link(s): security-tracker.debian.org (https: / / security- tracker. debian. org/ )
   * Access / Cost: Free public
   * Relevance: Debian package affectedness.
   * Notes: Backport-aware.
3. **Ubuntu OVAL / OSV / OpenVEX**
   * Link(s): github.com/canonical/ubuntu-security-notices (https: / / github. com/ canonical/ ubuntu- security- notices), ubuntu.com/security/oval (https: / / ubuntu. com/ security/ oval), ubuntu.com/security/vex (https: / / ubuntu. com/ security/ vex)
   * Access / Cost: Free public
   * Relevance: Ubuntu package affectedness and VEX status.
   * Notes: Use release-specific data.
4. **Alpine SecDB**
   * Link(s): secdb.alpinelinux.org (https: / / secdb. alpinelinux. org/ )
   * Access / Cost: Free public
   * Relevance: Alpine package vulnerability data.
   * Notes: Container-critical.
5. **SUSE CSAF / OVAL**
   * Link(s): www.suse.com/support/security/csaf (https: / / www. suse. com/ support/ security/ csaf/ ), www.suse.com/support/security/oval (https: / / www. suse. com/ support/ security/ oval/ )
   * Access / Cost: Free public
   * Relevance: SUSE vendor affectedness and scanner data.
   * Notes: Use machine-readable formats where possible.
6. **Oracle Linux OVAL / errata**
   * Link(s): linux.oracle.com/errata (https: / / linux. oracle. com/ errata/ ), linux.oracle.com/security/oval (https: / / linux. oracle. com/ security/ oval/ )
   * Access / Cost: Free public
   * Relevance: Oracle Linux patch and OVAL data.
   * Notes: Oracle Linux-specific.
7. **Amazon Linux ALAS**
   * Link(s): alas.aws.amazon.com (https: / / alas. aws. amazon. com/ )
   * Access / Cost: Free public
   * Relevance: Amazon Linux advisories.
   * Notes: Separate AL2 and AL2023.
8. **AlmaLinux / Rocky / Fedora / Arch / Gentoo**
   * Link(s): bodhi.fedoraproject.org/updates/?type=security (https: / / bodhi. fedoraproject. org/ updates/ ? type= security), errata.almalinux.org (https: / / errata. almalinux. org/ ), errata.build.resf.org (https: / / errata. build. resf. org/ ), security.archlinux.org (https: / / security. archlinux. org/ ), security.gentoo.org/glsa (https: / / security. gentoo. org/ glsa/ )
   * Access / Cost: Free public
   * Relevance: Additional Linux distribution affectedness sources.
   * Notes: Distro semantics vary substantially.
9. **Wolfi / Chainguard**
   * Link(s): github.com/wolfi-dev/advisories (https: / / github. com/ wolfi- dev/ advisories), packages.cgr.dev/chainguard/security.json (https: / / packages. cgr. dev/ chainguard/ security. json), packages.wolfi.dev/os/security.json (https: / / packages. wolfi. dev/ os/ security. json)
   * Access / Cost: Wolfi free public; Chainguard feed may relate to commercial product scope
   * Relevance: Container-first package vulnerability feeds.
   * Notes: Useful for minimal images.
10. **Vendor advisories**
    * Link(s): helpx.adobe.com/security.html (https: / / helpx. adobe. com/ security. html), msrc.microsoft.com/update-guide (https: / / msrc. microsoft. com/ update- guide), security.paloaltonetworks.com (https: / / security. paloaltonetworks. com/ ), sec.cloudapps.cisco.com/security/center/publicationListing.x (https: / / sec. cloudapps. cisco. com/ security/ center/ publicationListing . x), support.apple.com/en-us/100100 (https: / / support. apple. com/ en- us/ 100100), support.broadcom.com/web/ecx/security-advisory (https: / / support. broadcom. com/ web/ ecx/ security- advisory), support.citrix.com/securitybulletins (https: / / support. citrix. com/ securitybulletins), support.sap.com/en/my-support/knowledge-base/security-notes-news.html (https: / / support. sap. com/ en/ my- support/ knowledge- base/ security- notes- news. html), www.atlassian.com/trust/security/advisories (https: / / www. atlassian. com/ trust/ security/ advisories), www.fortiguard.com/psirt (https: / / www. fortiguard. com/ psirt), www.ivanti.com/resources/v/doc/ivi/2629/0e3e2be1e66d (https: / / www. ivanti. com/ resources/ v/ doc/ ivi/ 2629/ 0e3e2be1e66d), www.oracle.com/security-alerts (https: / / www. oracle. com/ security- alerts/ )
    * Access / Cost: Mostly free public advisories; some vendors require support accounts/subscriptions for full details or downloads
    * Relevance: Vendor truth for affected products, fixed versions, mitigations, and exploitation notes.
    * Notes: Often most authoritative for product affectedness. Access, formatting, and update latency vary.

### 15.5 Tier 4 - severity & prioritization

1. **CVSS v3.1/v4.0**
   * Link(s): www.first.org/cvss/v3.1/specification-document (https: / / www. first. org/ cvss/ v3. 1/ specification- document), www.first.org/cvss/v4.0/specification-document (https: / / www. first. org/ cvss/ v4. 0/ specification- document)
   * Access / Cost: Free public
   * Relevance: Standard severity scoring.
   * Notes: Severity is not exploit likelihood.
2. **EPSS**
   * Link(s): www.first.org/epss (https: / / www. first. org/ epss/ )
   * Access / Cost: Free public data/API
   * Relevance: Exploit likelihood prediction.
   * Notes: Temporal; store score date.
3. **KEV**
   * Link(s): www.cisa.gov/sites/default/files/feeds/known\_exploited\_vulnerabilities.json (https: / / www. cisa. gov/ sites/ default/ files/ feeds/ known\_ exploited\_ vulnerabilities. json)
   * Access / Cost: Free public feed
   * Relevance: Known exploited vulnerability signal.
   * Notes: Strong but incomplete exploited-in-the-wild signal.
4. **SSVC**
   * Link(s): github.com/CERTCC/SSVC (https: / / github. com/ CERTCC/ SSVC), www.cisa.gov/stakeholder-specific-vulnerability-categorization-ssvc (https: / / www. cisa. gov/ stakeholder- specific- vulnerability- categorization- ssvc)
   * Access / Cost: Free public / open-source
   * Relevance: Decision support for remediation urgency.
   * Notes: Requires environmental/mission context.
5. **CISA Vulnrichment**
   * Link(s): github.com/cisagov/vulnrichment (https: / / github. com/ cisagov/ vulnrichment)
   * Access / Cost: Free public GitHub repo
   * Relevance: SSVC and enrichment data.
   * Notes: Coverage varies.
6. **Vendor exploited-in-the-wild flags**
   * Link(s): msrc.microsoft.com/update-guide (https: / / msrc. microsoft. com/ update- guide), support.apple.com/en-us/100100 (https: / / support. apple. com/ en- us/ 100100), www.oracle.com/security-alerts (https: / / www. oracle. com/ security- alerts/ )
   * Access / Cost: Free public, though product support details may vary
   * Relevance: Vendor-provided exploitation status.
   * Notes: Often product-specific and time-sensitive.
7. **Patch availability & fixed-version feeds**
   * Link(s): access.redhat.com/security/data (https: / / access. redhat. com/ security/ data), github.com/canonical/ubuntu-security-notices (https: / / github. com/ canonical/ ubuntu- security- notices), security-tracker.debian.org/tracker/data/json (https: / / security- tracker. debian. org/ tracker/ data/ json)
   * Access / Cost: Free public data; some vendor support may require subscription
   * Relevance: Determines whether remediation exists.
   * Notes: Patch availability varies by distro/release/product.
8. **Environmental context**
   * Link(s): docs.greynoise.io (https: / / docs. greynoise. io/ ), search.censys.io (https: / / search. censys. io/ ), www.shodan.io (https: / / www. shodan. io/ )
   * Access / Cost: Free tiers / paid plans
   * Relevance: Internet exposure, asset criticality, privilege boundary, and data sensitivity determine real impact.
   * Notes: Must be joined with internal asset inventory and controls.

### 15.6 Tier 5 - exploitability & weaponization

1. **Exploit-DB**
   * Link(s): www.exploit-db.com (https: / / www. exploit- db. com/ )
   * Access / Cost: Free public
   * Relevance: Public exploit availability.
   * Notes: Verify target versions and exploit reliability.
2. **Metasploit modules**
   * Link(s): github.com/rapid7/metasploit-framework/tree/master/modules/exploits (https: / / github. com/ rapid7/ metasploit- framework/ tree/ master/ modules/ exploits)
   * Access / Cost: Free / open-source
   * Relevance: Weaponized exploit modules.
   * Notes: Strong operationalization signal.
3. **Packet Storm**
   * Link(s): packetstormsecurity.com/files/tags/exploit (https: / / packetstormsecurit y. com/ files/ tags/ exploit/ )
   * Access / Cost: Free public
   * Relevance: Exploit archive.
   * Notes: Metadata quality varies.
4. **Project Zero**
   * Link(s): googleprojectzero.blogspot.com (https: / / googleprojectzero. blogspot. com/ ), project-zero.issues.chromium.org (https: / / project- zero. issues. chromium. org/ )
   * Access / Cost: Free public; some issues may be restricted pre-disclosure
   * Relevance: Root-cause and exploitability research.
   * Notes: High-quality technical details.
5. **CERT/CC VU notes**
   * Link(s): www.kb.cert.org/vuls (https: / / www. kb. cert. org/ vuls/ )
   * Access / Cost: Free public
   * Relevance: Coordinated disclosure and affected vendor context.
   * Notes: Useful for ecosystem-wide vulns.
6. **Rapid7 AttackerKB**
   * Link(s): attackerkb.com (https: / / attackerkb. com/ )
   * Access / Cost: Free public content; commercial Rapid7 offerings separate
   * Relevance: Attacker value and exploitability context.
   * Notes: Secondary enrichment.
7. **GreyNoise**
   * Link(s): docs.greynoise.io (https: / / docs. greynoise. io/ ), viz.greynoise.io (https: / / viz. greynoise. io/ )
   * Access / Cost: Free tier / paid plans
   * Relevance: Internet exploitation/scanning telemetry.
   * Notes: Distinguishes noise from activity.
8. **Shadowserver**
   * Link(s): dashboard.shadowserver.org (https: / / dashboard. shadowserver. org/ ), www.shadowserver.org (https: / / www. shadowserver. org/ )
   * Access / Cost: Free for eligible organizations; registration may be required
   * Relevance: Exposure and threat telemetry.
   * Notes: Access and reporting terms vary.
9. **Nuclei templates**
   * Link(s): github.com/projectdiscovery/nuclei-templates (https: / / github. com/ projectdiscovery/ nuclei- templates)
   * Access / Cost: Free / open-source
   * Relevance: Detection templates for exposed vulnerabilities.
   * Notes: Template presence is not proof of exposure.
10. **Vendor emergency advisories**
    * Link(s): www.cisa.gov/cybersecurity-advisories (https: / / www. cisa. gov/ cybersecurity- advisories), www.fortiguard.com/psirt (https: / / www. fortiguard. com/ psirt), www.ivanti.com/resources/v/doc/ivi/2629/0e3e2be1e66d (https: / / www. ivanti. com/ resources/ v/ doc/ ivi/ 2629/ 0e3e2be1e66d)
    * Access / Cost: Free public
    * Relevance: Emergency/active exploitation guidance.
    * Notes: Highly time-sensitive; monitor frequently.

### 15.7 Tier 6 - weakness, attack-pattern & AI context

1. **CWE**
   * Link(s): cwe.mitre.org (https: / / cwe. mitre. org/ )
   * Access / Cost: Free public
   * Relevance: Weakness taxonomy.
   * Notes: CVE-to-CWE mappings can be broad or missing.
2. **CAPEC**
   * Link(s): capec.mitre.org (https: / / capec. mitre. org/ )
   * Access / Cost: Free public
   * Relevance: Attack-pattern taxonomy.
   * Notes: Maps weaknesses to attack patterns.
3. **ATT\&CK Enterprise**
   * Link(s): attack.mitre.org/matrices/enterprise (https: / / attack. mitre. org/ matrices/ enterprise/ )
   * Access / Cost: Free public
   * Relevance: Enterprise adversary behavior taxonomy.
   * Notes: More post-exploitation than CVE-specific.
4. **ATT\&CK STIX**
   * Link(s): github.com/mitre-attack/attack-stix-data (https: / / github. com/ mitre- attack/ attack- stix- data)
   * Access / Cost: Free public GitHub repo
   * Relevance: Machine-readable ATT\&CK data.
   * Notes: Best for ingestion.
5. **MITRE CTI repo**
   * Link(s): github.com/mitre/cti (https: / / github. com/ mitre/ cti)
   * Access / Cost: Free public GitHub repo
   * Relevance: MITRE STIX data repository.
   * Notes: Useful for CTI graphing.
6. **MITRE ATLAS**
   * Link(s): atlas.mitre.org (https: / / atlas. mitre. org/ )
   * Access / Cost: Free public
   * Relevance: AI adversary tactics and techniques.
   * Notes: Directly relevant to AI/ML systems.
7. **OWASP LLM Top 10**
   * Link(s): owasp.org/www-project-top-10-for-large-language-model-applications (https: / / owasp. org/ www- project- top- 10- for- large- language- model- applications/ )
   * Access / Cost: Free public / open community
   * Relevance: LLM application vulnerability taxonomy.
   * Notes: Good for AI appsec.
8. **OWASP ML Security Top 10**
   * Link(s): owasp.org/www-project-machine-learning-security-top-10 (https: / / owasp. org/ www- project- machine- learning- security- top- 10/ )
   * Access / Cost: Free public / open community
   * Relevance: ML security risk taxonomy.
   * Notes: Complements ATLAS.
9. **NIST AI RMF & NIST AI 600-1**
   * Link(s): nvlpubs.nist.gov/nistpubs/ai/NIST.AI.100-1.pdf (https: / / nvlpubs. nist. gov/ nistpubs/ ai/ NIST. AI. 100- 1. pdf), www.nist.gov/publications/artificial-intelligence-risk-management-framework-generative-artificial-intelligence (https: / / www. nist. gov/ publications/ artificial- intelligence- risk- management- framework- generative- artificial- intelligence)
   * Access / Cost: Free public
   * Relevance: AI risk management and GenAI risk profile.
   * Notes: Governance/risk context, not vuln feed.

### 15.8 Tier 7 - detection engineering & validation

1. **CodeQL**
   * Link(s): codeql.github.com (https: / / codeql. github. com/ )
   * Access / Cost: Free for many open-source uses; commercial GitHub Advanced Security for many enterprise/private workflows
   * Relevance: Semantic code vulnerability detection.
   * Notes: Strong for variant analysis.
2. **Semgrep**
   * Link(s): semgrep.dev (https: / / semgrep. dev/ )
   * Access / Cost: Free/open-source CLI; commercial products available
   * Relevance: Pattern-based static analysis.
   * Notes: Fast custom rules.
3. **Joern**
   * Link(s): joern.io (https://joern.io/)
   * Access / Cost: Free / open-source
   * Relevance: Code property graph analysis.
   * Notes: Useful for research and advanced detection.
4. **Infer**
   * Link(s): fbinfer.com (https: / / fbinfer. com/ )
   * Access / Cost: Free / open-source
   * Relevance: Static analysis engine.
   * Notes: Good for specific bug classes.
5. **Sonar rules**
   * Link(s): rules.sonarsource.com (https: / / rules. sonarsource. com/ )
   * Access / Cost: Free public catalog; commercial Sonar products available
   * Relevance: Security/code quality rule catalog.
   * Notes: Useful for rule taxonomy mapping.
6. **Nuclei templates**
   * Link(s): github.com/projectdiscovery/nuclei-templates (https: / / github. com/ projectdiscovery/ nuclei- templates)
   * Access / Cost: Free / open-source
   * Relevance: DAST/exposure templates.
   * Notes: Template quality varies.
7. **OSS-Fuzz**
   * Link(s): google.github.io/oss-fuzz (https: / / google. github. io/ oss- fuzz/ )
   * Access / Cost: Free for eligible open-source projects
   * Relevance: Continuous fuzzing.
   * Notes: Useful for discovery and OSV-linked vulns.
8. **SARD / Juliet**
   * Link(s): samate.nist.gov/SARD (https: / / samate. nist. gov/ SARD/ ), samate.nist.gov/SARD/test-suites/112 (https: / / samate. nist. gov/ SARD/ test- suites/ 112)
   * Access / Cost: Free public
   * Relevance: Test suites for vulnerability detection.
   * Notes: Useful for evaluation; not production vulnerability feed.
9. **Vulnerability datasets**
   * Link(s): github.com/DLVulDet/PrimeVul (https: / / github. com/ DLVulDet/ PrimeVul), github.com/Icyrockton/MegaVul (https: / / github. com/ Icyrockton/ MegaVul), github.com/ZeoVan/MSR\_20\_Code\_vulnerability\_CSV\_Dataset (https: / / github. com/ ZeoVan/ MSR\_ 20\_ Code\_ vulnerability\_ CSV\_ Dataset), github.com/secureIT-project/CVEfixes (https: / / github. com/ secureIT- project/ CVEfixes), github.com/tuhh-softsec/vul4j (https: / / github. com/ tuhh- softsec/ vul4j), github.com/wagner-group/diversevul (https: / / github. com/ wagner- group/ diversevul), sites.google.com/view/devign (https: / / sites. google. com/ view/ devign)
   * Access / Cost: Mostly free public research datasets; verify license individually
   * Relevance: ML/research datasets for vulnerability detection.
   * Notes: Validate labels, leakage, deduplication, and licensing.

## 16. Recommended canonical data model coverage

A complete vulnerability impact system should be able to ingest or derive the following fields.

### 16.1 Vulnerability identity

1. **CVE ID**
   * Link(s): github.com/CVEProject/cvelistV5 (https: / / github. com/ CVEProject/ cvelistV5), www.cve.org (https: / / www. cve. org/ )
   * Access / Cost: Free public
   * Relevance: Canonical vulnerability identifier.
   * Notes: Not all advisories have CVEs immediately.
2. **GHSA ID**
   * Link(s): github.com/advisories (https: / / github. com/ advisories)
   * Access / Cost: Free public
   * Relevance: GitHub Security Advisory identifier.
   * Notes: May exist without CVE.
3. **OSV ID**
   * Link(s): osv.dev (https://osv.dev/)
   * Access / Cost: Free public
   * Relevance: OSV vulnerability identifier.
   * Notes: Links package-specific affectedness and aliases.
4. **Vendor advisory ID**
   * Link(s): msrc.microsoft.com/update-guide (https: / / msrc. microsoft. com/ update- guide), www.oracle.com/security-alerts (https: / / www. oracle. com/ security- alerts/ )
   * Access / Cost: Mostly free public; some support details may require entitlement
   * Relevance: Vendor-specific advisory identifier.
   * Notes: Often most authoritative for product-specific truth.
5. **CWE ID**
   * Link(s): cwe.mitre.org (https: / / cwe. mitre. org/ )
   * Access / Cost: Free public
   * Relevance: Weakness class identifier.
   * Notes: Quality of mapping varies.
6. **CAPEC ID**
   * Link(s): capec.mitre.org (https: / / capec. mitre. org/ )
   * Access / Cost: Free public
   * Relevance: Attack-pattern identifier.
   * Notes: Useful for attack mechanism mapping.
7. **ATT\&CK technique ID**
   * Link(s): attack.mitre.org/matrices/enterprise (https: / / attack. mitre. org/ matrices/ enterprise/ )
   * Access / Cost: Free public
   * Relevance: Adversary technique identifier.
   * Notes: Useful for detection/response mapping.
8. **ATLAS technique ID**
   * Link(s): atlas.mitre.org/techniques (https: / / atlas. mitre. org/ techniques)
   * Access / Cost: Free public
   * Relevance: AI/ML adversary technique identifier.
   * Notes: Relevant for AI systems.
9. **Alias graph**
   * Link(s): github.com/CVEProject/cvelistV5 (https: / / github. com/ CVEProject/ cvelistV5), github.com/advisories (https: / / github. com/ advisories), osv.dev (https://osv.dev/)
   * Access / Cost: Free public
   * Relevance: Maps CVE/GHSA/OSV/vendor aliases.
   * Notes: Crucial for deduplication and correlation.

### 16.2 Affectedness

1. **Product name**
   * Link(s): nvd.nist.gov/products/cpe (https: / / nvd. nist. gov/ products/ cpe)
   * Access / Cost: Free public
   * Relevance: Identifies vulnerable products.
   * Notes: Normalize against CPE/PURL/vendor data.
2. **Vendor**
   * Link(s): www.cve.org (https: / / www. cve. org/ )
   * Access / Cost: Free public
   * Relevance: Vendor/product attribution.
   * Notes: Vendor naming can differ across sources.
3. **CPE**
   * Link(s): nvd.nist.gov/developers/products (https: / / nvd. nist. gov/ developers/ products)
   * Access / Cost: Free public; optional free API key for higher rate limits
   * Relevance: Product/platform matching.
   * Notes: Imprecise for many OSS packages.
4. **PURL**
   * Link(s): github.com/package-url/purl-spec (https: / / github. com/ package- url/ purl- spec)
   * Access / Cost: Free / open-source
   * Relevance: Package identity.
   * Notes: Prefer for package ecosystem matching.
5. **Package ecosystem**
   * Link(s): osv.dev/list (https: / / osv. dev/ list)
   * Access / Cost: Free public
   * Relevance: Defines package namespace and version rules.
   * Notes: Version semantics are ecosystem-specific.
6. **Package name**
   * Link(s): deps.dev (https://deps.dev/)
   * Access / Cost: Free public
   * Relevance: Dependency identity.
   * Notes: Normalize casing and namespace rules.
7. **Affected version range**
   * Link(s): ossf.github.io/osv-schema (https: / / ossf. github. io/ osv- schema/ )
   * Access / Cost: Free public / open-source
   * Relevance: Expresses vulnerable versions.
   * Notes: Range interpretation must respect ecosystem semantics.
8. **Fixed version**
   * Link(s): github.com/advisories (https: / / github. com/ advisories), osv.dev (https://osv.dev/)
   * Access / Cost: Free public
   * Relevance: Remediation target.
   * Notes: Distro fixed versions may differ due to backports.
9. **Introduced version / commit**
   * Link(s): ossf.github.io/osv-schema (https: / / ossf. github. io/ osv- schema/ )
   * Access / Cost: Free public / open-source
   * Relevance: Determines when vulnerability entered codebase.
   * Notes: Not always available.
10. **Last affected version**
    * Link(s): ossf.github.io/osv-schema (https: / / ossf. github. io/ osv- schema/ )
    * Access / Cost: Free public / open-source
    * Relevance: Helps determine affected version bounds.
    * Notes: Validate with vendor feeds.
11. **Backport status**
    * Link(s): access.redhat.com/security/data (https: / / access. redhat. com/ security/ data), security-tracker.debian.org (https: / / security- tracker. debian. org/ ), ubuntu.com/security/cves (https: / / ubuntu. com/ security/ cves)
    * Access / Cost: Mostly free public; some Red Hat support details may require subscription
    * Relevance: Determines if a distro package is patched despite upstream version appearing vulnerable.
    * Notes: Essential for reducing false positives.
12. **VEX status**
    * Link(s): github.com/openvex/spec (https: / / github. com/ openvex/ spec), www.csaf.io (https: / / www. csaf. io/ )
    * Access / Cost: Free / open-source standards
    * Relevance: Represents affected, not affected, fixed, or under investigation.
    * Notes: Preserve justification and author provenance.
13. **Justification for not affected**
    * Link(s): github.com/openvex/spec (https: / / github. com/ openvex/ spec)
    * Access / Cost: Free / open-source
    * Relevance: Explains why a product is not affected.
    * Notes: Key for trust and auditability.
14. **Distro/package release channel**
    * Link(s): packages.fedoraproject.org (https: / / packages. fedoraproject. org/ ), pkgs.alpinelinux.org/packages (https: / / pkgs. alpinelinux. org/ packages)
    * Access / Cost: Free public
    * Relevance: Tracks package release stream.
    * Notes: Channel differences can affect fix availability.

### 16.3 Severity & exploitability

1. **CVSS v2/v3/v4 vector**
   * Link(s): www.first.org/cvss (https: / / www. first. org/ cvss/ )
   * Access / Cost: Free public
   * Relevance: Structured severity vector.
   * Notes: Use vector, not only numeric score.
2. **CVSS base/temporal/environmental score**
   * Link(s): nvd.nist.gov/vuln-metrics/cvss (https: / / nvd. nist. gov/ vuln- metrics/ cvss)
   * Access / Cost: Free public
   * Relevance: Severity scoring.
   * Notes: Environmental score should be computed with local context.
3. **EPSS score**
   * Link(s): www.first.org/epss (https: / / www. first. org/ epss/ )
   * Access / Cost: Free public data/API
   * Relevance: Exploit likelihood.
   * Notes: Temporal; store score date.
4. **EPSS percentile**
   * Link(s): www.first.org/epss/data\_stats (https: / / www. first. org/ epss/ data\_ stats)
   * Access / Cost: Free public data downloads
   * Relevance: Relative exploit-likelihood ranking.
   * Notes: Useful for prioritization across backlog.
5. **KEV membership**
   * Link(s): www.cisa.gov/sites/default/files/feeds/known\_exploited\_vulnerabilities.json (https: / / www. cisa. gov/ sites/ default/ files/ feeds/ known\_ exploited\_ vulnerabilities. json)
   * Access / Cost: Free public feed
   * Relevance: Known exploited vulnerability marker.
   * Notes: Strong exploitation evidence.
6. **KEV date added**
   * Link(s): www.cisa.gov/sites/default/files/feeds/known\_exploited\_vulnerabilities.json (https: / / www. cisa. gov/ sites/ default/ files/ feeds/ known\_ exploited\_ vulnerabilities. json)
   * Access / Cost: Free public feed
   * Relevance: Temporal exploitation/prioritization signal.
   * Notes: Use for SLA and trend analysis.
7. **Known ransomware usage**
   * Link(s): www.ransomware.live (https: / / www. ransomware. live/ )
   * Access / Cost: Free public
   * Relevance: Ransomware exploitation context.
   * Notes: Attribution and mapping quality vary.
8. **Public exploit available**
   * Link(s): www.exploit-db.com (https: / / www. exploit- db. com/ )
   * Access / Cost: Free public
   * Relevance: PoC/exploit availability.
   * Notes: Verify reliability and version applicability.
9. **Metasploit module available**
   * Link(s): github.com/rapid7/metasploit-framework/tree/master/modules/exploits (https: / / github. com/ rapid7/ metasploit- framework/ tree/ master/ modules/ exploits)
   * Access / Cost: Free / open-source
   * Relevance: Weaponized exploit implementation.
   * Notes: Stronger than generic PoC signal.
10. **Nuclei template available**
    * Link(s): github.com/projectdiscovery/nuclei-templates (https: / / github. com/ projectdiscovery/ nuclei- templates)
    * Access / Cost: Free / open-source
    * Relevance: Detection template availability.
    * Notes: Indicates detectable exposure, not confirmed vulnerability.
11. **GreyNoise observed scanning**
    * Link(s): viz.greynoise.io (https: / / viz. greynoise. io/ )
    * Access / Cost: Free tier / paid plans
    * Relevance: Internet scanning/exploitation telemetry.
    * Notes: Helps prioritize exposed services.
12. **Shadowserver observed exposure**
    * Link(s): dashboard.shadowserver.org (https: / / dashboard. shadowserver. org/ )
    * Access / Cost: Free for eligible organizations; registration may be required
    * Relevance: Internet-scale exposure telemetry.
    * Notes: Access may require registration/eligibility.
13. **CISA SSVC decision points**
    * Link(s): github.com/cisagov/vulnrichment (https: / / github. com/ cisagov/ vulnrichment)
    * Access / Cost: Free public GitHub repo
    * Relevance: Decision support enrichment.
    * Notes: Useful for prioritization workflows.
14. **Vendor exploitation status**
    * Link(s): msrc.microsoft.com/update-guide (https: / / msrc. microsoft. com/ update- guide), security.paloaltonetworks.com (https: / / security. paloaltonetworks. com/ ), support.apple.com/en-us/100100 (https: / / support. apple. com/ en- us/ 100100)
    * Access / Cost: Free public
    * Relevance: Vendor-provided exploitation notes.
    * Notes: Time-sensitive and product-specific.
15. **Patch availability**
    * Link(s): access.redhat.com/security/data (https: / / access. redhat. com/ security/ data), security-tracker.debian.org (https: / / security- tracker. debian. org/ ), ubuntu.com/security/notices (https: / / ubuntu. com/ security/ notices)
    * Access / Cost: Mostly free public; some vendor support details may require subscription
    * Relevance: Determines if a fix exists.
    * Notes: Patch availability varies by release stream.
16. **Workaround availability**
    * Link(s): www.cisa.gov/cybersecurity-advisories (https: / / www. cisa. gov/ cybersecurity- advisories), www.kb.cert.org/vuls (https: / / www. kb. cert. org/ vuls/ )
    * Access / Cost: Free public
    * Relevance: Temporary mitigation when patching is not available.
    * Notes: Workarounds may reduce but not eliminate risk.

### 16.4 Environmental impact

1. **Asset criticality**
   * Link(s): www.cisecurity.org/controls (https: / / www. cisecurity. org/ controls)
   * Access / Cost: Free public
   * Relevance: Business/system importance affects risk.
   * Notes: Must come from internal asset inventory.
2. **Internet exposure**
   * Link(s): search.censys.io (https: / / search. censys. io/ ), www.shodan.io (https: / / www. shodan. io/ )
   * Access / Cost: Free tiers / paid plans
   * Relevance: Determines external exploitability surface.
   * Notes: External scan data may be incomplete or stale.
3. **Network reachability**
   * Link(s): nmap.org (https://nmap.org/)
   * Access / Cost: Free / open-source
   * Relevance: Determines whether an exploit path exists.
   * Notes: Internal network context required.
4. **Authentication required**
   * Link(s): www.first.org/cvss (https: / / www. first. org/ cvss/ )
   * Access / Cost: Free public
   * Relevance: Impacts exploitability.
   * Notes: CVSS may not capture local compensating controls.
5. **Privilege required**
   * Link(s): www.first.org/cvss (https: / / www. first. org/ cvss/ )
   * Access / Cost: Free public
   * Relevance: Impacts exploitability and blast radius.
   * Notes: Validate with product configuration.
6. **User interaction required**
   * Link(s): www.first.org/cvss (https: / / www. first. org/ cvss/ )
   * Access / Cost: Free public
   * Relevance: Impacts exploitability conditions.
   * Notes: User interaction can be bypassed in some real-world chains.
7. **Exploit preconditions**
   * Link(s): googleprojectzero.blogspot.com (https: / / googleprojectzero. blogspot. com/ ), www.kb.cert.org/vuls (https: / / www. kb. cert. org/ vuls/ )
   * Access / Cost: Free public
   * Relevance: Defines required configuration or state.
   * Notes: Crucial for false-positive reduction.
8. **Data sensitivity**
   * Link(s): www.cisecurity.org/controls (https: / / www. cisecurity. org/ controls)
   * Access / Cost: Free public
   * Relevance: Determines business impact.
   * Notes: Internal classification required.
9. **Compensating controls**
   * Link(s): public.cyber.mil/stigs (https: / / public. cyber. mil/ stigs/ ), www.cisecurity.org/cis-benchmarks (https: / / www. cisecurity. org/ cis- benchmarks)
   * Access / Cost: Free public; CIS benchmarks may require free registration
   * Relevance: Controls can reduce practical exploitability.
   * Notes: Document assumptions and evidence.
10. **Runtime configuration**
    * Link(s): docs.dependencytrack.org/datasources/overview (https: / / docs. dependencytrack. org/ datasources/ overview/ )
    * Access / Cost: Free public docs
    * Relevance: Enabled features/modules influence affectedness.
    * Notes: Scanner package matches alone can over-report.
11. **Feature/module enabled**
    * Link(s): github.com/openvex/spec (https: / / github. com/ openvex/ spec)
    * Access / Cost: Free / open-source
    * Relevance: VEX not-affected reasoning may depend on disabled code paths.
    * Notes: Requires product/runtime evidence.
12. **Cloud account/project/environment**
    * Link(s): github.com/prowler-cloud/prowler (https: / / github. com/ prowler- cloud/ prowler)
    * Access / Cost: Free / open-source core; commercial products separate
    * Relevance: Cloud context affects exposure and blast radius.
    * Notes: Join vulnerability data with cloud inventory.
13. **Blast radius**
    * Link(s): github.com/salesforce/cloudsplaining (https: / / github. com/ salesforce/ cloudsplaining)
    * Access / Cost: Free / open-source
    * Relevance: Privilege and dependency spread determine impact.
    * Notes: Requires IAM, network, and data-flow context.
14. **Business process ownership**
    * Link(s): www.cisecurity.org/controls (https: / / www. cisecurity. org/ controls)
    * Access / Cost: Free public
    * Relevance: Ownership determines remediation accountability.
    * Notes: Internal data source required.

### 16.5 Detection & remediation

1. **Scanner finding ID**
   * Link(s): dependencytrack.org (https: / / dependencytrack. org/ ), github.com/anchore/grype (https: / / github. com/ anchore/ grype), trivy.dev/docs/latest/scanner/vulnerability (https: / / trivy. dev/ docs/ latest/ scanner/ vulnerability/ )
   * Access / Cost: Free / open-source core tools; commercial support/products may exist
   * Relevance: Scanner-specific finding identity.
   * Notes: Preserve source scanner and version for reproducibility.
2. **Detection method**
   * Link(s): codeql.github.com (https: / / codeql. github. com/ ), github.com/projectdiscovery/nuclei (https: / / github. com/ projectdiscovery/ nuclei), owasp.org/www-project-top-ten (https: / / owasp. org/ www- project- top- ten/ )
   * Access / Cost: Mixed: free/open-source, with some commercial tiers
   * Relevance: Indicates whether finding came from SBOM, CPE, package manager, SAST, DAST, IaC, or runtime telemetry.
   * Notes: Different methods have different false-positive characteristics.
3. **Confidence**
   * Link(s): github.com/openvex/spec (https: / / github. com/ openvex/ spec)
   * Access / Cost: Free / open-source
   * Relevance: Confidence helps rank findings.
   * Notes: Use evidence and source provenance to compute confidence.
4. **False-positive reason**
   * Link(s): github.com/openvex/spec (https: / / github. com/ openvex/ spec)
   * Access / Cost: Free / open-source
   * Relevance: Captures why a match is not actually exploitable or affected.
   * Notes: VEX justification is key for auditability.
5. **Fix version**
   * Link(s): github.com/advisories (https: / / github. com/ advisories), osv.dev (https://osv.dev/)
   * Access / Cost: Free public
   * Relevance: Remediation target version.
   * Notes: Distro fixed versions may differ due to backports.
6. **Patch advisory**
   * Link(s): access.redhat.com/security/data (https: / / access. redhat. com/ security/ data), ubuntu.com/security/notices (https: / / ubuntu. com/ security/ notices), www.debian.org/security (https: / / www. debian. org/ security/ )
   * Access / Cost: Mostly free public; some Red Hat support details may require subscription
   * Relevance: Links vulnerability to vendor patch guidance.
   * Notes: Use vendor patch source for production remediation.
7. **Mitigation**
   * Link(s): www.cisa.gov/cybersecurity-advisories (https: / / www. cisa. gov/ cybersecurity- advisories), www.kb.cert.org/vuls (https: / / www. kb. cert. org/ vuls/ )
   * Access / Cost: Free public
   * Relevance: Temporary or compensating controls.
   * Notes: Mitigations may be partial and context-specific.
8. **Workaround**
   * Link(s): www.kb.cert.org/vuls (https: / / www. kb. cert. org/ vuls/ )
   * Access / Cost: Free public
   * Relevance: Alternative remediation when patch unavailable.
   * Notes: Track expiration and replacement by patch.
9. **Exploit detection signatures**
   * Link(s): github.com/SigmaHQ/sigma (https: / / github. com/ SigmaHQ/ sigma), github.com/VirusTotal/yara (https: / / github. com/ VirusTotal/ yara), github.com/projectdiscovery/nuclei-templates (https: / / github. com/ projectdiscovery/ nuclei- templates)
   * Access / Cost: Free / open-source public GitHub repos
   * Relevance: Detection content for exploit attempts or compromise.
   * Notes: Validate signatures in environment before high-confidence alerting.
10. **Regression test**
    * Link(s): github.com/google/oss-fuzz (https: / / github. com/ google/ oss- fuzz), google.github.io/oss-fuzz (https: / / google. github. io/ oss- fuzz/ )
    * Access / Cost: Free / open-source; OSS-Fuzz service for eligible OSS projects
    * Relevance: Tests that a vulnerability class or bug does not reappear.
    * Notes: Useful for secure SDLC feedback loops.
11. **Verification command**
    * Link(s): github.com/anchore/grype (https: / / github. com/ anchore/ grype), github.com/aquasecurity/trivy-db (https: / / github. com/ aquasecurity/ trivy- db), github.com/projectdiscovery/nuclei (https: / / github. com/ projectdiscovery/ nuclei)
    * Access / Cost: Free / open-source
    * Relevance: Command/procedure to verify vulnerability or remediation state.
    * Notes: Required for repeatable remediation closure.
12. **SLA due date**
    * Link(s): www.cisa.gov/news-events/directives/bod-22-01-reducing-significant-risk-known-exploited-vulnerabilities (https: / / www. cisa. gov/ news- events/ directives/ bod- 22- 01- reducing- significant- risk- known- exploited- vulnerabilities), www.cisa.gov/sites/default/files/feeds/known\_exploited\_vulnerabilities.json (https: / / www. cisa. gov/ sites/ default/ files/ feeds/ known\_ exploited\_ vulnerabilities. json)
    * Access / Cost: Free public
    * Relevance: Remediation deadline derived from KEV, severity, exposure, policy, or business context.
    * Notes: SLA should be policy-driven and context-aware.

## 17. Minimal source set for production use

1. **CVE List v5**
   * Link(s): github.com/CVEProject/cvelistV5 (https: / / github. com/ CVEProject/ cvelistV5)
   * Access / Cost: Free public GitHub repo
   * Relevance: Canonical CVE records.
   * Notes: Start here for CVE identity.
2. **CVE schema**
   * Link(s): github.com/CVEProject/cve-schema (https: / / github. com/ CVEProject/ cve- schema)
   * Access / Cost: Free public GitHub repo
   * Relevance: CVE schema validation.
   * Notes: Required for robust parsers.
3. **NVD CVE API**
   * Link(s): nvd.nist.gov/developers/vulnerabilities (https: / / nvd. nist. gov/ developers/ vulnerabilities)
   * Access / Cost: Free public; optional free API key for higher rate limits
   * Relevance: CVSS/CPE/CWE enrichment.
   * Notes: Core product matching source.
4. **NVD CPE API**
   * Link(s): nvd.nist.gov/developers/products (https: / / nvd. nist. gov/ developers/ products)
   * Access / Cost: Free public; optional free API key for higher rate limits
   * Relevance: Product/platform identity matching.
   * Notes: Combine with PURL.
5. **OSV full database**
   * Link(s): google.github.io/osv.dev/data/#full-database-download (https: / / google. github. io/ osv. dev/ data/ # full- database- download)
   * Access / Cost: Free public
   * Relevance: OSS package vulnerability database.
   * Notes: Local mirroring recommended.
6. **OSV schema**
   * Link(s): ossf.github.io/osv-schema (https: / / ossf. github. io/ osv- schema/ )
   * Access / Cost: Free public / open-source
   * Relevance: OSS vulnerability record schema.
   * Notes: Needed for parsing affected ranges.
7. **GitHub Advisory Database repo**
   * Link(s): github.com/github/advisory-database (https: / / github. com/ github/ advisory- database)
   * Access / Cost: Free / open-source public GitHub repo
   * Relevance: Raw GitHub advisory records.
   * Notes: Preserve GHSA aliases.
8. **CISA KEV JSON**
   * Link(s): www.cisa.gov/sites/default/files/feeds/known\_exploited\_vulnerabilities.json (https: / / www. cisa. gov/ sites/ default/ files/ feeds/ known\_ exploited\_ vulnerabilities. json)
   * Access / Cost: Free public feed
   * Relevance: Known exploitation signal.
   * Notes: High-priority remediation driver.
9. **CISA Vulnrichment**
   * Link(s): github.com/cisagov/vulnrichment (https: / / github. com/ cisagov/ vulnrichment)
   * Access / Cost: Free public GitHub repo
   * Relevance: CISA ADP and SSVC enrichment.
   * Notes: Coverage varies.
10. **FIRST EPSS**
    * Link(s): www.first.org/epss (https: / / www. first. org/ epss/ )
    * Access / Cost: Free public data/API
    * Relevance: Exploit likelihood prediction.
    * Notes: Store score date.
11. **CWE downloads**
    * Link(s): cwe.mitre.org/data/downloads.html (https: / / cwe. mitre. org/ data/ downloads. html)
    * Access / Cost: Free public downloads
    * Relevance: Weakness taxonomy ingestion.
    * Notes: Useful for classification and grouping.
12. **CAPEC downloads**
    * Link(s): capec.mitre.org/data/downloads.html (https: / / capec. mitre. org/ data/ downloads. html)
    * Access / Cost: Free public downloads
    * Relevance: Attack-pattern taxonomy ingestion.
    * Notes: Useful for weakness-to-attack mapping.
13. **ATT\&CK STIX data**
    * Link(s): github.com/mitre-attack/attack-stix-data (https: / / github. com/ mitre- attack/ attack- stix- data)
    * Access / Cost: Free public GitHub repo
    * Relevance: Machine-readable adversary techniques.
    * Notes: Useful for response/detection mapping.
14. **MITRE ATLAS**
    * Link(s): atlas.mitre.org (https: / / atlas. mitre. org/ )
    * Access / Cost: Free public
    * Relevance: AI/ML adversary framework.
    * Notes: Required for AI system risk mapping.
15. **CycloneDX**
    * Link(s): cyclonedx.org/specification/overview (https: / / cyclonedx. org/ specification/ overview/ )
    * Access / Cost: Free / open standard
    * Relevance: SBOM/vulnerability/VEX-capable standard.
    * Notes: Good for inventory ingestion.
16. **SPDX**
    * Link(s): spdx.dev/specifications (https: / / spdx. dev/ specifications/ )
    * Access / Cost: Free / open standard
    * Relevance: SBOM and package metadata standard.
    * Notes: Common in compliance workflows.
17. **PURL**
    * Link(s): github.com/package-url/purl-spec (https: / / github. com/ package- url/ purl- spec)
    * Access / Cost: Free / open-source
    * Relevance: Package identity.
    * Notes: Essential for package vulnerability matching.
18. **CSAF**
    * Link(s): docs.oasis-open.org/csaf/csaf/v2.0/os/csaf-v2.0-os.html (https: / / docs. oasis- open. org/ csaf/ csaf/ v2. 0/ os/ csaf- v2. 0- os. html)
    * Access / Cost: Free / open standard
    * Relevance: Structured security advisories.
    * Notes: Supports product status and VEX-like workflows.
19. **OpenVEX**
    * Link(s): github.com/openvex/spec (https: / / github. com/ openvex/ spec)
    * Access / Cost: Free / open-source
    * Relevance: Affected/not-affected status communication.
    * Notes: Reduces false positives.
20. **Distro feeds**
    * Link(s): access.redhat.com/security/data (https: / / access. redhat. com/ security/ data), alas.aws.amazon.com (https: / / alas. aws. amazon. com/ ), linux.oracle.com/security (https: / / linux. oracle. com/ security/ ), packages.cgr.dev/chainguard/security.json (https: / / packages. cgr. dev/ chainguard/ security. json), packages.wolfi.dev/os/security.json (https: / / packages. wolfi. dev/ os/ security. json), secdb.alpinelinux.org (https: / / secdb. alpinelinux. org/ ), security-tracker.debian.org (https: / / security- tracker. debian. org/ ), ubuntu.com/security/oval (https: / / ubuntu. com/ security/ oval), www.suse.com/support/security/csaf (https: / / www. suse. com/ support/ security/ csaf/ )
    * Access / Cost: Mostly free public; some vendor support/subscription details may apply
    * Relevance: Distro-specific affectedness and patch status.
    * Notes: Required to avoid backport false positives.
21. **Exploit signal feeds**
    * Link(s): docs.greynoise.io (https: / / docs. greynoise. io/ ), github.com/rapid7/metasploit-framework (https: / / github. com/ rapid7/ metasploit- framework), project-zero.issues.chromium.org (https: / / project- zero. issues. chromium. org/ ), www.exploit-db.com (https: / / www. exploit- db. com/ ), www.kb.cert.org/vuls (https: / / www. kb. cert. org/ vuls/ ), www.shadowserver.org (https: / / www. shadowserver. org/ )
    * Access / Cost: Mixed: free public, open-source, free tiers, paid plans, or registration-based access
    * Relevance: Exploitability, weaponization, and exposure enrichment.
    * Notes: Use for prioritization, not canonical vulnerability identity.

## 18. Final structure for all vulnerability management sources & exposure listings

1. **Canonical vulnerability records**
   * Link(s): github.com/CVEProject/cvelistV5 (https: / / github. com/ CVEProject/ cvelistV5), github.com/cisagov/vulnrichment (https: / / github. com/ cisagov/ vulnrichment), nvd.nist.gov (https: / / nvd. nist. gov/ ), www.cve.org (https: / / www. cve. org/ )
   * Access / Cost: Free public / open-source; NVD optional API key
   * Relevance: CVE, NVD, CVE schema, and CISA Vulnrichment provide base vulnerability identity and enrichment.
   * Notes: Use as foundational sources but enrich with vendor/package-specific affectedness.
2. **Package & ecosystem advisories**
   * Link(s): github.com/advisories (https: / / github. com/ advisories), github.com/github/advisory-database (https: / / github. com/ github/ advisory- database), osv.dev (https://osv.dev/)
   * Access / Cost: Free public / open-source
   * Relevance: OSV, GHSA, and language advisory DBs provide package-level affected version data.
   * Notes: Prefer PURL/package semantics over CPE for OSS dependencies.
3. **Vendor & distro affectedness**
   * Link(s): access.redhat.com/security/data (https: / / access. redhat. com/ security/ data), secdb.alpinelinux.org (https: / / secdb. alpinelinux. org/ ), security-tracker.debian.org (https: / / security- tracker. debian. org/ ), ubuntu.com/security/oval (https: / / ubuntu. com/ security/ oval), www.suse.com/support/security/csaf (https: / / www. suse. com/ support/ security/ csaf/ )
   * Access / Cost: Mostly free public; some vendor support entitlements may apply
   * Relevance: CSAF, VEX, OVAL, secdb, OSV, and vendor advisories identify whether a specific product/package is affected.
   * Notes: Essential for reducing false positives and handling backports.
4. **Exploitability & prioritization**
   * Link(s): github.com/rapid7/metasploit-framework (https: / / github. com/ rapid7/ metasploit- framework), viz.greynoise.io (https: / / viz. greynoise. io/ ), www.cisa.gov/sites/default/files/feeds/known\_exploited\_vulnerabilities.json (https: / / www. cisa. gov/ sites/ default/ files/ feeds/ known\_ exploited\_ vulnerabilities. json), www.exploit-db.com (https: / / www. exploit- db. com/ ), www.first.org/epss (https: / / www. first. org/ epss/ )
   * Access / Cost: Mixed: free public, open-source, free tiers / paid plans
   * Relevance: KEV, EPSS, SSVC, CVSS, Exploit-DB, Metasploit, and GreyNoise inform urgency.
   * Notes: Do not conflate severity with exploitability.
5. **Weakness & adversary mapping**
   * Link(s): attack.mitre.org/matrices/enterprise (https: / / attack. mitre. org/ matrices/ enterprise/ ), atlas.mitre.org (https: / / atlas. mitre. org/ ), capec.mitre.org (https: / / capec. mitre. org/ ), cwe.mitre.org (https: / / cwe. mitre. org/ )
   * Access / Cost: Free public
   * Relevance: CWE, CAPEC, ATT\&CK, and ATLAS map vulnerabilities to weaknesses and adversary behavior.
   * Notes: Useful for detection engineering and root-cause analysis.
6. **AI-specific vulnerability context**
   * Link(s): atlas.mitre.org (https: / / atlas. mitre. org/ ), owasp.org/www-project-machine-learning-security-top-10 (https: / / owasp. org/ www- project- machine- learning- security- top- 10/ ), owasp.org/www-project-top-10-for-large-language-model-applications (https: / / owasp. org/ www- project- top- 10- for- large- language- model- applications/ ), www.nist.gov/itl/ai-risk-management-framework (https: / / www. nist. gov/ itl/ ai- risk- management- framework)
   * Access / Cost: Free public / open community
   * Relevance: ATLAS, OWASP LLM Top 10, OWASP ML Top 10, and NIST AI RMF frame AI/ML risk.
   * Notes: AI vulnerabilities often lack CVEs; include threat-model and control frameworks.
7. **SBOM & identity**
   * Link(s): cyclonedx.org/specification/overview (https: / / cyclonedx. org/ specification/ overview/ ), github.com/package-url/purl-spec (https: / / github. com/ package- url/ purl- spec), nvd.nist.gov/products/cpe (https: / / nvd. nist. gov/ products/ cpe), spdx.dev/specifications (https: / / spdx. dev/ specifications/ )
   * Access / Cost: Free public / open standards
   * Relevance: CycloneDX, SPDX, PURL, CPE, and SWID identify components for matching.
   * Notes: Accurate inventory is prerequisite to vulnerability assessment.
8. **Exposure telemetry**
   * Link(s): leakix.net (https: / / leakix. net/ ), search.censys.io (https: / / search. censys. io/ ), viz.greynoise.io (https: / / viz. greynoise. io/ ), www.shadowserver.org (https: / / www. shadowserver. org/ ), www.shodan.io (https: / / www. shodan. io/ )
   * Access / Cost: Mixed: free public, free tiers, paid plans, registration-based access
   * Relevance: Censys, Shodan, Shadowserver, GreyNoise, LeakIX, and internal inventory help assess real exposure.
   * Notes: External scan data can be stale or incomplete; join with internal evidence.
9. **Malicious package & supply-chain compromise**
   * Link(s): github.com/advisories?query=type%3Amalware (https: / / github. com/ advisories? query= type% 3Amalware), github.com/ossf/malicious-packages (https: / / github. com/ ossf/ malicious- packages), github.com/ossf/package-analysis (https: / / github. com/ ossf/ package- analysis), security.snyk.io (https: / / security. snyk. io/ ), socket.dev/blog (https: / / socket. dev/ blog), sonatype.com/resources/vulnerability-database (https: / / sonatype. com/ resources/ vulnerability- database)
   * Access / Cost: Mixed: free public, open-source, free tiers / commercial products
   * Relevance: Tracks malicious package risk that may not appear as conventional CVEs.
   * Notes: Essential for supply-chain defense and dependency risk.
10. **Detection engineering**
    * Link(s): codeql.github.com (https: / / codeql. github. com/ ), github.com/projectdiscovery/nuclei (https: / / github. com/ projectdiscovery/ nuclei), google.github.io/oss-fuzz (https: / / google. github. io/ oss- fuzz/ ), joern.io (https://joern.io/), samate.nist.gov/SARD (https: / / samate. nist. gov/ SARD/ ), semgrep.dev (https: / / semgrep. dev/ )
    * Access / Cost: Mixed: free/open-source, free public datasets, commercial tiers for some products
    * Relevance: CodeQL, Semgrep, Joern, Infer, Nuclei, OSS-Fuzz, SARD, and vulnerability datasets support detection and validation.
    * Notes: Detection quality depends on rule precision, context, and evidence quality.
11. **Threat intelligence**
    * Link(s): blog.google/threat-analysis-group (https: / / blog. google/ threat- analysis- group/ ), blog.talosintelligence.com (https: / / blog. talosintelligence. com/ ), cloud.google.com/blog/topics/threat-intelligence (https: / / cloud. google. com/ blog/ topics/ threat- intelligence), unit42.paloaltonetworks.com (https: / / unit42. paloaltonetworks. com/ ), www.microsoft.com/en-us/security/blog/topic/threat-intelligence (https: / / www. microsoft. com/ en- us/ security/ blog/ topic/ threat- intelligence/ ), www.rapid7.com/blog/tag/vulnerability-management (https: / / www. rapid7. com/ blog/ tag/ vulnerability- management/ ), www.ransomware.live (https: / / www. ransomware. live/ )
    * Access / Cost: Mostly free public blogs/research; commercial threat intel products separate
    * Relevance: Exploitation-in-the-wild context and malware/research reporting.
    * Notes: Research sources vary in timeliness, depth, and attribution confidence.
12. **Compliance & configuration impact**
    * Link(s): github.com/ComplianceAsCode/content (https: / / github. com/ ComplianceAsCode/ content), ncp.nist.gov (https: / / ncp. nist. gov/ ), public.cyber.mil/stigs (https: / / public. cyber. mil/ stigs/ ), www.cisecurity.org/cis-benchmarks (https: / / www. cisecurity. org/ cis- benchmarks), www.open-scap.org (https: / / www. open- scap. org/ )
    * Access / Cost: Mostly free public / open-source; CIS benchmarks may require free registration and commercial tools exist
    * Relevance: CIS, STIG, SCAP, cloud posture, and Kubernetes benchmarks help assess environmental control weakness.
    * Notes: These are not vulnerability feeds but determine practical risk and exploitability.

## License

* Copyright ■ 2025 Keerthana Purushotham `<keep.consult@proton.me>`.
* Licensed under the GNU AGPL v3. See LICENSE for details.
* see license (https://github.com/keerthanap8898/CveToad/blob/main/LICENSE)

## Note

Some vendor/security pages change URLs over time, so treat this as a high-coverage baseline rather than a mathematically exhaustive list of every possible vulnerability source.
