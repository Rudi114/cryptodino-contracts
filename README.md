### Compile Code
cd into contract specific folder
```
cargo build --target wasm32-unknown-unknown --release
```


### Test the Code
cd into contract specific folder
```
cargo test -- --nocapture
```

### Deploying DinoToken
```
near deploy --accountId rudi114.testnet --wasmFile target/wasm32-unknown-unknown/release/dino_token.wasm --initFunction new --initArgs '{"owner_id": "rudi114.testnet", "total_supply": "10000000", "metadata": {
    "spec": "ft-1.0.0",
    "name": "dinotoken",
    "symbol": "DINO",
    "decimals": 18
}}'
```

### Deploying DinoNFT
```
near deploy --accountId rudi114.testnet --wasmFile target/wasm32-unknown-unknown/release/dino_nft.wasm --initFunction new --initArgs '{"owner_id": "rudi114.testnet", "total_supply": "10000000", "metadata": {
    "spec": "nft-1.0.0",
    "name": "dinoNFT",
    "symbol": "DINONFT",
    "decimals": 1
}}'
```

### Check Account Balance
```
near call rudi114.testnet ft_balance_of '{"account_id": "rudi114.testnet" }' --account-id rudi114.testnet
```