## ARTE NFT Smart Contract
> [ARTE NFT](https://arte-nft.art)는 [아르떼 뮤지엄(ARTE MUSEUM)](https://artemuseum.com)이 제공하는 공간과 미디어의 예술 경험을 확장하는 WEB3 프로젝트다. 아르떼 뮤지엄의 실감 미디어 작품의 일부를 원하는 비율과 크기 옵션으로 선택하여 NFT로 소장할 수 있는 기회를 제공하며, NFT 홀더만 구매할 수 있는 특별 MD 상품을 판매한다. 2023년 2월 서울옥션의 미술 대중화 브랜드인 [프린트 베이커리(PRINT BAKERY)](https://printbakery.com)와의 콜라보레이션을 통해 특별 기획된 MD 상품과 NFT를 발행했다.

## Environment  

- Ethereum
- Solidity 0.8.9
- Node.js 16
- Hardhat 2
- OpenZeppelin 4

## Features  

- `mintToken` : 사용자가 <ins>이더리움 결제</ins>를 선택하는 경우, <ins>일반 통화 결제(휴대폰 소액 결제, 계좌이체 등)</ins> 완료 후 <ins>NFT 받기</ins>를 요청하는 경우, 관리자 페이지 내에서 <ins>민팅하기</ins> 기능을 실행하는 경우 작동
  - paused 상태의 영향을 받는 기능
  - 잔액 및 송금액 점검 후 조건에 부합하지 않을 시 트랜잭션을 발생시키지 않고 에러를 반환
  - 상품 유형 및 에디션 종류별로 mintPrice가 달라져야 함
  - 결제 유형에 따라 NFT의 deployer가 달라져야 함
  - '일반 통화 결제' 후 'NFT 받기' 요청에 의해 작동하는 경우 정상 발행되지 않은 토큰 전송 요청은 revert
 
- `transferToken` : <ins>일반 통화 결제</ins> 완료 후 <ins>NFT 받기</ins> 요청이 발생한 경우, 오프라인 팝업 행사 판매를 통해 제공한 작품보증서의 QR코드 접속 링크에서 <ins>NFT 받기</ins> 요청이 발생한 경우 실행
  - paused 상태의 영향을 받는 기능
  - ownable
  - 실행 전 전송하려는 tokenId의 유효성을 검증해야 함
  - 실행 전 전송하려는 tokenId의 소유자가 owner인지 검증해야 함
 
- `withdraw` : 스마트 컨트랙이 보유한 잔액을 모두 출금하는 경우 실행
  - paused 상태의 영향을 받지 않는 기능
  - 출금액의 전송 대상을 오로지 컨트랙의 소유자 계정에만 가능해야 함
 
- `getCurrentTokenId` : 가장 최근에 생성된 tokenId의 Counter 값을 확인하는 외부 조회용 함수

- `verifyHash` : DApp에서 signer 검증을 위해 호출하는 함수

- `setPaused` : 스마트 컨트랙의 정지/재개 상태를 변경하는 함수

## Information

- Contract Address : [0xD9E38EA15872Dc2509b24649c90E7597eBD23e46](https://etherscan.io/address/0xD9E38EA15872Dc2509b24649c90E7597eBD23e46)
