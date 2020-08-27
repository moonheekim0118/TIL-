# Higher Order Functions

- 다른 함수를 argument로 받는 함수
- 다른 함수를 return 하는 함수

```javascript
const multiplyBy = function(num1){
    return function(num2){
        return num2*num1;
    }
}

// arrow function version
const multiplyBy = (num1) => (num2) => num1*num2;

const multiplyByTwo=multiplyBy(2);
const multiplyByFive=multiplyBy(5);
multiplyByTwo(4); // 8
multiplyByFive(4); // 20 
```

