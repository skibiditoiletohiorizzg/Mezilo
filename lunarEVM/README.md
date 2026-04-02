# LunarEVM Blockchain

LunarEVM is a blockchain built on the Cosmos SDK featuring Proof of Stake (PoS) consensus combined with Proof of History (PoH) for enhanced security and timestamping.

## Features

### 1. **Coin Specification**
- **Name**: Lunar
- **Symbol**: LUNAR
- **Decimals**: 18
- **Purpose**: Native token and staking currency

### 2. **Proof of Stake (PoS)**
Integrated with Cosmos SDK's built-in staking module:
- Validators stake "LUNAR" tokens to participate in consensus
- Rewards distributed to validators and delegators
- Slashing for misbehavior
- Up to 100 active validators
- Zero minimum commission

### 3. **Proof of History (PoH)** (Custom Implementation)
Similar to Solana's approach:
- Sequential history of all blockchain events
- Each entry cryptographically linked to the previous one using SHA256
- Provides verifiable ordering of transactions without relying solely on block timestamps
- Enables extremely efficient timestamp verification

**PoH Entry Structure:**
```go
type PoHEntry struct {
    Sequence   uint64        // Position in the PoH chain
    Hash       string        // SHA256 hash of this entry
    PrevHash   string        // Hash of the previous entry
    Timestamp  int64         // Block time
    Data       string        // Transaction or event hash
    EventType  string        // Type of event (tx, state_change, etc)
}
```

### 4. **Custom Token Creation**
Users can create their own tokens on LunarEVM:
- Create custom tokens with custom decimals
- Mint and burn tokens
- Transfer tokens between accounts
- Track token balances per user

**Token Metadata:**
```go
type TokenMetadata struct {
    Symbol      string   // Unique token symbol
    Name        string   // Token name
    Decimals    uint8    // Number of decimal places (0-18)
    TotalSupply int64    // Initial total supply
    Creator     string   // Creator's address
    Description string   // Token description
    CreatedAt   int64    // Creation timestamp
}
```

### 5. **NFT Support**
Create and manage custom NFTs on the blockchain:
- Create NFTs with metadata
- Transfer NFTs between addresses
- Track NFT ownership
- Burn NFTs
- Store external metadata URIs

**NFT Metadata:**
```go
type NFTMetadata struct {
    ID          string   // Unique NFT ID
    Name        string   // NFT name
    Symbol      string   // NFT symbol
    Description string   // NFT description
    URI         string   // Link to external metadata
    Owner       string   // Current owner address
    Creator     string   // Creator address
    CreatedAt   int64    // Creation timestamp
}
```

## Project Structure

```
lunarEVM/
├── app/
│   ├── app.go           # Main application setup and module integration
│   ├── config.go        # Chain configuration
│   └── encoding.go      # Encoding configuration (proto/amino)
├── x/
│   ├── nft/
│   │   ├── types.go     # NFT types and message definitions
│   │   ├── keeper.go    # NFT storage and logic
│   │   └── handler.go   # Message handlers (TODO)
│   ├── poh/
│   │   ├── types.go     # PoH entry types
│   │   ├── keeper.go    # PoH chain management
│   │   └── handler.go   # Event recording (TODO)
│   └── token/
│       ├── types.go     # Token types and messages
│       ├── keeper.go    # Token storage and logic
│       └── handler.go   # Message handlers (TODO)
├── cmd/lunarEVMd/
│   └── main.go          # Blockchain binary entrypoint
└── go.mod               # Module dependencies
```

## Modules

### Auth Module (Cosmos SDK)
- Account management
- Signature verification
- Transaction fee handling

### Bank Module (Cosmos SDK)
- Native token (lunar) transfers
- Balance management
- Multi-coin support for custom tokens

### Staking Module (Cosmos SDK)
- Validator management
- Delegation support
- Token bonding/unbonding

### Distribution Module (Cosmos SDK)
- Validator reward distribution
- Delegator reward distribution
- Commission management

### Slashing Module (Cosmos SDK)
- Validator misbehavior penalties
- Downtime slashing
- Double-sign slashing

### Mint Module (Cosmos SDK)
- Inflation management
- New token creation
- Block rewards

### NFT Module (Custom)
- NFT creation and management
- Transfer and burn operations

### Token Module (Custom)
- Custom token creation
- Token minting and burning
- Balance tracking

### PoH Module (Custom)
- Proof of History chain maintenance
- Event recording and verification
- Chain integrity validation

## Getting Started

### Prerequisites
- Go 1.22 or higher
- Cosmos SDK v0.50.0+
- CometBFT

### Installation

```bash
# Clone the repository
git clone https://github.com/lunarEVM/lunarEVM
cd lunarEVM

# Download dependencies
go mod download

# Build the binary
go build -o lunarEVMd ./cmd/lunarEVMd
```

### Initialize a Node

```bash
# Create a validator
./lunarEVMd init my-validator --chain-id lunarEVM-1

# Generate keys
./lunarEVMd keys add my-key

# Add genesis account
./lunarEVMd add-genesis-account my-key 1000000000stake
```

### Start the Node

```bash
./lunarEVMd start
```

## Message Types

### NFT Messages

#### CreateNFT
Create a new NFT:
```json
{
  "creator": "lunar1xxx...",
  "name": "My NFT",
  "symbol": "MNFT",
  "description": "A custom NFT",
  "uri": "https://example.com/metadata.json"
}
```

#### TransferNFT
Transfer an NFT to another address:
```json
{
  "sender": "lunar1xxx...",
  "recipient": "lunar1yyy...",
  "nft_id": "nft_123"
}
```

#### BurnNFT
Permanently burn an NFT:
```json
{
  "owner": "lunar1xxx...",
  "nft_id": "nft_123"
}
```

### Token Messages

#### CreateToken
Create a custom token:
```json
{
  "creator": "lunar1xxx...",
  "name": "My Token",
  "symbol": "MYTOKEN",
  "decimals": 6,
  "total_supply": "1000000000",
  "description": "A custom token"
}
```

#### MintToken
Mint additional tokens:
```json
{
  "creator": "lunar1xxx...",
  "symbol": "MYTOKEN",
  "amount": "1000000",
  "to": "lunar1yyy..."
}
```

#### BurnToken
Burn tokens:
```json
{
  "owner": "lunar1xxx...",
  "symbol": "MYTOKEN",
  "amount": "100000"
}
```

### PoH Messages

#### RecordPoHEvent
Record an event in the Proof of History chain:
```json
{
  "sender": "lunar1xxx...",
  "data": "tx_hash_xyz...",
  "event_type": "transaction"
}
```

## Chain Parameters

**Chain ID**: `lunarEVM-1`
**Native Denom**: `stake` (for staking)
**Coin Display**: `lunar`
**Decimals**: 18
**Max Validators**: 100
**Inflation Rate**: 7% annually
**Min Commission**: 0%

## Development Notes

### Adding New Modules
1. Create module directory under `x/`
2. Implement `types.go` with message definitions
3. Implement `keeper.go` for state management
4. Create `handler.go` for message processing
5. Register module in `app/app.go`

### Custom Queries
To add custom queries, implement:
1. Query definition in module's types
2. Query handler in module's keeper
3. gRPC gateway endpoint integration

### Testing
Run module tests:
```bash
go test ./x/nft/...
go test ./x/token/...
go test ./x/poh/...
```

## Future Enhancements

- [ ] EVM compatibility layer (Ethermint integration)
- [ ] IBC support for cross-chain communication
- [ ] Advanced NFT features (royalties, collections)
- [ ] Token liquidity pools
- [ ] Governance module for on-chain voting
- [ ] Smart contract support
- [ ] Sharding for scalability

## License

LunarEVM is licensed under the Apache 2.0 License.

## Support

For questions, issues, or contributions, please visit: https://github.com/lunarEVM/lunarEVM

---

**Build a decentralized future with LunarEVM** 🚀
