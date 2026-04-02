.PHONY: build clean test install help

## Build Variables
BINARY_NAME=lunarEVMd
BUILD_DIR=$(CURDIR)/build
LDFLAGS=-ldflags "-X github.com/lunarEVM/version.Version=1.0.0"

## Help
help:
	@echo "LunarEVM Makefile"
	@echo ""
	@echo "Available targets:"
	@grep -E '^[a-zA-Z_-]+:.*?## .*$$' $(MAKEFILE_LIST) | sort | awk 'BEGIN {FS = ":.*?## "}; {printf "  %-20s %s\n", $$1, $$2}'

## Build
build: ## Build the lunarEVMd binary
	@echo "Building $(BINARY_NAME)..."
	@mkdir -p $(BUILD_DIR)
	@go build $(LDFLAGS) -o $(BUILD_DIR)/$(BINARY_NAME) ./cmd/lunarEVMd/main.go
	@echo "✓ Binary built: $(BUILD_DIR)/$(BINARY_NAME)"

install: ## Install lunarEVMd to GOBIN
	@echo "Installing $(BINARY_NAME)..."
	@go install $(LDFLAGS) ./cmd/lunarEVMd
	@echo "✓ Installed to $$(go env GOBIN)/$(BINARY_NAME)"

clean: ## Remove built binaries and cache
	@echo "Cleaning..."
	@rm -rf $(BUILD_DIR)
	@go clean
	@echo "✓ Clean complete"

## Testing
test: ## Run all tests
	@echo "Running tests..."
	@go test -v ./...

test-nft: ## Test NFT module
	@echo "Testing NFT module..."
	@go test -v ./x/nft/...

test-token: ## Test token module
	@echo "Testing token module..."
	@go test -v ./x/token/...

test-poh: ## Test PoH module
	@echo "Testing PoH module..."
	@go test -v ./x/poh/...

## Development
fmt: ## Format code
	@echo "Formatting code..."
	@go fmt ./...

vet: ## Run go vet
	@echo "Running vet..."
	@go vet ./...

lint: ## Run linter (if installed)
	@command -v golangci-lint >/dev/null 2>&1 && golangci-lint run ./... || echo "golangci-lint not installed"

## Dependencies
deps: ## Download dependencies
	@echo "Downloading dependencies..."
	@go mod download
	@go mod verify

tidy: ## Tidy dependencies
	@echo "Tidying dependencies..."
	@go mod tidy

## Development Server
init: ## Initialize a new node
	@./$(BUILD_DIR)/$(BINARY_NAME) init test-validator --chain-id lunarEVM-1

start: build ## Start the blockchain node
	@./$(BUILD_DIR)/$(BINARY_NAME) start

## Documentation
docs: ## Generate documentation
	@echo "Documentation: See README.md and module READMEs"

## All-in-one
all: clean deps fmt vet test build ## Clean, test, and build

.PHONY: version
version: ## Show version
	@echo "LunarEVM v1.0.0"
