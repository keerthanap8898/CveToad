# COMMERCIAL USE & DEPLOYMENT GOVERNANCE
**LICENSE:** Dual-Licensed (GNU AGPL v3 for Open Source / Custom ELA for Commercial Deployment).
**OWNER:** Keerthana Purushotham (and designated Corporate Entities).

This repository (`CveToad` / `CVE Merkle Tree` / `VulnKeeper`) is governed by a strict Dual-Licensing model. Your right to clone, test, or execute this codebase depends entirely on your capacity and intent. 

---

## 1. PRIMARY DIRECTIVE: WHO SHOULD PULL THIS CODE

### ✅ PERMITTED: Individual Engineers, Researchers & Academics
Engineers, security researchers, and developers—including those currently employed by Amazon, Google, Microsoft, Meta, OpenAI, and other corporate entities—are fully encouraged to pull this code for **individual, local, non-commercial use**. 
You may freely:
* Clone the repository to your local development desktop.
* Compile and run the native C/Rust execution engine locally to study its architecture.
* Benchmark the $O(1)$ deterministic graph traversal algorithms.
* Validate the mathematics and use the architecture for non-commercial academic research.

### 🚫 FORBIDDEN: Corporate, Federal & Commercial Deployment
**Corporate entities (including but not limited to AWS, Google Cloud, Microsoft Azure, OpenAI) and defense contractors are strictly prohibited from using, deploying, hosting, or embedding this work in commercial, production, or networked environments without purchasing a commercial Enterprise License Agreement (ELA).**
Without an ELA, you may not:
* Deploy this engine into proprietary hypervisors (e.g., AWS Nitro, Azure Fabric) or data center infrastructure.
* Integrate this codebase into corporate CI/CD pipelines, cloud backends, or AI agent orchestration layers.
* Offer this dependency state verification as a SaaS/IaaS product.

---

## 2. THE AGPL v3 WARNING (THE "NETWORK INTERACTION" CLAUSE)

The open-source version of this repository is strictly licensed under the **GNU Affero General Public License v3 (AGPL v3)**. 

If a corporate entity attempts to bypass the commercial ELA and deploys this codebase into a networked cloud environment, you are triggering **Section 13 (Network Interaction)** of the AGPL v3. 
* **The Legal Consequence:** Under Section 13, if users or AI agents interact with this software remotely over a network, you are legally compelled to open-source and publicly distribute the complete "Corresponding Source" code of your **entire integrated proprietary backend**.
* **The Commercial Solution:** To integrate this $O(1)$ verification standard safely without contaminating your proprietary codebase and violating open-source law, your organization must negotiate a commercial Enterprise License Agreement (ELA). This agreement nullifies the AGPL v3 copyleft restrictions and permits proprietary embedding in exchange for standard royalty payments.

---

**For Enterprise License Agreements (ELA), Sovereign Grants, and Royalty Negotiations, contact the repository owner directly.**