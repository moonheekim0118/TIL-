# IIFE  즉시실행 함수

```javascript
(function(i){
    console.log(i);
})(1); // 1
```

- 새로운 즉시실행함수 자체의 variable Environment를 가진 실행 컨텍스트를 만든다.
- IIFE 내에서 생성된 변수는 **private data**로서, 외부에서 접근 불가능하다.

```javascript
var script =(function(){
    function(a){
        return 5;
    }
    return {
        a:a
    }
})();
```

