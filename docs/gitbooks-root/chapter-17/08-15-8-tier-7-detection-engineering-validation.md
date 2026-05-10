# 15.8 Tier 7 - detection engineering & validation

| Sl. # | Title | Link(s) | Access / Cost | Relevance | Notes & POIs |
|---:|---|---|---|---|---|
| 1 | CodeQL | [codeql.github.com](https://codeql.github.com/) | Free for many open-source uses; commercial GitHub Advanced Security for many enterprise/private workflows | Semantic code vulnerability detection. | Strong for variant analysis. |
| 2 | Semgrep | [semgrep.dev](https://semgrep.dev/) | Free/open-source CLI; commercial products available | Pattern-based static analysis. | Fast custom rules. |
| 3 | Joern | [joern.io](https://joern.io/) | Free / open-source | Code property graph analysis. | Useful for research & advanced detection. |
| 4 | Infer | [fbinfer.com](https://fbinfer.com/) | Free / open-source | Static analysis engine. | Good for specific bug classes. |
| 5 | Sonar rules | [rules.sonarsource.com](https://rules.sonarsource.com/) | Free public catalog; commercial Sonar products available | Security/code quality rule catalog. | Useful for rule taxonomy mapping. |
| 6 | Nuclei templates | [github.com/projectdiscovery/nuclei-templates](https://github.com/projectdiscovery/nuclei-templates) | Free / open-source | DAST/exposure templates. | Template quality varies. |
| 7 | OSS-Fuzz | [google.github.io/oss-fuzz](https://google.github.io/oss-fuzz/) | Free for eligible open-source projects | Continuous fuzzing. | Useful for discovery & OSV-linked vulns. |
| 8 | SARD / Juliet | [samate.nist.gov/SARD](https://samate.nist.gov/SARD/), [samate.nist.gov/SARD/test-suites/112](https://samate.nist.gov/SARD/test-suites/112) | Free public | Test suites for vulnerability detection. | Useful for evaluation; not production vulnerability feed. |
| 9 | Vulnerability datasets | [github.com/DLVulDet/PrimeVul](https://github.com/DLVulDet/PrimeVul), [github.com/Icyrockton/MegaVul](https://github.com/Icyrockton/MegaVul), [github.com/ZeoVan/MSR_20_Code_vulnerability_CSV_Dataset](https://github.com/ZeoVan/MSR_20_Code_vulnerability_CSV_Dataset), [github.com/secureIT-project/CVEfixes](https://github.com/secureIT-project/CVEfixes), [github.com/tuhh-softsec/vul4j](https://github.com/tuhh-softsec/vul4j), [github.com/wagner-group/diversevul](https://github.com/wagner-group/diversevul), [sites.google.com/view/devign](https://sites.google.com/view/devign) | Mostly free public research datasets; verify license individually | ML/research datasets for vulnerability detection. | Validate labels, leakage, deduplication, & licensing. |
> #### [*Back to **`Index`***](#index)
---
