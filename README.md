## Foundry

**Foundry is a blazing fast, portable and modular toolkit for Ethereum application development written in Rust.**

Foundry consists of:

- **Forge**: Ethereum testing framework (like Truffle, Hardhat and DappTools).
- **Cast**: Swiss army knife for interacting with EVM smart contracts, sending transactions and getting chain data.
- **Anvil**: Local Ethereum node, akin to Ganache, Hardhat Network.
- **Chisel**: Fast, utilitarian, and verbose solidity REPL.

## Documentation

https://book.getfoundry.sh/

## Usage

### Build

```shell
$ forge build
```

### Test

```shell
$ forge test
```

### Format

```shell
$ forge fmt
```

### Gas Snapshots

```shell
$ forge snapshot
```

### Anvil

```shell
$ anvil
```

### Deploy

```shell
$ forge script script/Counter.s.sol:CounterScript --rpc-url <your_rpc_url> --private-key <your_private_key>
```

### Cast

```shell
$ cast <subcommand>
```

### Help

```shell
$ forge --help
$ anvil --help
$ cast --help
```


### Usefull commands
#### Deployment SmartContract to Anvil using Script
```shell 1
$ anvil
```
- --rpc-url and --private-key get from shell 1
- use cast to convert hex to decimal
```shell 2
$ forge script ./script/DeploySimpleStorage.s.sol --rpc-url http://127.0.0.1:8545 --broadcast --private-key 0xac0974bec39a17e36ba4a6b4d238ff944bacb478cbed5efcae784d7bf4f2ff80

with .env
$ forge script ./script/DeploySimpleStorage.s.sol --rpc-url $RPC_URL --broadcast --private-key $PRIVATE_KEY

but with real money use 
$ forge script ./script/DeploySimpleStorage.s.sol --rpc-url $RPC_URL --broadcast --interactive

without keeping the key in the .env
$ cast wallet import defaultKey --interactive
> `defaultKey` keystore was saved successfully. Address: 0xf39fd6e51aad88f6f4ce6ab8827279cfffb92266
check it ...
$ cast wallet list
>defaultKey (Local)
$ forge script ./script/DeploySimpleStorage.s.sol --rpc-url $RPC_URL --account defaultKey --sender 0xf39fd6e51aad88f6f4ce6ab8827279cfffb92266 --broadcast
> contact address 0xe7f1725E7734CE288F8367e1Bb143E90bb3F0512
$ cast --to-base 0xb296a dec
$ cast send --help
$ cast send 0xe7f1725E7734CE288F8367e1Bb143E90bb3F0512 "store(uint256)" 123 --rpc-url $RPC_URL --private-key $PRIVATE_KEY
$ cast call --help
$ cast call 0xe7f1725E7734CE288F8367e1Bb143E90bb3F0512 "retrieve()"

ZKSync
$ foundryup
$ foundryup-zksync
$ forge build --zksync
$ anvil
$ anvil-zksync
```