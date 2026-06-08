# Buting EmergenSig

A local government dashboard that uses Stellar multi-signature accounts to ensure transparent, consensus-driven approvals for barangay emergency fund disbursements.

## Problem
In the Philippines, local government units (LGUs) such as Barangays manage localized calamity and emergency funds. When disaster strikes, these funds must be disbursed quickly to local merchants for relief goods, medicines, or hazard pay. However, the manual, paper-based approval process involving multiple council members is slow, opaque, and historically prone to corruption or mismanagement. Both the government and its citizens need a fast, transparent way to allocate and disburse these funds while maintaining strict, mathematically enforced oversight from the Barangay Council.

## How It Works
The dashboard functions as a digital portal for Barangay officials. 
1. **System Initialization**: A shared multi-signature "Fund Account" is created on the Stellar network.
2. **Proposing an Expense**: The Barangay Captain creates a new Fund Request (e.g., ₱5,000 for Relief Goods) through the dashboard, specifying a preferred local merchant's destination address. This creates a pending payment transaction but does not broadcast it.
3. **Consensus Approval**: To release the funds, a quorum of the council is required. At least 3 out of 4 Kagawads (council members) must log in and cryptographically sign the transaction using their secure keys.
4. **Execution**: Once the 3-signature threshold is met, any official can broadcast the fully signed transaction to the Stellar network, securely settling the funds with the merchant in seconds.

## How It Uses Stellar
- **Native Multi-Signature Governance**: Instead of building complex smart contracts, the app heavily leverages Stellar's built-in, account-level multi-sig primitives. The central fund account sets its low, medium, and high thresholds to 3, and adds the Captain and the Kagawads as authorized signers with a weight of 1.
- **Transaction Envelopes (XDR)**: Pending proposals are serialized into XDR format, allowing them to be stored locally or passed around off-chain until they accrue enough signatures to be valid.
- **Native Payments**: Emergency payouts are executed as standard Stellar payment operations.
- **Why Stellar?** Stellar's native multi-sig allows us to enforce strict institutional governance rules easily and securely. The near-zero transaction fees and sub-5-second settlement times make it the only realistic choice for resource-constrained public government units in the Philippines.

## Track
Track 5 Social Impact

## Tech Stack
- Framework: Next.js (serving a Vanilla JS/HTML dashboard)
- Stellar SDK: `@stellar/stellar-sdk` (via CDN)
- Network: testnet
- Styling: Custom Vanilla CSS

## Setup & Run
The application runs locally as a web dashboard.

```bash
git clone https://github.com/ChrisQuint0/Buting-EmergenSig.git
cd Buting-EmergenSig/web
npm install
npm run dev
```

Open `http://localhost:3000` in your browser. 
*(Note: Use the numbered keys 1-4 to quickly quick-switch between the Captain and Kagawad demo accounts as instructed on the login screen).*

## Network Details
- Network: testnet
- RPC URL: `https://horizon-testnet.stellar.org`
- Contract IDs: N/A (Native Multi-Sig)
- Asset issuers: N/A (Native XLM conceptualized as PHP for the demo)

## Team
- ChrisQuint0 — @ChrisQuint0

## License
MIT
