# 16.4 Environmental impact

| Sl. # | Title | Link(s) | Access / Cost | Relevance | Notes & POIs |
|---:|---|---|---|---|---|
| 1 | Asset criticality | [www.cisecurity.org/controls](https://www.cisecurity.org/controls) | Free public | Business/system importance affects risk. | Must come from internal asset inventory. |
| 2 | Internet exposure | [search.censys.io](https://search.censys.io/), [www.shodan.io](https://www.shodan.io/) | Free tiers / paid plans | Determines external exploitability surface. | External scan data may be incomplete or stale. |
| 3 | Network reachability | [nmap.org](https://nmap.org/) | Free / open-source | Determines whether an exploit path exists. | Internal network context required. |
| 4 | Authentication required | [www.first.org/cvss](https://www.first.org/cvss/) | Free public | Impacts exploitability. | CVSS may not capture local compensating controls. |
| 5 | Privilege required | [www.first.org/cvss](https://www.first.org/cvss/) | Free public | Impacts exploitability & blast radius. | Validate with product configuration. |
| 6 | User interaction required | [www.first.org/cvss](https://www.first.org/cvss/) | Free public | Impacts exploitability conditions. | User interaction can be bypassed in some real-world chains. |
| 7 | Exploit preconditions | [googleprojectzero.blogspot.com](https://googleprojectzero.blogspot.com/), [www.kb.cert.org/vuls](https://www.kb.cert.org/vuls/) | Free public | Defines required configuration or state. | Crucial for false-positive reduction. |
| 8 | Data sensitivity | [www.cisecurity.org/controls](https://www.cisecurity.org/controls) | Free public | Determines business impact. | Internal classification required. |
| 9 | Compensating controls | [public.cyber.mil/stigs](https://public.cyber.mil/stigs/), [www.cisecurity.org/cis-benchmarks](https://www.cisecurity.org/cis-benchmarks) | Free public; CIS benchmarks may require free registration | Controls can reduce practical exploitability. | Document assumptions & evidence. |
| 10 | Runtime configuration | [docs.dependencytrack.org/datasources/overview](https://docs.dependencytrack.org/datasources/overview/) | Free public docs | Enabled features/modules influence affectedness. | Scanner package matches alone can over-report. |
| 11 | Feature/module enabled | [github.com/openvex/spec](https://github.com/openvex/spec) | Free / open-source | VEX not-affected reasoning may depend on disabled code paths. | Requires product/runtime evidence. |
| 12 | Cloud account/project/environment | [github.com/prowler-cloud/prowler](https://github.com/prowler-cloud/prowler) | Free / open-source core; commercial products separate | Cloud context affects exposure & blast radius. | Join vulnerability data with cloud inventory. |
| 13 | Blast radius | [github.com/salesforce/cloudsplaining](https://github.com/salesforce/cloudsplaining) | Free / open-source | Privilege & dependency spread determine impact. | Requires IAM, network, & data-flow context. |
| 14 | Business process ownership | [www.cisecurity.org/controls](https://www.cisecurity.org/controls) | Free public | Ownership determines remediation accountability. | Internal data source required. |
