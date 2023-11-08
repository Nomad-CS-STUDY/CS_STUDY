## MIZ

### RTT(Round Trip TIme)가 무엇인지 설명하고 RTT증가를 해결하는방법에 대해 설명해주세요

RTT는 패킷이 목적지에 도달하고 나서 다시 출발지로 돌아오기까기 걸리는 시간입니다. 즉, 패킷 왕복 시간이라 할 수 있습니다. 매번 연결할 때마다 RTT가 증가하면 서버에 부담이 많이 가고 사용자 응답 시간이 길어집니다. 이를 해결하기 위해선 이미지 스플리팅, 코드 압축, 이미지 Base64 인코딩을 사용하면 됩니다. 이미지 스플리팅은 많은 이미지가 합쳐 있는 하나의 이미지를 다운받고 이를 기반으로 background-image의 position을 이용하여 이미지를 표기하는 방법입니다. 코드 압축은 코드를 압축해서 개행 문자, 빈칸을 없애 코드의 크기를 최소화하는 방법입니다. 이미지 Base64 인코딩은 이미지 파일을 64진법으로 이루어진 문자열로 인코딩하는 방법입니다. 결론적으로 세 개의 방법을 잘 사용하면 RTT 증가를 해결할 수 있습니다.

### 암호화 알고리즘 중 Diffie–Hellman key exchange 가 무엇인지 설명해주세요

디피-헬만 키 교환 암호화 알고리즘은 암호키를 교환하는 방법입니다. 처음에 공개 값을 공유하고 각자의 비밀 값과 혼합한 후 혼합 값을 공유합니다. 그 후 각자의 비밀 값과 또 혼합하는데요. 그 이후에 공통의 암호키가 생성됩니다. 이 과정이 진행된다면 악의적인 공격자가 개인키 또는 공개키를 가지고도 공통의 암호키가 없기 때문에 아무것도 할 수 없습니다.

---

## dog

---

## js

### HTTPS를 구축하는 3가지 방법에 대하여 설명해주세요.

HTTPS는 신뢰할 수 있는 HTTP 요청을 말합니다. 이를 구축할 수 있는 첫 번째 방법은 직접 CA에서 구매한 인증키를 기반으로 HTTPS 서비스를 구축하는 것입니다. CA에서 구매한 인증키는 사용자가 접속한 서버가 신뢰할 수 있는 서버임을 보장합니다. 두 번째 방법은 서버 앞단의 HTTPS를 제공하는 로드밸런서를 두는 것입니다. 로드밸런서는 클라이언트의 요청 및 네트워크의 트래픽이 집중되는 서버들 또는 네트워크 허브 사이에 위치하며 특정 서버 또는 네트워크 허브에 부하가 집중되지 않도록 트래픽을 분산시키는 역할을 합니다. 마지막 방법은 서버 앞단에 HTTPS를 제공하는 CDN을 두는 것입니다. CDN은 물리적으로 떨어져있는 사용자에게 컨텐츠를 더 빠르게 제공할 수 있는 기술이며 웹사이트 보안 개선의 장점을 가지고 있습니다. 이 세 가지 방법을 통해 HTTPS를 구축하여 안정화된 데이터 통신을 가능하게 합니다.

### 가장 많이 쓰이는 HTTP/1,1에는 HTTP/1.0에서는 표준화 되지 않았던 keep-alive가 기본 동작으로 채택되었습니다. keep-alive에 관해 설명해 주세요. (p.s HTTP/1.0에서는 keep-alive 였지만, 이를 HTTP/1.1에서 채택하면서 Persistence Connection(지속 연결)이라는 용어로 부르고 있습니다.)

keep-alive는 HTTP/1.1에서 채택하면서 Persistent Connection이라는 용어로 사용되고 있습니다. persistent connection은 서버에 연속적으로 동일한 클라이언트가 여러 요청을 보낼 가능성이 높은 경우가 계속됨에 따라 HTTP 어플리케이션이 TCP connection을 요청마다 close하지 않고 재사용할 수 있는 방법을 제공하는, 즉 요청이 처리된 후에도 connection을 유지하는 경우를 말합니다. persistent connection을 사용하게 되면 3-way handshake를 매 요청마다 맺을 필요가 없어지므로 네트워크 혼잡 감소, 네트워크 비용 감소, latency 감소의 장점이 있습니다.

---

## yeop222

### 허프만 코딩에 대해 설명해주세요.

허프만 코딩은 문자의 빈도 또는 확률정보를 이용해 통계적 압축하는 방법입니다. 텍스트에서 문자가 출현하는 빈도수에 따라 다른 길이의 부호를 부여합니다. 원본 데이터에서 자주 출현하는 문자는 적은 비트의 코드로 변환하여 표현하고 출현 빈도가 낮은 문자는 많은 비트의 코드로 변환하여 표현함으로써 전체 데이터를 표현하는데 필요한 비트 수를 줄이는 방식입니다. 이 압축 과정에서 가장 중요한 부분이 각 문자를 표현하기 위한 허프만 트리를 구성하는 것입니다.

### 사이퍼 슈트에 대해 설명해주세요.

사이퍼 슈트는 TLS 핸드쉐이크를 통해서 클라이언트/서버 간 최종 협의하게 되는데, 여기에는 어떤 프로토콜을 사용할 지, 어떻게 암호화하여 통신할 지에 대한 여러가지 정보가 포함되게 됩니다. 결론적으로 사이퍼 슈트는 프로토콜, AEAD 사이퍼 모드, 해싱 알고리즘이 나열된 규약을 말합니다.