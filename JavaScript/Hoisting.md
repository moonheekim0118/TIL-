# Hoisting

- 호이스팅은 Global Execution Context 내에서 Global Object와 this를 생성하는 creation phase 내에서 진행되어 실행 컨텍스트 내에 있는 var 변수와 함수들의 정보를 수집한다. 이 후, execution phase에서 호이스팅하여 수집한 변수들에 정의를 한다.
- 각각의 함수 내에서도 Global Execution Context가 생성된다. 즉 모든 실행 컨텍스트 내에서 호이스팅이 일어난다.

```javascript
var favFood="sushi"

var foodThouhgts = function (){
  console.log('origin:'+favFood); // undefined 출력 
  var favFood="pasta"; // 이게 위로 hoisting되었음
  console.log('new:'+favFood); // pasta 출력 

}

foodThouhgts();
```



```javascript
var favFood="sush"

var foodThouhgts = function (){
  console.log('origin:'+favFood); // sushi출력
    //스코프 체인에 의해서 바로 위의 영역에서 favFood를 찾으려고함

}

foodThouhgts();

```



### how hoisting works?

- lexical Environment 내의 environment Record는 현재 컨텍스트와 관련된 코드의 식별자 정보들이 저장되고, 이는 컨텍스트 내부 전체를 처음부터 끝까지 쭉 훑어가며 순서대로 수집



### 함수 선언문과 함수 표현식

```javascript
function foo (){
    console.log('bar');
} // 전체를 호이스팅함
```

```javascript
var foo = function(){
    console.log('bar'); 
} // 'var foo'변수 선언문만 호이스팅 함 
```

