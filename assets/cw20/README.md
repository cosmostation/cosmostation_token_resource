## How to add your cw20 token info

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

   - `chain`
     - Chain with the token
   - `contract_address`
     - Token's contract_address
   - `symbol`
     - Name of token's symbol
   - `decimal`
     - Decimal of the token
   - `image`
     - Image route of the token
     - `/coin_image/${chain}/cw20` add image in the folder
     - Make sure to upload a `png` file

   ---

- Cw20 Token

  `/assets/cw20/${chain}/assets.json`

  ```json
  // example JUNO
  [
    {
      "chain": "juno",
      "contract_address": "juno1pqht3pkhr5fpyre2tw3ltrzc0kvxknnsgt04thym9l7n2rmxgw0sgefues",
      "symbol": "DAO",
      "decimal": 6,
      "image": "https://bafkreiefe4icv32rsn5l43p776d5rd4yk6expmiita5jt5tqqugc65mbua.ipfs.cf-ipfs.com/"
    },
    {
      "chain": "juno",
      "contract_address": "juno168ctmpyppk90d34p3jjy658zf5a5l3w8wk35wht6ccqj4mr0yv8s4j5awr",
      "symbol": "NETA",
      "decimal": 6,
      "image": "https://raw.githubusercontent.com/cosmostation/cosmostation_token_resource/master/coin_image/juno/cw20/neta.png",
      "coinGeckoId": "neta"
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
