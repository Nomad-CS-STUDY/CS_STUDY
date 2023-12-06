# DNS (Domain Name System) 정리
Host (인터넷에 연결된 컴퓨터 한대) 끼리 통신을 하기 위해 필요한 주소 
=> IP Address(주소)
하지만 "IP주소를 기억하는것은 어렵고 이를 위해 DNS가 나오게 되었다" 라는것도 맞지만 
구체적인 DNS 탄생 흐름을 보면 아래와 같다. 

- 2대의 컴퓨터가 인터넷 통신을 위해 반드시 필요한 것은 IP주소 
  ( 컴퓨터 뿐 아니라 인터넷이 연결된 것은 Host라고 칭함) 
- 모든 IP주소를 기억하는 일은 너무 어려움!
- 이것을 해결하기 위해 운영체제마다 Hosts라는 파일이 존재
- Hosts라는 파일에는 IP주소와 도메인이름을 저장해두면 도메인 이름을 통해 다른 host에 접근할 수 있다. 

## DNS가 나오기 전 
Stanford Research Institute에서 전 세계의 hosts파일을 관리
위 기관의 hosts파일을 덮어쓰기 한 후, 사용자의 컴퓨터에서 접속을 원하는 도메인 이름으로 접속
유익한 방식이였지만 인터넷이 커지면서 문제점이 발생
1. hosts 파일을 다운로드하지 않으면 추가된 호스트 이름을 사용할 수 없다.
2. SRI(Stanford Research Institute) 에서 수작업으로 IP와 도메인 이름을 갱신해야해서 시간과 비용의 문제가 있었다.

## DNS 가 나오고 난 후 
DNS에게 이 IP는 ~라는 Domain 이름을 갖고 싶습니다!라고 요청하면(자동화되어 있다.) DNS에 갱신된 내용이 저장.
![정리1](https://github.com/Nomad-CS-STUDY/CS_STUDY/assets/71619429/3e62d3b6-1555-4bba-b28d-56d08a85e2c3)

컴퓨터에서 와이파이 혹은 인터넷이 연결되면 DNS Server에 있는 IP 주소가 DHCP를 통해 셋팅

웹 브라우저에서 도메인 이름을 입력하면 먼저 로컬의 hosts 파일에서 찾은 후, 없다면 DNS Server에 Domain 이름의 IP를 요청하고 받는다. 

- (DHCP 란?
https://inpa.tistory.com/entry/WEB-%F0%9F%8C%90-DHCP-%EC%9D%B4%EB%9E%80-%EB%AC%B4%EC%97%87%EC%9D%B8%EA%B0%80, 
https://nordvpn.com/ko/blog/what-is-dhcp/)


## DNS의 내부 원리
DNS Server는 IP 주소와 Domain 이름을 기억하는 기능과 Client가 이름을 물어보면 IP를 알려주는 기능
수천대의 서버가 같이 협력
![정리 2](https://github.com/Nomad-CS-STUDY/CS_STUDY/assets/71619429/bc97a28a-1e89-46c6-a713-651ba4253e5a)

각각의 부분들은 부분들을 담당하는 독자적인 Server Computer가 존재
- Root는 Top-level을 담당하는 Server의 목록과 IP를 알고 있다
- Top-level은 Second-level, Second-level은 sub의 목록과 IP를 알고 있다. (즉, 상위 목록이 직속 하위 목록을 알고 있음)

- 최초 root 네임서버의 IP 주소에게 blog.example.com을 물어보면 .com을 담당하는 Top-level을 알려주고, Top-level은 example.com을 담당하는 Second-level을 알려주고, Second-level은 blog.example.com 담당하는 sub DNS Server에게 물어보고, sub가 해당 IP 주소를 알려준다.
  DNS는 계층적인 구조를 가지고 있다.
