# 14. Source-code, dependency, artifact & build-chain provenance

## 14.1 Source & artifact provenance

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **SLSA**<br><br>**`Link(s)`:** [slsa.dev](https://slsa.dev/)<br><br>**`Access / Cost`:** Free / open standard | **`Relevance`:** Supply-chain Levels for Software Artifacts.<br><br>**`Notes & POIs`:** Useful for evaluating build integrity & provenance risk. |
| 2 | **Sigstore**<br><br>**`Link(s)`:** [www.sigstore.dev](https://www.sigstore.dev/)<br><br>**`Access / Cost`:** Free / open-source public infrastructure | **`Relevance`:** Signing & verification for software artifacts.<br><br>**`Notes & POIs`:** Helps verify artifact integrity & publisher identity. |
| 3 | **Cosign**<br><br>**`Link(s)`:** [github.com/sigstore/cosign](https://github.com/sigstore/cosign)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** Container/artifact signing tool.<br><br>**`Notes & POIs`:** Useful for verifying container image provenance. |
| 4 | **Rekor**<br><br>**`Link(s)`:** [docs.sigstore.dev/logging/overview](https://docs.sigstore.dev/logging/overview/)<br><br>**`Access / Cost`:** Free public docs / public transparency log | **`Relevance`:** Transparency log for signed artifacts.<br><br>**`Notes & POIs`:** Useful for auditability & tamper detection. |
| 5 | **in-toto**<br><br>**`Link(s)`:** [in-toto.io](https://in-toto.io/)<br><br>**`Access / Cost`:** Free / open-source | **`Relevance`:** Supply-chain integrity framework.<br><br>**`Notes & POIs`:** Useful for verifying build steps & provenance attestations. |
| 6 | **The Update Framework - TUF**<br><br>**`Link(s)`:** [theupdateframework.io](https://theupdateframework.io/)<br><br>**`Access / Cost`:** Free / open-source | **`Relevance`:** Secure software update framework.<br><br>**`Notes & POIs`:** Useful for update-channel compromise resistance. |
| 7 | **SLSA GitHub generators**<br><br>**`Link(s)`:** [github.com/slsa-framework/slsa-github-generator](https://github.com/slsa-framework/slsa-github-generator)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** GitHub-based SLSA provenance generators.<br><br>**`Notes & POIs`:** Useful for CI/CD provenance generation. |

## 14.2 Dependency inventory & graphing

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

## Discussion

This chapter section keeps the latest table structure, source titles, access/cost fields, relevance notes, & operational notes from the source inventory. Review the table entries as ingestion candidates, then validate source freshness, licensing, authentication requirements, & link-check behavior before production use.

---

#### [Back to Index](../../01-index.md)
