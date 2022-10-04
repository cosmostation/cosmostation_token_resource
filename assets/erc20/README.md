## How to add your erc20 token info

1. Fork this repo to your own github account

2. Clone fork and create new branch

   ```shell
   git clone git@github.com:YOUR_ACCOUNT/cosmostation_token_resource.git
   cd cosmostation_token_resource
   git branch <branch_name>
   git checkout <branch_name>
   ```

3. Add the info of your token in the chain that your token needs to be displayed

   If there is no chain in the list, create a folder for the chain and add info in the folder

   Then add the name of the folder in: supports.json

   Changes will be updated within 24 hours after merged to master

   - `chainId`
     - ChainId of the chain
   - `address`
     - Token's contract_address
   - `name`
     - Name of the displayed token
   - `symbol`
     - Name of token's symbol
   - `decimals`
     - Decimal of the token
   - `logoURI`
     - Image route of the token
     - `/assets/images/${chain}` add image in the folder
     - Make sure to upload a `png`file
   - `coinGeckoId` (optional)
     - Coin gecko site's API ID <ex) https://www.coingecko.com/en/coins/cosmos-hub -> API ID: cosmos>

   ---

- ERC20 Token

  `/assets/erc20/${chain}/assets.json`

  ```json
  // example EVMOS
  [
    {
      "chainId": 9001,
      "address": "0xD4949664cD82660AaE99bEdc034a0deA8A0bd517",
      "name": "Wrapped Evmos",
      "symbol": "WEVMOS",
      "decimals": 18,
      "logoURI": "evmos/wevmos.png",
      "coinGeckoId": "evmos"
    },
    {
      "chainId": 9001,
      "address": "0x7FF4a56B32ee13D7D4D405887E0eA37d61Ed919e",
      "name": "Tether USD",
      "symbol": "USDT",
      "decimals": 6,
      "logoURI": "ethereum/usdt.png",
      "coinGeckoId": "tether"
    },
  ]
  ```

4. Commit and push to your fork

   ```shell
   git add -A
   git commit -m “Add <YOUR TOKEN NAME>”
   git push origin <branch_name>
   ```

5. From your repository, make pull requesrt (PR)
