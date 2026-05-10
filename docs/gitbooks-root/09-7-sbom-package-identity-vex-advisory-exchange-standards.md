# 7. SBOM, package identity, VEX & advisory exchange standards

### 7.1 SBOM standards
| Sl. # | Title | Link(s) | Access / Cost | Relevance | Notes & POIs |
|---:|---|---|---|---|---|
| 1 | CycloneDX specification overview | [cyclonedx.org/specification/overview](https://cyclonedx.org/specification/overview/) | Free / open standard | SBOM, SaaSBOM, BOM, VEX, vulnerability & component metadata standard. | Good fit for vulnerability management workflows due to vulnerability & VEX support. |
| 2 | CycloneDX GitHub | [github.com/CycloneDX/specification](https://github.com/CycloneDX/specification) | Free / open-source public GitHub repo | CycloneDX specification source repository. | Use for versioned spec tracking. |
| 3 | CycloneDX VEX | [cyclonedx.org/capabilities/vex](https://cyclonedx.org/capabilities/vex/) | Free public docs | CycloneDX VEX capability documentation. | Useful for affected/not-affected communication. |
| 4 | SPDX specifications | [spdx.dev/specifications](https://spdx.dev/specifications/) | Free / open standard | SPDX specifications for software bills of materials & package metadata. | SPDX is widely used for license/package metadata & supply-chain exchange. |
| 5 | SPDX 3.0.1 spec | [spdx.github.io/spdx-spec/v3.0.1](https://spdx.github.io/spdx-spec/v3.0.1/) | Free public docs | SPDX 3.0.1 specification. | Track spec version compatibility in parsers. |
| 6 | SPDX package URL property | [spdx.github.io/spdx-spec/v3.0.1/model/Software/Properties/packageUrl](https://spdx.github.io/spdx-spec/v3.0.1/model/Software/Properties/packageUrl/) | Free public docs | SPDX support for package URL property. | Important for PURL-based vulnerability matching. |
| 7 | SPDX GitHub | [github.com/spdx/spdx-spec](https://github.com/spdx/spdx-spec) | Free / open-source public GitHub repo | SPDX specification repository. | Use for release tracking & schema/source inspection. |
| 8 | NTIA SBOM resources | [www.ntia.gov/page/software-bill-materials](https://www.ntia.gov/page/software-bill-materials) | Free public | SBOM policy & foundational resources. | Useful for governance & compliance context. |
| 9 | CISA SBOM | [www.cisa.gov/sbom](https://www.cisa.gov/sbom) | Free public | CISA SBOM guidance & resources. | Useful for U.S. public-sector & enterprise SBOM program alignment. |
### 7.2 Package & software identity
| Sl. # | Title | Link(s) | Access / Cost | Relevance | Notes & POIs |
|---:|---|---|---|---|---|
| 1 | Package URL - PURL spec | [github.com/package-url/purl-spec](https://github.com/package-url/purl-spec) | Free / open-source public GitHub repo | Standard package identifier used in SBOMs & vulnerability DBs. | Crucial for OSV & package ecosystem matching. |
| 2 | PURL types | [github.com/package-url/purl-spec/blob/master/PURL-TYPES.rst](https://github.com/package-url/purl-spec/blob/master/PURL-TYPES.rst) | Free public | Defines PURL types per ecosystem. | Helps normalize ecosystem-specific package coordinates. |
| 3 | CPE specification / dictionary | [nvd.nist.gov/products/cpe](https://nvd.nist.gov/products/cpe) | Free public | Product naming & CPE dictionary. | Useful for product/platform matching, but can be imprecise for packages. |
| 4 | NVD CPE API | [nvd.nist.gov/developers/products](https://nvd.nist.gov/developers/products) | Free public; optional free API key for higher rate limits | Programmatic CPE dictionary access. | Required for automated CPE matching workflows. |
| 5 | SWID tags - NIST | [csrc.nist.gov/projects/software-identification-swid](https://csrc.nist.gov/projects/software-identification-swid) | Free public | Software Identification Tags for installed software identity. | Useful in enterprise asset inventory & compliance. |
| 6 | GS1 Digital Link / identifiers | [www.gs1.org/standards/gs1-digital-link](https://www.gs1.org/standards/gs1-digital-link) | Free public standard docs; GS1 membership may apply for assigned identifiers | Optional identity standard for physical/embedded supply chains. | Not a vulnerability standard, but can matter in hardware/product traceability. |
| 7 | Software Heritage IDs | [www.swhid.org](https://www.swhid.org/) | Free public / open | Persistent source-code artifact identity. | Useful for source provenance & precise code artifact references. |
### 7.3 Advisory exchange, CSAF & VEX
| Sl. # | Title | Link(s) | Access / Cost | Relevance | Notes & POIs |
|---:|---|---|---|---|---|
| 1 | OASIS CSAF 2.0 specification | [docs.oasis-open.org/csaf/csaf/v2.0/os/csaf-v2.0-os.html](https://docs.oasis-open.org/csaf/csaf/v2.0/os/csaf-v2.0-os.html) | Free / open standard | Common Security Advisory Framework for structured advisories. | CSAF can express product status, remediation, impact, & VEX-like affectedness. |
| 2 | CSAF home | [www.csaf.io](https://www.csaf.io/) | Free public | CSAF ecosystem & tooling hub. | Good starting point for CSAF adoption. |
| 3 | OpenVEX specification | [github.com/openvex/spec](https://github.com/openvex/spec) | Free / open-source public GitHub repo | Minimal JSON-LD VEX format based on CISA VEX requirements. | Useful for communicating not-affected/fixed/affected status. |
| 4 | OpenVEX project page | [openssf.org/projects/openvex](https://openssf.org/projects/openvex/) | Free public | OpenSSF project page for OpenVEX. | Project-level overview. |
| 5 | CISA Minimum Requirements for VEX | [www.cisa.gov/sites/default/files/2023-04/minimum-requirements-for-vex-508c.pdf](https://www.cisa.gov/sites/default/files/2023-04/minimum-requirements-for-vex-508c.pdf) | Free public PDF | Baseline VEX requirements. | Useful for evaluating VEX completeness. |
| 6 | OpenSSF VDR, VEX, OpenVEX & CSAF explainer | [openssf.org/blog/2023/09/07/vdr-vex-openvex-and-csaf](https://openssf.org/blog/2023/09/07/vdr-vex-openvex-and-csaf/) | Free public | Explains VDR, VEX, OpenVEX, & CSAF. | Useful for conceptual alignment & terminology. |
| 7 | Red Hat CSAF/VEX guidance | [redhatproductsecurity.github.io/security-data-guidelines/csaf-vex](https://redhatproductsecurity.github.io/security-data-guidelines/csaf-vex/) | Free public docs | Red Hat CSAF/VEX semantics & usage guidance. | Important for vendor-specific interpretation. |
| 8 | Ubuntu VEX | [ubuntu.com/security/vex](https://ubuntu.com/security/vex) | Free public | Ubuntu VEX data entry point. | Useful for Ubuntu affectedness & false-positive reduction. |
| 9 | Canonical Ubuntu Security Notices repo - OSV & OpenVEX | [github.com/canonical/ubuntu-security-notices](https://github.com/canonical/ubuntu-security-notices) | Free public GitHub repo | Canonical USN/LSN, OSV, & OpenVEX JSON data. | Strong machine-readable source for Ubuntu security status. |
> #### [*Back to **`Index`***](#index)
---
