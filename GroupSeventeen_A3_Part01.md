## Description

## Endpoints

### 1. GET /users/{userid}/wallets

This returns a list of wallets for the provided user. Provides the walletid, cryptocurrency type (e.g. Bitcoin), and amount stored for each wallet in that user's account.

**Parameters:**

| Parameter | Type   | Description                          | Required |
|-----------|--------|--------------------------------------|----------|
| userID    | String | Uniquely identifies the user.        | Yes      |


**Example Usage**:
```
GET /users/user12bs/wallets
```

**Resource:**

Returns JSON with the following fields:

| Resource       | Type   | Description          |
|----------------|--------|----------------------|
| wallets        | Array  | The list of wallets. |
| walletID       | String | The ID of a wallet.  |
| cryptocurrency | String | The type of cryptocurrency stored in a wallet, e.g. BTC, ETH. |
| balance        | Number | The amount of currency stored in a wallet. |

**Example Resource:**
```json
{
  "wallets": [
    {
      "walletId": "wallet21adsf123",
      "balance": 1024.50,
      "currency": "BTC"
    },
    {
      "walletId": "wallet12412nu456",
      "balance": 5500.00,
      "currency": "ETH"
    }
  ]
}
```

### 2. GET /users/{userid}/wallets/{walletid}/transactions

This provides a list of transactions for the provided user from the specified wallet. The time period for the transactions can be set using the optional parameters. If no parameters are provided, the transactions for the current date will be returned.

**Parameters**:

| Parameter | Type   | Description                          | Required |
|-----------|--------|--------------------------------------|----------|
| userID    | String | Uniquely identifies the user.        | Yes      |
| walletID  | String | Uniquely identifies the wallet. Obtained from endpoint 1 response. | Yes |
| startDate | String | The starting date for the transaction period, given in MM-DD-YYYY format. Must be earlier than or the same as the end date parameter. If not included, will default to the current date. | No |
| endDate | String | The ending date for the transaction period, given in MM-DD-YYYY format. Must be later than or the same as the start date parameter. If not included, will default to the current date. | No |

**Example Usage**:
```
GET /users/user12bs/wallets/wallet9sh/transactions?startdate=01-01-2024&enddate=01-01-2024
```
**Resource:**

Returns JSON with the following fields:

| Resource       | Type   | Description          |
|----------------|--------|----------------------|
| startDate | String | The start date of the transaction period, in MM-DD-YYYY format. |
| endDate | String | The end date of the transaction period, in MM-DD-YYYY format. |
| transactions | Array | The list of transactions within the given transaction period. |
| type | String | The type of transaction, either "sent" or "received". |
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

