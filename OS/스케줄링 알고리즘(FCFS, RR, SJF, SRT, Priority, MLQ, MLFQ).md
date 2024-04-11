# 스케줄링 알고리즘

## 스케줄링 성능 척도

1. 시스템 입장에서의 성능 척도
   - CPU 이용률 (CPU Utilization) : 전체 시간 중 CPU가 쉬지 않고 일한 시간
   - 처리량 (Throughput) : 단위 시간당 수행 완료한 프로세스의 수
2. 프로그램 입장에서의 성능 척도
   - 소요 시간 : 프로세스가 Ready queue에서 대기한 시간부터 작업을 완료하는데 걸리는 시간
   - 대기 시간 : 프로세스가 Ready queue에서 대기한 시간
   - 응답 시간 : 프로세스가 처음으로 CPU를 할당받기까지 걸린 시간
     => 프로그램 입장에선 소요, 대기, 응답 시간이 모두 최소가 될수록 좋고 시스템 입장에선 CPU 이용률과 처리량이 모두 최대가 될수록 좋음

## FCFS 스케줄링(First Come First Served Scheduling)

- CPU에 먼저 도착하는 순서대로 프로세스를 할당해주는 방식
- Non-Preemptive 방식 → 각 작업이 종료될 때까지 CPU를 빼앗지 않음
- Convoy Effect → 하나의 긴 프로세스로 인해 나머지 프로세스가 오래 기다리게 되어 CPU 효율성이 낮아지는 문제점

## 최단 작업 우선 스케줄링(SJF, Shortest Job First Scheduling)

- 프로세스의 수행 시간이 짧은 순서대로 CPU에 할당함
- Convoy Effect를 해결하기 위한 방식
- 주어진 프로세스에 대해 최소의 평균 대기 시간을 보장함 → 최적임이 보장됨
- 기아 현상 발생 가능성 O → 수행시간이 긴 프로세스는 계속 뒤로 밀려남
- Non-preemptive와 preemptive 방식 존재 → 새로운 프로세스가 도착했을 때, 현재 남아있는 작업 중 가장 빨리 끝나는 작업부터 CPU를 할당해주는 Preemptive 방식을 이용하면 평균 대기 시간을 더 줄일 수 있음

## 라운드 로빈 스케줄링(Round Robin Scheduling)

- 각 프로세스가 주로 10 ~ 100ms의 동일한 크기의 할당 시간을 갖으며 할당 시간이 끝나면 프로세스는 자동으로 선점 당하고, Ready queue의 제일 뒤에 가서 다시 줄을 섬
- 기아 현상 발생 가능성 X
- 응답 시간 빠름
- 적절한 할당 시간 배정하는 것이 중요 → 할당 시간 q가 클수록 FCFS의 방식과 유사하고, q가 작을수록 컨텍스트 스위치의 오버헤드가 커지기 때문

## 우선순위 스케줄링(Priority Scheduling)

- 특정 기준으로 프로세스에게 우선순위를 부여해 우선순위가 제일 높은 프로세스에게 CPU를 할당하는 방식
- 숫자가 작으면 우선순위가 높음
- 기아 현생 발생 가능성 O → 우선순위가 낮은 프로세스가 계속해서 수행되지 않음 → 에이징 기법을 통해 해결 → 시간이 지날수록 오래 대기한 프로세스의 우선순위를 높이는 방식
- Non-preemptive와 preemptive 방식 존재

## SRT 스케줄링(Shortest Remaining Time Scheduling)

- 최단 잔여시간을 우선으로 하는 스케줄링
- 진행 중인 프로세스가 있어도, 최단 잔여시간인 프로세스를 위해 sleep 시키고 짧은 프로세스를 먼저 할당

## 다단계 큐 스케줄링(MLQ, MultiLevel Queue Scheduling)

- Ready Queue를 여러 개로 분할한 것
- 각 큐는 독립적인 스케줄링 알고리즘을 가짐
- Foreground 작업을 먼저 다 수행한 후, Background 작업을 수행하는 고정된 우선순위 스케줄링을 이용할 수 있음 → 기아 현상 발생 가능성 O
- 각 큐에 CPU Time을 적절한 비율로 할당하는 Time slice 방식을 사용할 수도 있음

## 다단계 피드백 큐 스케줄링(MLFQ, MultiLevel Feedback Queue Scheduling)

- 프로세스가 큐들 사이에서 이동할 수 있는 성질이 추가된 것
- 우선순위를 부여해서 에이징 기법을 통해 구현
- 기아 현상 해결 O

---

> 참고

- https://rebro.kr/175
- https://hyunah030.tistory.com/4
