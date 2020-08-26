# Pass By value & Pass By reference



### pass by value

```javascript
var a = 10
var b = a;
b+=15;
```

- b는 a의 value를 저장하지만 다른 메모리 공간을 만들어 해당 value를 따로 저장하게 된다.
- 따라서 b가 변해도 a는 변하지 않는다.



### pass by reference

```javascript
var obj1={name:'m', password:'123'};
var obj2=obj1
obj2.password='dfdf';
```

- obj2가 obj1을 복사할 때 단순히 값을 복사하는 것이 아니라, 해당 주소 자체를 복사하므로,  obj1과 obj2는 같은 주소를 바라보게 된다. (얕은복사)
- 따라서 obj2를 변경 시, obj1도 변경하게 된다. 



#### Array에서 깊은 복사하기

```javascript
var c = [1,2,3,4,5];
var d =[].concat(c); 
d.push(12121); 
```

#### Object에서 깊은 복사하기

```javascript
var obj1={name:'m', password:'123'};
var obj2= Object.assign({},obj1); // solution1 
var obj3 = {...obj1}; //solution2 new feature 
obj2.password('dfjdf');
```



### Object내부에 있는 Object는 ?

```javascript
var obj1={name:'m', password:'123', 
          c:
          {
              deep:'try'
          }};

let clone = JSON.parse(JSON.stringify(obj1));
```





```javascript
let obj1={
  a:5
}

let obj2={
  a:15
}
let i = 10;
function change(obj, obj2, i){
  obj=obj2; // obj1은 바뀌지 않음
  obj2.a=99; // obj2가 바뀜
  obj.a=101 // obj2 가 바뀜 
  i=15; // i는 바뀌지 않음
}

change(obj1,obj2,i);
console.log(obj1,i,obj2);
```

- 위 예제에서 obj=obj2 에서 obj1이 함수 밖에서 바뀌지 않는 것은 i가 바뀌지 않는것 과 마찬가지이다. (by value) 즉 실질적 주소 내부에서  값(value)변화가 일어나지 않는 것이다. 반면 obj의 프로퍼티를 변경하는 것은 해당 오브젝트의 실질적 주소 내부에서 값을 변경하는 것(by reference) 이므로 함수 밖의 obj2도 변화가 일어난다. 