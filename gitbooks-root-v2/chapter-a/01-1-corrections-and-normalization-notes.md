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

# 1. Corrections & normalization notes

<table><thead><tr><th width="90.4990234375" align="center">Sl. #</th><th>Source Title</th><th>Notes</th></tr></thead><tbody><tr><td align="center">1</td><td><strong>Project Zero issue tracker migration</strong><br><br><strong><code>Link(s)</code>:</strong> <br><a href="https://bugs.chromium.org/p/project-zero/issues/list">bugs.chromium.org/p/project-zero/issues/list</a>, <a href="https://project-zero.issues.chromium.org/issues">project-zero.issues.chromium.org/issues</a><br><br><strong><code>Access / Cost</code>:</strong> <br>Free public web access</td><td><strong><code>Relevance</code>:</strong><br>Tracks high-quality vulnerability research, root-cause analysis, exploitability notes, &#x26; coordinated disclosure. Useful for exploitability context &#x26; historical vulnerability behavior.<br><br><strong><code>Notes &#x26; POIs</code>:</strong> <br>Prefer the current tracker for ongoing lookups. Keep the old Monorail-style link for historical references that still appear in older write-ups.</td></tr><tr><td align="center">2</td><td><strong>Alpine SecDB mirror normalization</strong><br><br><strong><code>Link(s)</code>:</strong> <a href="https://github.com/alpinelinux/alpine-secdb">github.com/alpinelinux/alpine-secdb</a>, <a href="https://secdb.alpinelinux.org/">secdb.alpinelinux.org</a><br><br><strong><code>Access / Cost</code>:</strong> Free / open-source</td><td><strong><code>Relevance</code>:</strong> Provides Alpine package vulnerability affectedness. Important for container images using Alpine as a base.<br><br><strong><code>Notes &#x26; POIs</code>:</strong> The GitHub mirror is deprecated. Use <code>secdb.alpinelinux.org</code> as the primary ingestion source.</td></tr><tr><td align="center">3</td><td><strong>Wolfi / Chainguard feed split</strong><br><br><strong><code>Link(s)</code>:</strong> <a href="https://packages.cgr.dev/chainguard/security.json">packages.cgr.dev/chainguard/security.json</a>, <a href="https://packages.wolfi.dev/os/security.json">packages.wolfi.dev/os/security.json</a><br><br><strong><code>Access / Cost</code>:</strong> Free public feed for Wolfi; Chainguard feed may depend on product entitlement</td><td><strong><code>Relevance</code>:</strong> Provides Sec-db style security feeds for Wolfi &#x26; Chainguard images. Key for modern minimal container images.<br><br><strong><code>Notes &#x26; POIs</code>:</strong> The Wolfi feed &#x26; Chainguard Enterprise feed represent related but distinct package universes. Avoid treating them as exact duplicates.</td></tr><tr><td align="center">4</td><td><strong>GitHub Advisory APIs</strong><br><br><strong><code>Link(s)</code>:</strong> <a href="https://docs.github.com/en/graphql/reference/objects#securityadvisory">docs.github.com/en/graphql/reference/objects#securityadvisory</a>, <a href="https://docs.github.com/en/rest/security-advisories">docs.github.com/en/rest/security-advisories</a>, <a href="https://docs.github.com/en/rest/security-advisories/global-advisories">docs.github.com/en/rest/security-advisories/global-advisories</a><br><br><strong><code>Access / Cost</code>:</strong> Free public global advisories; authenticated API / repository advisories may require GitHub account &#x26; permissions</td><td><strong><code>Relevance</code>:</strong> Enables programmatic access to GitHub advisories, including GHSA records, CVE aliases, ecosystems, version ranges, &#x26; malware advisories.<br><br><strong><code>Notes &#x26; POIs</code>:</strong> Keep both GraphQL &#x26; REST. GraphQL is useful for complex queries; REST is simpler for ingestion &#x26; pagination.</td></tr><tr><td align="center">5</td><td><strong>NVD feeds vs APIs</strong><br><br><strong><code>Link(s)</code>:</strong> <a href="https://nvd.nist.gov/developers">nvd.nist.gov/developers</a>, <a href="https://nvd.nist.gov/vuln/data-feeds">nvd.nist.gov/vuln/data-feeds</a><br><br><strong><code>Access / Cost</code>:</strong> Free public; optional free API key for higher rate limits</td><td><strong><code>Relevance</code>:</strong> NVD provides CVE enrichment, CPE configurations, CVSS vectors, CWE mappings, references, &#x26; change metadata.<br><br><strong><code>Notes &#x26; POIs</code>:</strong> Prefer NVD 2.0 APIs for ongoing sync. Use bulk feeds for bootstrapping, archival snapshots, or local mirroring.</td></tr><tr><td align="center">6</td><td><strong>Link-check allowlist / restricted-source policy</strong><br><br><strong><code>Link(s)</code>:</strong> Vendor portals, support portals, API consoles, bot-blocked pages, JavaScript-heavy search pages<br><br><strong><code>Access / Cost</code>:</strong> Not a data source</td><td><strong><code>Relevance</code>:</strong> Avoids false “broken link” classifications in CI.<br><br><strong><code>Notes &#x26; POIs</code>:</strong> Treat <code>403</code>, bot-blocked, JS-only, rate-limited, auth-gated, &#x26; support-entitlement pages as <code>restricted/manual-review</code>, not automatically dead.</td></tr></tbody></table>

> #### [_Back to **`Index`**_](01-1-corrections-and-normalization-notes.md#index)
>
> ***

## Discussion

This chapter section keeps the latest table structure, source titles, access/cost fields, relevance notes, & operational notes from the source inventory. Review the table entries as ingestion candidates, then validate source freshness, licensing, authentication requirements, & link-check behavior before production use.

***

#### [Back to Index](../01-index.md)
