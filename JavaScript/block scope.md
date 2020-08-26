# block scope

- 자바스크립트는 원래 function scope 만 존재했음
- es6 이후 let과 const 는 block scope의 영향을 받게 된다.



```javascript
if(true){
    let i = 10;
}
console.log(i) // error
```

