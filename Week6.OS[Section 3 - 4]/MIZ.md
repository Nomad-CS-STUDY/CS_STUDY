## Hyewon

### 지역성이 무엇인지 설명해주세요.

지역성이란 기억장치 내의 정보를 균등하게 접근하는것이 아닌 한 순간에 특정 부분을 집중적으로 참조하는 특성입니다. 데이터에 대한 접근이 시각적/공간적으로 가깝게 발생하는것입니다. 시간적 지역성은 특정 데이터가 한번 참조된 경우, 가까운 미래에 또 한번 참조될 가능성이 높은것이고 공간적 지역성은 특정 데이터와 인접한 주소의 데이터가 참조될 가능성이 높은것을 의미합니다.


### 가상메모리가 필요한 이유에 대해서 설명해주세요.

가상 메모리란 프로그램을 실행시키는데 얼마만큼의 메모리가 필요한지 판단하여 실행에 필요한 일부분만 메모리에 로드하고 나머지는 디스크에 두고 필요할 때 교체하면서 쓰는 방식입니다. 이를 통해 메모리의 크기의 제약으로부터 자유로워 질수 있고 더 많으  프로그램을 동시 수행할수 있습니다. 


---

## js

### 메모리 할당 방식 중 비연속 할당과 구체적인 기법들에 대해 설명해 주세요.

비연속 메모리 할당은 프로그램의 코드가 메모리에 비연속적으로 할당되는 방식을 의미합니다.
그 중 세그먼테이션 기법은 동일하지 않은 크기로 주 기억장치와 프로세스를 분할하는 방식입니다. 
분할된 프로세스 조각을 Segmentation 이라 부르고 Segmentation 기법은 하나의 세그먼트가 하나 이상의 파티션을 차지할 수 있고 파티션들이 연속적일 필요가 없습니다. 

Reference: https://lordofkangs.tistory.com/211


### 페이지 교체 알고리즘에 대해 설명해주세요.

운영체제는 주기억장치보다 더 큰 용량의 프로그램을 실행하기 위해 프로그램의 일부만 적재하여 사용합니다, 이를 가상 메모리기법이라 하고 페이징기법으로 메모리를 관리하는 운영체제에서 필요한 페이지가 주 기억장치에 적재되지 않았을 시 어떤 페이지 프레임을 선택하여 교체할 것인지 결정하는 방법을 페이지 교체 알고리즘이라고 합니다.

Reference: https://doh-an.tistory.com/28


---

## yeop222

### L1, L2, L3 캐시에 대해 설명해주세요.

CPU에는 캐시 메모리가 2-3개 정도 사용되고 이를 L1,L2,L3 캐시 메모리라고합니다. L은 Level을 의미하고 속도와 크기에 따라 분류됩니다. L1캐시는 일반적으로 CPU칩안에 내장되어 데이터 사용/참조에 가장 먼저 사용됩니다. 여기서 데이터를 찾지 못하면 L2 캐시 메모리로 넘어갑니다. L2 캐시 메모리는 용도와 역할은 L1 캐시와 비슷하지만 속도는 그보다 느리고 L2 캐시는 CPU 회로판에 별도의 칩으로 내장된다. 앞서 말한대로 L1 캐시를 먼저 뒤지고, L2 캐시를 뒤져 데이터를 찾습니다. L3도 동일한 원리로 작동됩니다. L1/L2 캐시 메모리 정도만 CPU 성능에 직접적인 영향을 미치기에 L3 캐시는 크게 신경쓰지 않는것이 일반적인 추세입니다.

### 스레싱을 해결하는 방법에 대해 설명해주세요.


Working set

지역성의 원리를 이용하여 지역성 집합이 메모리에 동시에 올라갈 수 있도록 보장하는 메모리 관리 방법입니다.

워킹셋이라는 이름과 같이 프로세스의 작업을 구성하는 자주 참조되는 페이지들을 묶는다고 생각할수 있고 해당 워킹셋의 합인 전체 프레임이 할당된 페이지 프레임보다 크게되면 Thrashing이 발생하게 됩니다.


Page Fault Frequency(페이지 부재 빈도)

프로세스의 페이지 부재율을 주기적으로 조사하고 이 값에 근거하여 각 프로세스에 할당할 메모리 양을 동적으로 예측하고 조절하는 알고리즘입니다. 현재 페이지 부재와 직전 페이지 부재 사이의 시간을 관찰하여 상한 값(upper bound)을 초과하거나 하한 값(lower bound) 미만이 되면 운영체제가 메모리에 올라가 있는 프로세스의 수를 조절합니다.
