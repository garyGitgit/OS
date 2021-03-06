### Part2_1 Process

* 프로세스: 실행되는 프로그램
* 프로그램은 디스크에 저장 되어 있는 수동적은 개체, 프로세스는 액티브한 개체
* 프로그램이 메모리에 로드되어지면 프로세스가 될 수 있음
### Process in Memory

* Text: PC와 레지스터가 있는 공간
* Stack: 일시적으로 저장할 수 있는 데이터 -> 함수 호출, 로컬 변수, 함수 파라미터
* Data: 글로벌 변수
* Heap: malloc이나 자바 객체 선언처럼 동적으로 메모리를 할당 시켜줄 수 있는 장소
### Process State

* New: 프로세스가 만들어짐
* Running: CPU에 의해 명령이 실행됨 -> 오직 하나의 프로세스만 러닝 상태로 들어갈 수 있다.
* Waiting: 어떤 이벤트가 일어나기를 기다리는 상태
* Ready: CPU에 할당되기를 기다리는 프로세스들의 상태
* PCB: Process에 대한 정보들이 저장되어 있는 곳
### Process Management
* 그러므로 OS는 각 프로세스의 현재 상태를 관리 해야할 필요가 있다.
### Context Switching
CPU에 탑재될 프로세스를 바꾸는 것 -> 바꿀 때마다 System Call이 필요
### Process Scheduling
CPU에 탑재할 프로세스들의 순서를 정함으로써 CPU활용도를 최대화
### Ready Queue
메인 메모리에 있거나 실행되어지길 기다리는 프로세스들이 있는 큐
### Device Queue
* 특정 I/O연산을 기다리고 있는 Process들의 큐
* 처음에 러닝 상태에서 돌고있던 프로세스가 I/O연산이 필요하게 되면 I/O 연산이 끝날 때까지 디바이스 큐에 잔류. 끝나면 레디큐로 넘어가 디스패치 되기를 기다린다.
### Long term Scheduler – Job scheduler
디스크에 있는 어떤 프로세스가 레디큐에 들어 갈지 결정 하는 것
### Short term Scheduler – CPU scheduler
* 레디큐에서 어떤 프로세스가 CPU에 들어갈 지 결정하는 것
* 멀티 프로그래밍 정도에 따라서 많이 달라진다 – Long term scheduler
* I/O 바운드 프로세스: 연산보단 I/O작업에 더 많이 시간을 투자하는 것
* CPU 바운드 프로세스: 연산에 더많은 시간을 투자하는 것

### Context Switch
CPU가 다른 프로세스들로 스위치 할 때, 그 시스템은 예전 프로세스들의 상태를 저장 해야할 필요가 있고 컨텍스트 스위치를 통해 새로운 프로세스의 저장된 상태를 로드 해야한다.<br>
But context switch는 시간이 오래 걸리는 작업이다. 컨텍스트 스위치 수를 줄이는 것도 중요

### Part2_2 Process
* 프로세스들은 다이나믹하게 만들어지거나 지워진다.
* Wait()-> Child process들의 연산이 다 끝날 때까지 기다리는 것
* Fork()->Child process를 만드는 것, 트리 형식으로 이어진다.
* 각 프로세스들은 서로 다른 메모리 영역이 있으므로 wait()을 한다고 해도 패런트 프로세스가 가진 Data영역은 변하지 않는다.
### IPC (프로세스 간의 통신)
* OS가 서로에게 필요한 데이터 통신을 하게 해준다.
* 시스템 보호 상 어떤 프로세스가 다른 프로세스의 메모리에 함부로 접근할 수 없으므로 운영체제를 통해서 서로 데이터를 통신할 수 있게끔 해준다.
### IPC 방식
Message Passing, Shared Memory방식으로 동기화를 맞춘다.
### Producer-Consumer Problem
간단히 말해서 생산되지 않은 정보를 소비해서는 안되는 것
### Message Passing
* 메시지를 주고 받기 위해서 그들간의 커뮤니케이션 링크를 설립하고 메시지를 교환한다.
* 커뮤니케이션 링크의 속성
* 링크는 자동적으로 설립된다.
* 링크는 정확히 한 쌍의 프로세스들끼리 연관되어 있다.
* 각 쌍 사이에 정확히 하나의 링크가 있다.
