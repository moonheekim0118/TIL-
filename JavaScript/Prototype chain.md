# Prototype chain

```javascript
let dragon= {
    name:'boogie',
    fight(){
        return 5;
    },
    sing(){
        return 1;
    }
}

let lizard = {
    name="kiki",
    fight(){
        return 1
    }
}

lizard.__proto__=dragon; 
for (let prop in lizard){
    if(lizard.hasOwnProperty(prop)){
        console.log(prop); // name, fight 
    }
}
```

- 다른 객체를 프로토타입으로 삼고 상속한다고하여 해당 객체의 메서드를 복사하는 것이 아님
- 프로토타입 체인을 이용하여 lizard 에서 sing 이란 메서드를 호출하면 lizard에 있는지 먼저 살펴보고 없으면 상위 프로토타입을 살펴본다. ( 최상위 프로토타입까지 올라감)
- 실제로는 __ proto __ 를 직접 지정해주는 것은 성능에 좋지 못하고 아래와 같이 프로토타입을 상속 받을 수 있음 

```javascript
let human = {
    mortal:true
}

let socrates = Object.create(human);
```





## __ proto __와 prototype

```javascript
function func(){}
```

-  func.__ proto __ 는  Function.prototype을 가리킨다.
- __ proto __ 는 단순히 상위 프로토타입 객체의  포인터 / 참조자이다.
- 메서드는 prototype 내부에 정의되어 있고, 심지어 __ proto __ 조차도 prototype 내부에 정의되어 있다.



![](https://i.stack.imgur.com/AGfN3.png)



### 오직 함수만 prototype property가 있다

```javascript
typeof Object ===> "function"
const obj = {};
typeof obj ===> "object"
```

- Object는 object wrapper를 만들어주는 object **생성자**
- 즉,  객체 자체를 만들어주기 위한 생성자가 Object이고 이는 함수이기 때문에 prototype이 존재함, 이는 Boolean, Number도 마찬가지



### excercise 

- Date prototype에 새로운 메서드 추가하기

```javascript
Date.prototype.lastYear=function(){
  return this.getFullYear()-1;
}

new Date().lastYear();
```

- map 메서드 수정하기

```javascript

const newMap= function(){
   let newArr=[];
  for(let item of this){
    newArr.push( `${item}🗺`);
  }
  return newArr;
}


Array.prototype.map = newMap;

console.log([1,2,3].map());

```

- apply로 bind 메서드 만들기

```javascript
Function.prototype.bind = function(whoIsCallingMe){
  const self = this;
  return function(){ // bind는 함수를 return 하므로..
    return self.apply(whoIsCallingMe, arguments);
  };
}
```

