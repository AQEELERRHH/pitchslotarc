# PitchSlotArc
## Attention Auction Protocol on Arc Testnet

**Built by Aqeelerh | April 2026 | Arc L1 by Circle**  
**Live at:** https://pitchslotarc.vercel.app  
**Contract:** 0x8cE043782dA362F3E9Caf5fd995061765A993138 

---

## 1. What is PitchSlotArc?

PitchSlotArc is a decentralized attention marketplace built on Arc Testnet Circle's Layer 1 blockchain purpose-built for stablecoin finance. It creates a trustless, programmable market where companies and individuals bid USDC to reach creators, professionals, and busy people.

The core insight: attention is the scarcest resource on the internet. PitchSlotArc turns it into an economic primitive every message, reply, and interaction becomes priced, prioritized, and programmable.

Unlike Web2 pay-to-message tools (X Premium DMs, LinkedIn InMail), PitchSlotArc is fully trustless: funds are locked in a smart contract escrow and only released when the creator actually replies. No reply within 14 days means the bidder gets a full automatic refund. No platform can confiscate funds. No creator can take money without engaging.

---

## 2. How It Works

### 2.1 The Two-Sided Market

PitchSlotArc serves two types of users simultaneously:

- **Creators & Professionals** people with valuable attention: influencers, founders, developers, consultants, researchers. They register, set a minimum bid threshold, and receive a ranked inbox of messages sorted by USDC bid amount.
- **Companies & Bidders** anyone who wants to reach a creator: brands, recruiters, collaborators, investors. They submit a message plus a USDC bid. Funds lock in escrow immediately. They only pay if the creator responds.

### 2.2 The Auction Flow

1. Creator registers on-chain and sets minimum bid (e.g. $5 USDC)  
2. Bidder submits message + USDC bid funds lock in Arc smart contract escrow  
3. AI agent (Ollama llama3.2) scores messages for quality and ranks inbox by bid amount  
4. Creator sees ranked inbox highest USDC bids surface first  
5. Creator accepts (reply required, stored on-chain) → USDC released instantly to creator  
6. OR creator rejects → full USDC refund to bidder immediately  
7. OR 14 days pass with no response → agent auto-triggers refund on-chain  

### 2.3 Privacy Features

- Bidders can choose to keep their identity private the bid amount is visible to the creator but the wallet address is hidden  
- Creators see only anonymous bids unless the bidder opts into public attribution  
- All on-chain transactions are auditable on Arc Testnet Explorer  

---

## 3. Why Arc?

PitchSlotArc is architecturally dependent on Arc's unique features it is not simply deployed on Arc as a convenience. Here is the precise mapping:

| Arc Feature | PitchSlotArc Use | Why It Matters |
|------------|----------------|---------------|
| USDC Native Gas | All bid/accept/reject transactions | No ETH needed — users pay predictable dollar-denominated fees |
| Sub-second Finality | Instant escrow lock and payment release | Bids confirm in under 1 second — real-time UX |
| EVM Compatible | Solidity contracts, Foundry tooling | Standard dev tools work out of the box |
| ERC-20 USDC | Escrow, payment, refund logic | USDC is both gas and value token single asset |
| Claude Agent SDK (via Anthropic) | AI message scoring and filtering | Arc is integrated with Anthropic's Claude SDK for agentic apps |
| Low Predictable Fees | Frequent micro-transactions | Fees stay stable regardless of network activity |

---

## 4. Tech Stack

### 4.1 Smart Contract

- Solidity 0.8.30  
- Foundry (forge, cast, anvil)  
- Arc Testnet (Chain ID: 5042002)  
- 0x8cE043782dA362F3E9Caf5fd995061765A993138  
- 0x3600000000000000000000000000000000000000  
- https://rpc.testnet.arc.network  
- https://testnet.arcscan.app  

### 4.2 Frontend

- Vanilla HTML, CSS, JavaScript zero build tools  
- Ethers.js v6.7.0 (via CDN)  
- Fraunces + DM Mono (Google Fonts)  
- Vercel (pitchslotarc.vercel.app)  
- index.html (landing), creator.html (dashboard), bid.html (bidder)  

### 4.3 AI Agent

- Node.js v20  
- Ollama llama3.2 (free, runs locally)  
- ethers (v6), node-fetch (v2)  
- Rule-based scoring when Ollama unavailable  
- 30 seconds — monitors all registered creators via on-chain events  

### 4.4 Development Environment

- Windows 11 with WSL Ubuntu 24  
- Bash (WSL)  
- VS Code with WSL extension  
- Git + GitHub  
- npm 11.x  

---

## 5. How to Test on Arc Testnet

### Step 1: Install MetaMask

Install MetaMask browser extension from https://metamask.io. Create or import a wallet.

### Step 2: Add Arc Testnet to MetaMask

In MetaMask, go to Networks > Add Network > Add Manually and enter:

| Field | Value |
|------|------|
| Network Name | Arc Testnet |
| RPC URL | https://rpc.testnet.arc.network |
| Chain ID | 5042002 |
| Currency Symbol | USDC |
| Block Explorer | https://testnet.arcscan.app |

### Step 3: Get Testnet USDC

Go to https://faucet.circle.com, select Arc Testnet, paste your wallet address, and click Request. You will receive 20 testnet USDC enough to place multiple bids. This USDC has no real value and is for testing only.

### Step 4: Test as a Creator

8. Visit https://pitchslotarc.vercel.app/creator.html  
9. Click Connect MetaMask approve Arc Testnet if prompted  
10. Enter a minimum bid amount (e.g. 5 for $5 USDC)  
11. Click Register & Set Minimum confirm in MetaMask  
12. Copy your wallet address from the Connected field  
13. Share your wallet address with a bidder (or switch wallets and bid yourself)  

### Step 5: Test as a Bidder

14. Visit https://pitchslotarc.vercel.app/bid.html (use a different wallet than the creator)  
15. Click Connect MetaMask  
16. Paste the creator wallet address in the Creator Wallet Address field  
17. Enter bid amount (must be at or above creator's minimum)  
18. Write your message to the creator  
19. Click Lock USDC in escrow two MetaMask confirmations (Approve USDC, then Place Bid)  

### Step 6: Accept or Reject

20. Switch back to the creator wallet  
21. Refresh creator.html the bid appears in your ranked inbox  
22. Click Accept write a reply (minimum 10 characters, stored on-chain) confirm in MetaMask  
23. USDC (minus 2% fee) releases instantly to your wallet  
24. OR click Reject bidder receives full refund immediately  

---

## 6. Use Cases & Scenarios

### Scenario 1: Brand Partnership Outreach

A consumer brand wants to reach a Web3 creator with 50K followers. Instead of sliding into DMs with zero response rate, they bid $25 USDC. The creator's agent scores the message 8/10 for relevance it surfaces at the top of the inbox. The creator replies with interest, receives $24.50 (after 2% fee) instantly on Arc.

### Scenario 2: Recruiting a Developer

A Series A startup wants to hire a senior Solidity developer. They bid $50 USDC to reach them directly. The message scores 9/10. The developer replies with their availability. $49 USDC lands in their wallet. The startup paid for attention, not spam.

### Scenario 3: Investor Seeking a Founder

A VC wants to connect with a founder building in DeFi. They bid $30 USDC. The founder's agent filters out the 3 lower bids from less serious parties and surfaces the VC's message first. One reply = one connection = funds released.

### Scenario 4: Anonymous Research

A market research firm needs qualitative data from influencers. They bid privately identity hidden so the creator can't be biased by who's asking. The bidder's address never appears on the creator's dashboard. The reply proves engagement on-chain.

### Scenario 5: Conference Speaker Booking

Event organizers bid to reach keynote speakers. Multiple organizers compete the speaker sees a ranked list of opportunities sorted by bid size. Highest bidder gets the first reply. No agents or middlemen take 20% commission.

### Scenario 6: The 14-Day Auto-Refund

A company bids $10 USDC to reach a creator who has gone offline. After 14 days with no response, the PitchSlotArc agent automatically calls claimRefund() on-chain. The $10 returns to the company wallet without any manual action. Zero trust, zero loss.

---

## 7. ERC-8183 Future Integration

On March 31, 2026, Arc announced ERC-8183 is live on Arc Testnet. ERC-8183 introduces Jobs escrowed, verifiable, on-chain work between agents. This is the standard that PitchSlotArc will adopt in Version 2.

### Why ERC-8183 Matters for PitchSlotArc

PitchSlotArc is already architecturally aligned with ERC-8183 it has escrowed USDC, verifiable completion triggers (creator reply), and agent-executed release logic. The current Bid struct is essentially an ERC-8183 Job.

### V2 Integration Roadmap

| Component | V1 (Current) | V2 (ERC-8183) |
|----------|-------------|---------------|
| Bid structure | Custom Bid struct | Conforms to ERC-8183 Job spec |
| Escrow | Custom USDC escrow | Standard Job escrow |
| Agent | Rule-based + Ollama | ERC-8183 compliant agent with on-chain registration |
| Composability | Standalone dApp | Plugs into any Arc agentic marketplace |
| Discovery | Direct wallet address | Agent registry discover creators by capability |
| Cross-currency | USDC only | USDC + EURC via StableFX |

By conforming to ERC-8183, PitchSlotArc bids become composable with any other Arc protocol that understands the Job standard. A creator's inbox becomes accessible to any ERC-8183-compatible marketplace. The agent becomes registerable on-chain.

---

## 8. Smart Contract Reference

### Core Functions

| Function | Who Calls | What It Does |
|----------|----------|--------------|
| registerCreator(minBid) | Creator | Register with minimum bid threshold |
| updateMinBid(newMin) | Creator | Update minimum bid amount |
| placeBid(creator, amount, message, isPrivate) | Bidder | Lock USDC in escrow and submit message |
| acceptBid(bidId, reply) | Creator | Submit reply + release USDC to creator |
| rejectBid(bidId) | Creator | Refund USDC to bidder in full |
| claimRefund(bidId) | Anyone | Refund after 14-day timeout |
| getCreatorBids(address) | Read | All bid IDs for a creator |
| getBid(bidId) | Read | Full bid data including message |
| getTopBid(creator) | Read | Current top bid amount (for bidder UI) |

### Key Constants

- 14 days (1,209,600 seconds)  
- 200 (2% platform fee on acceptance only)  
- 6 (same as Arc native USDC)  

---

## 9. Known Issues & Future Improvements

- V1 uses a prompt() dialog for reply. V2 will use an inline text field in the dashboard with on-chain reply storage via acceptBid(bidId, reply).  
- The AI agent currently requires the builder to run node agent.js on their machine. V2 will host the agent as a persistent service or integrate with Arc's Claude Agent SDK for always-on monitoring.  
- Planned for V2 to make PitchSlotArc composable with the broader Arc agentic economy.  
- V1 supports USDC only. V2 will add EURC and other Arc partner stablecoins via StableFX.  
- The frontend works on desktop browsers. Mobile MetaMask app support requires WalletConnect integration.  
- AI scoring is the current spam filter. V2 will add on-chain reputation scores and stake-based creator verification.  

---

## 10. Project Links

- https://pitchslotarc.vercel.app  
- https://github.com/AQEELERRHH/pitchslotarc  
- https://testnet.arcscan.app/address/0xd97Df466F8de1BE0567aa5403c8d5dB06cee25B7  
- https://faucet.circle.com  
- https://docs.arc.network  
- https://testnet.arcscan.app  
- Aqeelerh| https://x.com/aqeelerh | Arc Architect  

---

**Built on Arc Testnet April 2026**  
**Attention is the new economy. PitchSlotArc is the market.**
