Now let focus on dapp which works with jetton and nft , let start with prerequisite

Okay, let's gear up to build a dApp that interacts with Jettons (fungible tokens) and NFTs (non-fungible tokens) on the TON blockchain. Before we dive into the code, it's crucial to understand the prerequisites and the underlying concepts.

**Prerequisites for Building a TON dApp with Jettons and NFTs**

1.  **Understanding TON Concepts:**

    - **TON Blockchain:** Familiarity with the TON blockchain's architecture and concepts.
    - **TON Smart Contracts:** Knowledge of how smart contracts are written, deployed, and interacted with on TON (using FunC or Tact).
    - **TON Addresses:** Understanding how TON addresses are formatted and used.
    - **TON Transactions:** Knowledge of how transactions are created, signed, and sent on the TON blockchain.
    - **TON SDK:** Basic understanding of the TON SDK for interacting with the blockchain.

2.  **Jettons and NFTs on TON:**

    - **Jettons (Fungible Tokens):** Understand that Jettons are smart contracts that represent a fungible token. Each jetton has an address and follows a specific set of rules for transfers, minting, and burning tokens.
    - **NFTs (Non-Fungible Tokens):** Understand that NFTs are also smart contracts. Each NFT is unique (non-fungible) and is identified by an address and a unique ID.
    - **NFT Collection:** An NFT collection is a smart contract that contains (or knows about) a group of NFTs.
    - **Metadata:** Understanding how Jetton and NFT metadata (name, description, image URI, etc.) is stored and accessed, usually using on-chain and/or off-chain solutions.

3.  **Development Tools:**

    - **Node.js and npm/yarn:** Needed for your Next.js app and TON SDK.
    - **Text Editor or IDE:** VS Code, Sublime Text, or your preferred IDE.
    - **TON SDK:** Install the TON SDK libraries (as we have done in the previous examples using `@ton/ton` and other related packages).
    - **TON Connect:** Install `@tonconnect/ui-react` for wallet integration.
    - **Prisma or Similar:** For database interactions (if necessary).
    - **Docker:** (Optional, but recommended) for containerizing your application.
    - **TON Wallet:** A TON wallet for testing (e.g., Tonkeeper) and for connecting to your Mini App.
    - **TON Testnet Faucet:** You'll need testnet TON tokens for testing (can be obtained from faucets).

4.  **Smart Contracts:**

    - **Jetton Smart Contract:** You'll need a Jetton smart contract that defines the token's logic. You can find example implementation in [TON docs](https://docs.ton.org/develop/smart-contracts/fungible-token).
    - **NFT Collection Smart Contract (Optional):** If you will be creating new NFTs, you'll need an NFT collection contract and potentially individual NFT contracts. You can find example implementation in [TON docs](https://docs.ton.org/develop/smart-contracts/non-fungible-token).
      - **Contract deployment:** You must deploy the smart contracts on TON blockchain to interact with them.

5.  **Development Environment Setup**
    - Follow the previous steps to setup the project with NextJS, docker and prisma.
    - Make sure to install all the required packages mentioned above.

**Key Concepts to Understand**

1.  **Jetton/NFT Address Retrieval:** You'll need to know the smart contract address for your Jetton or NFT collection contracts to interact with them. This address is the gateway to the token.
2.  **User Wallet Interaction:**
    - **TON Connect:** Users will connect their wallets to your Mini App using TON Connect.
    - **Transaction Signing:** When users make a transaction (e.g., transfer tokens, mint NFTs), they'll need to sign the transactions with their private keys. This is handled by TON Connect.
3.  **Data Encoding:**
    - TON transactions require data to be encoded into binary format (using Cells and BoCs - Bag of Cells) when interacting with smart contracts. You will need to familiarize with these encodings to construct proper calls to your smart contracts methods.
4.  **Gas Fees:** Transactions on TON require gas fees, so you must consider how to pay them (usually the user pays) when sending a transaction.

**Prerequisite Code**

Before moving forward, make sure you have the following packages installed:

```bash
npm install @ton/ton ton-crypto @orbs-network/ton-access @tonconnect/ui-react @prisma/client next react react-dom
```

**Example Prisma Schema (Simplified)**

For storing NFT information or any other relevant information in your backend:

```prisma
// prisma/schema.prisma
generator client {
    provider = "prisma-client-js"
}

datasource db {
    provider = "postgresql"
    url      = env("DATABASE_URL")
}

model User {
    id        Int     @id @default(autoincrement())
    points    Int     @default(0)
    taps      Int     @default(0)
    upgradeLevel Int @default(0)
    referredBy    Int?
}

model NFT {
    id        Int     @id @default(autoincrement())
    ownerAddress   String
    metadataURI   String
    // Other fields to save for each nft
    // collection Address to refer to the token collection.
}
```

**Next Steps**

With these prerequisites in place, we can move into the core functionality.

1. Build the smart contracts for you jetton and nft
2. Deploy them on testnet or mainnet.
3. Retrieve their contract addresses.
4. Build the UI in NextJS that displays user’s balance, NFTs, and options for transferring and minting.

Are you ready to start diving deeper with the code for the next steps? Do you have any questions about these prerequisites?
