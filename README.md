# eth-defi-abigen
ABI - Application Binary Interface. Go developers can then use the bindings to interact with the contract from their Go application without having to deal directly with data encoding and decoding. An ABI is generated when a contract is compiled.

# ABI
## Application Binary Interface
Ethereum smart contracts have a schema that defines its functions and returns types as a JSON file. This JSON file is known as an Application Binary Interface, or ABI.

## Utility
- The ABI acts as a specification for precisely how to encode data sent to a contract and how to decode the data the contract sends back.
- The ABI is the only essential piece of information required to generate Go bindings.
- Go developers can then use the bindings to interact with the contract from their Go application without having to deal directly with data encoding and decoding.

# Abigen - go binding generator
Geth includes a source code generator called abigen that can convert Ethereum ABI definitions into easy-to-use, type-safe Go packages. With a valid Go development environment set up and the go-ethereum repository checked out correctly, abigen can be built as follows:

``` shell
  go install github.com/ethereum/go-ethereum/cmd/abigen@latest
```

## ABI file
 there are two recommend method to get ABI file of specify Contract.
 1. For exsisting Contract, go to [eterscan](https://etherscan.io/), and search contract name like Uniswap V3 Factory, then type `Crtl + F` to find `Contract ABI`.
 2. Using development framework like [`Foundry`](https://book.getfoundry.sh/), [`Hardhat`](https://hardhat.org/), [`Brownie`](https://eth-brownie.readthedocs.io/en/stable/) or online IDE [`Remix`](https://remix.ethereum.org/). More detail command for DEFI contract abigen can be show below.

# Uniswap V3
1. Clone Uniswap V3 repo
```shell
git clone git@github.com:sugarshop/uniswap-v3-foundry.git
```
2. complie contract using `Foundry` command
```shell
forge build
```
3. ABI file will be generated in out/UniswapV3Factory.sol/UniswapV3Factory.json and out/UniswapV3Pool.sol/UniswapV3Pool.json

4. update Go version and install abigen
```shell
go install github.com/ethereum/go-ethereum/cmd/abigen@latest
```

5. abigen for Factory and Pool Contract
```shell
abigen --abi abi/uniswap/UniswapV3Factory.abi --pkg factory --type Factory --out contracts/uniswap/Factory.go

abigen --abi abi/uniswap/UniswapV3Pool.abi --pkg pool --type Pool --out contracts/uniswap/Pool.go
```