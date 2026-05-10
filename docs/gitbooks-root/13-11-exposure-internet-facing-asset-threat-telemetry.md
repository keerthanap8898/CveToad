# 11. Exposure, internet-facing asset & threat telemetry

### 11.1 Internet exposure search engines
| Sl. # | Title | Link(s) | Access / Cost | Relevance | Notes & POIs |
|---:|---|---|---|---|---|
| 1 | Censys Search | [search.censys.io](https://search.censys.io/) | Free tier / paid plans | Internet exposure search engine. | Useful for determining if vulnerable services are internet-facing. |
| 2 | Censys API | [search.censys.io/api](https://search.censys.io/api) | Free tier / paid plans; API key required | Programmatic Censys access. | API terms & quotas may apply. |
| 3 | Shodan | [www.shodan.io](https://www.shodan.io/) | Free limited access / paid plans | Internet-connected device search. | Useful for exposure discovery & banner-based matching. |
| 4 | Shodan developer API | [developer.shodan.io](https://developer.shodan.io/) | Paid/API credit model may apply; account required | Shodan API documentation. | Useful for automation. |
| 5 | ZoomEye | [www.zoomeye.org](https://www.zoomeye.org/) | Free limited access / paid plans | Internet asset search engine. | Useful as additional exposure telemetry. |
| 6 | FOFA | [fofa.info](https://fofa.info/) | Free limited access / paid plans | Internet asset search. | Coverage & access terms vary. |
| 7 | BinaryEdge | [www.binaryedge.io](https://www.binaryedge.io/) | Commercial / limited trial may exist | Internet scanning & threat intelligence. | Useful for external exposure enrichment. |
| 8 | Onyphe | [www.onyphe.io](https://www.onyphe.io/) | Free tier / paid plans | Cyber defense search engine. | Useful for passive/active exposure context. |
| 9 | SecurityTrails | [securitytrails.com](https://securitytrails.com/) | Free limited access / paid plans | DNS & asset intelligence. | Useful for attack surface discovery. |
| 10 | InternetDB by Shodan | [internetdb.shodan.io](https://internetdb.shodan.io/) | Free public API | Lightweight Shodan InternetDB API. | Useful for quick IP exposure enrichment. |
### 11.2 Scan/exploitation telemetry
| Sl. # | Title | Link(s) | Access / Cost | Relevance | Notes & POIs |
|---:|---|---|---|---|---|
| 1 | GreyNoise Visualizer | [viz.greynoise.io](https://viz.greynoise.io/) | Free tier / paid plans | Internet scanning/exploitation telemetry. | Helps separate background scanning from targeted activity. |
| 2 | GreyNoise API docs | [docs.greynoise.io](https://docs.greynoise.io/) | Free tier / paid plans; API key required | API docs for GreyNoise enrichment. | Useful for automated telemetry enrichment. |
| 3 | Shadowserver | [www.shadowserver.org](https://www.shadowserver.org/) | Free for eligible organizations; registration may be required | Internet-scale exposure & threat telemetry. | Good for population-level exposure signals. |
| 4 | Shadowserver reports | [dashboard.shadowserver.org](https://dashboard.shadowserver.org/) | Free for eligible organizations; login/registration may be required | Shadowserver reporting dashboard. | Access/eligibility may vary. |
| 5 | SANS Internet Storm Center | [isc.sans.edu](https://isc.sans.edu/) | Free public | Internet threat telemetry & diary reports. | Useful for emergent exploitation context. |
| 6 | Honeynet Project | [www.honeynet.org](https://www.honeynet.org/) | Free public / open research | Honeypot & threat research. | Useful for attacker behavior insight. |
| 7 | DShield | [www.dshield.org](https://www.dshield.org/) | Free public / community | Distributed intrusion detection & telemetry. | Useful for broad scanning trend analysis. |
| 8 | LeakIX | [leakix.net](https://leakix.net/) | Free limited access / paid plans | Exposed service & leak search. | Useful for exposure assessment. |
| 9 | urlscan.io | [urlscan.io](https://urlscan.io/) | Free tier / paid plans | URL scanning & web telemetry. | Useful for phishing, web exposure, & IOC enrichment. |
| 10 | VirusTotal | [www.virustotal.com](https://www.virustotal.com/) | Free community access / paid enterprise plans | File, URL, domain, & IP reputation. | Useful for malware/IOC enrichment; licensing constraints apply. |
| 11 | VirusTotal API | [docs.virustotal.com/reference/overview](https://docs.virustotal.com/reference/overview) | Free community API / paid enterprise API | VirusTotal API documentation. | API quota & data-sharing policies matter. |
### 11.3 Attack surface management context
| Sl. # | Title | Link(s) | Access / Cost | Relevance | Notes & POIs |
|---:|---|---|---|---|---|
| 1 | Amass | [github.com/owasp-amass/amass](https://github.com/owasp-amass/amass) | Free / open-source public GitHub repo | Attack surface mapping & DNS enumeration. | Useful for external asset discovery. |
| 2 | ProjectDiscovery Subfinder | [github.com/projectdiscovery/subfinder](https://github.com/projectdiscovery/subfinder) | Free / open-source public GitHub repo | Subdomain discovery. | Useful for asset inventory enrichment. |
| 3 | httpx | [github.com/projectdiscovery/httpx](https://github.com/projectdiscovery/httpx) | Free / open-source public GitHub repo | HTTP probing toolkit. | Useful for validating exposed services. |
| 4 | Naabu | [github.com/projectdiscovery/naabu](https://github.com/projectdiscovery/naabu) | Free / open-source public GitHub repo | Port scanner. | Useful for fast exposure discovery. |
| 5 | Nmap | [nmap.org](https://nmap.org/) | Free / open-source | Network discovery & security auditing. | Mature scanner for service detection & scripts. |
| 6 | Masscan | [github.com/robertdavidgraham/masscan](https://github.com/robertdavidgraham/masscan) | Free / open-source public GitHub repo | High-speed port scanner. | Use carefully; scan authorization & network impact matter. |
> #### [*Back to **`Index`***](#index)
---
