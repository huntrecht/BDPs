---
lip: 005
title: Transfer Specification
author: Kayode Odeyemi
discussions-to: https://github.com/huntrecht/LIPs/issues/5
status: Draft
type: Standards Track
category: Interface
created: 2018-09-04
---
# IMTO

## Abstract
Send money between people, home and abroad

Send money. Local and international

### Motivation

Send money. Local and international

### Use Cases / Scenarios
- End user is able to select designated country
- End user is able to select the recipient
- End user enters transfer amount
- Silent FX conversation occurs if mode is international. Please see x if you want to be FX conversion provider
- validate beneficiary. This should support query by email, phone number and
    full names
- system validates transfer limit

### Specification

The following specification is based on Protobuf 3

```
message Transfer {
    // The recipient. 
    required string to = 1;
    // The source. Card, BankAccount, Wallet
    requied string from = 2;
    // The currency symbol
    required string symbol = 3;
    // Amount to be transferred
    required int32 quantity = 4;
    // ISO x country format
    required string country = 5;
    // Transfer description
    required string desc = 6;
}

message SourceAccount {
    // The source. Card, BankAccount, Wallet
    string type = 1;
    optional Card card = 2;
    optional BankAccount bank = 3;
    optional Wallet wallet = 4;
    optional Qr = 5;
}

message Card {
    string name = 1;
    string exp = 2;
    string pan = 3;
}

message Wallet {
    string userId = 1;
    string currency = 2;
    double balance = 3;
}

// An Account in a Bank
message BankAccount {
    string accountName = 1;
    string accountNumber = 2;
    string country = 3;
    optional int32 bvn = 4;
}

message TransferResponse {
    string status = 1;
    string message = 2;
}
```

#### Methods

`transferFrom` - decode the source of funds

Returns `SourceDetails` object

`rpc transferFrom(SourceAccount) returns (SourceAccount) {}`

`transferTo` - Get the recipient

Returns `BankAccount` object

`rpc transferTo(BankAccount) returns (BankAccount) {}`

`transfer` - Perform a transfer

Returns `TransferResponse` object

`rpc transfer(Transfer) returns (TransferResponse) {}`

`getPaymentDetails` - Verify balance

Returns `Profile` object

`rpc getPaymentDetails(CreditProfile) returns (Profile) {}`

`list` - List own transfers

Returns a stream of `Transfer` object

`rpc list() returns (stream Transfer)`

### Implementation
- PaystackIMTO
- WaveIMTO

## Test Cases
Brokers provides the [brokers-specter] tool for checking compatibility with the Brokers specification.

## Copyright
Copyright and related rights waived via
[CC0](https://creativecommons.org/publicdomain/zero/1.0/).
