> # `Cve-Toad` 𖥧﹏𓆏࿐⚘𓇗
> #### *`hops on`, `helps you catch some bugs`* 𓆤༉ *, `then hops off`*
> - [*Take the CVE Consumer (User) Survey - forms.gle/QNCciH4vF7gtMaMF6 .*](https://forms.gle/QNCciH4vF7gtMaMF6)
> 
> ---

## A CVE Impact Predictor, in a Secure Ephemeral AI Shell

### `Contents`  
1. #### Other Repo-Documents to See:
    1. [`CVE-user-story_Description.md` - *github.com/keerthanap8898/CveToad/blob/main/CVE-user-story_Description.md*](https://github.com/keerthanap8898/CveToad/blob/main/CVE-user-story_Description.md)
    2. [`CVE-Consumer_User-Story.md` - *github.com/keerthanap8898/CveToad/blob/main/CVE-Consumer_User-Story.md*](https://github.com/keerthanap8898/CveToad/blob/main/CVE-Consumer_User-Story.md)

2. #### README Index
    1. [Problem Statement](#1-problem-statement)
    2. [Solution Overview](#2-solution-overview)
    3. [Architecture](#3-architecture)
    4. [Workflow](#workflow)
    5. [Key Components](#key-components)
    6. [Security Model](#4-security-model)
    7. [Benefits](#5-benefits)
    8. [Future Extensions](#6-future-extensions)
    9. [Summary](#7-summary)
    10. [Appendix – Project Concept](#8-appendix--project-snapshot)
    11. [License](#9-license)

---

### 1. `Problem Statement`

Security analysts and system engineers need to quickly assess the potential impact of Common Vulnerabilities and Exposures (CVEs) on diverse local systems (Windows, macOS, Linux) without exposing host data or credentials.  
Existing CVE scanners lack contextual awareness of system architecture and do not leverage modern AI reasoning. Traditional tools also persist sensitive configuration data, creating long-term security risks.

### 2. `Solution Overview`

I propose a secure, ephemeral “CVE‐Checker Shell” — a command‐line tool that launches a temporary containerised runtime to perform AI-assisted CVE impact analysis.  
The shell initialises with short-lived authentication tokens (≤ 8 hours) and dynamically installs approved AI model clients (e.g., OpenAI, Anthropic) inside the container. Once execution completes, the container and all secrets are destroyed, leaving no footprint on the host.

### 3. `Architecture`

- #### Workflow

  1. CLI authenticates via enterprise SSO and requests a time-bound JWT or Vault token encoding user role and permissions.  
  2. The controller script collects system metadata (OS, CPU, packages) on the local host and mounts it read-only into the container as JSON.  
  3. The container runs the AI analysis pipeline:  
     - Parses host data  
     - Queries configured AI providers for vulnerability context  
     - Generates a prioritised CVE impact report  
  4. Upon exit, all runtime artefacts, credentials, and network connections are destroyed.

- #### Key Components
  ```
  - Controller CLI: Handles auth, container lifecycle, token TTL, logging.  
  - Ephemeral Container: Sandboxed Python/Rust runtime with model adapters and CVE logic.  
  - Role Policy Engine: Defines permissions per role (e.g., admin, analyst).  
  - Secrets Backend: Issues expiring tokens and revokes access on logout or TTL expiry.
  ```
### 4. `Security Model`
```
- Isolation: Containerised runtime (Docker/Podman) with no host persistence (`--rm`).  
- Token Lifespan: Max 8 h TTL; revocable on demand.  
- Role-Based Access: Tokens encode role; container validates signature and policy before execution.  
- Network Control: Outbound traffic limited to approved AI API endpoints.  
- Zero Trust: No implicit trust in host or container; each run is independently authenticated.
```
### 5. `Benefits`
```
- Eliminates persistent secrets and local installs.  
- Enables cross-platform CVE context analysis tailored to system architecture.  
- Enforces reproducible, auditable sessions aligned with enterprise compliance.  
- Extensible to support offline or on-prem LLMs for air-gapped environments.
```
### 6. `Future Extensions`
```
- Integrate with HashiCorp Vault or AWS STS for federated token issuance.  
- Add Rust backend for lower latency and improved concurrency.  
- Extend to digital-twin telemetry for Software-Defined Vehicle (SDV) environments.
```
### 7. `Summary`
`CVE Impact Predictor combines ephemeral compute, AI reasoning, and strict tokenised authentication to deliver secure, context-aware vulnerability impact analysis. It embodies Amazon’s principles of security by default, least privilege, and short-lived trust, while showcasing modular extensibility for next-generation intelligent security tooling.`

### 8. `Appendix – Project Snapshot`
> “*CveToad*”, a localized, authenticated & containerised, open-src AI-workflow type of application; additionally secured by secret-managers, short-lived session tokens for container-shells with hard memory limits & role-based env configs. The use-case is to help you pin down CVE impact on your system whilst incrementally building user-specific CVE-context.  
> 
> The concept is to incrementally feed it the right context to optimise how accurately it predicts individual CVSS vector elements (specific to the CVSS version & CVE’s age/create-date).  
> 
> ### *For example*:  
> > 1. the CVSS-v4 specification document ([first.org/cvss/v4-0/specification-document](https://www.first.org/cvss/v4-0/specification-document)) as an automatable base-layer pre-process context,  
> > 2. ***`sys.info`*** context (including rpm-tree data); about the user OS-instance (from outside the shell) to specify system-specific CVE impact details,  
> > 3. identify useful pkg-attributes like `vendor`, `maintainer`, `rpm name` (*product name*), `dependencies` (*parent/child packages*), etc., from [pagure.io/fedora-packages-static](http://pagure.io/fedora-packages-static) … and so on.
> >
> > ---
> 
> ### `Reference Links to see`: ***CVE sources , User-Story Resources , Official Links***
> > 1. [**NVD (NIST)** - *nvd.nist.gov*](https://nvd.nist.gov/) ,
> > 2. [**RedHat API** - *docs.redhat.com/en/documentation/red_hat_security_data_api/1.0*](https://docs.redhat.com/en/documentation/red_hat_security_data_api/1.0/html/red_hat_security_data_api/index) ,
> > 3. [**Debian** - *security-tracker.debian.org*](https://security-tracker.debian.org/tracker/#:~:text=Search%20for%20package%20or%20bug%20name) ,
> > 4. [**Suse** - *suse.com/support/security*](https://www.suse.com/support/security/#:~:text=Security%20updates%20by,in%20CSAF%20format) ,
> > 5. [**Amazon Linux** - *explore.alas.aws.amazon.com*](https://explore.alas.aws.amazon.com/) ,
> > 6. [**Fedora (Script to pull all package names and meta-data)** : *pagure.io/fedora-packages-static*](https://pagure.io/fedora-packages-static) ,
> > 7. [**OSV.dev** - *github.com/google/osv.dev*](https://github.com/google/osv.dev) .
> >
> ---
> >
> > 1. [**My (** *Keerthana's* **) CVE user Story** - *github.com/keerthanap8898/CveToad/tree/main/CVE-Consumer_User-Story.md*](https://github.com/keerthanap8898/CveToad/blob/main/CVE-Consumer_User-Story.md) ,
> > 2. [**CVE User-story_Description** - *github.com/keerthanap8898/CveToad/blob/main/CVE-user-story_Description.md*](https://github.com/keerthanap8898/CveToad/blob/main/CVE-user-story_Description.md) ,
> > 3. [**CVE Meta-data Framework Table Image:** - *github.com/keerthanap8898/CveToad/blob/main/Resources/Images/CVE_Meta-data_Framework_Table.jpg*](https://github.com/keerthanap8898/CveToad/blob/main/Resources/Images/CVE_Meta-data_Framework_Table.jpg) . 
> >
> ---
> >
> > 1. [**CVE-Project Official Repo** - *github.com/CVEProject/cvelistV5*](https://github.com/CVEProject/cvelistV5) ,
> > 2. [**CVE-Project Official Schema** - *github.com/CVEProject/cve-schema*](https://github.com/CVEProject/cve-schema) ,
> > 3. [**CVE-Project Automation Working group** - *github.com/CVEProject/automation-working-group*](https://github.com/CVEProject/automation-working-group) .
> >
> ---
> 

# **`VulnKeeper`**
### [***`breachtrace.gitbook.io/vulnkeeper`***](https://breachtrace.gitbook.io/vulnkeeper/) 
> #### [ *`GitBook`* ]
>
> ```⎯⎯✧﹌𓆤༉𖧧𖥧𖤣. ༘༝ၴ( ၴႅၴ˖𓏲⚘ཐི༏ཋྀˎ ྀ𓏲𓇗𖤣﹏𓆏࿐⚘𖥧𖤣𓇗ˎˊˎˊ𓆈ˊˎ゛✧⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯⎯```
> 
> ## Root path to serve as a **`persistent link`** for `static files/PDFs` in addition to **storing archives** upon any updates / iterations, &/or extentions.
> 
> ---

### LICENSE

CveToad is available under the
[GNU Affero General Public License version 3](LICENSE) or under a separately
negotiated commercial license.

Project licensing documents:

- [Dual-license and project governance](LICENSING.md)
- [Commercial use and deployment](COMMERCIAL-USE.md)
- [Contribution policy](CONTRIBUTING.md)

The licensing scope expressly includes qualifying original materials in the
[CVE-Merkle-RPM slides](MerkleRPM_KP_watermark-May26.pdf) and the
[VulnKeeper GitBook](https://breachtrace.gitbook.io/vulnkeeper/), as
described in [`LICENSING.md`](LICENSING.md).

Copyright © 2025-2026 Keerthana Purushotham.