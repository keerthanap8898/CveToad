# 12. SBOM, package identity, VEX & advisory exchange standards

## 12.1 SBOM standards

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


## 12.2 Package & software identity

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **Package URL - PURL spec**<br><br>**`Link(s)`:** [github.com/package-url/purl-spec](https://github.com/package-url/purl-spec)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** Standard package identifier used in SBOMs & vulnerability DBs.<br><br>**`Notes & POIs`:** Crucial for OSV & package ecosystem matching. |
| 2 | **PURL types**<br><br>**`Link(s)`:** [github.com/package-url/purl-spec/blob/master/PURL-TYPES.rst](https://github.com/package-url/purl-spec/blob/master/PURL-TYPES.rst)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Defines PURL types per ecosystem.<br><br>**`Notes & POIs`:** Helps normalize ecosystem-specific package coordinates. |
| 3 | **CPE specification / dictionary**<br><br>**`Link(s)`:** [nvd.nist.gov/products/cpe](https://nvd.nist.gov/products/cpe)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Product naming & CPE dictionary.<br><br>**`Notes & POIs`:** Useful for product/platform matching, but can be imprecise for packages. |
| 4 | **NVD CPE API**<br><br>**`Link(s)`:** [nvd.nist.gov/developers/products](https://nvd.nist.gov/developers/products)<br><br>**`Access / Cost`:** Free public; optional free API key for higher rate limits | **`Relevance`:** Programmatic CPE dictionary access.<br><br>**`Notes & POIs`:** Required for automated CPE matching workflows. |
| 5 | **SWID tags - NIST**<br><br>**`Link(s)`:** [csrc.nist.gov/projects/software-identification-swid](https://csrc.nist.gov/projects/software-identification-swid)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Software Identification Tags for installed software identity.<br><br>**`Notes & POIs`:** Useful in enterprise asset inventory & compliance. |
| 6 | **GS1 Digital Link / identifiers**<br><br>**`Link(s)`:** [www.gs1.org/standards/gs1-digital-link](https://www.gs1.org/standards/gs1-digital-link)<br><br>**`Access / Cost`:** Free public standard docs; GS1 membership may apply for assigned identifiers | **`Relevance`:** Optional identity standard for physical/embedded supply chains.<br><br>**`Notes & POIs`:** Not a vulnerability standard, but can matter in hardware/product traceability. |
| 7 | **Software Heritage IDs**<br><br>**`Link(s)`:** [www.swhid.org](https://www.swhid.org/)<br><br>**`Access / Cost`:** Free public / open | **`Relevance`:** Persistent source- code artifact identity.<br><br>**`Notes & POIs`:** Useful for source provenance & precise code artifact references. |

## 12.3 Advisory exchange, CSAF & VEX

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

## Discussion

This chapter section keeps the latest table structure, source titles, access/cost fields, relevance notes, & operational notes from the source inventory. Review the table entries as ingestion candidates, then validate source freshness, licensing, authentication requirements, & link-check behavior before production use.

---

#### [Back to Index](../../01-index.md)
