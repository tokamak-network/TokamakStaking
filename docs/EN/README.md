# Guide for TONStaking contracts

This directory contains documentation for Tokamak Staking smart contracts, operator and L2 information, and how to use key features such as staking, unstaking, restaking, and withdrawal.

---

- [How to interact with contracts using Etherscan](./contract%20interaction%20using%20etherscan.md)
- [Contract addresses](./contract%20addresses.md)
- [How to stake](./TON%20staking.md)
- [How to unstake, restake, and withdraw](./unstake%2C%20restake%20and%20withdraw.md)
- [How to check operator information](./check%20l2%20information.md)

## Overall Usage Flow

1. **Preparation**
   - Prepare your wallet (e.g., MetaMask) and TON/WTON tokens.
   - See [contract addresses.md] for contract addresses.

2. **Staking**
   - To stake TON or WTON, refer to the `approveAndCall` function in [TON staking.md].

3. **Unstaking / Withdrawal Request**
   - To unstake and request withdrawal, refer to the `requestWithdrawal` and `processRequests` functions in [unstake, restake and withdraw.md].

4. **Restaking**
   - To restake pending withdrawal amounts, refer to the `redepositMulti` function in [unstake, restake and withdraw.md].

5. **Detailed Information**
   - For operator and L2 information, see [check l2 information.md].

> For each step, refer to the table of contents and explanations in the relevant document for function usage, parameters, and examples.

---

## Main Documents
- [TON staking.md]: How to stake TON/WTON and function explanations
- [unstake, restake and withdraw.md]: How to unstake, restake, and withdraw, and function explanations
- [check l2 information.md]: How to check operator and L2 information
- [contract addresses.md]: List of main contract addresses
- [contract interaction using etherscan.md]: How to use Etherscan to interact with contract functions

---
