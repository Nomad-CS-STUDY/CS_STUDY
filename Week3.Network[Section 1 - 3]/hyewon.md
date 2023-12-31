## MIZ

### TCP와 UDP의 차이점에 대해서 설명해보세요.

TCP는 패킷 사이의 순서를 보장하고 데이터의 경계를 구분하지 않으며 연결지향 프로토콜을 사용해서 연결을 하여 신뢰성을 구축해서 수신 여부를 확인하며 가상회선 패킷 교환 방식을 사용하는 반면, UDP는 순서를 보장하지 않고 데이터의 경계를 구분하며 수신 여부를 확인하지 않으며 단순히 데이터만 주는 데이터그램 패킷 교환 방식을 사용합니다. 결론적으로, 패킷 사이의 순서 보장 여부와 신뢰성 존재 여부, 교환 방식의 상이함, 수신 확인 여부, 데이터 경계 구분 여부의 차이점이 존재한다.

### TCP의 신뢰성을 보장하는 방법에 대해 설명해주세요.

TCP의 신뢰성을 보장하는 방법은 TCP 재전송 입니다. TCP는 자신이 보낸 데이터에 대해서 상대방이 받았다는 의미의 응답 패킷을 다시 받아야 통신이 정상적으로 이뤄졌다고 생각합니다. 그러므로 만약 상대방이 응답 패킷을 받지 못하면 패킷이 유실되었다고 판단하고 보냈던 패킷을 다시 한번 보냅니다. 결론적으로, 재전송을 통해 데이터가 정상적으로 수신되었는지 확인하므로 신뢰성을 보장합니다.

---

## dog

### 대용량 트래픽처리하는 방법 두 가지, 간단하게 설명해주세요.

대용량 트래픽을 처리할려면 서버를 확장해야 하므로 scale up, scale out 두 가지 방법을 활용해야 합니다. scale up은 서버 컴퓨터 자체를 더 상위 제품으로 교체하는 것이다. scale up의 장점은 한 대의 서버 컴퓨터를 업그레이드 하기 때문에 서버의 개수가 늘어나는 것보다 관리와 확장이 상대적으로 쉽고 서버끼리의 네트워크 비용이 추가로 들지 않습니다. 하지만, 하드웨어의 성능이 높아질수록 가격이 높아진다는 단점을 가지고 있습니다. scale out은 서버의 개수를 늘려 대용량 트래픽을 감당하는 방법입니다. scale out은 서버를 확장할 때 서비스를 일시 중단할 필요가 없으며 상대적으로 비용을 효율적으로 사용할 수 있습니다. 다만, 서버 노드 간 네트워크 통신 비용이 추가로 발생하며 서버 노드 간 동시성 문제가 발생합니다.

### 페이로드란?

페이로드란 사용에 있어서 전송되는 즉, 보내고자 하는 데이터 자체를 의미합니다. 데이터를 전송할 때, 헤더와 메타 데이터, 에러 체크 비트 등과 같은 다양한 요소들을 함께 보내어, 데이터 전송의 효율과 안정성을 높이게 됩니다. 다만, 앞서 설명한 다양한 요소들은 전송의 목적이 되는 데이터의 일부분으로 페이로드에 해당되지는 않습니다.

---

## js

### TCP는 기존 IP만 사용했을 때 발생하는 문제점을 해결하기 위해 3-way-handshake라는 방법을 사용합니다. 이에 관해 설명해주세요.

3-way-handshake는 총 3단계로 구성이 되어있는데요. 첫 번째 단계는 SYN 단계로 클라이언트는 서버와 커넥션을 연결하기 위해 서버에 클라이언트의 ISN을 담아 SYN을 보냅니다. 두 번째 단계는 SYN + ACK 단계로 서버는 SYN을 받고, 서버의 ISN을 보내며 승인번호로 클라이언트의 ISN + 1을 보냅니다. 마지막 단계는 ACK 단계로 클라이언트는 서버의 ISN + 1한 값인 승인번호를 담아 ACK를 서버에 보내는 단계입니다. 이러한 세 단계 이후 신뢰성이 구축되고 데이터 전송을 시작합니다.

### TCP/IP 4계층 모델에서, 사용자가 다른 컴퓨터와 통신을 하게 되면 계층 간 데이터 송수신 과정을 거치게 됩니다. 이 때 발생하는 캡슐화 과정에 대해 서술해 주세요.

캡슐화 과정은 데이터 송수신시, 각 계층에서 계층의 특징들을 담긴 헤더들이 붙는 과정입니다. 애플리케이션 계층에서 데이터가 전송 계층으로 전달되고 전송 계층에서는 TCP헤더가 추가되며 데이터그램화됩니다. 다음으로 전승계층에서 추가된 TCP헤더가 인터넷 계층으로 전달되며 IP헤더가 추가되며 패킷화가 됩니다. 마지막으로 인터넷 계층에서 추가된 IP헤더가 링크 계층으로 전달되며 프레임 헤더와 프레임 트레일러가 추가된 후 프레임화가 되고 나서 물리계층으로 전송이 진행됩니다.

---

## yeop222

### 스누핑(snooping)에 대해 설명해주세요.

스누핑이란 네트워크 상의 정보를 염탐하여 불법적으로 얻는 것을 말하므로 스니핑과 개념이 비슷합니다. 스누핑은 스니핑과 달리 감시와 분석에 초점이 맞춰져 있습니다. 즉, 네트워크 상 정보를 감시, 분석하는 행위라고 볼 수 있는거죠. 그렇기에 네트워크 트래픽 분석, 성능 모니터링, 보안 감사 등 우호적인 목적으로 사용될 수 있습니다.

### HTTP과 HTTPS의 차이점에 대해 설명해주세요

HTTP는 클라이언트와 서버 간 통신을 위한 통신 규칙 세트 또는 프로토콜입니다. 사용자가 웹 사이트를 방문하면 사용자 브라우저가 웹 서버에 HTTP 요청을 전송하고 웹 서버는 HTTP 응답으로 응답합니다. HTTPS는 SSL 인증서를 사용하는 HTTP입니다. 따라서 HTTPS는 HTTP보다 더 안전한 보안용 프로토콜이라고 할 수 있습니다. 즉, HTTP는 암호화가 추가되지 않았기 때문에 보안에 취약하지만 HTTPS는 안전하게 데이터를 주고받을 수 있다는 차이점이 있습니다.
