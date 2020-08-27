# Closures

- 생성될 당시의 환경을 기억하는 함수
  - 환경 : 스코프 체인 자체 

```javascript

function a(){
  let grandpa="grandpa";
  return function b(){
    let father= "father";
      return function c(){
        let son = "son";
        return `${grandpa} ${father} ${son}`
      }
  }
}

a()()();
```

- function c는 어떻게 father와 grandpa를 기억하는가 ? 스택에서 pop off 되면 가비지 콜렉터에 의해 제거되는 것이 아닌가 ?
- 원래대로라면 가비지 function a , b 가 스택에서 pop off 되면서, 가비지 콜렉터에 의해 변수가 제거되어야 하지만, 내부에서 해당 변수를 참조하는 곳이 있기 때문에 **클로저**에 담게 된다. 
- 자바스크립트 엔진은 클로저를 이용하여 함수 내부에서 외부로부터 모든 변수에 접근 할 수 있도록 해준다
- 그러면 어떻게 내부에서 특정 변수를 참조하는지 알 수 있는가?
  - lexical scoping 하는 과정에서 정보를 수집한다

```javascript
const boo = (string) =>(name)=>(name2)=>
	`${string} ${name} ${name2}`

const booString = boo('hi');
const booStringName=booString('Jane');
const booStringName2=booStringName('John');
console.log(booStringName);
```



## Memory Efficient

```javascript
function heavy(index){
  const bigArray= new Array(7000).fill('foobar');
    return bigArray[index];
}

heavy(1);
heavy(1000); 
```

- 위와같은 코드는 실행할때마다 Array를 생성 -> 디스트로이 하는 과정을 반복하게 되어서 메모리에 취약 



```javascript
function heavy(){
  const bigArray= new Array(7000).fill('foobar');
  return function(index){
    return bigArray[index];
  }
}

const getHeavy= heavy();

console.log(getHeavy(2);
console.log(getHeavy(150);
```

- 클로저를 이용하면 Array는 한번만 생성되어서 클로저에 저장되어 쓰여진다.



## Encapsulation

- 클로저에 담긴 변수는 객체지향 언어의 private변수와 같은 효과를 내기 때문에 외부에서 직접 접근하는 것을 제한 할 수 있다.

```javascript
function sayName(name){
    var __name = name;
    return function(){
        console.log('my name is '+ __name);
    }
}
```





### Examples

한번만 initialize 하도록 하기 

- 내부 함수에서 클로저에 담긴 변수 값을 변경 할 수 있음을 응용

```javascript
let view;
function initialize() {
    let called=0; 
      return function(){
        console.log(called);
        if(called> 0) return;
        else{
           view = '🏔';
          console.log('view has been set!')
          called++;
        }
      }
}

const startOnce = initialize();
startOnce();
startOnce();
startOnce();
startOnce();
console.log(view)
```



반복문에서 클로저

```javascript
const array = [1,2,3,4];
for(var i=0; i < array.length; i++) {
  setTimeout(function(){
    console.log('I am at index ' + i)
  }, 3000)
} 
// 이렇게 하면 마지막 인덱스에 대한 값만 출력된다
```



#### 0~3을 출력하기 위한 방법 

1. let keyword를 쓴다
   - let은 block scoping의 영향을 받으므로 각각 i 마다 scope을 생성하고, setTimeout 메서드는 해당 scope에 들어가게 된다. 

```javascript
const array = [1,2,3,4];
for(let i=0; i < array.length; i++) {
  setTimeout(function(){
    console.log('I am at index ' + i)
  }, 3000)
} 
```



2. IIFE 

```javascript
const array = [1,2,3,4];
for(var i=0; i < array.length; i++) {
  (function(closureI){
  setTimeout(function(){
    console.log('I am at index ' + closureI)
  }, 3000)
  })(i)
}
```

