# 2.3 Language & package ecosystem advisory databases

#### 2.3.1 Go

| Sl. # | Title                          | Link(s)                                                                                              | Access / Cost                | Relevance                                            | Notes & POIs                                                                         |
| ----: | ------------------------------ | ---------------------------------------------------------------------------------------------------- | ---------------------------- | ---------------------------------------------------- | ------------------------------------------------------------------------------------ |
|     1 | Go Vulnerability Database      | [vuln.go.dev](https://vuln.go.dev/)                                                                  | Free public / open data      | Official Go vulnerability database for Go modules.   | Strong source for Go-specific affected symbols, modules, packages, & fixed versions. |
|     2 | Go vulnerability database docs | [go.dev/doc/security/vuln/database](https://go.dev/doc/security/vuln/database)                       | Free public docs             | Explains Go vulnerability DB data model & OSV usage. | Important for correct ingestion & symbol/package-level interpretation.               |
|     3 | Go vuln browser                | [pkg.go.dev/vuln](https://pkg.go.dev/vuln/)                                                          | Free public                  | Human-readable curated Go vulnerability reports.     | Useful for triage & manual review.                                                   |
|     4 | Go vuln tooling                | [pkg.go.dev/golang.org/x/vuln/cmd/govulncheck](https://pkg.go.dev/golang.org/x/vuln/cmd/govulncheck) | Free / open-source Go module | Go source/binary vulnerability checking.             | Can reduce false positives by analyzing call reachability in Go code.                |

#### 2.3.2 Rust

| Sl. # | Title                      | Link(s)                                                                                                      | Access / Cost                         | Relevance                            | Notes & POIs                                                                        |
| ----: | -------------------------- | ------------------------------------------------------------------------------------------------------------ | ------------------------------------- | ------------------------------------ | ----------------------------------------------------------------------------------- |
|     1 | RustSec                    | [rustsec.org](https://rustsec.org/)                                                                          | Free public / open-source ecosystem   | Rust crate advisory ecosystem.       | Often includes Rust-specific unsoundness, yanked crates, & ecosystem-specific risk. |
|     2 | RustSec advisory DB repo   | [github.com/RustSec/advisory-db](https://github.com/RustSec/advisory-db)                                     | Free / open-source public GitHub repo | Machine-ingestible Rust advisories.  | Good for local ingestion & cargo-audit compatible workflows.                        |
|     3 | RustSec advisories browser | [rustsec.org/advisories](https://rustsec.org/advisories/)                                                    | Free public                           | Human-browsable Rust advisories.     | Useful for manual triage.                                                           |
|     4 | cargo-audit                | [github.com/RustSec/rustsec/tree/main/cargo-audit](https://github.com/RustSec/rustsec/tree/main/cargo-audit) | Free / open-source public GitHub repo | RustSec-based vulnerability scanner. | Reference implementation for Rust dependency scanning.                              |

#### 2.3.3 Python / PyPI

| Sl. # | Title                  | Link(s)                                                                        | Access / Cost                                               | Relevance                                   | Notes & POIs                                                             |
| ----: | ---------------------- | ------------------------------------------------------------------------------ | ----------------------------------------------------------- | ------------------------------------------- | ------------------------------------------------------------------------ |
|     1 | PyPA advisory database | [github.com/pypa/advisory-database](https://github.com/pypa/advisory-database) | Free / open-source public GitHub repo                       | Python/PyPI advisory source.                | Use with OSV & GitHub advisories for better Python coverage.             |
|     2 | PyPI security page     | [pypi.org/security](https://pypi.org/security/)                                | Free public                                                 | PyPI security reporting & advisory context. | Useful for process context, not necessarily complete advisory ingestion. |
|     3 | pip-audit              | [github.com/pypa/pip-audit](https://github.com/pypa/pip-audit)                 | Free / open-source public GitHub repo                       | Python dependency vulnerability scanner.    | Reference implementation for Python dependency assessment.               |
|     4 | Safety DB              | [github.com/pyupio/safety-db](https://github.com/pyupio/safety-db)             | Free public GitHub repo; related products may be commercial | Historical Python advisory source.          | Validate freshness & licensing before relying on it.                     |

#### 2.3.4 JavaScript / npm

| Sl. # | Title                          | Link(s)                                                                                            | Access / Cost                                            | Relevance                                                           | Notes & POIs                                                                                     |
| ----: | ------------------------------ | -------------------------------------------------------------------------------------------------- | -------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------ |
|     1 | npm advisories via GitHub      | [github.com/advisories?query=ecosystem%3Anpm](https://github.com/advisories?query=ecosystem%3Anpm) | Free public                                              | npm ecosystem vulnerability advisories.                             | Semver ranges, lockfiles, transitive dependencies, & malicious packages require careful parsing. |
|     2 | Node.js Security Working Group | [github.com/nodejs/security-wg](https://github.com/nodejs/security-wg)                             | Free / open-source public GitHub repo                    | Node ecosystem security coordination & historical advisory sources. | Some historical records may be superseded by GitHub Advisory DB.                                 |
|     3 | npm audit docs                 | [docs.npmjs.com/cli/commands/npm-audit](https://docs.npmjs.com/cli/commands/npm-audit)             | Free public docs                                         | Documents npm audit behavior.                                       | Useful to understand scanner behavior, dependency tree handling, & remediation suggestions.      |
|     4 | Socket.dev security research   | [socket.dev/blog](https://socket.dev/blog)                                                         | Free public blog; product/API features may be commercial | Malicious package & JS supply-chain threat intel.                   | Research source. Validate indicators & package claims against primary registries.                |

#### 2.3.5 Java / Maven / JVM

| Sl. # | Title                           | Link(s)                                                                                                | Access / Cost                                              | Relevance                                                                  | Notes & POIs                                                                |
| ----: | ------------------------------- | ------------------------------------------------------------------------------------------------------ | ---------------------------------------------------------- | -------------------------------------------------------------------------- | --------------------------------------------------------------------------- |
|     1 | Sonatype OSS Index              | [ossindex.sonatype.org](https://ossindex.sonatype.org/)                                                | Free tier / API terms; Sonatype products may be commercial | OSS vulnerability intelligence commonly used for Maven & other ecosystems. | Commercial/community source. Validate API terms, limits, & provenance.      |
|     2 | Sonatype vulnerability database | [sonatype.com/resources/vulnerability-database](https://sonatype.com/resources/vulnerability-database) | Free public search / commercial ecosystem                  | Sonatype vulnerability intelligence database.                              | Useful for enrichment & triage, but not canonical.                          |
|     3 | Maven Central                   | [central.sonatype.com](https://central.sonatype.com/)                                                  | Free public                                                | Package identity & metadata for JVM packages.                              | Not a vulnerability DB, but essential for coordinate resolution & metadata. |
|     4 | OSS Index API docs              | [ossindex.sonatype.org/doc/rest](https://ossindex.sonatype.org/doc/rest)                               | Free tier / API terms                                      | REST API access for OSS Index.                                             | Consider rate limits, authentication, & terms before ingestion.             |

#### 2.3.6 PHP / Composer

| Sl. # | Title                             | Link(s)                                                                                                | Access / Cost                         | Relevance                          | Notes & POIs                                                               |
| ----: | --------------------------------- | ------------------------------------------------------------------------------------------------------ | ------------------------------------- | ---------------------------------- | -------------------------------------------------------------------------- |
|     1 | FriendsOfPHP security advisories  | [github.com/FriendsOfPHP/security-advisories](https://github.com/FriendsOfPHP/security-advisories)     | Free / open-source public GitHub repo | PHP Composer package advisories.   | Historical & ecosystem-specific source. Cross-check with Packagist & GHSA. |
|     2 | Packagist security advisories API | [packagist.org/apidoc#list-security-advisories](https://packagist.org/apidoc#list-security-advisories) | Free public API docs / public API     | Composer package advisory API.     | Direct ecosystem source for Composer package advisories.                   |
|     3 | Composer audit docs               | [getcomposer.org/doc/03-cli.md#audit](https://getcomposer.org/doc/03-cli.md#audit)                     | Free public docs                      | Documents Composer audit behavior. | Useful for implementation parity with Composer-native workflows.           |

#### 2.3.7 Ruby

| Sl. # | Title               | Link(s)                                                                            | Access / Cost                         | Relevance                              | Notes & POIs                                        |
| ----: | ------------------- | ---------------------------------------------------------------------------------- | ------------------------------------- | -------------------------------------- | --------------------------------------------------- |
|     1 | RubySec advisory DB | [github.com/rubysec/ruby-advisory-db](https://github.com/rubysec/ruby-advisory-db) | Free / open-source public GitHub repo | RubyGems advisories.                   | Cross-check with GHSA RubyGems advisories.          |
|     2 | Bundler audit       | [github.com/rubysec/bundler-audit](https://github.com/rubysec/bundler-audit)       | Free / open-source public GitHub repo | Ruby dependency vulnerability scanner. | Reference implementation for Gemfile.lock scanning. |

#### 2.3.8 .NET / NuGet

| Sl. # | Title                       | Link(s)                                                                                                                          | Access / Cost    | Relevance                         | Notes & POIs                                                  |
| ----: | --------------------------- | -------------------------------------------------------------------------------------------------------------------------------- | ---------------- | --------------------------------- | ------------------------------------------------------------- |
|     1 | NuGet advisories via GitHub | [github.com/advisories?query=ecosystem%3Anuget](https://github.com/advisories?query=ecosystem%3Anuget)                           | Free public      | NuGet ecosystem advisories.       | Use with lockfile/project metadata for actual exposure.       |
|     2 | NuGet audit docs            | [learn.microsoft.com/en-us/nuget/concepts/auditing-packages](https://learn.microsoft.com/en-us/nuget/concepts/auditing-packages) | Free public docs | Documents NuGet package auditing. | Useful for Microsoft ecosystem parity & remediation guidance. |

#### 2.3.9 Erlang / Elixir / Hex

| Sl. # | Title                        | Link(s)                                                                                                  | Access / Cost | Relevance                                    | Notes & POIs                                                         |
| ----: | ---------------------------- | -------------------------------------------------------------------------------------------------------- | ------------- | -------------------------------------------- | -------------------------------------------------------------------- |
|     1 | Erlang advisories via GitHub | [github.com/advisories?query=ecosystem%3Aerlang](https://github.com/advisories?query=ecosystem%3Aerlang) | Free public   | Erlang/Hex advisories.                       | Validate ecosystem naming, package coordinates, & version semantics. |
|     2 | Hex package manager          | [hex.pm](https://hex.pm/)                                                                                | Free public   | Package registry for Erlang/Elixir packages. | Registry metadata helps resolve package identity.                    |

#### 2.3.10 Dart / Flutter / Pub

| Sl. # | Title                     | Link(s)                                                                                            | Access / Cost | Relevance                                       | Notes & POIs                                    |
| ----: | ------------------------- | -------------------------------------------------------------------------------------------------- | ------------- | ----------------------------------------------- | ----------------------------------------------- |
|     1 | Pub advisories via GitHub | [github.com/advisories?query=ecosystem%3Apub](https://github.com/advisories?query=ecosystem%3Apub) | Free public   | Dart/Pub advisories.                            | Coverage depends on GitHub advisory ingestion.  |
|     2 | Dart package repository   | [pub.dev](https://pub.dev/)                                                                        | Free public   | Package registry for Dart/Flutter dependencies. | Useful for package identity & version metadata. |

#### 2.3.11 Swift

| Sl. # | Title                       | Link(s)                                                                                                | Access / Cost | Relevance                                   | Notes & POIs                                                         |
| ----: | --------------------------- | ------------------------------------------------------------------------------------------------------ | ------------- | ------------------------------------------- | -------------------------------------------------------------------- |
|     1 | Swift advisories via GitHub | [github.com/advisories?query=ecosystem%3Aswift](https://github.com/advisories?query=ecosystem%3Aswift) | Free public   | Swift ecosystem advisories.                 | Coverage depends on GitHub Advisory DB support.                      |
|     2 | Swift Package Index         | [swiftpackageindex.com](https://swiftpackageindex.com/)                                                | Free public   | Swift package metadata & ecosystem context. | Not a vulnerability DB, but useful for package discovery & metadata. |

> [_**Back to****&#x20;****`Index`**_](../)

***
