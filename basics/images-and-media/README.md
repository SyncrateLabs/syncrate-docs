---
icon: coin-blank
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
    - https://app.gitbook.com/s/yE16Xb3IemPxJWydtPOj/basics/images-and-media
---

# The SYNC Token

The SYNC token is the native utility and governance asset of the Syncrate Protocol. It is designed to coordinate trustless cross-chain settlements and align the interests of liquidity providers, institutional users, and node operators.

***

### SYNC Utilities

* **Transaction Fees:** Every cross-chain RWA settlement requires a small fee (0.1bps) paid in either the native chain the user is routing to or in SYNC. This hybrid model reduces transaction frictions.&#x20;

Large institutional traders can boost their settlement speed and priority by staking or paying higher SYNC fees.

* **Node Staking:** Operators who validate the state of the cross-chain bridges must stake SYNC. If a node provides false data about a fiat on-ramp status (via the BaaS partner), their stake is slashed.

* **Insurance Fund:** A portion of SYNC transaction fees is diverted to a decentralized "Settlement Insurance Fund" to protect users in the event of unforeseen chain re-organizations.

* **Fee Abstraction:** Syncrate allows institutions to pay a single fee in SYNC, while the protocol’s backend automatically handles the underlying gas payments on the destination chains using the Syncrate treasury.

* **Governance:** SYNC holders vote on protocol parameters and the deployment of the Syncrate Treasury.

***

To ensure there is always enough liquidity for cross-chain "Payment vs. Delivery" (PvD), SYNC is distributed as a reward to:

• Liquidity Providers (LPs) who lock stablecoins into Syncrate’s settlement pools.

• BaaS Integration Partners who provide the fastest fiat-to-onchain gateways.


