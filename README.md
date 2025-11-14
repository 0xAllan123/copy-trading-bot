# Copy Trading Bot for Solana

A professional, modular copy-trading engine that monitors a target wallet on Solana and replicates its trades across your wallets. The project focuses on reliable trade replication, cross-DEX routing, observability, and configurable risk controls.

## Features
- Real-time monitoring of target wallet transactions
- Cross-DEX execution (Raydium, Orca, Jupiter and more)
- Configurable trade filters and risk-management rules
- Multi-wallet support and concurrent execution
- Price lookup, token metadata, and on-chain account inspection
- Optional integration with a local validator for pre-confirmation monitoring
- Simple frontend controls to start/stop the bot and adjust settings

## Benefits
- Tap into experienced traders’ strategies with automated replication
- Best-effort execution across Solana liquidity sources to reduce slippage
- Configurable behavior to match different risk profiles and capital allocation
- Extensible adapters for additional DEXes and routing services

## Architecture (high level)
- Listener: observes transactions from a target wallet or RPC/websocket feed
- Analyzer: classifies transactions and extracts actionable trades
- Router: chooses the best DEX and execution path (Jupiter/Raydium/Orca)
- Executor: performs signed transactions for one or more local wallets
- Telemetry: logs activity, PnL, and trade metrics for monitoring

## Requirements
- Node.js 18+ (LTS recommended)
- npm or yarn
- A funded Solana wallet(s) to execute trades
- RPC endpoint (public or private) — optional local validator for pre-confirmation monitoring

## Environment variables
Create a .env file in the project root with values for:
- HELIUS_API_KEY — Helius API key (used for token metadata and on-chain data)
- RPC_URL — Solana RPC endpoint (optional)
- MNEMONIC / PRIVATE_KEYS — keys for the bot wallets (handle securely)
- LOG_LEVEL — debug/info/warn/error

Example (.env):
HELIUS_API_KEY=your_helius_key_here
RPC_URL=https://api.mainnet-beta.solana.com
LOG_LEVEL=info

## Setup (Windows)
1. Install dependencies
   - PowerShell or CMD:
     npm install
2. Build (if using TypeScript)
   npm run build
3. Run (development)
   npm run dev
4. Run (production)
   npm start

Adjust npm scripts in package.json as required.

## Usage
- Configure environment variables and wallet keys
- Start the bot and specify the target wallet to follow
- Monitor logs and the frontend to control replication and view PnL

Example CLI (if available):
npm run follow -- --target <TARGET_WALLET_ADDRESS>

## Security and Safety
- Never commit private keys or mnemonics to source control.
- Run wallets with limited funds for testing before scaling capital.
- Use hardware wallets or managed custody where possible for production.
- Review and audit smart contract interactions and on-chain approvals.

## Performance
- The bot supports standard RPC and can integrate with a local validator.
- For ultra-low latency production deployments, use optimized RPC/gRPC stacks and colocated infrastructure.

## Observability
- Logging (structured JSON recommended)
- Trade and PnL metrics exported for dashboards (Prometheus/Grafana recommended)
- Error alerts for failed executions and insufficient balance events

## Contributing
- Fork, implement a fix or feature, add tests, and open a pull request
- Follow code style and include unit tests for core modules

## License
Specify project license here (e.g., MIT). Update LICENSE file accordingly.

## Example resources
- Solana transaction examples (for demonstration):
  - Target tx: https://solscan.io/tx/gEGTHyF1JH2GUYpML79m6rnzYpE3y2CJ3r4U2STa8himW53rzdCCAVkTdkLW9w7x3YE5pLw4vYa9qqWaLzKGrfp
  - Bot tx: https://solscan.io/tx/i8UKtsMbkfdz481MSD68Kawj3o8AkTyHLkjiJsgGfCZAtebUBnUCZ18TYkzCZxJLAkkrteU98sHxhiq3kwtL9rc

## Contact
Project maintainer: Allan  
Telegram: https://t.me/oxgoldenledger  
Twitter: https://x.com/oxgoldenledger
