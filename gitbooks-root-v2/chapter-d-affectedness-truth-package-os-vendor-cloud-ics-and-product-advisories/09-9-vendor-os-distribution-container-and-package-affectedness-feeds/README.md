# 9. Vendor, OS, distribution, container & package affectedness feeds

## 9.1 Scanner-oriented aggregators & vulnerability DB builders
| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **NeuVector vul-dbgen**<br><br>**`Link(s)`:** [github.com/neuvector/vul-dbgen](https://github.com/neuvector/vul-dbgen)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** Vulnerability DB generation source originally flagged by this project.<br><br>**`Notes & POIs`:** Useful as a reference for aggregating distro/package vulnerability feeds. |
| 2 | **NeuVector vul-source**<br><br>**`Link(s)`:** [github.com/neuvector/vul-source](https://github.com/neuvector/vul-source)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** Vulnerability source data used by NeuVector workflows.<br><br>**`Notes & POIs`:** Review for source coverage & feed normalization logic. |
| 3 | **Aqua Trivy vulnerability docs**<br><br>**`Link(s)`:** [trivy.dev/docs/latest/scanner/vulnerability](https://trivy.dev/docs/latest/scanner/vulnerability/)<br><br>**`Access / Cost`:** Free public docs | **`Relevance`:** Scanner behavior across OS packages, language packages, misconfig, Kubernetes, etc.<br><br>**`Notes & POIs`:** Useful for scanner semantics & supported target types. |
| 4 | **Trivy DB**<br><br>**`Link(s)`:** [github.com/aquasecurity/trivy-db](https://github.com/aquasecurity/trivy-db)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** Converts raw advisories into Trivy DB format.<br><br>**`Notes & POIs`:** Useful for ingestion architecture & feed normalization patterns. |
| 5 | **Trivy Java DB**<br><br>**`Link(s)`:** [github.com/aquasecurity/trivy-java-db](https://github.com/aquasecurity/trivy-java-db)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** Java-specific vulnerability database used by Trivy.<br><br>**`Notes & POIs`:** Useful for Maven/JAR matching. |
| 6 | **Trivy database configuration docs**<br><br>**`Link(s)`:** [trivy.dev/docs/latest/configuration/db](https://trivy.dev/docs/latest/configuration/db/)<br><br>**`Access / Cost`:** Free public docs | **`Relevance`:** Documents Trivy DB artifacts & configuration.<br><br>**`Notes & POIs`:** Useful for operational scanner deployment. |
| 7 | **Anchore Grype**<br><br>**`Link(s)`:** [github.com/anchore/grype](https://github.com/anchore/grype)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** Vulnerability scanner for container images & filesystems.<br><br>**`Notes & POIs`:** Useful reference for SBOM-to-vuln matching. |
| 8 | **Anchore Grype DB**<br><br>**`Link(s)`:** [github.com/anchore/grype-db](https://github.com/anchore/grype-db)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** Builds Grype vulnerability database from upstream sources.<br><br>**`Notes & POIs`:** Useful for feed normalization & source coverage comparison. |
| 9 | **Anchore Syft**<br><br>**`Link(s)`:** [github.com/anchore/syft](https://github.com/anchore/syft)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** SBOM generation for scanning & exposure matching.<br><br>**`Notes & POIs`:** Pair with Grype for inventory-to-vulnerability workflow. |
| 10 | **Quay ClairCore**<br><br>**`Link(s)`:** [github.com/quay/claircore](https://github.com/quay/claircore)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** Clair vulnerability matching engine core.<br><br>**`Notes & POIs`:** Useful for container security ingestion patterns. |
| 11 | **Clair**<br><br>**`Link(s)`:** [github.com/quay/clair](https://github.com/quay/clair)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** Container vulnerability scanner.<br><br>**`Notes & POIs`:** Compare feed matching behavior with Trivy & Grype. |
| 12 | **VulnerableCode**<br><br>**`Link(s)`:** [github.com/nexB/vulnerablecode](https://github.com/nexB/vulnerablecode)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** Open vulnerability DB aggregator.<br><br>**`Notes & POIs`:** Useful for importer coverage & open-source ingestion architecture. |
| 13 | **VulnerableCode importer docs**<br><br>**`Link(s)`:** [vulnerablecode.readthedocs.io/en/latest/importers_link.html](https://vulnerablecode.readthedocs.io/en/latest/importers_link.html)<br><br>**`Access / Cost`:** Free public docs | **`Relevance`:** Lists supported importer sources.<br><br>**`Notes & POIs`:** Good checklist for source coverage. |
| 14 | **Dependency-Track**<br><br>**`Link(s)`:** [dependencytrack.org](https://dependencytrack.org/)<br><br>**`Access / Cost`:** Free / open-source core project | **`Relevance`:** SBOM-oriented vulnerability management platform.<br><br>**`Notes & POIs`:** Useful reference for BOM ingestion & component risk tracking. |
| 15 | **Dependency-Track data sources**<br><br>**`Link(s)`:** [docs.dependencytrack.org/datasources/overview](https://docs.dependencytrack.org/datasources/overview/)<br><br>**`Access / Cost`:** Free public docs | **`Relevance`:** Documents Dependency-Track data sources.<br><br>**`Notes & POIs`:** Useful for comparing source prioritization. |
| 16 | **Dependency-Track GitHub Advisories datasource**<br><br>**`Link(s)`:** [docs.dependencytrack.org/datasources/github-advisories](https://docs.dependencytrack.org/datasources/github-advisories/)<br><br>**`Access / Cost`:** Free public docs | **`Relevance`:** Mirrors GHSA via GitHub public GraphQL API.<br><br>**`Notes & POIs`:** Useful reference for GHSA ingestion. |
| 17 | **OpenVAS / Greenbone Community Feed**<br><br>**`Link(s)`:** [www.greenbone.net/en/community-feed](https://www.greenbone.net/en/community-feed/)<br><br>**`Access / Cost`:** Free community feed; commercial Greenbone feeds/products available | **`Relevance`:** Network vulnerability test feed.<br><br>**`Notes & POIs`:** Useful for host/network exposure detection, not package-only matching. |
| 18 | **Wazuh vulnerability detector**<br><br>**`Link(s)`:** [documentation.wazuh.com/current/user-manual/capabilities/vulnerability- detection/index.html](https://documentation.wazuh.com/current/user-manual/capabilities/vulnerability-detection/index.html)<br><br>**`Access / Cost`:** Free public docs; Wazuh open-source, commercial support available | **`Relevance`:** Endpoint vulnerability detection capability.<br><br>**`Notes & POIs`:** Useful for host-level package inventory & vuln matching behavior. |
| 19 | **OSV-SCALIBR**<br><br>**`Link(s)`:** [github.com/google/osv-scalibr](https://github.com/google/osv-scalibr)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** Google library for Software Composition Analysis.<br><br>**`Notes & POIs`:** Useful for SCA implementation patterns, package/component extraction, vulnerability matching, & OSV-aligned workflows. |
| 20 | **HarborGuard**<br><br>**`Link(s)`:** [github.com/HarborGuard/HarborGuard](https://github.com/HarborGuard/HarborGuard)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** Image vulnerability scanning & patching platform with multi-tool integration.<br><br>**`Notes & POIs`:** Relevant to container/image vulnerability management, scanner orchestration, & remediation workflow automation. |

## 9.2 Red Hat / RHEL / CentOS Stream

| Sl. # | Source Title | Notes |
|---:|---|---|
| ---: | **---**<br><br>**`Link(s)`:** ---<br><br>**`Access / Cost`:** --- | **`Relevance`:** ---<br><br>**`Notes & POIs`:** --- |
| 1 | **Red Hat Security Data**<br><br>**`Link(s)`:** [access.redhat.com/security/data](https://access.redhat.com/security/data)<br><br>**`Access / Cost`:** Free public data; some product details/support content may require subscription | **`Relevance`:** Red Hat CSAF/VEX, OSV, OVAL, CVE data.<br><br>**`Notes & POIs`:** Essential for RHEL affectedness & backport-aware status. |
| 2 | **Red Hat Security Data API**<br><br>**`Link(s)`:** [docs.redhat.com/en/documentation/red_hat_security_data_api/1.0/html- single/red_hat_security_data_api/index](https://docs.redhat.com/en/documentation/red_hat_security_data_api/1.0/html-single/red_hat_security_data_api/index)<br><br>**`Access / Cost`:** Free public docs/API; support content may require subscription | **`Relevance`:** API retrieves Red Hat CVE/advisory/security data.<br><br>**`Notes & POIs`:** Prefer API for automation; handle auth/rate constraints if applicable. |
| 3 | **Red Hat CVE database**<br><br>**`Link(s)`:** [access.redhat.com/security/security-updates/#/cve](https://access.redhat.com/security/security-updates/#/cve)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Red Hat CVE lookup.<br><br>**`Notes & POIs`:** Human-facing; use data APIs for automation. |
| 4 | **Red Hat OVAL data**<br><br>**`Link(s)`:** [www.redhat.com/security/data/oval](https://www.redhat.com/security/data/oval/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** OVAL definitions for vulnerability assessment.<br><br>**`Notes & POIs`:** Useful for scanner compatibility & package-state evaluation. |
| 5 | **Red Hat CSAF/VEX guidance**<br><br>**`Link(s)`:** [redhatproductsecurity.github.io/security-data-guidelines/csaf-vex](https://redhatproductsecurity.github.io/security-data-guidelines/csaf-vex/)<br><br>**`Access / Cost`:** Free public docs | **`Relevance`:** Explains Red Hat CSAF/VEX & product/package semantics.<br><br>**`Notes & POIs`:** Important for correct interpretation of affected/not-affected states. |
| 6 | **Red Hat security advisories**<br><br>**`Link(s)`:** [access.redhat.com/security/security-updates/#/security-advisories](https://access.redhat.com/security/security-updates/#/security-advisories)<br><br>**`Access / Cost`:** Free public listing; some advisory/product support details may require subscription | **`Relevance`:** Red Hat advisory listing.<br><br>**`Notes & POIs`:** Useful for patch/remediation references. |
| 7 | **CentOS Stream security tracker**<br><br>**`Link(s)`:** [gitlab.com/redhat/centos-stream/rpms](https://gitlab.com/redhat/centos-stream/rpms)<br><br>**`Access / Cost`:** Free public GitLab | **`Relevance`:** CentOS Stream package source context.<br><br>**`Notes & POIs`:** Use carefully; package repo state differs from security advisory truth. |

## 9.3 Debian

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **Debian Security Tracker**<br><br>**`Link(s)`:** [security-tracker.debian.org](https://security-tracker.debian.org/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Debian-specific package vulnerability status.<br><br>**`Notes & POIs`:** Essential for Debian affectedness & backported patches. |
| 2 | **Debian Security Tracker JSON**<br><br>**`Link(s)`:** [security-tracker.debian.org/tracker/data/json](https://security-tracker.debian.org/tracker/data/json)<br><br>**`Access / Cost`:** Free public JSON | **`Relevance`:** Machine-readable Debian vulnerability data.<br><br>**`Notes & POIs`:** Primary automation source for Debian. |
| 3 | **Debian Security Tracker source Git**<br><br>**`Link(s)`:** [salsa.debian.org/security-tracker-team/security-tracker](https://salsa.debian.org/security-tracker-team/security-tracker)<br><br>**`Access / Cost`:** Free / open-source public Git repo | **`Relevance`:** Source repo for tracker data.<br><br>**`Notes & POIs`:** Useful for diffs, auditing, & local mirroring. |
| 4 | **Debian Security Information**<br><br>**`Link(s)`:** [www.debian.org/security](https://www.debian.org/security/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Debian security notices & process context.<br><br>**`Notes & POIs`:** Useful for advisory references & manual review. |
| 5 | **Debian Security Tracker docs**<br><br>**`Link(s)`:** [security-team.debian.org/security_tracker.html](https://security-team.debian.org/security_tracker.html)<br><br>**`Access / Cost`:** Free public docs | **`Relevance`:** Explains Debian tracker semantics.<br><br>**`Notes & POIs`:** Important for interpreting statuses like fixed, vulnerable, ignored, or postponed. |
| 6 | **Debian OVAL**<br><br>**`Link(s)`:** [www.debian.org/security/oval](https://www.debian.org/security/oval/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** OVAL data for Debian vulnerability assessment.<br><br>**`Notes & POIs`:** Useful for scanner integrations. |

## 9.4 Ubuntu / Canonical

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **Ubuntu Security Notices**<br><br>**`Link(s)`:** [ubuntu.com/security/notices](https://ubuntu.com/security/notices)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Ubuntu security notices for fixed packages.<br><br>**`Notes & POIs`:** Useful for patch references & release-specific remediation. |
| 2 | **Ubuntu CVE reports**<br><br>**`Link(s)`:** [ubuntu.com/security/cves](https://ubuntu.com/security/cves)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Ubuntu CVE tracking by package/release.<br><br>**`Notes & POIs`:** Important for Ubuntu affectedness & backport interpretation. |
| 3 | **Ubuntu OVAL**<br><br>**`Link(s)`:** [ubuntu.com/security/oval](https://ubuntu.com/security/oval)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** OVAL data for vulnerability assessment & patch status.<br><br>**`Notes & POIs`:** Useful for scanner compatibility. |
| 4 | **Ubuntu VEX data**<br><br>**`Link(s)`:** [ubuntu.com/security/vex](https://ubuntu.com/security/vex)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Ubuntu VEX data.<br><br>**`Notes & POIs`:** Useful for affected/not-affected status & scanner false-positive reduction. |
| 5 | **Ubuntu VEX docs**<br><br>**`Link(s)`:** [documentation.ubuntu.com/security/security-updates/vex](https://documentation.ubuntu.com/security/security-updates/vex/)<br><br>**`Access / Cost`:** Free public docs | **`Relevance`:** Ubuntu VEX source documentation.<br><br>**`Notes & POIs`:** Important for interpreting Canonical VEX publication model. |
| 6 | **Ubuntu Security Notices GitHub**<br><br>**`Link(s)`:** [github.com/canonical/ubuntu-security-notices](https://github.com/canonical/ubuntu-security-notices)<br><br>**`Access / Cost`:** Free public GitHub repo | **`Relevance`:** USN/LSN JSON, OSV JSON, & OpenVEX JSON formats.<br><br>**`Notes & POIs`:** Strong automation source. Preserve format-specific semantics. |
| 7 | **Ubuntu Security Tracker Git**<br><br>**`Link(s)`:** [git.launchpad.net/ubuntu-cve-tracker](https://git.launchpad.net/ubuntu-cve-tracker)<br><br>**`Access / Cost`:** Free public Git repo | **`Relevance`:** Ubuntu CVE tracker source.<br><br>**`Notes & POIs`:** Useful for local mirroring & historical diffing. |
| 8 | **Ubuntu security updates docs**<br><br>**`Link(s)`:** [documentation.ubuntu.com/security/security-updates](https://documentation.ubuntu.com/security/security-updates/)<br><br>**`Access / Cost`:** Free public docs | **`Relevance`:** Ubuntu security update documentation.<br><br>**`Notes & POIs`:** Useful for process context & VEX/OVAL interpretation. |

## 9.5 Alpine

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **Alpine SecDB**<br><br>**`Link(s)`:** [secdb.alpinelinux.org](https://secdb.alpinelinux.org/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Current Alpine machine-readable security DB.<br><br>**`Notes & POIs`:** Primary Alpine ingestion source. |
| 2 | **Alpine Security Tracker**<br><br>**`Link(s)`:** [security.alpinelinux.org](https://security.alpinelinux.org/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Tracks Alpine security issues.<br><br>**`Notes & POIs`:** Useful for human review & status context. |
| 3 | **Alpine SecDB deprecated GitHub mirror**<br><br>**`Link(s)`:** [github.com/alpinelinux/alpine-secdb](https://github.com/alpinelinux/alpine-secdb)<br><br>**`Access / Cost`:** Free public GitHub repo; deprecated | **`Relevance`:** Historical Alpine SecDB mirror.<br><br>**`Notes & POIs`:** Deprecated; do not rely on it for current ingestion. |
| 4 | **Alpine packages**<br><br>**`Link(s)`:** [pkgs.alpinelinux.org/packages](https://pkgs.alpinelinux.org/packages)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Alpine package metadata.<br><br>**`Notes & POIs`:** Not a vulnerability DB, but helps resolve package names & versions. |

## 9.6 SUSE / openSUSE

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **SUSE CSAF**<br><br>**`Link(s)`:** [www.suse.com/support/security/csaf](https://www.suse.com/support/security/csaf/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** SUSE CSAF advisory data.<br><br>**`Notes & POIs`:** Good for vendor-asserted affectedness & remediation states. |
| 2 | **SUSE CVRF / OVAL security data**<br><br>**`Link(s)`:** [www.suse.com/support/security/oval](https://www.suse.com/support/security/oval/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** SUSE OVAL/CVRF security data.<br><br>**`Notes & POIs`:** Useful for scanner compatibility & package-state evaluation. |
| 3 | **SUSE CVE pages**<br><br>**`Link(s)`:** [www.suse.com/security/cve](https://www.suse.com/security/cve/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** SUSE CVE lookup.<br><br>**`Notes & POIs`:** Human-facing; use machine-readable feeds when available. |
| 4 | **SUSE Security Advisories**<br><br>**`Link(s)`:** [www.suse.com/support/update/announcement](https://www.suse.com/support/update/announcement/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** SUSE security advisory listing.<br><br>**`Notes & POIs`:** Useful for remediation & patch references. |
| 5 | **openSUSE Security Announce**<br><br>**`Link(s)`:** [lists.opensuse.org/archives/list/security-announce@lists.opensuse.org](https://lists.opensuse.org/archives/list/security-announce@lists.opensuse.org/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** openSUSE security announcement mailing list archive.<br><br>**`Notes & POIs`:** Useful for distro-specific disclosure context. |

## 9.7 Oracle Linux

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **Oracle Security Alerts & Critical Patch Updates**<br><br>**`Link(s)`:** [www.oracle.com/security-alerts](https://www.oracle.com/security-alerts/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Oracle CPU, Security Alerts, third-party bulletins, & CVE mappings.<br><br>**`Notes & POIs`:** Oracle products often require vendor advisory interpretation beyond NVD. |
| 2 | **Oracle Linux security data**<br><br>**`Link(s)`:** [linux.oracle.com/security](https://linux.oracle.com/security/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Oracle Linux security data.<br><br>**`Notes & POIs`:** Useful for Oracle Linux affectedness. |
| 3 | **Oracle Linux OVAL**<br><br>**`Link(s)`:** [linux.oracle.com/security/oval](https://linux.oracle.com/security/oval/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Oracle Linux OVAL definitions.<br><br>**`Notes & POIs`:** Useful for scanner compatibility. |

| 4 | Oracle Linux errata | [linux.oracle.com/errata](https://linux.oracle.com/errata/) | Free public | Oracle Linux errata. | Use for patch mapping & fixed versions. |
| 5 | Oracle Linux CVE search | [linux.oracle.com/cve](https://linux.oracle.com/cve/) | Free public | Oracle Linux CVE lookup. | Human lookup source; pair with OVAL/errata for automation. |

## 9.8 Amazon Linux

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **Amazon Linux Security Center**<br><br>**`Link(s)`:** [alas.aws.amazon.com](https://alas.aws.amazon.com/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Amazon Linux security advisory portal.<br><br>**`Notes & POIs`:** Important for Amazon Linux package affectedness. |
| 2 | **Amazon Linux ALAS Explorer**<br><br>**`Link(s)`:** [explore.alas.aws.amazon.com](https://explore.alas.aws.amazon.com/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Search/explore interface for Amazon Linux advisories.<br><br>**`Notes & POIs`:** Useful for manual triage & ALAS advisory lookup. |
| 3 | **Amazon Linux 2 advisories**<br><br>**`Link(s)`:** [alas.aws.amazon.com/alas2.html](https://alas.aws.amazon.com/alas2.html)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Amazon Linux 2 advisories.<br><br>**`Notes & POIs`:** Version-specific advisory stream. |
| 4 | **Amazon Linux 2023 advisories**<br><br>**`Link(s)`:** [alas.aws.amazon.com/AL2023](https://alas.aws.amazon.com/AL2023/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Amazon Linux 2023 advisories.<br><br>**`Notes & POIs`:** Keep AL2 & AL2023 separate because package baselines differ. |
| 5 | **AWS Security Bulletins**<br><br>**`Link(s)`:** [aws.amazon.com/security/security-bulletins](https://aws.amazon.com/security/security-bulletins/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** AWS security bulletins for services & platforms.<br><br>**`Notes & POIs`:** Cloud-service affectedness may not map cleanly to package versions. |
| 6 | **Amazon Linux 2023 GitHub repository**<br><br>**`Link(s)`:** [github.com/amazonlinux/amazon-linux-2023](https://github.com/amazonlinux/amazon-linux-2023)<br><br>**`Access / Cost`:** Free public GitHub repo | **`Relevance`:** Amazon Linux 2023 project repository.<br><br>**`Notes & POIs`:** Useful for Amazon Linux 2023 package context, release notes, source/package metadata references, & distro-specific affectedness workflows. |

## 9.9 Fedora, AlmaLinux, Rocky, Arch, Gentoo

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **Fedora security updates**<br><br>**`Link(s)`:** [bodhi.fedoraproject.org/updates/?type=security](https://bodhi.fedoraproject.org/updates/?type=security)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Fedora security update advisories.<br><br>**`Notes & POIs`:** Useful for Fedora package remediation tracking. |
| 2 | **Fedora packages**<br><br>**`Link(s)`:** [packages.fedoraproject.org](https://packages.fedoraproject.org/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Fedora package metadata.<br><br>**`Notes & POIs`:** Not a vulnerability DB, but useful for package identity & version resolution. |
| 3 | **Fedora packages static - Pagure**<br><br>**`Link(s)`:** [pagure.io/fedora-packages-static](https://pagure.io/fedora-packages-static)<br><br>**`Access / Cost`:** Free public Pagure project; manually revalidate | **`Relevance`:** Fedora package-name & metadata/script reference.<br><br>**`Notes & POIs`:** Keep in link-check allowlist until manually validated; not a primary security advisory source. |
| 4 | **AlmaLinux Errata**<br><br>**`Link(s)`:** [errata.almalinux.org](https://errata.almalinux.org/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** AlmaLinux errata & security advisories.<br><br>**`Notes & POIs`:** Useful for RHEL-compatible distro assessment. |
| 5 | **AlmaLinux OSV data**<br><br>**`Link(s)`:** [github.com/AlmaLinux/osv-database](https://github.com/AlmaLinux/osv-database)<br><br>**`Access / Cost`:** Free public GitHub repo | **`Relevance`:** AlmaLinux OSV-formatted data.<br><br>**`Notes & POIs`:** Good for OSV-based pipelines. |
| 6 | **Rocky Linux security advisories**<br><br>**`Link(s)`:** [errata.build.resf.org](https://errata.build.resf.org/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Rocky Linux errata/security advisories.<br><br>**`Notes & POIs`:** Useful for RHEL-compatible distro assessment. |
| 7 | **Arch Linux Security Tracker**<br><br>**`Link(s)`:** [security.archlinux.org](https://security.archlinux.org/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Arch Linux security tracker.<br><br>**`Notes & POIs`:** Rolling-release semantics differ from fixed-release distros. |
| 8 | **Arch Linux security JSON**<br><br>**`Link(s)`:** [security.archlinux.org/json](https://security.archlinux.org/json)<br><br>**`Access / Cost`:** Free public JSON | **`Relevance`:** Machine-readable Arch security data.<br><br>**`Notes & POIs`:** Useful for automation. |
| 9 | **Gentoo GLSA**<br><br>**`Link(s)`:** [security.gentoo.org/glsa](https://security.gentoo.org/glsa/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Gentoo Linux Security Advisories.<br><br>**`Notes & POIs`:** Useful for Gentoo package affectedness. |
| 10 | **Gentoo GLSA XML**<br><br>**`Link(s)`:** [security.gentoo.org/glsa/feed.rss](https://security.gentoo.org/glsa/feed.rss)<br><br>**`Access / Cost`:** Free public RSS/XML | **`Relevance`:** Gentoo GLSA RSS/XML feed.<br><br>**`Notes & POIs`:** Useful for feed-based monitoring. |

## 9.10 Wolfi / Chainguard

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **Wolfi OS advisories**<br><br>**`Link(s)`:** [github.com/wolfi-dev/advisories](https://github.com/wolfi-dev/advisories)<br><br>**`Access / Cost`:** Free public GitHub repo | **`Relevance`:** Wolfi OS advisory data.<br><br>**`Notes & POIs`:** Important for modern minimal container images. |
| 2 | **Wolfi SecDB generator**<br><br>**`Link(s)`:** [github.com/wolfi-dev/secdb](https://github.com/wolfi-dev/secdb)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** Generates Wolfi security DBs based on Alpine secdb format.<br><br>**`Notes & POIs`:** Useful for understanding feed generation semantics. |
| 3 | **Wolfi OS feed**<br><br>**`Link(s)`:** [packages.wolfi.dev/os/security.json](https://packages.wolfi.dev/os/security.json)<br><br>**`Access / Cost`:** Free public feed | **`Relevance`:** Wolfi package security feed.<br><br>**`Notes & POIs`:** Use this for Wolfi base images. |
| 4 | **Chainguard Enterprise feed**<br><br>**`Link(s)`:** [packages.cgr.dev/chainguard/security.json](https://packages.cgr.dev/chainguard/security.json)<br><br>**`Access / Cost`:** Publicly reachable feed; may relate to commercial Chainguard product scope | **`Relevance`:** Chainguard Enterprise package security feed.<br><br>**`Notes & POIs`:** Separate from Wolfi OS feed. Confirm entitlement/licensing before commercial redistribution. |
| 5 | Chainguard security advisories docs | [edu.chainguard.dev/chainguard/chainguard-images/staying- secure/security-advisories/how-chainguard-issues](https://edu.chainguard.dev/chainguard/chainguard-images/staying-secure/security-advisories/how-chainguard-issues/) | Free public docs | Explains Chainguard advisory publication model. | Important for interpreting feed semantics & OSV/secdb transition. |
| 6 | Wolfi vulnerabilities in OSV | [osv.dev/list?ecosystem=Wolfi](https://osv.dev/list?ecosystem=Wolfi) | Free public | Wolfi ecosystem records in OSV. | Good for OSV-aligned ingestion. |
| 7 | Chainguard OSV advisory feed context | [www.chainguard.dev/unchained/chainguard-enhances-security-with- osv-advisory-feed](https://www.chainguard.dev/unchained/chainguard-enhances-security-with-osv-advisory-feed) | Free public blog | Context on Chainguard OSV advisory feed. | Blog/context source, not primary feed. |

> 
> #### [*Back to **`Index`***](#index)
---

## Discussion

This chapter section keeps the latest table structure, source titles, access/cost fields, relevance notes, & operational notes from the source inventory. Review the table entries as ingestion candidates, then validate source freshness, licensing, authentication requirements, & link-check behavior before production use.

---

#### [Back to Index](../../01-index.md)
