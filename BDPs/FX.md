---
lip: 00
title: Fx Specification
author: Kayode Odeyemi
discussions-to: https://github.com/huntrecht/LIPs/issues/2
status: Draft
type: Standards Track
category: Interface
created: 2018-09-04
---
# Fx

## Abstract

### Motivation

### Use Cases / Scenarios
- Company Issue a fund in USD, EUR, NGN, ZAR at certain price
- Investors buy into the issued fund, specifying x quantity. Investor A can buy into USD fund and Investor B can buy into EUR fund etc
Tokens owned by investors is persisted in investor own Wallet. For example, USD Wallet, EUR Wallet
- Exchange rate is set daily by the players (Bank or BDC) on the network. If it’s not set, a mean value is used based on past exchange rates
- End user A make a request to transfer USD of x qty in exchange for NGN    
- End user A must own USD in his wallet before it can be exchanged
- USD at qty x is removed from User A Wallet and transferred to USD fund of Company A
- NGN at qty x is deducted from NGN fund and transferred to User A
- Settlement occurs immediately. That is, all parties get paid

