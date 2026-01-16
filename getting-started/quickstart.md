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

# Architecture Overview

Syncrate’s architecture is built around a **KYC-compliant and Canonical Model**, designed for permissioned RWA ecosystems where each issuer operates inside its own isolated environment. Today, moving capital between issuers is slow and operationally heavy because every asset can only be minted, redeemed, or transferred through its issuer’s canonical gateway. Syncrate solves this by orchestrating the entire multi-step workflow end-to-end – using Account Abstraction (ERC-4337) to bundle multiple complex steps into a single signature.

### 1. Intent & Identity Layer (The Entry)&#x20;

Before any request enters the system, Syncrate performs a unified compliance check based on the issuer's attetstaion to ensure every user's transaction follows jurisdictional rules and are allowed to hold the target asset.

At this stage, the user specifies a source RWA (e.g., **OpenEden TBILL**) and a target RWA (e.g., **Backed bAAPL**). We integrate with BaaS companies via API to handle the jurisdictional requirements and asset movem licensing. This helps us to scale globally in months while a full license is in works.&#x20;

Instead of fragmented onboarding, Syncrate integrates an identity hub (e.g., Quadrata, Civic). It maps the user's existing credentials to the target issuer’s allowlist requirements before the transaction even begins.

### 2. The Canonical Exit (Liquidity Injection)

After KYC and allowlist checks are done, Syncrate triggers the Primary Redemption of the source asset rather than selling into thin secondary markets.\
Optimized Routing:

* For T-Bills (e.g, Matrixdock/OpenEden): Syncrate triggers the issuer’s requestRedeem() contract for T+0 or T+1 USDC settlement.
* For Private Credit: (e.g, Credix/Clearpool): This manages Epoch-based exits. Syncrate tracks Withdrawal Windows (e.g., Credix's 10-day request phase) to ensure the capital is ready for the next leg.

**Outcome:** The asset is burned, and **Canonical USDC** is received directly into the Syncrate settlement vault.

### 3. Stable Settlement & Cross-chain Bridging

All trades settle into permissionless USDC to avoid the risks of synthetic or wrapped assets. If the target RWA is on a different chain (e.g., moving from Ethereum to Base or Polygon), Syncrate utilizes Circle CCTP for cross-chain bridging.

This burn-and-mint bridge ensures 1:1 backing with zero liquidity provider (LP) risk.

### 4. The Canonical Entry (Issuance)

Once USDC arrives on the target chain, Syncrate calls the mint() or requestIssuance() function for the target RWA.

* **For Stocks (Backed/Swarm):** Syncrate submits the purchase request to the issuer during market hours (e.g., NASDAQ hours for bAAPL).

The user receives the **native, canonical token** directly from the issuer. No intermediary "Syncrate-Wrapped" tokens are ever held.



To ensure the "Single-Click" experience is truly 24/7, Syncrate's routing engine dynamically toggles between two liquidity sources:

1. **The Primary Conduit (NAV Optimization):** During traditional market hours, Syncrate routes "Canonical Entry/Exit" requests directly to issuers (e.g., Backed, OpenEden). This eliminates the "DeFi Premium" and ensures users receive 1:1 value against the underlying asset's Net Asset Value (NAV).
2. **The Secondary Mesh (24/7 Availability):** For instant settlement outside traditional market hours, Syncrate taps into decentralized AMMs and RWA-specific liquidity pools. This allows users to exit T-Bills or enter Stocks at 3:00 AM on a Saturday with sub-second finality.

Users get the best of both worlds – the 24/7 "always-on" nature of Crypto, with the institutional-grade pricing of Wall Street.

_Syncrate includes a **Slippage Guard**. If the 24/7 secondary price deviates too far from the last-known Oracle price, our router automatically queues the transaction for the 'Primary Route' at the next market open, protecting the user's capital._





***



