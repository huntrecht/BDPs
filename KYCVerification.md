# KYC Verification

## Abstract
Data is essential to KYC. Backed by a network of data for good agents, a good KYC
system should have good and complete data.

### Motivation
A developed economy needs Credit. The backbone of a good credit system is
quality KYC data.

### Use Cases / Scenarios

### Specification
The following Specification is based on Protobuf 3

Complete proto
```
message Kyc {
    User user = 1;
    string participantType = 2;
    string address = 3;
    bool verified = 4;
    string profileImage = 5;
    string identityId = 6;
    string registeredIdBook = 7;
    string fullnames = 8;
    string country = 9;
    }
```
