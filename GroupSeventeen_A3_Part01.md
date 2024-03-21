## Description

## Endpoints

### GET /users/{userid}/wallets

This returns a list of wallets for the provided user. Provides the walletid, cryptocurrency type (e.g. Bitcoin), and amount stored for each wallet in that user's account.

### GET /users/{userid}/wallets/{walletid}/transactions?startdate=01-01-2024&enddate=01-01-2024

This provides a list of transactions for the provided user from the specified wallet. The time period for the transactions can be set using the optional parameters. If no parameters are provided, the transactions for the current date will be returned.

Parameters:
* startdate: The starting date for the transaction period, given as a string in MM-DD-YYYY format. Must be earlier than or the same as the end date parameter. If not included, will default to the current date.
* enddate: The ending date for the transaction period, given as a string in MM-DD-YYYY format. Must be later than or the same as the start date parameter. If not included, will default to the current date.

## Resources

### GET /users/{userid}/wallets

Returns JSON with the following fields:
* wallets: the list of wallets
* walletid: the ID of a wallet
* cryptocurrency: the type of cryptocurrency stored in a wallet, e.g. BTC, ETH
* amount: the amount of currency stored in a wallet

'{
    "wallets": [
        {
            "walletid": "",
            "crypocurrency": "",
            "amount": 0
        }
    ]
}'

### GET /users/{userid}/wallets/{walletid}/transactions

Returns JSON with the following fields:
* startdate: the start date of the transaction period
* enddate: the end date of the transaction period
* transactions: the list of transactions within the given transaction period
* type: the type of transaction, either "sent" or "received"
* timestamp: the timestamp of when the transaction occurred
* amount: the amount of the transaction
* recipient: the recipient of the transaction amount, only provided if the transaction type is "sent"
* sender: the sender of the transaction amount, only provided if the transaction type is "received"

'{
    "startdate": "",
    "enddate": "",
    "transactions": [
        {
            "type": "",
            "timestamp": "",
            "amount": 0,
            "recipient": "",
            "sender": ""
        }
    ]
}'

## Examples