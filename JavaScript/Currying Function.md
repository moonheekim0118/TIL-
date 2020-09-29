# 커링 함수

- 여러개의 인자를 받는 함수를 하나의 인자만 받는 함수로 나눠서 순차적으로 호출 될 수 잇게 체인 형태로 구성한 함수
- 한번의 하나의 인자만을 전달 받을 수 있다.
- 마지막 인자가 전달 되기 전까지는 원본함수가 실행되지 않는다.
  - 부분 적용 함수에서는 실행결과를 재실행 할 때 마다 원본함수가 무조건 수행 되었다.

```javascript
var curry = function(func){
    return function(a){
        return function(b){
            return func(a,b);
        }
    }
}

var getMaxWith10 = curry(Math.max)(10);
console.log(getMaxWith10(8)); // 10
console.log(getMaxWith10(25)); // 25

// es6 화살표 함수를 사용하면 더 간결하게 표현 할 수 있다.

var curry=func=>a=>b=>func(a,b);
```



## lazy execution 지연 실행에 활용되는 커링 함수

- 지연실행이란 ?
  - 당장 필요한 정보만 받아 전달하고, 또 필요한 정보가 들어오면 전달하는 식으로 마지막 인자가 넘어갈 때 까지 함수실행을 지연하는 것

```javascript
var getInfomation = baseUrl=> path=> Id=> fetch(baseUrl+path+'/'+Id);
```





### Redux Thunk 에 활용되는 커링 함수

```javascript
const thunk = store => next => action => {
    return typeof action === 'function'
    	? action(dispatch, store.getState)
        : next(action)
}
```

