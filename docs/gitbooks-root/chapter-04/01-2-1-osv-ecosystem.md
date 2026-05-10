# 2.1 OSV ecosystem

| Sl. # | Title | Link(s) | Access / Cost | Relevance | Notes & POIs |
|---:|---|---|---|---|---|
| 1 | OSV main site | [osv.dev](https://osv.dev/) | Free public / open data | Aggregates OSS vulnerabilities by package ecosystem, version, commit, & aliases. Key for dependency-based detection. | OSV is package/version-centric & often better than CPE for OSS packages. Coverage depends on upstream ecosystem feeds. |
| 2 | OSV vulnerability list | [osv.dev/list](https://osv.dev/list) | Free public | Human-browsable OSV records. | Useful for manual triage & ecosystem browsing. Prefer API/full downloads for automation. |
| 3 | OSV full database download | [google.github.io/osv.dev/data/#full-database-download](https://google.github.io/osv.dev/data/#full-database-download) | Free public / open data | Full database ZIP, including withdrawn records, via `gs://osv-vulnerabilities/all.zip`. | Best for local mirroring. Preserve withdrawn records for historical auditability. |
| 4 | OSV data sources page | [google.github.io/osv.dev/data](https://google.github.io/osv.dev/data/) | Free public | Per-ecosystem downloads & full-database download. | Useful for targeted ecosystem ingestion. |
| 5 | OSV schema rendered spec | [ossf.github.io/osv-schema](https://ossf.github.io/osv-schema/) | Free public / open-source | Standard interchange format for OSS vulnerability records. | Handle aliases, affected ranges, fixed versions, withdrawn records, & ecosystem-specific semantics. |
| 6 | OSV schema GitHub repo | [github.com/ossf/osv-schema](https://github.com/ossf/osv-schema) | Free / open-source public GitHub repo | Schema source, releases, bindings, & tooling. | Track schema versions & validation changes over time. |
| 7 | OSV API docs | [google.github.io/osv.dev/post-v1-query](https://google.github.io/osv.dev/post-v1-query/) | Free public API | Query vulnerabilities by package, version, commit, or vulnerability ID. | Good for online lookup. Use full downloads for high-volume local matching. |
| 8 | OSV Scanner | [google.github.io/osv-scanner](https://google.github.io/osv-scanner/) | Free public / open-source | Reference scanner using OSV data. | Useful implementation reference for lockfile parsing & version matching. |
| 9 | OSV Scanner GitHub | [github.com/google/osv-scanner](https://github.com/google/osv-scanner) | Free / open-source public GitHub repo | Scanner implementation, matching logic, & lockfile parsing. | Review for practical matching edge cases. |
| 10 | OSV ecosystem list | [osv.dev/list](https://osv.dev/list) | Free public | Ecosystem browsing for Maven, npm, PyPI, Go, crates.io, Debian, Alpine, Ubuntu, Wolfi, OSS-Fuzz, etc. | Repeats the list URL intentionally because it serves both record browsing & ecosystem discovery. |
