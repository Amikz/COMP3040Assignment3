# Crypto Wallet API

## API Description

The Crypto Wallet API provides a comprehensive interface for interacting with and managing a user's cryptocurrency wallet. This API allows for real-time access to wallet balance, transaction history, and facilitates initiating and receiving cryptocurrency transactions. Designed for easy integration into financial apps or personal cryptocurrency management tools, this API aims to streamline the process of digital asset management.

## List of Endpoints

The Crypto Wallet API includes the following key endpoints:

### GET /wallets

Returns a list of all wallets associated with the user's account.

### GET /wallets/walletId

Retrieves detailed information for a specific wallet by its unique identifier.

### GET /wallets/dateRange

Fetches a list of transactions filtered by dateRange.

### GET /wallets/currency

Fetches a list of transactions filtered by currency (e.g., BTC, ETH).

## Type of Parameters

The API supports the following parameters for querying and filtering data:

| Parameter   | Type     | Description                                  | Required? |
|-------------|----------|----------------------------------------------|-----------|
| walletId    | String   | The unique identifier of the wallet.         | Yes       |
| current_balance| double | The current balance for the current wallet. | Yes       |
| currency    | String   | The cryptocurrency symbol (e.g., BTC, ETH).  | No        |
| dateRange   | String   | The range of dates for transaction history.  | No        |
| transactionType | String | Type of transaction (`sent`, `received`). | No        |

## Resource Description

Data returned by the Crypto Wallet API is in JSON format. Key resources include:

### Wallet

Represents a user's cryptocurrency wallet. Available fields:

- `walletId` - A unique identifier for the wallet.
- `currency` - The primary cryptocurrency of the wallet.
- `current_balance` - The current balance of the wallet.

```json
{
  "walletId": "String",
  "currency": "String",
  "current_balance": "Decimal"
}
```

### Transaction

Details a transaction associated with a wallet. Fields include:

- `transactionId` - The unique identifier of the transaction.
- `type` - The type of transaction (e.g., `send`, `receive`).
- `amount` - The amount of cryptocurrency transacted.
- `currency` - The cryptocurrency symbol.
- `timestamp` - The datetime the transaction occurred.

```json
{
  "transactionId": "String",
  "type": "String",
  "amount": "Decimal",
  "currency": "String",
  "timestamp": "DateTime"
}
```

## Sample Request with Sample Response

### Request: Wallet Details

[www.cryptowalletapi.com/wallets/12345]()

### Response
```json
{
  "walletId": "12345",
  "currency": "BTC",
  "current_balance": "0.5"
}
```

### Request: Transaction History

[www.cryptowalletapi.com/wallets/transactions?walletId=12345&currency=BTC]()

### Response
```json
[
  {
    "transactionId": "tx789",
    "type": "send",
    "amount": "0.1",
    "currency": "BTC",
    "timestamp": "2024-03-20T12:34:56Z"
  },
  {
    "transactionId": "tx790",
    "type": "receive",
    "amount": "0.2",
    "currency": "BTC",
    "timestamp": "2024-03-21T14:30:00Z"
  }
]
```
