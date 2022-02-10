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
1. Create subaccount for contract (makes redeploying easier)
    ```bash
    near create-account dinotoken.<your_account_id>.testnet --masterAccount <your_account_id>.testnet
    ```

1. Deploy the contract
    ```bash
    near deploy --accountId dinotoken.<your_account_id>.testnet --wasmFile target/wasm32-unknown-unknown/release/dino_token.wasm --initFunction new --initArgs '{"owner_id": "dinotoken.<your_account_id>.testnet", "total_supply": "10000000", "metadata": {
        "spec": "ft-1.0.0",
        "name": "dinotoken",
        "symbol": "DINO",
        "decimals": 18
    }}'
    ```

### Deploying DinoNFT
1. Create subaccount for contract (makes redeploying easier)
    ```bash
    near create-account dinonft.<your_account_id>.testnet --masterAccount <your_account_id>.testnet
    ```
1. Deploy the contract
    ```bash
    near deploy --accountId dinonft.<your_account_id>.testnet --wasmFile target/wasm32-unknown-unknown/release/dino_nft.wasm --initFunction new --initArgs '{"owner_id": "dinonft.<your_account_id>.testnet", "metadata": {
        "spec": "nft-1.0.0",
        "name": "dinoNFT",
        "symbol": "DINONFT"
    }}'
    ```


### Redeploying

To redeploy with fresh contract state, delete the subaccount, re-create the subaccount, and redeploy.

For ex. to redeploy the NFT contract, do

```bash
near delete dinonft.<your_account_id>.testnet <your_account_id>.testnet
near create-account dinonft.<your_account_id>.testnet --masterAccount <your_account_id>.testnet
near deploy --accountId dinonft.<your_account_id>.testnet --wasmFile target/wasm32-unknown-unknown/release/dino_nft.wasm --initFunction new --initArgs '{"owner_id": "dinonft.<your_account_id>.testnet", "metadata": {
    "spec": "nft-1.0.0",
    "name": "dinoNFT",
    "symbol": "DINONFT"
}}'
```

> src for redeploy info: https://www.near-sdk.io/zero-to-hero/basics/add-functions-call#reset-the-accounts-contract-and-state

### Check Account Balance

```
near call rudi114.testnet ft_balance_of '{"account_id": "rudi114.testnet" }' --account-id rudi114.testnet
```
