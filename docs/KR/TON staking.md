# TON 스테이킹 함수
> TON 컨트랙을 통해 스테이킹과 관련된 함수를 실행 할 수 있습니다.
- TON : [etherscan link](https://etherscan.io/address/0x2be5e8c109e2197D077D13A82dAead6a9b3433C5#writeContract)

---

## 목차
- [전체 스테이킹 흐름](#전체-스테이킹-흐름)
- [approveAndCall (TON)](#approveandcalladdress-spender-uint256-amount-data-bytes)
- [approveAndCall (WTON)](#approveandcalladdress-spender-uint256-amount-data-bytes-1)

---

## 전체 스테이킹 흐름

1. **준비**
   - 지갑(메타마스크 등)과 TON/WTON 토큰을 준비합니다.
   - 컨트랙트 주소 등은 [contract addresses.md] 문서를 참고하세요.

2. **스테이킹**
   - TON 또는 WTON을 스테이킹하려면 `approveAndCall` 함수를 사용합니다.
   - TON 스테이킹: [approveAndCall (TON)](#approveandcalladdress-spender-uint256-amount-data-bytes)
   - WTON 스테이킹: [approveAndCall (WTON)](#approveandcalladdress-spender-uint256-amount-data-bytes-1)

3. **언스테이킹/출금 요청**
   - 스테이킹 해제(언스테이킹) 및 출금은 [unstake, restake and withdraw.md] 문서를 참고하세요.
   - 주요 함수: requestWithdrawal, withdraw 등

4. **리스테이킹**
   - 출금 대기 중인 수량을 다시 스테이킹하려면 [unstake, restake and withdraw.md]의 redepositMulti 함수를 참고하세요.

5. **상세 정보 확인**
   - 오퍼레이터, L2 정보 등은 [check l2 information.md] 문서를 참고하세요.

> 각 단계별로 함수 사용법, 파라미터, 예시 등은 해당 문서의 목차 및 설명을 참고하면 됩니다.

---

![Write 선택](../img/stake_ton_0.png)

위의 이더스캔 링크 페이지의 **Write** 페이지에서 실행 가능한 함수를 확인하실 수 있습니다.

*********

## [approveAndCall(address spender, uint256 amount, data bytes)](https://etherscan.io/address/0x2be5e8c109e2197D077D13A82dAead6a9b3433C5#writeContract#F3)

TON 토큰을 스테이킹 컨트랙트에 승인(approve)하고, 동시에 지정된 layer2 오퍼레이터에 스테이킹을 실행하는 함수입니다. spender에 승인을 내주고 data 필드를 통해 어디에 스테이킹 할 지를 선택합니다.

- 파라미터
  - address spender: WTON 주소(`0xc4A11aaf6ea915Ed7Ac194161d2fC9384F15bff2`)
  - uint256 amount: 스테이킹할 TON 토큰 수량(Wei, 18 decimal)
  - data: DepositManager 주소(고정)와 스테이킹할 오퍼레이터 주소(가변)를 인코딩한 값
- 결과
  - 없음

> 이 함수는 approve와 staking을 한 번에 처리하므로, 별도의 approve 트랜잭션 없이 바로 스테이킹이 가능합니다.

**data 파라미터 설명**
- data 필드는 DepositManager 주소(예: `0x0b58ca72b12f01fc05f8f252e226f3e2089bd00e`)와 스테이킹할 오퍼레이터 주소(예: `0xF078AE62eA4740E19ddf6c0c5e17Ecdb820BbEe1`)를 순서대로 32바이트씩 이어붙여 인코딩한 값입니다.
- DepositManager 주소는 항상 고정되어 있으며, 오퍼레이터 주소만 변경됩니다.
- 예시:
  - data = `0x0000000000000000000000000b58ca72b12f01fc05f8f252e226f3e2089bd00e000000000000000000000000F078AE62eA4740E19ddf6c0c5e17Ecdb820BbEe1`
    - 앞 32바이트: DepositManager 주소
    - 뒤 32바이트: 스테이킹할 오퍼레이터 주소

> 오퍼레이터 주소만 변경하여 여러 오퍼레이터에 대해 스테이킹을 진행할 수 있습니다.

*********

# WTON 스테이킹 함수
> WTON 컨트랙을 통해 스테이킹과 관련된 함수를 실행 할 수 있습니다. 방법은 두 가지가 있습니다.
- WTON : [etherscan link](https://etherscan.io/address/0xc4A11aaf6ea915Ed7Ac194161d2fC9384F15bff2#writeContract)

위의 이더스캔 링크 페이지의 **Write** 페이지에서 실행 가능한 함수를 확인하실 수 있습니다.

*********

## [1. approveAndCall(address spender, uint256 amount, data bytes)](https://etherscan.io/address/0xc4A11aaf6ea915Ed7Ac194161d2fC9384F15bff2#writeContract#F3)

WTON 토큰을 스테이킹 컨트랙트에 승인(approve)하고, 동시에 지정된 layer2 오퍼레이터에 스테이킹을 실행하는 함수입니다.

- 파라미터
  - address spender: DepositManager 주소(`0x0b58ca72b12f01fc05f8f252e226f3e2089bd00e`)
  - uint256 amount: 스테이킹할 TON 토큰 수량(Ray, 27 decimal)
  - data: 스테이킹할 오퍼레이터 주소(가변)를 인코딩한 값
- 결과
  - 없음

> 이 함수는 approve와 staking을 한 번에 처리하므로, 별도의 approve 트랜잭션 없이 바로 스테이킹이 가능합니다.

**data 파라미터 설명**
- data 필드는 스테이킹할 오퍼레이터 주소(예: `0xF078AE62eA4740E19ddf6c0c5e17Ecdb820BbEe1`)를 순서대로 32바이트씩 이어붙여 인코딩한 값입니다.
- 스테이킹을 하고자 하는 오퍼레이터의 주소만 변경하면 됩니다.
- 예시:
  - data = `0x000000000000000000000000F078AE62eA4740E19ddf6c0c5e17Ecdb820BbEe1`
    - 뒤 32바이트: 스테이킹할 오퍼레이터 주소

> 오퍼레이터 주소만 변경하여 여러 오퍼레이터에 대해 스테이킹을 진행할 수 있습니다.

## 2. Approve and Deposit
> Approve 와 Deposit을 나눠서 실행합니다
### [2-1. approve](https://etherscan.io/address/0xc4A11aaf6ea915Ed7Ac194161d2fC9384F15bff2#writeContract#F2)
이 방법은 승인(approve)와 deposit을 나눠서 하는 작업이며, 가스비 절약 측면에서 이점이 있습니다.
- 파라미터
  - address spender: DepositManager 주소(`0x0b58ca72b12f01fc05f8f252e226f3e2089bd00e`)
  - uint256 amount: 스테이킹할 TON 토큰 수량(Ray, 27 decimal)

approve가 완료됐다면 그 다음은 Deposit Manager로 이동해서 deposit을 수행해주면 된다

### [2-2. deposit(address layer2, uint256 amount)](https://etherscan.io/address/0x0b58ca72b12f01fc05f8f252e226f3e2089bd00e#writeProxyContract#F2)
- 파라미터
  - address layer2: 스테이킹할 오퍼레이터 주소
  - uint256 amount: 스테이킹할 TON 토큰 수량(Ray, 27 decimal)