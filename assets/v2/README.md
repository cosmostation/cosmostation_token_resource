## How to add your token info
‼️ Please be noted that tokens of Testnets and unverified networks may not be merged to master.

1. Fork this repo to your own github account

2. Clone fork and create new branch

   ```shell
   git clone git@github.com:YOUR_ACCOUNT/cosmostation_token_resource.git
   cd cosmostation_token_resource
   git branch <branch_name>
   git checkout <branch_name>
   ```

3. Add the info of your token in the chain that your token needs to be displayed

   - Common info to fill

     - `denom`
       - token's denom
     - `type`
       - `staking` refers that the token is the native staking token of a chain.
       - `native` refers that the token is a native token issued on a chain, but not the staking token.
       - `ibc` refers that the token was ibc transferred.
       - `pool` refers that the token represents a pool token.
       - `bridge` refers that the token is a bridge token.
       - `cw20` refers that the token is a cw20 token.
       - `erc20` refers thatthe token is an erc20 token.
     - `base_denom`
       - Original denom of the token
     - `base_type`
       - Original type of the token. [ staking, native, pool, ibc, bridge, cw20, erc20 ]
     - `dp_denom`
       - The displayed name of the token in the list.
     - `origin_chain`
       - The origin chain where this token was issued.
     - `decimal`
       - Token's decimal
     - `image` (optional)
       - Image route of the token
       - Add image in `/assets/images` folder
         - In case it is a `staking` token, `/assets/images/common` add image in the folder
         - In case it is included in a specific chain, add image in the chain folder [ native, pool, cw20, erc20 ]
         - Make sure to upload a `png` file
     - `coinGeckoId` (optional)
       - Coin gecko site's API ID <ex) https://www.coingecko.com/en/coins/cosmos-hub -> API ID: cosmos>
     - `price_denom` (optional)
       - Denom for price
   - If the type is staking, provide the info below:

     - `description`
       - A brief summary of the token
   - If the type is ibc, provide the info below:

     - `channel` (optional)
     - `port` (optional)
       - Add the token's channel and port

     - `counter_party` (optional)
       - `channel`
       - `port`
         - Add counter party's channel and port

       - `denom`
         - Token's denom before ibc transfer


     - `path` (optional)
       - If the token was transferred via ibc, bridge or other path, provide full details of where it was transferred from.

   - If the type is bridge, provide the info below:

     - `path` (optional)
       - If the token was transferred via ibc, bridge or other path, provide full details of where it was transferred from.
     - `contract` (optional)
       - If the token was transferred via contract, provide the contract address.

   ---

- Native Token

  `/assets/v2/${chain}/assets.json`

  ```json
  // example OSMOSIS
  [
    {
      "denom": "uosmo",
      "type": "staking",
      "base_denom": "uosmo",
      "base_type": "staking",
      "dp_denom": "OSMO",
      "origin_chain": "osmosis",
      "decimal": 6,
      "description": "Osmosis Staking Coin",
      "image": "common/osmo.png",
      "coinGeckoId": "osmosis",
    },
    {
      "denom": "uion",
      "type": "native",
      "base_denom": "uion",
      "base_type": "native",
      "dp_denom": "ION",
      "origin_chain": "osmosis",
      "decimal": 6,
      "description": "Native Coin",
      "image": "osmosis/ion.png",
      "coinGeckoId": "ion",
    },
    // example KUJIRA
    {
      "denom": "factory/kujira1qk00h5atutpsv900x202pxx42npjr9thg58dnqpa72f2p7m2luase444a7/uusk",
      "type": "native",
      "base_denom": "factory/kujira1qk00h5atutpsv900x202pxx42npjr9thg58dnqpa72f2p7m2luase444a7/uusk",
      "base_type": "native",
      "dp_denom": "USK",
      "origin_chain": "kujira",
      "decimal": 6,
      "description": "USK Stable Asset",
      "image": "kujira/usk.png",
      "coinGeckoId": "usk",
      "price_denom": "uusk"
    },
  ]
  ```

- IBC Token

  ```json
  [
    // example COSMOS
    {
      "denom": "ibc/14F9BC3E44B8A9C1BE1FB08980FAB87034C9905EF17CF2F5008FC085218811CC",
      "type": "ibc",
      "base_denom": "uosmo",
      "base_type": "staking",
      "dp_denom": "OSMO",
      "origin_chain": "osmosis",
      "decimal": 6,
      "path": "osmosis>cosmos",
      "channel": "channel-141",
      "port": "transfer",
      "counter_party": {
          "channel": "channel-0",
          "port": "transfer",
          "denom": "uosmo"
      },
      "image": "common/osmo.png", // Set image route for base_denom
      "coinGeckoId": "osmosis"
    },
    // example IRIS
    {
      "denom": "ibc/E244B968EE0D1EC047E7516F6ABECE7B68E9FD93B4BD8D08D13642247416BB17",
      "type": "ibc",
      "base_denom": "weth",
      "base_type": "erc20",
      "dp_denom": "WETH",
      "origin_chain": "ethereum",
      "decimal": 18,
      "path": "ethereum>gravity-bridge>iris",
      "channel": "channel-29",
      "port": "transfer",
      "counter_party": {
          "channel": "channel-47",
          "port": "transfer",
          "denom": "gravity0xC02aaA39b223FE8D0A0e5C4F27eAD9083C756Cc2"
      },
      "image": "ethereum/weth.png", // Set image route for base_denom
      "coinGeckoId": "weth",
      "contract": "0xC02aaA39b223FE8D0A0e5C4F27eAD9083C756Cc2"
    }
  ]
  ```

- Bridge Token

  ```json
  [
    // example GRAVITY-BRIDGE
    {
      "denom": "gravity0x2260fac5e5542a773aa44fbcfedf7c193bc2c599",
      "type": "bridge",
      "base_denom": "wbtc",
      "base_type": "erc20",
      "dp_denom": "WBTC",
      "origin_chain": "ethereum",
      "decimal": 8,
      "path": "ethereum>gravity-bridge",
      "image": "ethereum/wbtc.png",
      "coinGeckoId": "wrapped-bitcoin",
      "contract": "0x2260fac5e5542a773aa44fbcfedf7c193bc2c599"
    },
    // example IRIS
    {
      "denom": "htltbcbusd",
      "type": "bridge",
      "base_denom": "busd",
      "base_type": "bep2",
      "dp_denom": "BUSD",
      "origin_chain": "bnb-beacon-chain",
      "decimal": 8,
      "path": "bnb-beacon-chain>iris",
      "image": "bnb-beacon-chain/busd.png",
      "coinGeckoId": "binance-usd"
    },
  ]
  ```

- Pool Token

  ```json
  // example COSMOS
  [
    {
      "denom": "poolDFB8434D5A80B4EAFA94B6878BD5B85265AC6C5D37204AB899B1C3C52543DA7E",
      "type": "pool",
      "base_denom": "gdex-1",
      "base_type": "pool",
      "dp_denom": "GDEX-1",
      "origin_chain": "cosmos",
      "decimal": 6,
      "description": "pool/1",
      "image": "cosmos/pool.png" // Add pool image in the target chain’s folder
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
