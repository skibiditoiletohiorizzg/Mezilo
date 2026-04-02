# 🌙 LunarEVM CLI Commands Reference

Complete guide to all LunarEVM blockchain commands.

---

## 📋 Table of Contents

1. [Version](#version)
2. [Initialize](#initialize)
3. [Keys Management](#keys-management)
4. [Start Node](#start-node)
5. [Query](#query)
6. [Transactions](#transactions)
7. [RPC Servers](#rpc-servers)
8. [Configuration](#configuration)

---

## Version

### `lunarEVMd version`

Print the application version information.

**Usage:**
```bash
./lunarEVMd version
```

**Output:**
```
LunarEVM v1.0.0
```

**Description:**
Shows the current version of the LunarEVM blockchain daemon.

---

## Initialize

### `lunarEVMd init`

Initialize a new blockchain validator node.

**Usage:**
```bash
./lunarEVMd init <validator-name> [flags]
```

**Flags:**
```
--chain-id string         Chain ID (default: lunarEVM-1)
--home string             Home directory (default: ~/.lunarEVM)
--overwrite               Overwrite existing configuration
```

**Examples:**
```bash
# Initialize a validator named "my-validator"
./lunarEVMd init my-validator

# With custom chain ID
./lunarEVMd init my-validator --chain-id custom-chain-1

# With custom home directory
./lunarEVMd init my-validator --home /custom/path/.lunarEVM

# Overwrite existing config
./lunarEVMd init my-validator --overwrite
```

**What it does:**
- Creates node configuration directory
- Generates node ID
- Sets up genesis configuration
- Initializes blockchain state

**Output:**
Creates `.lunarEVM` directory with:
```
.lunarEVM/
├── config/
│   ├── app.toml
│   ├── client.toml
│   ├── config.toml
│   └── genesis.json
├── data/
└── keyring-test/
```

---

## Keys Management

### `lunarEVMd keys`

Manage blockchain keys and accounts.

**Usage:**
```bash
./lunarEVMd keys <subcommand> [flags]
```

**Subcommands:**

#### `lunarEVMd keys add`

Create a new key pair (account).

**Usage:**
```bash
./lunarEVMd keys add <key-name> [flags]
```

**Flags:**
```
--keyring-backend string   Keyring backend (test, file, kwallet, pass, os) (default: test)
--home string              Home directory
--dry-run                  Simulate key creation
```

**Examples:**
```bash
# Create a new key named "my-account"
./lunarEVMd keys add my-account

# Create with file backend (production)
./lunarEVMd keys add my-account --keyring-backend file

# View output without saving (dry-run)
./lunarEVMd keys add my-account --dry-run
```

**Output:**
```
- name: my-account
  type: local
  address: lunar1xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
  pubkey: lunarxxx...
  mnemonic: "word1 word2 word3 ... word12"

⚠️  SAVE YOUR MNEMONIC!
```

#### `lunarEVMd keys list`

List all available keys.

**Usage:**
```bash
./lunarEVMd keys list [flags]
```

**Examples:**
```bash
# List all keys
./lunarEVMd keys list

# List with keyring backend
./lunarEVMd keys list --keyring-backend file
```

**Output:**
```
- name: my-account
  type: local
  address: lunar1xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
  pubkey: lunarxxx...

- name: my-validator
  type: local
  address: lunar1yyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyy
  pubkey: lunaryyyy...
```

#### `lunarEVMd keys show`

Display details of a specific key.

**Usage:**
```bash
./lunarEVMd keys show <key-name> [flags]
```

**Flags:**
```
--address            Show address only
--pubkey             Show public key only
--json               Output as JSON
```

**Examples:**
```bash
# Show key details
./lunarEVMd keys show my-account

# Show only address
./lunarEVMd keys show my-account --address

# Show as JSON
./lunarEVMd keys show my-account --json
```

#### `lunarEVMd keys delete`

Delete a key from the keyring.

**Usage:**
```bash
./lunarEVMd keys delete <key-name> [flags]
```

**Examples:**
```bash
# Delete a key (will prompt for confirmation)
./lunarEVMd keys delete my-account
```

#### `lunarEVMd keys import`

Import a private key.

**Usage:**
```bash
./lunarEVMd keys import <key-name> <key-file> [flags]
```

**Examples:**
```bash
# Import from key file
./lunarEVMd keys import my-account ./my-key.txt
```

#### `lunarEVMd keys export`

Export a private key.

**Usage:**
```bash
./lunarEVMd keys export <key-name> [flags]
```

**Examples:**
```bash
# Export key (requires password confirmation)
./lunarEVMd keys export my-account
```

---

## Start Node

### `lunarEVMd start`

Start the blockchain node.

**Usage:**
```bash
./lunarEVMd start [flags]
```

**Flags:**
```
--home string              Home directory
--log_level string         Log level (debug, info, warn, error)
--trace                    Print out full stack trace on errors
--with-tendermint          Include Tendermint (default: true)
--grpc.address string      GRPC server address (default: localhost:9090)
--api.address string       API server address (default: localhost:1317)
```

**Examples:**
```bash
# Start with default configuration
./lunarEVMd start

# Start with debug logging
./lunarEVMd start --log_level debug

# Start with custom home directory
./lunarEVMd start --home /custom/path/.lunarEVM

# Start with trace enabled
./lunarEVMd start --trace
```

**Output:**
```
Starting blockchain node...
Loaded configuration from ~/.lunarEVM/config/app.toml
Tendermint listening on 26656
API server listening on 1317
GRPC server listening on 9090
***** NODE STARTED *****
```

---

## Query

### `lunarEVMd query`

Query blockchain data.

**Usage:**
```bash
./lunarEVMd query <module> <query> [flags]
```

**Flags:**
```
--node string              Node URL
--output string            Output format (text, json)
--height int64             Query at specific block height
```

---

### Bank Module Queries

#### `lunarEVMd query bank balances`

Query account balances.

**Usage:**
```bash
./lunarEVMd query bank balances <address> [flags]
```

**Examples:**
```bash
# Query balance of an account
./lunarEVMd query bank balances lunar1xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx

# Query in JSON format
./lunarEVMd query bank balances lunar1xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx --output json

# Query at specific block height
./lunarEVMd query bank balances lunar1xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx --height 1000
```

**Output:**
```
balances:
- amount: "1000000000000000000"
  denom: LUNAR
- amount: "500000000"
  denom: ulunar
pagination:
  next_key: null
  total: "0"
```

#### `lunarEVMd query bank total`

Query total supply of tokens.

**Usage:**
```bash
./lunarEVMd query bank total [flags]
```

**Examples:**
```bash
# Query total supply
./lunarEVMd query bank total

# Query in JSON format
./lunarEVMd query bank total --output json
```

---

### Staking Module Queries

#### `lunarEVMd query staking validators`

List all validators.

**Usage:**
```bash
./lunarEVMd query staking validators [flags]
```

**Examples:**
```bash
# List all validators
./lunarEVMd query staking validators

# Output as JSON
./lunarEVMd query staking validators --output json
```

#### `lunarEVMd query staking delegations`

Query delegations for an account.

**Usage:**
```bash
./lunarEVMd query staking delegations <delegator-address> [flags]
```

**Examples:**
```bash
# View delegations
./lunarEVMd query staking delegations lunar1xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

#### `lunarEVMd query staking rewards`

Query staking rewards for an account.

**Usage:**
```bash
./lunarEVMd query staking rewards <delegator-address> [flags]
```

**Examples:**
```bash
# View rewards
./lunarEVMd query staking rewards lunar1xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

---

### Distribution Module Queries

#### `lunarEVMd query distribution params`

Query distribution module parameters.

**Usage:**
```bash
./lunarEVMd query distribution params [flags]
```

**Examples:**
```bash
# Get distribution params
./lunarEVMd query distribution params --output json
```

---

### NFT Module Queries

#### `lunarEVMd query nft nfts`

Query NFT data (future implementation).

**Usage:**
```bash
./lunarEVMd query nft nfts [flags]
```

---

### Token Module Queries

#### `lunarEVMd query token tokens`

Query custom tokens (future implementation).

**Usage:**
```bash
./lunarEVMd query token tokens [flags]
```

---

## Transactions

### `lunarEVMd tx`

Send transactions to the blockchain.

**Common Flags:**
```
--from string              Account name or address to send from
--gas string               Gas limit (auto, 0, or value)
--gas-adjustment float     Gas adjustment multiplier
--gas-prices string        Gas prices in format amount denom
--chain-id string          Chain ID
--sequence int             Account sequence
--account-number int       Account number
--memo string              Transaction memo
--node string              Node URL
--dry-run                  Simulate transaction
--broadcast-mode string    Broadcast mode (sync, async, block)
```

---

### Bank Module Transactions

#### `lunarEVMd tx bank send`

Send tokens between accounts.

**Usage:**
```bash
./lunarEVMd tx bank send <from-address> <to-address> <amount> [flags]
```

**Examples:**
```bash
# Send LUNAR tokens
./lunarEVMd tx bank send lunar1xxxx lunar1yyyy 100LUNAR \
  --from my-account \
  --chain-id lunarEVM-1 \
  --gas auto \
  --gas-prices 1LUNAR

# Dry run (simulate without broadcasting)
./lunarEVMd tx bank send lunar1xxxx lunar1yyyy 100LUNAR \
  --from my-account \
  --chain-id lunarEVM-1 \
  --dry-run

# With custom memo
./lunarEVMd tx bank send lunar1xxxx lunar1yyyy 100LUNAR \
  --from my-account \
  --memo "Payment for services"
```

**Output:**
```
code: 0
codespace: ""
data: ""
events: []
gas_used: "54321"
gas_wanted: "100000"
height: "12345"
info: ""
logs:
- events:
  - attributes:
    - key: amount
      value: 100LUNAR
    - key: recipient
      value: lunar1yyyy
    - key: sender
      value: lunar1xxxx
    type: transfer
  log: ""
  msg_index: 0
raw_log: '[{"events":[...]'
timestamp: ""
tx: null
txhash: abc123...
```

---

### Staking Module Transactions

#### `lunarEVMd tx staking create-validator`

Create a new validator.

**Usage:**
```bash
./lunarEVMd tx staking create-validator [flags]
```

**Flags:**
```
--amount string            Amount to stake (required)
--pubkey string            Validator public key (required)
--moniker string           Validator name (required)
--identity string          Optional identity signature
--website string           Validator website
--security-contact string  Security contact email
--details string           Validator details
--comission-rate string    Commission rate (0-1)
--comission-max-rate string   Max commission rate (0-1)
--comission-max-change-rate string  Max commission change
--min-self-delegation string       Minimum self-delegation
```

**Examples:**
```bash
# Create validator
./lunarEVMd tx staking create-validator \
  --amount 1000000000LUNAR \
  --pubkey $(./lunarEVMd tendermint show-validator) \
  --moniker "My Validator" \
  --from my-validator \
  --chain-id lunarEVM-1
```

#### `lunarEVMd tx staking delegate`

Delegate tokens to a validator.

**Usage:**
```bash
./lunarEVMd tx staking delegate <validator-address> <amount> [flags]
```

**Examples:**
```bash
# Delegate tokens
./lunarEVMd tx staking delegate lunar1validator 500LUNAR \
  --from my-account \
  --chain-id lunarEVM-1
```

#### `lunarEVMd tx staking undelegate`

Undelegate tokens from a validator.

**Usage:**
```bash
./lunarEVMd tx staking undelegate <validator-address> <amount> [flags]
```

**Examples:**
```bash
# Undelegate tokens
./lunarEVMd tx staking undelegate lunar1validator 250LUNAR \
  --from my-account \
  --chain-id lunarEVM-1
```

#### `lunarEVMd tx staking redelegate`

Redelegate tokens to another validator.

**Usage:**
```bash
./lunarEVMd tx staking redelegate <src-validator> <dst-validator> <amount> [flags]
```

**Examples:**
```bash
# Redelegate tokens
./lunarEVMd tx staking redelegate \
  lunar1validator1 \
  lunar1validator2 \
  300LUNAR \
  --from my-account \
  --chain-id lunarEVM-1
```

---

### Distribution Module Transactions

#### `lunarEVMd tx distribution withdraw-rewards`

Withdraw staking rewards.

**Usage:**
```bash
./lunarEVMd tx distribution withdraw-rewards <validator-address> [flags]
```

**Examples:**
```bash
# Withdraw rewards
./lunarEVMd tx distribution withdraw-rewards lunar1validator \
  --from my-account \
  --chain-id lunarEVM-1

# Withdraw all rewards
./lunarEVMd tx distribution withdraw-all-rewards \
  --from my-account \
  --chain-id lunarEVM-1
```

---

### NFT Module Transactions

#### `lunarEVMd tx nft create`

Create a new NFT (future implementation).

**Usage:**
```bash
./lunarEVMd tx nft create <name> <symbol> [flags]
```

**Flags:**
```
--description string   NFT description
--uri string          Metadata URI
```

---

### Token Module Transactions

#### `lunarEVMd tx token create`

Create a custom token (future implementation).

**Usage:**
```bash
./lunarEVMd tx token create <name> <symbol> [flags]
```

**Flags:**
```
--decimals int        Number of decimals (0-18)
--supply string       Initial supply
--description string  Token description
```

---

## RPC Servers

### `lunarEVMd rpc`

Start RPC servers with auto-generated wallet connector URLs.

**Usage:**
```bash
./lunarEVMd rpc [flags]
```

**Flags:**
```
--evm-port int              EVM RPC port for MetaMask (default: 8545)
--solana-port int           Solana RPC port for Phantom (default: 8899)
--http-port int             HTTP port for wallet connector UI (default: 3000)
--chain-id int              Numeric chain ID for EVM (default: 1)
```

**Examples:**
```bash
# Start RPC servers with defaults
./lunarEVMd rpc

# Custom ports
./lunarEVMd rpc \
  --evm-port 9545 \
  --solana-port 9899 \
  --http-port 5000

# Custom chain ID
./lunarEVMd rpc --chain-id 12345
```

**Output:**
```
======================================================================
            🌙 LunarEVM - Auto RPC Connection URLs 🌙
======================================================================

📱 Open in browser to add networks automatically:
   🌐 http://localhost:3000

🦊 MetaMask (EVM):
   💻 http://localhost:8545
   📋 Copy & paste in MetaMask settings

👻 Phantom (Solana-compatible):
   💻 http://localhost:8899
   📋 Settings → Network → Custom RPC

🎯 Quick Setup:
   1. Open: http://localhost:3000
   2. Click 'Add Network' buttons
   3. Done! Start transacting

======================================================================

🦊 MetaMask Configuration:
   Network Name: LunarEVM
   RPC URL: http://localhost:8545
   Chain ID: 1
   Currency Symbol: LUNAR

👻 Phantom Wallet Configuration:
   RPC URL: http://localhost:8899
   Network: LunarEVM (Solana-compatible)

⏳ Starting RPC servers...
🌐 Wallet Connector UI: http://localhost:3000
📱 EVM RPC (MetaMask): http://localhost:8545
👻 Solana RPC (Phantom): http://localhost:8899
```

---

## Configuration

### `lunarEVMd metamask-config`

Display MetaMask configuration details.

**Usage:**
```bash
./lunarEVMd metamask-config
```

**Output:**
```
🦊 MetaMask Network Configuration:
=====================================
Network Name: LunarEVM
RPC URL: http://localhost:8545
Chain ID: 1
Currency Symbol: LUNAR
Block Explorer: (optional)

Add to MetaMask:
1. Click the network selector
2. Click 'Add Network'
3. Enter the details above
4. Save

Or paste this into MetaMask:
https://chainlist.org/ - search for LunarEVM (if added)
```

---

### `lunarEVMd phantom-config`

Display Phantom Wallet configuration details.

**Usage:**
```bash
./lunarEVMd phantom-config
```

**Output:**
```
👻 Phantom Wallet Configuration:
==================================
RPC URL: http://localhost:8899
Network Name: LunarEVM
Network Type: Solana-compatible

Add to Phantom:
1. Click Settings
2. Click 'Network'
3. Click 'Add Custom RPC'
4. Enter RPC URL: http://localhost:8899
5. Click 'Save'
```

---

## Global Flags

These flags work with all commands:

```
--help, -h              Show help for command
--version, -v           Show version
--home string           Home directory (default: ~/.lunarEVM)
--json                  Output as JSON
--output string         Output format (text, json)
```

---

## Common Workflows

### 1. Initialize a New Node

```bash
./lunarEVMd init my-validator --chain-id lunarEVM-1
./lunarEVMd keys add my-key
./lunarEVMd add-genesis-account my-key 1000000000LUNAR
```

### 2. Start the Blockchain

```bash
# Start node
./lunarEVMd start

# In another terminal, start RPC servers
./lunarEVMd rpc
```

### 3. Send a Transaction

```bash
# Check balances
./lunarEVMd query bank balances lunar1xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx

# Send transaction
./lunarEVMd tx bank send lunar1xxxx lunar1yyyy 100LUNAR \
  --from my-account \
  --chain-id lunarEVM-1 \
  --gas auto \
  --gas-prices 1LUNAR
```

### 4. Stake Tokens

```bash
# Create validator
./lunarEVMd tx staking create-validator \
  --amount 1000000000LUNAR \
  --pubkey $(./lunarEVMd tendermint show-validator) \
  --moniker "My Validator" \
  --from my-validator \
  --chain-id lunarEVM-1

# Delegate to validator
./lunarEVMd tx staking delegate lunar1validator 500LUNAR \
  --from my-account \
  --chain-id lunarEVM-1

# View rewards
./lunarEVMd query staking rewards lunar1xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx

# Withdraw rewards
./lunarEVMd tx distribution withdraw-rewards lunar1validator \
  --from my-account \
  --chain-id lunarEVM-1
```

### 5. Connect Wallets

```bash
# Start RPC servers
./lunarEVMd rpc

# Open wallet connector UI
open http://localhost:3000
# or
xdg-open http://localhost:3000  # Linux
start http://localhost:3000     # Windows
```

---

## Error Messages & Solutions

| Error | Cause | Solution |
|-------|-------|----------|
| `home directory does not exist` | Node not initialized | Run `./lunarEVMd init <name>` |
| `failed to parse private key` | Invalid key format | Re-create key with `keys add` |
| `address does not exist` | Invalid address | Check address spelling |
| `insufficient funds` | Not enough balance | Check with `query bank balances` |
| `account sequence mismatch` | Transaction already sent | Use `--sequence` flag with correct value |
| `RPC unreachable` | RPC server not running | Run `./lunarEVMd rpc` |
| `port already in use` | Port occupied | Use different port with `--evm-port` |

---

## Tips & Best Practices

✅ **Always verify addresses** before sending transactions
✅ **Save your mnemonic** in a secure location
✅ **Use dry-run flag** to test transactions first
✅ **Set gas-prices** to ensure transaction inclusion
✅ **Connect wallets** through `http://localhost:3000` UI
✅ **Check balances** before transactions
✅ **Monitor logs** with `--log_level debug`
✅ **Backup your keys** regularly

---

**For more information, visit:** https://github.com/lunarEVM/lunarEVM
