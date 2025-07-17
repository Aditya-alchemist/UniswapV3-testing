

# Uniswap V3 Swap Foundry Testing Suite

This project contains advanced Uniswap V3 swap tests using the [Foundry](https://github.com/foundry-rs/foundry) framework. The suite covers ERC20  WETH  WBTC swap scenarios, using a mainnet fork environment to simulate real protocol interactions and token economics.

## Features

- Realistic mainnet forking tests for Uniswap V3 swaps.
- Swap and route coverage: DAI/WETH, WETH/WBTC, and multi-hop DAI/WBTC.
- Support for **exact input** and **exact output** strategies.
- Detailed logs for each step and assertion.
- Modular, extendable, and easily adaptable for future DeFi protocol explorations.

## Outputs

### Swapping
<img width="1127" height="537" alt="image" src="https://github.com/user-attachments/assets/be262405-7037-45c0-ac20-1afd537fed65" />

### Factory
<img width="1232" height="494" alt="Screenshot 2025-07-17 145144" src="https://github.com/user-attachments/assets/aad5d30c-ab6a-43e5-be0e-cac3e41e8793" />



## Prerequisites

- [Foundry](https://github.com/foundry-rs/foundry) (`forge` installed, updated with `foundryup`)
- A mainnet archival node RPC URL (e.g., from [Alchemy](https://www.alchemy.com/) or [Infura](https://infura.io/))
- Git for version control and code management[1]

## Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com//.git
cd 
```

### 2. Install Dependencies

```bash
forge install
```

This will fetch all required contracts and test libraries (forge-std, openzeppelin-contracts, Uniswap v3-core, v3-periphery).

### 3. Environment Setup

Export your mainnet RPC URL as an environment variable:

```bash
export MAINNET_RPC_URL=
```

### 4. Run the Tests

```bash
forge test --fork-url $MAINNET_RPC_URL -vvv
```

## Project Structure

```
src/                # Interfaces and constants for DAI/WETH/WBTC addresses
test/
  uniswap-v3/
    solutions/      # Your filled-out tests (UniswapV3Swap.test.sol)
    exercises/      # Exercise templates if applicable
lib/                # External dependencies (forge-std, OpenZeppelin, Uniswap)
foundry.toml        # Foundry project configuration
```

## Key Files

- **src/interfaces/** – ERC20, WETH, Uniswap V3 routers and pools
- **src/Constants.sol** – Mainnet constants for DAI, WETH, WBTC, SwapRouter
- **test/uniswap-v3/solutions/UniswapV3Swap.test.sol** – Main swap test contract

## Main Test Scenarios

- **test_exactInputSingle**: Swaps a fixed amount of DAI for WETH in a single pool.
- **test_exactInput**: Multi-hop swap from DAI to WETH to WBTC.
- **test_exactOutputSingle**: Determines minimum DAI needed for an exact WETH amount.
- **test_exactOutput**: Determines minimum DAI needed for an exact WBTC amount, routing via WETH.

## Notes and Tips

- Default DAI input is `1000 * 1e18` but swap output/requirements may need adjustment based on market price and pool slippage at runtime.
- If you encounter an "insufficient balance" failure, check the DAI funded in `setUp()` and decrease the output target or increase the input amount.
- All addresses used are Ethereum mainnet canonical contracts.

## Contribution

Feel free to fork this repo, submit PRs, or file issues related to DeFi testing, Uniswap, or Foundry usage.

## License

MIT

**Happy Testing!**

