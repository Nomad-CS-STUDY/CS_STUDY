## MIZ

### TCP와 UDP의 차이점에 대해서 설명해보세요.

IP는 다음과 같은 한계점을 가지고 있습니다.

- 비연결성: 패킷을 받을 대상이 없거나 서비스 불능 상태여도 패킷이 전송된다.
- 비신뢰성: 중간에 패킷이 사라져도 확인할 수 없고(전달성), 패킷이 순서대로 전송되지 않을 수 있다/(순서).
- 같은 서버에서 서로 다른 애플리케이션이 동작할 때 구분하지 못한다.

TCP는 3 way handshake라는 방법을 통해 데이터의 비연결성을 해소해주고, 전달성을 보장해줍니다.
또한 패킷이 순서대로 도착하지 않을 경우 순서가 맞지 않는 부분부터 다시 전송받아서 순서를 보장해줍니다.
UDP는 IP와 거의 같다는 차이점이 있습니다.
그래서 TCP를 신뢰성 있는 계층, UDP를 신뢰성이 없는 계층이라고 합니다.

### TCP의 신뢰성을 보장하는 방법에 대해 설명해주세요

먼저 3 way handshake를 통해 컴퓨터 A가 데이터를 보내면(syn) 컴퓨터 B가 데이터를 받은 후에 확인했다는 연락을 보내고(syn+ ack)
이를 컴퓨터 A가 다시 확인하는(ack) 과정을 통해 컴퓨터간의 연결성이 보장됩니다.

컴퓨터 A가 데이터를 전송하면 컴퓨터 B에서 전송받은 데이터에 대한 응답을 보내주기 때문에 전달성이 보장됩니다.

처음 데이터를 전송하는 syn 에 tcp의 연결에 할당된 임이의 시퀀스 번호가 명시되어 있어서, 이를 통해 컴퓨터 B는 순서대로 A의 데이터를
전송받을 수 있습니다.

이와 같은 과정들을 통해 TCP의 신뢰성이 보장됩니다.

## dog

### 대용량 트래픽처리하는 방법 두 가지, 간단하게 설명해주세요.

- 스타 토폴로지: 중앙에 있는 노드에 문제가 발생하면 모든 노드에 문제가 생기지만, 그렇지 않은 경우 서로 다른 노드 간의 영향이 적어서 노드 추가, 에러 탐지 등이 용이하다는
  장점이 있습니다. 물론 비용은 고가입니다.
- 메시 토폴로지 : 망형 토폴로지 라고도 하며, 노드 들이 그물망처럼 연결되어 있어서 한 노드에서 장애가 발생해도 네트워크를 계속 이용할 수 있습니다.
  하지만 노드의 추가가 어렵고, 구축 비용과 운용 비용이 많이 듭니다.

### 페이로드란?

링크 계층의 이더넷 프레임에서 상위 계층에서 캡슐화되어 내려온 데이터를 지칭하는 말입니다.

## hyewon

### 패킷이 뒤늦게 도달하고 이를 처리하지 못한다면 데이터 무결성 문제가 발생합니다. 여기서의 데이터 무결성이란 무엇인지 설명해주세요.

데이터 무결성이란 데이터의 정확성과 일관성을 유지하고 보증하는 것 => 쉽게 말해 데이터가 올바르게 전송되었는지 보장하는 것이다.

- 왜 지연 패킷은 데이터 무결성을 발생시킬까?
  위에 TCP를 예로 들어보자. 컴퓨터 A가 데이터 1,2,3,4가 있다. 컴퓨터 B는 1,2,4,3의 순서로 데이터가 들어오자 1,2만 받고 3부터 다시 요청하는 상태이다.
  이 때 지연 패킷이 발생한다면 TCP에 의해 보장되는 순서를 지키기 위해 컴퓨터 B는 데이터 3이 도착할 때까지 대기해야 한다. 이 지연된 패킷이 제대로 처리되지 않으면,
  데이터 무결성이 손상될 수 있다. => 이로 인해 TIME_WAIT이라는 잠시 대기하는 시간이 필요해진다.

### 라우터는 어떤 장비인지 설명해주세요.

서로 다른 네트워크 간의 정보 전송을 중개해주는 인터넷 계층의 핵심 장비입니다.
라우터는 패킷이 효율적으로 전달될 수 있도록 경로를 정해주고, 패킷을 IP주소에 맞게 전달하고, 패킷 소모를 줄여줍니다.
또한 서로 다른 네트워크(ex. 이더넷과 wifi) 간의 통신을 가능하게 해줍니다.

---

## yeop222

### 스누핑(snooping)에 대해 설명해주세요.

스푸핑은 누군가가 다른 사람이나 장치처럼 위장해서 통신 네트워크에 무단으로 접근하려고 할 때 사용하는 기술입니다.
이를 통해 송신 노드에서 보낸 패킷이 수신 노드로 전달되기 전 가로채게 됩니다.

### HTTP과 HTTPS의 차이점에 대해 설명해주세요

HTTP는 Hypertext Transfer Protocole로 클라이언트와 서버 간 통신을 위한 프로토콜입니다. 과거에는 링크로 연결된 문서(Hyepertext)를 전송했지만
요즘은 거의 모든 형태의 데이터를(HTML, TEXT, 이미지, 영상, 파일, Json 등) 전송 가능합니다.
HTTP/1.1(RFC7230)을 주로 사용하고, HTTP/2와 HTTP/3는 성능 개선에 초점을 맞춘 버전입니다.
TCP는 HTTTP/1.1, HTTP/2 기반으로 UDP는 HTTP/3 기반으로 동작합니다.
HTTP의 가장 중요한 특징은 클라이언트와 서버 구조로 이루어져 있어서, 비지니스 로직과 UI를 분리했다는 것입니다.

HTTPS는 HTTP 보다 보안성이 더 뛰어난 버전입니다.