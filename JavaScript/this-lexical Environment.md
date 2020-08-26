# this == dynamic scoped

```javascript
const obj = {
    name:'moonee',
    sing(){
        console.log('a',this)  // 결과 : obj
        var anotherFunc= function(){
            console.log('b',this); // 결과 : window
        }
        anotherFunc()
    }
}
obj.sing();
```

- 자바스크립트에서 모든 것은 lexically scoped ( === 호출된 곳이 아니라 정의된 곳에 따라서 달라짐) 이지만, this keyword만 예외, 위에서는 obj 내부에서 실행된 함수이므로 this가 obj가 나올 것 같지만 anotherFunc()을 호출한 주체가 없기 때문에 window가 나온다.
- 위 예제의 혼란성을 줄이는 것은 ES6의 애로우펑션, 애로우 펑션은 함수가 정의된 곳에 따라서 this가 달라진다. 