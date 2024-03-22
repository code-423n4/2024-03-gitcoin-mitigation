# Gitcoin Passport - Mitigation Review details

- Total Prize Pool: $4,750 in USDC
  - Warden Pool: $4,000 in USDC
  - Judge Pool: $750 in USDC
- [Warden guidelines for C4 mitigation reviews](https://code4rena.notion.site/Guidelines-for-C4-mitigation-reviews-ed10fc5cfbf640bd8dcec66f38b343c4)
- Submit findings [using the C4 form](https://code4rena.com/contests/2024-03-identity-staking-invitational-mitigation-review/submit)
- Starts March 26, 2024 20:00 UTC
- Ends March 29, 2024 20:00 UTC

## Important note

Each warden must submit a mitigation review for _every High and Medium finding_ from the parent audit that is listed as in-scope for the mitigation review. **Incomplete mitigation reviews will not be eligible for awards.**

## Findings being mitigated

Mitigations of all High and Medium issues will be considered in-scope and listed here.

- [H-01: userTotalStaked invariant will be broken due to vulnerable implementations in release()](https://github.com/code-423n4/2024-03-gitcoin-findings/issues/9)

In addition to that we have also addressed the following issues:

- [90 day minimum appeal period can be violated by lockAndBurn in the edge case of protocol pausing](https://github.com/code-423n4/2024-03-gitcoin-findings/issues/15)
- [release() is vulnerable to racing conditions against permissionless lockAndBurn(), users might lose released refunds](https://github.com/code-423n4/2024-03-gitcoin-findings/issues/7)

Other changes included in the smart contract are:

- adding missing `Release` event and changing the `Slash` event
- adding convenience functions to allow managing multiple community stakes in 1 call: `multipleCommunityStakes`, `extendMultipleCommunityStake` and `withdrawMultipleCommunityStake`

## Overview of changes

The changes include:

1. fix for the high prio issue found (H-01)
2. fixes for some of the QA level issues
3. new code:
    - small changes related to events
    - convenience functions that we have added to be able to manage multiple community stakes in 1 transaction (create, extend and withdraw multiple stakes)

## Mitigations to be reviewed

### Branch

The link to the branch containing all changes: [https://github.com/gitcoinco/id-staking-v2/tree/test_v2_1](https://github.com/gitcoinco/id-staking-v2/tree/test_v2_1)

### Individual PRs

Wherever possible, mitigations should be provided in separate pull requests, one per issue. If that is not possible (e.g. because several audit findings stem from the same core problem), then please link the PR to all relevant issues in your findings repo.

| URL                                                | Mitigation of | Purpose                                                                                                                                                                       |
| -------------------------------------------------- | ------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| https://github.com/gitcoinco/id-staking-v2/pull/8  | H-01          | This fixes the userTotalStaked invariant (acocunting error) https://github.com/code-423n4/2024-03-gitcoin-findings/issues/9                                                   |
| https://github.com/gitcoinco/id-staking-v2/pull/9  | QA            | This fixes the following: https://github.com/code-423n4/2024-03-gitcoin-findings/issues/15, https://github.com/code-423n4/2024-03-gitcoin-findings/issues/7                   |
| https://github.com/gitcoinco/id-staking-v2/pull/12 | -             | This adds a missing `Release` event and changes the `Slash` event                                                                                                             |
| https://github.com/gitcoinco/id-staking-v2/pull/10 | -             | This adds convenience functions to handle multiple community stakes in 1 call: `multipleCommunityStakes`, `extendMultipleCommunityStake` and `withdrawMultipleCommunityStake` |

## Out of Scope

n.a.
