# Guide for TONStaking contracts

이 디렉토리는 Tokamak Staking 관련 스마트컨트랙트 및 오퍼레이터, L2 정보, 스테이킹/언스테이킹/리스테이킹/출금 등 주요 기능의 사용법을 정리한 문서 모음입니다.

---

- [이더스캔에서 컨트랙 함수를 호출하는 방법](./contract%20interaction%20using%20etherscan.md)
- [컨트랙트 주소](./contract%20addresses.md)
- [Stake 하는 방법](./TON%20staking.md)
- [Unstake, Restake, Withdraw 하는 방법](./unstake%2C%20restake%20and%20withdraw.md)
- [Operator 관련 정보 조회 방법](check%20l2%20information.md)

## 전체 사용 흐름 안내

1. **준비**
   - 지갑(메타마스크 등)과 TON/WTON 토큰을 준비합니다.
   - 컨트랙트 주소 등은 [contract addresses.md] 문서를 참고하세요.

2. **스테이킹**
   - TON 또는 WTON을 스테이킹하려면 [TON staking.md](./TON%20staking.md)의 `approveAndCall` 함수를 참고하세요.

3. **언스테이킹/출금 요청**
   - 스테이킹 해제(언스테이킹) 및 출금은 [unstake, restake and withdraw.md](./unstake%2C%20restake%20and%20withdraw.md)의 `requestWithdrawal`, `processRequest` 함수를 참고하세요.

4. **리스테이킹**
   - 출금 대기 중인 수량을 다시 스테이킹하려면 [unstake, restake and withdraw.md](./unstake%2C%20restake%20and%20withdraw.md)의 `redepositMulti` 함수를 참고하세요.

5. **상세 정보 확인**
   - 오퍼레이터, L2 정보 등은 [check l2 information.md](check%20l2%20information.md) 문서를 참고하세요.

> 각 단계별로 함수 사용법, 파라미터, 예시 등은 해당 문서의 목차 및 설명을 참고하면 됩니다.



