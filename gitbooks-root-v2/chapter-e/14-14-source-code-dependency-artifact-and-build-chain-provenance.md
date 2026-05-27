---
layout:
  width: wide
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
  metadata:
    visible: true
  tags:
    visible: true
  actions:
    visible: true
---

# 14. Source-code, dependency, artifact & build-chain provenance

## 14.1 Source & artifact provenance

<table><thead><tr><th width="87.5" align="right">Sl. #</th><th>Source Title</th><th>Notes</th></tr></thead><tbody><tr><td align="right">1</td><td><strong>SLSA</strong><br><br><strong><code>Link(s)</code>:</strong> <a href="https://slsa.dev/">slsa.dev</a><br><br><strong><code>Access / Cost</code>:</strong> Free / open standard</td><td><strong><code>Relevance</code>:</strong> Supply-chain Levels for Software Artifacts.<br><br><strong><code>Notes &#x26; POIs</code>:</strong> Useful for evaluating build integrity &#x26; provenance risk.</td></tr><tr><td align="right">2</td><td><strong>Sigstore</strong><br><br><strong><code>Link(s)</code>:</strong> <a href="https://www.sigstore.dev/">www.sigstore.dev</a><br><br><strong><code>Access / Cost</code>:</strong> Free / open-source public infrastructure</td><td><strong><code>Relevance</code>:</strong> Signing &#x26; verification for software artifacts.<br><br><strong><code>Notes &#x26; POIs</code>:</strong> Helps verify artifact integrity &#x26; publisher identity.</td></tr><tr><td align="right">3</td><td><strong>Cosign</strong><br><br><strong><code>Link(s)</code>:</strong> <a href="https://github.com/sigstore/cosign">github.com/sigstore/cosign</a><br><br><strong><code>Access / Cost</code>:</strong> Free / open-source public GitHub repo</td><td><strong><code>Relevance</code>:</strong> Container/artifact signing tool.<br><br><strong><code>Notes &#x26; POIs</code>:</strong> Useful for verifying container image provenance.</td></tr><tr><td align="right">4</td><td><strong>Rekor</strong><br><br><strong><code>Link(s)</code>:</strong> <a href="https://docs.sigstore.dev/logging/overview/">docs.sigstore.dev/logging/overview</a><br><br><strong><code>Access / Cost</code>:</strong> Free public docs / public transparency log</td><td><strong><code>Relevance</code>:</strong> Transparency log for signed artifacts.<br><br><strong><code>Notes &#x26; POIs</code>:</strong> Useful for auditability &#x26; tamper detection.</td></tr><tr><td align="right">5</td><td><strong>in-toto</strong><br><br><strong><code>Link(s)</code>:</strong> <a href="https://in-toto.io/">in-toto.io</a><br><br><strong><code>Access / Cost</code>:</strong> Free / open-source</td><td><strong><code>Relevance</code>:</strong> Supply-chain integrity framework.<br><br><strong><code>Notes &#x26; POIs</code>:</strong> Useful for verifying build steps &#x26; provenance attestations.</td></tr><tr><td align="right">6</td><td><strong>The Update Framework - TUF</strong><br><br><strong><code>Link(s)</code>:</strong> <a href="https://theupdateframework.io/">theupdateframework.io</a><br><br><strong><code>Access / Cost</code>:</strong> Free / open-source</td><td><strong><code>Relevance</code>:</strong> Secure software update framework.<br><br><strong><code>Notes &#x26; POIs</code>:</strong> Useful for update-channel compromise resistance.</td></tr><tr><td align="right">7</td><td><strong>SLSA GitHub generators</strong><br><br><strong><code>Link(s)</code>:</strong> <a href="https://github.com/slsa-framework/slsa-github-generator">github.com/slsa-framework/slsa-github-generator</a><br><br><strong><code>Access / Cost</code>:</strong> Free / open-source public GitHub repo</td><td><strong><code>Relevance</code>:</strong> GitHub-based SLSA provenance generators.<br><br><strong><code>Notes &#x26; POIs</code>:</strong> Useful for CI/CD provenance generation.</td></tr></tbody></table>

## 14.2 Dependency inventory & graphing

<table><thead><tr><th width="90.7265625" align="right">Sl. #</th><th width="281.15234375">Source Title</th><th width="286.78515625">Notes</th></tr></thead><tbody><tr><td align="right">1</td><td>deps.dev</td><td><a href="https://deps.dev/">deps.dev</a></td></tr><tr><td align="right">2</td><td>GUAC</td><td><a href="https://guac.sh/">guac.sh</a></td></tr><tr><td align="right">3</td><td>GUAC GitHub</td><td><a href="https://github.com/guacsec/guac">github.com/guacsec/guac</a></td></tr><tr><td align="right">4</td><td>OpenSSF Scorecard</td><td><a href="https://github.com/ossf/scorecard">github.com/ossf/scorecard</a></td></tr><tr><td align="right">5</td><td>OpenSSF Scorecard API</td><td><a href="https://api.securityscorecards.dev/">api.securityscorecards.dev</a></td></tr><tr><td align="right">6</td><td>Maven Central</td><td><a href="https://central.sonatype.com/">central.sonatype.com</a></td></tr><tr><td align="right">7</td><td>npm registry</td><td><a href="https://registry.npmjs.org/">registry.npmjs.org</a></td></tr><tr><td align="right">8</td><td>PyPI JSON API</td><td><a href="https://docs.pypi.org/api/json/">docs.pypi.org/api/json</a></td></tr><tr><td align="right">9</td><td>crates.io API</td><td><a href="https://crates.io/data-access">crates.io/data-access</a></td></tr><tr><td align="right">10</td><td>Go module proxy</td><td><a href="https://proxy.golang.org/">proxy.golang.org</a></td></tr></tbody></table>

> #### [_Back to **`Index`**_](14-14-source-code-dependency-artifact-and-build-chain-provenance.md#index)

***

***

## Discussion

This chapter section keeps the latest table structure, source titles, access/cost fields, relevance notes, & operational notes from the source inventory. Review the table entries as ingestion candidates, then validate source freshness, licensing, authentication requirements, & link-check behavior before production use.

***

#### [Back to Index](../index.md)
