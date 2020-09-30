# Array methods 

### concat()

- 2개 이상의 배열을 합친 후, 새로운 배열을 반환한다.
- 기존 배열에 영향을 미치지 않는다.
- const concatedArray=앞에올배열.concat(뒤에올배열)

```javascript
const arr1= ["inception", "interstellar"];
const arr2 =["dunkirk", "Tennet"];
const christoperNolan=arr1.concat(arr2);
// [ "inception", "interstellar", "dunkirk", "Tennet"]
```

<br/>



### copyWithin()

- 배열의 요소를 배열 내 다른 위치에 복사하며, 기존 배열을 변경한다.
- 배열 길이를 벗어나는 요소에 복사하려고 하면 복사되지 않음! 절대 배열 자체의 길이를 늘릴 수 없다.
- array.copyWithin(요소를 넣을 배열 인덱스, 복사할 요소가 있는 배열 인덱스)

```javascript
const arr=["inception", "interstellar","dunkirk"];
console.log(arr.copyWithin(2,0))
// ["inception", "interstellar","inception"]
```



<br/>



### entries()

- key와 value를 가진 배열 반복자(Iterator)를 반환한다.
- 기존의 배열을 변경하지 않는다.
- 여기서 key는 인덱스가 되고, value는 기존 배열의 요소가 된다. 
- const iterator = array.entries();

```javascript
const arr=["inception", "interstellar","dunkirk"];
const newArr=arr.entries();
for(x of newArr){
    console.log(x);
    // 0,inception
    // 1,interstellar
    // 2, dunkirk
}
```

<br/>



### every()

- 모든 배열 요소가 특정 패스를 테스트하는지 체크해준다.
- 테스트를 위해서 특정 함수를 한번 수행한다.
  - 만약 함수에서 false를 반환하는 value를 찾는다면 every()는 false를 리턴하고, 나머지 value를 체크하지 않는다.
- 기존의 배열을 변경하지 않는다.
- const result= array.every(함수) 

```javascript
const ages=[32,22,16,40];

const checkAudult=(age)=>{
    return age>=18;
}

const myFunction=()=>{
    ages.every(checkAudult);
}
```

<br/>



### fill()

- 기존의 배열을 덮어쓴다. 
- 배열내 특정한 요소를 다른 value로 변경한다.
- 위치를 지정하면 특정한 요소만 변경하고, 위치를 지정하지 않으면 배열내 모든 요소가 변경된다.
- array.fill(변경할 value, 시작, 끝)

```javascript
var fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.fill("Kiwi",0,2);
// ["Kiwi", "Kiwi", "Apple", "Mango"];
```



<br/>



### find()

- 함수로 제공되는 테스트를 가장 먼저 통과한 배열 요소를 반환한다.
- 배열 요소내 테스트를 통과한 요소가 없다면 undefined를 반환한다.
- const result= array.find(함수)

```javascript
const ages=[3,10,18,20];

const checkAudult=(age)=>{
    return age>=18;
}

const myFunction=()=>{
    console.log(ages.find(checkAudult)); // 18
}
```



<br/>

### join()

- 배열을 string으로 변경한다.
- 기존의 배열을 변경하지 않고, 새로운 string을 반환한다.
- 특정 seperator에 따라서 join 할 수 있다. default seperator는 ',' 이다.
- const newStr= array.join();

```javascript
const fruits = ["Banana", "Orange", "Apple", "Mango"];
const str=fruits.join();
console.log(str) ; //Banana,Orange,Apple,Mango
```



<br/>

## shift()

- 기존 배열에서 첫번째 요소를 삭제한다.
- 기존 배열을 변경하며, 삭제된 아이템을 반환한다.



<br/>

### slice()

- 배열내 특정 아이템을 새로운 배열로 만들어 반환한다.
- 기존 배열은 변경되지 않는다.
- const part=array.slice(시작점,끝)

```javascript
const fruits = ["Banana", "Orange", "Lemon", "Apple", "Mango"];
const part= fruits.slice(1,3);
// parts === ["Orange","Lemon"];
```

<br/>



### splice()

- 기존 배열을 덮어 쓴다.
- 기존 배열의 특정 자리에 요소를 삭제 혹은 추가한다.
- array.splice(index, howmanyRemoved, item1....itemX)
  - index : 아이템을 삭제 / 추가할 인덱스 자리
  - homanyRemoved: 옵셔널, 삭제할 아이템의 수 
  - item1...: 옵셔널, 배열에 추가될 요소들 

```javascript
const fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.splice(2); // 추가하는 아이템 명시 X, 삭제 아이템수 명시 X 므로 인덱스 2 이후의 요소를 모두 삭제한다.

fruits.splice(2,0)// 추가하는 아이템 명시 X, 삭제 아이템수 0 이므로 아무것도 진행하지 않는다.

fruits.splice(2,0,"kiwi"); // 추가하는 아이템 명시 O, 삭제 아이템수 0 이므로 인덱스 2 자리에 kiwi를 넣는다. 기존 아이템은 뒤로 밀려난다.

fruits.splice(2,1,"kiwi"); // 추가하는 아이템 명시 O, 삭제 아이템수 1 이므로, 인덱스 2 자리의 요소를 하나를 삭제하고 인덱스 2 자리에 kiwi 아이템을 넣는다. 

```

