# Architecture Overview

Syncrate is a non-custodial orchestration protocol designed to unify fragmented real-world asset liquidity. Unlike issuance platforms, Syncrate acts as a stateless middleware that coordinates state transitions across multiple blockchains while respecting the compliance boundaries of native issuers.

***

#### 1. The Three-Layer Stack

Syncrate’s architecture is divided into three functional layers that separate user intent from institutional compliance.

* **The Intent & Access Layer (Application):** The entry point where users or institutional treasuries define their desired state (e.g., "Routing from OUSG to BUILD"). This layer handles the connection to user wallets and displays the available RWA routes from integrated issuers.

* **The Orchestration Engine (Middleware):** This is the core logic of Syncrate. This layer calculates the optimal execution path for asset movement by selecting the most cost-effective messaging transport and batching cross-chain commands. It ensures atomic transitions by verifying destination-chain compliance requirements (KYC/AML) before triggering issuer gateways, preventing transaction reverts and fragmented state.

* **The Connectivity & Gateway Layer (Integration):** It consists of adapters that plug directly into the Issuance & Redemption Gateways of third-party partners (e.g., Ondo, Backed, Centrifuge). It does not hold keys or custody; it simply triggers the issuer's native functions.


To maintain a non-custodial and non-issuing status, Syncrate maintains three strict boundaries:

* **The Compliance Boundary:** Syncrate does not perform KYC. Instead, it utilizes Attestation Hooks. Before an orchestration event is executed, the protocol queries the issuer’s native KYC registry (or a shared identity standard like ERC-3643). If the user’s wallet is not whitelisted by the issuer, the transaction reverts at the smart-contract level.

* **The Custody Boundary:** Syncrate never takes possession of the underlying RWA. Assets move from the User's Wallet —> Issuer's Gateway –> Destination Wallet. If the route isn't completed, the asset remains in the source wallet.

* **The Messaging Boundary:** Syncrate is messaging-agnostic. We utilize a Transport Abstractor that can route via Chainlink CCIP, LayerZero, or Wormhole depending on the issuer's preference.
