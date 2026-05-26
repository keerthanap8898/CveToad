# 14. Source-code, dependency, artifact & build-chain provenance

## 14.1 Source & artifact provenance

| Sl. # | Source Title                                                                                                                                                                                                                                                                                                 | Notes                                                                                                                                                                                                                  |
| ----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|     1 | <p><strong>SLSA</strong><br><br><strong><code>Link(s)</code>:</strong> <a href="https://slsa.dev/">slsa.dev</a><br><br><strong><code>Access / Cost</code>:</strong> Free / open standard</p>                                                                                                                 | <p><strong><code>Relevance</code>:</strong> Supply-chain Levels for Software Artifacts.<br><br><strong><code>Notes &#x26; POIs</code>:</strong> Useful for evaluating build integrity &#x26; provenance risk.</p>      |
|     2 | <p><strong>Sigstore</strong><br><br><strong><code>Link(s)</code>:</strong> <a href="https://www.sigstore.dev/">www.sigstore.dev</a><br><br><strong><code>Access / Cost</code>:</strong> Free / open-source public infrastructure</p>                                                                         | <p><strong><code>Relevance</code>:</strong> Signing &#x26; verification for software artifacts.<br><br><strong><code>Notes &#x26; POIs</code>:</strong> Helps verify artifact integrity &#x26; publisher identity.</p> |
|     3 | <p><strong>Cosign</strong><br><br><strong><code>Link(s)</code>:</strong> <a href="https://github.com/sigstore/cosign">github.com/sigstore/cosign</a><br><br><strong><code>Access / Cost</code>:</strong> Free / open-source public GitHub repo</p>                                                           | <p><strong><code>Relevance</code>:</strong> Container/artifact signing tool.<br><br><strong><code>Notes &#x26; POIs</code>:</strong> Useful for verifying container image provenance.</p>                              |
|     4 | <p><strong>Rekor</strong><br><br><strong><code>Link(s)</code>:</strong> <a href="https://docs.sigstore.dev/logging/overview/">docs.sigstore.dev/logging/overview</a><br><br><strong><code>Access / Cost</code>:</strong> Free public docs / public transparency log</p>                                      | <p><strong><code>Relevance</code>:</strong> Transparency log for signed artifacts.<br><br><strong><code>Notes &#x26; POIs</code>:</strong> Useful for auditability &#x26; tamper detection.</p>                        |
|     5 | <p><strong>in-toto</strong><br><br><strong><code>Link(s)</code>:</strong> <a href="https://in-toto.io/">in-toto.io</a><br><br><strong><code>Access / Cost</code>:</strong> Free / open-source</p>                                                                                                            | <p><strong><code>Relevance</code>:</strong> Supply-chain integrity framework.<br><br><strong><code>Notes &#x26; POIs</code>:</strong> Useful for verifying build steps &#x26; provenance attestations.</p>             |
|     6 | <p><strong>The Update Framework - TUF</strong><br><br><strong><code>Link(s)</code>:</strong> <a href="https://theupdateframework.io/">theupdateframework.io</a><br><br><strong><code>Access / Cost</code>:</strong> Free / open-source</p>                                                                   | <p><strong><code>Relevance</code>:</strong> Secure software update framework.<br><br><strong><code>Notes &#x26; POIs</code>:</strong> Useful for update-channel compromise resistance.</p>                             |
|     7 | <p><strong>SLSA GitHub generators</strong><br><br><strong><code>Link(s)</code>:</strong> <a href="https://github.com/slsa-framework/slsa-github-generator">github.com/slsa-framework/slsa-github-generator</a><br><br><strong><code>Access / Cost</code>:</strong> Free / open-source public GitHub repo</p> | <p><strong><code>Relevance</code>:</strong> GitHub-based SLSA provenance generators.<br><br><strong><code>Notes &#x26; POIs</code>:</strong> Useful for CI/CD provenance generation.</p>                               |

## 14.2 Dependency inventory & graphing

| Sl. # | Source Title          | Notes                                                             |
| ----: | --------------------- | ----------------------------------------------------------------- |
|     1 | deps.dev              | [deps.dev](https://deps.dev/)                                     |
|     2 | GUAC                  | [guac.sh](https://guac.sh/)                                       |
|     3 | GUAC GitHub           | [github.com/guacsec/guac](https://github.com/guacsec/guac)        |
|     4 | OpenSSF Scorecard     | [github.com/ossf/scorecard](https://github.com/ossf/scorecard)    |
|     5 | OpenSSF Scorecard API | [api.securityscorecards.dev](https://api.securityscorecards.dev/) |
|     6 | Maven Central         | [central.sonatype.com](https://central.sonatype.com/)             |
|     7 | npm registry          | [registry.npmjs.org](https://registry.npmjs.org/)                 |
|     8 | PyPI JSON API         | [docs.pypi.org/api/json](https://docs.pypi.org/api/json/)         |
|     9 | crates.io API         | [crates.io/data-access](https://crates.io/data-access)            |
|    10 | Go module proxy       | [proxy.golang.org](https://proxy.golang.org/)                     |

> #### [_Back to **`Index`**_](14-14-source-code-dependency-artifact-and-build-chain-provenance.md#index)

***

***

## Discussion

This chapter section keeps the latest table structure, source titles, access/cost fields, relevance notes, & operational notes from the source inventory. Review the table entries as ingestion candidates, then validate source freshness, licensing, authentication requirements, & link-check behavior before production use.

***

#### [Back to Index](../01-index.md)
