# 16. Exposure, internet-facing asset & threat telemetry

## 16.1 Internet exposure search engines

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **Censys Search**<br><br>**`Link(s)`:** [search.censys.io](https://search.censys.io/)<br><br>**`Access / Cost`:** Free tier / paid plans | **`Relevance`:** Internet exposure search engine.<br><br>**`Notes & POIs`:** Useful for determining if vulnerable services are internet-facing. |
| 2 | **Censys API**<br><br>**`Link(s)`:** [search.censys.io/api](https://search.censys.io/api)<br><br>**`Access / Cost`:** Free tier / paid plans; API key required | **`Relevance`:** Programmatic Censys access.<br><br>**`Notes & POIs`:** API terms & quotas may apply. |
| 3 | **Shodan**<br><br>**`Link(s)`:** [www.shodan.io](https://www.shodan.io/)<br><br>**`Access / Cost`:** Free limited access / paid plans | **`Relevance`:** Internet-connected device search.<br><br>**`Notes & POIs`:** Useful for exposure discovery & banner-based matching. |
| 4 | **Shodan developer API**<br><br>**`Link(s)`:** [developer.shodan.io](https://developer.shodan.io/)<br><br>**`Access / Cost`:** Paid/API credit model may apply; account required | **`Relevance`:** Shodan API documentation.<br><br>**`Notes & POIs`:** Useful for automation. |
| 5 | ZoomEye | [www.zoomeye.org](https://www.zoomeye.org/) | Free limited access / paid plans | Internet asset search engine. | Useful as additional exposure telemetry. |
| 6 | FOFA | [fofa.info](https://fofa.info/) | Free limited access / paid plans | Internet asset search. | Coverage & access terms vary. |
| 7 | BinaryEdge | [www.binaryedge.io](https://www.binaryedge.io/) | Commercial / limited trial may exist | Internet scanning & threat intelligence. | Useful for external exposure enrichment. |
| 8 | Onyphe | [www.onyphe.io](https://www.onyphe.io/) | Free tier / paid plans | Cyber defense search engine. | Useful for passive/active exposure context. |
| 9 | SecurityTrails | [securitytrails.com](https://securitytrails.com/) | Free limited access / paid plans | DNS & asset intelligence. | Useful for attack surface discovery. |
| 10 | InternetDB by Shodan | [internetdb.shodan.io](https://internetdb.shodan.io/) | Free public API | Lightweight Shodan InternetDB API. | Useful for quick IP exposure enrichment. |

## 16.2 Scan/exploitation telemetry

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **GreyNoise Visualizer**<br><br>**`Link(s)`:** [viz.greynoise.io](https://viz.greynoise.io/)<br><br>**`Access / Cost`:** Free tier / paid plans | **`Relevance`:** Internet scanning/exploitation telemetry.<br><br>**`Notes & POIs`:** Helps separate background scanning from targeted activity. |
| 2 | **GreyNoise API docs**<br><br>**`Link(s)`:** [docs.greynoise.io](https://docs.greynoise.io/)<br><br>**`Access / Cost`:** Free tier / paid plans; API key required | **`Relevance`:** API docs for GreyNoise enrichment.<br><br>**`Notes & POIs`:** Useful for automated telemetry enrichment. |
| 3 | **Shadowserver**<br><br>**`Link(s)`:** [www.shadowserver.org](https://www.shadowserver.org/)<br><br>**`Access / Cost`:** Free for eligible organizations; registration may be required | **`Relevance`:** Internet-scale exposure & threat telemetry.<br><br>**`Notes & POIs`:** Good for population-level exposure signals. |
| 4 | **Shadowserver reports**<br><br>**`Link(s)`:** [dashboard.shadowserver.org](https://dashboard.shadowserver.org/)<br><br>**`Access / Cost`:** Free for eligible organizations; login/registration may be required | **`Relevance`:** Shadowserver reporting dashboard.<br><br>**`Notes & POIs`:** Access/eligibility may vary. |
| 5 | **SANS Internet Storm Center**<br><br>**`Link(s)`:** [isc.sans.edu](https://isc.sans.edu/)<br><br>**`Access / Cost`:** Free public | **`Relevance`:** Internet threat telemetry & diary reports.<br><br>**`Notes & POIs`:** Useful for emergent exploitation context. |
| 6 | **Honeynet Project**<br><br>**`Link(s)`:** [www.honeynet.org](https://www.honeynet.org/)<br><br>**`Access / Cost`:** Free public / open research | **`Relevance`:** Honeypot & threat research.<br><br>**`Notes & POIs`:** Useful for attacker behavior insight. |
| 7 | **DShield**<br><br>**`Link(s)`:** [www.dshield.org](https://www.dshield.org/)<br><br>**`Access / Cost`:** Free public / community | **`Relevance`:** Distributed intrusion detection & telemetry.<br><br>**`Notes & POIs`:** Useful for broad scanning trend analysis. |
| 8 | **LeakIX**<br><br>**`Link(s)`:** [leakix.net](https://leakix.net/)<br><br>**`Access / Cost`:** Free limited access / paid plans | **`Relevance`:** Exposed service & leak search.<br><br>**`Notes & POIs`:** Useful for exposure assessment. |
| 9 | **urlscan.io**<br><br>**`Link(s)`:** [urlscan.io](https://urlscan.io/)<br><br>**`Access / Cost`:** Free tier / paid plans | **`Relevance`:** URL scanning & web telemetry.<br><br>**`Notes & POIs`:** Useful for phishing, web exposure, & IOC enrichment. |
| 10 | **VirusTotal**<br><br>**`Link(s)`:** [www.virustotal.com](https://www.virustotal.com/)<br><br>**`Access / Cost`:** Free community access / paid enterprise plans | **`Relevance`:** File, URL, domain, & IP reputation.<br><br>**`Notes & POIs`:** Useful for malware/IOC enrichment; licensing constraints apply. |
| 11 | **VirusTotal API**<br><br>**`Link(s)`:** [docs.virustotal.com/reference/overview](https://docs.virustotal.com/reference/overview)<br><br>**`Access / Cost`:** Free community API / paid enterprise API | **`Relevance`:** VirusTotal API documentation.<br><br>**`Notes & POIs`:** API quota & data-sharing policies matter. |

## 16.3 Attack surface management context

| Sl. # | Source Title | Notes |
|---:|---|---|
| 1 | **Amass**<br><br>**`Link(s)`:** [github.com/owasp-amass/amass](https://github.com/owasp-amass/amass)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** Attack surface mapping & DNS enumeration.<br><br>**`Notes & POIs`:** Useful for external asset discovery. |
| 2 | **ProjectDiscovery Subfinder**<br><br>**`Link(s)`:** [github.com/projectdiscovery/subfinder](https://github.com/projectdiscovery/subfinder)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** Subdomain discovery.<br><br>**`Notes & POIs`:** Useful for asset inventory enrichment. |
| 3 | **httpx**<br><br>**`Link(s)`:** [github.com/projectdiscovery/httpx](https://github.com/projectdiscovery/httpx)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** HTTP probing toolkit.<br><br>**`Notes & POIs`:** Useful for validating exposed services. |
| 4 | **Naabu**<br><br>**`Link(s)`:** [github.com/projectdiscovery/naabu](https://github.com/projectdiscovery/naabu)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** Port scanner.<br><br>**`Notes & POIs`:** Useful for fast exposure discovery. |
| 5 | **Nmap**<br><br>**`Link(s)`:** [nmap.org](https://nmap.org/)<br><br>**`Access / Cost`:** Free / open-source | **`Relevance`:** Network discovery & security auditing.<br><br>**`Notes & POIs`:** Mature scanner for service detection & scripts. |
| 6 | **Masscan**<br><br>**`Link(s)`:** [github.com/robertdavidgraham/masscan](https://github.com/robertdavidgraham/masscan)<br><br>**`Access / Cost`:** Free / open-source public GitHub repo | **`Relevance`:** High-speed port scanner.<br><br>**`Notes & POIs`:** Use carefully; scan authorization & network impact matter. |

> 
> #### [*Back to **`Index`***](#index)
---

## Discussion

This chapter section keeps the latest table structure, source titles, access/cost fields, relevance notes, & operational notes from the source inventory. Review the table entries as ingestion candidates, then validate source freshness, licensing, authentication requirements, & link-check behavior before production use.

---

#### [Back to Index](../../01-index.md)
