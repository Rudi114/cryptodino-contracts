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

### Deploying the contracts
cd into contract specific folder
```
near deploy --wasmFile target/wasm32-unknown-unknown/release/<contract-name-snake-case>.wasm --accountId <YOUR_ACCOUNT_HERE>
```