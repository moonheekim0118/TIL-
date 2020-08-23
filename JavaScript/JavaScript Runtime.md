# JavaScript Runtime



### Web API

- 브라우저에서 제공하는 API
- DOM , fetch() setTimeout() 등
- web API를 동기적으로 실행하면 너무 느려짐 따라서 비동기적 처리를 함
- web API가 call stack에 들어오면 call stack은 web API에서 처리하도록 보냄
- web api 에 대한 코드가 background에서 실행이 완료되면 callback queue에 들어가게 되고, call stack이 비어지면 callback queue에 있는 내용을 stack으로 푸시함 ( by Event loop )

 

### Event loop

- 이벤트 루프는 Callback Queue에 있는 내용을 Call Stack으로 보내기 위해서, 계속해서 Call stack이 비었는지(해당 자바스크립트 파일이 끝까지 다 실행이 되었는지) 확인한다. 
- Call Stack이 비었다면 이벤트루프가 실행되면서 Callback Queue에 있는 내용을 Call Stack으로 푸시하게 된다.



