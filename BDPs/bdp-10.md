---
bdp: 10
title: Tokens
author: Kayode Odeyemi
discussions-to: https://github.com/huntrecht/BDPs/issues/7
status: Draft
type: Standards Track
category: Interface
created: 2018-09-04
---
# Tokens

## Notable Security Token Offerings issued and supported by Brokers
- Consumer loans security token
- Security token backed by pool of funds
- Trade finance token backed by projects from legit/registered corporates
- Real estate security token backed by projects from legit/registered Real
    Estate companies

## Consumer loan token valuation lifecycle
- Loan STO is issued
- Members buy into it
- Distribution to borrowers occur
- Borrowers pay back with interest or default
- Repayments converted into tokens (lumens)
- Investors decide to/against reinvest return
- Investors stake rises/decline
- Token valuation rises/decline

## User Access
Permission | Description | Role
-----------|-------------|------------
                          Investor
                          User
                          Admin

## Specification
```
message FundResponse {
    string status = 1;
    string message = 2;
}

message TransferTokenParams {
    string owner = 1; // the to address
    string quantity = 2;
    string orgid = 3;
}

message TokenQueryParams {
    string txid = 1;
    string orgid = 2;
}

message RedeemTokenParams {
    string quantity = 1;
    string orgid = 2;
}

message AddTokenParams { 
    string type = 1;
    // number of units os symbol that the fund represents
    string quantity = 2; 
    string owner = 3;
    string orgid = 4;
}
```
### Methods

#### issue

Issue a new token

Returns `FundResponse`

`rpc createFund(AddTokenParams) returns (FundResponse) {}`

#### transfer

Buy a security. Perform a transfer into an investment fund.

Returns a `FundResponse`

`rpc transfer(TransferTokenParams) returns (FundResponse)`

#### list

View token details. Balance and ownership

Returns a `FundResponse`

`rpc getFund(TokenQueryParams) returns (FundResponse) {}`

#### redeem

Redeem a token

Returns a `FundResponse`

`rpc redeemFund(RedeemTokenParams) returns (FundResponse) {}`

## Copyright
Copyright and related rights waived via
[CC0](https://creativecommons.org/publicdomain/zero/1.0/).
