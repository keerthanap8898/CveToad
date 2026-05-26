# 19. Minimal source set for production use

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

## Discussion

This chapter section keeps the latest table structure, source titles, access/cost fields, relevance notes, & operational notes from the source inventory. Review the table entries as ingestion candidates, then validate source freshness, licensing, authentication requirements, & link-check behavior before production use.

---

#### [Back to Index](../../01-index.md)
