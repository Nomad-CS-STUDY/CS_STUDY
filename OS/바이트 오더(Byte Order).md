# 바이트 오더(Byte order)

![1](https://github.com/Nomad-CS-STUDY/CS_STUDY/assets/135118163/95befea8-9a98-472e-9479-5a96ace23eba)

## 바이트 오더란?
컴퓨터는 데이터를 메모리에 저장할 때 바이트(byte) 단위로 나눠서 저장합니다. 하지만 컴퓨터가 저장하는 데이터는 대게 32비트(4바이트)나 64비트(8바이트)로 구성됩니다. 따라서 이렇게 연속되는 바이트를 순서대로 저장하는데, 이를 바이트 저장 순서(byte order)라고 합니다. 
## 엔디안(Endianness)
한국어는 왼쪽에서 오른쪽으로 읽고 아랍어는 오른쪽에서 왼쪽으로 읽는 것처럼, 언어마다 텍스트를 다른 순서로 읽습니다. 이처럼 엔디안은 컴퓨터가 텍스트를 어떠한 순서로 읽을 것인지에 관한 규칙입니다. 즉 엔디안은 바이트 저장 순서(byte order)를 결정하는 규칙으로, 컴퓨터 메모리의 바이트가 특정 순서로 읽혀지는 것을 의미합니다. 엔디안의 주요 형태로는 빅 엔디안(big endian)과 리틀 엔디안(little endian) 두 가지 방식이 있습니다.

### 빅 엔디안(big endian)
- 주소 정렬 (Address Alignment): 빅 엔디안 방식에서는 가장 의미 있는 바이트(Most Significant Byte, MSB)가 낮은 주소에 위치합니다.
- 읽기 방식 (Reading Method): 숫자를 읽는 우리의 일반적인 방식과 동일하여, 메모리에 저장된 순서대로 읽으면 됩니다. 예를 들어, 0x1A2B3C4D라는 16진수를 메모리에 저장할 때 0x1A가 가장 낮은 주소에 위치합니다.
- 사용 사례 (Use Cases): 빅 엔디안은 네트워크 통신에서 데이터를 전송하거나 파일 저장 시에 주로 사용됩니다. 이는 데이터의 순서가 변하지 않기 때문에 다른 시스템 간의 호환성을 보장합니다.

### 리틀 엔디안(little endian)
- 주소 정렬 (Address Alignment): 리틀 엔디안 방식에서는 가장 의미 없는 바이트(Least Significant Byte, LSB)가 낮은 주소에 위치합니다.
- 읽기 방식 (Reading Method): 메모리에 저장된 데이터를 읽을 때는 역순으로 읽어야 합니다. 예를 들어, 0x1A2B3C4D라는 16진수를 메모리에 저장할 때 0x4D가 가장 낮은 주소에 위치합니다.
- 사용 사례 (Use Cases): 대부분의 인텔 x86 CPU 계열과 ARM 아키텍처에서는 리틀 엔디안 방식을 사용하여 데이터를 저장합니다. 이는 CPU가 데이터를 처리하는 데 있어 효율적이기 때문입니다.

## 빅 엔디안(big endian) VS 리틀 엔디안(little endian)
엔디언이라는 단어는 조너선 스위프트의 《걸리버 여행기》에 나오는 소인국 릴리퍼트 이야기에서 달걀을 깰 때 뭉툭한 끝(big-end)을 먼저 깨는 사람들(빅 엔디안)과 뾰족한 끝(little-end)을 먼저 깨는 사람들(리틀 엔디안)에서 유래했습니다. 이 두 그룹은 작은 쪽이든 큰 쪽이든 달걀을 어느 쪽에서 열어야 하는지에 대해 결론을 낼 수 없었습니다. 이 계란 문제와 마찬가지로 두 엔디안 사이에는 한 쪽을 누를만한 극명한 기술 우위가 존재하지 않기 때문에, 상황에 맞게 선택하면 됩니다.

---

> 참고
- https://www.tcpschool.com/c/c_refer_endian
- https://www.freecodecamp.org/news/what-is-endianness-big-endian-vs-little-endian/
- [그림출처](https://www.linkedin.com/posts/alexxubyte_systemdesign-coding-interviewtips-activity-7147631723344797696-1PXp)
