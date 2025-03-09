# BioWallet Agent: Verifiable AI Backend 🧠🔐

## 🌟 Overview

BioWallet Agent is the backend service that powers the BioWallet application with **verifiable AI capabilities**. Built to work with Sonic Network, it provides cryptographically proven AI interactions and transaction processing.

This agent uses Opacity's zkTLS technology to ensure all AI responses can be verified on-chain, creating a trustworthy environment for financial transactions and data exchange.

## ✨ Key Features

- 🧠 **Verifiable AI Engine** - AI responses with cryptographic proof using Opacity's zkTLS
- 🔗 **Sonic Network Integration** - Direct connection to Sonic Network for transactions
- 📝 **Transaction Verification** - Every transaction includes cryptographic proof
- 🔄 **REST API** - Simple endpoints for the frontend to consume
- 🛡️ **Security Focus** - End-to-end verification of all operations

## 🚀 Quick Start

### Prerequisites

- Node.js v18+
- npm or pnpm
- Sonic Network account/credentials

### Installation

```bash
# Clone the repository
git clone https://github.com/your-username/biowallet.git

# Install dependencies
npm install
# or
pnpm install

# Set up environment variables
cp .env.example .env
# Edit .env with your API keys and configuration
```

### Configuration

Edit your `.env` file with the following credentials:

```
# Opacity (for verifiable AI)
OPACITY_OPENAI_KEY=your_opacity_key
OPACITY_TEAM_ID=your_team_id
OPACITY_TEAM_NAME=your_team_name
OPACITY_PROVER_URL=https://prover.opacity.io

# Sonic Network Configuration
SONIC_RPC_URL=your_sonic_rpc_url
SONIC_CHAIN_ID=your_sonic_chain_id
SONIC_PRIVATE_KEY=your_private_key
```

### Running the Agent

```bash
# Development mode
npm run dev

# Production build
npm run build
npm start
```

## 🔧 API Endpoints

### Generate Verifiable AI Response

```bash
POST /api/generate
```

Request body:

```json
{
  "prompt": "Transfer 5 SONIC to 0x123...",
  "user": "0xYourAddress"
}
```

Response:

```json
{
  "response": {
    "text": "I'll transfer 5 SONIC to 0x123...",
    "functionCall": {
      "name": "transferTokens",
      "args": {
        "amount": "5",
        "recipient": "0x123...",
        "token": "SONIC"
      }
    }
  },
  "verification": {
    "proofId": "abc123...",
    "timestamp": 1678234567,
    "signature": "0xdef456..."
  }
}
```

### Get Transaction History

```bash
GET /api/transactions/:address
```

Response:

```json
{
  "address": "0xYourAddress",
  "count": 2,
  "transactions": [
    {
      "hash": "0xabc...",
      "timestamp": 1678234567,
      "amount": "5",
      "token": "SONIC",
      "recipient": "0x123...",
      "status": "confirmed",
      "proofId": "abc123..."
    },
    ...
  ]
}
```

### Health Check

```bash
GET /health
```

Response:

```json
{
  "status": "healthy",
  "version": "1.0.0",
  "opacity": "connected",
  "sonicNetwork": "connected"
}
```

## 🧩 How It Works

1. **Request Processing**: The agent receives a request from the frontend
2. **AI Inference**: The prompt is processed by Opacity's verifiable AI
3. **Proof Generation**: zkTLS proof is generated for the AI response
4. **Function Extraction**: Any requested actions (transfers, etc.) are extracted
5. **Blockchain Integration**: Transactions are submitted to Sonic Network
6. **Verified Response**: The response and proof are returned to the frontend

## 🛠️ Development

### Project Structure

```
bioWallet-opacity-agent/
├── src/
│   ├── agent/
│   │   ├── createAgent.ts      # Core agent implementation
│   │   └── verifier.ts         # Proof verification logic
│   ├── blockchain/
│   │   └── sonicNetwork.ts     # Sonic Network integration
│   ├── api/
│   │   ├── generate.ts         # AI generation endpoint
│   │   └── transactions.ts     # Transaction history endpoint
│   ├── types/                  # TypeScript type definitions
│   ├── server.ts               # Express API server
│   └── index.ts                # Entry point
├── test/                       # Unit and integration tests
├── package.json
└── tsconfig.json
```

### Adding New Features

1. Implement your feature in the appropriate file
2. Add any new API endpoints to `src/api/`
3. Update types as needed in `src/types/`
4. Write tests in the `test/` directory
5. Document the new functionality in this README

## 📜 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 🙏 Acknowledgements

- [Sonic Network](https://sonic.network/) - For providing the blockchain infrastructure
- [Opacity](https://opacity.io/) - For verifiable AI technology

---

Built with ❤️ by the BioWallet Team
