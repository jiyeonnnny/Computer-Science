# CPU Scheduling
---
## 1. 스케줄링
- CPU를 잘사용하기 위해서 process를 잘 배정해야함. 그 배정하는 기준
- CPU 효율적으로 썼다
  - overhead 감소
  - 사용률 증가
  - 기아 현상 감소
 
- 목표
    1. Batch System : 가능하면 많은 일을 수행함. 시간보다 처리량을 중시
    2. Interactive System : 빠른 응답 시간. 적은 대기 시간
    3. Read-Time System : 기한(deadline) 맞추기

<br>
<br>

## 2. 선점 / 비선점 스케줄링
- 선점(preemptive) : 운영체제가 CPU의 사용권을 선점할 수 있게 강제로 회수하는 경우(처리시간 예측 어려움)
- 비선점(nonpreemptive) : 프로세스 종료 혹은 I/O 등의 이벤트가 있을때까지 실행을 보장함(처리시간 예측 용이함)

<br>
<br>

## 3. 프로세스 상태
![image](https://github.com/jiyeonnnny/Computer-Science/assets/139419091/43d1cf37-ac18-43fa-ba57-6ac9915abad3)
- 선점 스케줄링 : interrupt, I/O or Event Completion, I/O or Event Wait, Exit
- 비선점 스케줄링 : I/O or Event Wait, Exit

<br>

프로세스 상태 전이   
- 승인(admitted) : 프로세스 생성이 가능를 확인하고 승인함
- 스케줄러 디스패치(Scheduler Dispatch) : 준비상태에 있는 프로세스 중 하나를 선택하여 실행
- 인터럽트(Interrupt) : 예외, 입출력, 이벤트 등이 발생하여 현재 실행 중인 프로세스를 대기 상태로 바꾸고, 해당 작업을 먼저 처리함
- 입출력 또는 이벤트 대기(I/O or Event wait) : 실행 중인 프로세스가 입출력이나 이벤트를 처리해야 하는 경우, 입출력/이벤트가 모두 끝날 때까지 대기 상태로 만드는 것
- 입출력 또는 이벤트 완료 : 입출력/이벤트가 끝난 프로세스를 대기상태로 전환해서 스케줄러에 의해 선택될 수 있게 함

<br>
<br>

## 4. CPU 스케줄링 종류
 - 비선점 스케줄링
   1. FCFS(First Come First Served)
     - 큐에 도착한 순서대로 CPU에 할당
     - 실행 시간 짧은 게 뒤로 가면 평균 대기 시간이 길어짐
   2. SJF(Shorted Job First)
     - 수행시간이 가장 짧은 작업을 먼저 수행
     - FCFS보다 평균 대기 시간 감소, 짧은 작업에 유리
   3. HRN(Hightest Response-ratio Next)
     - 우선순위를 계산해서 점유 불평등을 보완(SJF의 단점 보완)
     - 우선순위 = (대기시간 + 실행시간)/(실행시간)
  
<br>

 - 선점 스케줄링
   1. Priority Scheduling
      - 정적/동적으로 우선순위를 부여하여 우선순위가 높은 순서대로 처리함
      - 단점 : 우선 순위가 낮은 프로세스가 무한정 기다리는 starvation이 생길 수 있음
      - 단점 보완 : Aging 방법으로 Starvation 문제 해결 가능
 
   2. Round Robin(이해부족)
      - FCFS 순으로 프로세스를 보내면, 각 프로세스는 동일한 time quantum(시간할당)만큼 CPU할당을 받음
      - time Quantum or time slice : 실행의 최소 단위 시간
      - 할당 시간( time quantum )이 크면 FCFS와 같게 되고, 작으면 context switching이 잦아져 오버헤드 증가함

   3. Multilevel-Queue
  
      - 다단계 큐
      - 작업들을 여러 종류의 그룹으로 나눠 여러개의 큐를 이용하는 기법
      - 우선순위가 낮은 큐를 실행하지 못할 수 있음
      - 각 큐마다 다른 시간 할당을 설정해주면 단점을 보완할 수 있음
      - 우선순위가 높은 큐는 작은 시간할당으로 설정하고, 우선순위가 높은 큐는 큰 시간할당으로 설정함
     

   4. Multilevel-Feedback-Queue
      - 다단계 피드백 큐
      - 다단계 큐에서 자신의 시간할당을 다 채운 프로세스는 밑으로 내려가고, 자신의 시간할당을 채우지 못한 프로세스는 원래 큐 그대로 남아있음
      - 시간 할당을 다 채운 프로세스는 CPU burst 프로세스로 판단하기 때문임
      - 짧은 작업에 유리하고, 입출력 위주(인터럽트가 잦은) 작업에 우선권을 줌
      - 처리시간이 짧은 프로세스를 먼저 처리해서 Turnaround 평균 시간을 줄여줌

<br>
<br>

5. CPU 스케줄링 척도
  1. Response time : 작업이 처음 실행되기까지 걸린 시간
  2. Turnaround time : 실행시간과 대기시간을 모두 합한 시간, 작업이 완료될때까지 걸리는 시간을 의미함


<br>
<br>
