# API

Several data endpoints are used internally and by our partners. These have been created incrementally on an as-needed basis and are not intended for widespread use. This documentation has been added for convenience, but please do not rely on this API for mission-critical data. If you need additional data to use in your application, please [reach out on Discord](https://originprotocol.com/discord).

The are two separate hostnames where different endpoints are hosted. The source code can be found in the [ousd-analytics](https://github.com/OriginProtocol/ousd-analytics/blob/2b16b3af85e90ed85c6375f2a6c0b41848dd8bd8/eagleproject/eagleproject/urls.py#L51-L64) and [origin-website](https://github.com/OriginProtocol/origin-website/blob/master/views/web\_views.py#L291-L324) GitHub repositories.

Some dates are displayed as timestamps or epochs, which can be converted to human-readable dates [here](https://www.epochconverter.com/).

### OUSD/OETH Analytics <a href="#ousd-oeth-analytics" id="ousd-oeth-analytics"></a>

## Trailing yield <a href="#trailing-yield" id="trailing-yield"></a>

`GET` `https://analytics.ousd.com/api/v2/{symbol}/apr/trailing/{days}`

The annualized trailing yield for OUSD or OETH over a given number of days

Numbers greater than 365 may produce unexpected results

**Path Parameters**

| Name     | Type   | Description    |
| -------- | ------ | -------------- |
| days     | Number | Number of days |
| symbol\* | String | ousd or oeth   |

200: OKCopy

```
{
  "apr": "8.124428550334684695499731787",
  "apy": "8.43"
}
```

## Yield history <a href="#yield-history" id="yield-history"></a>

`GET` `https://analytics.ousd.com/api/v2/{symbol}/apr/history`

The recent annualized historical yield for OUSD or OETH

**Path Parameters**

| Name     | Type   | Description  |
| -------- | ------ | ------------ |
| symbol\* | String | ousd or oeth |

200: OKCopy

```
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

\
Collateral <a href="#collateral" id="collateral"></a>
-----------------------------------------------------

`GET` `https://analytics.ousd.com/api/v2/{symbol}/collateral`

A list of backing assets and their balances held by OUSD

**Path Parameters**

| Name     | Type   | Description |
| -------- | ------ | ----------- |
| symbol\* | String | ousd        |

200: OKCopy

```
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

## Strategies <a href="#strategies" id="strategies"></a>

`GET` `https://analytics.ousd.com/api/v2/{symbol}/strategies{?structured}`

A list of OUSD's yield-earning strategies and its token balances

**Path Parameters**

| Name     | Type   | Description |
| -------- | ------ | ----------- |
| symbol\* | String | ousd        |

**Query Parameters**

| Name       | Type   | Description |
| ---------- | ------ | ----------- |
| structured | String |             |

200: OK unstructured200: OK structuredCopy

```
{
  "strategies": [
    {
      "name": "Vault",
      "total": 7448.884896,
      "dai": 0,
      "usdt": 7448.884896,
      "usdc": 0,
      "ousd": 0,
      "comp": 0
    },
    {
      "name": "Compound Strategy",
      "total": 17398875.172562208,
      "dai": 7269054.303955209,
      "usdt": 870672.787103,
      "usdc": 9259148.081504,
      "ousd": null,
      "comp": 0
    },
    {
      "name": "Convex Strategy",
      "total": 986822.3425206443,
      "dai": 328940.78084064426,
      "usdt": 328940.78084,
      "usdc": 328940.78084,
      "ousd": null,
      "comp": null
    },
    {
      "name": "Aave Strategy",
      "total": 9671353.458348105,
      "dai": 5770579.280891105,
      "usdt": 3900774.177457,
      "usdc": 0,
      "ousd": null,
      "comp": null
    },
    {
      "name": "Morpho Strategy",
      "total": 300046.72524734936,
      "dai": 100009.00572028894,
      "usdt": 100030.335322,
      "usdc": 100007.091334,
      "ousd": null,
      "comp": 0.29287106042538863
    },
    {
      "name": "OUSD MetaStrategy",
      "total": 16191392.352579273,
      "dai": 2698565.3920966364,
      "usdt": 2698565.3920965,
      "usdc": 2698565.3920965,
      "ousd": 8095696.176289637,
      "comp": null
    }
  ]
}
```

## OGN circulating supply <a href="#ogn-circulating-supply" id="ogn-circulating-supply"></a>

`GET` `https://api.originprotocol.com/circulating-ogn`

The number of Origin Tokens (OGN) in circulation

200: OKCopy

```
503712464
```



## OGN total supply <a href="#ogn-total-supply" id="ogn-total-supply"></a>

`GET` `https://api.originprotocol.com/total-ogn`

The total number of Origin Tokens (OGN) in existence

200: OK OKCopy

```
1000000000
```

\
OETH total supply <a href="#ogv-total-supply" id="ogv-total-supply"></a>
------------------------------------------------------------------------

`GET` `https://api.originprotocol.com/total-oeth`

The total number of Origin Ether (OETH) tokens in existence



```
200: OK
```

## OGN protocol revenue <a href="#ogv-protocol-revenue" id="ogv-protocol-revenue"></a>

`GET` `https://api.originprotocol.com/api/v2/protocol-fees`

Protocol revenue derived from OETH and OUSD performance fees

```
200: OK
```
