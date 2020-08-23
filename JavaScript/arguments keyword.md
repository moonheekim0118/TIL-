# Arguments

- 함수로 인하여 새로운 실행 컨텍스트가 생성 될때, creation phase에서 생성된다.

```javascript
const marry=function (person1,person2){
  console.log(arguments);
}
marry('will', 'laura');

// 결과 :  { '0': 'will', '1': 'laura' }
```



### why Arguments is dangerous to use?

- array처럼 보이지만 array가 아니므로 array methods를 사용하지 못함. 따라서 자바스크립트 엔진에 부담이 간다.



### how to use Arguments?

1. **Array.from**을 이용하여 배열형태로 변환하기 

```javascript
const marry=function (person1,person2){
  const arr1 = Array.from(arguments)
  //[ 'will', 'laura' ]
}
marry('will', 'laura');
```



2. **Rest parameters**

```javascript
const marry=function (...args){
  console.log(args)
    //[ 'will', 'laura' ]
}
marry('will', 'laura');
```

