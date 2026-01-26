---
icon: message-arrow-down
---

# Governance

The Syncrate protocol is designed to transition into a decentralized, community-governed ecosystem. Governance is not merely about technical parameters but focuses on the safety, compliance, and integrity of the real-world assets orchestrated by the protocol.

***

## The SYNC DAO

The SYNC DAO is the primary decision-making body. Token holders stake SYNC to receive veSYNC (Voting Escrow SYNK), which grants the right to propose and vote on protocol upgrades.

**Core Governance Pillars:**

* **Fee Modules:** Adjusting routing fees and the percentage allocated to the SYNC buy-back and burn mechanism.
* **Treasury Managerment:** Directing protocol revenue toward project development and RWA research.

***

## The Legal Wrapper & Special Purpose Vehicle

Unlike pure DeFi, Syncrate governs assets tied to traditional legal systems.

* **The Syncrate Foundation:** A legal wrapper (ADGM Foundation) which acts as the protocol's legal representative to sign contracts with offchain custodians and regulated issuers. Governance decisions that impact the legal status of an asset must be ratified by the Foundation to ensure they do not violate local securities laws or MiCA regulations.

***

## The Syncrate Council

To prevent governance attacks and ensure rapid response to regulatory changes, Syncrate employs a Guardian Council - a multi-sig composed of core team members, legal experts, and institutional partners.

* **Veto Power:** The Council can veto proposals that pose a systemic regulatory risk or technical threat to the protocol.
* **Emergency Pausing:** In the event of a smart contract exploit or a major regulatory black swan event, the Council can pause ochestration modules to protect user capital.

***

## Proposal Lifecycle

To ensure high-quality decision-making, all **Syncrate Improvement Proposals (SIPs)** follow a structured path:

1. **Phase I: Discussion (Soft Consensus):** Ideas are debated on the Syncrate Governance Forum for a minimum of 7 days.
2. **Phase II: Snapshot (Signal Voting):** An off-chain gasless vote to gauge community sentiment.
3. **Phase III: OnChain Vote:** A binding executable vote requiring a 4% quorum of total SYNC supply; however, during the first 24 months of the protocol's lifecycle (while team and investor tokens are locked), the quorum requirement is adjusted to 10% of the circulating supply.
4. **Phase IV: Timelock:** Approved changes are subject to a 48-hour timelock before implementation, allowing users to exit if they disagree with the outcome.
