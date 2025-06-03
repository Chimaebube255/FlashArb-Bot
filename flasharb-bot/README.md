# Flash Loan Arbitrage Bot 🚀

An automated arbitrage bot built for the Stacks blockchain that leverages flash loans to capture price differences across decentralized exchanges (DEXs) without requiring upfront capital.

## 🎯 Overview

This smart contract implements a sophisticated arbitrage bot that:
- Monitors price differences across multiple DEXs (Alex, Arkadiko, StackSwap, BitFlow)
- Executes flash loan-based arbitrage trades automatically
- Manages risk through configurable parameters
- Tracks performance and profitability metrics

## 🏗️ Architecture

The bot operates through several key components:

### Core Modules
- **Price Feed Management**: Real-time price tracking across exchanges
- **Arbitrage Detection**: Automated opportunity identification
- **Flash Loan Integration**: Capital-efficient trade execution
- **Risk Management**: Slippage protection and profit thresholds
- **Statistics Tracking**: Performance monitoring and analytics

### Supported Exchanges
- **Alex** (Exchange ID: 1)
- **Arkadiko** (Exchange ID: 2) 
- **StackSwap** (Exchange ID: 3)
- **BitFlow** (Exchange ID: 4)

### Supported Tokens
- STX, USDA, ALEX, DIKO, XUSD, stSTX

## 🚀 Quick Start

### Prerequisites
- Stacks wallet with STX for gas fees
- Contract deployment tools (Clarinet recommended)
- Access to supported DEX contracts

### Installation

1. **Clone the repository**
```bash
git clone https://github.com/your-username/flash-loan-arbitrage-bot
cd flash-loan-arbitrage-bot
```

2. **Deploy the contract**
```bash
clarinet deployments apply -p devnet
```

3. **Configure exchanges**
```clarity
(configure-exchange 
  u1 ;; Alex
  "Alex DEX"
  'SP3K8BC0PPEVCV7NZ6QSRWPQ2JE9E5B6N3PA0KBR9.amm-swap-pool
  'SP3K8BC0PPEVCV7NZ6QSRWPQ2JE9E5B6N3PA0KBR9.amm-router
  u30  ;; 0.3% fee
  true ;; Flash loan supported
)
```

## 📖 Usage

### Basic Operations

#### 1. Create Arbitrage Opportunity
```clarity
(create-arbitrage-opportunity
  u1    ;; STX
  u2    ;; USDA  
  u1    ;; Buy on Alex
  u2    ;; Sell on Arkadiko
  u1000000000000 ;; 1M STX loan amount
)
```

#### 2. Execute Arbitrage
```clarity
(execute-arbitrage u1) ;; Execute opportunity ID 1
```

#### 3. Scan for Opportunities
```clarity
(scan-for-opportunities)
```

### Configuration Management

#### Update Bot Settings
```clarity
(update-config
  u1000000    ;; Min profit (1 STX)
  u300        ;; Max slippage (3%)
  u2000000    ;; Gas limit
  u30         ;; Flash loan fee (0.3%)
)
```

#### Toggle Bot Status
```clarity
(toggle-bot true)  ;; Enable bot
(toggle-bot false) ;; Disable bot
```

## 🔧 Configuration Parameters

| Parameter | Default | Description |
|-----------|---------|-------------|
| `min-profit-threshold` | 1,000,000 μSTX | Minimum profit required |
| `max-slippage` | 300 bp | Maximum acceptable slippage (3%) |
| `gas-limit` | 2,000,000 | Maximum gas per operation |
| `flash-loan-fee` | 30 bp | Flash loan fee (0.3%) |
| `execution-timeout` | 10 blocks | Maximum execution time |
| `max-loan-amount` | 10M STX | Maximum flash loan size |

## 📊 Monitoring & Analytics

### View Bot Statistics
```clarity
(get-bot-stats u123) ;; Get stats for period 123
```

### Check Execution History
```clarity
(get-execution-history u1) ;; View execution ID 1
```

### Monitor Current Config
```clarity
(get-bot-config)
```

## 🛡️ Risk Management

### Built-in Protections
- **Slippage Control**: Configurable maximum slippage tolerance
- **Profit Thresholds**: Minimum profit requirements before execution
- **Time Limits**: Execution timeouts prevent stuck transactions
- **Gas Limits**: Maximum gas consumption controls
- **Price Staleness**: Fresh price feed requirements

### Emergency Controls
```clarity
(emergency-stop)              ;; Immediately disable bot
(force-repay-flash-loan addr) ;; Force loan repayment
```

## 🔍 Read-Only Functions

| Function | Purpose |
|----------|---------|
| `calculate-arbitrage-profit` | Estimate profit for given parameters |
| `check-arbitrage-opportunity` | Validate opportunity existence |
| `get-token-price` | Retrieve current token prices |
| `get-bot-config` | View current configuration |
| `is-bot-enabled` | Check bot operational status |

## 📈 Performance Metrics

The bot tracks comprehensive statistics:
- Total executions and success rate
- Volume processed and profits earned
- Gas consumption and efficiency
- Opportunity identification vs execution ratio

## ⚠️ Important Considerations

### Flash Loan Requirements
- Loans must be repaid within the same transaction
- Flash loan fees are automatically calculated
- Insufficient liquidity will cause transaction failure

### MEV Protection
- Consider transaction privacy to avoid front-running
- Monitor gas prices for optimal execution timing
- Be aware of potential sandwich attacks

### Regulatory Compliance
- Ensure compliance with local regulations
- Consider tax implications of automated trading
- Maintain proper records for regulatory purposes

## 🐛 Error Codes

| Code | Error | Description |
|------|-------|-------------|
| u100 | ERR-OWNER-ONLY | Only contract owner can perform this action |
| u101 | ERR-NOT-FOUND | Requested resource not found |
| u102 | ERR-INVALID-AMOUNT | Invalid amount specified |
| u105 | ERR-FLASH-LOAN-FAILED | Flash loan operation failed |
| u106 | ERR-ARBITRAGE-FAILED | Arbitrage execution failed |
| u107 | ERR-SLIPPAGE-EXCEEDED | Slippage tolerance exceeded |
| u108 | ERR-INSUFFICIENT-PROFIT | Profit below minimum threshold |

## 🔮 Future Enhancements

- [ ] Multi-hop arbitrage support
- [ ] Advanced MEV protection
- [ ] Machine learning price prediction
- [ ] Cross-chain arbitrage capabilities
- [ ] Automated parameter optimization
- [ ] Mobile monitoring dashboard

## 🤝 Contributing

We welcome contributions! Please see our [Contributing Guidelines](CONTRIBUTING.md) for details.

### Development Setup
```bash
# Install Clarinet
curl --proto '=https' --tlsv1.2 -sSf https://sh.clarinet.xyz | sh

# Run tests
clarinet test

# Check contract syntax
clarinet check
```

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## ⚡ Disclaimer

**Important**: This software is provided as-is for educational purposes. Automated trading involves significant financial risk. Users are responsible for:
- Understanding smart contract functionality
- Conducting thorough testing before mainnet deployment  
- Managing their own risk exposure
- Complying with applicable regulations

The authors are not responsible for any financial losses incurred through use of this software.

## 🔗 Links

- [Stacks Documentation](https://docs.stacks.co/)
- [Clarity Language Reference](https://docs.stacks.co/clarity)
- [Alex Protocol](https://alexgo.io/)
- [Arkadiko Protocol](https://arkadiko.finance/)

## 📞 Support

- Create an [Issue](https://github.com/your-username/flash-loan-arbitrage-bot/issues) for bugs
- Join our [Discord](https://discord.gg/your-server) for discussions
- Follow us on [Twitter](https://twitter.com/your-handle) for updates

---

**Built with ❤️ for the Stacks ecosystem**