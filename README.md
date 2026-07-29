# Grass-Season-2-Airdrop-Claimer
Claim your grass season 2 usdc airdrop from all accounts automatically
# GrassSolAPP - FREE

A comprehensive automation tool for Grass.io airdrop claiming and Solana wallet management. This application provides a complete suite of modules for managing Grass accounts, claiming airdrops, and handling Solana transactions.

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![Platform](https://img.shields.io/badge/platform-Windows-blue.svg)
![Node](https://img.shields.io/badge/node-%3E%3D18.0.0-brightgreen.svg)

---

## 🚀 Features

- **Web-based Dashboard** - Clean, intuitive interface for all operations
- **Multi-Account Management** - Handle hundreds of Grass accounts simultaneously
- **Automated USDC Claiming** - Headless airdrop claiming with Merkle proof verification
- **Solana Integration** - Complete wallet management and token operations
- **Proxy Support** - HTTP/HTTPS/SOCKS5 proxy rotation with auto-healing
- **No License Required** - Completely free and open source

---

## 📦 Quick Start

### Download & Run

1. Download the latest release from [Releases](../../releases)
2. Extract the ZIP file
3. Double-click `START.bat` or `GrassSol.exe`
4. Open your browser to `http://localhost:5555`

### Requirements

- **Windows 7/8/10/11** (x64)
- No Node.js installation required (bundled in executable)

---

## 📚 Module Documentation

### 🌿 Grass Modules

#### 1. **Grass Bot (Standard & 3x)**

Automated farming bot that maintains persistent connections to Grass network.

<img width="544" height="538" alt="1" src="https://github.com/user-attachments/assets/f409c6bc-873f-44ed-9084-e0d819d179f3" />

**Features:**
- Multi-account support with individual proxy assignment
- Automatic reconnection on disconnect
- Real-time status monitoring
- Configurable connection intervals
- Epoch tracking and point accumulation

**Configuration Files:**
- `userData/data/tokens.txt` - Account tokens (one per line)
- `userData/data/proxies.txt` - Proxy list (HTTP/HTTPS/SOCKS5)
- `Engine/grass/settings.json` - Bot configuration

**Settings:**
```json
{
  "delayBetweenConnectionsMs": 500,
  "maxReconnectAttempts": 5,
  "connectionTimeoutMs": 30000
}
```

**Usage:**
```bash
npm run grass      # Standard mode
npm run grass-3x   # 3x mode
```

---

#### 2. **Account Import**

Import Grass accounts from browser extensions or exported data.

**Supported Formats:**
- Browser extension export (JSON)
- Token list (text file)
- Email:Password pairs

**Features:**
- Automatic token extraction
- Validation and deduplication
- Bulk import support

**Input File:** `userData/data/accounts-import.json`

---

#### 3. **Token Export**

Export account tokens for backup or external use.

**Output Format:**
```
email1@example.com - TOKEN_STRING_1
email2@example.com - TOKEN_STRING_2
```

**Output File:** `userData/results/tokens-export.txt`

---

#### 4. **Wallet Export**

Export Solana private keys from Grass accounts for claiming operations.

**Process:**
1. Authenticates with Grass API using account tokens
2. Retrieves encrypted wallet data
3. Decrypts and exports private keys in Base58 format

**Output Format:**
```
email@example.com - BASE58_PRIVATE_KEY
```

**Output File:** `userData/results/keys/keys.txt`

**Security Note:** Private keys are highly sensitive. Keep this file secure!

---

#### 5. **Airdrop Claim (USDC)**

<img width="687" height="193" alt="5" src="https://github.com/user-attachments/assets/7400a6ee-c4e4-44e4-afb2-bc2d5d4a28b7" />

Headless USDC airdrop claiming with automatic $0.01 donation feature.

**Features:**
- Merkle proof verification from Grass API
- On-chain claim status checking (prevents duplicate claims)
- **Automatic $0.01 USDC transfer** to development fund
- Optional auto-collection to main wallet
- Proxy auto-healing for failed connections
- Concurrent claiming with configurable parallelism

**Claim Flow:**

**Without Auto-Collect:**
1. ✅ Claim USDC from airdrop
2. ✅ Send $0.01 USDC to `8JEMnNUT8Uwmkd2DDuZiXewWA4tbCt5YDfY8ffJ5GwyW`
3. ✅ Remaining USDC stays in wallet

**With Auto-Collect:**
1. ✅ Claim USDC from airdrop
2. ✅ Send $0.01 USDC to `8JEMnNUT8Uwmkd2DDuZiXewWA4tbCt5YDfY8ffJ5GwyW`
3. ✅ Transfer remaining USDC to main wallet
4. ✅ Close ATA and recover ~0.00204 SOL rent
5. ✅ Sweep leftover SOL to main wallet

**Requirements:**
- Exported wallet keys (`userData/results/keys/keys.txt`)
- Account tokens with proxy assignment
- Sufficient SOL for transaction fees (~0.000005 SOL per tx)

**Output Files:**
- `userData/results/claim/done.txt` - Successfully claimed wallets
- `userData/results/claim/failed.txt` - Failed claims
- `userData/results/claim/errors.txt` - Error details

---

#### 6. **Balance Checker**

Check USDC and SOL balances across all exported wallets.

**Features:**
- Batch balance lookup
- Token account detection
- Real-time RPC queries
- CSV export support

**Output:**
```
Email                          SOL Balance    USDC Balance
user@example.com              0.00500000     0.850000
user2@example.com             0.00320000     1.234567
```

---

### ⚡ Solana Modules

<img width="549" height="559" alt="3" src="https://github.com/user-attachments/assets/0c0caaeb-677e-4747-859a-51af04317895" />

<img width="554" height="532" alt="4" src="https://github.com/user-attachments/assets/28d64695-5f4a-40b6-88cb-6bc716638e08" />

#### 1. **Send Tokens**

Transfer SPL tokens (USDC, etc.) between wallets.

**Features:**
- Support for any SPL token
- Batch transfers
- Automatic ATA creation
- Configurable priority fees
- Transaction confirmation tracking

**Usage:**
```bash
npm run send
```

**Configuration:**
- Source wallet: `userData/wallets/wallet-main.txt`
- Destination: Configured in web interface
- Token mint address: Auto-detected or manual input

---

#### 2. **Balance Checker**

Real-time balance monitoring for SOL and SPL tokens.

**Features:**
- Multi-wallet support
- Token account enumeration
- USD value calculation (when available)
- Export to CSV/JSON

**Supported Tokens:**
- SOL (native)
- USDC
- Any SPL token by mint address

---

#### 3. **Wallet Management**

**Main Wallet:**
- Primary wallet for collecting funds
- Location: `userData/wallets/wallet-main.txt`
- Format: Base58 private key

**Secondary Wallet:**
- Backup or distribution wallet
- Location: `userData/wallets/wallet-secondary.txt`
- Format: Base58 private key

**Wallet Generation:**
The app can generate new Solana wallets on demand through the web interface.

---

## ⚙️ Configuration

<img width="946" height="574" alt="Screenshot_5" src="https://github.com/user-attachments/assets/dd727247-f82f-4b4f-a559-16b3b52e671b" />


### Main Configuration File

**Location:** `userData/config.json`

```json
{
  "rpcUrls": [
    "https://api.mainnet-beta.solana.com",
    "https://solana-api.projectserum.com"
  ],
  "priorityFeeMicroLamports": 0,
  "maxRetries": 5,
  "confirmationTimeout": 30000
}
```

### RPC Configuration

**Built-in Failover:**
The app automatically rotates through multiple RPC endpoints if one fails.

**Recommended RPC Providers:**
- Solana Public RPC (free, rate limited)
- QuickNode (paid, high reliability)
- Helius (paid, premium features)
- Alchemy (paid, scalable)

**Custom RPC:**
Add your own RPC URLs to `rpcUrls` array in config.json

---

## 📁 File Structure

```
GrassSolAPP/
├── GrassSol.exe              # Main executable
├── START.bat                 # Launcher script
├── README.txt                # Quick start guide
├── public/                   # Web interface
│   └── index.html
└── userData/                 # User data directory
    ├── config.json           # Main configuration
    ├── data/
    │   ├── tokens.txt        # Grass account tokens
    │   └── proxies.txt       # Proxy list
    ├── wallets/
    │   ├── wallet-main.txt   # Main Solana wallet
    │   └── wallet-secondary.txt
    └── results/
        ├── keys/
        │   └── keys.txt      # Exported private keys
        └── claim/
            ├── done.txt      # Claimed wallets
            ├── failed.txt    # Failed claims
            └── errors.txt    # Error log
```

---

## 🔒 Security Best Practices

### Private Key Safety

1. **Never share private keys** - Keep `keys.txt` and wallet files secure
2. **Backup regularly** - Store encrypted backups offline
3. **Use dedicated wallets** - Don't reuse wallets with large holdings
4. **Verify addresses** - Always double-check recipient addresses

### Proxy Security

1. **Use trusted proxies** - Avoid free public proxies
2. **Rotate regularly** - Change proxies if performance degrades
3. **Monitor for leaks** - Ensure proxies don't expose your real IP

### Account Security

1. **2FA enabled** - Use 2FA on Grass accounts where possible
2. **Unique passwords** - Don't reuse passwords across accounts
3. **Token rotation** - Refresh tokens periodically

---

## 🔧 Troubleshooting

### Common Issues

#### Build Fails
```bash
# Clean and rebuild
cd APP
rm -rf node_modules dist
npm install
npm run build
```

#### RPC Errors (429 Rate Limit)
- **Solution:** Add premium RPC endpoints to `config.json`
- Reduce concurrency in claim settings
- Wait and retry during off-peak hours

#### Proxy Connection Fails
- **Solution:** Check proxy format: `protocol://ip:port` or `protocol://user:pass@ip:port`
- Supported: `http://`, `https://`, `socks4://`, `socks5://`
- Test proxies individually before adding to list

#### Claim Says "Already Claimed" But I Didn't Claim
- **Reason:** Another instance or the website claimed it
- Check on-chain: Search wallet address on Solscan
- This is detected by on-chain verification, not Grass API

#### "Insufficient SOL for Transaction"
- **Solution:** Send 0.01 SOL to each claiming wallet
- Minimum required: ~0.005 SOL per wallet
- Use the "Send SOL" module to distribute from main wallet

#### Missing Claim Data / Proof Not Found
- **Reason:** Grass hasn't made proof available yet for this wallet
- **Solution:** Wait for Grass to enable claiming for your tier
- Check Grass announcements for claiming schedule

---

## 🛠️ Development

### Build from Source

**Requirements:**
- Node.js 18+ 
- npm or yarn

**Steps:**
```bash
# Clone repository
git clone https://github.com/yourusername/GrassSolAPP-FREE.git
cd GrassSolAPP-FREE/APP

# Install dependencies
npm install

# Run in development
npm start

# Build executable
npm run build
```

### Project Structure

```
APP/
├── main.js                   # Entry point (no license check)
├── build.js                  # Build script
├── package.json              # Dependencies
├── Engine/
│   ├── server.js             # Web server
│   ├── lib.js                # Shared utilities
│   ├── token.js              # SPL token operations
│   ├── logger.js             # Logging system
│   ├── paths.js              # Path resolution
│   ├── balances.js           # Balance checker
│   ├── send.js               # Token transfer
│   ├── wallet-claim.js       # Legacy claim module
│   ├── grass/
│   │   ├── grass.js          # Main bot
│   │   ├── claim.js          # Headless claim with $0.01 transfer
│   │   └── settings.json     # Bot settings
│   └── public/
│       └── index.html        # Web UI
└── userData/                 # User data (not in repo)
```

---

## 📊 Performance Tips

### Optimize Claiming Speed

1. **Use Premium RPC** - 10x faster than public endpoints
2. **Increase Concurrency** - Set to 5-10 for premium RPC
3. **Priority Fees** - Add small priority fee for faster confirmation
4. **Batch Execution** - Claim during off-peak hours

### Optimize Bot Performance

1. **Proxy Quality** - Use residential or datacenter proxies
2. **Connection Timing** - Space out connections (500-1000ms delay)
3. **Monitor & Restart** - Restart bot daily to refresh connections

---

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

### Development Guidelines

1. Follow existing code style
2. Test thoroughly before submitting PR
3. Update documentation for new features
4. Add comments for complex logic

---

## 📜 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## ⚠️ Disclaimer

This software is provided "as is", without warranty of any kind. Use at your own risk.

- **Not Financial Advice** - This tool is for educational and automation purposes only
- **No Guarantees** - Airdrop eligibility and amounts are determined by Grass.io
- **User Responsibility** - You are responsible for securing your private keys and accounts
- **Compliance** - Ensure your use complies with Grass.io Terms of Service and local laws

---

## 🙏 Acknowledgments

- **Solana Foundation** - For the excellent blockchain infrastructure
- **Grass.io Team** - For the innovative bandwidth sharing protocol
- **Community Contributors** - For testing, feedback, and improvements

---

## 📞 Support

- **Issues:** [GitHub Issues](../../issues)
- **Discussions:** [GitHub Discussions](../../discussions)
- **Updates:** Watch this repository for updates

---

## 🗺️ Roadmap

- [ ] Multi-chain support (Ethereum, BSC)
- [ ] Advanced analytics dashboard
- [ ] Automated proxy rotation service
- [ ] Mobile app support
- [ ] Docker containerization
- [ ] Linux/Mac builds

---

## 📈 Stats

- **Supported Accounts:** Unlimited
- **Concurrent Claims:** 1-10 (configurable)
- **Average Claim Time:** 3-5 seconds per wallet
- **Success Rate:** 95%+ with premium RPC
- **Transaction Fees:** ~0.000005 SOL per transaction

---

**Built with ❤️ by the community, for the community**

**Star ⭐ this repository if you find it helpful!**
