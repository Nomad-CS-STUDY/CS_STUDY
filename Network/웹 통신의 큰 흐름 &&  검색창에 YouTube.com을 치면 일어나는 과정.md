# 웹 통신의 큰 흐름 && 검색창에 youtube.com을 치면 일어나는 과정

### 사전지식

## IP 주소 
  
- 컴퓨터들이 인터넷 상에서 서로를 인식하기 위해 지정받은 번호
- 현재는 32비트인 IPv4버전을 많이 쓰고 있다.

## DNS(Domain name system)

- TCP/IP 네트워크에서 사용되는 네임 서비스의 구조, 인터넷 전화번호부라고 할 수 있다.
- 도메인 네임은 IP주소의 12자리의 숫자를 몇개의 의미있는 문자들과 점(.)의 조합으로 구성된다.
- DNS 기록을 찾기 위해서 브라우저는 다음 순서로 네 개의 캐시를 확인한다.
1. 내가 이전에 방문한 웹사이트의 DNS 기록을 저장하고 있는 브라우저 캐시를 확인한다.
2. 브라우저 캐시에 원하는 DNS 기록이 없다면 OS 캐시를 확인한다.
3. OS 캐시에도 없다면 라우터 캐시를 확인한다.
4. ISP 캐시를 확인한다. 만약 DNS 기록을 못찾았다면 브라우저는 ISP에서 DNS 기록을 찾는다.

## TCP(Transmission Control Protocol)

- TCP는 여러 종류의 HTTP 요청에 사용되는 가장 일반적인 프로토콜
- 클라이언트와 서버 간에 데이터 패킷을 전송하기 위해서는 TCP 연결이 중요함
- 이러한 연결을 설정하는 TCP/IP 3-way handshake는 서버와 클라이언트가 메시지를 주고받아 연결을 설정하는 3단계 프로세스이다.
1. 클라이언트가 인터넷을 통해 SYN(연결 요청) 패킷을 보내며 새 연결의 가능여부를 묻는다.
2.  서버가 접속 및 샐행 가는한 포트가 열려있으면 SYN(연결 요청)/ACK(승인) 패킷을 사용하여 SYN패킷의 ACK 확인으로 응답한다.
3. 클라이언트가 SYN/ACK 패킷을 수신하고 ACK 패킷을 전송하여 승인한다. 그러면 데이터 전송을 위한 TCP연결이 설정된다.

## 검색창에 youtube.com을 치면 일어나는 과정

1. 브라우저 주소창에 youtube.com을 입력한다.
2. 브라우저가 youtube.com의 IP주소를 찾기 위해 DNS 기록을 확인한다.
3. 브라우저가 해당 서버와 TCP 연결을 시작한다.
4. 브라우저가 웹서버에 HTTP 요청을 보낸다.
5. 서버가 요청을 처리하고 응답을 보낸다.
6. 서버가 HTTP 응답을 보낸다.
7. 브라우저가 HTML 내용을 보여준다.


---

참고
- https://velog.io/@khy226/브라우저에-url을-입력하면-어떤일이-벌어질까
- https://github.com/WooVictory/Ready-For-Tech-Interview/blob/master/Network/주소창에%20naver.com을%20치면%20일어나는%20일.md
- https://medium.com/@maneesa/what-happens-when-you-type-an-url-in-the-browser-and-press-enter-bb0aa2449c1a

  
