# call / apply / bind 메서드 활용



## call() 

- 첫번째 인자로 객체를 주는데, call 을 호출하는 함수가 인자로 주어진 객체에 딸려있는 객체처럼 동작하게 된다
- func.call(thisArg[, arg1, [,arg2[, ...]]]) 첫번째 인자는 함수를 소유하는 객체 지정(this가 될 객체), 두번째부터는 옵션 

```javascript
var person= {
  funllName: function(city,country){
    console.log(this);
    return this.firstName + " " + this.lastName + "," +city + ", "+ country
  }
}

var person1 ={
  firstName: "Moonee",
  lastName: "Kim"
}

person.funllName.call(person1, "Oslo", "Norway")

// 결과: console.log(this) ==>{ firstName: 'Moonee', lastName: 'Kim' }
```



#### 익명함수 호출에 call 사용

```javascript
var animals =[
  {species:'Wolf', name:'Gang'},
  {species: 'Dog', name:'Boogie'}
];


for(var i =0; i< animals.length; i++){
  (function(i) {
    this.print=function(){
      console.log('#'+i+' '+ this.species +
      ':'+this.name);
    }
    this.print();
  }).call(animals[i],i);
}
```



## Apply()

- call 과 거의 흡사하지만, call은 함수에 전달된 **인수 리스트**를 받고, apply는 함수에 전달될 **인수들의 단일 배열**을 받는다는것이 다르다.
- func.apply(thisArgs, [argsArray])



### apply 와 내장함수 사용

배열에 배열을 붙이기 ( 배열 내부 배열 말고!)

```javascript
var array=['a', 'b']
var element=[0,1,2]
array.push.apply(array,element)
--> ['a','b',0,1,2]
```



여러개의 배열 중에서 max/min값 루프없이 구하기

```javascript
var nums=[5,1,3,7,10];
var max = Math.max.apply(null,nums); // 10
var min = Math.min.apply(null,nums);  // 1
```



주의할 점 

- 함수에 너무 많은 (몇만개 이상) 인수를 줄 때는 예외를 주거나, 참조하는 인수의 수를 제한하기도 한다.



### 생성자 체이닝을 위한 apply

```javascript
Function.prototype.construct = function (aArgs){
    var oNew = Object.create(this.prototype);
    this.apply(oNew, aArgs);
    return oNew;
}
```





## Call & Apply 활용

### 유사 배열 객체에 배열 메서드를 활용 

- 객체, arguments, NodeList, 문자열  등 

```javascript
var obj={
    0:'a',
    1:'b',
    2:'c'
}

Array.prototype.push.call(obj,'d');
```

- 문자열에 배열 메서드 적용 예시

```javascript
var str ="abc def";

Array.prototype.push.call(str, ', pushed String'); // Error 

Array.prototype.every.call(str, function(char) { return char!==' ';}) 
// every 메서드는 배열 안의 모든 요소가 주어진 판별함수를 통과하는지 테스트한다.
// some 메서드는 배열 안의 어떤 요소라도 주어진 판별 함수를 통과하는지 테스트한다.

var newArr = Array.prototype.map.call(str,function(char) {return char+"!";});

var newStr = Array.prototype.reduce.apply(str, [
    function(string,char, i){return string+char+i;}
])
```



### 생성자 내부에서 다른 생성자 호출

```javascript
function Person(name, gender){
    this.name=name;
    this.gender=gender;
}

function Student(name,gender,school){
    Person.call(this,name,gender);
    this.school=school;
}
```







## bind 메서드

- func.prototype.bind(thisArg,[, arg1 [, arg2 [,...]]])

- call 과 유사하지만, 즉시 호출하지 않고 넘겨받은 this 및 인수들을 바탕으로 새로운 함수를 반환하기만 하는 메서드이다. 

```javascript
var func = function(a,b,c,d){
    console.log(this,a,b,c,d);
}

var bindFunc1 = func.bind({x:1});
bindFunc1(5,6,7,8)

var bindFunc2 = func.bind({x:1}, 4, 5);
bindFunc2(6,7) // 4 5 6 7
bindFunc2(8,9) // 4 5 8 9
```



### bind의 name 프로퍼티

- bind의 name 프로퍼티에는 bound라는 접두어가 붙는다.



### 상위 컨텍스트의 this를 내부 함수나 콜백함수에 전달하기

- call 사용 

```javascript
var obj={
    outer:function(){
        console.log(this);
        var innerFunc = function(){
            console.log(this);
        }
        innerFunc.call(this);
    }
}
```

- bind 사용

```javascript
var obj={
    outer:function(){
        console.log(this);
        var innerFunc= function(){
            console.log(this);
        }.bind(this);
        innerFunc();
    }
}
```





## 화살표 함수 예외사항

- ES6 의 화살표 함수는 실행 컨텍스트 생성 시, this 바인딩 과정이 제외되었음
- 접근하고자 하면, 스코프 체인상 가장 가까운 this에 접근하게 된다.

```javascript
var obj ={
    outer: function(){
        console.log(this);
        var innerFunc=()=>{
            console.log(this);
        }
        innerFunc();
    }
}
```





## 별도의 인자로 this를 받는 경우

- 배열 메서드

```javascript
var report = {
    sum: 0 ,
    count : 0,
    add : function(){
        var args = Array.prototype.slice.call(arguments);
        args.forEach(function(entry){
            this.sum+=entry;
            ++this.count;
        },this)
    },
    average: functon(){
    	return this.sum / this.count;
	}
};

report.add(60,85,95);

```

