# 실행컨텍스트 (execution context)

- 실행할 코드에 제공할 환경 정보들을 모아놓은 객체
- 동일한 환경(하나의 실행컨텍스트) 의 코드들을 실행 시, 필요한 환경정보들을 모아 컨텍스트를 구성하고 이를 콜 스택에 쌓아놨다가, **가장 위에 쌓여있는 컨텍스트와 관련있는 코드들을 실행**함
  - 동일한 환경이 구성되는 조건: eval 함수, 함수, 전역 공간
- 자바스크립트를 실행하는 동시에 전역 컨텍스트가 콜 스택에 담김
  - 최상단은 브라우저에서 자동으로 실행되므로, 자바스크립트 파일이 열림과 동시에 전역 컨텍스트가 활성화 된다.
- 어떤 실행 컨텍스트가 활성화 될 때 자바스크립트 엔진은, 해당 컨텍스트에 관련된 **코드들을 실행하는데 필요한 환경 정보들을 수집**해서 **실행 컨텍스트 객체에 저장**한다. 



### 실행 컨텍스트 객체 

- VariableEnvironment
- LexicalEnvironment
- This binding 



#### 1. VariableEnvironment 

- environment Record (snapshot) - 초기 상태 유지 
- outerEnvironmentReference (snapshot) - 초기 상태 유지 
- 실행 컨텍스트 실행 시 Variable Environment에 가장 먼저 정보를 담음
- 그 후에 이를 그대로 복사하여 Lexical Environment 생성
- 전역 실행 컨텍스트는 변수 객체를 생성하는 대신, 자바스크립트 구동환경이 별도로 제공하는 객체(global object)를 활용



#### 2. LexicalEnvironment 

- environment Record - 함수 실행도중에 변경되는 사항이 즉시 반영 
- outerEnvironmentReference - 함수 실행도중에 변경되는 사항이 즉시 반영 
- 컨텍스트를 구성하는 환경정보들을 모아놓음 (식별자, 참조 등)



> **environmentRecord** 

- 현재 컨텍스트와 관련된 코드의 식별자 정보들이 저장 ( 함수에 지정된 매개변수 식별자, 함수 자체, var 선언 변수 식별자 등..)
- 컨텍스트 내부 전체를 처음-끝 까지 훑어가며 순서대로 식별자 정보 수집
- 이렇게 environmentRecord에서 코드가 실행되기 전에 해당 환경에 속한 변수명을 모두 수집함 == '호이스팅'
  - 즉, 자바스크립트 엔진이 실제적으로 '끌어올리지는' 않고 enviromentRecord가 변수 정보를 미리 수집하는 것이다.



```javascript
function a() {
    var x = 1;
	console.log(x); 
	var x ;
	console.log(x);
	var x =2; 
	console.log(x); 
}
```

호이스팅이 없다면 위의 결과는 1, undfined, 2 여야 할 것이다. 하지만 호이스팅의에 의해서 결과는 1,1,2 가 된다.



> **environmentRecord** - 호이스팅의 규칙

- 변수는 선언부와 할당부를 나누어 선언부만 끌어올리는 반면, 함수 선언은 함수 전체를 끌어올린다.
- 변수의 할당부는 원래 자리에 남겨둔다. 



> **environmentRecord** - 함수 선언문 ,함수 표현식의 호이스팅 차이점 

```javascript
function a() {} // 함수 선언문
var b = function(){} // 익명 함수 표현식 
```



```javascript
console.log(sum(1,2));
console.log(multiply(1,2));

function sum(a, b){
    return a+b;
}

var multiply = function(a,b){
    return a*b;
}
```

environment record에 의해 호이스팅 후

```javascript
function sum(a,b){
    return a+b;
} // 함수 선언문은 함수 정보 전체가 수집됨

var multipy ; // 함수 표현식은 함수명만 수집되고 함수 선언은 그 자리에 남음

console.log(sum(1,2)); // 3 
console.log(muliply(1,2)); // mutiply is not a function 에러 

var multiply = function(a,b){
    return a*b;
}
```



> **outerEnvironmentReference** - 스코프 ,스코프 체인

- 스코프(Scope) : 식별자에 대한 유효범위 (함수 스코프, 블럭 스코프)
- 스코프 체인 (Scope chain) : 식별자의 유효범위를 안에서 바깥으로 차례대로 검색해가는 것
  - 스코프와 스코프체인은 outerEnvironmentReference에 의해  가능



> **outerEnvironmentReference** - 스코프 체인 

- outerEnvironmentReference는 현재 호출된 함수가 선언될 당시의 LexicalEnvironment를 참조
  - A함수 내부에서 선언된 B함수의 outerEnvironmentReference는 함수 A의 LexicalEnvironment참조 .. 이렇게 타고 올라가다보면 전역 컨텍스트의 LexicalEnvironment가지 가게 된다.
  - 위와 같이 연결리스트 형태를 띄게 된다.
- 각 outerEnvironmentReference는 자신이 선언된 시점의 LexicalEnvironemt만 참조하므로, **가장 가까운 요소부터 차례대로 접근** 가능 ==> 여러 스코프에서 동일한 식별자 선언한 경우 **스코프 체인 상에서 가장 먼저 발견 된 식별자에게만 접근 가능**



```javascript
var a = 1; 
var outer = function(){
    var inner= function(){
        console.log(a); // # 1번 
        var a = 3; 
    }
    inner();
    console.log(a); // #2 번 
};

outer();
```

* 1번에서는 식별자 정보 a를 수집하여 호이스팅했으나 할당은 console.log보다 아래있으므로 undefined 출력
  * 아래 변수 은닉화 참조 
* 2번에서는 활성화된 실행 컨텍스트 LexicalEnvironmnet에 접근하여 environmentRecord에 a 가 있는지 찾아보고 없으면 **outerEnvironmentReference가 가리키고 있는 environmentRecord (여기서는 전역 LexicalEnvironment)로 넘어가 a 가 있는지 찾아봄**. a가 있으므로 a에 저장된 값 1 출력



> **outerEnvironmentReference** - 변수 은닉화 ( variable shadowing)

- 스코프 체인 상 있는 변수라고 해서 모두 접근 가능하지 않음
- 스코프 체인 상 첫번째 인자만 검색 가능,  식별자 발견시 더이상 체인 검색을 하지 않음





#### 3. This Binding

- this로 지정된 객체가 저장
- 실행 컨텍스트 활성화 당시 this가 지정되지 않는다면, this에는 **전역 객체**가 저장됨 