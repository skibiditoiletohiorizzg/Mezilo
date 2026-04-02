# 🌙 Mezilo Blockchain Suite

Complete blockchain implementation with **LunarEVM** - a Cosmos SDK-based blockchain with Proof of Stake, Proof of History, custom tokens, and NFTs.

---

## 📁 Project Structure

```
/workspaces/Mezilo/
├── cosmos-sdk/              # Cosmos SDK source code
├── lunarEVM/                # Main blockchain implementation
│   ├── cmd/lunarEVMd/      # CLI command entry point
│   ├── rpc/                # RPC servers (EVM + Solana)
│   ├── x/                  # Blockchain modules (nft, token, poh, evm)
│   ├── app/                # App configuration
│   ├── lunarEVMd           # Compiled binary
│   ├── COMMANDS.md         # Complete CLI reference
│   ├── START_HERE.md       # Quick start guide
│   ├── README.md           # Blockchain overview
│   └── chainlist.json      # Network metadata
└── README.md               # This file
```

---

## 🚀 Quick Start (60 seconds)

### 1. Navigate to blockchain directory

```bash
cd /workspaces/Mezilo/lunarEVM
```

### 2. Initialize blockchain

```bash
./lunarEVMd init
```

### 3. Use real CLI commands

```bash
# Create wallet
./lunarEVMd wallet create my-wallet

# Create and mint token (max 5000 per tx)
./lunarEVMd token create "MyToken" MYTOKEN
./lunarEVMd token mint MYTOKEN 5000 lunar1recipient

# Create NFT
./lunarEVMd nft create "My NFT" MYNFT "https://example.com/metadata.json"

# Check status
./lunarEVMd status
```

### 4. Done! 🎉

All data is stored persistently in `~/.lunarEVM/`

---

## 📚 Where to Run Commands

**ALL commands run from inside the `lunarEVM` directory:**

```bash
cd /workspaces/Mezilo/lunarEVM
./lunarEVMd <command>
```

---

## 🔧 Common Commands

### Start & Initialize

```bash
cd /workspaces/Mezilo/lunarEVM

./lunarEVMd init          # Initialize blockchain (one-time)
./lunarEVMd status        # Show network status
./lunarEVMd version       # Show version
./lunarEVMd ping          # Test network
```

### Wallets & Keys

```bash
# Create wallet
./lunarEVMd wallet create my-wallet
./lunarEVMd wallet list
./lunarEVMd wallet show my-wallet

# Create keypair
./lunarEVMd keys add my-key
./lunarEVMd keys list
./lunarEVMd keys show my-key
```

### Tokens (Max 5000 per mint)

```bash
# Create and mint tokens
./lunarEVMd token create "MyToken" MYTOKEN
./lunarEVMd token mint MYTOKEN 5000 lunar1address
./lunarEVMd token list
./lunarEVMd token info MYTOKEN
```

### NFTs

```bash
# Create and manage NFTs
./lunarEVMd nft create "My NFT" NFT "https://uri.json"
./lunarEVMd nft list
./lunarEVMd nft show nft_xxxxx
```

### Transactions & Accounts

```bash
# Account operations
./lunarEVMd account create
./lunarEVMd balance lunar1address
./lunarEVMd transaction send lunar1to 100
./lunarEVMd airdrop lunar1address 1000
```

---

## 🌍 Network Details

| Setting | Value |
|---------|-------|
| **Network Name** | LunarEVM |
| **Chain ID** | 7372 |
| **Symbol** | LUNAR |
| **Decimals** | 18 |
| **MetaMask RPC** | http://localhost:8545 |
| **Phantom RPC** | http://localhost:8899 |
| **UI Connector** | http://localhost:3000 |

---

## 📖 Documentation

Start with these in order:

1. **Quick Start** - `lunarEVM/START_HERE.md`
   ```bash
   cat lunarEVM/START_HERE.md
   ```

2. **All Commands** - `lunarEVM/COMMANDS.md`
   ```bash
   cat lunarEVM/COMMANDS.md
   ```

3. **Full Overview** - `lunarEVM/README.md`
   ```bash
   cat lunarEVM/README.md
   ```

---

## 🎯 Complete Workflow

### Terminal: Use Real CLI Commands

```bash
cd /workspaces/Mezilo/lunarEVM

# Initialize blockchain (one-time)
./lunarEVMd init

# Create wallet
./lunarEVMd wallet create alice

# Create token
./lunarEVMd token create "MyToken" MYTOKEN

# Mint tokens (max 5000 per transaction)
./lunarEVMd token mint MYTOKEN 5000 lunar1recipient

# Create NFT
./lunarEVMd nft create "Digital Art" ART "https://example.com/metadata.json"

# Check status
./lunarEVMd status

# List all created items
./lunarEVMd wallet list
./lunarEVMd token list
./lunarEVMd nft list
```

All data is stored persistently in `~/.lunarEVM/`

---

## 💰 Key Features

### ✅ Real Implementation (Now Available)
- **Real Wallet Creation** - Create wallets with persistent storage
- **Real Token Creation** - Create custom tokens with minting (max 5000 per tx)
- **Real NFT Support** - Create and manage NFTs
- **Real Accounts** - Create accounts with balances
- **Real Transactions** - Send transactions between accounts
- **Persistent State** - All data stored in `~/.lunarEVM/`
- **Command Init** - Initialize blockchain with `init` command
- **Status Reporting** - Real network status with `status` command

### 🔄 Proof of Stake (PoS)
- Validators can be created
- Staking support
- Delegation operations

### 📚 Proof of History (PoH)
- Solana-inspired timestamping
- Sequential event history
- Cryptographic verification

### 🤝 Multi-Wallet Support (Future)
- MetaMask (EVM mode)
- Phantom (Solana mode)
- Trust Wallet
- Coinbase Wallet
- WalletConnect
- Hardware wallets (Ledger, Trezor)

---

## 🔗 RPC Endpoints

### MetaMask / EVM
```
http://localhost:8545
```

### Phantom / Solana
```
http://localhost:8899
```

### Auto-Add UI
```
http://localhost:3000
```

---

## 🛠️ Setup by Platform

### Linux / macOS

```bash
cd /workspaces/Mezilo/lunarEVM
./lunarEVMd rpc
```

### Windows (Git Bash)

```bash
cd /workspaces/Mezilo/lunarEVM
./lunarEVMd rpc
```

### Docker (Future)
```bash
docker run lunarEVM:latest
```

---

## 📱 Mobile Wallets

### Using Phone Wallet

1. Get your computer's IP:
   ```bash
   # macOS/Linux
   ifconfig | grep "inet "
   # Windows
   ipconfig
   ```

2. On phone, visit:
   ```
   http://[your-ip]:3000
   ```

3. Click "Add Network"

4. Approve in wallet

---

## 🐛 Troubleshooting

### "Command not found"
```bash
# Make sure you're in lunarEVM directory
cd /workspaces/Mezilo/lunarEVM

# Check binary exists
ls -la lunarEVMd
```

### "Port already in use"
```bash
# Kill existing process
pkill -f "lunarEVMd"

# Or use different ports
cd /workspaces/Mezilo/lunarEVM
./lunarEVMd rpc --evm-port 9545 --solana-port 9899 --http-port 5000
```

### "Can't connect to wallet"
- Make sure RPC is running (Terminal 1)
- Check http://localhost:3000 loads
- Refresh browser
- Check firewall allows ports 3000, 8545, 8899

### "Insufficient balance"
- You need LUNAR tokens to transact
- Check balance: `./lunarEVMd query bank balances <address>`

---

## 🎓 Learning Resources

### Beginner
1. Read `START_HERE.md`
2. Start RPC
3. Add network to wallet
4. Send test transaction

### Intermediate
1. Create multiple accounts
2. Send tokens between accounts
3. Check transaction history
4. View account balances

### Advanced
1. Become a validator
2. Stake tokens
3. Create custom tokens
4. Create and manage NFTs
5. Build DApps

---

## 📚 All Commands (Quick Reference)

```bash
cd /workspaces/Mezilo/lunarEVM

# Blockchain
./lunarEVMd rpc              # Start RPC servers
./lunarEVMd start            # Start node
./lunarEVMd init             # Initialize node

# Keys
./lunarEVMd keys add         # Create new key
./lunarEVMd keys list        # List all keys
./lunarEVMd keys show        # Show key details

# Query
./lunarEVMd query bank balances              # Check balance
./lunarEVMd query bank total                 # Total supply
./lunarEVMd query staking validators         # List validators
./lunarEVMd query staking delegations        # View delegations

# Transactions
./lunarEVMd tx bank send                     # Send tokens
./lunarEVMd tx staking create-validator      # Become validator
./lunarEVMd tx staking delegate              # Delegate tokens
./lunarEVMd tx distribution withdraw-rewards # Claim rewards

# Configuration
./lunarEVMd metamask-config              # MetaMask setup
./lunarEVMd phantom-config               # Phantom setup
```

**See `COMMANDS.md` for complete reference with examples.**

---

## 🔐 Security

⚠️ **Development Only**
- Not for production use
- RPC on localhost only
- No authentication
- Use test keys only

✅ **Best Practices**
- Save mnemonics securely
- Don't share private keys
- Use hardware wallets for mainnet
- Always verify addresses

---

## 📋 Directory Walkthrough

### `/lunarEVM/cmd/lunarEVMd/`
CLI command implementations
```bash
main.go  # Entry point for lunarEVMd command
```

### `/lunarEVM/rpc/`
RPC servers
```bash
evm_rpc.go       # MetaMask compatibility
solana_rpc.go    # Phantom compatibility
wallet_connect.go  # WalletConnect protocol
url_server.go    # Auto URL generation
server.go        # Main RPC orchestration
```

### `/lunarEVM/x/`
Blockchain modules
```bash
x/nft/    # NFT creation & management
x/token/  # Custom token support
x/poh/    # Proof of History
x/evm/    # EVM address compatibility
```

### `/lunarEVM/app/`
Application setup
```bash
app.go     # Main app configuration
config.go  # Chain parameters
encoding.go  # Encoding setup
```

---

## 🚀 Next Steps

1. **Start blockchain:**
   ```bash
   cd /workspaces/Mezilo/lunarEVM
   ./lunarEVMd rpc
   ```

2. **Open UI:**
   ```
   http://localhost:3000
   ```

3. **Add wallet**

4. **Read `START_HERE.md`**
   ```bash
   cat lunarEVM/START_HERE.md
   ```

5. **Read `COMMANDS.md` for full reference**
   ```bash
   cat lunarEVM/COMMANDS.md
   ```

---

## 💡 Pro Tips

✅ Keep RPC running in separate terminal
✅ Use dry-run to test transactions: `--dry-run`
✅ Set gas prices: `--gas-prices 1LUNAR`
✅ Save mnemonics securely
✅ Use addresses starting with `lunar1`
✅ Chain ID for EVM: `7372`
✅ Chain ID for Cosmos: `lunarEVM-1`

---

## 🆘 Need Help?

1. Check `START_HERE.md` - Quick start
2. Check `COMMANDS.md` - All commands
3. Run `--help` on any command
4. Check GitHub issues

---

## 📜 License

LunarEVM is licensed under the Apache 2.0 License.

---

## 🎉 You're Ready!

Everything is set up. Just run:

```bash
cd /workspaces/Mezilo/lunarEVM && ./lunarEVMd rpc
```

Then open http://localhost:3000 🌙✨

**Happy blockchain building!**
