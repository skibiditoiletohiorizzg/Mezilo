# 🌙 LunarEVM - Ultra Quick Reference

## 📍 Where to Run Everything

```bash
cd /workspaces/Mezilo/lunarEVM
./lunarEVMd <command>
```

---

## ⚡ Most Common Commands

### Start Everything
```bash
./lunarEVMd rpc                              # Start blockchain 🚀
```

### Wallets
```bash
./lunarEVMd wallet create my-wallet          # Create wallet 🔐
./lunarEVMd wallet list                      # See all wallets 📋
./lunarEVMd wallet show my-wallet            # View wallet details 👛
./lunarEVMd wallet backup my-wallet          # Backup wallet 💾
```

### Keys
```bash
./lunarEVMd keys add my-key                  # Create new key 🔑
./lunarEVMd keys list                        # List all keys 📋
./lunarEVMd keys show my-key                 # Show key details 🔑
```

### Tokens (Max 5000 per mint)
```bash
./lunarEVMd token create MyToken MYTOKEN     # Create token 💰
./lunarEVMd token mint MYTOKEN 5000 <addr>  # Mint tokens 🪙
./lunarEVMd token list                       # List tokens 📋
./lunarEVMd token balance MYTOKEN <addr>     # Check balance 💵
```

### NFTs
```bash
./lunarEVMd nft create "My NFT" MYNFT <uri>  # Create NFT 🎨
./lunarEVMd nft list                         # List NFTs 🖼️
./lunarEVMd nft transfer <id> <addr>         # Transfer NFT 🔄
./lunarEVMd nft burn <id>                    # Burn NFT 🔥
```

### Accounts & Balance
```bash
./lunarEVMd account create                   # Create account 👤
./lunarEVMd account list                     # List accounts 👥
./lunarEVMd balance <address>                # Check balance 💰
```

### Staking & Delegation
```bash
./lunarEVMd stake delegate <from> <val> <amt>   # Delegate 🤝
./lunarEVMd delegate create <del> <val> <amt>   # Create delegation 🤝
./lunarEVMd validator create <name> <comm>      # Create validator ✅
./lunarEVMd validator list                      # List validators ✅
./lunarEVMd validate                            # Show all validators ✅
```

### Transactions
```bash
./lunarEVMd transaction send <from> <to> <amt>  # Send tx 💸
./lunarEVMd transaction status <hash>           # Check tx 📊
./lunarEVMd airdrop <address> <amount>          # Airdrop 🎁
```

### Network Info
```bash
./lunarEVMd status                           # Network status 📊
./lunarEVMd supply                           # Token supply 📊
./lunarEVMd inflation                        # Inflation info 📈
./lunarEVMd version                          # Version info 📦
./lunarEVMd ping                             # Ping network 🏓
```

---

## 🎯 Popular Workflows

### Workflow 1: Create & Mint Token
```bash
./lunarEVMd token create "My Token" MYTOKEN
./lunarEVMd token mint MYTOKEN 5000 lunar1address    # Max 5000
./lunarEVMd token mint MYTOKEN 3000 lunar1another    # 2nd batch
./lunarEVMd token list
```

### Workflow 2: Create NFT
```bash
./lunarEVMd nft create "My NFT" MYNFT "https://example.com/meta.json"
./lunarEVMd nft list
./lunarEVMd nft show nft_001
./lunarEVMd nft transfer nft_001 lunar1newowner
```

### Workflow 3: Become Validator
```bash
./lunarEVMd validator create my-validator 5
./lunarEVMd validator list
./lunarEVMd validate      # Show all with you in list
```

### Workflow 4: Delegate Stake
```bash
./lunarEVMd stake delegate lunar1me lunar1validator 1000LUNAR
./lunarEVMd delegate list
./lunarEVMd account rewards lunar1me
```

---

## 📊 All Command Categories (90+ Commands)

| Category | Count |
|----------|-------|
| Wallets | 7 |
| Keys | 10 |
| Tokens | 10 |
| NFTs | 10 |
| Accounts | 8 |
| Staking | 8 |
| Delegation | 5 |
| Validators | 8 |
| Transactions | 6 |
| Blocks | 5 |
| Network Info | 10 |
| Configuration | 4 |
| Programs | 4 |
| Misc | 15+ |

---

## ⚠️ Important Limits

- **Token Mint:** Max 5000 per transaction
- **Chain ID (Cosmos):** `lunarEVM-1`
- **Chain ID (EVM):** `7372`
- **Decimals:** 18
- **Symbol:** LUNAR

---

## 🚀 Full Command Reference

For **complete details** on all 90+ commands:
```bash
cat CLI_REFERENCE.md
```

For **quick start**:
```bash
cat START_HERE.md
```

---

## 💡 Tips

1. **Always:** `cd /workspaces/Mezilo/lunarEVM` first
2. **Token mint:** Limited to 5000 per transaction (use multiple txs)
3. **Need help:** `./lunarEVMd --help`
4. **Chain ID:** Use `lunarEVM-1` for Cosmos, `7372` for EVM/MetaMask
5. **Save backups:** `./lunarEVMd wallet backup <name>`

---

**🌙 Happy transacting! All 90+ commands ready to use! 🌙**
