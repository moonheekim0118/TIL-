# Execution Context

- 자바스크립트는 함수 실행을 보면 실행컨텍스트를 실행하고, 해당 실행 컨텍스트를 Call stack에 넣는다.
- 가장 먼저 Call Stack에 쌓이는 실행 컨텍스트는 Global 실행 컨텍스트
- 모든 자바스크립트 코드는 결국 실행 컨텍스트에 속해있다 - function으로 생성된 실행 컨텍스트 or Global 실행 컨텍스트



### Global Execution Context

- global 실행 컨텍스트는 **Global object**와 **this**를 정의함 (creation phase)
- 내가 작성한 코드를 실행해줌 (execution phase)