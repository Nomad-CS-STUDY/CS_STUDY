## yeop222

1. 스누핑(snooping)에 대해 설명해주세요.
네트워크에서 데이터를 도청하거나 감시하는 행위를 가리키는 용어

2. HTTP과 HTTPS의 차이점에 대해 설명해주세요.

HTTPS는 HTTP에서 보안 및 데이터 무결성을 강화한 버전

---

## hyewon

1. 패킷이 뒤늦게 도달하고 이를 처리하지 못한다면 데이터 무결성 문제가 발생합니다. 여기서의 데이터 무결성이란 무엇인지 설명해주세요.

데이터 누락되거나 부분적으로 저장되지 않고 정확성과 일관성을 유지하고 보증하는 것

2. 라우터는 어떤 장비인지 설명해주세요.

여러 개의 네트워크를 연결, 분할, 구분 시키고 라우팅을 하는 장비

---

## KJS

1. TCP는 기존 IP만 사용했을 때 발생하는 문제점을 해결하기 위해 3-way-handshake라는 방법을 사용합니다. 이에 관해 설명해주세요.
우선 클라이언트가 서버에 클라이언트의 ISN을 담아 SYN을 보내면 서버는 클라이언트의 SYN을 받고 서버의 ISN, 승인번호를 ISN+1로 보낸다. 그 후 클라이언트는 서버의 ISN + 1한 값인 승인번호를 ACK에 담아 서버에 보냄

2. TCP/IP 4계층 모델에서, 사용자가 다른 컴퓨터와 통신을 하게 되면 계층 간 데이터 송수신 과정을 거치게 됩니다. 이 때 발생하는 캡슐화 과정에 대해 서술해 주세요.

애플리케이션 계층의 데이터가 전송계층에서 데이터에 TCP 헤더가 붙여지고 인터넷 계층에서 IP헤더가 붙여진다. 그 후 링크 계층에서 프레임 헤더와 프레임 트레일러가 붙여진다.

---

## dog

1.대용량 트래픽처리하는 방법 두 가지, 간단하게 설명해주세요.  

대역폭 확장과 부하를 분산시키는 로드 밸런싱이 있다.

2.페이로드란?

패킷에 담겨 있는 실직전인 데이터, 4계층의 모든 데이터는 3계층 페이로드가 된다.

---
## MIZ

1. TCP와 UDP의 차이점에 대해서 설명해보세요.

TCP는 가상 회선 패킷 교환 방식을 사옹하지만 UDP는 데이터그램 패킷 교환 방식을 사용한다.

2. TCP의 신뢰성을 보장하는 방법에 대해 설명해주세요

3-way handshake를 진행하여 신뢰성을 확보한다. 3-way handshake는 SYN단계, SYN + ACK 단계, ACK 단계로 이루어져있다.
