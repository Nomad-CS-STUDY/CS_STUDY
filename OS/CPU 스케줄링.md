# CPU 스케줄링

## CPU 스케줄러

- 어떤 프로세스에게 자원을 할당할지 결정하는 운영체제 커널의 모듈

## CPU 스케줄링

- 스케줄러를 통해 CPU를 사용하려고 하는 프로세스 사이의 우선 순위를 관리
- 프로세스에게 언제, 얼마나 시간과 자원을 할당해줄지 조율하는 것
- CPU 자원을 효율적으로 사용하기 위해 커널이 프로세스를 스케줄링함
- 어떤 프로세스에게 CPU를 줄 것인가, 언제 뺏을 것인가의 이슈들이 중요함

## CPU 스케줄링의 목적

- CPU 이용률 최대화
- 처리량 최대화
- 총 처리 시간 최소화
- 대기 시간 최소화
- 응답 시간 최소화

## CPU 스케줄링이 언제 필요할까?

<div align=center>
    <img src="../assets/CPU scheduling.png" width="600"/>
</div>

| 생성(NEW) | 프로세스가 생성되고 아직 준비가 되지 않은 상태 |
| 준비(Ready) | 프로세스가 실행을 위해 기다리는 상태 |
| 실행(Running) | 프로세스가 CPU를 할당받아 실행되는 상태 |
| 대기(Waiting) | 프로세스가 특정 이벤트가 발생하여 대가하는 상태 |
| 종료(Terminated) | 프로세스가 실행을 완료하고 종료된 상태 |

1. Running → Waiting(Blocked)

- I/O 요청이나 자식 프로세스들 중의 하나가 종료되기를 기다리기 위해 wait를 호출할 때 (ex I/O 같이 오래걸리는 작업을 하러 간 경우, I/O 요청하는 시스템 콜)

2. Running → Ready

- 계속 CPU 쓰고 싶은데 너무 오래 갖고 있어서 CPU를 빼앗길 때 (ex 할당 시간 만료로 timer interrupt)

3. Waiting → Ready

- CPU를 얻을 수 있는 권한을 다시 줄 때 / priority에 기반한 스케줄링을 할 때 I/O를 하러 갔던 프로세스가 우선순위가 가장 높은 프로세스라면 I/O가 끝나자마자 CPU를 가지게 됨 (ex I/O 완료 후 interrupt)

4. Running → Terminate

=> 1, 4는 강제로 빼앗지 않고 자진반납하는 경우 (Non-preemptive 비선점)
=> 2, 3은 계속 쓰고 싶은데 강제로 빼앗기는 경우 (preemptive 선점)

## 비선점 스케줄링 vs 선점 스케줄링

비선점 스케줄링

- 한 프로세스가 CPU를 할당 받으면 다른 프로세스에 CPU 할당 불가능
- CPU를 다 쓰고 나갈 때까지 CPU를 보장함
- 협조적임
- 스케줄러의 작업량이 적고 문맥 교환 오버헤드가 작지만, 처리율이 떨어짐
- 일괄 작업 방식 스케줄러(FCFS, SJF, Priority)

선점 스케줄링

- 현재 실행 중인 프로세스를 밀어내고 더 우선 순위가 높은 프로세스를 스케줄링
- 문맥 교환 오버헤드가 많음
- 공유 메모리를 사용할 경우, 이전 프로세스 데이터 내용을 선점된 프로세스가 영향을 줄 수 있으므로 조정에 필요한 비용을 유발함
- 커널 프로세스 선점으로 생기는 경쟁을 통해 커널의 데이터 보안 문제가 발생함
- 시분할 방식 스케줄러(RR, SRT, 다단계 큐, 다단계 피드백 큐)

---

> 참고

- https://cocoon1787.tistory.com/123
- https://velog.io/@evergreen_tree/OS-%EC%8A%A4%EC%BC%80%EC%A4%84%EB%9F%AC
- https://today-studies.tistory.com/22
- https://velog.io/@mimmimmu/OS-CPU-Scheduling-1
- https://inpa.tistory.com/entry/%F0%9F%91%A9%E2%80%8D%F0%9F%92%BB-%ED%94%84%EB%A1%9C%EC%84%B8%EC%8A%A4-%E2%9A%94%EF%B8%8F-%EC%93%B0%EB%A0%88%EB%93%9C-%EC%B0%A8%EC%9D%B4#%ED%95%9C%EB%88%88%EC%97%90_%EC%9D%B4%ED%95%B4%ED%95%98%EB%8A%94_%ED%94%84%EB%A1%9C%EC%84%B8%EC%8A%A4__%EC%8A%A4%EB%A0%88%EB%93%9C_%EA%B0%9C%EB%85%90
- [이미지 출처](https://cocoon1787.tistory.com/123)
