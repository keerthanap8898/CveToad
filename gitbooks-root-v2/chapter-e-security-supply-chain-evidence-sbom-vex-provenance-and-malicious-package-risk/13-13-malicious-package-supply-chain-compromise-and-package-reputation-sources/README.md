# 13. Malicious package, supply-chain compromise & package reputation sources

## 13.1 Malicious package databases

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

## 13.2 Package reputation / dependency health

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

## Discussion

This chapter section keeps the latest table structure, source titles, access/cost fields, relevance notes, & operational notes from the source inventory. Review the table entries as ingestion candidates, then validate source freshness, licensing, authentication requirements, & link-check behavior before production use.

---

#### [Back to Index](../../01-index.md)
