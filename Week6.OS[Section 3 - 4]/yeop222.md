## KJS

###  메모리 할당 방식 중 비연속 할당과 구체적인 기법들에 대해 설명해 주세요.

 비연속 할당은 프로세스가 물리적인 메모리에 연속적으로 할당하지 않는 방식을 뜻한다. 연속적으로 할당하지 않기 떄문에 메모리가 프로세스의 크기와 상관없이 여러 조각으로 나눠어져 할당할 수 있다.
	
페이징: 동일한 크기의 페이지 단위로 물리적 메모리, 논리적 메모리로 나누어 메모리의 서로 다른 위치에 프로세스를 할당하는 기법

세그멘테이션: 논리적인 단위인 세그먼트로 나누는 방식. 프로세스는 코드, 데이터 등으로 이루어지는데, 코드와 데이터 등 을 기반으로 나눈 수도 있고 함수 단위로도 나눌 수 있다.

### 페이지 교체 알고리즘에 대해 설명해주세요.

스와핑이 일어날때 사용되는 것이 페이지 교체 알고리즘이다. 
	FIFO(First-In-First-Out): 가장 먼저 온 페이지를 먼저 교체하는 알고리즘
	LRU(Least Recently Used): 최근에 사용되지 않은 페이지를 교체하는 알고리즘
	LFU(Least Frequently Used): 최근에 사용 빈도가 가장 적은 페이지를 교체하는 알고리즘
	

---

## hyewon

### 지역성이 무엇인지 설명해주세요.

지역성은 데이터 처리 시 특정 지역에 대한 접근성을 나타내는 개념으로 공간 지역성과 시간 지역성으로 나뉜다.
	1. 공간 지역성: 최근 접근한 데이터를 이루고 있는 공간이나 가까운 공간에 접근하는 특성을 뜻한다.
	2. 시간 지역성: 최근 사용한 데이터를 다시 접근하려는 특성을 뜻한다.

### 가상 메모리가 필요한 이유에 대해서 설명해주세요.

가상 메모리는 실제 물리적인 RAM보다 큰 메모리 공간을 사용하는 개념이다. 가상 메모리가 있으면 RAM의 한계를 초과한 크기의 프로그램들을 실행 할 수 있다. 또한 가상 메모리는 프로그램의 필요한 부분만 필요한 시점에 메모리에 로드하여 효율적인 실행을 하도록 도와준다.

---

## MIZ

### 컨텍스트 스위칭의 과정에 대해 설명해주세요.

1.현재 프로세스의 상태를 저장한다.
2. 새로은 프로세스의 상태를 로드한다.
3. 커널 스케줄러에 의해 제어권을 이전한다.

### 스레드와 멀티스레딩에 대해 설명해 주세요

스레드: 프로세스 내에서 동작하는 실행 단위. 프로세스의 자원을 공유하며 실행됨.
멀티스레딩: 여러 스레드가 동시에 실행되는 것을 뜻함.
