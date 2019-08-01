---
lip: 001
title: Resilient Service Protocol Specification
author: Kayode Odeyemi
discussions-to: https://github.com/huntrecht/LIPs/issues/1
status: Draft
type: Standards Track
category: Core
created: 2018-09-04
---
# RSP (Resilient Service Protocol)

## Abstract
The Resilient Service Protocol is an RL System. It is based on the notion that multiple service providers or components in a distributed system should be deterministic and fault tolerant. It is for this purpose we present the Resilient Service Protocol.

## Motivation and Requirements
In a digital economomy, the internet of value is essential. Large corporates
have complex operations and processes that require solving using scientific
methodologies. The state of affairs calls for the development of distributed solutions that can efficiently automate operations and processes. In particular, such systems should satisfy the following requirements: 

- Fault Tolerance: Digital systems should recover from task failures and
    elastically scale without end-users noticing
- Efficiency
- Interoperability
- High throughput and Low Latency: Ability to horizontally scale the system to support  a high throughput of fine-grained tasks while maintaining fault-tolerance and low latency task scheduling 

## Proposal
A Protocol that learns a path and rewards accordingly. Simulate, Serve, learn, store

Simultae - Learn a path

Distributed computing - Merge-sort at a large scale


### Architecture
The RSP Architecture is based on 2PC, Paxos, PBFT and other SMR protocols.

#### Protocol Coordinator
This is the control plane. It stores and monitors which implementation returns first and terminates the rest. This is a stateless design. It simplifies support for fault tolerance, that is, on failure, components simply restarts.

#### Persistence

#### Distributed Scheduler

Every request is automatically registered and distributed to every worker in the cluster.

#### RL
Our use of RL is x based on the need for agents to learn about service provider
environments in return, earns rewards and continue to utilize the service of the
service provider with the highest rewards.

Periodically, the agents are used to simulate the environment of service providers to generate tragetories. Then, uses these tragetories to improve the policy. To know the effective service providers, the agent uses the tragetories to improve the policy. That is, to update the policy in the direction of the gradient that maximizes the reward.

#### Predictive Models
The policies are updated using predictive models. We train Stochastic Gradient
Descent models on a distributed scheduler.  The models are weighted and
synchronized via parameter server.

#### Efficiency
The RSP system at it's core is designed to be efficient by minimizing latency
and maximizing the number of decisions per second.

### Multiprocessing and Parallel Computing Choices
Ray vs Scoop vs Pathos
