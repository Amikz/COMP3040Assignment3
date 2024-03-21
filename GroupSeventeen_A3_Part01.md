## Description

## Endpoints

### 1. GET /users/{userid}/wallets

This returns a list of wallets for the provided user. Provides the walletid, cryptocurrency type (e.g. Bitcoin), and amount stored for each wallet in that user's account.

**Parameters:**

>| Parameter | Type   | Description                          | Required |
>|-----------|--------|--------------------------------------|----------|
>| userid    | String | Uniquely identifies the user.        | Yes      |


**Example Usage**:
```
GET /users/user12bs/wallets
```

**Resource:**
>Returns JSON with the following fields:
>* wallets: the list of wallets
>* walletid: the ID of a wallet
>* cryptocurrency: the type of cryptocurrency stored in a wallet, e.g. BTC, ETH
>* balance: the amount of currency stored in a wallet

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

>| Parameter | Type   | Description                          | Required |
>|-----------|--------|--------------------------------------|----------|
>| userid    | String | Uniquely identifies the user.        | Yes      |
>| walletid  | String | Uniquely identifies the wallet. Obtained from endpoint 1 response. | Yes |
>| startdate | String | The starting date for the transaction period, given in MM-DD-YYYY format. Must be earlier than or the same as the end date parameter. If not included, will default to the current date. | No |
>| enddate | String | The ending date for the transaction period, given in MM-DD-YYYY format. Must be later than or the same as the start date parameter. If not included, will default to the current date. | No |

**Example Usage**:
```
GET /users/user12bs/wallets/wallet9sh/transactions?startdate=01-01-2024&enddate=01-01-2024
```
**Resource:**
> Returns JSON with the following fields:
> * startdate: the start date of the transaction period
> * enddate: the end date of the transaction period
> * transactions: the list of transactions within the given transaction period
> * type: the type of transaction, either "sent" or "received"
> * timestamp: the timestamp of when the transaction occurred
> * amount: the amount of the transaction
> * otherparty: the recipient or sender of the transaction amount

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

