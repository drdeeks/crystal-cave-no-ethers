# 🏔️✨ Crystal Cave Adventure

An interactive offline educational adventure game where players explore magical caves, solve puzzles, and learn through exploration. No cryptocurrency, wallets, or blockchain required.

## 🌟 Project Overview

Crystal Cave Adventure is a purely client-side React game (with optional Electron desktop build). Players collect in-game "artifacts" and increase their Wisdom, Courage, Kindness, and Discovery stats by overcoming educational challenges.

### 🎮 Game Features
- **60+ interactive scenes** across four adventure branches
- **Educational challenges** in math, science, geography, history, and philosophy
- **Character development** with intuitive stat system
- **28 unique endings** including comedic "death" finales packed with easter-egg phrases
- **Full offline play** – no network connection needed once assets are loaded

## 🛠️ Tech Stack

### Frontend
- **React 18** (TypeScript)
- **Electron** for cross-platform desktop app (optional)
- **Lucide React** for icons
- **Responsive design** and touch support

## 🚀 Quick Start

```bash
# 1) Install dependencies
npm install

# 2) Start the game in the browser
npm start

# 3) Build for production
npm run build

# 4) (Optional) Launch desktop version
npm run electron-dev
```

That's it! Enjoy exploring the Crystal Cave ��️🧙‍♂️✨

## 📱 Game Experience

### Desktop Application
- **Standalone executable** with installer
- **Offline gameplay** for educational content
- **Native window controls** and menu system
- **Cross-platform** (Windows, Mac, Linux)

## 🎨 User Interface

### Game Layout Structure

The Crystal Cave Adventure features a **modern horizontal game interface** designed for optimal user experience:

#### **Upper Game Area**
- **Full-screen game content**: Adventure scenes, quizzes, and story elements
- **Responsive design**: Adapts to different screen sizes
- **Interactive elements**: Choice buttons, activity components, and progress indicators

#### **Lower Status Bar** (Persistent)
Crystal Cave uses a **horizontal status bar** similar to traditional game interfaces:

```
┌─────────┬──────────────────────────────────────────┬───────────┐
│ SCORE   │   CHARACTERISTIC TRAITS (W,C,K,D)        │ ARTIFACTS │
│   55    │          3   5   7   2                   │ 12 / 22   │
└─────────┴──────────────────────────────────────────┴───────────┘
           (scrollable row of 22 artifact icons)
```

**Bar Layout (Three-Column Grid):**
1. **Score** – large numeric value.
2. **Characteristic Traits** – Wisdom, Courage, Kindness, Discovery in compact grid.
3. **Artifacts** – shows owned/total count.

The **artifact icons** now live in their **own horizontally scrollable container directly below** the bar. Owned artifacts display their miniature artwork with a green border; empty slots remain gray.

#### **Bottom Quote**
- **Persistent footer**: "💜 Made With Love By DrDeek 💜"
- **Subtle styling**: Purple background with centered text

### Wallet Integration
- **Accurate artifact counting**: Reads actual NFTs from connected wallet
- **Real-time updates**: Artifact slots update when NFTs are minted
- **Connection status**: Clear wallet connection indicators

### Responsive Design
- **Desktop**: Full horizontal layout with all elements visible
- **Mobile**: Adaptive layout with scrollable artifact container
- **Touch-friendly**: Optimized button sizes and spacing

## 🎯 Educational Content

### Challenge Categories
- **Mathematics**: Pattern recognition, order of operations, sequences
- **Science**: Crystallization, marine biology, astronomy, physics
- **Geography**: Rivers, continents, navigation
- **History**: Ancient civilizations, landmarks
- **Philosophy**: Critical thinking, ethics, wisdom

### NFT Artifacts (22 Total)
- **Classic Artifacts** (0-17): Ancient Map, Sage's Blessing, Magical Compass, etc.
- **Monanimal Collection** (18-21): Chill Dak, Moyaki, Salmonad, Dead Chog

## 🔧 Development

### Game Development
```bash
# Start development server
npm start

# Build for production
npm run build

# Create desktop app
npm run electron-dev
npm run dist
```

### Smart Contract Development
```bash
# Test contracts
forge test

# Deploy locally
anvil  # Start local blockchain
forge script script/Deploy.s.sol --fork-url http://localhost:8545 --broadcast
```

### Testing
```bash
# Frontend tests
npm test

# Smart contract tests
forge test -vvv

# Integration tests
npm run test:integration
```

## 🌐 Deployment

### Game Deployment
- **Netlify**: Automated deployment from git
- **Electron**: Desktop installers for Windows/Mac/Linux
- **IPFS**: Decentralized hosting option

### Contract Deployment
```bash
# Monad Testnet (Basic Deployment)
forge script script/Deploy.s.sol --rpc-url $ETH_RPC_URL --broadcast

# Monad Testnet (Deploy + Verify)
forge script script/Deploy.s.sol --rpc-url $ETH_RPC_URL --broadcast --verify --verifier sourcify --verifier-url https://sourcify-api-monad.blockvision.org

# Verify existing contract
node scripts/verify-contract.js <CONTRACT_ADDRESS>
```

### Contract Verification (Multiple Methods)

#### Method 1: Automated Script (Recommended)
```bash
# Use our comprehensive verification script
node scripts/verify-contract.js 0xYourContractAddress

# Example output:
# ✅ Contract verification completed successfully!
# 🔗 View: https://testnet.monadexplorer.com/address/0xYourContractAddress
```

#### Method 2: Direct Foundry Command
```bash
# Official Monad Sourcify verification
forge verify-contract \
    0xYourContractAddress \
    src/contracts/CrystalCaveNFT.sol:CrystalCaveNFT \
    --chain 10143 \
    --verifier sourcify \
    --verifier-url https://sourcify-api-monad.blockvision.org
```

#### Method 3: Deploy + Verify in One Command
```bash
# Deploy and verify simultaneously
forge create src/contracts/CrystalCaveNFT.sol:CrystalCaveNFT \
    --rpc-url $ETH_RPC_URL \
    --private-key $PRIVATE_KEY \
    --verify \
    --verifier sourcify \
    --verifier-url https://sourcify-api-monad.blockvision.org
```

#### Method 4: Manual Verification
If automated methods fail:
1. **Monad Explorer**: https://testnet.monadexplorer.com/verify-contract
2. **Sourcify Direct**: https://sourcify.dev/#/verifier
3. **Required Info**:
   - Contract Address: `0xYourContractAddress`
   - Compiler Version: `0.8.20`
   - Optimization: `true` (200 runs)
   - Contract Path: `src/contracts/CrystalCaveNFT.sol`
   - Contract Name: `CrystalCaveNFT`

#### Verification Troubleshooting
```bash
# Check if already verified
forge verify-check 0xYourContractAddress --chain-id 10143 --verifier sourcify

# Ensure foundry.toml is correct
cat foundry.toml

# Verify contract compiles
forge build

# Check deployment transaction
cast receipt 0xYourTransactionHash --rpc-url $ETH_RPC_URL
```

### Environment Configuration
```bash
# Required environment variables
ETH_RPC_URL=https://testnet-rpc.monad.xyz
REACT_APP_ETH_RPC_URL=https://testnet-rpc.monad.xyz
REACT_APP_CHAIN_ID=10143
REACT_APP_CONTRACT_ADDRESS=<your_deployed_address>
```

## 📊 Contract Details

### Crystal Cave NFT (CrystalCaveNFT.sol)
- **Standard**: ERC721 with extensions
- **Features**: Pausable, Ownable, ReentrancyGuard
- **Minting**: Free (gas only), one per artifact type per user
- **Metadata**: IPFS-hosted with comprehensive traits

### Key Functions
```solidity
mintArtifact(uint256 artifactId)  // Mint specific artifact
userOwnsArtifact(address, uint256) // Check ownership
getUserArtifacts(address)         // Get user's collection
```

## ⛽ Gas Optimization (Monad-Specific)

### 🎯 Optimized Gas Settings
Crystal Cave is optimized for **Monad Testnet's unique gas model** where users are charged the gas limit (not gas used).

#### Current Gas Targets
- **Minting**: ~150,000 gas (down from 200,000)
- **Deployment**: ~2,500,000 gas 
- **Base Fee**: 50 monad gwei (fixed on testnet)
- **Priority Fee**: 50 monad gwei (recommended)

#### Key Optimizations
1. **Explicit Gas Limits**: No `eth_estimateGas` to prevent MetaMask high limits
2. **Predictable Costs**: Users know exact transaction costs upfront
3. **Efficient Storage**: Optimized contract storage patterns
4. **Monad EIP-1559**: Proper base fee + priority fee configuration

### 🔧 Frontend Gas Configuration
The frontend automatically uses optimized gas settings:

```typescript
// Automatic gas limits for common operations
const GAS_LIMITS = {
  MINT_ARTIFACT: 180000,      // Conservative minting limit
  APPROVE: 50000,             // Standard approvals
  TRANSFER: 21000,            // Native token transfers
};

// EIP-1559 gas pricing for Monad
const GAS_CONFIG = {
  maxFeePerGas: '100000000000',        // 100 gwei (50 base + 50 priority)
  maxPriorityFeePerGas: '50000000000', // 50 gwei priority
};
```

### 📈 Gas Savings Achieved
| Operation | Before | After | Savings |
|-----------|--------|-------|---------|
| Minting | ~200k | ~150k | **25%** |
| Deployment | ~3M | ~2.5M | **17%** |
| User Experience | Variable | Predictable | **Stable Costs** |

### ⚠️ Monad-Specific Notes
- **Gas Charging**: Monad charges gas limit, not gas used
- **MetaMask Behavior**: Explicit limits prevent overly high gas estimates
- **Priority Auction**: Proper priority fees ensure transaction inclusion
- **User Confidence**: Predictable costs improve user experience

## 🔐 Security

### Smart Contract Security
- **OpenZeppelin** audited contracts
- **ReentrancyGuard** protection
- **Access controls** for admin functions
- **Comprehensive test suite**

### Key Management
- **Encrypted keystore** with AES-256-GCM
- **WSL requirement** for secure operations
- **Environment isolation**
- **No private keys in code**

## 📚 Documentation Files

- **[ARTIFACT_METADATA_MAPPING.md](ARTIFACT_METADATA_MAPPING.md)**: Complete artifact trait documentation
- **[IPFS_DEPLOYMENT_GUIDE.md](IPFS_DEPLOYMENT_GUIDE.md)**: Metadata hosting guide
- **[VERIFICATION_GUIDE.md](VERIFICATION_GUIDE.md)**: Complete contract verification guide
- **[CHEATSHEET.md](CHEATSHEET.md)**: Game challenge answers (for educators)

## 🤝 Contributing

We welcome contributions for:
- Educational content improvements
- New artifact designs
- Smart contract enhancements
- UI/UX improvements
- Documentation updates

## 📄 License

MIT License - see LICENSE file for details.

## 🆘 Support

- **Game Issues**: Check browser console for errors
- **Wallet Connection**: Ensure Monad Testnet is added to MetaMask
- **Contract Issues**: Verify contract address and network
- **Build Problems**: Use `--legacy-peer-deps` with npm commands

## 🌟 Monad Network Configuration

Add to MetaMask:
- **Network Name**: Monad Testnet
- **RPC URL**: https://testnet-rpc.monad.xyz
- **Chain ID**: 10143
- **Currency**: MON
- **Explorer**: https://testnet.monadexplorer.com

---

*Ready to explore the Crystal Cave? Connect your wallet and start your educational adventure! 🧙‍♂️✨* #   c r y s t a l - c a v e - a d v e n t u r e - s t a n d a l o n e  
 