## IPC(Inter Process Communication)

프로세스는 독립적으로 실행된다.
이처럼 독립적인 공간을 가진 프로세스 간 통신에 사용되는 기법이 IPC 통신이다.
프로세스는 커널이 제공하는 IPC 설비를 이용해 프로세스 간의 통신을 할 수 있게 된다.

---


IPC의 대표적인 방법(모델)은 메세지 전달방식과 공유 메모리 방식이 있다.

### 1.Shared Memory model

협력 프로세스 간 공유되는 메모리를 생성 후 이를 이용하여 정보를 교환한다. 데이터의 형식과 위치는 프로세스들에 의해 결정되며 운영체제 소관은 아니다 (커널의 도움이 거의 필요 없다). 주로 전역 변수, 공유 변수, 공유 파일을 통해 통신을 이룬다.


성능은 좋지만 프로세스간의 동기화 문제가 발생하여 어플리케이션에서 직접 동기화를 해야한다. (충돌 가능성이 있다.)

- Shared Memory model에는 producer 프로세스와 consumer 프로세스가 있다.
- 공유 메모리(버퍼)를 통해 동시에 (concurrently) 통신한다.
- 생산자가 item을 생산하고 buffer에 저장하면, 소비자는 buffer의 item을 소비한다.
- 가용한 항목이 있을 때만 소비가 이루어지도록, 생산자/소비자 간의 프로세스는 동기화되어야 한다.


### 2. Messaging Passing Model
![message passing](https://github.com/Nomad-CS-STUDY/CS_STUDY/assets/71619429/854820d2-42fd-4fe6-b650-843c163adcea)

OS가 프로세스 간 통신 방법을 제공하고, 메세지를 대리 전달해준다. OS가 동기화를 해주기 때문에 안전하고 동기화 문제가 없으나, 시스템 콜을 사용하기 때문에 성능이 떨어진다. 

분류
Direct vs Indirect


Direct :
프로세스들은 서로의 이름을 명시한다. 한 쌍에는 하나의 링크만 존재하고, 1대 1통신에 사용된다.

send(P, message): P로 메시지를 보내라

receive(Q, message): Q로부터 메시지를 받아라.

Indirect:

메세지들이 mailbox(port)를 이용하여 send와 receive가 이루어진다. 각 mailbox는 고유의 id를 가진다.
-send(A, message) : mailbox A 로 메시지를 보내라.
-receive(A, message): mailbox A로부터 메시지를 받아라.
따라서 여러 프로세스가 mailbox를 공유할 수 있다.

Synchronization (동기화) / Blocking
- Blocking send : 송신자는 수신자가 메시지를 받을 때까지 blocked 되는 것
- Non-blocking send : 송신자는 메시지를 보내고 자기 할 일 하는 것
- Blocking receive : 수신자는 메시지가 모두 다 받을 때까지 blocked 되는 것
- Non-blocking receive : 수신자가 메시지가 왔는지 수시로 검사하는 것 (the receiver retrieves either a valid message or a null message )

### IPC의 종류
#### PIPE (파이프)
![pipe](https://github.com/Nomad-CS-STUDY/CS_STUDY/assets/71619429/c1c2f8a6-35b3-4aed-8771-127ef2d8738d)

- 파이프는 두 개의 프로세스를 연결하고 하나의 프로세스는 데이터를 쓰기만 하고, 다른 프로세스는 데이터를 읽기만 한다
- 부모 자식 간에 단방향 통신으로 자주 사용한다
- 한쪽 방향으로만 통신이 가능한 PIPE의 특징 때문에 Half-Duplex(반이중) 통신 이라고도 불린다
- PIPE는 반이중 통신이기에 하나의 통신선로는 읽기/쓰기 중 하나만 가능하므로 만약 읽기/쓰기, 즉 송/수신을 모두 하기 원한다면 두 개의 파이프를 만들어야 가능하다
- read()와 write()가 기본적으로 block mode로 작동되기에 프로세스가 read 대기중이라면 read가 끝나기전에는 write를 할 수 없다


#### Message Queues

![message queue](https://github.com/Nomad-CS-STUDY/CS_STUDY/assets/71619429/4897ec1a-65f4-4292-b93a-754c82d82ed9)

- 메모리를 사용한 pipe이며, 구조체를 기반으로 통신(stream X)한다.
- 메세지 타입(msgtype)에 따라 구조체(데이터?) 종류를 다르게 받을 수 있으며, 여러 프로세스가 동시에 데이터를 다룰 수 있다.
- 커널에서 제공하기 때문에 메모리 제한이 있을 수 있다.

- Shared Memory
위 참고

#### Memory Map
- 공유 메모리처럼 메모리를 공유하지만, 메모리 맵은 열린 파일을 메모리에 매핑시켜서 공유하는 방식이다. (파일 + 메모리)
- 주로 파일로 대용량 데이터를 공유해야할 때 사용한다.

#### Client - Server System
Socket
- 네트워크 소켓 통신을 이용하여 데이터를 통신한다. pipe 개념을 네트워크로 확장시킨 것이다.
원격에서 프로세스 간의 데이터를 공유할 때 사용한다.
- 네트워크 프로그래밍이 가능해야하며, 데이터 세그먼트 처리를 잘해야한다.

---

RPC (Remote Procedure Call) - 중요x
원격지 프로세스 간에 함수의 호출에 기반을 둔 기법이다.

RPC 서버에 함수가 실제로 구현이 되어있고 클라이언트의 코드에서 함수를 호출하면 서버에 있는 함수가 실행되는 형태를 띈다. 서버와 클라이언트 간에는 Stub이라는 것을 이용해 서로 네트워크를 연결한다.

LPC (Local Procedure Call)은 동일 시스템내에서 호출 기법을 말한다.
