# Module Pattern

- 함수로 데이터를 감추고, 모듈 API를 담고있는 객체를 반환하는 형태



1. 임의 함수를 호출하여 생성하는 모듈
2. 즉시 실행 함수 (IIFE) 기반의 모듈 



- 단일 책임의 원칙에 따라 모듈을 한가지 역할만 하도록 한다.
- 모듈 자신이 사용할 객체가 있다면 의존성 주입 형태로 제공한다. 



### 1. 임의 모듈 패턴

```javascript
var App = App || {};
App.Person = function(God){
    var name= God.makeName();
    return{
        getName: function(){return name},
        setName: function(newName){name=newName};
    }
}
const person = App.Person(God)
person.getName();
```





### 2. 즉시 실행함수 모듈 패턴

```javascript
var App = App || {};
App.Person (function(){
    let name="";
    return {
        getName(God){
            name= name || God.makeName();
            return name;
        },
        setName(newName){name=newName}
    }
})()
```



