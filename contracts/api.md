# API

Several data endpoints are used internally and by our partners. These have been created incrementally on an as-needed basis and are not intended for widespread use. This documentation has been added for convenience, but please do not rely on this API for mission-critical data. If you need additional data to use in your application, please [reach out on Discord](https://originprotocol.com/discord).

Our wrapper API can be found on the `api.originprotocol.com` endpoint. Most of the endpoints are wrapping access to our indexer [`origin-squid`](https://github.com/OriginProtocol/origin-squid). Note that our graphQl api is **not** public, you should rely on the REST wrapper api for stability.

Some dates are displayed as timestamps or epochs, which can be converted to human-readable dates [here](https://www.epochconverter.com/).

## OUSD/OETH Analytics <a href="#ousd-oeth-analytics" id="ousd-oeth-analytics"></a>

### Trailing yield <a href="#trailing-yield" id="trailing-yield"></a>

***

`GET` `https://api.originprotocol.com/api/v2/{token}/apr/trailing/{days}{?chainId}`

The annualized trailing yield for OUSD, OETH, superOETHb over a given number of days

Number of days greater than 100 may produce unexpected results

**Path Parameters**

| Name     | Type   | Description            |
| -------- | ------ | ---------------------- |
| symbol\* | String | ousd, oeth, superoethb |
| days     | Number | Number of days         |

**Query Parameters**

<table><thead><tr><th width="185">Name</th><th width="131">Type</th><th>Description</th></tr></thead><tbody><tr><td>chainId</td><td>Number</td><td>chain id, defaults to <code>1</code> mainnet</td></tr></tbody></table>

200: OK

```json
{
  "apr": "8.124428550334684695499731787",
  "apy": "8.43"
}
```

### Stats <a href="#stats" id="stats"></a>

***

`GET` `https://api.originprotocol.com/api/v2/{token}/stats/{stat}{?chainId}`

All available stats for OETH, OUSD and superOETHb

**Path Parameters**

| Name     | Type   | Description            |
| -------- | ------ | ---------------------- |
| symbol\* | String | ousd, oeth, superoethb |
| stat     | String | available Stat         |

**Query Parameters**

<table><thead><tr><th width="185">Name</th><th width="131">Type</th><th>Description</th></tr></thead><tbody><tr><td>chainId</td><td>Number</td><td>chain id, defaults to <code>1</code> mainnet</td></tr></tbody></table>

**Available stats**

| Stat                | Description               |
| ------------------- | ------------------------- |
| `totalSupply`       | total supply (default)    |
| `apr`               | average APR               |
| `apy`               | average APY               |
| `apy14`             | trailing apy 14 days      |
| `apy30`             | trailing apy 30 days      |
| `apy7`              | trailing apy 7 days       |
| `blockNumber`       | latest computed block     |
| `fees`              | fee perceived             |
| `marketCapUSD`      | market cap                |
| `amoSupply`         | AMO supply                |
| `dripperWETH`       | WETH dripper              |
| `nonRebasingSupply` | total non rebasing supply |
| `rateETH`           | ETH price                 |
| `rateUSD`           | USD price                 |
| `rebasingSupply`    | total rebasing            |
| `wrappedSupply`     | total wrapped             |
| `yield`             | total yield               |

200: OK

```json
6098790 // default value is totalSupply
```

### Ratios <a href="#yield-history" id="yield-history"></a>

***

`GET` `https://api.originprotocol.com/api/v2/{symbol}/ratios{?chainId}`

The current credits per token

**Path Parameters**

| Name     | Type   | Description            |
| -------- | ------ | ---------------------- |
| symbol\* | String | ousd, oeth, superoethb |

**Query Parameters**

<table><thead><tr><th width="185">Name</th><th width="131">Type</th><th>Description</th></tr></thead><tbody><tr><td>chainId</td><td>Number</td><td>chain id, defaults to <code>1</code> mainnet</td></tr></tbody></table>

200: OK

```json
{
  "current_credits_per_token": "0.906962953549645688293728531",
  "next_credits_per_token": "0.906962953549645688293728531"
}
```

### Yield history <a href="#yield-history" id="yield-history"></a>

***

`GET` `https://api.originprotocol.com/api/v2/{symbol}/apr/history`

The recent annualized historical yield for OUSD or OETH

**Path Parameters**

| Name     | Type   | Description  |
| -------- | ------ | ------------ |
| symbol\* | String | ousd or oeth |

200: OK

```json
{
  // 30-day apr
  "apr": "8.124428550334684695499731787",
  // 30-day apy
  "apy": "8.43",
  // daily apy for the prior 8+ days
  "daily": [
    {
      // today so far
      "apy": "2.757855899964977550381669000"
    },
    {
      // one day ago
      "apy": "5.203087867622041259311806600"
    },
    {
      // two days ago
      "apy": "5.024625361292970831224569500"
    },
    {
      // three days ago
      "apy": "56.33547497366474799228160500"
    },
    {
      // four days ago
      "apy": "3.735047272855167725188208800"
    },
    {
      // five days ago
      "apy": "3.572624475443835457212147200"
    },
    {
      // six days ago
      "apy": "4.959726075089981319735877800"
    },
    {
      // seven days ago
      "apy": "4.907690010865496625532084100"
    },
    {
      // eight days ago
      "apy": "4.643674734037820771919993600"
    }
  ]
}
```

### Collateral <a href="#collateral" id="collateral"></a>

***

`GET` `https://api.originprotocol.com/api/v2/{symbol}/collateral`

A list of backing assets and their balances held by OUSD

**Path Parameters**

| Name     | Type   | Description |
| -------- | ------ | ----------- |
| symbol\* | String | ousd        |

200: OK

```json
{
  "collateral": [
    {
      "name": "dai",
      "total": "18865713.513970309197419331"
    },
    {
      "name": "usdt",
      "total": "10604997.234377000000000000"
    },
    {
      "name": "usdc",
      "total": "15085226.289650000000000000"
    },
    {
      "name": "ousd",
      "total": "8095696.025185597"
    }
  ]
}
```

### Strategies <a href="#strategies" id="strategies"></a>

***

`GET` `https://api.originprotocol.com/api/v2/{symbol}/strategies{?structured}`

A list of OUSD's yield-earning strategies and its token balances

**Path Parameters**

| Name     | Type   | Description |
| -------- | ------ | ----------- |
| symbol\* | String | ousd        |

**Query Parameters**

<table><thead><tr><th width="220">Name</th><th width="131">Type</th><th>Description</th></tr></thead><tbody><tr><td>structured</td><td>String</td><td></td></tr></tbody></table>

200: OK structured

```json
{
  "block_time": 1725289283,
  "block_number": 20663645,
  "strategies": {
    "vault_holding": {
      "name": "OETH Vault",
      "address": "0x39254033945aa2e4809cc2977e7087bee48bd7ab",
      "icon_file": "oeth-icon.svg",
      "total": 82.639087904602,
      "tvl": 82.639087904602,
      "holdings": {
        "WETH": 82.6390879045019,
        "FRXETH": 0,
        "STETH": 8e-18,
        "RETH": 1.00114803e-10
      },
      "holdings_value": {
        "WETH": 82.6390879045019,
        "FRXETH": 0,
        "STETH": 8e-18,
        "RETH": 1.11635358e-10
      }
    },
    "frax_eth_strat": {
      "name": "FraxETH",
      "address": "0x3ff8654d633d4ea0fae24c52aec73b4a20d0d0e5",
      "icon_file": "frxeth-icon.svg",
      "total": 0,
      "tvl": 0,
      "holdings": {
        "SFRXETH": 0
      },
      "holdings_value": {
        "SFRXETH": 0
      }
    },
    "oeth_curve_amo": {
      "name": "OETH/ETH Curve AMO",
      "address": "0x1827f9ea98e0bf96550b2fc20f7233277fcd7e63",
      "icon_file": "oeth-icon.svg",
      "total": 7568.50216258337,
      "tvl": 7568.50216258337,
      "holdings": {
        "ETH": 3562.3529068203,
        "OETH": 4019.37421469013
      },
      "holdings_value": {
        "ETH": 3562.3529068203,
        "OETH": 4019.37421469013
      }
    },
    "oeth_morpho_aave_strat": {
      "name": "Morpho Aave",
      "address": "0xc1fc9e5ec3058921ea5025d703cbe31764756319",
      "icon_file": "morpho.png",
      "total": 0,
      "tvl": 0,
      "holdings": {
        "WETH": 0
      },
      "holdings_value": {
        "WETH": 0
      }
    },
    "oeth_balancer_reth_strat": {
      "name": "Balancer rETH/WETH Pool Strategy",
      "address": "0x49109629ac1deb03f2e9b2fe2ac4a623e0e7dfdc",
      "icon_file": "buffer-icon.svg",
      "total": 0,
      "tvl": 0,
      "holdings": {
        "RETH": 0,
        "WETH": 0
      },
      "holdings_value": {
        "RETH": 0,
        "WETH": 0
      }
    }
  },
  "total_value": 34759.5792065542,
  "total_value_usd": 87581369.0353948,
  "eth_price": 2519.632603,
  "total_supply": 34759.5792065542,
  "circulating_supply": 30740.2049918641,
  "protocol_owned_supply": 4019.37421469013
}
```

### OGN circulating supply <a href="#ogn-circulating-supply" id="ogn-circulating-supply"></a>

***

`GET` `https://api.originprotocol.com/circulating-ogn`

The number of Origin Tokens (OGN) in circulation

200: OK

```json
503712464
```

### OGN total supply <a href="#ogn-total-supply" id="ogn-total-supply"></a>

***

`GET` `https://api.originprotocol.com/total-ogn`

The total number of Origin Tokens (OGN) in existence

200: OK

```json
1000000000
```

### OETH total supply <a href="#ogv-total-supply" id="ogv-total-supply"></a>

***

`GET` `https://api.originprotocol.com/total-oeth`

The total number of Origin Ether (OETH) tokens in existence

200: OK

```json
34759
```

### superOETHb total supply <a href="#superoethb-total-supply" id="superoethb-total-supply"></a>

***

`GET` `https://api.originprotocol.com/total-superoethb`

The total number of Origin Dollar (OUSD) tokens in existence

200: OK

```json
831
```

### OGN protocol revenue <a href="#ogv-protocol-revenue" id="ogv-protocol-revenue"></a>

***

`GET` `https://api.originprotocol.com/api/v2/protocol-fees`

Protocol revenue derived from OETH and OUSD performance fees

200: OK

```json
{
  "revenue": {
    "now": 1736391.64,
    "oneDayAgo": 1733964.75,
    "twoDaysAgo": 1731260.21,
    "oneWeekAgo": 1721591.91,
    "twoWeeksAgo": 1701508.32,
    "thirtyDaysAgo": 1660510.44,
    "sixtyDaysAgo": 1592424.46,
    "ninetyDaysAgo": 1505980.6
  },
  "days": [
    {
      "date": 1725235200,
      "revenue": 2426.88
    },
    {
      "date": 1725148800,
      "revenue": 2704.54
    },
    {
      "date": 1725062400,
      "revenue": 1426.15
    },
    {
      "date": 1724976000,
      "revenue": 3234.23
    },
    // all fee history
  ]
}
```

