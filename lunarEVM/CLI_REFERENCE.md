# 🌙 LunarEVM - Complete CLI Command Reference

**All commands run from:** `/workspaces/Mezilo/lunarEVM/`

```bash
cd /workspaces/Mezilo/lunarEVM
./lunarEVMd <command> [subcommand] [options]
```

---

## 📋 Complete Command List

### RPC & Network
- `./lunarEVMd rpc` - Start RPC servers
- `./lunarEVMd status` - Network status
- `./lunarEVMd version` - Show version
- `./lunarEVMd ping` - Ping network
- `./lunarEVMd cluster version` - Cluster version
- `./lunarEVMd cluster info` - Cluster information
- `./lunarEVMd cluster nodes` - List cluster nodes

### Wallets & Keys
- `./lunarEVMd wallet create <name>` - Create new wallet
- `./lunarEVMd wallet import <name>` - Import wallet
- `./lunarEVMd wallet list` - List wallets
- `./lunarEVMd wallet show <name>` - Show wallet details
- `./lunarEVMd wallet backup <name>` - Backup wallet
- `./lunarEVMd wallet restore <file>` - Restore wallet
- `./lunarEVMd wallet export <name> [format]` - Export wallet
- `./lunarEVMd keys add <name>` - Create new key
- `./lunarEVMd keys list` - List all keys
- `./lunarEVMd keys show <name>` - Show key details
- `./lunarEVMd keys delete <name>` - Delete key
- `./lunarEVMd keys import <name>` - Import key
- `./lunarEVMd keys export <name>` - Export key
- `./lunarEVMd keys recover` - Recover from mnemonic
- `./lunarEVMd keys pair` - Generate key pair
- `./lunarEVMd keys sign <key>` - Sign message
- `./lunarEVMd keys verify` - Verify signature

### Accounts & Balances
- `./lunarEVMd account create` - Create account
- `./lunarEVMd account list` - List accounts
- `./lunarEVMd account balance <address>` - Check balance
- `./lunarEVMd account info <address>` - Account information
- `./lunarEVMd account transactions <address>` - Transaction history
- `./lunarEVMd account stake <address>` - Staking info
- `./lunarEVMd account delegate <address>` - Delegation info
- `./lunarEVMd account rewards <address>` - Rewards info
- `./lunarEVMd balance <address>` - Quick balance check
- `./lunarEVMd get-account <address>` - Get account details
- `./lunarEVMd get-balance <address>` - Get account balance
- `./lunarEVMd get-multiple-accounts <addr1> <addr2>` - Multiple accounts
- `./lunarEVMd get-account-info <address>` - Account info with full details
- `./lunarEVMd show-account <address>` - Show account metadata
- `./lunarEVMd largest-accounts` - Largest account holders
- `./lunarEVMd address generate` - Generate address
- `./lunarEVMd address validate <address>` - Validate address
- `./lunarEVMd address info <address>` - Address information
- `./lunarEVMd address verify <address>` - Verify address

### Tokens (* max 5000 per mint)
- `./lunarEVMd token create <name> <symbol>` - Create token
- `./lunarEVMd token mint <symbol> <amount> <to>` - Mint tokens (max 5000)*
- `./lunarEVMd token burn <symbol> <amount>` - Burn tokens
- `./lunarEVMd token list` - List all tokens
- `./lunarEVMd token balance <symbol> <address>` - Token balance
- `./lunarEVMd token info <symbol>` - Token information
- `./lunarEVMd token supply <symbol>` - Token supply
- `./lunarEVMd token metadata <symbol>` - Token metadata
- `./lunarEVMd token holders <symbol>` - Token holders
- `./lunarEVMd token transactions <symbol>` - Token transactions

### NFTs
- `./lunarEVMd nft create <name> <symbol> <uri>` - Create NFT
- `./lunarEVMd nft list` - List NFTs
- `./lunarEVMd nft transfer <id> <recipient>` - Transfer NFT
- `./lunarEVMd nft burn <id>` - Burn NFT
- `./lunarEVMd nft show <id>` - Show NFT details
- `./lunarEVMd nft metadata <id>` - NFT metadata
- `./lunarEVMd nft owner <id>` - NFT owner
- `./lunarEVMd nft collection <id>` - NFT collection
- `./lunarEVMd nft royalties <id>` - NFT royalties
- `./lunarEVMd nft verify <id>` - Verify NFT

### Staking
- `./lunarEVMd stake create-account <account> <withdrawer>` - Create stake account
- `./lunarEVMd stake authorize <account>` - Authorize stake account
- `./lunarEVMd stake delegate <account> <validator> <amount>` - Delegate stake
- `./lunarEVMd stake deactivate <account>` - Deactivate stake
- `./lunarEVMd stake withdraw <account> <amount>` - Withdraw stake
- `./lunarEVMd stake split <account> <amount>` - Split stake
- `./lunarEVMd stake merge <source> <destination>` - Merge stake
- `./lunarEVMd stake history <account>` - Stake history

### Validators
- `./lunarEVMd validator create <name> [commission]` - Create validator
- `./lunarEVMd validator list` - List validators
- `./lunarEVMd validator info <validator>` - Validator information
- `./lunarEVMd validator commission <validator> [rate]` - Commission
- `./lunarEVMd validator uptime <validator>` - Validator uptime
- `./lunarEVMd validator stake <validator>` - Validator stake
- `./lunarEVMd validator slashing <validator>` - Slashing info
- `./lunarEVMd validator deactivate <validator>` - Deactivate validator
- `./lunarEVMd validate` - Show validators

### Delegation
- `./lunarEVMd delegate create <delegator> <validator> <amount>` - Create delegation
- `./lunarEVMd delegate list` - List delegations
- `./lunarEVMd delegate info <delegation>` - Delegation information
- `./lunarEVMd delegate redelegate <from> <to>` - Redelegate
- `./lunarEVMd delegate undelegate <validator> <amount>` - Undelegate

### Voting
- `./lunarEVMd vote create <account>` - Create vote account
- `./lunarEVMd vote authorize <account>` - Authorize vote account
- `./lunarEVMd vote commission <account> [rate]` - Vote commission
- `./lunarEVMd vote list` - List vote accounts

### Transactions
- `./lunarEVMd transaction send <from> <to> <amount>` - Send transaction
- `./lunarEVMd transaction confirm <hash>` - Confirm transaction
- `./lunarEVMd transaction status <hash>` - Transaction status
- `./lunarEVMd transaction decode <hash>` - Decode transaction
- `./lunarEVMd transaction history <address>` - Transaction history
- `./lunarEVMd transaction fees <hash>` - Transaction fees
- `./lunarEVMd pay <address> <amount>` - Pay
- `./lunarEVMd airdrop <address> <amount>` - Airdrop

### Blocks & Slots
- `./lunarEVMd block info <height>` - Block information
- `./lunarEVMd block time` - Block time
- `./lunarEVMd block hash` - Latest block hash
- `./lunarEVMd block transactions <height>` - Block transactions
- `./lunarEVMd block latest` - Latest block
- `./lunarEVMd slots current` - Current slot
- `./lunarEVMd slots first-normal-rollover` - First normal rollover slot
- `./lunarEVMd blockhash` - Recent blockhash
- `./lunarEVMd epoch` - Epoch information
- `./lunarEVMd leader-schedule` - Leader schedule

### Programs
- `./lunarEVMd program deploy <name> <path>` - Deploy program
- `./lunarEVMd program verify <id>` - Verify program
- `./lunarEVMd program list` - List programs
- `./lunarEVMd program info <id>` - Program information
- `./lunarEVMd program-set-upgrade <program> <authority>` - Set upgrade authority
- `./lunarEVMd program-set-close <program> <authority>` - Set close authority
- `./lunarEVMd find-program-derived-address <program> <seed>` - Find PDA
- `./lunarEVMd custom program <name>` - Custom program info
- `./lunarEVMd custom invoke` - Invoke custom instruction

### Address Lookup Tables
- `./lunarEVMd address-lookup-table create` - Create lookup table
- `./lunarEVMd address-lookup-table extend <table>` - Extend lookup table
- `./lunarEVMd address-lookup-table show <table>` - Show lookup table
- `./lunarEVMd address-lookup-table close <table>` - Close lookup table
- `./lunarEVMd address-lookup-table show-usage <table>` - Show usage
- `./lunarEVMd address-lookup-table show-authority <table>` - Show authority


### Configuration
- `./lunarEVMd config set <key> <value>` - Set config
- `./lunarEVMd config get <key>` - Get config
- `./lunarEVMd config show` - Show all config
- `./lunarEVMd config reset` - Reset configuration

### Network Information
- `./lunarEVMd supply` - Token supply
- `./lunarEVMd inflation` - Inflation parameters
- `./lunarEVMd get-inflation-governor` - Inflation governor details
- `./lunarEVMd rent` - Rent calculations
- `./lunarEVMd fees estimate <tx>` - Estimate fees
- `./lunarEVMd fees burn` - Fees burned
- `./lunarEVMd fees validator-commission` - Validator commission
- `./lunarEVMd suggest-fee <address>` - Suggest transaction fee
- `./lunarEVMd largest-accounts` - Largest accounts
- `./lunarEVMd genesis-hash` - Genesis hash
- `./lunarEVMd pubkey` - Public key
- `./lunarEVMd blockhash` - Recent blockhash
- `./lunarEVMd get-chain-id` - Get network chain ID
- `./lunarEVMd get-identity` - Get network identity
- `./lunarEVMd nonce authority <account>` - Nonce authority
- `./lunarEVMd nonce new` - New nonce account
- `./lunarEVMd build-budget <address>` - Calculate transaction budget

### Network & Gossip
- `./lunarEVMd gossip peers` - Connected peers
- `./lunarEVMd gossip entrypoints` - Entry points

### Help & Info
- `./lunarEVMd --help` - Show help
- `./lunarEVMd -h` - Short help
- `./lunarEVMd version` - Show version
- `./lunarEVMd ping` - Ping network
- `./lunarEVMd status` - Network status

---

## 🎯 Common Workflows

### 1. Quick Transaction
```bash
cd /workspaces/Mezilo/lunarEVM
./lunarEVMd transaction send lunar1xxx lunar1yyy 100LUNAR
```

### 2. Create & Mint Token (Max 5000 per tx)
```bash
./lunarEVMd token create MyToken MYTOKEN
./lunarEVMd token mint MYTOKEN 5000 lunar1recipient
./lunarEVMd token mint MYTOKEN 3000 lunar1another
```

### 3. Staking
```bash
./lunarEVMd stake create-account my-stake lunar1address
./lunarEVMd stake delegate my-stake validator1 1000LUNAR
./lunarEVMd validate
```

### 4. NFT Management
```bash
./lunarEVMd nft create "MyNFT" MYNFT "https://example.com/metadata.json"
./lunarEVMd nft list
./lunarEVMd nft transfer nft_001 lunar1newowner
```

### 5. Wallet Management
```bash
./lunarEVMd wallet create my-wallet
./lunarEVMd wallet show my-wallet
./lunarEVMd wallet backup my-wallet
./lunarEVMd wallet export my-wallet json
```

### 6. Account Operations
```bash
./lunarEVMd account create
./lunarEVMd account list
./lunarEVMd balance lunar1xxxx
./lunarEVMd account transactions lunar1xxxx
```

### 7. Validator Setup
```bash
./lunarEVMd validator create my-validator 5
./lunarEVMd validator list
./lunarEVMd validate
```

### 8. Delegation
```bash
./lunarEVMd delegate create lunar1delegator lunar1validator 500LUNAR
./lunarEVMd delegate list
./lunarEVMd delegate redelegate lunar1validator1 lunar1validator2
```

---

## ⚠️ Important Limits

| Feature | Limit |
|---------|-------|
| Token Mint | 5000 per transaction |
| NFT Creation | Unlimited |
| Staking | Unlimited |
| Commission | 0-100% |

---

## 💡 Pro Tips

1. **All commands start with:** `./lunarEVMd`
2. **Run from:** `/workspaces/Mezilo/lunarEVM/`
3. **Token minting:** Max 5000 per tx - use multiple transactions for more
4. **Need help?** Add `--help` to any command
5. **Save mnemonics:** Backup your wallets using `wallet backup`
6. **Chain ID:** Use `lunarEVM-1` for Cosmos commands, `7372` for EVM

---

## 🚀 Quick Start

```bash
cd /workspaces/Mezilo/lunarEVM

# Start RPC
./lunarEVMd rpc &

# Create wallet
./lunarEVMd wallet create my-wallet

# Create token
./lunarEVMd token create "My Token" MYTOKEN

# Mint tokens (max 5000)
./lunarEVMd token mint MYTOKEN 5000 lunar1address

# View validators
./lunarEVMd validator list

# Create NFT
./lunarEVMd nft create "My NFT" MYNFT "https://example.com/metadata.json"
```

---

**All commands are now available! Happy blockchain building! 🌙✨**
