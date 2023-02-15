# Buidl the contract

cargo concordium build --out dist/module.wasm.v1 --schema-out dist/schema.bin

# Deploy the contract

concordium-client module deploy dist/module.wasm.v1 --sender <YOUR-ADDRESS> --name poap3 --grpc-port 10000 --grpc-ip node.testnet.concordium.com

# Initialize the contract

concordium-client contract init <MODULE-HASH> --sender <YOUR-ADDRESS> --energy 30000 --contract poap --grpc-port 10000 --grpc-ip node.testnet.concordium.com

# Mint Fungible Tokens

concordium-client contract update <YOUR-INDEX> --entrypoint mint --parameter-json nft-artifacts/mint-params.json --schema dist/schema.bin --sender <YOUR-ADDRESS> --energy 6000 --grpc-port 10000 --grpc-ip node.testnet.concordium.com

# View Contract State

concordium-client contract invoke <YOUR-INDEX> --entrypoint view --schema dist/schema.bin --grpc-port 10000 --grpc-ip node.testnet.concordium.com

# Check Balance

concordium-client contract invoke <YOUR-INDEX> --entrypoint balanceOf --parameter-json nft-artifacts/balance.json --schema dist/schema.bin --grpc-port 10000 --grpc-ip node.testnet.concordium.com

# Check Metadata

concordium-client contract invoke <YOUR-INDEX> --entrypoint tokenMetadata --parameter-json nft-artifacts/ids.json --schema dist/schema.bin --grpc-port 10000 --grpc-ip node.testnet.concordium.com

# Transfer

concordium-client contract update <YOUR-INDEX> --entrypoint transfer --parameter-json nft-artifacts/transfer.json --schema dist/schema.bin --sender <YOUR-ADDRESS> --energy 6000 --grpc-port 10000 --grpc-ip node.testnet.concordium.com

# Burn

concordium-client contract update <YOUR-INDEX> --entrypoint revoke --parameter-json nft-artifacts/burn2.json --schema dist/schema.bin --sender 3bzmSxeKVgHR4M7pF347WeehXcu43kypgHqhSfDMs9SvcP5zto --energy 6000 --grpc-port 10000 --grpc-ip node.testnet.concordium.com

# Event

concordium-client contract update <YOUR-INDEX> --entrypoint pause --schema dist/schema.bin --sender 3bzmSxeKVgHR4M7pF347WeehXcu43kypgHqhSfDMs9SvcP5zto --energy 6000 --grpc-port 10000 --grpc-ip node.testnet.concordium.com

concordium-client contract update <YOUR-INDEX> --entrypoint resume --schema dist/schema.bin --sender 3bzmSxeKVgHR4M7pF347WeehXcu43kypgHqhSfDMs9SvcP5zto --energy 6000 --grpc-port 10000 --grpc-ip node.testnet.concordium.com
