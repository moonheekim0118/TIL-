# function currying using bind

```javascript
function multiply(a,b){
    return a*b;
}

let multiplyByTow = multiply(this,2); // 첫번째 인자만 넘겨준 함수를 만들어준다.
// 이 함수는 추후에 두번째 인자만 넘겨주도록 사용 가능하다.
multiplyByTwo(4); ==> 2*4 == 8 

```

