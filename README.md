🌐 Celo Engage Hub - Social Engagement Platform

https://img.shields.io/badge/Celo-Mainnet-gold
https://img.shields.io/badge/License-MIT-yellow.svg
https://img.shields.io/github/stars/tebberen/celo-engage-hub
https://img.shields.io/github/forks/tebberen/celo-engage-hub
https://img.shields.io/github/issues/tebberen/celo-engage-hub
https://img.shields.io/twitter/url?style=social&url=https%3A%2F%2Fgithub.com%2Ftebberen%2Fcelo-engage-hub

Social TX - Where Every Interaction Builds Real Value
A decentralized social engagement platform built on Celo blockchain that rewards meaningful community interactions through governance, badges, and social verification.

📑 Table of Contents

· 🌟 Introduction
· 🚀 Features
· 🏗️ Architecture
· 📦 Installation
· 🎮 Quick Start
· 🔧 Smart Contracts
· 🛠️ Development
· 🧪 Testing
· 📚 API Documentation
· 🌍 Deployment
· 🤝 Contributing
· 📝 License
· 🙏 Acknowledgments
Base 

🌟 Introduction

Celo Engage Hub is a groundbreaking social platform that leverages blockchain technology to create a trustless, community-driven ecosystem. Built on the Celo network, it combines social interactions with on-chain governance and reputation systems.

🎯 Problem Statement

Traditional social platforms suffer from:

· Centralized control and censorship
· Lack of transparency in content moderation
· No real ownership or rewards for users
· Limited community governance

💡 Our Solution

· Decentralized Governance: Community-driven proposal and voting system
· Social Verification: Support-based content curation
· Monetization & Rewards: Badge-based achievement system
· Transparent Operations: Fully on-chain interactions

🚀 Features

🛡️ Social Verification System

· Support-Based Submission: Users must support existing content before submitting their own
· Community Curation: Content visibility determined by community engagement
· Anti-Spam Mechanism: Limits and verification prevent platform abuse

🏛️ On-Chain Governance

· Proposal Creation: Any user can create governance proposals
· Transparent Voting: Verifiable on-chain voting with Celo transactions
· Community Decisions: Platform evolution driven by user votes

🎖️ Badge & Reputation System

· Achievement Tracking: Earn badges for platform participation
· Reputation Scoring: Build reputation through quality contributions
· Soulbound Tokens: Non-transferable achievement badges (future)

💰 Gas Optimization

· Efficient Transactions: Optimized for Celo's low-gas environment
· Batch Operations: Multiple actions in single transactions
· Gas Estimation: Accurate gas prediction for better UX

🌐 Multi-Platform Integration

· Social Media Links: Support for X, Farcaster, GitHub, and more
· Cross-Platform Verification: Unified identity across platforms
· Content Syndication: Share across multiple platforms seamlessly

🔐 Advanced Wallet Integration

· MetaMask Support: Full MetaMask compatibility
· Celo Native Wallets: Support for Valora, Celo Wallet
· Network Switching: Automatic Celo network detection and switching

🏗️ Architecture

System Overview

```
┌─────────────────┐    ┌──────────────────┐    ┌─────────────────┐
│   Frontend      │    │   Smart Contract │    │   Celo Network  │
│   (Client)      │    │   (Middleware)   │    │   (Blockchain)  │
├─────────────────┤    ├──────────────────┤    ├─────────────────┤
│ • HTML/CSS/JS   │◄──►│ • User Registry  │◄──►│ • Transactions  │
│ • Ethers.js     │    │ • Governance     │    │ • Smart Contracts│
│ • LocalStorage  │    │ • Badge System   │    │ • CELO/cUSD     │
└─────────────────┘    └──────────────────┘    └─────────────────┘
```

Technology Stack

· Frontend: HTML5, CSS3, Vanilla JavaScript (ES6+)
· Blockchain: Celo Network (Mainnet & Alfajores Testnet)
· Web3 Library: Ethers.js v5.7.2
· Wallet Integration: MetaMask, Celo-Compatible Wallets
· Storage: Browser LocalStorage + On-chain Storage
· Styling: Custom CSS with Celo Brand Colors

Smart Contract Architecture

```solidity
// Core Contract Structure
CeloEngageHub.sol
├── UserRegistry
│   ├── registerUser()
│   ├── updateProfile()
│   └── getUserProfile()
├── Governance
│   ├── createProposal()
│   ├── voteProposal()
│   └── getProposalDetails()
├── BadgeSystem
│   ├── awardBadge()
│   ├── getUserBadges()
│   └── checkEligibility()
└── Utilities
    ├── checkUserActive()
    └── getPlatformStats()
```

📦 Installation

Prerequisites

· Node.js (v16 or higher)
· npm or yarn
· MetaMask or Celo-compatible wallet
· Celo tokens for gas fees

Step-by-Step Installation

```bash
# 1. Clone the repository
git clone https://github.com/tebberen/celo-engage-hub.git

# 2. Navigate to project directory
cd celo-engage-hub

# 3. Install dependencies (if any added in future)
npm install

# 4. Start local development server
npm run dev

# 5. Open browser and navigate to
# http://localhost:3000
```

Docker Installation (Optional)

```bash
# Build Docker image
docker build -t celo-engage-hub .

# Run container
docker run -p 3000:3000 celo-engage-hub
```

🎮 Quick Start

For End Users

1. Connect Your Wallet
   · Click "Connect MetaMask" button
   · Approve connection request
   · Switch to Celo Mainnet when prompted
2. Support Community Content
   · Browse existing links in the support section
   · Click "Support This Content" on at least one item
   · This unlocks your submission privileges
3. Submit Your Content
   · Enter your social media link (X, Farcaster, GitHub, etc.)
   · Confirm transaction in your wallet
   · Pay gas fee (typically < $0.01 on Celo)
4. Participate in Governance
   · Create proposals for platform improvements
   · Vote on active proposals
   · Shape the future of the platform
5. Earn Badges
   · Receive badges for active participation
   · Build your reputation score
   · Unlock special privileges

For Developers

```javascript
// Quick integration example
const engageHub = {
  connect: async () => {
    if (typeof window.ethereum !== 'undefined') {
      await window.ethereum.request({ method: 'eth_requestAccounts' });
      const provider = new ethers.providers.Web3Provider(window.ethereum);
      return provider.getSigner();
    }
  },
  
  submitLink: async (link) => {
    const contract = new ethers.Contract(CONTRACT_ADDRESS, ABI, signer);
    const tx = await contract.registerUser("username", link);
    return await tx.wait();
  }
};
```

🔧 Smart Contracts

Contract Addresses

· Mainnet: 0x22eA49c074098931a478F381f971C77486d185b2
· Alfajores Testnet: Deploying Soon

Core Functions

User Management

```solidity
function registerUser(string memory _username, string memory _link) public
function updateProfile(string memory _username, string memory _link) public
function getUserProfile(address _user) public view returns (
    string memory link,
    string memory username, 
    uint256 supportCount,
    uint256 reputation,
    uint256 badgeCount,
    bool isActive,
    uint256 timestamp
)
```

Governance

```solidity
function createProposal(string memory _title, string memory _description) public
function voteProposal(uint256 _proposalId, bool _support) public
function getActiveProposals() public view returns (uint256[] memory)
function getProposalDetails(uint256 _proposalId) public view returns (
    uint256 id,
    string memory title,
    string memory description,
    address creator,
    uint256 votesFor,
    uint256 votesAgainst,
    uint256 deadline,
    bool executed
)
```

Badge System

```solidity
function awardBadge(address _user, string memory _badge) public
function getUserBadges(address _user) public view returns (string[] memory)
function revokeBadge(address _user, string memory _badge) public
```

Events

```solidity
event UserRegistered(address indexed user, string username);
event ProposalCreated(uint256 indexed proposalId, string title, address creator);
event Voted(uint256 indexed proposalId, address indexed voter, bool support);
event BadgeAwarded(address indexed user, string badge);
```

🛠️ Development

Setting Up Development Environment

1. Fork the Repository
   ```bash
   # Fork on GitHub, then clone your fork
   git clone https://github.com/YOUR_USERNAME/celo-engage-hub.git
   cd celo-engage-hub
   ```
2. Install Development Dependencies
   ```bash
   npm install --save-dev live-server gh-pages
   ```
3. Run Development Server
   ```bash
   npm run dev
   ```

Building for Production

```bash
# Build optimized version
npm run build

# Deploy to GitHub Pages
npm run deploy
```

Code Structure

```
src/
├── index.html              # Main application entry point
├── css/
│   └── style.css           # All styles and responsive design
├── js/
│   ├── app.js              # Main application logic
│   ├── wallet.js           # Wallet connection and management
│   ├── contract.js         # Smart contract interactions
│   └── ui.js               # User interface controls
├── contracts/
│   └── CeloEngage.sol      # Smart contract source
└── tests/
    └── test.js             # Test suites
```

🧪 Testing

Smart Contract Testing

```bash
# Run contract tests
npx hardhat test

# Run tests with coverage
npx hardhat coverage
```

Frontend Testing

```javascript
// Example test case
describe('Celo Engage Hub', () => {
  it('should connect wallet successfully', async () => {
    const result = await connectWallet();
    expect(result).toBe(true);
  });

  it('should submit link with proper validation', async () => {
    const link = 'https://github.com/tebberen';
    const result = await submitLink(link);
    expect(result.status).toBe('success');
  });
});
```

Integration Testing

```bash
# Run full test suite
npm test

# Run specific test group
npm run test:contracts
npm run test:frontend
```

📚 API Documentation

JavaScript SDK

Initialization

```javascript
import CeloEngageHub from 'celo-engage-hub';

const hub = new CeloEngageHub({
  network: 'mainnet', // or 'alfajores'
  contractAddress: '0x22eA49c074098931a478F381f971C77486d185b2'
});
```

Core Methods

connectWallet()

```javascript
// Connect user's wallet
const userAddress = await hub.connectWallet();
```

submitContent(link, platform)

```javascript
// Submit new content
const result = await hub.submitContent(
  'https://github.com/tebberen',
  'github'
);
```

getUserProfile(address)

```javascript
// Get user profile
const profile = await hub.getUserProfile('0x...');
```

REST API (Future)

```bash
# Get platform statistics
GET /api/stats

# Get user profile
GET /api/users/:address

# Get active proposals
GET /api/proposals/active
```

🌍 Deployment

GitHub Pages Deployment

The project is automatically deployed to GitHub Pages:

· Live URL: https://tebberen.github.io/celo-engage-hub/
· Branch: main
· Auto-deploy: On every push to main

Manual Deployment

```bash
# Build project
npm run build

# Deploy to any static hosting
# Netlify, Vercel, AWS S3, etc.
```

Smart Contract Deployment

```bash
# Deploy to Celo Mainnet
npx hardhat run scripts/deploy.js --network celo

# Deploy to Alfajores Testnet
npx hardhat run scripts/deploy.js --network alfajores
```

🤝 Contributing

We love your input! We want to make contributing to Celo Engage Hub as easy and transparent as possible.

How to Contribute

1. Fork the repo and create your branch from main
2. Make your changes and test thoroughly
3. Follow our code style and add tests if applicable
4. Submit a pull request with clear description of changes

Development Workflow

```bash
# Create feature branch
git checkout -b feature/amazing-feature

# Make changes and commit
git add .
git commit -m "feat: add amazing feature"

# Push and create PR
git push origin feature/amazing-feature
```

Reporting Bugs

· Use the GitHub Issues template
· Describe the bug and steps to reproduce
· Include browser/device information

Suggesting Enhancements

· Open an issue with enhancement label
· Explain the proposed feature
· Discuss implementation approach

📝 License

This project is licensed under the MIT License - see the LICENSE file for details.

Permitted Use:

· ✅ Commercial use
· ✅ Modification
· ✅ Distribution
· ✅ Private use

Requirements:

· ℹ️ License and copyright notice preservation

🙏 Acknowledgments

Core Team

· tebberen - Project Lead & Full-stack Development

Special Thanks

· Celo Foundation for ecosystem support and builder rewards
· Celo Community for testing, feedback, and support
· Builder Rewards Program for incentivizing quality development

Technologies & Tools

· Celo Blockchain - Green, mobile-first blockchain
· Ethers.js - Complete Ethereum wallet implementation
· MetaMask - Crypto wallet & gateway to blockchain apps
· GitHub Pages - Static site hosting

Inspiration

This project draws inspiration from:

· Social media platforms with community governance
· Blockchain-based reputation systems
· DAO (Decentralized Autonomous Organization) models

---

<div align="center">⭐ If this project helped you, please give it a star!

https://img.shields.io/github/stars/tebberen/celo-engage-hub?style=social
https://img.shields.io/github/forks/tebberen/celo-engage-hub?style=social

Built with ❤️ for the Celo Ecosystem

</div>---
*
