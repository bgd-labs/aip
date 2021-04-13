---
aip: 11
title: desactivation of Aave V1 stable rate borrowing
status: Proposed
author: Marc Zeller (@marczeller), Emilio Frangella (@The3D_)
shortDescription: Disable Aave V1 Stable Rates
discussions: https://governance.aave.com/t/aave-protocol-v1-v2-migration-tool-and-transition-plan/2053
created: 2021-04-02
updated: 2021-04-02
---

## AIP rationale

The Aave Protocol V2 was launched in Dec 2020 and is now concentrating the majority of the Aave protocol Liquidity
Aave V1 users have the option to upgrade their position seamlessly into V2 with the native Aave migration tool

With significant reserves in, the community has the opportunity to implement a plan to transition the remaining reserves from V1 to v2.
The community has the opportunity to bring about this change to ease the borrowing pressure on V1, to address high transaction fees that exist now, and may increase further upon the implementation of Berlin hardfork.
The migration can benefit not only Aave users, but also the Aave ecosystem as a whole because it will allow protocols integrating with Aave to have additional stablecoins liquidity available(due to the ecosystem wide stablecoin liquidity crush).

Besides the beneficial effects on the migration procedure, disabling the stable rate borrowing overcomes the friction generated by the inefficient lending rate oracle V1, which currently proposes rates that are too low for the current market conditions. This has generated a consistent amount of stable rate debt, which results in frictions for the V1 liquidity providers and integrators that still rely on Aave V1 for their deposits.

If this proposal is approved by the Aave governance, new stable rates loans positions will be disabled for Aave V1.

The rebalancing mechanism will also be updated to an enforced swap to variable rates. Which means, in case of extremely high borrowing pressure on the stablecoins reserves, users at stable rate will be migrated to variable until rebalancing conditions are not satisfied anymore.


## AIP content in short

Deactivation of the ability to open new stable rate borrowing positions on Aave V1 and update of the rebalance mechanism

## Implementations details

Executes the proposal deployed at

https://etherscan.io/address/0x6a46c03c861cab74c8a213983b7eb295234c16b3#code

The proposal executes the following:

- Updates the LendingPool implementation to 

  https://etherscan.io/address/0xDB9217fad3c1463093fc2801Dd0a22C930850A61#code

- Updates the LendingPoolCore implementation to

  https://etherscan.io/address/0x2847A5D7Ce69790cb40471d454FEB21A0bE1F2e3#code

  These contract updates are needed to update the implementation of the rebalanceStableRate() function

- Execute disableReserveStableBorrowRate() in all the assets listed on the protocol V1

## Copyright

Copyright and related rights waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).