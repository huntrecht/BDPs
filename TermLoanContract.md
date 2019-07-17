---
lip: 003
title: Credit Specification
author: Kayode Odeyemi
discussions-to: https://github.com/huntrecht/LIPs/issues/3
status: Draft
type: Standards Track
category: Interface
created: 2018-09-04
---
# TermLoanContract

## Abstract
This proposal is an implementation of Term Loan on a Blockchain.

### Motivation
Our financial institutions are not transparent enough when it comes to credit financing. We believe there are genuine use case for fair credit financing of individual needs and small businesses.

### Requirements
- A credit score card. Should be provided by existing Credit Bureau. This is a
    minimum requirement for loan approval
- [A basic credit request](https://likid.huntrecht.com/apidocs/#creditrequest)
- Computation of Credit worthiness a.k.a Credit Grade + Computed interest rate
- Issue loan offer

### Verification Process
- An accepted loan offer by the loanee is made available to investors to fund.
    Investors can decide from here whether to verify borrower or not
- Annual income is verified
- Credit request is funded
- Credit request is removed from platform if rejected

### Use Cases / Scenarios
- An existing MFB wants to increase demand of its loans
- Push potential customer credit profile to financial institutions
- If the loan provider request for a ask price(margin call), A borrower must supply 15% of the ask price.
- The margin call (a portion of the loan value) shall be kept in a fund should in case the borrower defaults.

### Specification

The following specification is based on Protobuf 3

```
message CreditProfile {
    // The listed amount of the loan applied for by the borrower. If at some point in time, the credit department reduces the loan amount, then it will be reflected in this value.
    int32 loanAmt = 1; 
    
    // The total amount committed to that loan at that point in time
    int32 fundedAmt = 2; 
    
    // The total amount committed by investors for that loan at that point in time 
    int32 fundAmtInv = 3; 
    
    // The interest rate on the loan
    double intRate = 4; 
    
    // Paid instalment amount
    double instalment = 5; 
    
    // credit grade. Could be called risk rating.
    string grade = 6; 
    
    string subGrade = 7;
    
    bool homeOwnership = 8;
    
    double annualIncome = 9;
    
    // income source verification
    bool verificationStatus = 10; 
    
    int32 issuedDate = 11;
    
    // fully paid, charged off
    bool loanStatus = 12; 
    
    string paymentPlan = 13;
    
    string desc = 14;
    
    // loan purpose
    string purpose = 15; 
    
    string profile = 16;
    
    int32 dti = 17;
    
    // Delinquent/overdue activities within 2 years
    string delinq = 18;
    
    // How many months since overdue/delinquent date
    string mthsSinceLastDelinq = 19; 
    
    // The first ever loan you got.
    string earliestCrLine = 20; 
    
    // Have you requested for loan in the last 6 months excluding auto and mortgage enquiries
    
    bool inqLast6mths = 21; 
    
    string mthsSinceLastRecord = 22;
    
    // Revolving balance
    double revBal = 23; 
    
    // The amt of credit the boroower is using relative to all available revolving credit (revolving balance)
    
    double revUtil = 24; 
    
    // Num of open credit lines in the borrowers profile. That is, 
    double openAcc = 25; 
    
    // number of derogatroy public record
    string pubRec = 26; 
    
    // Total number of credit lines in the borrowers profile
    string totalAcc = 27; 
    
    // num of years in employment
    string empLength = 28; 
    
    // remaining outstanding principal for total amt funded
    string outPrncp = 29; 
    
    // remaining outstanding principal for portion of total amt funded by investors
    string outPrncpInv = 30; 
    
    // total payment received to date for total amt funded
    double totalPymnt = 31; 
    
    // total payment received received to date for portion of total amt funded by investors
    double totalPymntInv = 32; 
    
    // principal received till date
    double totalRecPrncp = 33; 
    
    // interest received to date
    double totalRecInt = 34; 
    
    // late fee received till date
    double totalRecLateFee = 35; 
    
    // post-charge off gross recovery. Charges on third parties for recoveries. inv receive a pro-rata share of the recovery amt less any fees.
    double recoveries = 36; 
    
    // post-charge off collection fee
    double collectionRecoveryFee = 37; 
    
    int32 lastPymntDate = 38; 
    
    double lastPymntAmt = 39;
    
    int32 nextPymntDate = 40;
    
    // most recent month LC, MFBs check your credit standing
    int32 lastCreditPullDate = 41; 
    
    // num of collections in 12 mths that's not for medicals
    string collections12MthsExMed = 42; 
    
    // mths since most recent worst rating
    string mthsSinceLastMajorDerog = 43; 
    
    string policyCode = 44; //
    
    string applicationType = 45;
    
    // co-borrowers annual income
    double annualIncJoint = 46; 
    
    // ratio calculated using co-borrowers total mthly payment on the total debt obligation excluding mortgages on the provided loan
    double dtiJoint = 47; 
    
    // joint income verification
    string verificationStatusJoint = 48; 
    
    // num of acc on which borrower is delinquent. This comes from the credit bureau
    string accNowDelinq = 49; 
    
    // total collection amount ever owed by the borrower
    double totCollAmt = 50; 
    
    double totCurBal = 51; // 
    
    // num of open trades (i.e revolving acc, charge acc, instalment, collection acc)
    int32 open_acc_6m = 52; 
    
    // num of instalment acc opened in 6 mths
    string open_il_6m = 53; 
    
    // num of instalment acc opened in 12m
    string open_il_12m = 54; 
    
    // num of instalment acc opened in 24m
    string open_il_24m = 55; 
    
    // mths since recent instalment acc opened
    string mths_since_rcnt_il = 56; 
    
    // total bal on instal acc
    int32 total_bal_il = 57; 
    
    // ratio of total cur bal to high credit over credit limit on all instalment account
    double il_util = 58; 
    
    // num of revolving trade opened in last 12 mths
    int32 open_rv_12m = 59; 
    
    // num of revolving trade opened in last 24 mths
    int32 open_rv_24m = 60; 
    
    // max bal owed on all revolving account
    double max_bal_bc = 61; 
    
    // bal to credit limit on all trades
    double all_util = 62; 
    
    // total revolving high credit or credit limit
    double total_rev_hi_lim = 63; 
    
    // number of personal finance inquiries
    int32 inq_fi = 64; 
    
    // number of finance trade
    int32 total_cu_tl = 65; 
    
    // num of credit inquiries in past 12m
    int32 inq_last_12m = 66; 
}
```

#### Methods

orderTermLoan

`rpc orderTermLoan(CreditProfile) returns (CreditProfile) {}`

loadCreditProfile

Returns `CreditProfile` object

`rpc loadCreditProfile(CreditProfile) returns (CreditProfile) {}`


creditScore

Returns `CreditProfile` object

`rpc creditScore(CreditProfile) returns (CreditProfile) {}`


creditVerify

Returns `CreditProfile` object

`rpc creditVerify(Empty) returns (Empty) {}`

computeInterestRate

Returns 

`rpc computeInterestRate(CreditProfile) returns () {}`

computeCreditGrade

Returns 

`rpc computeCreditGrade(CreditProfile) returns () {}`

## Test Cases
Brokers provides the [brokers-specter] tool for checking compatibility with the Brokers specification.

## Copyright
Copyright and related rights waived via
[CC0](https://creativecommons.org/publicdomain/zero/1.0/).
