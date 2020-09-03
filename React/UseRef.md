# UseRef

- useState를 통해 선언한 변수의 값이 수정되면, 렌더링이 다시 되지만,  useRef를 통해 선언된 변수의 값이 수정되어도 렌더링이 되지 않는다. 
- useRef를 통해 선언한 변수는 .current 내부에다 저장해주어야 한다.

```javascript
const variable=useRef();
variable.current=54;
```

- 따라서, 값이 바뀌어도 렌더링을 다시 실행시키고 싶지 않은 값은 useRef에 넣어서 사용하자



