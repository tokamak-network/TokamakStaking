# L2 오퍼레이터 정보 확인 함수
> L2 오퍼레이터의 주요 정보를 확인할 수 있는 함수 및 절차를 안내합니다.

*********

### [operator()](address)

오퍼레이터 컨트랙트 주소 조회

- 파라미터
  - 없음
- 결과값
  - address: 오퍼레이터 컨트랙트 주소

*********


### [rollupConfig()](address)

오퍼레이터의 롤업 설정(RollupConfig) 컨트랙트 주소 조회

- 파라미터
  - 없음
- 결과값
  - address: RollupConfig 컨트랙트 주소

*********

### [manager()](address)

오퍼레이터의 매니저 주소 조회

- 파라미터
  - 없음
- 결과값
  - address: 매니저 주소

*********

### [checkL1BridgeDetail(address rollupConfigAddress)](address)

L1 브릿지 상세 정보 조회

- 파라미터
  - address rollupConfigAddress: RollupConfig 컨트랙트 주소
- 결과값
  - array: L1 브릿지 상세 정보 (5번째 인덱스가 1이면 L2 오퍼레이터)

*********

### [optimismPortal()](address)

L2 브릿지(Optimism Portal) 주소 조회

- 파라미터
  - 없음
- 결과값
  - address: L2 브릿지 주소

*********

### [balanceOf(address account)](address)

WTON 또는 TON 잔액 조회

- 파라미터
  - address account: 조회할 계정 주소
- 결과값
  - uint256: 해당 계정의 잔액

*********

### [estimatedDistribute(uint256 blockNumber, address opAddress, bool flag)](address)

다음 블록에서 분배될 예상 시그(Seig) 보상량 조회

- 파라미터
  - uint256 blockNumber: 블록 번호
  - address opAddress: 오퍼레이터 주소
  - bool flag: 옵션 플래그
- 결과값
  - array: 분배 예상 정보 (7번째 인덱스가 추가로 분배될 WTON)

*********

## 참고
- 각 단계에서 오류가 발생할 수 있으므로, try-catch로 예외 처리를 해주는 것이 좋습니다.
- 실제 컨트랙트 주소 및 ABI, 반환값 인덱스 등은 프로젝트 환경에 맞게 적용해야 합니다. 