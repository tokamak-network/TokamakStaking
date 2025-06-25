# TON 스테이킹 관련 함수
> DepositManager 컨트랙을 통해 스테이킹과 관련된 함수를 실행 할 수 있습니다.
- DepositManager : [etherscan link](https://etherscan.io/address/0x0b58ca72b12f01fc05f8f252e226f3e2089bd00e#writeProxyContract)

![Write as Proxy 선택](../img/ton_staking_0.png)

위의 이더스캔 링크 페이지의 **Write as Proxy** 페이지에서 실행 가능한 함수를 확인하실 수 있습니다.

*********

### [requestWithdrawal(address layer2, uint256 amount)](https://etherscan.io/address/0x0b58ca72b12f01fc05f8f252e226f3e2089bd00e#writeProxyContract#F15)

스테이킹 된 수량 출금 요청하기

- 파라미터
  - address layer2: 출금을 수행할 오퍼레이터 주소
  - uint256 amount: 출금할 수량
- 결과
  -  없음

*********

### [redepositMulti(address layer2, uint256 n)](https://etherscan.io/address/0x0b58ca72b12f01fc05f8f252e226f3e2089bd00e#writeProxyContract#F11)

출금 요청 대기 중인 수량들 다시 스테이킹하기

- 파라미터
  - address layer2: 출금을 수행할 오퍼레이터 주소
  - uint256 n: 다시 스테이킹 요청할 요청의 개수
- 결과
  -  없음

*********

# TON 스테이킹 관련 읽기 함수
> DepositManager 컨트랙트를 통해 스테이킹과 관련된 정보를 조회할 수 있습니다.  
> DepositManager : [etherscan link](https://etherscan.io/address/0x0b58ca72b12f01fc05f8f252e226f3e2089bd00e#readProxyContract)

아래 함수들은 이더스캔의 **Read as Proxy** 탭에서 직접 실행해볼 수 있습니다.

*********

### [numPendingRequests(address layer2, address account)](https://etherscan.io/address/0x0b58ca72b12f01fc05f8f252e226f3e2089bd00e#readProxyContract#F13)

특정 계정이 특정 layer2 오퍼레이터에 대해 대기 중인 출금 요청의 개수를 반환합니다.

- 파라미터
  - address layer2: layer2 오퍼레이터 주소
  - address account: 조회할 사용자 주소
- 반환값
  - uint256: 대기 중인 출금 요청 개수

*********

### [numRequests(address layer2, address account)](https://etherscan.io/address/0x0b58ca72b12f01fc05f8f252e226f3e2089bd00e#readProxyContract#F14)

특정 계정이 특정 layer2 오퍼레이터에 대해 생성한 전체 출금 요청의 개수를 반환합니다.

- 파라미터
  - address layer2: layer2 오퍼레이터 주소
  - address account: 조회할 사용자 주소
- 반환값
  - uint256: 전체 출금 요청 개수

*********

### [withdrawalRequest(address layer2, address account, uint256 index)](https://etherscan.io/address/0x0b58ca72b12f01fc05f8f252e226f3e2089bd00e#readProxyContract#F16)

특정 계정이 특정 layer2 오퍼레이터에 대해 생성한 출금 요청의 상세 정보를 반환합니다.

- 파라미터
  - address layer2: layer2 오퍼레이터 주소
  - address account: 조회할 사용자 주소
  - uint256 index: 요청 인덱스 (0부터 시작)
- 반환값
  - 출금 요청 정보(구조체 형태, 예: amount, requestedTime, claimed 등)

*********

각 함수는 [DepositManager 컨트랙트의 Read as Proxy](https://etherscan.io/address/0x0b58ca72b12f01fc05f8f252e226f3e2089bd00e#readProxyContract) 탭에서 직접 입력값을 넣고 결과를 확인할 수 있습니다.

> 참고: withdrawalRequest의 반환값 구조는 컨트랙트 구현에 따라 다를 수 있으니, 실제 반환 필드는 이더스캔에서 확인하거나 컨트랙트 소스를 참고하세요.