# Crypto3040 Wallet API

## Description

The Crypto Wallet Management API offers comprehensive insights and management tools for cryptocurrency wallets associated with a user's account. This API enables users to access detailed transaction histories within specific date ranges. It is designed to meet to the needs of cryptocurrency investors who require a detailed overview of their digital assets across different wallets.

## Endpoints


### GET /wallets/{walletid}/transactions

This provides a list of transactions for the specified wallet. The time period for the transactions can be set using the optional parameters. If no parameters are provided, the transactions for the current date will be returned.

**Parameters**:

| Parameter | Type   | Description                          | Required |
|-----------|--------|--------------------------------------|----------|
| walletid  | String | Uniquely identifies the wallet. Obtained from endpoint 1 response. | Yes |
| startdate | String | The starting date for the transaction period, given in MM-DD-YYYY format. Must be earlier than or the same as the end date parameter. If not included, will default to the current date. | No |
| enddate | String | The ending date for the transaction period, given in MM-DD-YYYY format. Must be later than or the same as the start date parameter. If not included, will default to the current date. | No |

**Example Usage**:
```
GET /wallets/wallet9sh/transactions?startdate=01-01-2024&enddate=01-01-2024
```
**Resource:**

Returns JSON with the following fields:

| Resource       | Type   | Description          |
|----------------|--------|----------------------|
| startDate | String | The start date of the transaction period, in MM-DD-YYYY format. |
| endDate | String | The end date of the transaction period, in MM-DD-YYYY format. |
| transactions | Array | The list of transactions within the given transaction period. |
| type | String | The type of transaction, either `sent` or `received`. |
| timestamp | String | The timestamp of when the transaction occurred. | 
| amount | Number | The amount of the transaction. |
| otherParty | String | The recipient or sender of the transaction amount. |

**Example Resource:**

```json
{
    "startdate": "01-01-2022",
    "enddate": "03-03-2024",
    "transactions": [
        {
            "type": "received",
            "timestamp": "1679407200",
            "amount": 102400,
            "otherparty": "Bob",
        }
    ]
}
```

