# Gachi Coin
The meme coin is created by Deesthortered.


## Install Solana
1. Prepare environment
   ```
   sudo apt-get update
   sudo apt-get upgrade
   sudo apt install build-essential pkg-config libssl-dev htop catimg
   ```
2. Install Rust 
   ```
   curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh -s -- -y
   . "$HOME/.cargo/env"
   rustc --version
   ```
3. Install Solana CLI
   ```
   sh -c "$(curl -sSfL https://release.anza.xyz/stable/install)"
   export PATH="$HOME/.local/share/solana/install/active_release/bin:$PATH"
   solana --version
   ```
4. Install Anchor 
   ```
   agave-install update
   cargo install --git https://github.com/coral-xyz/anchor avm --force
   avm --version
   avm install latest
   avm use latest
   anchor --version
   ```
5. Install Node.js (by NVM)
   ```
   curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/master/install.sh | bash
   --relogin
   command -v nvm
   nvm install node
   node --version
   ```
   
## Storing files in the public Internet by IPFS (https://ipfs.tech)
1. Create dedicated folder (let it be "ipfs")
   ```
   mkdir ipfs
   cd ipfs
   ``` 
2. Install Kubo (IPFS CLI tool) - https://docs.ipfs.tech/install/command-line/#install-official-binary-distributions
   ```
   wget https://dist.ipfs.tech/kubo/v0.32.1/kubo_v0.32.1_linux-amd64.tar.gz
   tar -xvzf kubo_v0.32.1_linux-amd64.tar.gz
   cd kubo
   sudo bash install.sh
   ipfs --version
   ```
3. Generating IPFS ID
   ```
   ipfs init
   ```
4. Run IPFS daemon in another terminal and **DO NOT CLOSE IT** until you send your files to IPFS
   ```
   ipfs daemon
   ```
5. Check your data
   ```
   ipfs id
   ipfs swarm peers
   ulimit -a
   ```


## Create SPL Token
For this document we will describe creation of "Gachi Coin"

1. Create dedicated folder (let it be "gachi-coin")
   ```
   mkdir gachi-coin
   cd gachi-coin
   ```
2. Run IPFS daemon in another terminal and **DO NOT CLOSE IT** until you send your files to IPFS
   ```
   ipfs daemon
   ```
3. Prepare your image (512px*512px, JPEG) for coin metadata, name it `metadata-image.jpg`. 
4. Add it to IPFS and get public link to the image
   ```
   ipfs add metadata-image.jpg
   ```
   * Result: `QmZKE7JBZtt8KQH2EMPJTcmiUp8y9RTG42Sqhp3mAek1ix`
   * Link: `https://ipfs.io/ipfs/QmZKE7JBZtt8KQH2EMPJTcmiUp8y9RTG42Sqhp3mAek1ix`
   * Check the image in the local IPFS cache: `ipfs cat QmZKE7JBZtt8KQH2EMPJTcmiUp8y9RTG42Sqhp3mAek1ix | catimg -` 
   * Ask the image in the local IPFS cache: `curl -s http://127.0.0.1:8080/ipfs/QmZKE7JBZtt8KQH2EMPJTcmiUp8y9RTG42Sqhp3mAek1ix | catimg -` 
   * Check who is familiar with the data: `ipfs routing findprovs QmZKE7JBZtt8KQH2EMPJTcmiUp8y9RTG42Sqhp3mAek1ix`
   * Force providing the data into network: `ipfs routing provide QmZKE7JBZtt8KQH2EMPJTcmiUp8y9RTG42Sqhp3mAek1ix`
5. Prepare your `metadata.json` file. It must contain "name", "symbol", "description" and "image" fields. 
   Put link to the metadata-image.png in the "image" field.
   ```
   {
     "name": "GachiCoin",
     "symbol": "♂",
     "description": "Еhe currency of true Alpha Gym Bosses, dungeon conquerors, and masters of deep dark fantasies. Flex your wallet like you flex your chest!",
     "image": "https://ipfs.io/ipfs/QmZKE7JBZtt8KQH2EMPJTcmiUp8y9RTG42Sqhp3mAek1ix"
   }
   ```
   * Result: 
   * Link: https://ipfs.io/ipfs/
6. 123
