# TON Staking Functions
> You can execute staking-related functions through the TON contract.
- TON: [etherscan link](https://etherscan.io/address/0x2be5e8c109e2197D077D13A82dAead6a9b3433C5#writeContract)

---

## Table of Contents
- [Overall Staking Flow](#overall-staking-flow)
- [approveAndCall (TON)](#approveandcalladdress-spender-uint256-amount-data-bytes)
- [approveAndCall (WTON)](#approveandcalladdress-spender-uint256-amount-data-bytes-1)

---

## Overall Staking Flow

1. **Preparation**
   - Prepare your wallet (e.g., MetaMask) and TON/WTON tokens.
   - For contract addresses, refer to [contract addresses.md].

2. **Staking**
   - To stake TON or WTON, use the `approveAndCall` function.
   - TON staking: [approveAndCall (TON)](#approveandcalladdress-spender-uint256-amount-data-bytes)
   - WTON staking: [approveAndCall (WTON)](#approveandcalladdress-spender-uint256-amount-data-bytes-1)

3. **Unstaking / Withdrawal Request**
   - For unstaking and withdrawal, refer to [unstake, restake and withdraw.md].
   - Main functions: requestWithdrawal, withdraw, etc.

4. **Restaking**
   - To restake pending withdrawal amounts, refer to the redepositMulti function in [unstake, restake and withdraw.md].

5. **Detailed Information**
   - For operator and L2 information, see [check l2 information.md].

> For each step, refer to the table of contents and explanations in the relevant document for function usage, parameters, and examples.

---

![Write selection](../img/stake_ton_0.png)

You can check the available functions on the **Write** page of the Etherscan link above.

*********

## [approveAndCall(address spender, uint256 amount, data bytes)](https://etherscan.io/address/0x2be5e8c109e2197D077D13A82dAead6a9b3433C5#writeContract#F3)

This function approves TON tokens to the staking contract and simultaneously stakes them to the specified layer2 operator. You approve the spender and select where to stake via the data field.

- Parameters
  - address spender: WTON address (`0xc4A11aaf6ea915Ed7Ac194161d2fC9384F15bff2`)
  - uint256 amount: Amount of TON tokens to stake (Wei, 18 decimal)
  - data: Encoded value of the fixed DepositManager address and the variable operator address to stake to
- Result
  - None

> This function handles both approve and staking in one transaction, so you can stake directly without a separate approve transaction.

**About the data parameter**
- The data field is a concatenation of the DepositManager address (e.g., `0x0b58ca72b12f01fc05f8f252e226f3e2089bd00e`) and the operator address to stake to (e.g., `0xF078AE62eA4740E19ddf6c0c5e17Ecdb820BbEe1`), each as 32 bytes.
- The DepositManager address is always fixed; only the operator address changes.
- Example:
  - data = `0x0000000000000000000000000b58ca72b12f01fc05f8f252e226f3e2089bd00e000000000000000000000000F078AE62eA4740E19ddf6c0c5e17Ecdb820BbEe1`
    - First 32 bytes: DepositManager address
    - Last 32 bytes: Operator address to stake to

> You can stake to multiple operators by changing only the operator address.

*********

# WTON Staking Functions
> You can execute staking-related functions through the WTON contract. There are two methods.
- WTON: [etherscan link](https://etherscan.io/address/0xc4A11aaf6ea915Ed7Ac194161d2fC9384F15bff2#writeContract)

You can check the available functions on the **Write** page of the Etherscan link above.

*********

## [1. approveAndCall(address spender, uint256 amount, data bytes)](https://etherscan.io/address/0xc4A11aaf6ea915Ed7Ac194161d2fC9384F15bff2#writeContract#F3)

This function approves WTON tokens to the staking contract and simultaneously stakes them to the specified layer2 operator.

- Parameters
  - address spender: DepositManager address (`0x0b58ca72b12f01fc05f8f252e226f3e2089bd00e`)
  - uint256 amount: Amount of TON tokens to stake (Ray, 27 decimal)
  - data: Encoded value of the operator address to stake to (variable)
- Result
  - None

> This function handles both approve and staking in one transaction, so you can stake directly without a separate approve transaction.

**About the data parameter**
- The data field is a 32-byte encoding of the operator address to stake to (e.g., `0xF078AE62eA4740E19ddf6c0c5e17Ecdb820BbEe1`).
- Only the operator address needs to be changed for each staking.
- Example:
  - data = `0x000000000000000000000000F078AE62eA4740E19ddf6c0c5e17Ecdb820BbEe1`
    - Last 32 bytes: Operator address to stake to

> You can stake to multiple operators by changing only the operator address.

## 2. Approve and Deposit
> Execute approve and deposit separately
### [2-1. approve](https://etherscan.io/address/0xc4A11aaf6ea915Ed7Ac194161d2fC9384F15bff2#writeContract#F2)
This method separates approve and deposit, which can be advantageous in terms of gas savings.
- Parameters
  - address spender: DepositManager address (`0x0b58ca72b12f01fc05f8f252e226f3e2089bd00e`)
  - uint256 amount: Amount of TON tokens to stake (Ray, 27 decimal)

Once approve is complete, move to the DepositManager and perform the deposit.

### [2-2. deposit(address layer2, uint256 amount)](https://etherscan.io/address/0x0b58ca72b12f01fc05f8f252e226f3e2089bd00e#writeProxyContract#F2)
- Parameters
  - address layer2: Operator address to stake to
  - uint256 amount: Amount of TON tokens to stake (Ray, 27 decimal) 