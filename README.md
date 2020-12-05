# 프로세스와 스레드

### 프로세스란
- 프로세스는 실행 중인 프로그램으로 디스크로부터 메모리에 적재되어 CPU의 할당을 받을 수 있는 상태
- 운영체제로부터 
    - 함수의 매개변수, 복귀주소와 로컬 변수와 같은 임시적인 자료를 가지는 프로세스 스택
    - 전역 변수들을 수록하는 데이터 섹션
    - 프로세스 실행 중 동적으로 할당되는 힙
- 실행 파일이 메모리에 적재될 때 프로세스가 됨

### 프로세스 제어 블록 (PCB, Process Control Block)
- 각 프로세스는 프로세스 제어 블록에 의해 표현된다
- PCB는 특정 프로세스에 대한 중요한 정보를 나타내는 운영체제의 자료구조
- 단순하게, 프로세스마다 달라지는 모든 정보 저장하며 프로세스의 생성과 동시에 고유한 PCB가 생성됨.
- 프로세스는 CPU를 할당받아 작업을 처리하다가도 프로세스 전환이 발생하면 진행하던 작업을 저장하고, CPU를 반환하는데 이 때 작업의 진행 상황을 모두 PCB에 저장

- PCB에 저장되는 정보
    - 프로세스 식별번호(PID, Process ID)
    - 프로세스 상태 : new, ready, running, waiting, halted 상태 등..
    - 프로그램 카운터 : 해당 프로세스 다음에 실행할 명령어의 주소
    - CPU 레지스터들 : 컴퓨터의 구조에 따라 다양한 수와 타입을 가짐
    - CPU 스케쥴링 정보 : 프로세스의 우선순위, 스케줄 큐에 대한 포인터
    - 메모리 관리 정보 : 페이지 테이블 또는 세그먼트 테이블 등과 같은 정보 포함
    - 입출력 상태 정보 : 프로세스에 할당된 입출력 장치들과 열린 파일 목록
    - 어카운팅 정보 : 사용된 PCU시간, 경과된 시간 등..
    
### 스레드란 (Thread)
- 한 프로세스 내에서 동작되는 여러 실행 흐름
- 프로세스 내의 주소 공간이나 자원 공유 가능
- 스레드 구성
    - 스레드 ID, 프로그램 카운터, 레지스터 집합, 스택

- **스택을 스레드마다 독립적으로 할당하는 이유**
    - 스택은 함수 호출 시 전달되는 인자, 되돌아갈 주소 값 및 함수 내에서 선언하는 변수 등을 저장하기 위해 사용되는 메모리 공간으로 스택 메모리 공간이 독립적이여야 독립적인 함수 호출이 가능

- **PC Register를 스레드마다 독립적으로 할당하는 이유**
    - PC값은 스레드가 명령어의 어디까지 수행하였는지를 나타냄
    - 스레드는 CPU를 할당 받았다가 스케쥴러에 의해 잠시 뻇긴다. 
    - 추후에 어느 부분부터 수행해야 하는지 기억을 위해 독립적으로 할당
    
    