---
icon: bolt
layout:
  width: default
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
metaLinks:
  alternates:
    - https://app.gitbook.com/s/yE16Xb3IemPxJWydtPOj/getting-started/quickstart
---

# The Syncrate Workflow

Syncrate's routing layer is built around a **KYC-compliant and Canonical Model**, designed for permissioned RWA ecosystems where each issuer operates inside its own isolated environment. Today, moving capital between issuers is slow and operationally heavy because every asset can only be minted, redeemed, or transferred through its issuer’s canonical gateway. Syncrate solves this by orchestrating the entire multi-step workflow end-to-end – using Account Abstraction (ERC-4337) to bundle multiple complex steps into a single signature.

***

### 1. Intent & Identity Layer (The Entry)

Before any request enters the system, Syncrate performs a unified compliance check based on the issuer's attetstaion to ensure every user's transaction follows jurisdictional rules and are allowed to hold the target asset.

At this stage, the user specifies a source RWA (e.g., **OpenEden TBILL**) and a target RWA (e.g., **Backed bAAPL**).

***

### 2. The Canonical Exit

After KYC and allowlist checks are done, Syncrate triggers the Primary Redemption of the source asset at the issuer's redemption gateway rather than selling into thin secondary markets.

**Outcome:** The asset is burned, and **Canonical USDC** is received directly into the Syncrate settlement vault.

***

### 3. Stable Settlement & Cross-chain Bridging

If the target RWA is on a different chain (e.g., moving from Ethereum to Base or Polygon), Syncrate utilizes Circle's CCTP for cross-chain bridging.

***

### 4. The Canonical Entry 

Once USDC arrives on the target chain, Syncrate performs a second allowlist check - making sure the user is allowed to hold the target RWA. Once this allowlist is done, Syncrate sends a mint/issuance request for the target RWA at the issuer's mint gateway.

The user receives the **native, canonical token** directly from the issuer. No intermediary Syncrate-wrapped tokens are ever held.

