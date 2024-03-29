## Computer Architecture

### 4장 CPU의 작동원리   

### 4-01 ALU와 제어장치   
- **ALU**
  - CPU내부에서 계산을 담당하는 역할
  - ALU는 계산을 하기 위해서 피연산자와 수행할 연산이 필요
  - ALU는 레지스터를 통해 피연산자를 받아들이고 제어장치로부터 수행할 연산을 알려주는 제어 신호를 받아들임
  - ALU가 내보내는 정보
    - 연산을 수행한 결과는 특정 숫자, 문자, 메모리 주소가 될 수 있음
    - 결과값은 바로 메모리에 저장되지 않고 일시적으로 레지스터에 저장
    - CPU가 메모리에 접근하는 속도는 레지스터에 접근하는 속도 보다 훨씬 느리기 때문에 ALU의 결과 값을 레지스터에 저장
    - ALU는 계산 결과값과 연산 결과에 대한 추가적인 정보(Flag)를 내보냄
    <br>  
    <center>   
  |플래그 정보| 의미 | 사용예시|
  |----|----|-----|
  |부호플래그| 연산한 결과의 부호| 1일 경우 음수, 0일 경우 양수|
  |제로플래그| 연산의 결과가 0인지 여부 |제로플래그 1일 경우 0, 0일 경우 0이 아님|
  |캐리플래그| 연산 결과 올림수나 버림수 발생 여부 |1일 경우 올림수/버림수 발생, 0일 경우 발생하지 않음 |
  |오버플로우 플래그|오버플로우 발생 여부 |1일 경우 발생, 0인 경우 발생하지 않음|
  |인터럽트 플래그|인터럽트 가능 여부| 1일 경우 가능, 0일 경우 불가능 |
  |슈퍼바이저 플래그|커널모드 사용자 모드 실행여부 |1일 경우 커널모드, 0일 경우 사용자 모드|
  </center>
  
  - 플래그들은 플래그 레지스터에 저장 
  <br>
- **제어장치**
  - 제어 장치는 제어 신호(컴퓨터 부품을 관리하고 작동 시키기위한 일종의 전기 신호)를 내보내고 명령어를 해석하는 부품

  - 제어장치는 클럭 신호를 받아들인다 
    - 클럭(Clock) 주기에 맞춰 한 레지스터에서 다른 레지스터로 이동, ALU 연산 수행, CPU가 메모리 저장된 명령어 읽어들임
    - 하나의 명령어가 여러 클럭에 걸쳐서 실행
    <br>  
  - 제어장치는 '해석해야 할 명령어'를 받아들인다
    - CPU가 해석해야 할 명령어는 명령어 레지스터에 저장
    <br>  
  - 제어장치는 플래그 레지스터 속 플래그 값을 받아 들인다
    - 플래그는 ALU 연산에 대한 추가적인 상태 정보
    - 제어장치는 플래그 값을 받아들이고 이를 참고하여 제어 신호를 발생 시킴    
    <br>
    
  - 제어장치는 시스템 버스 중 제어버스로 전달된 제어 신호를 받아 들인다
    - 제어장치가 내보내는 정보는 CPU 외부에 전달하는 제어 신호, CPU 내부에 전달하는 제어 신호로 구분
    - 제어장치가 CPU 외부에 제어신호를 전달한다는 것은 제어 버스로 제어 신호를 보낸다는 의미
      - 메모리에 전달하는 제어 신호
      - 입출력장치에 전달하는 제어 신호
      <br>
    - 제어장치가 CPU 내부에 전달하는 제어신호
      - ALU에 전달하는 제어 신호: ALU에 수행할 연산을 지시하기 위함
      - 레지스터에 전달하는 제어 신호: 레지스터 간 데이터 이동, 레지스터에 저장된 명령어 해석
    
***
> 강민철, 『혼자 공부하는 컴퓨터 구조 + 운영체제』, 한빛미디어(2022)  
  
