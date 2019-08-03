# Blockchain

## Abstract
This proposal details the flow Specification, intercommunication and exchange of data on the Blockchain network

### Motivation
All communication between client apps and the business network should be handled on a distributed ledger.

### Use Cases / Scenarios
- A request (lending, forex, loan) and client apps posts (CRUD action) to the chaincode service (smart contract).
- All smart contracts emit events over websocket to the blockchain business network.
- All requests (lending, forex, loan) and client apps subscribe to business network events over websocket to receive messages from smart contract.

### API & Integration
![Brokers client-server communication](/images/brokers-comm-arch.png)

From the diagram, a lending request sends a POST request populated with the Stake model to the REST Server running on the business network. When a Stake request is received, the LendingContract acts on it and executes. The LendingContract emits events to the business network which the lending client app subscribes to.

All client apps interact with smart contracts on the Blockchain by subscribing to messages over websocket connection. The REST server on the business network provide a websocket server which client apps can connect to.

### Specification
```
```
