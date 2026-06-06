# AstrumGate

> **A symmetric cross-chain NFT bridge built on LayerZero, enabling seamless transfer of ERC721 tokens between Conflux, Base, and Arbitrum networks, with full metadata support, dynamic wrappers, and a[...]

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Conflux](https://img.shields.io/badge/built%20on-Conflux-blue)](https://confluxnetwork.org)
[![Hackathon](https://img.shields.io/badge/SummerHackfest-2025-green)](https://github.com/conflux-fans/summerhackfest-2025)

---

## ⚠️ SECURITY NOTICE

**THIS SMART CONTRACT HAS NOT BEEN AUDITED.** This is a proof-of-concept project developed for the SummerHackfest 2025 hackathon. Use at your own risk. **DO NOT use this bridge with mainnet assets or in production environments without a professional security audit.** Users assume all risks associated with using this software. The developers are not responsible for any losses, damages, or vulnerabilities that may occur.

---

## 🎯 Overview

**AstrumGate** is an advanced cross-chain NFT bridge between **Conflux eSpace**, **Base**, and **Arbitrum**.  
It enables NFT projects on Conflux to access the **$14.8B TVL liquidity on Base** and **$19.97B TVL on Arbitrum (as of writing)** and expand NFT utility beyond a single chain with symmetric bridging c[...]

The project leverages **LayerZero-powered interoperability** to unlock new opportunities for NFT projects, including dynamic support for any ERC721 collection, automatic wrapper deployment for foreign[...]

Key enhancements in this updated version:
- Symmetric bridging (works identically on all chains).
- Full metadata support for seamless NFT representation across chains.
- Integrated NFT factory for creating, minting, and managing collections (with batch mint/burn).
- Bridge history tracking in the frontend.
- Dynamic registration and handling of native/wrapped collections without hardcoding.

This version is a robust proof-of-concept, ready for demonstration and further production hardening.

---

## 🏆 Hackathon Information

- **Event**: Code Without Borders - SummerHackfest 2025  
- **Focus Area**: Open Innovation — Build anything using Conflux features  
- **Team**: N/A 
- **Submission Date**: September 15, 2025  

---

## 👥 Team

| Name | Role                      | GitHub | Discord |
|------|---------------------------|--------|---------|
| Syv  | Full-Stack Blockchain Dev | [@0xfdbu](https://github.com/0xfdbu) | syv_dev |

---

## 🚀 Problem Statement

NFT ecosystems are siloed by design. On Conflux, NFT projects:  
- Cannot reach the liquidity available on other chains (e.g., Base's $14.8B TVL, Arbitrum's $19.97B TVL)  
- Have limited cross-chain utility and exposure  
- Rely on centralized bridges or exchanges  

This isolation reduces NFT adoption and market opportunities.

---

## 💡 Solution

AstrumGate provides a **permissionless, symmetric ERC721 cross-chain bridge**:  
- 🌉 **Symmetric Bridging** of NFTs between Conflux eSpace, Base, and Arbitrum (lock/unlock natives, mint/burn wrappers).  
- 🔗 **Dynamic Support** for any ERC721 contract with automatic registration and wrapper deployment.  
- 🏭 **NFT Collection Factory** for creating custom collections with batch minting/burning.  
- 🧾 **Full Metadata Bridging** (collection name/symbol, per-token URIs) for perfect cross-chain representation.  
- 📜 **Bridge History** tracking in the frontend for user transparency.  

**Unique aspects:**
- Designed specifically for **Conflux eSpace** with expansion to Base's and Arbitrum's liquidity.  
- Handles collections originating from any chain dynamically.  
- Lightweight, hackathon-ready prototype with enhanced reliability.

---

## ⚡ Conflux Integration

- [x] **eSpace** – Bridge and factory contracts deployed on eSpace.  
- [ ] **Core Space** – Not used.  
- [ ] **Cross-Space Bridge** – Not used in this POC.  
- [ ] **Gas Sponsorship** – Not implemented.  
- [ ] **Built-in Contracts** – Not used.  
- [ ] **Tree-Graph Consensus** – Inherited from eSpace.  

### Partner Integrations
- [x] **LayerZero** – Cross-chain messaging layer.  
- [ ] **Privy** – Not used.  
- [ ] **Pyth Network** – Not used.  
- [ ] **Other** – N/A.  

---

## ✨ Features

### Core Features
- 🌉 **Symmetric Cross-chain NFT Bridging** between Conflux eSpace, Base, and Arbitrum (supports multiple tokens in one transaction).  
- 🔗 **Dynamic Token Support** with permissionless registration and automatic wrapper deployment.  
- 🏭 **NFT Collection Factory** for creating collections, minting/batch minting, burning/batch burning.  
- 🧾 **Full Metadata Support** (name, symbol, tokenURI passed across chains).  
- 📜 **Bridge History** viewing in the frontend.  
- ⚡ **Hackathon-ready demo** with frontend + contracts.  

### Current Limitations
- No UI integration for LayerZero fees or bridge time estimates (planned for future).  

### Future Roadmap
- ✅ Metadata bridging (completed).  
- ✅ Reliable NFT minting with factory and batch support (completed).  
- ✅ Symmetric bridging and dynamic wrappers (completed).  
- ⏳ Frontend enhancements for LayerZeroScan (fees, tracking).  
- ⏳ Mainnet-ready deployment with audits.  

---

## 🛠️ Technology Stack

### Frontend
- **Framework**: React + TypeScript + Vite.  
- **Web3 Integration**: ethers.js.  
- **Hosting**: [Vercel Demo](https://summerhackfest-2025-sooty.vercel.app/).  

### Blockchain
- **Networks**: Conflux eSpace, Base, Arbitrum.  
- **Smart Contracts**: Solidity.  
- **Framework**: Hardhat.  
- **Libraries**: OpenZeppelin (ERC721, Ownable, Clones).  

### External APIs
- Etherscan v2 API (loading NFTs by contract address).  
- eSpace Conflux Scan API (loading NFTs by contract address).  
- Arbiscan API (loading NFTs by contract address).  
- LayerZero for cross-chain messaging.  

---

## 🏗️ Architecture

The architecture is symmetric, with `DynamicONFTBridge` deployed on Conflux eSpace, Base, and Arbitrum. Native collections are locked/unlocked on their home chain, while wrappers are minted/burne[...]

```
    ┌────────────────────────────┐
    │          Frontend          │
    │    (React + Vite + ethers) │
    └─────────────▲──────────────┘
                  │
                  │ User tx / UI (incl. history)
                  │
    ┌─────────────┴──────────────┐
    │ Conflux/Base/Arbitrum      │
    │ (Origin Chain)             │
    │                            │
    │ DynamicONFTBridge          │
    │ (Lock native or Burn wrap) │
    └─────────────┬──────────────┘
                  │
                  │ LayerZero Msg (with metadata)
                  ▼
    ┌─────────────┴──────────────┐
    │        LayerZero            │
    │    Messaging Relayer/ULN    │
    └─────────────┬──────────────┘
                  │
                  │ LayerZero Msg (with metadata)
                  ▼
    ┌─────────────┴──────────────┐
    │ Conflux/Base/Arbitrum      │
    │ (Destination Chain)        │
    │                            │
    │ DynamicONFTBridge          │
    │ (Unlock native or Mint wrap)│
    └─────────────┬──────────────┘
                  │
                  │ Transfer/Mint NFT
                  ▼
          ┌───────┴────────┐
          │    Recipient   │
          │ (User wallet)  │
          └────────────────┘

```

### NFT Factory Flow (on Conflux)
```
    ┌────────────────────────────┐
    │          Frontend          │
    └─────────────▲──────────────┘
                  │
                  │ Create/Mint
                  │
    ┌─────────────┴──────────────┐
    │ NFTCollectionFactory       │
    │ (Deploy clone via Clones)  │
    └─────────────┬──────────────┘
                  │
                  │ Initialize/Mint
                  ▼
    ┌─────────────┴──────────────┐
    │ BaseNFT (Cloned Collection)│
    │ (ERC721 with URI storage)  │
    └─────────────────────────────┘
```

**Flow:**
1. User connects wallet in frontend.  
2. (Optional) Create NFT collection via factory (name, symbol, image, contractURI).  
3. Mint/batch mint NFTs to the collection.  
4. Select NFT(s), destination chain, and bridge.  
5. Approve NFT transfer if needed.  
6. Sign the bridge transaction (via `bridgeSend`).  
7. Origin bridge locks/burns NFT and sends LayerZero message with metadata.  
8. Destination bridge unlocks/mints NFT (deploying wrapper if first time).  
9. View bridge history in frontend.  

---

## 📄 Smart Contracts

### Key Contracts
- **NFTCollectionFactory**: Factory for creating and managing ERC721 collections using clones. Supports mint, batchMint, burn, batchBurn.  
- **BaseNFT**: Cloned ERC721 implementation with URI storage, collection metadata.  
- **DynamicONFTBridge**: Symmetric bridge contract for cross-chain transfers, handling natives and wrappers dynamically.  
- **WrappedONFT**: Wrapped ERC721 for foreign NFTs, with metadata support.  

### Deployed Addresses
- DynamicONFTBridge (Conflux eSpace): 0x8078EFb3CEe419Abde856B6F5f470CC9d8971319  
- DynamicONFTBridge (Base): 0xd97deC9D62011e63AD3Bd27B51E33c8df3Ac44Cf  
- DynamicONFTBridge (Arbitrum): 0x16dED18bd0ead69b331B0222110F74b5716627f8  
- NFTCollectionFactory (Conflux eSpace): 0x47fC91Df5266456BAc2de008A4A4DB7Ae532c5C8  
- WrappedONFT Implementation: Deployed internally by bridge.  

---

## 📋 Prerequisites

- Node.js (>= 18)  
- npm or yarn  
- Git  
- Fluent Wallet or MetaMask for eSpace (Rabby recommended for multichain support)  

---

## 🚀 Installation & Setup

**Clone the repo**
```bash
git clone https://github.com/0xfdbu/summerhackfest-2025.git
```

**Contract setup instructions**
```bash
https://github.com/0xfdbu/summerhackfest-2025/blob/main/projects/layerzero_nftBridge/contracts/README.md
```

**Frontend setup instructions**
```bash
https://github.com/0xfdbu/summerhackfest-2025/blob/main/projects/layerzero_nftBridge/app/README.md
```

Open: [http://localhost:5173](http://localhost:5173)

---

## 📱 Usage

1. Connect your wallet (Fluent / MetaMask / Rabby).  
2. Create a new NFT collection via the factory if needed.  
3. Mint or batch mint NFTs to your collection.  
4. Select NFT(s) and target chain (Conflux, Base, or Arbitrum).  
5. Approve and send the bridge transaction.  
6. Wait for LayerZero delivery.  
7. NFT appears on destination chain with full metadata.  
8. Check bridge history in the frontend for past transfers.

---

## 🧪 Testing

```bash
# Run contract tests
cd contracts
npx hardhat compile
npx hardhat test
```

---

## 🚧 Known Issues & Limitations

- Frontend lacks LayerZero fee/time estimates (use LayerZeroScan manually).  
- Batch bridging supports multiple tokens but requires gas optimization for large batches.

---

## 🗺️ Roadmap

**Phase 1 (Hackathon) ✅**
- Core contracts deployed.  
- Demo frontend built.  
- Proof-of-concept live with symmetric bridging.  

**Phase 2 (Hackathon-Time-Extension) ✅**
- Metadata bridging.  
- Reliable minting with factory.  
- Bridge history in frontend.  

**Phase 3 (Future)**
- More Security audits.  
- Vast explorer with many features.

---

## 🤝 Contributing

We welcome contributions!  
Please fork, branch, and open a Pull Request.

---

## 📄 License

MIT License – see the LICENSE file for details.

---

## ⭐ Acknowledgments

- Conflux Hackathon  
- Conflux Network — hosting and platform  
- Conflux Team — technical guidance  
- Community — feedback and encouragement  

**Third-Party Tools**  
- LayerZero Labs — cross-chain messaging  
- OpenZeppelin — ERC721 contracts and utilities  
- Vercel — hosting  

Built with ❤️ for Code Without Borders – SummerHackfest 2025

---

Thanks for checking out our project!  
We hope it helps expand NFT innovation in the Conflux ecosystem.
