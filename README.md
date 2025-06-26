

# Stacklancer TalentVerse: Decentralized Talent Auction Marketplace on Stacks

## Overview

**TalentVerse** is a decentralized talent marketplace built on the **Stacks blockchain** using the Clarity smart contract language. The platform enables verified talents (freelancers, creators, etc.) to list their services via **time-bound auctions**, allowing clients to **bid competitively** for talent engagement.

It introduces transparency, on-chain escrow handling, bidding logic, and reputation tracking — all while maintaining trustless interactions and a fair marketplace dynamic.

---

## 📦 Features

* **Talent Registration**: Only verified users can list services.
* **Service Auctions**: Talents can create time-bound auctions with custom price floors.
* **Competitive Bidding**: Bidders must outbid previous offers by a minimum increment.
* **Fee Handling**: A 5% platform fee is deducted and transferred to the contract owner.
* **Escrow & Refunds**: STX is held in escrow during bids, and previous bidders are refunded.
* **Auction Completion**: Once auctions expire, talents can finalize and receive their payment.
* **On-Chain Reputation**: Each talent builds a track record with earnings and completed auctions.

---

## 🛠️ Smart Contract Architecture

### Constants

* `FEE-RATE`: Platform fee (5% in basis points)
* `MIN/MAX-AUCTION-DURATION`: Duration limits (1 to 30 days)
* `MIN/MAX-PRICE`: Allowed price range per auction
* `CONTRACT-OWNER`: Fee recipient (deployer or initial sender)

### Errors

Predefined error constants for better readability and validation handling (e.g., `ERR-NOT-AUTHORIZED`, `ERR-INVALID-BID`, etc.).

### Storage

* **Data Vars**:

  * `next-auction-id`: ID for tracking the next auction.
  * `total-auctions-completed`, `total-fees-collected`: Stats tracking.
* **Maps**:

  * `talents`: Stores verified talent data (rating, earnings, etc.).
  * `auctions`: Stores all auction listings and states.

### Functions

#### Public

* `register-talent`: Allows new talents to join the platform.
* `create-auction`: Creates a new service auction.
* `place-bid`: Places a bid on an active auction.
* `complete-auction`: Finalizes an auction after expiration and pays out the talent.

#### Read-Only

* `get-auction`: Fetch details of an auction.
* `get-talent-info`: View talent statistics and history.
* `get-contract-stats`: Total auctions and fees.
* `is-registered`: Checks if a user is a verified talent.
* `can-complete-auction`: Indicates if an auction is ready for finalization.

---

## 🔐 Security Considerations

* **Authorization Checks**: Only auction owners can finalize their listings.
* **Anti-Self-Bid**: Talents cannot bid on their own auctions.
* **Refunds**: Previous bidders are safely refunded upon being outbid.
* **Escrow Logic**: Funds are safely held within the contract until auction resolution.

---

## 🚀 Deployment Instructions

1. **Install Clarinet** (Stacks smart contract tool):

   ```bash
   npm install -g @hirosystems/clarinet
   ```

2. **Clone the Repository**:

   ```bash
   git clone https://github.com/your-repo/talentverse.git
   cd talentverse
   ```

3. **Test the Contract**:

   ```bash
   clarinet test
   ```

4. **Deploy to Testnet/Mainnet**:
   Modify your project’s deployment settings and use:

   ```bash
   clarinet deploy
   ```

---

## 📖 Example Workflow

1. Alice registers as a talent.
2. She creates an auction for “Logo Design” at 10 STX lasting 3 days.
3. Bob places a bid of 12 STX.
4. Eve places a higher bid of 14 STX — Bob is refunded.
5. After the auction ends, Alice completes the auction and receives 14 STX (minus fee).

---

## 🧪 Testing

Use Clarinet’s testing framework to simulate:

* Multiple bids
* Auction edge cases (expired, no bidders, invalid price/duration)
* Fund transfers and fee deductions

---

## 📄 License

MIT License — feel free to fork, extend, and contribute.

---
