# GrassSolAPP - Grass Season 2 Airdrop Claimer

A comprehensive automation tool for Grass.io airdrop claiming and Solana wallet management. This application provides a complete suite of modules for managing Grass accounts, claiming airdrops, and handling Solana transactions.

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![Platform](https://img.shields.io/badge/platform-Windows-blue.svg)
![Node](https://img.shields.io/badge/node-%3E%3D18.0.0-brightgreen.svg)

## 🙏 Acknowledgments

**Author:** [@softerx49](https://t.me/softerx49) on Telegram

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
2. Extract the ZIP file to any location
3. Run `GrassSol.exe`
4. The application will start automatically
5. Open your browser to `http://localhost:5555`
6. Use the web interface to manage all operations

### Requirements

- **Windows 7/8/10/11** (x64)
- No installation required - just download and run!
- No Node.js, Python, or any dependencies needed

---

## 📚 Module Documentation

### 🌿 Grass Modules

<img width="544" height="538" alt="1" src="https://github.com/user-attachments/assets/5ab88d38-9b0d-478c-a8ae-be984b18ec72" />

#### 1. **Grass Bot**

Automated farming bot that maintains persistent connections to Grass network.

**Features:**
- Multi-account support with individual proxy assignment
- Automatic reconnection on disconnect
- Real-time status monitoring
- Configurable connection intervals
- Epoch tracking and point accumulation

**Configuration Files:**
- `userData/data/tokens.txt` - Account tokens (one per line)
- `userData/data/proxies.txt` - Proxy list (HTTP/HTTPS/SOCKS5)
- `userData/config.json` - APP configuration

**How to Use:**
1. Open the web interface at `http://localhost:5555`

#### 2. **Account Login & Token Generation**

Generate authentication tokens from account credentials.

**Supported Formats:**
- `account:account_password`
- One account per line

**Features:**
- Automatic login and token extraction
- Session management
- Token refresh
- Bulk import support
- **Automatic captcha solving** (2Captcha/CapMonster/CapSolver)

**Requirements:**
- Valid captcha service API key configured in `config.json`

**Input File:** `userData/data/accs.txt`

**Features:**
- Automatic token extraction
- Validation and deduplication
- Bulk import support

**Input File:** `userData/data/accs.txt`

---

#### 3. **Token Export**

Export account tokens for backup or external use.

**Output Format:**
```
email1@example.com - TOKEN_STRING_1
email2@example.com - TOKEN_STRING_2
```

**Output File:** `userData/results/tokens.txt`

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

Headless USDC airdrop claiming with automatic $0.01 donation feature.

**Features:**
- Merkle proof verification from Grass API
- On-chain claim status checking (prevents duplicate claims)
- **Automatic $0.01 USDC transfer** to development fund
- Optional auto-collection to main wallet
- Proxy auto-healing for failed connections
- Concurrent claiming with configurable parallelism

**Claim Flow:**

<img width="687" height="193" alt="5" src="https://github.com/user-attachments/assets/4ae7687b-0556-4e83-9b77-b8ad6f19e450" />

Overall Fees for 1 Claim: **~0.00132 SOL**

**Without Auto-Collect:**
1. ✅ Claim USDC from airdrop
2. ✅ Send $0.01 USDC to `Developer`
3. ✅ Remaining USDC stays in wallet

**With Auto-Collect:**
1. ✅ Claim USDC from airdrop
2. ✅ Send $0.01 USDC to `Developer`
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

<img width="549" height="559" alt="3" src="https://github.com/user-attachments/assets/4bb68919-acaf-4ed1-b9e0-0dc62775f464" />

#### 1. **Send Tokens**

Transfer SPL tokens (USDC, etc.) between wallets.

**Features:**
- Support for any SPL token
- Batch transfers
- Automatic ATA creation
- Configurable priority fees
- Transaction confirmation tracking

**How to Use:**
1. Open the web interface
2. Navigate to **Send Tokens** module
3. Enter destination address and amount
4. Click **"Send"**

**Configuration:**
- Source wallet: `userData/wallets/wallet-main.txt`
- Destination: Enter in web interface
- Token mint address: Auto-detected or manual input

---

#### 2. **Balance Checker**

<img width="554" height="532" alt="4" src="https://github.com/user-attachments/assets/0ff734ab-e111-481b-b967-41a9b62ddf6b" />

Real-time balance monitoring for SOL and SPL tokens.

**Features:**
- Multi-wallet support
- Token account enumeration![Uploading 4.png…]()

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

### Main Configuration File

<img width="946" height="574" alt="Screenshot_5" src="https://github.com/user-attachments/assets/26932655-fd5d-4416-9657-967f1131386a" />

**Location:** `userData/config.json`

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

#### Application Won't Start
- **Solution:** Right-click `GrassSol.exe` → "Run as Administrator"
- Check Windows Firewall settings
- If Windows SmartScreen blocks it: Click "More info" → "Run anyway"

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

## 🎯 How to Use Each Module

All modules are accessed through the web interface at `http://localhost:5555` after running the application.

### Step-by-Step Guide:

1. **Start the Application**
   - Double-click `START.bat` or `GrassSol.exe`
   - Wait for "Server running on port 5555" message
   - Open browser to `http://localhost:5555`

2. **Import Accounts**
   - Click **"Account Import"** in the navigation
   - Upload your accounts file or paste tokens
   - Click **"Import"**

3. **Export Wallets**
   - Click **"Wallet Export"**
   - Click **"Export All Wallets"**
   - Keys will be saved to `userData/results/keys/keys.txt`

4. **Claim Airdrop**
   - Click **"Claim Airdrop"**
   - Configure auto-collect settings if desired
   - Click **"Start Claiming"**
   - Monitor progress in real-time

5. **Check Balances**
   - Click **"Check Balances"**
   - View SOL and USDC balances for all wallets
   - Export results if needed

6. **Run Grass Bot**
   - Click **"Grass Bot"**
   - Select standard or 3x mode
   - Click **"Start Bot"**
   - Bot runs in background, check status anytime

---

## 📊 Performance Tips

### Optimize Claiming Speed

1. **Use Premium RPC** - 10x faster than public endpoints
2. **Increase Concurrency** - Set to 5-10 for premium RPC
3. **Priority Fees** - Add small priority fee for faster confirmation
4. **Batch Execution** - Claim during off-peak hours

### Optimize Bot Performance

1. **Proxy Quality** - Use residential proxies
2. **Connection Timing** - Space out connections (500-1000ms delay)
3. **Monitor & Restart** - Restart bot daily to refresh connections

---

## 💡 Tips for Best Results

### Claiming Airdrops
1. **Timing Matters** - Claim during off-peak hours for faster processing
2. **Use Good Proxies** - Quality proxies = higher success rate
3. **Check Balances First** - Ensure wallets have ~0.005 SOL for fees
4. **Enable Auto-Collect** - Consolidate funds automatically to main wallet

### Running Grass Bot
1. **Quality Proxies** - Use residential or datacenter proxies
2. **Monitor Regularly** - Check dashboard for disconnected accounts
3. **Restart Daily** - Fresh connections improve performance
4. **Spread Connections** - Don't connect all accounts at once

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

## 📈 Stats

- **Supported Accounts:** Unlimited
- **Average Claim Time:** 3-5 seconds per wallet
- **Success Rate:** 95%+ with premium RPC
- **Transaction Fees:** ~0.000005 SOL per transaction

---

**Built with ❤️ by the community, for the community**

**Star ⭐ this repository if you find it helpful!**
