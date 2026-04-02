# 🌙 LunarEVM - Getting Started

Welcome to **LunarEVM**! This is your quick start guide.

---

## 🚀 Quick Start (5 minutes)

### Step 1: Start the Blockchain

```bash
cd /workspaces/Mezilo/lunarEVM
./lunarEVMd rpc
```

You'll see output like:
```
🌐 Wallet Connector UI: http://localhost:3000
📱 EVM RPC (MetaMask): http://localhost:8545
👻 Solana RPC (Phantom): http://localhost:8899
```

### Step 2: Open Wallet Connector

Open in your browser:
```
http://localhost:3000
```

You'll see a page with buttons to add LunarEVM to your wallet.

### Step 3: Choose Your Wallet

**🦊 MetaMask (Desktop)?**
- Click the blue "Add to MetaMask" button
- Approve in your MetaMask extension

**👻 Phantom (Desktop)?**
- Copy the Solana RPC URL: `http://localhost:8899`
- Go to Phantom Settings → Network → Add Custom RPC
- Paste the URL

**📱 Mobile Wallet (Trust Wallet, Phantom Mobile)?**
- Visit `http://[your-computer-ip]:3000` on your phone
- Click "Add Network"
- Approve in wallet

### Step 4: You're Done! 🎉

You can now:
- ✅ View your balance
- ✅ Send transactions
- ✅ Sign messages
- ✅ Interact with the blockchain

---

## 📚 Learn More

### All Available Commands

See every CLI command:
```bash
./lunarEVMd --help
./lunarEVMd rpc --help
./lunarEVMd tx bank send --help
```

**Full reference:** [COMMANDS.md](COMMANDS.md)

### Network Details

| Setting | Value |
|---------|-------|
| **Network Name** | LunarEVM |
| **Chain ID** | 7372 |
| **Currency** | LUNAR |
| **Decimals** | 18 |
| **MetaMask RPC** | http://localhost:8545 |
| **Phantom RPC** | http://localhost:8899 |
| **Connector UI** | http://localhost:3000 |

### Blockchain Features

- **Proof of Stake** - Validators stake LUNAR tokens
- **Proof of History** - Solana-like timestamping
- **Custom Tokens** - Create your own tokens
- **NFTs** - Create and manage NFTs
- **Staking** - Earn rewards by staking

---

## 🔧 Common Tasks

### Check Your Balance

```bash
./lunarEVMd query bank balances lunar1xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

### Send LUNAR Tokens

```bash
./lunarEVMd tx bank send \
  lunar1xxxx \
  lunar1yyyy \
  100LUNAR \
  --from my-account \
  --chain-id lunarEVM-1
```

### Create a Key

```bash
./lunarEVMd keys add my-account
```

### List All Keys

```bash
./lunarEVMd keys list
```

### Stake Tokens

```bash
./lunarEVMd tx staking create-validator \
  --amount 1000000000LUNAR \
  --pubkey $(./lunarEVMd tendermint show-validator) \
  --moniker "My Validator" \
  --from my-validator \
  --chain-id lunarEVM-1
```

---

## 🐛 Troubleshooting

### "Can't connect to wallet"
- Make sure `./lunarEVMd rpc` is running
- Check http://localhost:3000 is accessible
- Refresh your browser

### "RPC server error"
- Ports might be in use
- Kill the process: `pkill -f "lunarEVMd rpc"`
- Start again: `./lunarEVMd rpc`

### "Address not found"
- Make sure you created a key: `./lunarEVMd keys add my-account`
- Check the address: `./lunarEVMd keys show my-account --address`

### "Insufficient balance"
- You need LUNAR tokens to transact
- Check balance: `./lunarEVMd query bank balances <address>`

---

## 📖 Documentation

- **All Commands**: [COMMANDS.md](COMMANDS.md) - Complete CLI reference
- **README**: [README.md](README.md) - Project overview
- **Features**: Staking, NFTs, Custom tokens, PoH

---

## 🎯 What's Next?

1. ✅ Run `./lunarEVMd rpc`
2. ✅ Open http://localhost:3000
3. ✅ Add to your wallet
4. ✅ Start transacting!

**Questions?** Check [COMMANDS.md](COMMANDS.md) for detailed command usage.

---

**Happy blockchain building! 🌙✨**
