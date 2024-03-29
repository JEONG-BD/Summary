## Computer Architecture

### 4장 CPU의 작동원리   

### 4-03 명령어 사이클과 인터럽트     
- **명령어 사이클(Interuction Cycle)**
  - 우리가 실행하는 프로그램은 수많은 명령어로 구성
  - CPU는 이 명령어들을 하나씩 실행하며, 각각의 명령어들은 일정한 주기가 반복되며 실행되는데 이 주기를 명령어 사이클이라고 함
  - 인출 사이클(Fetch Cycle) 
    - 메모리에 저장된 명령어 하나를 실행할 때 명령어를 메모리에서 CPU로 가지고 오는 단계    
  - 실행 사이클(Execution Cycle)  
    - CPU로 명령어를 인출 했다면 명령어를 실행하는 단계
    - 제어장치가 명령어 레지스터에 담긴 값을 해석하고 제어 신호를 발생시키는 단계 
  - 간접 사이클(Indirect Cycle) 
    - 명령어를 인출하여 CPU로 가져왔다고 해서 바로 실행사이클에 돌입이 불가능
    - 명령어를 실행하기 위하여 메모리 접근을 한번 더 하는 단계
  ***
  
- **인터럽트(Interrupt)**
  - CPU가 수행 중인 작업은 방해를 받아 잠시 중단되는데 CPU의 작업을 방해하는 신호를 인터럽트라고 함
  - 인터럽트의 종류에는 크게 동기 인터럽트와 비동기 인터럽트로 구분
  - 동기 인터럽트(syschronous interrupt)
    - CPU에 의해서 발생하는 인터럽트
    - CPU가 명령어들을 수행하다가 예상치 못한 상황을 마주쳤을 때(CPU가 실행하는 프로그래밍상의 오류와 같은 예외적인 상황)
    - 동기 인터럽트를 예외라고 부름
    <br>
 
  - 비동기 인터럽트(asynchronous inerrupt)
    - 하드웨어 인터럽트라고 부름   
    - 입출력장치에 의해서 발생하는 인터럽트
    - CPU가 프린터와 같은 입출력 작업을 부탁하면 작업을 끝낸 입출력 장치가 CPU에 완료알림(인터럽트)를 보냄    

  - 하드웨어 인터럽트
    - 하드웨어 인터럽트는 알림과 같은 인터럽트
    - CPU는 입출력 작업 도중 효율적으로 명령어를 처리하기 위해 하드웨어 인터럽트를 사용
    - 하드웨어 인터럽트 처리순서
      - 입출력장치는 CPU에 __인터럽트 요청 신호__ 전송
      - CPU는 실행 사이클이 끝나고 명령어를 인출하기 전에 항상 인터럽트 여부 확인
      - CPU는 인터럽트 요청을 확인 하고 __인터럽트 플래그__ 를 통해 현재 인터럽트를 받아들일 수 있는지 여부 확인
      - 인터럽트를 받아들일 수 있으면 CPU는 지금까지의 작업 백업
      - CPU는 __인터럽트 벡터__ 를 참조하여 __인터럽트 서비스 루틴__ 실행
      - 인터럽트 서비스 루틴 실행 종료 후 백업해둔 작업 복구하여 실행 재개

    - 인터럽트 요청 신호
      - 인터럽트는 CPU의 정상적인 실행 흐름을 끊는 것이기에 인터럽트하기 전에 CPU에게 확인하는 것
        
    - 인터럽트 플래그
      - 인터럽트 플래그는 하드웨어 인터럽트를 받아들일지 무시할지 결정하는 플래그
      - CPU가 중요한 작업을 처리하거나 어떤 방해도 받지 않아야 할 때는 인터럽트 플래그는 불가능으로 설정
      - 인터럽트 플래그가 불가능으로 설정되어 있다면 CPU는 인터럽트 요청이 들어오더라도 해당 요청을 무시
      - 인터럽트 플래그가 가능으로 설정되어 있다면 CPU는 인터럽트 요청 신호를 받아 들이고 인터럽트를 처리
      - 인터럽트 플래그가 불가능으로 설정되어 있어도 무시할 수 없는 인터럽트 요청도 존재
        > 막을 수 있는 인터럽트(maskable Interrupt)  
        > 막을 수 없는 인터럽트(non maskable Interrupt)
        
    - 인터럽트 서비스 루틴(ISR; Interrupt Service Routine)
      - 인터럽트를 처리하기 위한 프로그램으로 인터럽트가 발생하면 어떻게 행동해야할지 알려주는 프로그램 
      - 인터럽트 핸들러라고도 부름

    - 인터럽트 벡터(Interrupt Vector)
      - CPU는 각기 다른 인터럽트 서비스 루틴을 구분하기 위하여 인터럽트 벡터를 이용
      - 인터럽트 벡터는 인터럽트 서비스 루틴을 식별하기 위한 정보
      - 인터럽트 벡터를 알면 인터럽트 서비스 루틴의 시작 주소를 알수 있음  
         
***
> 강민철, 『혼자 공부하는 컴퓨터 구조 + 운영체제』, 한빛미디어(2022)  
  
